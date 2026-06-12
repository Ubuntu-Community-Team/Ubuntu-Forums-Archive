---
title: "RaLink RT3090 [or RT2860] Wireless driver issues. Idiotproof method, anyone?"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by MrHarryWarne on 2010-08-19
**[If you're confused by the name of the wireless card, please read the bottom of the post. I'm confused too.]**

Right, I'm new to the whole Linux world. And also to coding and the  general use of tools like Terminal. To highlight just how much of a noob  I am: the other day I was really chuffed with myself for learning how  to eject my USB drive in OSX using *diskutil eject /dev/disk1/* , or something like that. So I guess that gives you an idea of my skill level.

Ok, so the root of my problem is trying to get drivers for a RaLink  RT3090 PCIe wireless card inside of some crappy netbook that hasn't even  got the model name on it. It's my ex-girlfriend's, she bought it from  the clothes shop Next. I knew I should've advised her against it. She  managed to mess up XP pretty bad about a week ago. So she asked me for  help. I had a look and XP was well and truly screwed. Fixing it would've  involved techniques that I just don't know how to do. I'd begun looking  at Ubuntu as a 3rd partition on my MacBook Pro, and though "Aha! Why  not install Ubuntu 10.04 Netbook Remix via USB onto her netbook. It will  be easy!" I installed it fine, but now it's gotten to the stage of  hunting around for drivers, I feel I've reached the limit of my  knowledge.

There are many threads on this site dealing with the RT3090, and many of  them give solutions and have people posting thank you replies saying  that they worked. The only problem is, these solutions give long strands  of code and what not. You wouldn't think this would be a problem  because I should be able to just follow step by step. Well what trips me  up is the use of terminology and shorthand. For instance, I will quote  from a readme that came with the latest RT3090 drivers, in the section  detailing how to build the driver from the included files:

```
1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.
```Now I'm sure to a lot of people on  this forum this will look idiot proof, but for me I have no idea. For  instance: 'x.x.x.x.tgz' and '...x.x.x.x." directory.' What am I supposed  to replace 'x.x.x.x.' with? And 'set the "MODE = STA" in Makefile and  chose [*choose?] the TARGET to Linux...' What does any of that  mean?!?!??!


So I'm asking two things:

1. Is there anywhere anyone can point me to learn these sort of things?  (Preferably not involving purchasing anything.) How did everyone else  come to understand all these things, as well as general Terminal tasks?

2. Can anyone help me specifically with building the RT3090 PCIe driver, bearing in mind this level of computing is new to me.

I'm not a complete idiot when it comes to computers, but this is the  first time I've ever really delved into the world of Linux and coding  generally. I want to learn, but for the time being, I'm in slightly too  deep. (And my ex wants her laptop back, xD.)


Thank you so much in advance, I've been at this for literally days and have gotten no where.

EDIT: OK, just to confuse me more...when I use: ```
sudo lshw -c  network
``` it tells me I have an RT3090 PCIe. But when I use:  ```
iwconfig
``` it tells me that I have an RT2860 Wireless ESSID.  Wth?!

EDIT: EDIT: I already posted this in *General* or whatever it's called because I was in a rush to put it up and didn't notice this sub-forum existed.

---

