---
title: "Broadcom BCM 4311 network unclaimed, no wireless"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by kafka201 on 2011-08-01
I've got a Broadcom 4311 card and since upgrading I can't connect to wireless.  I went through the solutions in the sticky and I still can't connect, when I type lshw -C network I get:

> *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0003fff
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:ed:f7:1c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation


When I go to the Additional Drivers it says that Broadcom STA Wireless Driver is activated and currently in use, but I can't find a way to enable wireless anywhere.

What am I doing wrong?

---

### Post by nm_geo on 2011-08-01
> since upgrading I can't connect to wireless
 
I assume you upgraded to Natty 11.04 correct?
 
```
 
lspci -nn | greg 0280

```
 
Give us that and we might be able to help with your wireless.
 
Does an ethernet cable work on this computer?

---

### Post by kafka201 on 2011-08-01
Yes, sorry, I upgraded to 11.04.  I ran > lspci -nn | grep 0280 and got > 10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
  

I'm assuming you meant grep in that code.

Wired ethernet works great, just inconvenient.

---

### Post by wildmanne39 on 2011-08-01
Hi, run this command please.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
Then disconnect your wired connection and restart your computer, do you have wireless now?
Thank you

---

### Post by nm_geo on 2011-08-01
> **kafka201 said:**
> Yes, sorry, I upgraded to 11.04.  I ran  and got   

I'm assuming you meant grep in that code.

Wired ethernet works great, just inconvenient.

Good catch yes grep was correct...
Now cable up ..
Turn off STA (wl) driver or go to Synaptic and uninstall bcmwl-kernel-source

in terminal 

```
sudo apt-get install b43-fwcutter 

``````
sudo apt-get install firmware-b43-installer
```Then ```
sudo lshw -C network

```We might have some blacklist problems so run this too

```
cat /etc/modprobe.d/* | egrep 'b43|bcm|ssb|wl'
```

---

### Post by kafka201 on 2011-08-01
Thank you both for your help, I'm typing this through the wireless right now.  Working perfectly.

---

### Post by wildmanne39 on 2011-08-01
Hi, your welcome! I am glad you have it working,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by modusoperandi303 on 2012-02-03
Hello I have been trying to solve  the same problem but both my ethernet and wireless are not working.  I am not new to Linux but know enough to be dangerous which is the reason why my ethernet is not working though I am not sure how I ****** it.

When I type 
sudo lshw -c network

it says network unclaimed on both my network controller bcm4311 and my ethernet controller bcm4401-no 

I suspect I need to download the packages which were recommended in the posts above so I now get errors when I try to reinstall them. Though this is proving difficult as I am having to do everything on my Android phone. 

Could anyone recommend some where I can download them onto my phone and transfer then across?

---

### Post by feargal on 2012-03-16
one solution would be:
put in a usb bluetooth dongle.
open bluetooth, in system, preferences, select <set up a new device....>
and pair with your phone, select use internet through this device,
and your computer is then a personal area network user of the phone's internet.
now you can reinstall/install the broadcom packages through synaptic.

---

### Post by mauleshjani on 2012-03-17
[SIZE=3]dear do this,
 
give this command 1st 

[/SIZE][SIZE=4]sudo lspci -v[/SIZE]
[SIZE=3]

then... give all these commands... u ll succeed...

[SIZE=4]sudo apt-get update[/SIZE][/SIZE][SIZE=4]

sudo apt-get install firmware-b43-installer[/SIZE]


[SIZE=4]sudo apt-get remove bcmwl-kernel-source[/SIZE]


[SIZE=4]sudo reboot[/SIZE]

===============================================================================
[SIZE=4]bye  thx [/SIZE]

---

### Post by weidnerr on 2012-07-11
Thanks for your post  [mauleshjani]("http://ubuntuforums.org/member.php?u=1520701")...

I did a fresh install of 12.04 yesterday.
Can get on wired but wireless network is UNCLAIMED

I have BCM4311 
Vendor: Broadcom

Hardware
Network: After doing your steps I now see the wireless network which wasn't there before.
The problems is firmware is missing and when I install and activate the Broadcom STA wireless driver supplied with 12.4 and reboot I completely lose the wireless network again.

Tried three times and the same outcome each time.

---

### Post by wildmanne39 on 2012-07-11
Hi, try:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot
Thanks

---

### Post by weidnerr on 2012-07-12
Solved....
Wasn't online with ethernet cable when installing B43.
Thank you. Wireless Now!

---

### Post by andriansah on 2012-07-20
thank you, it works with my laptop

---

### Post by BitterBuffaloCo1981 on 2012-07-27
:guitar:And Roll thanks so much was was scared of linux at first but am starting to warm up to it. I guess the real thing is don't be scared to goggle and read till you find an answer Thanks!!!

---

### Post by spalac24 on 2012-11-28
Hello! I just had the same problem while installing ubuntu 12, through the install everything was fine, i was even able to connect to the wifi, and even when i started using it everything was fine, but as soon as i updated some packages, and restarted (as it asked), it stopped working. I've followed what you said here, and i got the same problem as OP, *-networ UNCLAIMED with broadcom when i run sudo lshw -C network. Thanks.

---

### Post by wildmanne39 on 2012-11-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by spalac24 on 2012-11-28
Thank you for the extremely quick reply! I actually didn't see that until now. I choose to re-install ubuntu, as it was fresh and i had some time, it seems to be working right now, altough it didn't asked me for updates this time. Again, thank you, and sorry for not reading that earlier.

---

### Post by wildmanne39 on 2012-11-28
Your welcome! I suspect when you update it will happen again.

---

### Post by spalac24 on 2012-11-29
If that happens i will open a new thread, i don't exactly like to refloat old-ones, or should i post here?

---

### Post by wildmanne39 on 2012-11-29
Hi, you can start a new one because I am going out of town that way you can get help from others.

---

### Post by wildmanne39 on 2012-11-29
Hi spalac24, please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r)
```
```
 sudo apt-get install --reinstall bcmwl-kernel-source
```
```
sudo modprobe wl 
```
Thanks

---

### Post by spalac24 on 2012-11-30
Problem solved! I'm now writing from wireless! Thank you so much for your help!

---

### Post by wildmanne39 on 2012-11-30
Your welcome!

---

### Post by Pocc on 2013-02-06
> **Wild Man said:**
> Hi, try:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot
Thanks

I had a similar problem after a fresh install (Dell Vostro 1400, Linux Mint 14) and this was the thing that worked.
Thanks!!

---

### Post by janekapmann on 2013-02-25
Only your (maulesjahni) methodes works for me. Thanks  !

---

