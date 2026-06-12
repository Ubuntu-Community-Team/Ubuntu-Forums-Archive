---
title: "Update my Inspiron to Intrepid = no sound"
date: 2008-11-11
forum: Multimedia Software
---

### Post by jswhite on 2008-11-11
I seem to be digging myself in a bit deeper with this, so I'm going to stop trying to "fix" it myself and see if I can get myself.

I have an Inspiron 1420n, preloaded with Edgy IIRC. It's been upgraded a few times as new releases come out. Anyway, I recently upgraded to Intrepid a couple of days ago. When I did, I lost all sound. From what I can tell, the hardware end of things does/did appear to be working, there's just no sound coming out.

Here's what I've done so far:

1. Attempted the fix noted [here]("http://ubuntuforums.org/showthread.php?t=616845"), with no success. That worked for me when I did a previous upgrade (I believe using the "3stack" model), but here it gave me nothing. I even jumped around trying a whole bunch of different models to see if anything would work, and thus far I've found nothing.

2. Checked Alsamixergui, sound prefs, and everything else I could think of to make sure the volume isn't muted, turned down, or otherwise set incorrectly. It isn't.

3. Switched everything over to OSS, since I found another thread where someone said that worked for them. It didn't work for me; in fact I had the exact same problem.

4. Gone through the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") to see if that would help. I actually made the problem worse (go me!). aplay worked, lspci listed my sound card & driver (snd-hda-intel), etc. Everything seemed as though it *should* be working, it just didn't. So, I followed the instructions to purge alsa-related packages and reinstall them. After I rebooted, I still have no sound, but now I have two new problems:

a.) "aplay -l" used to output this:
```
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Now, it only has the "Analog" version listed.

b.) It does not appear that a kernel module is being loaded anymore. When I purged, the package "alsa-modules-2.6.24-16-generic" was removed; I cannot find this package in the apt repos to reinstall it. I tried following the instructions to recompile the modules from alsa-source using module assistant, but I'm getting errors on the build. Here's the relevant portion of the logfile:

```
/usr/src/modules/alsa-driver/acore/sound.c: In function ‘snd_request_other’: /usr/src/modules/alsa-driver/acore/sound.c:100: warning: format not a string literal and no format arguments CC [M]  /usr/src/modules/alsa-driver/acore/init.o /usr/src/modules/alsa-driver/acore/init.c: In function ‘snd_card_register’: /usr/src/modules/alsa-driver/acore/init.c:568: warning: passing argument 5 of ‘device_create’ makes pointer from integer without a cast /usr/src/modules/alsa-driver/acore/init.c:568: warning: format not a string literal and no format arguments 
```

There was more in there; sorry for the poor formatting, I don't know where the logfile for that is stored and copying from the terminal did not work so well.

Either way, I'm still basically stuck in the same spot: no sound, with no discernible reason why it's not working. Any help would be greatly appreciated.

---

