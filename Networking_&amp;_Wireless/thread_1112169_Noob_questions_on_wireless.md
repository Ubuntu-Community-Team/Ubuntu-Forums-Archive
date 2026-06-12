---
title: "Noob questions on wireless"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by That Guy 2-1 on 2009-03-31
Okay so I get a bit creative when I installed Ubuntu 8.10 on my Toshiba Portage M200-S838.  Since the laptop doesn't have a CD-ROM, I took the formatted (using Fdisk on DOS through a boot Floppy image) HD out and put it in my Dell Laptop and used the Ubuntu CD to boot and install it into the HD.  Then switched it back to the Toshiba.  Now I didn't know all this would work when I did it (I've tried everything I could find info on and nothing worked up to this point), but it started up and runs better than it did when the HD was in the Dell unit.

So the LAN connection works for getting on the internet but I'd like to get the wireless card working.  I'm using a D-Link WNA-2330 card and I found that I can use ndiswrapper to run windows drivers and I installed the win2K driver though the GUI.  However, the drop down menu doesn't have the wireless network active and doesn't let me activate it because it's grayed out ... how do I activate wireless networking?  I looked at the tutorial ... [http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html) ... and done most of it but don't understand the part where it says "comment out ....".  How do you do that?  I'm not a programming type so I don't understand what that means and also how to create a file by a certain name; do I have to create it in a certain directory?  or do I just copy and paste that whole name when creating the file name? ... just a couple questions that I need clarification on 'cos I think that's where I get stuck and therefor I can't get to the next steps and do the re-start/etc.

Thanks for your help

---

### Post by chili555 on 2009-03-31
> Comment out everything other than “lo” entries in that file and save the fileThat means put a # in front of something so the system will ignore it. Thus:```
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth0
#iface eth0 inet dhcp
```Check your work, save and close.> Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the fileThat really means:```
sudo gedit /etc/default/wpasupplicant
```A text editor will pop up and you can type in your needed text:```
ENABLED=0
```Check, save and close.

If you have other questions, post back.

---

### Post by That Guy 2-1 on 2009-03-31
> **chili555 said:**
> That means put a # in front of something so the system will ignore it. Thus:```
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth0
#iface eth0 inet dhcp
```Check your work, save and close.That really means:```
sudo gedit /etc/default/wpasupplicant
```A text editor will pop up and you can type in your needed text:```
ENABLED=0
```Check, save and close.

If you have other questions, post back.thanks!  When I opened up that file, it didn't have the two extra sets of lines, only the first two ... could that be the reason my wireless isn't working?  Well, if we're commenting it out, I guess it doesn't matter now anyways.

I think the other issue I had was that I don't have the Network Manager in my list and something I read said it's just not shown there but was activated through the terminal?  WTF?

---

### Post by chili555 on 2009-03-31
Perhaps this will help: [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager)

---

### Post by That Guy 2-1 on 2009-04-01
thanks for all your help.  I was being an idiot and didn't realize that this laptop had a internal wireless card and it only needed to be turned on!!! DUH!  Turned it on and the wireless network was detected and etc.  :D

---

