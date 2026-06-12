---
title: "Multiple sound card troubles (hardy)"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Willothewisp on 2008-05-11
Hi there,

I've already spent hours on this forum trying to fix my sound problems myself, but I need some help to fix this in a structured way.

I've got an onboard soundcard (ICH4 - Intel 82801DB-ICH4) and an external USB soundcard (Creative Soundblaster MP3+). In Gutsy I managed to use my USB sound card by disabling the compaq audio device in my BIOS. After upgrading to Hardy I still have this audio device disabled, but still sound comes from my internal speakers instead of my soundblaster system.

I'll need some help in fixing this problem. Maybe my soundcard hasn't got the right drivers in Hardy? How can I tell? And is there a way to shut off the internal soundcard? I really just need the soundblaster.

Some output for common questions:
cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981A at irq 23
 1 [MP3            ]: USB-Audio - Sound Blaster MP3+
                      Creative Labs Sound Blaster MP3+ at usb-0000:00:1d.1-2, full speed


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: MP3 [Sound Blaster MP3+], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci -v
(won't paste the output, is too long but there's no MP3 soundblaster listed, just the Intel device.)
Does this mean my external card isn't installed well? How can I solve this?

Thanks a lot!

---

