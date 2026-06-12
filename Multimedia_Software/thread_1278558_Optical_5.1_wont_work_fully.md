---
title: "Optical 5.1 wont work fully"
date: 2009-09-29
forum: Multimedia Software
---

### Post by Kieeps on 2009-09-29
Hi all.
Been spending the entire day to search for answers to a problem i got.

I'm trying to get the optical out to send more then to 2 speakers, last time i actually got this to work i was on gnome and iirc there is some otions to check to make it work.

What i'w done so far is messin with the .asoundrc file.

```
pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}
```

I read about that on some tutorial that didn't work but i think this is on the right track. 

aplay -L gave the following:
```
default:CARD=Intel
    HDA Intel, CMI9880
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, CMI9880
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, CMI9880
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, CMI9880
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, CMI9880
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, CMI9880
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, CMI9880
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, CMI9880 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=HDMI
    HDA ATI HDMI, ATI HDMI
    HDMI Audio Output

```

So that explains what "surround51" is...but what does "type" and "slave" stand for? 

Anyhow. i get sound from 2 speakers WITHOUT the .asoundrc and WITH the file i get nothing at all. Does anyone have any clues to what i'm doing wrong? I'd love to get this up and running asap :D

---

### Post by Kieeps on 2009-09-30
Been doin alot more searching today and it seems to be a common problem to get it working the first time, i read through the entire manual on alsa but i cant really say it helped :/ didn't understand to much of it.

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
```

If there is anyone with the same situation as me pleace tell me how you solved it 'cus this is driving me nuts :'(


EDIT:
Found [this]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml") great site that explains some more, I used the example he had on the site and BAM i got sound....only on 2 speakers and the sub though as usual, but here is the strange thing, i did the "speaker-test -c 6 -D surround51 -t wav" test and got NOTHING.... i get sound when i play music in a player but not with the speakertest...will this help to troubleshoot? first though that came in to mind is that it might be another soundcontroller in the system that messes with my config or something....it's a bit confusing with alsa and kmix and all, kmix seems so damn messy, every time i log in i have to open kmix and unmute IEC958 to get any sound at all :/ getting 5.1 to work is actually starting to look sistant :'(

---

