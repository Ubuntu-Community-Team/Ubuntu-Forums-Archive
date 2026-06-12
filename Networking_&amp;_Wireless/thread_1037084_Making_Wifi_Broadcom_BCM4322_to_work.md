---
title: "Making Wifi Broadcom BCM4322 to work"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by bibmorano on 2009-01-11
Hi,
first of all, this is my first post as a new proud Ubuntu user. I'm pretty new to this world, it may reflect in this thread :)

I want Ubuntu to recognize my wireless card :
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

I have a new Dell Studio 1535 laptop.

First, in the Ubuntu Wifi Doc, seems my card is supported out-of-the-box, and when i try several cmd, nothing seems ok.

A quick sudo lshw -C Network gives:

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Do I need ndiswrapper? What do the "UNCLAIMED" mean?

Thank to point me in the right direction :)
mat

---

### Post by mlchris2 on 2010-01-12
Did you get any help with this? Ive got a Studio 17 and having the same problem. I'm  a total Linux Newb as well. I dont even know where to start. I've been reading in the Wireless forum, but havent found a resolution yet.

---

### Post by bkratz on 2010-01-12
I remembered seeing somewhere that the 4321 and 4322 were similar to the BCM4311 and BCM4312.  I didn't find the exact passage, but I think this will help you.

[http://dimitar.me/broadcom-wireless-chipset-bcm4311-bcm4312-bcm4321-and-bcm4322-on-ubuntu-karmic/](http://dimitar.me/broadcom-wireless-chipset-bcm4311-bcm4312-bcm4321-and-bcm4322-on-ubuntu-karmic/)

---

### Post by simonfilby on 2010-04-29
> **bkratz said:**
> I remembered seeing somewhere that the 4321 and 4322 were similar to the BCM4311 and BCM4312.  I didn't find the exact passage, but I think this will help you.

[http://dimitar.me/broadcom-wireless-chipset-bcm4311-bcm4312-bcm4321-and-bcm4322-on-ubuntu-karmic/](http://dimitar.me/broadcom-wireless-chipset-bcm4311-bcm4312-bcm4321-and-bcm4322-on-ubuntu-karmic/)

As a newby I thought "Linuk for human beings" meant an end to the code and commands like the above link...  

Having loaded Ubuntu 10.04 as a Windows application using Wubi everything works just fine except for the Dell Broadcom 4322 wireless card which simply says "UNCLAIMED".  The System/Administration/Hardware Drivers installed the Broadcom proprietary driver which says "activated but not currently in use".  So how do I put it into use?

I used a hardwire cnnxn to update all the patches but still nothing.

Any help would be VERY appreciated.

PS: I followed the ndiswrapper instructions after downloading the Windows driver installable from the Dell website. It installed a driver OK using Windows Wireless Drivers but still nothing.

---

### Post by ublintu on 2010-04-29
Hi,
This was working in 9.10 :
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
Maybe is still ok in 10.04... I don't know, because I'm still in 9.10.

---

### Post by simonfilby on 2010-04-30
Got my Broadcom wireless working last night - I removed and re-activated the STA driver.  Strangely the taskbar icon stills shows its disconnected state but it is actually connected and online.

However, this morning after power-up it reverted to UNCLAIMED.

Tried toggling the Wi-Fi switch but nothing changed.

Removing and re-activate the STA driver did it again, but I won't be doing that every morning !

A lot of posts and suggested fixes refer to Ubuntu 9.10 but few for 10.04.

---

### Post by efeurich on 2010-04-30
Don't know if you all got it to work but when the wireless drivers don't work in Ubuntu, most of the time the problem is related to not having a open source driver for the hardware involved. The best way to go then is to go to Hardware Driver and download on of the drivers that is in the list. if non are there you have a problem and need to search further.

Hope this helps.

---

### Post by simonfilby on 2010-05-05
Thanks <efeurich>.

I got it to be more or less stable by using the locate command to find all instances of "ndiswrapper" and delete them.  Then on next boot the WiFi lights-up and connects.

Two remaining annoyances: (i) the wi-fi connection won't save my WPA password and prompts every time; and (ii) after connection the taskbar symbol displays the disconnected symbol even though I have a connection.  I can live with these though.

---

### Post by rol801 on 2010-05-05
Search and tried many work around for 9.10 / 10.04 . However , they all able to work "1" time since the very first time at Ubuntu installation. after reboot, everything fail again..
This sucks !!

---

### Post by ublintu on 2010-05-06
Hi,
Maybe this one can help:
[http://ubuntuforums.org/showthread.php?p=9244288](http://ubuntuforums.org/showthread.php?p=9244288)

---

### Post by rol801 on 2010-05-11
tried already, tried near 15 times . install, crash , reinstall..
already tried most method mentioned for 9.04 , 9.10 .. all fail..
PS.. try these method in 10.4 are easy to crash the system.. beware !!!

Totally give up wifi function ...... Poor

---

### Post by Lilonius on 2010-05-11
I have bad experiance with bmc4322. it worked 2 times, and now i can't start it ever, installed the STA drivers, tried 1000 things, and still not working. 

My gf is going to kill me because of this long cable i am having through the midle of the room :S

---

### Post by jschille on 2010-05-11
has anyone fixed this issue yet?
I also have a BMC4322 and network says UNCLAIMED.
Not sure if others are having this, but when i click on the connections it ONLY SHOWS
Wired Network
    Auto etho0
and then NO WIRELESS CONNECTIONS....

---

### Post by Lilonius on 2010-05-13
One thing that is now working for me, is that while booting the notebook, i first need to switch off the button for the wireles card, and when the system is up and running i turn it on and it finds the networks. but even if ti connects to a network the icon displays the red exclamation mark. but i can live with that!

I just hope there is some update that will fix this!

---

### Post by rol801 on 2010-05-14
> **Lilonius said:**
> One thing that is now working for me, is that while booting the notebook, i first need to switch off the button for the wireles card, and when the system is up and running i turn it on and it finds the networks. but even if ti connects to a network the icon displays the red exclamation mark. but i can live with that!

I just hope there is some update that will fix this!

Agree !! Found this and verify for times. it works.. 
and if you disable the wifi switch in bios.. the switch will not care its on or off.. , just change to switch button to another side then wifi function will back on again.. is weird...

---

