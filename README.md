# Kubernetes at Home
This project was intended to be a method to experiment with Kubernetes on a home-lab environment and to utilize some spare Raspberry Pi single board computers that I had. It ended up evolving into a slightly more meaningful project for daily use as I now use a single node Kubernetes cluster as my primary media server, network attached storage, and DNS sinkhole. As such, I have been able to verify the stability of such an implementation and the fun in designing and experimenting on this platform.

## Setup
The initial setup contained:
* Raspberry Pi 3B
* Raspberry Pi 4B
* 2x 64GB microSD cards
* 4 port gigabit switch
* 2TB external hard drive

After experimenting and simplifying:
* Raspberry Pi 4B
* 64GB microSD card
* 2TB external hard drive

The RPI computers are hooked into the LAN and the firewall is set up to not allow any traffic into or out of the LAN with these devices.

## Services
* Plex Media Server
  * ARM based version
  * Requires Plex account, but is fully self-hosted
  * No directions on where you get your media files, that is up to you
* Pihole
  * DNS sinkhole
  * Can also be used as a DHCP server
* SFTP Share
  * Fairly basic share, but could be extended with a project like OpenMediaVault
  
## Outline
1. Flash the sd cards
   1. Raspberry Pi Imager is nice and easy
   2. Used a basic Raspbian Lite image
      1. Only contains the minimum requirements and is designed for RPI
      2. No desktop environment, so headless is the way to go
2. Install K3s on the main node
   1. K3s is from Rancher and is designed for lightweight Kubernetes deployments
   2. Some great posts on how to do this:
      1. https://blog.alexellis.io/test-drive-k3s-on-raspberry-pi/
      2. https://www.replex.io/blog/how-to-install-access-and-add-heapster-metrics-to-the-kubernetes-dashboard
3. Install K3s on the secondary node
   1. Make sure to bring this node into the cluster
4. Install the Kuberneted Dashboard
   1. This is a great way to interact without needing to use the command line all the time
   4. Creating a dashboard service account is also desireable here
   5. Setting the dashboard to a NodePort is also a way to simplify the process
5. Install kubectl on Windows (or whatever your development machine is)
6. Run a proxy on the kubernetes cluster for the dashboard to connect to
7. See the .bat file for a great way to connect the remote to the local machine
8. Deploy other applications and containers using the command line and the dashboard