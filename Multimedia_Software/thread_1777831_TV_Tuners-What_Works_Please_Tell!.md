---
title: "TV Tuners-What Works? Please Tell!"
date: 2011-06-08
forum: Multimedia Software
---

### Post by robert-drury on 2011-06-08
Please help me. I want to buy a new TV Tuner Card. I like Black gold BGT3595 PCIe Terrestrial and Satellite TV channels. It must work in Ubuntu 11.04 Desktop amd64bit. Black gold do have a downloadable Linux/Ubuntu 10.04 binary 32bit driver set for it. WILL THAT WORK, do you reckon?
Please tell, Any Other TV Tuners that will work in Ubuntu?
Do you have a list of approved hardware, somewhere?
My Hauppauge WinTV-HVR 900 is a cert non-starter
I do not see MythUbuntu as being my solution.

---

### Post by mastablasta on 2011-06-08
mythbuntu has them tested and also info which one work and which ones don't in their wiki.
 
you don't need to have mythbuntu for them to work. you do need a TV programme. there are a couple of others other than mythTV

---

### Post by LowSky on 2011-06-08
Mythbuntu is just a  modified version of Ubuntu that used XFCE and a few applications to make TV viewing easy. All of whcih can be added from a normal Ubuntu install.

Your haupauge 900 should work. Probably the most famous working tuner is the haupauge hvr-2250

---

### Post by seawolf167 on 2011-06-08
I have the "Hauppauge WinTV-HVR-2250 Dual TV Tuner / Encoder 1229 PCI-Express x1 Interface - OEM" (just copied/pasted the name from newegg) and it works great. I've been using it since 9.04. I did have to modprobe the drivers then, but in later versions it works out-of-the-box. I use MythTV almost exclusively with it.

---

### Post by Mac-ghost-hunter on 2011-06-08
Well I have a Haugepauge PVR-150 and I use tv-viewer.  There is no deb file for this you must install mplayer, ITVT-Utils and TCL 8.5 to complile it on you linux.  After the install of the dependancies run ./tv-viewer installer.tcl to complile.
 
Mac-Ghost-hunter

---

### Post by oldos2er on 2011-06-08
> **robert-drury said:**
> 
My Hauppauge WinTV-HVR 900 is a cert non-starter


According to [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-900](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-900) that card should work. Is it USB or PCI?

---

### Post by dozycat on 2011-06-08
Mythtv could work but must be compile from source to work with ubuntu 11.04.
I am waiting to get it from synaptic.

---

### Post by Maheriano on 2011-06-08
I have both a Hauppauge Win-TV HVR-1800 and a 1250, neither of them work in Ubuntu nor Windows. I spent an entire weekend trying to get either of them to work in either operating system, it was impossible.

---

### Post by uRock on 2011-06-08
Moved to ***Multimedia & Video***

---

### Post by wolfen69 on 2011-06-08
> **Mac-ghost-hunter said:**
> Well I have a Haugepauge PVR-150 and I use tv-viewer.  There is no deb file for this you must install mplayer, ITVT-Utils and TCL 8.5 to complile it on you linux.  After the install of the dependancies run ./tv-viewer installer.tcl to complile.
 
Mac-Ghost-hunter

I also have the pvr-150 and it works great. Ghost-hunter: you can also use vlc to watch tv. [Here]("http://ubuntuforums.org/showthread.php?t=1734916") is my tutorial. 

Btw, besides the pvr-150, the pvr-250/350/500 also work well.

---

### Post by MartyBuntu on 2011-06-08
I've been using my Hauppauge PVR-150 on Ubuntu for a few years...works perfectly. Excellent capture card.

I just installed the HVR-1850 PCI-e in another computer running Natty. Although the wiki claims that the card is unsupported, this card works out-of-the-box with a digital input to the tuner from my OTA antenna...tuning in of channels is done with Me-TV.

---

### Post by Maheriano on 2011-06-09
> **MartyBuntu said:**
> I've been using my Hauppauge PVR-150 on Ubuntu for a few years...works perfectly. Excellent capture card.

I just installed the HVR-1850 PCI-e in another computer running Natty. Although the wiki claims that the card is unsupported, this card works out-of-the-box with a digital input to the tuner from my OTA antenna...tuning in of channels is done with Me-TV.

How the F did you get this to work? I spent days and days and more days working on it.

---

### Post by MartyBuntu on 2011-06-09
> **Maheriano said:**
> How the F did you get this to work? I spent days and days and more days working on it.

How is your tuner card connected? Analog or digital connection...and to what?

You say you have the HVR-1800 PCI card, correct?

---

