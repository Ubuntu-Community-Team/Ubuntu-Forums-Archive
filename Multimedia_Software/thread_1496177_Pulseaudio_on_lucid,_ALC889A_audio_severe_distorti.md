---
title: "Pulseaudio on lucid, ALC889A audio severe distortion"
date: 2010-05-28
forum: Multimedia Software
---

### Post by CrustyRatFink on 2010-05-28
I've read through a lot of posts on peripherally related topics, but I haven't found one to answer this one.

I did a fresh install of Lucid after running for a long while on Karmic with no sound problems at all.

First thing I noticed was... I guess you'd describe it as "skipping"-- as though the timing was garfed.  That led me to the tsched=0 fix for the udev driver.  That seems to have rectified that one...

Now, I've got two notable problems:

- Firstly, and worse, any audio will play for a while and then snap into a distorted, barely audible mode.  It's making sound, of a sort, but it's only barely identifiable as the source.  Mostly bzzzttt bzzzttt bzzzzzzzt. So, if I switch the profile within the pulseaudio volume control configuration panel (e.g., switch from "analog duplex" to "5.1 surround") it'll start working again for a while.  Touch anything else... adjust volume, start another audio app, whatever... and it drops back into bzzztt... switch the profile (even back to the original stereo in this case), and it works again... for a while.

As far as I can tell, there are no errors in any of the logs.  I've tweaked sample size and rate, but it doesn't make any difference.

This is an (Azalia) ALC889A-based on-board audio on a Gigabyte AMD quad-core mobo-- forget the specific model at the moment, but happy to get it if it matters.

OK, the second thing... is that I don't seem to be able to enable RTP multicast from pulse.  As far as I can tell, it simply doesn't work.  This is much less important, but then... it's supposed to work, no?  Again, enabling it usually causes pulse to crash, and if not, it seriously exacerbates the distortion thing.

Soooo... any tips on where I might look for diagnostics?  Any other ideas to try?  I've enable the audio-dev PPA and updated, I've turned off power safe in the modprobe config for the hda module, I've noodled with the sample rates as I've mentioned.  Just can't think of anything else even to look for, and given that I listen to music on it about 10 hours a day... it'd be nice if it worked without my having to switch the device profile every other song.

---

### Post by lidex on 2010-05-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by CrustyRatFink on 2010-05-30
Gladly... thanks for looking at it.

uname -a:
```
Linux hallix 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686 GNU/Linux
```

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

asound version:
```

Advanced Linux Sound Architecture Driver Version 1.0.21.

```

codecs:
```

==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC889A

==> /proc/asound/card2/codec#0 <==
Codec: ATI RS690/780 HDMI

```

edit:
Forgot to add that this is a home-built rig.  The mobo is a GA-MA790GPT-UD3H.  It's got a 4-core Phenom and 8GB RAM.  Let me know if there's any other specs that'd be useful.  

I'm using the on-board audio, though I do have an M-audio 2496 that I yanked cuz Pulseaudio couldn't deal with it in Karmic without a fair amount of brain surgery.  I'll stick that in when I have a moment and see how it goes.

---

### Post by lidex on 2010-05-31
An alsa upgrade is probably the next step. Follow the alsa-upgrade link in my sig.

---

### Post by CrustyRatFink on 2010-06-01
> **lidex said:**
> An alsa upgrade is probably the next step. Follow the alsa-upgrade link in my sig.

Done... no dice.  Rebooted, and while I now have the upgraded ALSA, it started right out playing distorted.  

Now, given that this is a homemade machine, not surprisingly I guess, I couldn't find an exact match in the card model text file.  I tried adding intel-alc889a as the model, but it didn't help.

Also tried upgrading to the snapshot (with the -s option) but it wouldn't build because of some error in the USB subsection.

At that point, I started to feel like I'd gone way over the appropriate time allotment for this.  I've disabled the on-board sound for now.  If I can provide you any diagnostics if you're interested in pursuing this, let me know.  Otherwise, see below for the end of my story...

EDIT:
Because I'm a masochist, I thought I'd double-check that I rebooted after I changed that module model specification.  I just rebooted and re-enabled on-board sound, and it *DOES SEEM* to be working-- though, I wouldn't bet my life on it.  It's been pretty intermittent.  Notably, the surround options are now gone from the pulse configuration panel.  Anyway, I'll try to exercise it a bit over the next few days and report back.  The fact is that I prefer the 2496 card, so this is mostly a technical exercise at this point.

=== peripherally related M-Audio 2496 / ICE1712 lessons

The good news is that I stuck my M-Audio 2496 card back in and was able to get that working-- so far, so good.  

It may be worth noting that while the upgrade script specifies "all" cards, the Alsa driver compilation was *not* building the snd-ice1712 module.  It made 1724 and 17xx-ak4xxx, but neither of those worked, and my system didn't recognize the card at all beyond lspci.

So, I went in to the /usr/src/Alsa.../alsa-driver... tree, and manually set the config for CONFIG_SND_ICE1712=m (it was blank).  Did a make and make install, restarted pulseaudio, and there was my card.

---

### Post by lidex on 2010-06-01
Good work. Please continue to follow up here for the benefit of others with the same problems.

---

### Post by CrustyRatFink on 2010-06-07
Thanks... OK, first update...

Went on a client visit, and when I got back, the system was queued up to do a fairly significant upgrade.  After absent-mindedly allowing that to run (i.e., the system suggested upgrade), nothing works again.  The on-board audio is back to non-functioning distortion, and the M-Audio card has disappeared completely (except in lspci).

So, it would appear that the "standard issue" pulseaudio and ALSA components are fairly significantly, let's say, 'incompatible with my particular system', though I'm fairly tempted to say "garfed."

I'll go back and redo all the steps that I can remember for upgrading everything again and doing the custom builds and see if I can get my sound back.

FWIW, I'm sad to report that both work fine when the machine is booted under Windows-- only to point out that there's nothing wrong with these pieces of very common hardware.  

I'll let you know how it goes.

---

### Post by lidex on 2010-06-07
Sorry to hear that. I'm willing to bet that it's alsa. A kernel upgrade overwrites alsa with it's own version. You'll need to redo that for sure.

---

### Post by CrustyRatFink on 2010-06-08
Yup... re-did the upgrade per your sig, and all is well-ish.  Same deal-- had to go in and manually config the ice1712 module, but she's back and squawkin' again.  

I'm noticing a bit of new... hmm... jitter?  stutter? in the audio, but it's very intermittent and tolerable for now.  The on-board distortion seems to have cleared up, and the M-Audio 2496 is working fine.

Thanks for your assistance with this.  Hopefully, it clears things up for someone encountering audio regression with their upgrade to Lucid.

:guitar:

---

