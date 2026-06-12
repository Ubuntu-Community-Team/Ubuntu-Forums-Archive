---
title: "wireless card not detected ubuntu in vm!"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by totallynew on 2010-11-16
sorry for the totally no clue what i'm doing but here goes
i'm running ubuntu in vm box
all seems good have internet access etc
now i have a wireless card i want working (netgear wg311 v2) its working in the windows enviroment.
but doing all (maybe not all) terminal commands to see if its there in ubuntu do not show it.
have you any tips
tia
i post i saw mentioned even pci bridge error from bios!! ??

---

### Post by uncaspi on 2010-11-16
Open a terminal and post the output of sudo lshw -C network or
sudo /sbin/lshw -C network

---

### Post by totallynew on 2010-11-17
just lists the ethernet interface i.e lan port on eth0
copy and paste dont work ubuntu to pc :(
only other note is warning should run as superuser

---

### Post by uncaspi on 2010-11-17
Well it don't see your hardware in lshw. Is it a build in card or an usb stick?

---

### Post by totallynew on 2010-11-17
its pci device (netgear wg311 v2)

---

### Post by uncaspi on 2010-11-17
Well ok it's not detected in lshw so if it's a desktop computer you had to check if the card is properly plugged into the slot. IF it works in windows it is. There is not much you can do if it's not showing up in lshw.

---

### Post by totallynew on 2010-11-17
has to be.
someone suggested the pci bridge is the problem ? no driver or not configured right

---

### Post by totallynew on 2010-11-17
would the chances be increased if i boot to ubuntu as a proper os?

---

### Post by uncaspi on 2010-11-17
I don't know.

---

### Post by totallynew on 2010-11-17
where are the genius's when you need them lol

---

### Post by stefangr1 on 2010-11-17
> **totallynew said:**
> sorry for the totally no clue what i'm doing but here goes
i'm running ubuntu in vm box
all seems good have internet access etc
now i have a wireless card i want working (netgear wg311 v2) its working in the windows enviroment.
but doing all (maybe not all) terminal commands to see if its there in ubuntu do not show it.
have you any tips
tia
i post i saw mentioned even pci bridge error from bios!! ??

VMware cannot access the physical PCI hardware on the host! If you wan't to use this wireless card from the VM directly (for example to run aircrack-ng), it just can't be done. You would need an usb wifi card for that.

If you just wan't your VM to access the internet, it's not that difficult. You need to change your VM's configuration from "bridged" (which is default) to "NAT". That way, the VM isn't directly connected to the internet, but to a virtual LAN (that even has it's own DHCP server) that uses the connection of the host as a gateway.

---

### Post by totallynew on 2010-11-17
thx stef
so can i install ubuntu as a os? and it will work then?
i have a 750meg odd iso can i use that to install it?

---

### Post by stefangr1 on 2010-11-17
> **totallynew said:**
> thx stef
so can i install ubuntu as a os? and it will work then?

I'm not entirely sure about what you intend to do.

Let me start by stating that you can use VMware only to get a general impression of Ubuntu. You can't use it as a check to whether your hardware is supported, because VMware emulates all hardware. Also, graphical and IO performance will be a lot better when Ubuntu is run on the hardware directly.

To test whether your hardware is supported properly, you can download a Live CD. You can run Ubuntu from it (not very fast, btw.), and it won't touch your current windows installantion at all. If your wireless works from the Live CD, you're good. Otherwise, it's probably possible to get your PCI wireless working manually, but this can be quite complex.

> i have a 750meg odd iso can i use that to install it?

Sorry, but I don't know what a 750MB odd ISO is. Can you explain?

If you want a dual boot system: this can be done without trouble. Just be sure to make a good backup, as the system might propose to shrink your current windows partition, and that's a risky procedure.

---

### Post by totallynew on 2010-11-17
i can install ubuntu on a spare harddrive or even a partition if i wanted.
the iso is ubuntu i guess. just needs ripping to a cd then i can install from there
so i was asking if i have a purely ubuntu os/desktop i will more than likely get my pci wireless working?

---

### Post by grahammechanical on 2010-11-17
Did you put the wireless card into the computer after you installed Ubuntu into the VM box? If so, then Ubuntu does not know if a wireless card exists. Does VMware recognize the existence of a wireless card? 

regards.

---

### Post by totallynew on 2010-11-17
no the wireless card was already installed (under windows)
how do i get vm ware to look?
edit to add: ah i see. vm only lists "adapter1:" lan port

---

### Post by totallynew on 2010-11-17
ok maybe some progress. before entering ubuntu using the vm tools i added the wireless card (i think)
i now have a lan and wlan listed in vm ware
so started ubuntu and lshw -c network now reveals 2 adapters
doesn't actually say wireless but both "ethernet interface" eth0 and eth1
good?
they have different bus info,physical id,serial,IRQ and memory addy's
but the product is the same? 82540EM gigabit eternet controller
in ubuntu network connections i have 2 wired listed Auto eth0 and Auto eth1
i have a wirless entry in the wirless tab altho i think i added that trying to get it to work

---

### Post by grahammechanical on 2010-11-17
The wireless card is actually an ethernet device. The ethernet cable is replaced by a wireless transmitter/receiver. So, you are making progress. Where to go from here I do not know? Have you tried accessing the network icon? Is there a tick mark against enable networking and enable wireless? If not, click them with the mouse. Is there a list of available wireless networks? Can you see your wireless network? If so, click on it and enter the wireless key. Not your login password. I am sorry if I am assuming that you do not know what you are doing. I thinnk that it is better to do that then tell you to do things that you do not understand.

If Windows is giving you a wireless connection then the VM should be using that to make a wireless connection available to Ubuntu. 

I have only tested a virtual machine on a Ubuntu installation and I installed Ubuntu onto it. I was using 64bit Ubuntu and I wanted a 32bit version so I could view television programs through the Internet. At the time there was only a 32bit version of Flash player working. I had no problems accessing the Internet through a version of Ubuntu in a virtual machine on a Ubuntu installation. It should be possible to do the same when the host is Windows.

regards.

---

### Post by stefangr1 on 2010-11-17
> **totallynew said:**
> ok maybe some progress. before entering ubuntu using the vm tools i added the wireless card (i think)
i now have a lan and wlan listed in vm ware
so started ubuntu and lshw -c network now reveals 2 adapters
doesn't actually say wireless but both "ethernet interface" eth0 and eth1
good?
they have different bus info,physical id,serial,IRQ and memory addy's
but the product is the same? 82540EM gigabit eternet controller
in ubuntu network connections i have 2 wired listed Auto eth0 and Auto eth1
i have a wirless entry in the wirless tab altho i think i added that trying to get it to work

Sorry to say, but these attempts to get a PCI wireless NIC working in VMware are really a waste of time, as VMware doesn't support raw PCI access.

If you do a real Ubuntu install, it's very likely that it's possible to get your wireless working eventually (did a quick check on google), but I't may be difficult if it's not supported out of the box. You can use the Live CD (you probably have it already, it has "desktop" in it's filename) to check whether your wifi card works out of the box.

---

### Post by totallynew on 2010-11-17
cheers stef think your right
i read it is a works out the box device!
for the hassle and a tenna might just get a usb stick

---