### Post by Maheriano on 2011-06-10
> **MartyBuntu said:**
> How is your tuner card connected? Analog or digital connection...and to what?

You say you have the HVR-1800 PCI card, correct?
Ya, 1800 and 1250. I just plugged them into the PCI-E slot on the board and that's it. I tried downloading experimental drivers for the 1800 from the Hauppauge site but they didn't work. It's not connected to anything else, I'm trying to get ATSC.

---

### Post by poe503 on 2011-06-11
Check out my tutorial for the 1250: [*http://ubuntuforums.org/showthread.php?t=1648472*]("http://ubuntuforums.org/showthread.php?t=1648472")

---

### Post by MartyBuntu on 2011-06-11
> **Maheriano said:**
> Ya, 1800 and 1250. I just plugged them into the PCI-E slot on the board and that's it. I tried downloading experimental drivers for the 1800 from the Hauppauge site but they didn't work. It's not connected to anything else, I'm trying to get ATSC.

Make sure your RG-6 cable is plugged into the digital input on the card. You're using an ATSC antenna on the other end, right?

Kaffeine and ME-TV work with digital out-of-the-box with the 1800 and 1850 (I have both). No additional drivers are necessary for digital, they are included in the latest kernel.

---

### Post by Maheriano on 2011-06-13
> **MartyBuntu said:**
> Make sure your RG-6 cable is plugged into the digital input on the card. You're using an ATSC antenna on the other end, right?

Kaffeine and ME-TV work with digital out-of-the-box with the 1800 and 1850 (I have both). No additional drivers are necessary for digital, they are included in the latest kernel.

Who and a what now? What does the RG-6 cable look like? All I have is the card, it came out of a machine someone was throwing away, there's nothing connected to it, not even an antenna. So I just plug the card into my machine and I didn't do anything else with the hardware, no cables, no antenna, nothing. But I live in the second or third largest city in Canada, ATSC should be nice and strong.

The 1250 I bought from a store so I have all the hardware but I didn't see any extra cables in there.

EDIT - is RG-6 the coaxial cable from the wall? Do I need that for over the air ATSC?

---

### Post by cmargolin on 2011-06-13
> **Maheriano said:**
> Who and a what now? What does the RG-6 cable look like? All I have is the card, it came out of a machine someone was throwing away, there's nothing connected to it, not even an antenna. So I just plug the card into my machine and I didn't do anything else with the hardware, no cables, no antenna, nothing. But I live in the second or third largest city in Canada, ATSC should be nice and strong.

The 1250 I bought from a store so I have all the hardware but I didn't see any extra cables in there.

EDIT - is RG-6 the coaxial cable from the wall? Do I need that for over the air ATSC?

RG-6 is coaxial cable.  

For over-the-air ATSC, you need an antenna.

If your coax in the wall connects to a working TV antenna (VHF and UHF frequencies), you are all set for over-the-air ATSC.  If you have a strong signal, an indoor antenna will work too.

---

### Post by MartyBuntu on 2011-06-13
> **Maheriano said:**
> 

EDIT - is RG-6 the coaxial cable from the wall? Do I need that for over the air ATSC?

You need to run RG-6 cable to your antenna (preferably external and roof mounted and high up...aiming at the broadcast towers in Calgary.)

You won't pick up anything without some sort of antenna. Definitely not in high-def, which is the best part of OTA broadcast.

---

### Post by poe503 on 2011-06-14
> But I live in the second or third largest city in Canada, ATSC should be nice and strong.


Are you sure ATSC (digital) is used in Canada?  I have some relatives who tune into Montreal french language stations. I believe that they use the old analog tuner on their set to catch that signal.  I might be mistaken there but I don't think Canada changed at the same time the US did.

---

### Post by Maheriano on 2011-06-14
> **poe503 said:**
> Are you sure ATSC (digital) is used in Canada?  I have some relatives who tune into Montreal french language stations. I believe that they use the old analog tuner on their set to catch that signal.  I might be mistaken there but I don't think Canada changed at the same time the US did.

I know the plan was for us to switch over later but the original release I read was that it would be switched over by last April, though I hadn't checked it in about 6 months prior to that. Now that I check it, it says August 31 2011, maybe it got pushed back at some point and I didn't check it.

So it seems like I can only get NTSC and all this time I've been forcing it to ATSC. Stupid changing release dates. Do any of you in Canada have working ATSC tuners?

---

### Post by MartyBuntu on 2011-06-14
> **Maheriano said:**
> 

So it seems like I can only get NTSC and all this time I've been forcing it to ATSC. Stupid changing release dates. Do any of you in Canada have working ATSC tuners?

Pretty much every broadcast is ATSC...although there might be a few stations broadcasting in analog as well until the end of August.
It's not an "either/or" situation. I'm not sure there are even any analog-only broadcasts.

---

### Post by Maheriano on 2011-06-14
> **MartyBuntu said:**
> Pretty much every broadcast is ATSC...although there might be a few stations broadcasting in analog as well until the end of August.
It's not an "either/or" situation. I'm not sure there are even any analog-only broadcasts.

Okay well if there is ATSC in Calgary then my problem still applies.

---

### Post by MartyBuntu on 2011-06-14
> **Maheriano said:**
> Okay well if there is ATSC in Calgary then my problem still applies.

What problem?

Plug RG-6 cable into HVR 1850/1250.
Point antenna in direction of broadcast towers.
Receive signal.

Go here:

[http://www.tvfool.com/](http://www.tvfool.com/)

..and punch in your location for aligning your antenna for best signal.

---

### Post by poe503 on 2011-06-14
Perhaps it would be a good idea to check the basics:

In my tutorial [*http://ubuntuforums.org/showthread.php?t=1648472*]("http://ubuntuforums.org/showthread.php?t=1648472"), there is a section devoted to checking that your card is recognized.

If it is recognized, in mythbackend under "capture cards", you should have enabled the 1250 ATSC card and it looks something like this:

[I]Card Type: DVB DTV capture card (v3.x)
DVB Device Number: /dev/dvb/adapter0/frontend0
Frontend ID: LGDT3305
Subtype: ATSC[/I]

In the main Mythbackend menu, there is also "video sources" and "input connections".

The bare bones of it is you need to set your card as a "video source" and then fix up the "input connection" which includes scanning for channels.

If you got all of that and no channels are picked up by the scanning process, then you probably need an appropriate antenna for ATSC.  I used to be able to pick up NTSC channels with my little indoor antenna but when they switched, I needed to use a roof antenna.  I live in a major metropolitan area and the broadcast towers are only 6-7 miles away and can be seen from my roof.

---

### Post by joel.wietelmann on 2011-07-20
> **seawolf167 said:**
> I have the "Hauppauge WinTV-HVR-2250 Dual TV Tuner / Encoder 1229 PCI-Express x1 Interface - OEM" (just copied/pasted the name from newegg) and it works great. I've been using it since 9.04. I did have to modprobe the drivers then, but in later versions it works out-of-the-box. I use MythTV almost exclusively with it.

Your 2250 works out of the box :confused: I'm fighting with mine like mad right now to get it running in 11.04.  Please tell me what I'm missing.

---

### Post by MartyBuntu on 2011-07-21
> **joel.wietelmann said:**
> Your 2250 works out of the box :confused: I'm fighting with mine like mad right now to get it running in 11.04.  Please tell me what I'm missing.

Are you hooked up to an ATSC antenna?

What program are you using for TV viewing?

---

### Post by joel.wietelmann on 2011-07-21
Ahhh, wait.  I'm hosed when it comes to analog cable, aren't I?

---

### Post by MartyBuntu on 2011-07-23
My PVR-150 and HVR-1800 work with analog cable.

Read this: (specifically post #10)

[http://ubuntuforums.org/showthread.php?p=7344302#post7344302](http://ubuntuforums.org/showthread.php?p=7344302#post7344302)

---

### Post by robertallen79 on 2011-10-26
can someone tell me if the HVR-2250 fm tuner works, I see a lot of people have gotten the tuner up, though of building a htpc itx machine so once I move back out on my own from my parents and bills I can just hook something up has a entertainment/computer all in one

though I haven't seen anything on the fm tuner

~Robert

---

### Post by wolfen69 on 2011-10-26
> **robertallen79 said:**
> can someone tell me if the HVR-2250 fm tuner works, I see a lot of people have gotten the tuner up, though of building a htpc itx machine so once I move back out on my own from my parents and bills I can just hook something up has a entertainment/computer all in one

though I haven't seen anything on the fm tuner

~Robert

[Here]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250") is the wiki page for the 2250.

---

### Post by Grand old man on 2011-10-31
> **MartyBuntu said:**
> Pretty much every broadcast is ATSC...although there might be a few stations broadcasting in analog as well until the end of August.
It's not an "either/or" situation. I'm not sure there are even any analog-only broadcasts.
Canada changed to digital transmission on September 1st, 2011. 

I live in the Toronto area and get about 30 stations. Wow the HD quality is amazing, free too.

---

### Post by &lt;mike&gt; on 2011-12-06
I'm having trouble with a Hauppauge 2200.
The SD digital channels all work perfectly, but all the High definition channels seem to have horrible pink interference.
Not sure what's going on....

---

