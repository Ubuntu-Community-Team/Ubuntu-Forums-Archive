---
title: "Mythbuntu - various issues (hardware)"
date: 2008-01-23
forum: Mythbuntu
---

### Post by hamishau on 2008-01-23
Hi everyone

I have spent two days bashing my head against the MythTV wall, and have very little to show for it. I can't even get the video card to display on the TV correctly. It took me almost two days to get to the point where I now have black and white on the TV, but the resolutions are all wacky, and I can't get the following to work at all:

I definitely don't have
* colour TV-Out
* DVD playback (unencrypted disk)
* unable to watch TV (card says GENERIC/UNKNOWN cx8800)

Not yet tested
* audio or video (avi, wmv, etc) playback
* picture display
(but what's the point with no colour and correct resolution?)

Hardware setup:
* PC = HP D530, P4 2.8 GHz, 512MB RAM, 2 x 80 GB IDE HDDs (only one in use, other for recordings when this thing works!)
* VGA = Gigabyte nVidia 6200 256MB AGP with S-Video/Composite out. Using Composite to a LG 54inch CRT TV
* Sound = Creative Audigy Value 5.1 (haven't got to test this yet, but worked with Ubuntu)
* Networking = started with wired but installed Linksys WUSB54G. This is working well. I have given this a fixed IP in the router. I can get to the PC via ssh and web (port 80 brings up the MythBuntu control site). The requirement to type in the password is grating, but I should be able to fix that
* Remote = Microsoft MCE (1039) which seems to work with the "new" drivers
* TV Tuner = DTV2000H I was led to believe it is supported, but I get the following error messages:
htpc@htpc:~$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-14-generic/ke* rnel/drivers/media/video/cx88/cx88* -dvb.ko): No such device
htpc@htpc:~$ sudo modprobe cx88_dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-14-generic/ke* rnel/drivers/media/video/cx88/cx88* -dvb.ko): No such device

Problems:
I had a hell of a time to get the system to "see the TV" and output to that. I tried standard Ubuntu, MythBuntu, Knoppmyth, GeeXBox (which worked well, but didn't see the TV tuner card). Eventually MythBuntu began to see the TV and I can now get a picture on the TV! (don't know what I did there, as that was about the 400th reinstall)

However...
a) it is black and white. I initially tried TV-Out with PAL-B (I live in Australia). Also tried NTSC-M. Same result
b) the resolutions are all wacky. The LCD monitor is now "disabled" and initially the desktop displayed on the TV was set to 1024x768 or something that was so small I couldn't make it out, I changed the resolutions around and it doesn't help. If I change to 800x600 or 640x480 I can't get to the whole screen. The MythBuntu GUI is OK, as that seems to be independent. The remote works!

I'd love to get some help with getting this to work! Once I get the TV all worked out I will try to get the rest of it all setup. Also, if I need to change hardware I can do that, but I did a lot of searching around and found various posts that said it all worked. All help is really gratefully appreciated :-)

Hamish

---

### Post by scruffy1 on 2008-02-14
hang in there - it can work, but it is not an obvious thing

i am on my 5th or so try with a new install, and although i too had the monochrome (and silent) output, something strange and wonderful occurred and it went technicolor and correctly so, although the sound remains a mystery

i have been trying to stream foxtel digital via the analogue out from my stb, and indeed it did timeslip in colour, so i have seen the potential

dvd's play fine; i am using a 6600 to send tv to a 68cm tv (crt)

i wish i had been more obsessive in recording my setup procedure, as i am now unable to even get the tv card to play, but wth, i can see it is possible

keep the faith !

i have to admit that even with the frustration it is simpler than trying to get vista ultimate to work - i have a 939 with 2gig of ram and a 4000+ running at 2.6gig, and vista was s...l...o...w as a wet weekend

good luck

---

### Post by scruffy1 on 2008-02-14
> **hamishau said:**
> 
However...
a) it is black and white. I initially tried TV-Out with PAL-B (I live in Australia). Also tried NTSC-M. Same result
b) the resolutions are all wacky. The LCD monitor is now "disabled" and initially the desktop displayed on the TV was set to 1024x768 or something that was so small I couldn't make it out, I changed the resolutions around and it doesn't help. If I change to 800x600 or 640x480 I can't get to the whole screen. The MythBuntu GUI is OK, as that seems to be independent. The remote works!

try using a keyboard - the "w" changes from 4:3 to 16:9 and allows fullscreen on the tv

amen to the monochrome experience here too

maybe it's an australian thing :(

---

### Post by ian dobson on 2008-02-14
Hi,

I had the same problem with a B&W TV-Out. I was using a S-VIDEO SCART adapter.

Turns out the the cable was abit too long and after cutting it down/soldering on a new SCART plug I got colour :lolflag:

I still haven't got a "non-standard" resolution working for the TV-out, and running at 800x600 is OK but the scaling isn't quite right (black bands above/below picture or part of the picture cut off left/right).


Regards
Ian Dobson

---

### Post by scruffy1 on 2008-02-15
> **ian dobson said:**
> I still haven't got a "non-standard" resolution working for the TV-out, and running at 800x600 is OK but the scaling isn't quite right (black bands above/below picture or part of the picture cut off left/right).

tv is at weird resolutions and frequencies

in oz the standard on my tv was ?78something by ? 57something at ? 57hz

but it looked great on standard definition

and then i killed it as noted :cry:

---

