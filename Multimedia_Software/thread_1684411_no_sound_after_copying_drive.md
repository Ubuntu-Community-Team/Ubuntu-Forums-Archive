---
title: "no sound after copying drive"
date: 2011-02-09
forum: Multimedia Software
---

### Post by mystmaiden on 2011-02-09
I upgraded my Ubuntu 10.04 hard drive, which worked really well except that I lost sound on both drives. The sound icon on the top task bar disappeared as well. I was able to get the sound back on one drive by adjusting the audio settings under users and groups  (still no sound icon though) on the other, I've had no luck at all. I tried reinstalling pulse but that didn't seem to help at all. 

This is my onboard sound -

```
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
    Subsystem: Micro-Star International Co., Ltd. Device 7380
    Flags: medium devsel, IRQ 22
    I/O ports at b800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: VIA 82xx Audio
    Kernel modules: snd-via82xx

```I checked bios and didn't find anything there to enable. I hooked up a different drive with puppy linux on it and the sound worked but I'm wondering what the capabilities <access denied> means above.

I'd love some help trouble shooting this, its got me puzzled.

EDIT - the one thing I hadn't checked system/preferences/sound the very last tab had a check mark next to 'mute'. Not sure why or how it got that way but its fixed now. The speaker icon I can live without if I can listen to music :)

thanks

mystmaiden

---

