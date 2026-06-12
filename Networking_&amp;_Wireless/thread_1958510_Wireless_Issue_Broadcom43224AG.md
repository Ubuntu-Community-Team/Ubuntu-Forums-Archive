---
title: "Wireless Issue Broadcom43224AG"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by pinkpanther1569 on 2012-04-14
[FONT=Arial Narrow][SIZE=3]New to Ubuntu...[/SIZE][/FONT]
[FONT=Arial Narrow][SIZE=3]Unable to view wireless NIC. HP Probook 6540b with Broadcom 43224AG 802.11a/b/gn-draft WiFi adapter. When I enter ifconfig, I am only able to view eth0 and loopback. [/SIZE][/FONT]

---

### Post by chili555 on 2012-04-14
Is ndiswrapper installed on your system? Please open a terminal and run:```
ndiswrapper -v
```Also, run and post here:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by pinkpanther1569 on 2012-04-14
[EMAIL="lg@LG-STATION3:~$"]l[/EMAIL]ndiswrapper was not running, but after performing the second command piped with grep nothing occcurred.  (Things that make you go hmm...)
 
[EMAIL="lg@LG-STATION3:~$"]lg@LG-STATION3:~$[/EMAIL] ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
[EMAIL="lg@LG-STATION3:~$"]lg@LG-STATION3:~$[/EMAIL] sudo apt-get install ndiswrapper-common
[sudo] password for lg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 20 not upgraded.
Need to get 21.7kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main ndiswrapper-common 1.54-2ubuntu1 [21.7kB]
Fetched 21.7kB in 0s (40.4kB/s)       
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 153317 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.54-2ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.54-2ubuntu1) ...

---

### Post by chili555 on 2012-04-14
> after performing the second command piped with grep nothing occcurred. (Things that make you go hmm...)Hmmmm, indeed! Let's dig deeper:```
lspci -nn
lsusb
```I'll prepare myself a headache remedy...

---

### Post by pinkpanther1569 on 2012-04-14
This is worst that than the Tylenol Ban of 2010... Here you go!  Remedy this?
 
g@LG-STATION3:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02)
00:01.0 ISA bridge [0601]: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] [8086:7000]
00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:02.0 VGA compatible controller [0300]: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter [80ee:beef]
00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
00:04.0 System peripheral [0880]: InnoTek Systemberatung GmbH VirtualBox Guest Service [80ee:cafe]
00:05.0 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 01)
00:06.0 USB Controller [0c03]: Apple Computer Inc. KeyLargo/Intrepid USB [106b:003f]
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
00:0d.0 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
[EMAIL="lg@LG-STATION3:~$"]lg@LG-STATION3:~$[/EMAIL] lsusb
Bus 001 Device 002: ID 80ee:0021  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[EMAIL="lg@LG-STATION3:~$"]lg@LG-STATION3:~$[/EMAIL]

---

### Post by pinkpanther1569 on 2012-04-14
[SIZE=2]Oh, I am running Ubuntu 10.04 TLS via VirtualBox..[/SIZE]

---

### Post by chili555 on 2012-04-14
I just don't see any Broadcom anything nor any wireless anything. It isn't PCMCIA, is it? ISA?? SCSI???

Broken?

---

### Post by pinkpanther1569 on 2012-04-14
I don't think it is broken since I am connected wirelessly on my home network.  I think the 'operator' is broken (me). 
 
I have selected the 'Bridged' option as well. It is showing on under my network adapters via VirtualBox.
 
Can you recommend how I can install the driver?

---

### Post by pinkpanther1569 on 2012-04-14
My adapter is a Broadcom PCI

---

### Post by chili555 on 2012-04-14
> I have selected the 'Bridged' option as well. It is showing on under my network adapters via VirtualBox. Can you recommend how I can install the driver?Drive what? I see no hardware to marry the software and connect. If you are using the bridged option, isn't an interface br0 simply using the host computer's network connection no matter what it is?

I am not very familiar with Virtual Box. The few times I've tried it, it just worked with no fiddling.> Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02)Are these in fact dummy devices set up by VB? 440FX is pretty old stuff, circa 1996.

---

### Post by pinkpanther1569 on 2012-04-14
I agree there is no hardware to marry the software with.  I want to install a hardware driver for my wireless NIC.
 
No worries...Virtual Box is new to me as well.  
But perhaps this will help.
 
With bridged networking, VirtualBox uses a device driver on your *host* system that filters data from your physical network adapter. This driver is therefore called a "net filter" driver. This allows VirtualBox to intercept data from the physical network and inject data into it, effectively creating a new network interface in software. When a guest is using such a new software interface, it looks to the host system as though the guest were physically connected to the interface using a network cable: the host can send data to the guest through that interface and receive data from it. This means that you can set up routing or bridging between the guest and the rest of your network.
For this to work, VirtualBox needs a device driver on your host system.

---

### Post by chili555 on 2012-04-14
> For this to work, VirtualBox needs a device driver on your ***host*** system.Well, if you are posting wirelessly from the *host*, then you have that, correct?

Did you see this?  [https://help.ubuntu.com/community/VirtualBox/Networking](https://help.ubuntu.com/community/VirtualBox/Networking)> Wireless Networking

Setting up a normal bridged network generally doesn't work if you're bridging from a wireless card to VirtualBox. A simple script that utilises the parprouted tool will allow your VM full access to the wireless network.

You will require parprouted to do this:

*sudo apt-get install parprouted*

Next, using your favorite text editor, create and edit the script, for example:

*sudo nano /etc/network/if-up.d/vbox_network*

Then, enter the script (replacing $USER with your username (or whoever you intend to run virtualbox as)). Replace wlan0 with the name of your wireless interface. Use an available IP address on your network for tap0 (I have used 192.168.1.100 in this case): 

<snip>

---

### Post by pinkpanther1569 on 2012-04-14
I agree with you, but I am completely stuck on how to install the driver. I searched and have installed b43-fwcutter.  No luck!

---

### Post by chili555 on 2012-04-14
> I searched and have installed b43-fwcutter.On the host? Why if your host wireless is working?

On the guest? I don't see any device to use it on. I repeat:> Setting up a normal bridged network generally doesn't work *if you're bridging from a wireless card* to VirtualBox.

---

### Post by pinkpanther1569 on 2012-04-14
I parpouted and created the script and still no luck.

---

### Post by chili555 on 2012-04-14
I'm sorry. You are in Virtual Box territory and my specialty is wireless networking. I'd ask over on General Help and include Virtual Box in the thread title. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I regret I can't be of more assistance.

---

### Post by westie457 on 2012-04-14
Hi If as chilli555 has already asked your wifi is working with the host operating system there is no need to get it to work with the guest OS. Change the Network settings of the guest OS to 'NAT' as in the attached screenshot

---

