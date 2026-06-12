---
title: "edimax ew 7711utn"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Pink October on 2009-11-14
Has anyone managed to get the above wireless adaptor running on ubuntu? How did you get it working???

Also does anyone know of any better wireless adaptors that have been confirmed as working in Ubuntu? Only got the wireless adaptor 2 weeks ago and if I can't get it working I'll have to return it. It does say that it's linux compatible, obviously just doesn't like me!!:mad:

---

### Post by markhepworth on 2010-01-15
You've probably returned it to the shop by now, but for the record, it works in Karmic by following
> 
On the main menu at the top of the screen:
Click Applications -> Accessories -> Terminal

In terminal:
     Code:
     sudo gedit /etc/modprobe.d/blacklist.conf 
add these lines to the end of the file:
     Code:
     blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist ndiswrapper 
Save the file, then insert your USB wifi device.
Note that ndiswrapper was blacklisted. If in the future you wish to use it, remember this.from [http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870](http://ubuntuforums.org/showthread.php?t=1342593&highlight=rt2870)

---

### Post by duncanmaybury on 2010-02-19
Hi Mark

This is all new to me as I am new to Linux. I have one of the these 7711utn sticks coming to me. I want it to work in Karmic. I have had a look around and on the Hardware support page [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax") it says that this hardware uses the rt2800 chipset, On the code you have given it say to black list rt2800usb, Is this correct? If so why, what does it use instead?
Have you succeeded using what you have posted, did you do anything else?

Thanks

---

### Post by duncanmaybury on 2010-02-19
Just a quick note to say thanks, I did what was said above and it worked. Great.;)

---

### Post by Spabuntu on 2010-03-07
cheers, worked perectly!

---

### Post by EarthMind on 2010-03-23
Is there any more info on this? 

I tried the above but my EW-7711UTn USB adapter refuses to work; no wireless networks are shown in the network manager.

---

### Post by pdc on 2010-03-23
if you copy and paste this command into a terminal

> gedit /etc/modprobe.d/blacklist.conf 

and if you copy and paste all the results back here please

---

### Post by EarthMind on 2010-03-24
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist ndiswrapper 

```

I also tried after compiling & installing the latest driver from the ralink website. I was able to connect to unprotected networks then but I couldn't connect to my WPA2 protected network, it kept repetitively asking for the password, while I had entered the correct one.

Other details:
kernel version: 2.6.31-20

---

### Post by EarthMind on 2010-04-30
Also doesn't work in Lucid :(

I don't get it, it works and has always worked in every Mandriva One release I tried :(...

---

### Post by combinekidd on 2010-05-02
> **EarthMind said:**
> 

I also tried after compiling & installing the latest driver from the ralink website. I was able to connect to unprotected networks then but I couldn't connect to my WPA2 protected network, it kept repetitively asking for the password, while I had entered the correct one.

Other details:
kernel version: 2.6.31-20

I have exactly the same problem as you, I've been trying two days now, any luck yet? I could connect to the same connection on the computer when Windows was installed.

---

### Post by EarthMind on 2010-05-03
Unfortunately no solution yet to get this adapter to work.

I've also searched for other (read: more popular) adapters that use the same chipset as our adapter but I haven't found any yet that I'm certain of that they have the same chipset.
I'm also going to try to find out why it does always work in Mandriva One, while it uses the same kernel as Ubuntu 9.10 & OpenSUSE 11.2. Maybe they use a different driver or maybe it's a 64 bit issue as Mandriva One is only available as 32 bit.

This is a very time consuming task...

---

### Post by danhilu on 2010-05-03
Hi,
below my experience, which I am sharing first because I'm Happy my wife's PC now can connect and second in the hope this will help someone else. Please apologize in case my post is not adding value.
Thanks to cyberhood and chili555 for their help on post "http://ubuntuforums.org/showthread.php?t=1444420". My single contribution here is to have made the effort to go through the 10 pages of this thread. Thanks again for the linux and ubuntu community ! 


1. My config:
-------------
Toshiba laptop Satellite Pro Pentium 4
Xubuntu 9.10 karmic kernel 2.6.31-21-generic
Wifi USB key "Edimax EW-7711UTn"

2. What I have done:
--------------------
```
sudo mousepad /etc/modprobe.d/blacklist.conf
```

-> added those 5 lines at the end of /etc/modprobe.d/blacklist.conf :
```
# Excellent fix from cyberhood and chili555 
# see http://ubuntuforums.org/showthread.php?t=1444420
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
```

(note up to now it's almost same as the proposal from markhepworth at the begining of this thread)

Then I have done the vodoo below:
```
~$ sudo su
# echo rt2870sta >> /etc/modules
# exit
exit
```

I might have typed before 
```
sudo modprobe rt2870sta
``` (although I dont know if needed)

Then I've rebooted and .. it works !!


3. What has changed:
--------------------
I now can see the list of available wifi networks by left clikcking on the "NetworkManager" applet !
And I can access my network !!

---

### Post by EarthMind on 2010-05-03
Kind thanks for the additional information. I'll try it out as soon as I can.

---

### Post by Crestopher on 2010-06-09
> **danhilu said:**
> Hi,
below my experience, which I am sharing first because I'm Happy my wife's PC now can connect and second in the hope this will help someone else. Please apologize in case my post is not adding value.
Thanks to cyberhood and chili555 for their help on post "http://ubuntuforums.org/showthread.php?t=1444420". My single contribution here is to have made the effort to go through the 10 pages of this thread. Thanks again for the linux and ubuntu community ! 


1. My config:
-------------
Toshiba laptop Satellite Pro Pentium 4
Xubuntu 9.10 karmic kernel 2.6.31-21-generic
Wifi USB key "Edimax EW-7711UTn"

2. What I have done:
--------------------
```
sudo mousepad /etc/modprobe.d/blacklist.conf
```-> added those 5 lines at the end of /etc/modprobe.d/blacklist.conf :
```
# Excellent fix from cyberhood and chili555 
# see http://ubuntuforums.org/showthread.php?t=1444420
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
```(note up to now it's almost same as the proposal from markhepworth at the begining of this thread)

Then I have done the vodoo below:
```
~$ sudo su
# echo rt2870sta >> /etc/modules
# exit
exit
```I might have typed before 
```
sudo modprobe rt2870sta
``` (although I dont know if needed)

Then I've rebooted and .. it works !!


3. What has changed:
--------------------
I now can see the list of available wifi networks by left clikcking on the "NetworkManager" applet !
And I can access my network !!

WOW!!! WORKS JUST FINE!!! THANK YOU SO MUCH!!! :p

---

### Post by cramie10 on 2010-08-31
Absolutely fantastic. Worked fine. I think its just the blacklists required as I couldn't complete the other commands and on re-boot it worked. Fantastic!

---

### Post by ssam on 2010-09-25
works out of the box in maverick (on x86-64 and ARM :-) ). make sure you have the linux-firmware package install (usually installed by default)

---

### Post by kihon on 2011-05-20
Has anyone been having problems with 11.04? Especially when set to manual IP address, it seems very hit and miss whether or not the card will scan and connect to networks.

---

