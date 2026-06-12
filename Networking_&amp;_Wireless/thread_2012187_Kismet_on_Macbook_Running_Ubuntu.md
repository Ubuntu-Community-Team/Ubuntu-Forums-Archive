---
title: "Kismet on Macbook Running Ubuntu"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by BilliardX on 2012-06-28
After installing Kismet, I received an initial message stating "FATAL: Please configure at least one packet source.  Kismet will not  function if no packet sources are defined in kismet.conf or on the  command line.  Please read the README for more information about  configuring Kismet."

I have been attempting to configure my kismet.conf doc so that it will run on my macbook, however I am having some trouble with getting the conf setup correctly. Here is my conf currently...

------

# User to setid to (should be your normal user)
suiduser=ghost

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=wl0,eth1,broadcom

------

Here is my wireless card information...

-----

*-network               
       description: Ethernet interface
       product: MCP89 Ethernet
       vendor: nVidia Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: a1
       serial: e8:06:88:e2:90:46
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:40 memory:93286000-93287fff ioport:22a0(size=8)
  *-network
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 60:33:4b:1a:ee:1c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=10.0.1.19 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:23 memory:93100000-93103fff

--------

Can anyone give me a hand with this? I just cant seem to get it to work correctly. I keep getting an error saying "FATAL: Unknown capture source type 'wl0' in source 'wl0,eth1,broadcom" when I try to run it.

Thanks!

---

### Post by chili555 on 2012-06-28
I am not at all sure that the Broadcom STA driver, wl can actually do monitor mode which is required by Kismet. However, you have evidently volunteered to be our test pilot, so hook up your safety belts. Here we go!

I noticed this in the readme for the driver located at /usr/share/doc/broadcom-sta-source/README.txt.gz:> HOW TO USE MONITOR MODE
-----------------------
To enable monitor mode:
$ echo 1 > /proc/brcm_monitor0

Enabling monitor mode will create a 'prism0' network interface. Wireshark and
other netwokk tools can use this new prism0 interface.

To disable monitor mode:
$ echo 0 > /proc/brcm_monitor0I believe Kismet is one of the referenced 'netwokk' tools. In order to try this, I suggest you change your kismet.conf to amend:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=wl,prism0,Broadcom
```Now let's follow the readme:```
sudo su
echo 1 > /proc/brcm_monitor0
exit
```Did it create the interface?```
ifconfig
iwconfig
```If so, start Kismet:```
sudo kismet
```Any improvement?

---

### Post by BilliardX on 2012-06-28
I attempted the echo after making the necessary changes to the source, however it could not find the directory. I also tried to run Kismet after making the change, however it responded saying that "wl" was an unknown capture source. 

I'm not really sure how to go about fixing this :D

---

### Post by chili555 on 2012-06-28
> echo 1 > /proc/brcm_monitor0Is there anything like that in /proc?```
ls /proc | grep brcm
```All I can do, without the device, is read the README.

---

### Post by chili555 on 2012-06-28
Please see: [http://wiki.debian.org/wl/](http://wiki.debian.org/wl/)> Monitor mode is not supported prior to driver version *5.100.82.111*.

    Testing users, see /usr/share/doc/broadcom-sta-{dkms,source}/README.txt.gz to enable. I believe the version in Ubuntu 12.04 is 5.100.82.38. We will need to compile from source code in order to proceed. Are you strapped in and ready? If so, please do:```
sudo apt-get install linux-headers-generic build essential
```I will be back in a few minutes with the remainder.

EDIT: The build is messy, but do-able. Please do:```
sudo apt-get build-dep linux
```Go here and download either the 32- or 64-bit version as needed. Drag and drop it to your desktop. Right-click it and select *Extract Here*. Open the folder and drill down to src > wl > sys and open the file wl_linux.c with any text editor such as gedit. Go down to line 388 (at least on the 32-bit version) and find this line:```
.ndo_set_multicast_list = wl_set_multicast_list,
```Change it to read:```
.ndo_set_rx_mode = wl_set_multicast_list,
```Spacing, punctuation, etc. are crucial. Proofread carefully, twice, save and close the text editor.

Now open a terminal and do:```
cd Desktop/hybrid-portsrc_x86_32-v5_100_82_112/  [COLOR="Red"]<--or x86_64 as needed[/COLOR]
make
modinfo wl
```Make note of where the current version is located; on my system it's /lib/modules/3.2.0-25-generic-pae/updates/dkms. We are going to move the older version out of the way:```
sudo mv /lib/modules/3.2.0-25-generic-pae/updates/dkms/wl.ko /lib/modules/3.2.0-25-generic-pae/updates/dkms/wl.old
```And copy over the new version:```
sudo cp wl.ko /lib/modules/3.2.0-25-generic-pae/updates/dkms
```Of course, substitute your exact location.

Now unload and reload the driver:```
sudo modprobe -r wl
sudo modprobe wl
```Can you monitor and kismet now?

Whew!!

---

### Post by BilliardX on 2012-06-28
Thanks for the help Chili! I looked through the proc folder and I dont see any file or folder named or including brcm.

I will go ahead and dl/install the file you listed now.

*Edit*

I attempted the download however I received an error:

sudo apt-get install linux-headers-generic build essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'build' has no installation candidate
E: Unable to locate package essential

---

### Post by BilliardX on 2012-06-28
Working on the new build I'll let you know how it goes.

Thanks!

---

### Post by BilliardX on 2012-06-28
Alright so I ran into a problem almost half way through.

I pulled the file entitled "bcmwl-5.100.82.38+bdcom" onto my desktop and went to the specified file where I made the necessary changes via copy paste (i think it was on line 322). After saving I attempted the cd bash but the file was not found. I also search my desktop for any file including hybrid-portsrc but nothing was found. I don't mean to be a pain, I am not as versed in linux and ubuntu as I should be :p. 

Any ideas?

---

### Post by chili555 on 2012-06-28
> I pulled the file entitled "bcmwl-5.100.82.38+bdcom"oh, noooooo!

At the site I thought I linked, you want 5.100.82.[COLOR="Red"]112[/COLOR]. Remember, monitor mode was introduced with x.100. Your x.38 won't work.

[http://www.broadcom.com/support/802.11/linux_sta.php/](http://www.broadcom.com/support/802.11/linux_sta.php/)

I apologize if I failed Link 101. It's late.

---

### Post by BilliardX on 2012-06-29
I'm still getting an unknown source fatal error when I try to run kismet. I think I am going to give up for the time being and have someone look at the computer in person. I think I won't be able to get it up and running without someone looking at it. 

Thanks for all your help!

---

