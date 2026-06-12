---
title: "Running 8.10, audio not working at all, I have researched and read stickies."
date: 2009-01-23
forum: Multimedia Software
---

### Post by danielbaer on 2009-01-23
Hello, after having windows xp become inoperable on me, I decided to run Ubuntu on my machine. I have enjoyed ubuntu thus far, but a lack of audio while using firefox is a distinct gap in the OS. I have heavily researched this topic, on this and other forums, and I have attempted using the very detailed sticky on this forum to no avail. 

I have tried adjusting the ALSAmixer, pulseaudio, and sound preferences, but nothing I have tried so far has worked. 

Here are my system specs from lspci;

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:02.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

I realize this question has been asked numerous times, but help would be greatly appreciated.

---

### Post by 2hot6ft2 on 2009-01-23
Perhaps something in here will help. Some you may have tried already.

Here are a few options to choose from from fixing pulse to disabling it and using asla, or replacing pulse with esound.

First fixing pulse
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

Sound trouble shooting
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Disabling pulse and using alsa (Before deciding to remove pulse you should read the warning here as to what the result could be).
[http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2179&start=0&st=0&sk=t&sd=a)
and another one going the same route here
[http://ubuntuforums.org/showthread.php?p=6370902#post6370902](http://ubuntuforums.org/showthread.php?p=6370902#post6370902)

Replacing pulse with esound
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
A short version here. I suspect it will be modified.
[http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html](http://ubuntuextreme.blogspot.com/2008/12/how-to-fix-audio-in-intrepid-ibex.html)

There are more but this gives you some alternatives that are being used.
--------------
no sound
Do you have all the needed codecs to be able to play sound?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

if so and you still have no sound try these maybe one will help.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Rim on 2009-01-23
Is the audio not working all the time or just with firefox? :) if its just firefox then ur flashplayer is to blame or whichever that runs the specific video/audio in firefox.

^^ if not then i know this may sound simple and stupid coming from me but have u opene audio settings and pulled the master volume to maximum, loaded the others and pulled them up as wel? i notised whener i install Ubuntu its down and i hear no sound but the sound actually works.

On the upper task-bar beside the date and time right click on volume then click on "Open volume control". In there u will find "Master Front" pull it completely up. 

^^ hope it helps if not post here again.

---

### Post by danielbaer on 2009-01-24
I have tried listening to music in rhythmbox, but still no sound, does that suggest that the audio problem is not localized to flash?

---

### Post by akash2008 on 2009-01-24
I decided to run Ubuntu on my machine. I have enjoyed ubuntu thus far, but a lack of audio while using firefox is a distinct gap in the OS. I have heavily researched this topic, on this and other forums

---

### Post by Rim on 2009-01-24
If at ubuntu start-up u do hear the start-up track then audio works. If not then its a problem with the drivers and u need to find the appropriate drivers or its a problem with the sound being as always after an instal turned off in which case follow my advice in the previous post and make sure all the chanels r pulled to the max. Check ur card and ask on forum for the location and install of the drivers :).

If u do hear sound and only some players or for example here firefox doesen't play the sound then u have a problem with ur codecs for the players and the plugins in case of firefox. (or the volume might be accidentally turned off).

<.< oki so which 1 is it? Sound doesen't work at all or just firefox and some players?

If its just firefox then u have to go into Tools>Add-ons> and probably this 1 is the colprit as i had problems with it "flashplugin".

Disable it. I'm using Schokwave Flash plugin. It works well for me on my x64 filesystem and it works on the x86 as well <.< from my experience. If it differs from this then install the 1 i mentioned here.

If the problem seems to be the plugin then report here and i will redirect u to a forum where u can find how to install it properly :)

---

