---
title: "changed soundcard - lost sound"
date: 2011-04-10
forum: Multimedia Software
---

### Post by judy001 on 2011-04-10
I'm having a bit of a furball trying to change a soundcard.  I took out an Audigy card.  KDE detected the removal of the old card and asked me if I wanted to remove the drivers.  I said yes.   I went into the bios and enabled the onboard sound.

Now I've got no sound so I guess I've got some configuration to do.  So far:




aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


=====================================================


lspci -v


00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
        Subsystem: ATI Technologies Inc SBx00 Azalia (Intel HDA)
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at fcbf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


(Further down the list it shows this)


05:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. Device 8326
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fe97c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


=====================================================


sudo modprobe snd-
FATAL: Module snd_ not found.


=====================================================



So ...... what's the next step??

---

### Post by judy001 on 2011-04-10
Modprobe refused to let me load the module manually, so I kept digging.  This is a fairly new Asus board and the on-board sound was identifying itself as VIA 440.   After much digging I think there is no solution yet for 32 bit Kubuntu.

I reinstalled the Audigy and locked out the on-board soundcard in the bios.  I'm back to my original problem -- I hear the sign-on and shutdown tones but I have no sound in videos at all.  This original problems started after installing the Nvidia proprietary vid driver.  Also, on boot, it's complaining: 

===============

Phonon: KDE's Multimedia Library
The audio playback device "Jack Audio Connection kit" does not work.

===============

How do you troubleshoot something like this?

---

