---
title: "[SOLVED] Issues with USB audio"
date: 2008-08-29
forum: Multimedia Software
---

### Post by djbon2112 on 2008-08-29
[http://ubuntuforums.org/showthread.php?t=442083](http://ubuntuforums.org/showthread.php?t=442083) is actually the exact same problem I have, but I'll recap:

Gear: 
Ubuntu Hardy Heron x64
Dell Vostro 1700
Turtle Beech Audio Advantage Micro USB sound card, outputting S/PDIF to Logitech Z5500s

Problem:
No audio though USB sound card in Firefox (Flash specifically) or media players (Mplayer, VLC, Totem)

Other:
Amarok works fine through a manual fix to use ALSA ("plughw:default")
>Preferences >Sound set correctly to "USB Audio"
When all was "working" (see below), listening to one device would cut sound in the others

Everything was buggy when I first installed Hardy x64 a couple weeks ago, then my some miracle everything seemed to work, though with some quirks. Now, it's back to nothing but Amarok again. I tried changing almost every audio setting in Mplayer, nothing. Uninstalled, tried the same with VLC, still nothing. Followed the advice in the thread at the top, again nothing. All these sources will play through the Laptop speakers when on "default", but if I try to manually configure them like Amarok (though either ALSA or OSS, including every hardware option given in both), I get nothing. Some devices give me explicit "no sound output" warnings, others simply don't play. Any advice would be appreciated. I'd prefer Mplayer as my video player, but will settle with either of the other two if it gets sound working.

Update:
With some settings in both Mplayer and VLC, I get no sound but do occasionally hear pops and crackles from the USB Audio which seem awfully well timed to events in the video I'm watching. Perhaps a lead?

---

### Post by Crafty Kisses on 2008-08-29
Post the results of > lsusb

---

### Post by djbon2112 on 2008-08-30
joshua@laptop-001:~$ lsusb
Bus 007 Device 005: ID 046d:c041 Logitech, Inc. 
Bus 007 Device 004: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 007 Device 003: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 007 Device 002: ID 2001:f103 D-Link Corp. [hex] 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by minky311 on 2008-08-30
Could you post the results when you type this in terminal
```
cat /proc/asound/modules
```

---

### Post by djbon2112 on 2008-08-30
joshua@laptop-001:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio

---

### Post by minky311 on 2008-08-30
Go about half way down the page in this guide [http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=82801G+Sound) where it states how to configure default soundcards and do as it says.

---

### Post by djbon2112 on 2008-09-01
Well, I got it working by following that guide, kinda. The sound was all choppy, metallic and distorted in mplayer though. Then, my system ground to a halt, froze, and on reboot Ubuntu won't detect my USB sound card at all. It works fine in other PCs (including another Ubuntu machine), but regardless of what USB port I have it in, the card isn't detected on my laptop anymore! ("cat /proc/asound/modules" only returns my build-in Intel chipset, and as device 0). Advice?

---

### Post by djbon2112 on 2008-09-02
Alright, I followed that guide to rebuild ALSA from scratch, and now I'm back to square one. I'm CERTAIN that everything is set right (USB audio is "default" and at position 0), but Mplayer/VLC STILL play "default" though the laptop speakers and refuse to play anything at all with other settings. Advice?

joshua@laptop-001:~$ cat /proc/asound/modules
 0 snd_usb_audio
 1 snd_hda_intel

joshua@laptop-001:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by minky311 on 2008-09-02
In vlc have you tried going to settings->preferences and checking the advanced options at the bottom. Then expanding the audio tab and making sure ALSA is set to use the usb sound card?
You could also make sure that when you press alt F2 and type in gstreamer-properties that the device is set as the usb soundcard.

---

### Post by djbon2112 on 2008-09-02
> **minky311 said:**
> In vlc have you tried going to settings->preferences and checking the advanced options at the bottom. Then expanding the audio tab and making sure ALSA is set to use the usb sound card?
You could also make sure that when you press alt F2 and type in gstreamer-properties that the device is set as the usb soundcard.

It wasn't, but changing it didn't help mplayer. I still get nothing.

I'm more concerned with getting mplayer working than VLC, since I prefer it more.

---

### Post by minky311 on 2008-09-02
When you enter terminal and type in alsamixer what comes up as your sound card. If it's not your usb sound card try setting it as the default by first doing asoundconf list which will list the available soundcards and then doing asoundconf set-default-card <usbsoundcardhere>. Then going back to System->preferences->sound and setting everything to alsa.

---

### Post by djbon2112 on 2008-09-03
> **minky311 said:**
> When you enter terminal and type in alsamixer what comes up as your sound card. If it's not your usb sound card try setting it as the default by first doing asoundconf list which will list the available soundcards and then doing asoundconf set-default-card <usbsoundcardhere>. Then going back to System->preferences->sound and setting everything to alsa.

It's set to USB Audio, the PCM volume is all the way up, but "Loudness" isn't and I can't seem to change it. Could that be a problem?

---

### Post by djbon2112 on 2008-09-06
I'm starting to get a little flustered with the seeming lack of sense this is making. Is there any way to completely remove the drivers/etc. for my other card to make USB audio the only option? Would this help?

---

### Post by minky311 on 2008-09-07
[http://ubuntuforums.org/archive/index.php/t-233294.html](http://ubuntuforums.org/archive/index.php/t-233294.html)

Try reading through all of that.

---

### Post by djbon2112 on 2008-09-10
Alright, I did the blacklisting, and now Firefox works fine, but the media players (specifically mplayer) still don't work. They now give me "Error: No sound device" when I used settings that before worked, and I still get no sound.

This is obviously a problem with mplayer. I am running Ubuntu x64, could that be in conflict with it? Is there a particular way I should compile mplayer (this one was from the repos) for x64/USB audio?

---

### Post by djbon2112 on 2008-10-04
I'm still trying to get this working. Firefox and Amarok work perfectly, the 3 media players (mplayer, VLC and Totem) don't. I can think of no explanation for this. Can anyone else?

---

### Post by markbuntu on 2008-10-04
Most likely Mplayer is looking for your now blacklisted sound card. Look in my guide here, the try this first part may help you, also, you can try the  Multiple Application Sound Sharing section and look in the link in the Multiple Sound Cards section.

---

### Post by djbon2112 on 2008-10-05
> **markbuntu said:**
> Most likely Mplayer is looking for your now blacklisted sound card. Look in my guide here, the try this first part may help you, also, you can try the  Multiple Application Sound Sharing section and look in the link in the Multiple Sound Cards section.

It does this regardless of what I set in the audio properties for all 3 players. I only have 1 sound card (the USB one) that I ever want to use.

---

### Post by markbuntu on 2008-10-05
It does not really matter what you want, what matters is what the applications think that they want. Anyway, it seems I neglected to include the link to my guide, sorry:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by djbon2112 on 2008-10-05
Well I'll be damned:

> One way that some people have fixed their sound problems is by creating a new user in System/Administration/Users and Groups and then logging in with that. It seems the generic system defaults for new users are different from the initial user defaults that Ubuntu installs. You should try that first before resorting to some of the more drastic steps below, It is a simple thing to do and will make no changes to your system. And if it works, you will know it is just a user configuration problem and you can compare the hidden user default files in the respective home directories to find and fix the problems.

I did this and everything worked for the new user. VLC crashed, but sound played for the 2-3 seconds it was playing :p All the other apps worked too!

I guess it's time to re-create my user account!

---

