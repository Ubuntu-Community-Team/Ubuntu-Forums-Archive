---
title: "TFTP Timeout in LTSP"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by amit@nitttrchd.ac.in on 2010-03-29
I'm attempting to use a Ubuntu 9.10 and 9.04  machine as a terminal server. 
However, I'm running into problems with TFTP. When the clients boot 
they receive an IP address, but when they try to connect to the TFTP 
server, the following error is returned: 

PXE-E11- ARP timeout 
PXE-E11- ARP timeout 
PXE-E38- TFTP cannot open connection 
PXE-M0F- Exiting Intel Boot Agent 

I checked to make sure that my settings were in accordance with the 
advice given here, and everything checks out. My TFTP server is using 
/tftpboot as root, everything is installed, and everything is enabled. 
However, my clients time out when trying to connect to the server. 
Anyone have any ideas?

---

### Post by amit@nitttrchd.ac.in on 2010-04-05
We would first install the Required applications step by step and then configure them later.
  
[LIST]
[*]1.Install the Regular Ubuntu Desktop Distro, I am using ubuntu 9.04 for this howto.
[*]2.Once Installed, update the distro and install all the necessary updates.
[*]3.Once Done Install NFS kernel Server via this Command : sudo apt-get install nfs-kernel-server
[*]4.Install the DHCP SERVER on the same machine,make sure there is only one dhcp server running on the network else.it will cause a conflict.
[*]5.Set a static ip to the machine via /etc/network/interfaces file – i am using 192.168.0.1 as SERVER ip for this HOWTO.
[*]6.Now install the server module for LTSP running this command on terminal : – sudo apt-get install ltsp-server-standalone openssh-server ( this would install the LTSP Server and the openssh on the desktop.
[*]7.Now Create your Thin Client environment on the server with this command: sudo ltsp-build-client
[*]The First command installs the LTSP SERVER and the Second command installs the module that  will provide/create  the environment  to run the remote disk less machines. ( Please be patient, the client module takes time to install as it fetches about 150 MB of files from the repos. )
[/LIST]
 
 Once the client installation is done run these 2 commands to create the ssh keys
 sudo ltsp-update-sshkeys
 sudo ltsp-update-image
 [LEFT]**Be sure to do it in that order.**[/LEFT]
 **We are now done with the installation. now comes the configuration part.**
  
[LIST]
[*]Open the /etc/default/tftpd-hpa and edit first line Run_Daemon to “Yes” in place of NO.Save and Exit.
[*]Now Open the /etc/ltsp/dhcpd.conf and change some values to the file as below.uncomment value next-server and put the server ip infromt of it ( next-server 192.168.0.1; )
[*]add these two values below that :
[*]allow booting;
[*]allow bootp;
[*]now go to the last line of the dhcpd.conf and it has a default value : filename (  ”/ltsp/i386/nbi.img”;  )   change that to (  filename “pxelinux.0&#8243;;  )
[*]Once done save and exit and restart the  dhcp server /etc/init.d/dhcp3-server restart
[*]Once done now u can just Boot the diskless workstations and it should aautomatically find the  dhcp server get an IP address and load the Remote OS. and Login.
[/LIST]

---

### Post by Madurama on 2010-08-26
go to steps.

(1) First i installed ltsp stand alone
sudo apt-get install ltsp-server-standalone openssh-server

(2) Second i build client
sudo ltsp-build-client --arch i386

(3) And then run the below commands

sudo ltsp-update-sskeys
sudo ltsp-update-image

end, no error :p

---

