---
title: "3G Modem K3770 Setup"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by SneakPeak on 2011-06-24
Hi,

I am running Ubuntu 11.04 on an external USB drive on a Dell D630 laptop.  

My issue is I can't get my 3G modem to work.  It is a K3770 Huawei modem.

When I plug it in after boot up it is not recognized at all as far as I can tell. (Which is not very far).

When I plug it in before boot up it shows up as a CD rom drive.  I have usb-modeswitch is installed. (It was installed by default during the 11.04 installation.)

I have searched for help on the forums but the posts get so complex so quickly I can't follow them.  Can anybody give a simple step by step guide on what to do to get this to work?  Remember my Ubuntu is running on an external USB drive so anything that switches USB off even temporarily won't work. (I don't think).

Thanks for your help

Adrian :(

---

### Post by alexfish on 2011-06-25
can try safely remove device from the Disk Utility or if the device is showing on the desktop, try right click and safely remove, does anything happen

also use the usb-devices command before and after the safely remove device
```
usb-devices
```
locate the lines which indicate the device and post only those lines

alexfish

---

### Post by SneakPeak on 2011-06-26
Thanks for the reply.

Unfortunately I am on holiday at the moment and I have no alternative connection to the 3G connection.  I am currently using my wife's windows PC to post this replay.  As soon as I want to try to trouble shoot the 3G modem on my machine I have no connection which is going to make this very difficult.

When the usb modem appears on my desktop as a CD drive I have no probelm unmounting it or safely removing it.  Trouble is after I have done that I still have no internet connection.  I can go into the network manager and create a 3G connection and tell it to connect automatically but it does nothing.  I assume it is doing nothting because it cant see the the 3G modem??

Adrian

---

### Post by alexfish on 2011-06-26
can try this when back

look here RE Post #30
[Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312") 
you will have to identify the device from lsusb command from the terminal
or can use the usb-devices command , this should show the device status , switched or unswitched + possible the driver status , although do know some laptops have usb configuration problems , can also check your bios settings, or try swapping to different usb port
also look sakis3g, worth having on the system, if sakis3g works
will then possibly look at other software options as regards Vodafone, i presume it is a Vodafone device from k3770

see what happens

alexfish

---

### Post by narcisgarcia on 2011-07-01
I'm trying to register this device in usb.ids :

```
12d1  Huawei Technologies Co., Ltd.
    14d1  K3770 USB Modem Stick HSDPA/HSUPA/WCDMA
```

Through [https://usb-ids.gowdy.us/](https://usb-ids.gowdy.us/) and/or [http://www.linux-usb.org/usb-ids.html](http://www.linux-usb.org/usb-ids.html)

I've sent the data by mail, to be included in future *update-usbids* and be listed as something like:
```
12d1:14d1 Huawei Technologies Co., Ltd. K3770 USB Modem Stick HSDPA/HSUPA/WCDMA
```

Note that this device has additional interface for MicroSD memory card, and seems to include some ROM part with Microsoft and Mac drivers.

(Another foruym thread about the same device: [http://ubuntuforums.org/showthread.php?p=11002456](http://ubuntuforums.org/showthread.php?p=11002456))

---

### Post by narcisgarcia on 2011-07-03
cre8or may have found a solution here:

[http://ubuntuforums.org/showthread.php?p=11005408](http://ubuntuforums.org/showthread.php?p=11005408)

---

### Post by kareempharmacist on 2011-10-14
It works perfectly and out-of-the-box on ubuntu 11.10 .....tried..all u have to do is to upgrade.
it works also on debian and any debian-based distribution.

---

### Post by SneakPeak on 2011-10-17
Thanks for the replies.  I should have marked this thread as solved a long time back. It slipped my mind completey.  I got my modem worknig no problem with Sakis3G.  I can't remember exactly the steps but it wasn't much more complicated than installing and following the Sakis3G instructions.  I have since bought a new Laptop and I installed 11.10 over the weekend.  I haven't gotten around to installing my 3G yet.  Will try this evening.

---

### Post by foxy123 on 2011-11-24
> **SneakPeak said:**
> Thanks for the replies.  I should have marked this thread as solved a long time back. It slipped my mind completey.  I got my modem worknig no problem with Sakis3G.  I can't remember exactly the steps but it wasn't much more complicated than installing and following the Sakis3G instructions.  I have since bought a new Laptop and I installed 11.10 over the weekend.  I haven't gotten around to installing my 3G yet.  Will try this evening.

was it successful?

---

### Post by SneakPeak on 2011-11-24
Yes it was.  Same procedure installed Sakis3G and followed the Sakis instructions.

---

### Post by foxy123 on 2011-11-25
> **SneakPeak said:**
> Yes it was.  Same procedure installed Sakis3G and followed the Sakis instructions.

So it wasn't working for you out of the box with 11.10? I mean through NetworkManager.

---

### Post by SneakPeak on 2011-11-25
That's right.  It didn't work out the box.  Once I had got it up and running once I managed to connect using Network Manager.  I guess Sakis3G changed some settings which I hadn't managed to get right by using Network manager only.  Sorry I am not being more specific.  I gave my 3G modem away and am using wireless as my main network connection now so I can't plug in my 3G again to give you a more detailed run down.

---

### Post by foxy123 on 2011-11-25
> **SneakPeak said:**
> That's right.  It didn't work out the box.  Once I had got it up and running once I managed to connect using Network Manager.  I guess Sakis3G changed some settings which I hadn't managed to get right by using Network manager only.  Sorry I am not being more specific.  I gave my 3G modem away and am using wireless as my main network connection now so I can't plug in my 3G again to give you a more detailed run down.

Cheers anyway!

---

### Post by narcisgarcia on 2011-11-29
These are the simplest ways I found to use this device on Ubuntu Natty.

**Method 1:** Terminal commands with the device already plugged
(this must be done on every session)
```
sudo usb_modeswitch -v 0x12d1 -p 0x14d1 -V 0x12d1 -P 0x14c9 -M 55534243123456780000000000000011062000000100000000000000000000
sudo modprobe usbserial vendor=0x12d1 product=0x14c9

```

**Method 2:** Upgrading packages from 11.10 (Oneiric) to do it automatic
[LIST=1]
[*]Uninstall the package usb-modeswitch-data
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch-data](http://packages.ubuntu.com/oneiric/usb-modeswitch-data)
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch](http://packages.ubuntu.com/oneiric/usb-modeswitch)
[/LIST]

---

### Post by foxy123 on 2011-12-01
> **narcisgarcia said:**
> These are the simplest ways I found to use this device on Ubuntu Natty.

**Method 1:** Terminal commands with the device already plugged
(this must be done on every session)
```
sudo usb_modeswitch -v 0x12d1 -p 0x14d1 -V 0x12d1 -P 0x14c9 -M 55534243123456780000000000000011062000000100000000000000000000
sudo modprobe usbserial vendor=0x12d1 product=0x14c9

```

**Method 2:** Upgrading packages from 11.10 (Oneiric) to do it automatic
[LIST=1]
[*]Uninstall the package usb-modeswitch-data
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch-data](http://packages.ubuntu.com/oneiric/usb-modeswitch-data)
[*]Install the next version package from [http://packages.ubuntu.com/oneiric/usb-modeswitch](http://packages.ubuntu.com/oneiric/usb-modeswitch)
[/LIST]

I wonder why it works for you on 11.04 using Oneiric packages but not for me on Oneiric. I have to use sakis3g to make it work.

---

### Post by Pyrosopher on 2011-12-05
I've been struggling with this for about three weeks, finally fixed it!

I've got a K3770 in the UK with Vodafone on a Pay-As-You-Go basis.

There are three hurdles I've had to overcome to get it to work on Oneric.

1) The mode-switching which has been covered nicely in this thread. (On  Natty I have to enter the commands in manually, I've not tried getting  the new data package. It is automatic on my Oneiric system)

2) Installing the package modem-manager:
[B]
sudo apt-get install modemmanager
  
[/B]Once this was installed the network manager started to pick up the USB automatically on Oneiric. Thanks to Alex22 from [http://ubuntuforums.org/showthread.php?t=1472896](http://ubuntuforums.org/showthread.php?t=1472896)

3) The automatic configuration for the modem has the wrong setting.  Anyone who knows who to inform, please do so. There are two ways to fix  this.

Once you've the device mode-switching and the modem manager installed,  the network manager should be picking up the existence of the device.  However, it will be greyed out and unselectable. This is because the  network manager knows it's there, has a signal, but doesn't know how to  connect. So, we set up a connection. There should be an option for  AutoConnect or something similar just beneath the Vodafone connection  that fires up a wizard. 

**The first way to get the right setting is to set it up right first time using a custom setup.**

Go through the wizard and choose "My plan is not listed". It will ask  you for the APN which is the "Access Point Name". This is the key  because **the wizard gets it wrong**. Enter the APN as **SMART**. 

You'll also need a username and password. **Both username and password are: web**

Now it should connect.

**The second way to get things right is to modify the configuration.**

Under Natty you go through the Wizard, choose the TopUp and Go option. Now choose "Edit Connections..." in the network manager change the APN from **ppbundle.internet** to **SMART**

The username and password are already in there and it should connect happily.

In Oneiric they've crippled the Network Manager, so you can't modify the setting easily. 

If you have chosen the TopUp and Go option, you'll need to:
**sudo gedit /etc/NetworkManager/system-connections/"Vodafone TopUp and Go"**

Again, just replace the text **ppbundle.internet** with **SMART**

Save and then restart network manager or your computer and you should be golden.

If you've tried one of the other configurations in the wizard and you have the Pay-As-You-Go USB, your best bet is to **sudo nautilus**  navigate to /ect/NetworkManager/system-connections/ and delete any  Vodafone entries. Now Network Manager should allow you to set up the  modem again from scratch. Use the first way I suggested to set up the  modem creating with the "My plan is not listed" option.

Thanks to everyone here for helping me to get this working. I hope pulling this together helps others.

---

### Post by foxy123 on 2011-12-10
> **Pyrosopher said:**
> I've been struggling with this for about three weeks, finally fixed it!

I've got a K3770 in the UK with Vodafone on a Pay-As-You-Go basis.

There are three hurdles I've had to overcome to get it to work on Oneric.

1) The mode-switching which has been covered nicely in this thread. (On  Natty I have to enter the commands in manually, I've not tried getting  the new data package. It is automatic on my Oneiric system)

2) Installing the package modem-manager:
[B]
sudo apt-get install modemmanager
  
[/B]Once this was installed the network manager started to pick up the USB automatically on Oneiric. Thanks to Alex22 from [http://ubuntuforums.org/showthread.php?t=1472896](http://ubuntuforums.org/showthread.php?t=1472896)

3) The automatic configuration for the modem has the wrong setting.  Anyone who knows who to inform, please do so. There are two ways to fix  this.

Once you've the device mode-switching and the modem manager installed,  the network manager should be picking up the existence of the device.  However, it will be greyed out and unselectable. This is because the  network manager knows it's there, has a signal, but doesn't know how to  connect. So, we set up a connection. There should be an option for  AutoConnect or something similar just beneath the Vodafone connection  that fires up a wizard. 

**The first way to get the right setting is to set it up right first time using a custom setup.**

Go through the wizard and choose "My plan is not listed". It will ask  you for the APN which is the "Access Point Name". This is the key  because **the wizard gets it wrong**. Enter the APN as **SMART**. 

You'll also need a username and password. **Both username and password are: web**

Now it should connect.

**The second way to get things right is to modify the configuration.**

Under Natty you go through the Wizard, choose the TopUp and Go option. Now choose "Edit Connections..." in the network manager change the APN from **ppbundle.internet** to **SMART**

The username and password are already in there and it should connect happily.

In Oneiric they've crippled the Network Manager, so you can't modify the setting easily. 

If you have chosen the TopUp and Go option, you'll need to:
**sudo gedit /etc/NetworkManager/system-connections/"Vodafone TopUp and Go"**

Again, just replace the text **ppbundle.internet** with **SMART**

Save and then restart network manager or your computer and you should be golden.

If you've tried one of the other configurations in the wizard and you have the Pay-As-You-Go USB, your best bet is to **sudo nautilus**  navigate to /ect/NetworkManager/system-connections/ and delete any  Vodafone entries. Now Network Manager should allow you to set up the  modem again from scratch. Use the first way I suggested to set up the  modem creating with the "My plan is not listed" option.

Thanks to everyone here for helping me to get this working. I hope pulling this together helps others.

Thanks a lot! Works like a charm.

---

