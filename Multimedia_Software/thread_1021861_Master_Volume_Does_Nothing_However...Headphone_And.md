---
title: "Master Volume Does Nothing However...Headphone And PCM volume does."
date: 2008-12-26
forum: Multimedia Software
---

### Post by morbid_bean on 2008-12-26
Im using some basic computer speakers through an onboard sound card and the only way of controlling the sound its with the knob on the speaker and adjusting the Headphone and PCM controls under the Volume Control thing...when raising the master volume it does nothing... wondering if there is a fix?

---

### Post by cariboo on 2008-12-26
Usually if you leave the PCM control at near full, you can use the Master Volume control to turn the volume up and down.

Jim

---

### Post by namdung on 2008-12-26
> **morbid_bean said:**
> Im using some basic computer speakers through an onboard sound card and the only way of controlling the sound its with the knob on the speaker and adjusting the Headphone and PCM controls under the Volume Control thing...when raising the master volume it does nothing... wondering if there is a fix?

In *System-->Preferences-->Sound*

Set *Default Mixer Tracks - ALSA* and ensure ***Master*** is selected.

---

### Post by morbid_bean on 2008-12-26
> **namdung said:**
> In *System-->Preferences-->Sound*

Set *Default Mixer Tracks - ALSA* and ensure ***Master*** is selected.

I Have tried all of the diffrent mixer tracks and selected Master but still not working...thanks though :D

---

### Post by Johan D. on 2009-01-02
Hi
 I had almost a similar problem recently. "almost" because I just installed Fedora and this problem came out of my Gentoo box when setting a PulseAudio server between these two computers ... so I decided to post here ^^. (Oh guy, the GNU/Linux world could really become disturbing !)
Back to our problem: I managed to get the master volume fixed by tweaking the kernel sound module. Here is how I proceeded: 

[LIST=1]
[*]Find your sound module
```
$> lsmod | grep snd
snd_via82xx            20948  0 
...
```

[*]Look at the alsa documentation in the kernel source
I was lucky to being able to access the /usr/src/linux/Documentation/sound/alsa/ALSA-Configuration.txt file. But you can easily find a similar one [online]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt").
There you can read that my card (via82xx, and probably the intel8x too) accept a special argument called *ac97_quirk* when you load the module.

[*]Get the correct quirk
Try different value for the quirk option, for example:
```
$>sudo modprobe -rv snd_via82xx
$>sudo modprobe -v snd_via82xx ac97_quirk=swap_hp
```
(This option suppressed my volume "headphone" and merged it with "Master")
[/LIST]

On my Gentoo box, I just add into the file */etc/modprobe.d/alsa* the following line:
> options snd_via82xx ac97_quirk=swap_hp
And then I ran `sudo update-modules` to ensure that this option is activated at each boot.
Sorry, but I do not have the exact command for Ubuntu. I suggest you'll look at /etc/modprobe.conf ('man modprobe.conf') for some hints.

Regards,
Johan

---

