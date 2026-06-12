---
title: "PXE installation over a network"
date: 2012-04-08
forum: Networking &amp; Wireless
---

### Post by quikslvr1982 on 2012-04-08
Hello, this is my first post on these forums.  I am a college student working on a project as part of a class.  The basic idea is our sponsor wants my project team to create an image for a small network of desktop computers using Ubuntu 11.10.  They would like this image to be deployable over a network using a PXE installation method, where the ISO image is stored on a central server and can be deployed to these desktops remotely.
 
I created the custom distribution using Remastersys, which worked perfectly as it wiped all the admin user settings but retained the custom packages they requested.  I have the ISO saved to USB flash drive and on a DVD.  Our team could deploy the image simply using the DVD but this would not satisfy the PXE installation requirements.
 
I have researched several methods ranging from FAI to Cobbler and openQRM.  My plan was to test if the ISO can be installed over a small test network at home before bringing the configuration into a larger business infrastructure.  However, configuring my home network has become more troublesome than I originally anticipated.
 
I have experience in networking and PXE installations using Windows Deployment Services at my job, but I am finding that while the basic concept is the same on Ubuntu that it is still a very different animal.  My current setup consists of a standalone machine where Ubuntu Server 11.10 is installed, which will host the TFTP server as well as the ISO location itself.  I was using a router as the DHCP server (although I have read that this is not a preferred method since some routers cannot forward requests to a TFTP server for the boot file) but this was not working.  The "client" is my personal laptop which when configured to boot using PXE attempts to connect through the gateway (default address for the router 192.168.1.1) but then boots to the Windows OS partition with the error code:
 
PXE-E53: No boot filename received.
The client received at least one valid DHCP/BOOTP offer, but does not have a boot filename to download. 
 
This setup was done using Cobbler, and I followed the steps exactly as detailed in the Cobbler documentation, including importing the ISO into Cobbler.  However, when I access the Cobbler web interface, there is nothing stored there.
 
I have never used the Linux operating system before, so this has been a major self-teaching project.  I am finding that there is an abundance of information and tutorials for older releases of Ubuntu (Natty and Maverick, for instance) but the commands to use in the Terminal for the installation of the packages do not always produce the same results in Oneiric.  For instance, attempting to configure the *package dhcp3-*server is more difficult since the configuration files to edit are not in the same location or have several additional lines of code that are not displayed in the tutorials.  At the risk of breaking my network (which I have already done once), I have been blindly attempting to get this to work.
 
Is there a more centralized location for Ubuntu Server 11.10 specifically, or any additional recommended applications that I have not considered that might be easier for a beginner to use?  Any help would be greatly appreciated.

---

### Post by roelforg on 2012-04-08
You know there's a rule about asking for homework, right?
But just make your server the router, works fine for my home net.
Only make sure your clients are on the same vlan and really are using your router because it seems like they are getting a different one than the one your laptop uses.

---

### Post by boethius on 2012-04-10
> **quikslvr1982 said:**
> \ I was using a router as the DHCP server (although I have read that this is not a preferred method since some routers cannot forward requests to a TFTP server for the boot file).

Is there a more centralized location for Ubuntu Server 11.10 specifically, or any additional recommended applications that I have not considered that might be easier for a beginner to use?  Any help would be greatly appreciated.
I would take a big step back from how you're doing this and try to understand the nuts and bolts of what you're attempting to do.  Given you've done this with Windows you should have some idea of how PXE booting is done and translate that to the Linux world.

Cobbler, FAI, OpenQRM, etc. are all designed for large-scale management of deployments, including PXE deployments.  You're front-loading your project for failure by using heavy-duty and fairly complex tools from what should be a simple task.  I don't think you need them.

You need three basic components for PXE booting to work:

1.  A DHCP server that sends option 66 (your PXE boot server) and option 67 (your TFTP boot filename).  These options will provide the filename in the DHCP response to the PXE client so you can bootstrap off the network.  If you're in an environment where you don't control the DHCP server setup or in an environment that has limited DHCP server functionality - e.g., a typical wireless router - there ARE ways around this requirement however for your purposes let's assume you can install say ISC DHCP or Microsoft DHCP server on your LAN.  Also if you have a wireless router (e.g. WRT54G, Netgear N300) that supports "open source" firmware (e.g., DD-WRT, Tomato, etc.) you CAN setup these more advanced DHCP options by loading that firmware.  

2.  A TFTP server.  You can "apt-get install tftp-server" this on to your Ubuntu server.

3.  A network bootstrap.  pxelinux is very common and very popular.  It's part of the syslinux package.  If you've got Ubuntu server you can "sudo apt-get syslinux" this if you haven't already.

While you can specific default boot options for your project using pxelinux you may want a menu system.  Syslinux has numerous COM32 programs that are designed to run in the bootstrapped environment - menu.c32 is probably one of the most popular for providing a very simple menu system.  The short story there is:

1.  Copy pxelinux.0 out of the syslinux package into your tftpboot folder. 

2.  Copy menu.c32 out of the syslinux package into your tftpboot folder.

3.  Tweak your tftpbootfolder/pxelinux.cfg/default text file as follows (an example; Google for more options): 
```

default menu.c32
prompt 0
timeout 600

MENU TITLE Your Cool Projects PXE Service Menu
TIMEOUT 150
label diagnostics
    menu label Diagnostics and Test
    kernel menu.c32
    append menus/diag.conf
label ubuntu
    menu label Ubuntu Installer Menu
    kernel vesamenu.c32
    append menus/ubuntu1.conf
label localboot
   MENU LABEL Boot off local hard disk (default)
   kernel chain.c32
   append hd0 0

```
Here could be an example Ubuntu preseed (i.e., automated install) menu:
```

label ubuntu-oneirc-amd64
MENU LABEL Ubuntu Oneiric 64-bit
kernel ubuntu/oneiric/amd64/linux
append vga=normal locale=en_US setup/layoutcode=en_US console-setup/layoutcode=us initrd=ubuntu/oneirc/amd64/initrd.gz preseed/url=http://192.168.1.35/ubuntu/oneiric/preseed.txt netcfg/get_hostname= -- quiet

```
... and, lastly, here's an example Oneiric preseed (e.g., preseed.txt file above): [http://help.ubuntu.com/11.10/installation-guide/amd64/preseed-contents.html]("http://help.ubuntu.com/11.10/installation-guide/amd64/preseed-contents.html")

That should get you started to understanding the nuts and bolts of how these basic PXE boot tools work.  Best of luck!

---

