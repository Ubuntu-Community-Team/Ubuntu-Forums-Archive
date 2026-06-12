---
title: "Distorted sound in Karmic Intel HD audio"
date: 2009-10-30
forum: Multimedia Software
---

### Post by caish5 on 2009-10-30
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

I'm getting distortion with the above card when 5.1 is activated in the sound preferences. Kind of a high pitched tinniness.
I discovered that if i set it to stereo instead of 5.1 it is ok, but i want 5.1 to work since it's a media center computer.

I'm using karmic 64bit

Anyone know a solution?

---

### Post by barthel on 2009-10-30
No solution here, but I got similar output when testing Karmic-64 from the CD on my Toshiba P105-S9339 laptop.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by ell02 on 2009-10-30
I have same card,but using 32 bit.My problem was stutter sound when gaming. This thread helped that. Hope it helps u.

[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

---

### Post by caish5 on 2009-10-30
Not much there to help us I think.

---

### Post by barthel on 2009-10-31
Looks like this is part of the pop/click bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201")

The rest of the distortion seems to have been from excessive volume. Apparently the new audio drivers do a much better job with the HDA Intel chips and my default volume from Jaunty was overdriving my laptop speakers in Karmic.

Reportedly there is a fix in PPA, but in the meantime, changing a line in /etc/modprobe.d/alsa-base.conf should do the trick:

```
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel power_save=0 power_save_controller=N

```

I'll be checking more audio output in the next few days to confirm this work-around.

For immediate relief, try
```
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```

Note that you must do this from a root terminal. Just using 'sudo' will get you a "permission denied", just as if you were a normal user.

---

### Post by Jive Turkey on 2009-10-31
I'm having the exact same problem with tinny distortion in 5.1 mode on the a slightly older chipset.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
For music I can get passable results using "Analog Stereo Duplex" setting.  

I tried some 5.1 AC3 input, totem locked up, mplayer said invalid stream, and VLC played it but the background noise was still there. (with 5.1 mode on).

the command 
```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```
works correctly playing from all the right speakers without the distortion, weird.

I've also noticed that the volume/fade/balance sliders in the sound preferences will cause distortion when being moved.  I'm ot really sure what package is responsible but I think we should post a bug.

---

### Post by caish5 on 2009-10-31
I've already done the pop/click fix.
he pop/clicks are gone but i still have exactly the same symptoms as Jive Turkey!
Cool username!

---

### Post by Jive Turkey on 2009-10-31
In looking into this problem I've found that the distortion has peaks at intervals along the volume slider.  As I move the volume slider on the panel I can find points where there is no distortion and points where it is more intense. 

The good news is there are points where there is little to no distortion when in 5.1 mode, its a bit touchy but I can find usable spots that still sound good.  I think I might have enough of an to file a bug report now.

Ya, why not.  Here's a link to the bug I filed.  If it affects you too, let them know:
[B]
[Bug# 46693]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/466936")[/B]

---

### Post by Jamie Lokier on 2009-11-02
> **barthel said:**
> 
```
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel power_save=0 power_save_controller=N

```

I'll be checking more audio output in the next few days to confirm this work-around.

For immediate relief, try
```
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```

Note that you must do this from a root terminal. Just using 'sudo' will get you a "permission denied", just as if you were a normal user.

Alas, neither fix works for me.  Sounds works for a while, then after some app or other has finished using it for a while, no more sound.

Neither of the above sets of commands solves the problem.

---

### Post by ZarathustraDK on 2009-11-02
Got the highpitched whine too with 5.1 surround enabled (same thing with 4.1).

Switching to stereo output fixed it for me. Not a viable long-term solution, but nonetheless...

---

### Post by deankovell on 2009-11-06
It's not just intel . I have NVidia (realtek) alc1200, and I was also getting the high pitched whine that went away by switching to stereo.
Karmic

Edit: Pulseausio later quit working alltogether and following istructions on this thread, I can't hear the whine noise anymore in 5.1 surround.
[http://ubuntuforums.org/showthread.php?t=1243064](http://ubuntuforums.org/showthread.php?t=1243064)

> had a similar problem on a fresh installed Karmic (thinkpad t61).
deleted ~/.pulse
( rm -r ~/.pulse )
and restarted pulseaudio
( killall pulseaudio )


---

### Post by caish5 on 2009-11-09
That doesn't work for me.
Still sounds awful in 5.1

---

### Post by deankovell on 2009-11-10
I figured out how to reproduce the noise and make it go away again, but we may be having different problems. If I set sound preferences hardware profile to 5.1, change to the output tab, and mess with the fade or subwoofer sliders the whine comes back. But, I can then open up gnome-alsa-mixer and then move the master slider down and up and the noise goes away. It may not also be going away entirely, but it at least gets quiet enough I can't hear it.
Hope it helps.

I also wonder if it has something to do with converting stereo files to 5.1. I haven't tried any media that is actually in 5.1 surround.
Edit: using the slider on the main volume control applet also causes the noise to return.

---

### Post by 2541 on 2009-11-10
> **barthel said:**
> Looks like this is part of the pop/click bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201")

The rest of the distortion seems to have been from excessive volume. Apparently the new audio drivers do a much better job with the HDA Intel chips and my default volume from Jaunty was overdriving my laptop speakers in Karmic.

Reportedly there is a fix in PPA, but in the meantime, changing a line in /etc/modprobe.d/alsa-base.conf should do the trick:

```
# Power down HDA controllers after 10 idle seconds
#options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel power_save=0 power_save_controller=N

```

For immediate relief, try
```
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```

Note that you must do this from a root terminal. Just using 'sudo' will get you a "permission denied", just as if you were a normal user.

Thank you, barthel. That fixed my soundproblems with karmic.

---

### Post by topdownjimmy on 2009-11-16
> **barthel said:**
> Reportedly there is a fix in PPA
Where have you heard this?

Thanks for the link to a temporary solution.

---

### Post by barthel on 2009-11-17
I saw it when I was researching the bug, but I don't recall seeing a link to the actual PPA. Hence my use of "reportedly"--I was unable to verify the PPA at the time--and I can't seem to find the original post again now.

Sorry I can't be of more help on that.

---

### Post by jakefromlondon on 2009-11-25
I also have the distortion problem.  I'm running a shiny new P55 based motherboard, with a core i5.  Dmesg output:

jacob@glottis:~$ dmesg | grep "hda"
[   11.248037] ALSA hda_intel.c:684: No response from codec, disabling MSI: last cmd=0x300f0000
[   12.257306] ALSA hda_intel.c:699: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   13.266579] ALSA hda_intel.c:1382: Codec #3 probe error; disabling it...
[   13.618022] hda_codec: ALC889A: BIOS auto-probing.
[   25.991167] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

Sound has a tinny distortion at certain points on the volume slider.  When this occurs, the problem can be resolved by using alsamixer to adjust the PCM volume back up to 100.  For whatever reason, changing the master volume causes the PCM volume to shift to 99 or 98 and seemingly unpredictable master volume settings.

Hope this helps.

---

### Post by amitaibar on 2009-11-27
I came across this:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/445849)
All you need to do it sudo apt-get install linux-backports-modules-alsa-karmic-generic and it should work.
I didn't try it but I think it might help since the problem is with alsa and not with the intel driver

---

