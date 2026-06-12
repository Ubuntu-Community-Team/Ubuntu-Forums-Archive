---
title: "[solved] No microphone or capture in asus eee pc 1005he or 1008he"
date: 2009-07-04
forum: Multimedia Software
---

### Post by jmjohn on 2009-07-04
Oddly, I couldn't get any microphone output.  Oh yeah, and I have a 1005ha-p.

First, the ideas:

Under Volume Icon -> Volume Control you can see that you have the option to select a device.  Lots of devices, huh?

FIrst, configure your Alsa and OSS mixers.  Alsa is the base, which sends your sound over to Pulse, which sends it to your applications.  Pulse is a sound server that allows other applications to share the Alsa mixer device.  OSS is older and phasing out.  

Therefore, under Preferences -> Sound it's best practice to use all Pulse, and if you can't get that to work, use Alsa.  Pulse is a layer between you and the Alsa Mixer.  Pulse is your friend.

Click the volume icon -> volume control -> preferences and enable all mic/capture devices.

Next, you must do something that I don't understand, but I had to do for my sound to work.  Found here: [http://urbanoia.net/?p=39](http://urbanoia.net/?p=39)
> The trick, it seems, is to:

    * go into alsamixer (that is, from a terminal, type "alsamixer",
    * tab to the inputs grouping,
    * move the cursor to the &#8216;capture&#8217; control
    * hit &#8217;space&#8217; to change &#8216;&#8212;&#8212;&#8217; to &#8216;CAPTUR&#8217;
Next, under Sound and Video, try the sound recorder and record your voice.  You can also test under Preferences -> Sound and if you get feedback, the mic works.

Once you get the sound tested and working, if you want Skype, download the static non-OSS skype version under the options, then set the Sound Devices to be all either pulse, and set the microphone to be one of the Intel hw options, trying each until you find one that works.

Now it works.  Go figure.

---

### Post by theworldisnormal on 2009-07-23
hi john,
did exactly what you described but without success...

---

### Post by igorzwx on 2009-07-23
see Wikipedia -> OSS (open sound system)

---

### Post by UncoElite on 2009-07-25
Yeah I've tried this aswell and can't get anything to work. 1005ha

---

### Post by oiad on 2009-08-29
This worked for me on a 1005hab, but I installed the skype-static-oss from the medibuntu repos after the prior steps.

---

### Post by irpsit on 2010-12-27
I tried every solution I found in the web, and nothing works for me. This is the the most enduring problem I have with Ubuntu!

Ubuntu 10.10, Asus eee 1001px
No internal microphone

---

### Post by meditatingfrog on 2011-02-01
> **irpsit said:**
> I tried every solution I found in the web, and nothing works for me. This is the the most enduring problem I have with Ubuntu!

Ubuntu 10.10, Asus eee 1001px
No internal microphone

have you tried this:  [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")?

also, i know with my mic set up (i am using 10.10 desktop), i need to have "front mic" in alsamixer in order for it to capture audio.

---

