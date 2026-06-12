---
title: "[SOLVED] SB Live 5.1 AWOL"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by rillip on 2007-07-11
Okay, I've had my sound working before, and it quit.  Using the sound guide that's posted here, I got it working again, but now, for no reason that is known to me, it's not working again.

If I do a

```
lspci
```

the device apepars.  If I try and open the alsa mixer, I get

```
alsamixer: function snd_ctl_open failed for default: No such device
```

The device does not appear in kmix (I'm running kde), only my onboard audio does.

At the end of the day, I'd like to have my SB Live 5.1 (which is physically working) to be the default and have it play again. I'd then like to lock my settings so I can't possibly goof this up.  I might have caused this by trying to set the default a few weeks ago (it kept defaulting to my onboard), and I just now noticed it after a restart.

I have tried 

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

and then

```
 sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo modprobe snd-emu10k1 
```


snd-emu10k1 is listed in my /etc/modules file

my  /etc/modprobe.d/alsa-base file has snd-emu10k1 listed as index 0

I'm in the audio group

```
aplay -l
``` only shows my onboard card

Thanks in advance for any help!

---

### Post by rillip on 2007-07-11
Running alsamixer no longer gives an error after setting the default to onboard, using ```
 alsamixer -c 0
``` but alsamixer 1 gives usb, and alsamixer 2 or more gives "wrong argument."

So the device is detected, it seems like an alsa settings error, but I've already purged and reinstalled.  Any ideas?

---

### Post by rillip on 2007-07-12
Well, I seem to be on my own for now on this one, but for anyone who finds this later, I see that /var/log/dmesg is giving the following:

EMU10K1_Audigy: probe of 0000:00:09.0 failed with error -16

not sure what this means yet, will update this when I know more.

Update: error 16 means the device is busy.  Not sure how to resolve this yet.

Update: It was marked as busy because the interupts for it were not set right.  I found that this was because I had disabled ACPI.  I didn't think this had anything to do with the issue, but when I removed the acpi=off, it started to work like a charm again.

Ah well, hopefully somebody out there will find this the next time they need help with a sound problem!

---

### Post by just-want-one-attachment on 2008-01-15
> **rillip said:**
> Well, I seem to be on my own for now on this one, but for anyone who finds this later, I see that /var/log/dmesg is giving the following:

EMU10K1_Audigy: probe of 0000:00:09.0 failed with error -16

not sure what this means yet, will update this when I know more.

Update: error 16 means the device is busy.  Not sure how to resolve this yet.

Update: It was marked as busy because the interupts for it were not set right.  I found that this was because I had disabled ACPI.  I didn't think this had anything to do with the issue, but when I removed the acpi=off, it started to work like a charm again.

Ah well, hopefully somebody out there will find this the next time they need help with a sound problem!

Where did you have to go to turn on ACPI?   I'm having a similar issue.  TIA.

---

