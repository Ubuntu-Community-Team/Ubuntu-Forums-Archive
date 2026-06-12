---
title: "Different problems with 8.10 (CD boot) and 8.04.1 (wireless)"
date: 2009-01-20
forum: Mythbuntu
---

### Post by faginbagin on 2009-01-20
I'm trying to upgrade my system to mythtv 0.21 by installing mythbuntu, but both 8.10 and 8.04.1 are giving me trouble. The machine currently is running ubuntu 7.10 and I used Myth Control Centre to ease set up a year ago. Fortunately I've set it up to multi boot so I can easily go back to my working configuration.

Mythbuntu 8.10 problems:
I can boot the desktop ISO, but when I select any of the options (Live CD, Install, integrity check, etc), it fails. It seems to have trouble locating the CD on either my IDE CD burner (LITE-ON CD-RW SOHR-5239S) or my SATA DVD burner (Sony OPITARC AD-7170S). And with quiet and splash disabled, I see error messages for the SATA burner that look suspiciously like error messages I saw with debian etch. In fact that's what lead me to ubuntu 7.10 last year because the problem was a bug in the sata_sil driver that was fixed in the 2.6.22 kernel. Now I'm concerned that bug or something similar might have crept back into the 2.6.27 kernel. The motherboard is an ECS RS482-M754 with RS482 Northbridge (NB) and SB400 Southbridge (SB) chipsets.

Mythbuntu 8.04.1 problems:
I was able to get past the problems I had with 8.10 and could get into the live CD environment using either IDE or SATA drives, so I went ahead and installed 8.04.1. My problem is that I can't get my wireless device working, a Linksys WUSB54G. It works with the rt2570 legacy driver on ubuntu 7.10. I'm guessing the next-generation rt2x00 driver included in the 2.6.24 kernel in 8.04.1 is still pretty buggy. But maybe it is more stable in the 2.6.27 kernel in 8.10?

I'm trying to decide where to go from here. Right now, I see two approaches:

1) Stick with 8.04.1. I assume I'll be able to use the legacy rt2570 driver and be able to blacklist the rt2x00 driver. What I don't like about this approach is that I'd really like to get WPA working, something that I don't think the legacy driver supports.

2) Try a little harder to load 8.10. Maybe I'm imagining a problem with the support for my SATA controller and I just need to provide an appropriate root= option when it's time to boot the installer? Or try it once and if it fails, accept I'm not going to get WPA encryption for a long time. I'm guessing the option would be:
root=/dev/hdd for the IDE drive, and
root=/dev/scd0 for the SATA drive

My questions are:
- If you're running 8.10 with a SB400 chipset and a SATA DVD burner, can you burn DVDs with the drive?
- If you have a Linksys WUSB54G, what distro and driver are you using? Have you gotten WPA encryption to work?
- If you were me, which of the above approaches would you pursue first?
- Anyone care to suggest another approach?

TIA,
Helen

---

