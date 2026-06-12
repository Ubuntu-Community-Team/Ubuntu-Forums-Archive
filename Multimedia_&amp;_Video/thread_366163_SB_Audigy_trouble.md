---
title: "SB Audigy trouble"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by yoda715 on 2007-02-20
Hi guys,
 I'm fairly new to Linux, but I'll try to be as descriptive as I can. I have a Intel box that is raided. I had to install using this guide: [http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system) . I am currently running 6.10. I have ubuntu up and running. Most everything appears to be working, except my soundcard. The wierd part is when Ubuntu boots up to the login screen, I hear the first login sound, the Kongas? Once I'm logged in I do not hear any further sounds. In troubleshooting this I noticed that there is no default sound card applied, and there is no sound card even listed.

Anyone able to give me pointers where to start? I'm confused as to why the sound would work at the login screen, but not once I'm logged in.

---

### Post by r4ik on 2007-02-20
Just in case you have not found it yet.

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by yoda715 on 2007-02-21
yes I went through those steps. Still no luck. Sound card is installed and working when I get to login screen, after that it doesnt work :(

---

### Post by yoda715 on 2007-02-27
Friendly bump. Any ideas why sound would work before I login and not afterwards?

I tried running these commands and this is what I get:
****@ubuntu:~$ asoundconf set-default-card Audigy2
****@ubuntu:~$ esd &
[1] 18836
****@ubuntu:~$ ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Audigy2'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

---

### Post by yoda715 on 2007-02-27
Bumpity bump

---

### Post by yoda715 on 2007-02-27
Bump. Anyone? Please help, I don't want to switch back to windows :(.

---

### Post by yoda715 on 2007-02-27
Bump

---

### Post by yoda715 on 2007-02-27
When I try to play a test file under System>Preferences>Sound I get the following:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

What does this mean?

---

### Post by yoda715 on 2007-02-28
Ok I did a clean install of Edgy. Updated, still having problem. However at least when I do aplay -l I get this:

root@ubuntu:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
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
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But no default sound card is showing up in the sound configuration. So I did this:

sudo asoundconf set-default-card Audigy2

Still nothing! Someone please help. Why in the world would I hear sounds Before I log in, and not afterwards?

---

### Post by Daveth on 2007-02-28
does your motherboard have an on-board sound chip and have you disabled that in the bios? Just a thought.

---

### Post by yoda715 on 2007-03-01
Yes, it does, but I had it disabled. I even tried removing my Audigy2 card and using MB sound card. Had the same issue. I would hear login sound but nothing after that.

No worries though. I gave up on Ubuntu and moved to Fedora, which is AWESOME! Fedora recognized my raid partition right off the bat, and the sound works at all times! When ubuntu gets its act together with the latest hardware maybe I'll switch back, but for now Fedora has better hardware support and implementation.

---

