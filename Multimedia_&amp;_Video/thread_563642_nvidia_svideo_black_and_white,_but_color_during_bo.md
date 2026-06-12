---
title: "nvidia svideo black and white, but color during boot"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by shailiha on 2007-09-30
Hello.

Using a GeForce 6600 GT, s-video out I had color output until I recently restarted X after a system update. Now I have color during boot (Bios and Ubuntu loading progress bar), but as soon as X kicks in it is all in black and white.

The TV supports NTSC, NTSC-M, PAL and SECAM, and like I said since it had color until just recently the cable is fine.

I've tried several combinations of 
        Option          "TVOutFormat"   "SVIDEO" or "COMPOSITE"
        Option          "TVStandard"    "NTSC-M" or "PAL-G" or "PAL-B" or "PAL" or "NTSC"
under both Device and Screen to no avail.

Between having color and losing it, I made no changes at all to my xorg.conf file.

Does anyone have any suggestions?

Edit:

Nevermind, after a few reboots it just started working like it should.

---

### Post by KnightCode on 2007-10-01
I just got a Dell XPS 410 with Ubuntu and a nVidia 8300 GS. I'm having exactly this problem. I've tried every different kind of TvOutFormat, including a bunch of PAL formats (should be NTSC-M since I'm in the US). I've tried changing the TVStandard to COMPOSITE (should be SVIDEO). And my version of nvidia-settings, for whatever stupid, frustrating reason, has no option to alter a "saturation" or "hue" setting.

---

### Post by Brian96 on 2008-06-14
I just bought a couple of GeForce 7XXX series cards on ebay and I am having this trouble with both of them and in all OSes.

One machine has a 7600 and is connected to the TV using the HDTV dongle that came with the 7950 I also bought, and it is plugged into the component connectors on my TV. The other machine has the 7950 and is connected via s-video (using the identical setup I had my old Radeon X300 working just days ago, so it is not a cabling issue).

I realize this is not an Nvidia hardware forum, but I thought I'd post here since I'm already a member (and I've been waiting forever for my confirmation e-mail for a more relevant forum).

Any ideas? I bought Nvidia cards because of the workarounds you have to do to get ATI cards working with Compiz and the like. I had no idea I was going from the frying pan into the fire!

---

### Post by overdrank on 2008-06-14
> **Brian96 said:**
> I just bought a couple of GeForce 7XXX series cards on ebay and I am having this trouble with both of them and in all OSes.

One machine has a 7600 and is connected to the TV using the HDTV dongle that came with the 7950 I also bought, and it is plugged into the component connectors on my TV. The other machine has the 7950 and is connected via s-video (using the identical setup I had my old Radeon X300 working just days ago, so it is not a cabling issue).

I realize this is not an Nvidia hardware forum, but I thought I'd post here since I'm already a member (and I've been waiting forever for my confirmation e-mail for a more relevant forum).

Any ideas? I bought Nvidia cards because of the workarounds you have to do to get ATI cards working with Compiz and the like. I had no idea I was going from the frying pan into the fire!

Hi and I do not know if you realize it but this thread is in the forum archive and you may want to create a new thread in the forums for help. :)

---

