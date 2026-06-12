---
title: "Is there any way to use my Emu card in ubuntu?"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by Anarchy965 on 2007-02-22
I have an E-mu 1212m soundcard and it won't work when I'm using the liveCD is there any way to get emu cards to work in ubuntu? I would really like to make a dual boot Ubuntu/Windows XP system, but if the emu card is completely incompatible I may not want to do this yet. So has anyone on the forums ever gotten an E-mu 0404 or 1212 card to work in Ubuntu? By the way I am running the 64-bit 6.06 LTS LiveCD on the following system:

-Asus A8N32-SLI MoBo
-Athlon 64 3200+ (socket 939) CPU
-XFX 7800GT video card
-2x Western Digital 80GB SATA2 Hard Drive in RAID 1 using the RAID controller from my NVIDIA nForce4 SLI chipset
-Emu 1212m PCI audio card

---

### Post by deadgobby on 2007-02-22
[http://ubuntuforums.org/showthread.php?t=199597](http://ubuntuforums.org/showthread.php?t=199597)
 It seems that Emu is not to linux friendly. It kind of strange since EMU and Sound blaster had joined forces years ago. I do not know how much you love your sound card or you are tight on the cash flow. Sound Blast Live sound card is fairly cheap. All so you are running a live CD and if the live CD does not detect the chances are that you are going have to do some mojo when you install Ubie. Sorry for the dim news. Maybe some one did get it working with the live CD.
Gobby

---

### Post by polarfox on 2007-11-15
I hope a driver for 1212 is on the way. As other says, I'd pay a few bucks for it.:)

---

### Post by roki on 2007-12-09
Works with ALSA 1.0.15.

You just have to build alsa-driver, alsa-firmware, alsa-lib and alsa-utils from source.

Source code is available at [ftp://ftp.alsa-project.org/]("ftp://ftp.alsa-project.org/").

Some more information is available at [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

I'm not sure if Ubuntu 7.10 is enough since I upgraded my system to hardy before that ALSA upgrade.

---

### Post by hetbeest on 2008-02-13
It works fine in 7.10 after indeed building alsa-driver, alsa-firmware, alsa-lib and alsa-utils from source. You might have to put the firmware in the right place, but the docs should point that out clear enough. If not, let me know.

---

