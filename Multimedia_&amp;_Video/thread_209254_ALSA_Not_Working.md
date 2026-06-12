---
title: "ALSA Not Working"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by Useff on 2006-07-04
Earlier, I enabled and then disabled IEC958 output on my Crystal Sound 46xx soundcard. After doing that, all of my ALSA output stopped for this user. OSS output works fine, though.

I can still hear the double drum at the startup screen, and a newly-created user has perfect ALSA output. Permissions for this user look to be in order.

I'm lost. Any ideas?

---

### Post by LordRaiden on 2006-07-05
For the user who doesn't get alsa, have a look under the /etc/group (or /etc/groups) file. Scroll down to the audio section, and make sure that the user's name is in the audio section.

---

### Post by Useff on 2006-07-05
This user's name is in the audio section. Curiously enough, the test user without problems is unlisted under audio.

---

### Post by LordRaiden on 2006-07-05
Try listing/unlisting both users and changinf the IEC 958 output.

---

### Post by Useff on 2006-07-05
The test user, when re-listed and then unlisted, lost audio. When re-listed a second time everything was back to normal.

This user remains the same after unlisting and re-listing. I tried changing IEC 958 output while unlisted and listed, and it had zero effect.

---

### Post by LordRaiden on 2006-07-05
for the normal user (not test) do aplay -l in a console. You should get the name of the soundcard meaning it is installed.

What music player are you using? Type its name in a console, then try to play something using the player. If there is an error, you should see the output in the console.

---

### Post by Useff on 2006-07-05
aplay -l seems to give a normal result:

**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 30/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CS46xx [Sound Fusion CS46xx], device 3: CS46xx - Center LFE [CS46xx - Center LFE]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30

I use amarok.

These are the errors I get when running the app through the console:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

---

### Post by LordRaiden on 2006-07-05
Those errors are just X server errors. Did you get anything while playing? Do the visualizations move around as if something is being played?

How about fiddling with the engine (auto, alsa, oss)?

---

### Post by Useff on 2006-07-05
Actually playing a song doesn't give a new error, despite the fact that I can't hear it. Visualizations work correctly, as if the music is audible.

Changing the engine to oss gives sound. Auto and alsa don't.

---

### Post by LordRaiden on 2006-07-05
You wouldn't by any chance have speakers with digital speakers to test with? Or even headphones to test the front headphone jack?

---

### Post by Useff on 2006-07-05
I've got headphones. Volume on them is at about 75%, but no sound.

Okay, here's something strange I just tried: When I run amarok with the sudo prefix, alsa output works fine. Now I'm really scratching my head.

---

### Post by revilot on 2006-07-05
[QUOTE=Useff]I've got headphones. Volume on them is at about 75%, but no sound.

Okay, here's something strange I just tried: When I run amarok with the sudo prefix, alsa output works fine. Now I'm really scratching my head.[/QUOTE]

Try plugging into some of the other jacks on your card.

---

### Post by LordRaiden on 2006-07-05
Wow, then it is permissions problem (must say lol). I was thinking it was a driver thing all along. Under /etc/groups compare the groups of your testing user and your normal user. All the groups where you find the testing user BUT not the normal user, switch/add the normal user to that group (not the other way around).

---

### Post by Useff on 2006-07-05
I went through the groups and they're identical.

---

### Post by LordRaiden on 2006-07-06
Getting more weird lol. Look for files in your home directory that could be in the least way related to sound (.asoundrc would be one) and delete them. If it works for one user and not the other but permissions are ok, then it has to be some user setting.

---

### Post by Useff on 2006-07-06
[QUOTE=LordRaiden]Getting more weird lol. Look for files in your home directory that could be in the least way related to sound (.asoundrc would be one) and delete them. If it works for one user and not the other but permissions are ok, then it has to be some user setting.[/QUOTE]

Deleting .asoundrc did it. Thanks a LOT!

---

### Post by LordRaiden on 2006-07-06
OK Great! Finally lol. I'll post this in my guide since it gave me headache.

---

### Post by crgutierrez on 2006-08-29
Have a card
0 snd_intel8x0
have read your wonderful instructions but so far no sound

---

### Post by craft47 on 2006-11-09
I'm also not getting any sound out of my VIA 82xx card.  It was working in Hoary.  When I type aplay -i my card is listed, so I've gone through all the alsamixer steps, but I have no sound.  I have a new install of Dapper on an Averatec 3250.  I had sound at the beginning, but I have since installed amaroK and Kaffeine and it seems to have happened since that.
I tried modinfo soundcore and all I got was:

filename:    /lib/modules/2.6.15-27-386/kernel/sound/soundcore.ko
description: Core sound module
author:      Alan Cox
license:     GPL
alias:       char-major-14-*
vermagic:    2.6.15-27-386 preempt 486 gcc-4.0
depends:     
srcversion:  DD426F1CCA2CC5F060F6F92

Shouldn't there be another module for "VIA VT82xx audio"
as well?](*,)

---

### Post by mtbk on 2007-12-12
I'm not sure where the best place to post this is, since I've read over a lot of threads that discuss problems getting via82xx on-board audio to work. This fix isn't Ubuntu-specific, but this is where I've gotten most of my info so far.

I have a via cl10000 motherboard, and after spending several days reading suggested fixes, I finally went back to my motherboard manual. Upon reading it, I found out that my F_AUDIO jumpers were not installed. Once I shorted the appropriate pins (5-6 and 9-10 in my case) the audio worked!

The F_AUDIO pins are used to add front panel audio ports (mic, line out, etc). However, when not in use, they need jumpers since they disable the on-board ports.

I know this is a simple fix, and I should have checked this first. I don't know if this will help anyone else, but if you have a new motherboard, check this out. I hope this helps some of you.

---

### Post by psparky on 2008-02-26
Just wanted to say many thanks for this tip.   Solved my problem completely.

k


> **LordRaiden said:**
> For the user who doesn't get alsa, have a look under the /etc/group (or /etc/groups) file. Scroll down to the audio section, and make sure that the user's name is in the audio section.

---

