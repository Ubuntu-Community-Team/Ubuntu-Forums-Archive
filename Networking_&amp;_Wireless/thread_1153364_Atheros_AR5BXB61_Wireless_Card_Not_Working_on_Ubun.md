---
title: "Atheros AR5BXB61 Wireless Card Not Working on Ubuntu 9.04 (Jaunty)"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Oriana on 2009-05-08
I have a Toshiba Satellite with detected wireless card Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) running Ubuntu 9.04 . I had no problems with my wireless until I updated to 9.04 from... whatever it was previously.

My problem is this: my wireless internet will work for a short while, and then it will stop. There is no Network Manager, and no way to find the status of my wireless network. I can, however, find some status of my (working) ethernet connection through System>Preference>Network Connections

I took the computer to my linux-knowledgeable friend, who tried to solve it, crawled the internet to find the answer, and in fact tried the answer posted here, [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529) , but after "build essential" completed, and we moved on to the next step Terminal returned that the files could not be found.

When reading the previous thread, I noticed that some people had had a different card detected than they owned. I'm not sure what I'd be looking for, the sticker says that it contains the radio device AR5BXB61, if that helps.

---

### Post by t0mppa on 2009-05-08
The Atheros version numbering is rather confusing since it consists of different layers (chip, chipset, family, etc.). The end result is that your device could be described in various different ways. Running lspci on Ubuntu shows the chip type, so that's a fairly good way of identifying it as far as the OS is concerned. The ar242x is a bit of a problem child though, since it refers to any chip from ar2420 to ar2429 and different users have reported different solutions working for it - usually described with "I tried everything else and this was the only thing that worked" - thus there's no clear unified how-to available for it.

Anyway, you mentioned not having any sort of network manager with a GUI. Have you tried restarting the Network Manager (alt + F2, 'nm-applet') incase you accidently closed it? If that doesn't work, then you should check if its package is installed. Alternatively, you could just install WICD, some users swear upon its superiority.

As for the drivers, Jaunty ships with ath5k as the default driver and according to MadWifi team, it should by now be superior to the original MadWifi driver, that the thread you posted suggested. If you're convinced ath5k is the source of all evil, then just try DL'ing the latest snapshot for the original driver from [here]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz") and then continuing with the manually compiling instructions.

---

### Post by pastalavista on 2009-05-08
I have a very similar wireless card (AR5BMB5) and it worked the same way until I rebooted into the previous kernel (2.6.28-11) and disabled the madwifi driver. The ath5k driver is unconflicted now and wireless is copacetic.

---

### Post by kennethmsmith on 2009-05-09
using lspci it appears that I have the AR242x Atheros problem child.  I tried first using the ath5k driver that came standard in Jaunty... no luck at all with wireless (not even showing any wireless access points) wire ethernet works fine.  I then tried activating the alternate Atheros madwifi driver... no luck.  Then I tried deactivating the alternate driver and installing the linux-backports-modules for jaunty and restarting to get the ath5k module, but still no luck.  Seems so far, nothing I have done even registers wireless connectivity is there at all.  I'm getting so frustrated.  I want to use Ubuntu so bad, and get off the Windows drip feed adiction, but without wireless ..what is the point.  Can someone please help me figure this out.  I'm running an HP dv6000 series laptop. Used the wubi install method.  Everything else seems to be working fine in jaunty except wireless connectivity.  PLEASE HELP.

---

### Post by Oriana on 2009-05-09
t0mppa;

Thanks for the info about the numberings, I figured that there was some problem like that.

> **t0mppa said:**
> 
Anyway, you mentioned not having any sort of network manager with a GUI. Have you tried restarting the Network Manager (alt + F2, 'nm-applet') incase you accidently closed it? If that doesn't work, then you should check if its package is installed. Alternatively, you could just install WICD, some users swear upon its superiority.

Yeah, restarting the applet was the first thing we tried. It seems to be completely gone. (What is truly mystifying is that it was there and accessible from the panel for several restarts after I updated to Jaunty, and didn't vanish until I started messing with the display of the panels.)

Trying WICD. *is nervous*

> **t0mppa said:**
> 
As for the drivers, Jaunty ships with ath5k as the default driver and according to MadWifi team, it should by now be superior to the original MadWifi driver, that the thread you posted suggested. If you're convinced ath5k is the source of all evil, then just try DL'ing the latest snapshot for the original driver from here and then continuing with the manually compiling instructions.

Do you think I'm having a problem with my driver? I have no idea what is going on. I do know that Jaunty had to get rid of the better driver for my graphics card because there was no current version, but that might be fixed already. Idk because I can't update, but see below for further details there. :(

Interestingly, after I posted, I was able to majickally get some wireless connection and was surfing Facebook and Myspace (huge resource draws for my likkle Satellite) at the same time for about 20 minutes to half an hour... until I hit a new snag.
My new problem appears to have to do with something with the update process. I have a few security updates for Jaunty that I am dying to download and install, however when I click Install Updates under Update Manager I lose whatever connection I had - wireless (not shocked) OR ETHERNET. The last time this happened, I did not get it back at all at the location I was at (my school). I am at home now, and I am curious if perhaps the different system reset whatever bug my ethernet card was having.

EDIT: Totally lost connection before I could post that because I installed WICD. But I'm connected now, and can view the different networks available, thanks to your tip of WICD, and while it is not nearly as pretty as the previous thing was, it is hella better than nothing.

EDIT x2: SUCCESS!!!

Thank you so much!!

---

### Post by t0mppa on 2009-05-10
@Oriana: So, it works now? That's good news. Did that even solve your update problem?

@kennethsmith: The wubi installation is merely meant for trying Linux out from inside your Windows, I'm not sure if it even works, if you go ahead and scrap your Windows. Since you said you want to get off the drip feed, you should do a proper install and put Linux on its own partition.

As for getting back to ath5k, trying the alternative driver probably blacklisted your ath5k (modules on blacklist are installed, but the OS is forbidden to load them up). And if it did, no matter what you do, the module won't load before it's removed from the blacklist. So you should check for that first, by crawling through the blacklist*.conf files in your /etc/modprobe.d/ directory.

---

### Post by kennethmsmith on 2009-05-11
I found ath_pci was blacklisted.  I commented it out... and bingo.. it appears my wireless is now working.  I'm not at home and the only network here is locked, but I'll test it when I get home to make sure.  I'll keep yall posted.

---

### Post by bjab on 2009-05-12
I too have the wifi problem, but with Atheros ar5007 on Compaq CQ70-201TU.  I too find that ath_pci.config is blacklisted, but when I try to comment it out, as suggested, ubuntu won't let me, putting up a notice that I don't have the necessary permissions!  Can anybody help?  I am a complete novice with ubuntu, so please try to make replies as if you are talking to a baby!

---

### Post by kennethmsmith on 2009-05-14
using the method of commenting out the blacklisted ath_pci driver and getting the jaunty backports ath5k driver seems to have worked for me.  I now have wireless :) Thanks t0mppa

---

### Post by kennethmsmith on 2009-05-14
bjab.. you are going to need to use sudo gedit followed by the file path and name to open it with root rights to be able to edit it.  If you need more info about using sudo gedit just search on it... you will find lots of info about using commands like this in the terminal.

---

### Post by t0mppa on 2009-05-15
Glad to see it worked, it's sometimes the simplest of things that mess everything up.

bjab: Like kenneth said, you need to use root priviledges to edit the file.

---

