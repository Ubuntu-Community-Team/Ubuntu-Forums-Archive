---
title: "Installing rpm files"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by tripathi93 on 2009-05-22
Howdy!!!!!!
I'm just a 2 day transfer from windows to kubuntu 9.04......
My questions might sound foolish but help this new guy in need!please!!!!!!!!!!

I'm facing two problems..........

1.installing rpm files
->when i open this files and click install.it says 'unknown error' and even can't look into details..................


2.my isp provider gave me a bunch of settings.
Ip,subnet mask,default gateway,preferred dns,alternate dns.............
Help me apply this setting..........
I'm a complete new-bee!!!


I really appreciate ubuntu for such a good-looking and working free & open-source software...............
I have already recommended it to all my friends (more than 100 people) 

i'm now on a dual oper.system. Due to my non-internet connectivity in kubuntu. I'm now using windows with kubuntu 9.04.i'm using windows to connect to internet

---

### Post by chili555 on 2009-05-22
> 1.installing rpm filesAre you sure you really want to do this? rpm files are usually built for the peculiarities of Red Hat-based systems, just as deb files are built for Debian-based systems, including Ubuntu. To put it another way, I suppose you could jam a Mercedes engine into your BMW with enough adapters and reverse engineering, but why?

Just about any program you can think of, and a lot that you can't even imagine, is in the Ubuntu repositories, available in System -> Administration -> Synaptic. If you have a specific need that is not available in Synaptic, post back and we'll help you.> Ip,subnet mask,default gateway,preferred dns,alternate dns.In the Network Manager icon at the top right, you should be able to drill down and edit your connection, select Manual and enter those details. 

If this is a stay at home computer that never goes down to the cybercafe where you need to select a different wireless network, then you probably don't need Network Manager and can safely remove it through Synaptic. Then set your details by opening a terminal and doing:```
sudo gedit /etc/network/interfaces
```Edit it to look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address <IP address>
netmask <netmask address>
gateway <gateway address>
```Proofread twice, save and close gedit. Then do:```
sudo gedit /etc/resolv.conf
```Make it look like this:```
nameserver <primary DNS>
nameserver <secondary DNS>
```Proofread twice, save and close gedit. Substitute your details here. This assumes the interface you are using is eth0, your wired ethernet interface. Then do:```
sudo /etc/init.d/networking restart
```

Post back if you get stuck.

---

### Post by tripathi93 on 2009-05-22
> **chili555 said:**
> Are you sure you really want to do this? rpm files are usually built for the peculiarities of Red Hat-based systems, just as deb files are built for Debian-based systems, including Ubuntu. To put it another way, I suppose you could jam a Mercedes engine into your BMW with enough adapters and reverse engineering, but why?

Just about any program you can think of, and a lot that you can't even imagine, is in the Ubuntu repositories, available in System -> Administration -> Synaptic. If you have a specific need that is not available in Synaptic, post back and we'll help you.In the Network Manager icon at the top right, you should be able to drill down and edit your connection, select Manual and enter those details. 

If this is a stay at home computer that never goes down to the cybercafe where you need to select a different wireless network, then you probably don't need Network Manager and can safely remove it through Synaptic. Then set your details by opening a terminal and doing:```
sudo gedit /etc/network/interfaces
```Edit it to look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address <IP address>
netmask <netmask address>
gateway <gateway address>
```Proofread twice, save and close gedit. Then do:```
sudo gedit /etc/resolv.conf
```Make it look like this:```
nameserver <primary DNS>
nameserver <secondary DNS>
```Proofread twice, save and close gedit. Substitute your details here. This assumes the interface you are using is eth0, your wired ethernet interface. Then do:```
sudo /etc/init.d/networking restart
```

Post back if you get stuck.
A great thanks to you,"chili555"....
Thank you for considering my problem & helping me with writing with such vast specifications. I needed this!!!
I want to install 'rpm' files coz my internet connection requires ISP software log-in.ISP provider even provides a 'install.sh' for installing the log-in software but when i double click it nothing happens.The software comes bundled with a bunch of files too.
I will try the above way and hope it works...............

[B][I][U][COLOR="DarkOrange"]"Great people make linux,
People like you make it work"

[/COLOR][/U][/I][/B]

----------------------------------------------THANK YOU...........

---

### Post by The Recorder on 2009-05-23
The install.sh file might not be working because of permissions on the file.  As root, open up "Dolphin" (kdesu dolphin), and right-click on "Properties" - Click on the "Permissions" tab.  First, make sure that the "Is executable" is checked in "Permissions".  Next, run the file in a terminal, in the directory where the "install.sh" is located; if it's a root file, run it as root (sudo install.sh).  This will either work, or come back with some (perhaps vague) statements on why it didn't work.

Good luck!

---

### Post by Chemical Imbalance on 2009-05-23
.rpm packages are for other linux distros like Fedora and Mandriva, etc...

Ubuntu uses a variant of package called .deb

---

### Post by chili555 on 2009-05-23
> ISP provider even provides a 'install.sh'The usual way to run these is drag and drop the file, and all the ancillary files to a new directory in your /home/user direstory, and then in a terminal:```
sudo chmod +x install.sh
sudo ./install.sh
```Jot down any errors so we can all troubleshoot them. You might also reply and attach the install.sh so we can see what it is trying to do.

There is a program called *alien* that is supposed to convert alien packages to .deb files (and vice versa). It comes with quite a stack of dependencies:```
debhelper gettext html2text intltool-debian libbeecrypt6 libmail-sendmail-perl librpm4.4 libsys-hostname-long-perl po-debconf rpm
```You might open System -> Administration -> Synaptic and select Settings -> Repostitories. Add the installation CD. See if you can install *alien* from the CD.

---

### Post by radi0j0hn on 2009-05-29
In some cases, a deb package is not available.  For example, my copy of VMware is an RPM.

Alien is supposed to convert these, right?

---

### Post by chili555 on 2009-05-29
> Alien is supposed to convert these, right?Yes, indeed, however, not always perfectly. Read the man pages, however it should be as simple as:```
sudo alien -d package.rpm
```If you want to install it immediately:```
sudo alien -di package.rpm
```

---

