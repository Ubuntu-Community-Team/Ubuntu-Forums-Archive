---
title: "No wireless or wired connection after upgrade"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by WolfgangInSummit on 2013-02-05
I'm new-ish to Ubuntu. After an update yesterday, I have lost the ability to connect to the internet.
Here is what I've got: Dell Inspiron 6400 with Ubuntu 12.04.1
After "lspci -nn":\
.
.
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
.
.
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 
I've tried a few problem solving solution posted on this forum to no avail. I am stuck.
Wireless never worked but Ethernet did. I would like to get both working. Any ideas?

---

### Post by bkratz on 2013-02-05
> **WolfgangInSummit said:**
> I'm new-ish to Ubuntu. After an update yesterday, I have lost the ability to connect to the internet.
Here is what I've got: Dell Inspiron 6400 with Ubuntu 12.04.1
After "lspci -nn":\
.
.
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
.
.
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
 
I've tried a few problem solving solution posted on this forum to no avail. I am stuck.
Wireless never worked but Ethernet did. I would like to get both working. Any ideas?



It is really hard when both are down!  Anyway, I think we should try to get the ethernet first. This may work or not, but just temporarily anyway ( until the next reboot).

Try,

sudo modprobe b44

and see if the internet is back, if so we will work on the wireless.

---

### Post by WolfgangInSummit on 2013-02-05
Thank you bkratz!
I've typed in "sudo modprobe b44", I was then prompted for my password which I typed in. Then, a white rectangle appeared blinking and then it was solid. I hit "return" and the white rectangle just moves down. Nothing else happens, except that it was blinking a bit and then stopped.
 
What would you suggest I tried next?

---

### Post by bkratz on 2013-02-05
> **WolfgangInSummit said:**
> Thank you bkratz!
I've typed in "sudo modprobe b44", I was then prompted for my password which I typed in. Then, a white rectangle appeared blinking and then it was solid. I hit "return" and the white rectangle just moves down. Nothing else happens, except that it was blinking a bit and then stopped.
 
What would you suggest I tried next?


Since you said you have tried several things we should make sure that the blacklisted drivers are correct.  Can you copy/paste the output of 

```
cat /etc/modprobe.d/blacklist.conf 
```back here or just see if b43 or b44 or ssb are there?

with 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```if so, we will need to make some changes.

Also, you might post the output of 

```
lsmod
```using the "<>" code tags.

---

### Post by ahallubuntu on 2013-02-05
~

---

### Post by Cyclops_ on 2013-02-05
I wouldn't be so quick to think it's hardware.  I have the same issue.  After the upgrade, I lost networking.  Thing is, I have a dual boot system, and I checked in Windows, and I have networking just fine there.  So it has something to do with this upgrade, methinks.  And others are having issues as well.

---

### Post by unixpcguy on 2013-02-05
Some of the new upgrades are buggy. However, it is different with each setup.

---

### Post by WolfgangInSummit on 2013-02-05
> **bkratz said:**
> Since you said you have tried several things we should make sure that the blacklisted drivers are correct. Can you copy/paste the output of 
 
```
cat /etc/modprobe.d/blacklist.conf 
```back here or just see if b43 or b44 or ssb are there?
 
with 
 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```if so, we will need to make some changes.
 
[COLOR=blue]Thanks for that! Here is what it gave me:[/COLOR]
[COLOR=blue]"<[/COLOR]
[COLOR=blue] [/COLOR]
[COLOR=blue]# This file lists those modules which we don't want to be loaded by# alias expansion, usually so some other driver will be loaded for the# device instead.# evbug is a debug tool that should be loaded explicitlyblacklist evbug# these drivers are very simple, the HID drivers are usually preferredblacklist usbmouseblacklist usbkbd# replaced by e100blacklist eepro100# replaced by tulipblacklist de4x5# causes no end of confusion by creating unexpected network interfacesblacklist eth1394# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much# hardware on its own (Ubuntu bug #2011, #6810)blacklist snd_intel8x0m# Conflicts with dvb driver (which is better for handling this device)blacklist snd_aw2# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)blacklist i2c_i801# replaced by p54pciblacklist prism54# replaced by b43 and ssb.blacklist bcm43xx# most apps now use garmin usb driver directly (Ubuntu: #114565)blacklist garmin_gps# replaced by asus-laptop (Ubuntu: #184721)blacklist asus_acpi# low-quality, just noise when being used for sound playback, causes# hangs at desktop session start (Ubuntu: #246969)blacklist snd_pcsp# ugly and loud noise, getting on everyone's nerves; this should be done by a# nice pulseaudio bing (Ubuntu: #77010)blacklist pcspkr# EDAC driver for amd76x clashes with the agp driver preventing the aperture# from being initialised (Ubuntu: #297750). Blacklist so that the driver# continues to build and is installable for the few cases where its# really needed.blacklist amd76x_edac[/COLOR][COLOR=blue]>" I hope that makes some sort of sense.[/COLOR] 
Also, you might post the output of 
 
