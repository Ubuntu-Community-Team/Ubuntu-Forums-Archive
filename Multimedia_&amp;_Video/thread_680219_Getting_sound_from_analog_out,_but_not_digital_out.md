---
title: "Getting sound from analog out, but not digital outs"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Levander on 2008-01-27
On my GA-P35-DS3L motherboard, I got sound working via the analog outs, but not the digital outs.  

Do I have to configure ALSA somehow so that it's using the digital outs, and not the analog ones?

It's one of those Intel HD Audio, onboard cards.

---

### Post by Metaljaz on 2008-01-27
Right click on the volume button in the top right hand corner. Open volume control and make sure that PCM is not muted. Mute PC speaker and Line in to start with.
Then again right click on the volume control button and select preferences. try selecting alsa mixer and then scroll down to PCM. Give that a try.

---

### Post by Levander on 2008-01-27
Tried it, nothing.

One thing I'm wondering about.  When I open the volume control, there's a File->Change Device menu that lets me select either "HDA Intel (Alsa Mixer)" or "Realtek ALC888 (OSS Mixer)".  I think I'm supposed to have it set to the first one, the HDA one, so that's most of what I been playing with, but I been playing with both.

Also, 'aplay -l' says I have two sound cards:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So, maybe ALSA is using the first sound card but not the second?

---

### Post by Levander on 2008-01-28
Well, I really have no idea how I got it working, but it works now.  I was following the instructions on these pages:

[http://forums.gentoo.org/viewtopic-p-4441706.html](http://forums.gentoo.org/viewtopic-p-4441706.html)
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

But, I didn't get far enough in understanding them that I actually reconfigured anything.

Running the "cat /dev/urandom > /dev/dsp" and "speaker-test" commands from the Gentoo forum page, I noticed I was getting sound out my audio optical out.  I tried totem for like the 20th time, and all the sudden it works.  I have no idea what happened...

I'm about to reboot and see if it still works after I reboot.

---

