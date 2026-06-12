---
title: "Generic video card problems - complete Linux neophyte"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by ScoutV2 on 2006-11-22
Evening all, 

As the title of this thread states, I am a complete Linux neophyte (lower than a noob) I've spent some time perusing the forums in search of an answer, but didn't have much luck.  This is my 1st attempt at using a Linux OS, and the install went fine, wireless worked, etc. My video is giving me a problem though.  I imagine its a driver issue because the only problem is that whenever I move a window or scroll a webpage, it's extremely delayed and choppy.  

I spent some time surfing the net for tutorials in an effort to learn how to navigate the bash command line. I know the bare basics, and that's about it.  I've consistently heard that the Ubuntu forums welcome noobs with open arms so....I'm hoping some forum members can offer an assist. Bare with me though if I ask for additional clarification and/or assistance in working through any command line issues.  That having been said......

I'm running dual OS's (XP Pro and Ubuntu) on an old HP Pavillion zt1000 laptop.  The system device manager identifies the card as a Via VT8605 [PM 133 AGP][ProSavageDDR K4M266] I found a thread that mentioned trying "sudo dpkg-reconfigure xserver-xorg" which I did (what the hell does sudo mean anyway??) and switched from vesa to via.  Umm, yeah...... not so much. I couldn't boot to the GUI after I rebooted and when I swtiched it back to vesa and booted back up, my wireless quit working.  I have no idea why.

After much jacking with the wireless settings without any luck, I opted for a reinstall and threw my pride out the door to ask for help.  :???:   Any information, thoughts, insights, or links to additional bash command line tutorials would be much appreciated. I'm looking forward to learning something new and hopefully contributing to the forums in the future. Thanks in advance....(Sorry about the length, just needed to set the stage) 

ScoutV2

---

### Post by Rajiv_Nair on 2006-11-22
think u shld hv tried chngin vesa to via AFTER installing updated drivers for ur via card. And sudo means Super User DOmain. Only a su can perform administrative tasks:)

---

### Post by ScoutV2 on 2006-11-23
Thanks for the reply bud.  I've been trying to figure out where to find those drivers, and how to install them. Can you point me in the right direction?  Thanks again for the help.

---

### Post by deanlinkous on 2006-11-23
Drivers SHOULD be included for that chip, so you just need to make some changes to the xorg.conf file. 
Of course you need to change vesa to via.
then add a line to the Device section of the file that says

Option "VBEModes" "true"

That should do it! If not we can find some drivers for it.

---

### Post by ScoutV2 on 2006-11-23
Thanks for the insight, I'll see if I can work through that before I come back screaming for help.  If I can find the xorg.file, I should be able to work through it. 

Thanks for the help, I'll let you know how it comes out. 

ScoutV2

---

### Post by ScoutV2 on 2006-11-24
Ok, 

I edited the xorg.conf file with the info dean referred to and still no dice.  I got the same problem I mentioned earlier when I simply switched from "vesa" to "via"  I'm guessing it's a driver issue.  Can someone point me in the write direction to find a driver for my card?  Much appreciated. 

Scout

---

### Post by deanlinkous on 2006-11-24
Which version of Ubuntu is this?

Are you sure you got it put in right, saved the file and all that good stuff. Someone said that was all they had to do, I personally did the following...

I downloaded drm.ko and via.ko from here
[http://gamesplace.info/opensource/op...pper-binaries/](http://gamesplace.info/opensource/op...pper-binaries/)
put the drm.ko and via.ko files in the /lib/modules/2.6.15-26-386/kernel/drivers/char/drm/ folder.

Now download xserver-xorg-driver-via_+194-1_i386.deb from
[http://gamesplace.info/opensource/op...pper-binaries/](http://gamesplace.info/opensource/op...pper-binaries/)
and save it somewhere.

Install the deb using dpkg -i xserver-xorg-driver-via_+194-1_i386.deb
Now use the command **sudo depmod -ae**
Now edit you xorg.conf and change **vesa** to **via**

reboot or restart xserver...

This is on 6.06 which I think they call dapper. Thread here...
[http://ubuntuforums.org/showthread.php?t=264650](http://ubuntuforums.org/showthread.php?t=264650)

---

### Post by ScoutV2 on 2006-11-24
Thanks Dean, I'll give it a try and see if that cleans up the problem.  I'll post an update once I give it a whirl.  BTW, I'm running Edgy. 

Scout

---

### Post by deanlinkous on 2006-11-24
Hello! I reinstalled gNewSense and had to redo mine.
It seems you do not need to replace the drm.ko or the via.ko files.
All I did this time was - 
Download xserver-xorg-driver-via_+194-1_i386.deb from
[http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/)
and install the deb using dpkg -i xserver-xorg-driver-via_+194-1_i386.deb

Now edit you xorg.conf and change vesa to via and reboot or restart your xserver.

---

### Post by ScoutV2 on 2006-11-25
Ok, downloaded the xserver-xorg-driver-via_+194-1_i386.deb and attempted to install but received the following error msg:

dpkg: error processing /home/ryan/Desktop/xserver-sorg-driver-via_+194-1_1386.deb (-- install):
 Conflicting packages - not installing xserver-xorg-driver-via

Couldn't get it installed.  Thought maybe I need to replace the drm.ko or the via.ko files you referred to in your previous post.  Tried the link, but it wasn't valid. Routed me to a non-existent page. I'm also running Edgy and I noticed you referred to a thread that dealt with Dapper Drake, which could be part of my problem.  Thoughts??

---

### Post by deanlinkous on 2006-11-25
ouch!
Well, you could try forcing it but may not be a good idea. Maybe google or search the forums for some info. I haven't seen much about edgy and via chips.
sorrrryyyy

---

### Post by Jose Catre-Vandis on 2006-11-25
> **deanlinkous said:**
> Drivers SHOULD be included for that chip, so you just need to make some changes to the xorg.conf file. 
Of course you need to change vesa to via.
then add a line to the Device section of the file that says

Option "VBEModes" "true"

That should do it! If not we can find some drivers for it.

Thanks, this worked for me under Edgy on a Shuttle PC SK21G with a Via Unichrome Pro Graphics on board video.

---

### Post by deanlinkous on 2006-11-26
cool
yea, different things seem to work for different chipsets - not sure what the difference is.

---

