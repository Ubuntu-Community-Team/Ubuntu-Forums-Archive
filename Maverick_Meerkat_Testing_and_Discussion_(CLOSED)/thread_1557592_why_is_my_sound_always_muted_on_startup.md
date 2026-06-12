---
title: "why is my sound always muted on startup?"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by setherd on 2010-08-21
On startup my sounds are always muted.
I have to goto system-> preferences-> sound

sound effects and output volume are set to 0 and are muted.

can I change this?

---

### Post by Stoneface on 2010-08-21
I have the same issue. Not a solution yet though..

---

### Post by philinux on 2010-08-21
> **setherd said:**
> On startup my sounds are always muted.
I have to goto system-> preferences-> sound

sound effects and output volume are set to 0 and are muted.

can I change this?

Always happens during testing.

---

### Post by nick_stokie on 2010-08-21
It could be related to this?
[https://bugs.launchpad.net/bugs/352732](https://bugs.launchpad.net/bugs/352732)

Comments #38 and #77 appear to be popular workarounds, although they don't work for me.

---

### Post by VMC on 2010-08-21
From a terminal do this:
```
sed -n '/load-module module-device-restore/p' /etc/pulse/default.pa

```
output = load-module module-device-restore

Then, do this from same terminal:

```
sudo sed -i 's/load-module module-device-restore/#load-module module-device-restore/g' /etc/pulse/default.pa
```

You can recheck by again doing this:

```
sed -n '/load-module module-device-restore/p' /etc/pulse/default.pa

```

You should now have a '#' in front of the load-module.

Make sure your volume is unmuted before reboot.

---

### Post by mc4man on 2010-08-21
This 'bug' may be audio output, hardware related ( and however unlikely, when you installed maverick

No longer have this issue on a laptop w/ stereo output, does still occur w/ a desktop w/ 5.1 output.

commenting the line does workaround the issue and doesn't produce any noticeable ill effects - on a 5.1 I don't ever use the applet to adjust sound and think it may be 'better' w/ the line commented.

bug specific to maverick is here though I usually never got muted sound, rather sound level set to 0
( there was finally a response to the bug requesting a log, though that was a month ago

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/592016](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/592016)

---

### Post by ranch hand on 2010-08-21
Too many sensible answers here.

How about it is a vast conspiracy to destroy, Destroy I say, the morale of Ubuntu users?

Oh geeze, this isn't over in the community conspiracy formum.  Oops.

---

### Post by amauk on 2010-08-21
as philinux said,
always the same in testing

I've always assumed it's done on purpose to reduce developer annoyance when bisecting the kernel (or other core components) that require constant reboots

---

### Post by ktp on 2010-08-21
I haven't ran into this much but it does happen during testing...and for me, it always seems to be when pulseaudio had crashed and failed to restore values after reboot.

---

### Post by kyleabaker on 2010-08-21
This is affecting my installs of maverick, but I can live with unmuting each time during development stages compared to other problems I've been seeing.

---

### Post by VinDSL on 2010-08-22
Hrm...  That's interesting!

I'm dual-booting 10.04.1 LTS and 10.10 Alpha 3 on this machine.

Lucid doesn't have the "muted on startup" problem.  Soooo...

I simply renamed the *alsa-utils* file in Maverick and copy n' pasted the one from Lucid.  End of problem!

The interesting thing is, I compared the 2 *alsa-utils* files, and the only difference is:

```
$ diff /sbin/alsa-utils /sbin/alsa-utils-orig 
384a385
> 	mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

A single (missing) line is the only difference.

That was an easy fix!  :lolflag:

---

### Post by VinDSL on 2010-08-22
> **pilinux said:**
> Always happens during testing.This is *probably* intentional.

Thinking about it a little...

A dev release is likely to have problems with the audio system, as they are sorting out drivers, config files, and such.

I'm using a very modest amplifier/speaker setup on this machine, however, I could just as easily have it hooked up to my $8000 Klipschorns and Harmon/Kardon amp (110dB @ 1 watt input).

LoL! I would be thoroughly miffed if I lost my hearing, or gave my wife a heart attack @ 3:30 AM, because of an errant update.

Perusing the *alsa-utils* file, it would appear that the 'mute_and_zero_levels' section is called after an error.  If I'm reading it correctly, when an error is detected in the sound system, it zeroes out (and mutes) the volume, restarts the sound card, and exits.

This would correspond with the 'muting problem' that I've been having with Maverick.

In my case, the volume didn't _always_ mute at startup.  When it was muted at startup, I would occasionally see a PulseAudio error @ Plymouth.  The error flashes so quickly, I wasn't able to read the whole thing.  And, AFAIK, Plymouth doesn't have an error log.  But, I'm *guessing* that when the muting occurs, it's because of a sound system error, and it's intentional, on the part of the devs.

Anyway, I *think* you're correct!  It makes sense...  ;)

---

### Post by mc4man on 2010-08-22
I can't see this as being intentional, but have been surprised before.
First the changelog indicates the opposite intention
> 
alsa-utils (1.0.23-0ubuntu1) maverick; urgency=low
..........
 + Stop muting on reboot/shutdown

But the issue does seem directly related to alsa-utils, not if it is installed which doesn't cause this.
With the line in pulse.pa uncommented and alsa-utils installed sound is fine on a reboot (not muted or set to 0

Once alsamixer is run though, upon reboot sound will be  muted and or level sound set to zero.

The line could be removed or set to (possibly the intention
mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=[COLOR="Blue"]0[/COLOR]

---