```
lsmod
```using the "<>" code tags.
 
..

---

### Post by bkratz on 2013-02-05
This explains how to use code tags

[http://ubuntuforums.org/showthread.php?t=1189729](http://ubuntuforums.org/showthread.php?t=1189729)

---

### Post by WolfgangInSummit on 2013-02-05
Thank you for the heads up.
 
After I've typed in
gksudo gedit /etc/modprobe.d/blacklist.conf
this appeared on the screen:
```

 
# This file lists those modules which we don't want to be loaded by# alias expansion, usually so some other driver will be loaded for the# device instead.# evbug is a debug tool that should be loaded explicitlyblacklist evbug# these drivers are very simple, the HID drivers are usually preferredblacklist usbmouseblacklist usbkbd# replaced by e100blacklist eepro100# replaced by tulipblacklist de4x5# causes no end of confusion by creating unexpected network interfacesblacklist eth1394# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much# hardware on its own (Ubuntu bug #2011, #6810)blacklist snd_intel8x0m# Conflicts with dvb driver (which is better for handling this device)blacklist snd_aw2# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)blacklist i2c_i801# replaced by p54pciblacklist prism54# replaced by b43 and ssb.blacklist bcm43xx# most apps now use garmin usb driver directly (Ubuntu: #114565)blacklist garmin_gps# replaced by asus-laptop (Ubuntu: #184721)blacklist asus_acpi# low-quality, just noise when being used for sound playback, causes# hangs at desktop session start (Ubuntu: #246969)blacklist snd_pcsp# ugly and loud noise, getting on everyone's nerves; this should be done by a# nice pulseaudio bing (Ubuntu: #77010)blacklist pcspkr# EDAC driver for amd76x clashes with the agp driver preventing the aperture# from being initialised (Ubuntu: #297750). Blacklist so that the driver# continues to build and is installable for the few cases where its# really needed.blacklist amd76x_edac
```
 
By the way, I am working with two computers here. One to post in this forum and one that is not connected - that's the one I am having trouble with. The code I posted on here was copied and pasted using an USB stick.

---

### Post by WolfgangInSummit on 2013-02-05
I feel like I'm being left hanging here. The problem that I have seem to be widespread and I have yet to find a solution within this forum. I do hope someone will help!
What ticks me off is the fact that after an update yesterday my network connectivity was gone. The ethernet connection was working fine before the update.
 
In windows you can "go back in time", is that also possible in Ubuntu?

---

### Post by ahallubuntu on 2013-02-05
~

---

### Post by WolfgangInSummit on 2013-02-11
> **ahallubuntu said:**
> I am not suggesting the Broadcom card installed now has failed.  I am sure you can get it to work.  And the next time you upgrade, you'll have to spend more time trying to make it work again.  Broadcom wireless cards are difficult in Linux.

Or - replace the Broadcom card with an Intel 5100 as I do and never worry about it again as this card has long, stable support in Ubuntu.

Hi! Thanks for your post. Would it be the one I found on Amazon?: [http://www.amazon.com/Intel-WiFi-Wireless-512AN_MMW-802-11a/dp/B009AO8I1A/ref=sr_1_1?s=electronics&ie=UTF8&qid=1360590184&sr=1-1&keywords=intel+5100+wireless+card](http://www.amazon.com/Intel-WiFi-Wireless-512AN_MMW-802-11a/dp/B009AO8I1A/ref=sr_1_1?s=electronics&ie=UTF8&qid=1360590184&sr=1-1&keywords=intel+5100+wireless+card)

Please let me know. Thanks in advance

---

### Post by WolfgangInSummit on 2013-02-11
I've read your previous thread and just ordered the intel 5100. I hope it'll work.

---

### Post by WolfgangInSummit on 2013-02-19
I have now received the new wifi card in the post and installed it. Turned on the computer and - voila - got my wifi connection!:KS

---