### Post by desnaike on 2010-08-19
Hello, I went here to get my RT 3090 driver. 
[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

There is a DEB file to download and install very easy.

---

### Post by MrHarryWarne on 2010-08-19
> **desnaike said:**
> Hello, I went here to get my RT 3090 driver. 
[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

There is a DEB file to download and install very easy.

Thank you, thank you, thank you. But, er, am I being really stupid when I ask where the download link is on the page? o_0.

---

### Post by MrHarryWarne on 2010-08-19
> **desnaike said:**
> Hello, I went here to get my RT 3090 driver. 
[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

There is a DEB file to download and install very easy.

Oh, I think I just worked it out. You need to get it through Linux, right? Well that's a bit of a deadend because I can't connect to the internet without it. Well, I guess I'll have to Ethernet it up. [There's currently a gigantic fridge-freezer in a box in front of the Windows desktop that is manually hooked up to the router with the only Ethernet cable, - _ -.

Cheers again.

---

### Post by MrHarryWarne on 2010-08-19
Ok, I installed the link you just gave me, but now, er...now what? It hasn't all of a sudden popped up with wireless networks. The wireless icon, top-right, still just has the icon with an exclamation mark next to it - like it did before I installed the drivers.

Any ideas? I thought I had it too, :/.

---

### Post by desnaike on 2010-08-19
Did u reboot the system

---

### Post by desnaike on 2010-08-19
The link is at the top  [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
click on it.

---

### Post by bkratz on 2010-08-19
> **desnaike said:**
> The link is at the top  [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
click on it.

That link is no longer functional, just tried  for the heck of it

---

### Post by desnaike on 2010-08-19
Am uploading the file to my dropbox account will post download link in a few minutes.

heres the download link [http://dl.dropbox.com/u/4827426/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb](http://dl.dropbox.com/u/4827426/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb)

---

### Post by MrHarryWarne on 2010-08-19
Yeah, I've rebooted, twice: once after I installed, and again after I did a general software update.

The link you put doesn't work. But I think I recognise the address, isn't it the download for the driver files directly from Ralink? But they're not build.

I think the drivers are installed, just not activated or something...I don't know. Is there anyway I can turn them on or something?

---

### Post by desnaike on 2010-08-19
All I did was install the deb file and it worked. whats pc specs ie; hp dv600 etc.

---

### Post by MrHarryWarne on 2010-08-19
Ah, cheers...I'll try that now.

I don't know if it makes much difference, but I just looked in /ect/wireless/ and 1. all there is is a folder called RT2860STA and 2. there's nothing in it, shouldn't there be a .dat or something?

But yeah, I'll try that .deb, cheers...

---

### Post by MrHarryWarne on 2010-08-19
```
ERROR: A later version is already installed
```
Is what came up... :/.

I did have a stab earlier at using this guy's guide (and .deb download near the bottom): [http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/)
I assume this one must've installed properly then...but I have no idea why it's not working, :s.

D'ya reckon I should try some RT2860 drivers? As I mentioned at the end of my first post. What's the right terminal command to find out the exact details of your wireless?
```
sudo lshw -c network
```
Is telling me it's:```
product: RT3090 Wireless 802.11n 1T/1R PCIe
```
and now ```
iwconfig
``` is telling me ```
no wireless extensions
``` for both lo and eth0 .

---

### Post by MrHarryWarne on 2010-08-19
[Sorry for jumbled replies, I'm getting the thread update weirdly.]

RE: the spec of the PC...erm, is there a terminal cmd for that? Because it's some crappy laptop bought from the clothes shop Next (I advised against it), and has no real distinguishing features on the skin.

---

### Post by desnaike on 2010-08-19
You need to google how to purge wireless drivers in ubuntu 10.04 I'm not that good at how to do it. after that install the deb file and it should work good luck.

---

### Post by bkratz on 2010-08-19
> **MrHarryWarne said:**
> [Sorry for jumbled replies, I'm getting the thread update weirdly.]

RE: the spec of the PC...erm, is there a terminal cmd for that? Because it's some crappy laptop bought from the clothes shop Next (I advised against it), and has no real distinguishing features on the skin.

I think you should post the whole output, (using the code tags) for the output of the 

```
lshw -C Network
```


so all can see the whether the device is managed and what driver it thinks is being used.

---

### Post by MrHarryWarne on 2010-08-19
Makes sense, I'll see what Google throws up, cheers.

Yeah ok, I'll go hook the netbook and copy it...

---

### Post by MrHarryWarne on 2010-08-19
The plot thickens...the network icon top left is saying 'networking disabled' now neither wireless nor ethernet is working. I'll type out the result of ```
lshw -c Network
``` for the wireless, say if you think ethernet would be helpful too:
```
*-network UNCLAIMED
description: Network controller
product: RT3090 Wireless 802.11n 1T/1R PCIe
vendor: RaLink
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:febf0000-febfffff
```But yeah, just before the 'networking disabled' I did a reboot and the pc started in BIOS. I dont know if it was an accidental button press on my part though. I though I'd look at the boot order and ```
USB:USB Hotplug FDD
``` was above the HDD. So I though, ok, I'll switch them. Then obviously I logged into find 'networking disabled'. The only thing I could think I'd changed was the boot order - even though I cant think how it would affect networking - so I changed it back. Any significance? Like I said, it starting up in BIOS in the first place *may* have been human error on my part.

---

### Post by finnbuntu on 2010-08-19
Hello,
There is a simpler way. Go on Synaptic and follow the prompts. Then install the linux-backports-modules-wireless-lucid-generic-pae package, and then try to connect to your wireless. It should work, it worked for me.
Hope it works,
finnbuntu

---

### Post by bkratz on 2010-08-19
There is a wealth of information in this thread.

[http://swiss.ubuntuforums.org/showthread.php?t=1490123](http://swiss.ubuntuforums.org/showthread.php?t=1490123)

And @finnbuntu
right now he doesn't even have wired ability.

hopefully something in that thread will help.

Also see this
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

---

