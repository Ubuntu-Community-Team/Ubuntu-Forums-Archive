---
title: "Jaunty and PCI-Express SB X-Fi Xtreme"
date: 2009-06-09
forum: Multimedia Software
---

### Post by AoSteve on 2009-06-09
Alright, I have a P7nDiamond that came with the MSI version of the SB X-Fi Xtreme sound card.   After MUCH reading, none of the search posts have resulted in ANY sound from my system at all.

After all the searching, I've found guides that claim to work by downloading packages and running make install commands and that, still nothing.   The one guide, which is probably the closest I've found to use was [How-To: Creative X-Fi](http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative+Sound+Blaster+Fi) by Nullhead.    After toying with this for hours, I've came to the fact that this method is NOT going to work at all.

Being that I have a PCI-Express version of the X-Fi, I figured I have to follow the link there and check this part out.  Here's a quote of that post...

> **CptHook said:**
> Nullhead you may want to add this info to your front page.

If you check dmesg you may see a line reading something like
CTALSA: probe of 0000:03:00.0 failed with error -2

After install you are not getting the driver to completely load you need to check the subsystem of your sound card.


An example of a non working card.

#lspci -v
04:00.0 Audio device: Creative Labs Device 000b (rev 03)
    Subsystem: Creative Labs Device 0043
    Flags: bus master, fast devsel, latency 0, IRQ 9
    Memory at e4200000 (64-bit, non-prefetchable) [size=64K]
    Memory at e4000000 (64-bit, non-prefetchable) [size=2M]
    Memory at e0000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
        Kernel modules: ctxfi

An example of a working card.

#lspci -v
03:00.0 Audio device: Creative Labs Device 000b (rev 03)
    Subsystem: Creative Labs Device 0043
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
    Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: CTALSA
    Kernel modules: ctxfi

Notice the Kernel driver in use: CTALSA line on the working card.

The problem lies in the fact that Creative did not add all the subsystems to the ctdrv.h file.

Check what subsystem you have line 2 of the lspci -v, if you have a newer PCIe card your subsystem most likely will be 42 or 43. make the below adjustments to the ctdrv.h file and remake the driver.

#define PCI_SUBSYS_CREATIVE_SB0880    0x0041

to

#define PCI_SUBSYS_CREATIVE_SB0880    0x0042
or 
#define PCI_SUBSYS_CREATIVE_SB0880    0x0043

after a reinstall and reboot your sound should work.



Well, after following this and running the **lspci -v** command, I get this...

```

0b:00.0 PCI bridge: Creative Labs Device 7006
    Flags: bus master, fast devsel, latency 0
    Bus: primary=0b, secondary=0c, subordinate=0c, sec-latency=64
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>
    Kernel modules: shpchp

0c:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
    Subsystem: Creative Labs Device 0010
    Flags: bus master, medium devsel, latency 64, IRQ 5
    Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

```

So, mine says it's on "0010"?     I edit the ctdrv.h file and change the subsystem to the 0010 that I found, and still nothing.  I tried the other ones listed in the original post as well...   

Nothing there.   I tried reinstalling the alsa drivers as forementioned in another post, and I'm not going to even get in detail here as it changed absolutely nothing.   In the original "how-to" thread, the picutre shows that "Creative ALSA X-Fi WaveOut/WaveIn" is under the menu.  The closest I can see in the sound properties is,  "ALSA Advanced Linux Sound Architecture" and "OSS -  Open Sound System".

The test on the ALSA prompt reveals a box that seems like it's testing and let's me click "Ok" when the I feel the test has completed.   Upon trying the OSS method I get this error..

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

A third option, "PulseAudio Sound Server" can have this test executed as well but results in the same test box running but seemingly doing nothing at all.   No sound has came from the speakers at all, not even with the Live CD. 

So my question here is, has ANYONE got the PCI Express version of the Sound Blaster X-Fi Xtreme working under 9.04?   And if so, what did you have to do?   I don't care about 5.1, I just want sound at all.   I run a Dual Boot configuration, as my college software has to be ran from Windows, so any super hi definition audio or whatnot can be left for windows.  I just want some basic sound, anything at all!   

Thanks ahead of time,
Steve

---

### Post by pinan on 2009-06-18
Possible SOLUTION :D:D:D

I have the same sound hardware as you do, ie
 
Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
        Subsystem: Creative Labs Device 0043
I tried JaJaJim solution, it ie 
[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz)


Code:

./configure --with-cards=ctxfi , make , sudo make install

Kernal is  2.6.28-11-generic release is 9.04.

lsmod returns snd                    77896  16 snd_ctxfi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device

My motherboard had an on board sound system,  I disabled that in the BOIS.

It worked for me,  my desktop is gnome, but I can't see that changing anything.

The gnome settings are Autodetect, for the mixer mine is set to Creative X-FI(Alsa mixer)

I did discover some warning messages in /var/log/messages.

---

### Post by JackCorbae on 2009-07-27
I'm in the same boat - MSI Ecplise mb with the SB X-Fi Xtreme Audio PCIe card included.

Tried everything so far - no luck.

Thinking the suggestion some one made to toss the X-Fi and go out and buy another card is starting to sound good!

---

### Post by AoSteve on 2009-07-29
I just ended up using my Sound Blaster Live in parallel with the X-Fi so I could use the SB Live with Ubuntu with NO SETUP.   IT worked straight on boot.  The X-Fi is used in Windows only, and the Live! is disabled therein.   Works perfect with my splitters and a bit of wiring mastery LOL.

---

