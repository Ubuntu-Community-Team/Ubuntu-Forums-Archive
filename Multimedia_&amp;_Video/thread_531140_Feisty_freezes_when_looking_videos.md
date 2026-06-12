---
title: "Feisty freezes when looking videos"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by zenacim on 2007-08-21
[SIZE="4"]hello everyone,

sorry for my english.

So, when i launch a video with any software (VLC,Totem,Democracy) the system freezes for a couple of seconds but the sound go on. It's happening several times during the movie.

Can you help me please?[/SIZE]

---

### Post by RudolfMDLT on 2007-08-21
Hey! 

What version of Ubuntu are you running? 
What is your computer spec? 
What Videos are you trying to play, i.e., what is the extension of the video file, mpg, avi, vob(DVD Files)? 
Are you using an ATI card?

Get back to me with these and I'll try and sort you out! :)

---

### Post by zenacim on 2007-08-21
hello thank u for your response

i m using ubuntu 7.04

my pc is a 3500+AMD with 700MB ram
and a nvidia chipset incorporated

some weeks ago, i did not have this problem

---

### Post by RudolfMDLT on 2007-08-21
Cool - so your machine has the hardware! :)

Did you  install any new or weird software not in the repo's?

Can you please try to play an mp3,  and one or two video files. Tell me what player you used and what type of video where you playing? If you are not sure of the type of video then rightclick on the file and look under file type.

Also, open synaptic and search for this library:
libxine1-ffmpeg

If it is installed, right click  on it and say reconfigure or re-install.

 Cheers,

Rudolf

---

### Post by zenacim on 2007-08-21
the problem is i installed a lot of soft.

the mp3 have no problems

i use VLC player (but i tested with totem and democracy)
i reinstalled libxine1-ffmpeg

and it s the same problem with avi and mpegs :'(

---

### Post by RudolfMDLT on 2007-08-21
very weird!

Try and install Mplayer? and also - lets check whether your graphics drivers are still loading. In the terminal, type,**lsmod | grep nv** and paste the output of the command here.

---

### Post by Gremlinzzz on 2007-08-21
change vidio settings to X11.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl](http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by RudolfMDLT on 2007-08-21
> **Gremlinzzz said:**
> change vidio settings to X11.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl](http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Well, I would never think of that! :) It's worth remembering though! Thanks, lets hope that it works.

---

### Post by zenacim on 2007-08-22
nass@nass-desktop:~$ lsmod | grep nv
nvidia               6837140  32 
agpgart                35400  1 nvidia
i2c_core               22656  3 i2c_ec,nvidia,i2c_nforce2
sata_nv                20868  0 
libata                125720  2 ata_generic,sata_nv



how to change to X11??

thank you

---

### Post by zenacim on 2007-08-22
up please :'(

---

### Post by RudolfMDLT on 2007-08-22
Nothing?

Weird!

Try this:
> 
 What to do if Video players crash while using Beryl

    * You will need to change video driver from xv to x11 in ~/.mplayer/config and gstreamer-properties. 

where ~ is Linux short-hand for /home/rudolf of /home/zenacim

Are you running beryl?

See if this guide helps?
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

Cheers,

Rudolf

---

### Post by zenacim on 2007-08-22
all videos worked fine till two weeks ago.

in same times of my problems a used wine to play on football manager07

---

### Post by RudolfMDLT on 2007-08-22
did you EVER run wine as root? (Don't try it now!)

**sudo** wine /football_manager/setup.exe or something similar?

Because you are not supposed to.

---

### Post by zenacim on 2007-08-22
maybe one time

to try to install sony ericcson softs i think

---

### Post by zenacim on 2007-08-22
i reinstalled libdvdcss2 w32codecs
 
and it seems to be less worst

nope maybe sudo wine some sony .exe

---

### Post by RudolfMDLT on 2007-08-22
I recently had to reformat my PC in order to correct the damage that wine did as root.... 

anyway - the driver that X loads is an Nvidia Geforce 2 driver, is this a card that you have in your machine?

---

### Post by zenacim on 2007-08-22
nass@nass-desktop:~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)

nass@nass-desktop:~$ lspci -n
00:00.0 0500: 10de:02f0 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:04.0 0604: 10de:02fb (rev a1)
00:05.0 0300: 10de:0241 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0260 (rev a2)
00:0a.1 0c05: 10de:0264 (rev a2)
00:0b.0 0c03: 10de:026d (rev a2)
00:0b.1 0c03: 10de:026e (rev a2)
00:0d.0 0101: 10de:0265 (rev a1)
00:0e.0 0101: 10de:0266 (rev a1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:14.0 0680: 10de:0269 (rev a1)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
nass@nass-desktop:~$

---

### Post by RudolfMDLT on 2007-08-22
Okay - lets try from the start:

1) Are you running Beryl, if you are not sure, do you windows warp or wobble when you move them? Do you have desktop effects installed?

2) press ALT+F2 and in the run dialog enter "gstreamer-properties" . It might take a while to load. click the video tab. Under default Output, click the drop down and select "X Windows system(X11/...)"

restart your machine.

See if you can play the videos.

If you still have trouble, read this thread,
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

and UN-install everything that it tells you to install. Search for the items in synaptic and right click, and select remove. do not Completely remove the file. 

restart your machine.

Play some videos and see if you still get the same problem or whether you actually now get an error! 

Now re-install all of the above.


I know it's a long list but your problem is not a normal one to have.

Goodluck,

Rudolf

---

### Post by zenacim on 2007-08-22
1) i did not install beryl

2) thank you i m trying

---

### Post by RudolfMDLT on 2007-08-22
Cool! I'll stay up until you report back.  though I have to admit that if you have reinstalled all the drivers  and the players and reconfigured Gstreamer then I am seriously out of ideas.

---

### Post by zenacim on 2007-08-22
i think i m going to reinstall feisty

---

### Post by RudolfMDLT on 2007-08-22
didn't that help - then thats about the only option you have. Sorry mate! :(

Is your home directory on a different partition? Well, with the re-install make sure that it is. that way you can reinstall the OS but still keep your desktop and stuff.

also

backup the /var/cache/apt/archives folder. it contains all your deb files that you downloaded with synaptic. After the install, copy them back as root and do a 

sudo apt-get update

and then when you install them in synaptic, it'll save you the time of downloading them! :)

If you have KDE installed you can just highlight all the packadges, rightclick and say install all. after an hour your system should be back just the way it was.

Anyway, sorry that I couldn't be of more help.

Goodluck with the re-install.

Cheers,

Rudolf

---

### Post by zenacim on 2007-08-22
really thank you

you tried, me too :)

cheers

---

### Post by Seamyst on 2007-09-15
Whoo, 2 worked for me!  I'd been having problems playing one avi video since I did a nuke-and-pave yesterday... which was weird because my other avi videos worked just fine.  I can now play it - only in MPlayer, yes, but it works.

---

