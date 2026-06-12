---
title: "Need help with realtec high def audio drivers"
date: 2008-05-20
forum: Multimedia Software
---

### Post by jras20 on 2008-05-20
Hello,
I'm trying to get sound from my realtec high def audio drivers, I used windows XP but I got Ubuntu 32bit 8.04LST version installed.  Please help me get this to work.
Thanks
Hopefully Ubuntu supports that driver!!

---

### Post by 47_MasoN_47 on 2008-05-20
Have you checked to see if restricted drivers are enabled?

I haven't used a realtec in a long time.  I know Ubuntu supports HD audio though.

---

### Post by jras20 on 2008-05-20
> **47_MasoN_47 said:**
> Have you checked to see if restricted drivers are enabled?

I haven't used a realtec in a long time.  I know Ubuntu supports HD audio though.

They are not in the list.

---

### Post by 47_MasoN_47 on 2008-05-20
Install hardinfo ```
sudo aptitude install hardinfo
``` and then run it from the terminal.  See if your audio card is listed in the multimedia section when you click "Summary."  That will let us know if Ubuntu even detects that it is there.  I assume that it is an integrated card?

---

### Post by jras20 on 2008-05-20
Here is what happened:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  libsoup2.2-8 
The following NEW packages will be installed:
  hardinfo libsoup2.2-8 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 317kB of archives. After unpacking 905kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libsoup2.2-8 2.2.105-4 [88.8kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe hardinfo 0.4.2.3-3 [228kB]
Fetched 317kB in 2s (117kB/s)    
Selecting previously deselected package libsoup2.2-8.
(Reading database ... 102860 files and directories currently installed.)
Unpacking libsoup2.2-8 (from .../libsoup2.2-8_2.2.105-4_i386.deb) ...
Selecting previously deselected package hardinfo.
Unpacking hardinfo (from .../hardinfo_0.4.2.3-3_i386.deb) ...
Setting up libsoup2.2-8 (2.2.105-4) ...

Setting up hardinfo (0.4.2.3-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by cferrell on 2008-05-20
I'm also having trouble here. Specifically, there IS sound, but you can only hear it when the volume is turned all the way up, and even then its very quiet.

---

### Post by jras20 on 2008-05-20
Mine shows that the driver is there, but I still have no sound, and it is not muted.

---

### Post by Damanther on 2008-05-20
I am having similiar problems. Sound worked fine under gutsy, but ever since the upgrade to hardy I haven't heard a peep from my speakers.

It is an hp m7750m with integrated audio. I'm running th 64bit hardy version.

aplay -l shows that the card exists.

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: pcsp [pcsp], device 0: pcspeaker [pcsp]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci | grep Audio shows it as

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

I have ths snd_hda_intel module loaded in alsa

The only error I see in the logs is this from dmesg:

 hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...

Does anyone have a clue how to help us out?

Non of my apps complain about not having or connecting to an output device, but I get NO sound.

---

### Post by jras20 on 2008-05-20
Ok this is weird I can hear audio over my headphones, but nothing is comming out of my laptop speakers, any suggestions?

---

### Post by 47_MasoN_47 on 2008-05-21
Have you gone into the preferences for the volume control and made sure that there is nothing muted?  When I first installed Hardy the front speakers were muted for some reason and only the rear speakers were putting out audio.  Maybe something similar is going on with your laptop.

---

### Post by jras20 on 2008-05-21
> **47_MasoN_47 said:**
> Have you gone into the preferences for the volume control and made sure that there is nothing muted?  When I first installed Hardy the front speakers were muted for some reason and only the rear speakers were putting out audio.  Maybe something similar is going on with your laptop.

I'll half to see but I dont think it is...

---

### Post by Damanther on 2008-05-21
OK, just to check since I've read a lot of posts about headphones not working and normal speakers working and vice versa, when i got home today I plugged my headphones in and bingo, I could hear music.

Then I took them out, and the speakers were working. I'm thinking my case was something in the plug that detects the presence of the headphones that got reset when I plugged in/unplugged the headphones??????

I swear I did no updates/tweaks this afternoon, but I spent 3 days tweaking and researching before this.

I must admit I'm afraid to reboot my computer at this point though. :P

---

### Post by larry19l on 2008-07-16
Hi Folks,

I'm in the same boat with you. HP Pavilion and I did the other stuff (hardinfo, aptitude...) too...

larry@m8457:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
larry@m8457:~$ lspci | grep Audio
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

In gnome-alsamixer nothing is muted and all sliders are between 75-100%

So are we looking at Realtec or nVidia HDA ?

I'm getting sound (enough for headphones) from the front jack using Totem but the monitor is an HP 2408 so I'm connected via HDMI cable. In winVista.HP sound is ok for headphones or HDMI fed monitor speakers IF all controls are maxed out, which is not really how you're supposed to have it. Normal (old-fashioned) stereo systems: 20-100 watts/channel = volume knob was usually at about 1/4-1/3 of max. But HH gives me nothing from the built-in monitor speakers fed by that HDMI cable.

HOWEVER... I did get totem to play video & sound (to headphones) but VLC produces no sound. I'm going lookin for any drivers I can find (Realtec or nVidia) and maybe a reinstal of VLC and then try the 883 analog choice in VLC. And, lets see what nVidia and Realtec have on their websites...

we'll see...

back later...

maybe we'll get lucky...:confused:

---

### Post by larry19l on 2008-07-16
Hi Folks,

Just come back from HP, nVidia etc...
For my HP Pavilion (m8457c) with the M2N68-LA (Narra3) motherboard,
I do NOT have any name brand audio. All it's called is "Onboard Audio"
and described by: 8 channel high definition audio using Audio CODEC ALC888S.

Somewhere else in here, someone said goto Preferences | Sound and try all the driver combinations. It looks like the only one that doesn't work is the ALC883 digital. But the sound only comes out the regular audio jacks and not the HDMI. So I may not be able to use the HDMI audio unless the folks doing the ALSA project add that in. 

As to those notebook speakers, well, maybe there is something in your BIOS that can be changed or a jumper somewhere under one of those little screwed down panels ? Course, the easy fix is to get a pair of those tiny (or not so tiny) portable speakers and plug them in the headphone jack ?
I have at least 4-5 sets of them around here!

After I get everything working on this new HP, gotta start all over with my old HP (notebook!) :-({|=

Now it's on to see why VLC don't work and where in heck the output is when I print to that generic PDF driver that comes with CUPS when you set up a fresh HH, and then there is my wacom Intuos3 to get working and the Logitech webcam (at least the USB audio input from the mic is working! TIP: the ALSA driver doesn't work for Logitech Webcam, at least not that big-*** butt ugly one with the glass lens) and of course VirtualBOX and SSH and maybe samba and then the notebook and the network and sharing and anyone know if HellaNZB is the best newsleecher? And when will I get time for all the compiz-fusion eyecandy !? That alone makes it all worthwhile! :lolflag:

And I gotta start looking for a program like tree.com (I think?). I gotta get a handle on the tree structure of this filesystem so I can figure out where to get stuff when I write make files. I am not happy with any of the PIM's out there. They just try to hard to do to much! KISS, right?

And I still gotta get back to my art, too! Haven't held a brush in my paint stained fingers in 2 weeks !
---
Have fun
L8r
me

---

### Post by Linux Kelley on 2008-10-01
> **larry19l said:**
> Hi Folks,

Just come back from HP, nVidia etc...
For my HP Pavilion (m8457c) with the M2N68-LA (Narra3) motherboard,
I do NOT have any name brand audio. All it's called is "Onboard Audio"
and described by: 8 channel high definition audio using Audio CODEC ALC888S.

Somewhere else in here, someone said goto Preferences | Sound and try all the driver combinations. It looks like the only one that doesn't work is the ALC883 digital. But the sound only comes out the regular audio jacks and not the HDMI. So I may not be able to use the HDMI audio unless the folks doing the ALSA project add that in. 


This is what is happening to me. I to have my sound going to my HP 2408 HDMI monitor and its speakers but it doesn't work.

The headphones do work.

Anyone have any ideas?

Kelley

---

### Post by Linux Kelley on 2008-10-02
> **Linux Kelley said:**
> This is what is happening to me. I to have my sound going to my HP 2408 HDMI monitor and its speakers but it doesn't work.

The headphones do work.

Anyone have any ideas?

Kelley

Well, I wasn't able to get sound through my HDMI cable, BUT I got a set of 2.1 speakers from Staple for $20 and now I have sound! 
:popcorn::D

---

### Post by markbuntu on 2008-10-03
My guide here has links and information for your hda and HDMI problems and just about anything else you want to know about sound in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

