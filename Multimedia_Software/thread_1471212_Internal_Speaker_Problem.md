---
title: "Internal Speaker Problem"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Blutkoete on 2010-05-03
Hello!

Ubuntu (10.04 - 64 bit) isn't using all internal speakers. Only the right speaker is working, resulting in low volume. If I attach external speakers or headphones, everything is fine.

I checked the Alsamixer, but there's nothing to unmute there that has any effect.

*aplay -i* produces

```
Karte 0: SIS966 [HDA SIS966], Gerät 0: ALC888 Analog [ALC888 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: SIS966 [HDA SIS966], Gerät 1: ALC888 Digital [ALC888 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: HDMI [HDA ATI HDMI], Gerät 3: ATI HDMI [ATI HDMI]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
```"Gerät" means "device", and "Karte" means "card".

The sound settings shows* Internal Audio* and *RV710/730*, but if I switch to the latter I have no sound.

Has anyone an idea?

Thank you very much,

Tobias

---

### Post by Hrairoo on 2011-06-09
I have the same problem on ubuntu 11.04 (32bit). I managed to figure out what is going on. both left and right channels are outputted on the internal laptop subwoofer.

I tested this with:
sudo speaker-test -t wav -c 8 -s 1
sudo speaker-test -t wav -c 8 -s 2

But I still haven't figured out how to fix this.

My hardware is a msi GX700 laptop with a HDA SIS966 card and Realtek ALC888 chip. 

```
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SIS966 [HDA SIS966], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

for me the same thing happens in windows with it's default driver. I guess it's got to be some weird sound card configuration.

---

### Post by mizu12 on 2011-06-27
Same problem on MSI CR720.
No luck with all the "model=" configs in alsa-base.conf.

Tried 10.10, 11.04, Opensuse 11.4 - no success.

All the sound is coming out from the sub-woofer, silent and distorted.

Whole day of pain just for getting rid of MS from my father's notebook.
Ay.

---

### Post by dv310p3r on 2011-07-11
Hairoo, I'm not sure if this will help you or not, but I also had that problem, here's what I did.

First thing, I upgraded my alsa driver to 1.23. Here are some good instructions on how to do that:
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")

Then I added the following line to the bottom of the /etc/modprobe.d/alsa-base.conf file: 
options snd-hda-intel model=targa-dig

Make sure it's at the very bottom then do sudo alsa force-reload.

That did it for me.

I hope it helps.

---

### Post by lidex on 2011-07-14
Any fix will be hardware specific, not universal. There's at least one acer out there that has only one speaker and yet people wonder why sound only comes from one side. Post your alsa-info to see if there is a fix for you. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

EDIT: BTW, I do NOT recommend using the monespaceperso method for the uninitiated. Much better and more support to 
use the alsa-upgrade link in my sig.

---

### Post by Hrairoo on 2011-07-16
Yeah I wanted to leave the alsa alone for as long as I could... but I see it's getting me nowhere so I'll try to "upgrade" the asla now. I'll do the lidex method of the upgrade. Let's see what happens. Crossing fingers :)

oh and the alsa link thingy [http://www.alsa-project.org/db/?f=f14a109d1c9be96bfb90101879424c37ae70d333](http://www.alsa-project.org/db/?f=f14a109d1c9be96bfb90101879424c37ae70d333)

and it's 100% sure this laptop has 3 speakers.

---

### Post by lidex on 2011-07-16
> **Hrairoo said:**
> Yeah I wanted to leave the alsa alone for as long as I could... but I see it's getting me nowhere so I'll try to "upgrade" the asla now. I'll do the lidex method of the upgrade. Let's see what happens. Crossing fingers :)

oh and the alsa link thingy [http://www.alsa-project.org/db/?f=f14a109d1c9be96bfb90101879424c37ae70d333](http://www.alsa-project.org/db/?f=f14a109d1c9be96bfb90101879424c37ae70d333)

and it's 100% sure this laptop has 3 speakers.

> hda_codec: ALC888: BIOS auto-probing.
That usually means your model selection is not working. So remove the targa-2ch-dig thing from alsa-base.conf. Try auto instead, then plain targa (you have no digital in/outs)

---

### Post by Hrairoo on 2011-07-17
ok so I reinstalled alsa. Tried to set the targa without digital and auto both come up with the same result. I still have the sound only out of the woofer.

so,

targa         = no sound,
targa-2ch     = woofer-only,
targa-2ch-dig = woofer-only,
auto          = woofer-only,

---

### Post by lidex on 2011-07-17
> **Hrairoo said:**
> ok so I reinstalled alsa. Tried to set the targa without digital and auto both come up with the same result. I still have the sound only out of the woofer.

so,

targa         = no sound,
targa-2ch     = woofer-only,
targa-2ch-dig = woofer-only,
auto          = woofer-only,

I'd stick with targa and auto. Check your mixer settings as well as profile selection via 'Sound Preferences' on the 'Hardware' tab using each option.

---

### Post by Hrairoo on 2011-07-17
That was the first thing I checked. The mixsers are all on max, mutes are unchecked.

Got to love exotic HW configurations... :D

I also tried installing the realteck driver downloaded from their page, but it returned the same results.

---

### Post by lidex on 2011-07-17
What are your profile options?

---

### Post by Hrairoo on 2011-07-18
Analog Stereo Duplex <- selected
Analog Stereo Output
Digital Stereo (IEC958) Output + Analog Stereo Input
Digital Stereo Duplex (IEC958)
Analog Stereo Input 
and Off

That's the list of it.

---

