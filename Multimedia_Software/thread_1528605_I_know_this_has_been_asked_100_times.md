---
title: "I know this has been asked 100 times"
date: 2010-07-11
forum: Multimedia Software
---

### Post by Zerorebels on 2010-07-11
i know this has been asked multiple times but none of the answers were able to help me fix my issue, so heres the deal i got fed up by the fact that the sound came out from both speakers and headphones so i decided to play around with the sound settings what i did was go to,
system>preference>sounds
then output
and disabled and re-enabled it to test if that was my internal speakers of which the sound was coming from apparently it was and re enabling it just messed up the sound now when ever i go to watch a video online i have no sound, when i boot up, i have sound you know the beep and things that you hear when you turn on your computer,im not sure what you need exactly but this is some basic info maybe it'll help you try to help me fix this issue,

Linux 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
and im running Ubuntu 10.04
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

*Advanced Linux Sound Architecture Driver Version 1.0.21.
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5
==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

its a HP DV6

 pretty brand new only a couple of months old.
AMD Turion x2 (64bit compatible)
Ati Radeon 4530
4GB
sound was working great before but i just wanted to listen to music  without disturbing anyone else with it,

Thank you for everything,
Zero

Edit: i forgot to mention i can no longer open Sound, it keeps saying
"Waiting for sound system to respond"

---

### Post by MIJ-VI on 2010-07-11
Hi Zerorebels.

In Terminal type [FONT=Courier New]alsamixer[/FONT] and see if your sound card is selected and if any inputs or outputs are muted.

--------

BTW. On my AMD notebook (an Acer Aspire 5517-1536) the audio won't function properly unless there's a Wi-Fi adaptor plugged into one of the Acer's two USB 2.0 ports at boot time.

It's the last AMD/ATI-based product I'll ever buy. :P

---

### Post by Zerorebels on 2010-07-11
i have gnome-alsamixer but none of the sounds are muted, except "system beeps" is there anything else i could check? heres a screenshot of gnome alsamixer.[IMG]http://i25.tinypic.com/24x4cgm.png[/IMG]

---

### Post by Zerorebels on 2010-07-11
it seems to have fixed itself. thanks anyways [MIJ-VI]("http://ubuntuforums.org/member.php?u=955375")

---

