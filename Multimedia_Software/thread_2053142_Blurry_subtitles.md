---
title: "Blurry subtitles"
date: 2012-09-04
forum: Multimedia Software
---

### Post by kill o matic on 2012-09-04
I've noticed recently that the default video output driver (xv) in both Smplayer (with mplayer2) and VLC player causes subtitles to be displayed with an added blur in fullscreen. It's likely an issue with scaling, since it's a lot less pronounced in HD video. It disappears after switching to gl and in the case of VLC to X11 as well. It happens with both .&#1072;ss and .srt subtitles, with libass on and off and with embedded and external subtitles.

I'm running Ubuntu 12.04, 64-bit version on an Acer Aspire with an Intel/Geforce GT520M GPU with drivers from the "x-updates" ppa. Attached is a composite screenshot with the same test subtitles rendered with xv and gl in Smplayer for comparison.

---

### Post by SeijiSensei on 2012-09-04
Hmm.  I watch a lot of subtitled material and don't see that on my NVIDIA 9500GT with xv and smplayer.  I'm just using the stock NVIDIA proprietary driver.  Mine do typically appear with drop shadows, though, like the attached.  This is with 64-bit Kubuntu 12.04. 

Maybe it's a problem with the video driver?

---

### Post by kill o matic on 2012-09-05
For .&#1072;ss subtitles, the shadows depend on the style settings in the script, unless you override them with Smplayer's options.

It probably is the video driver, since I can't get vdpau working and that's supposed to be made specifically for NVIDIA. Maybe it has to do with the Optimus setup not being supported, but I image the Intel card is more than capable of scaling vector graphics images. Is xv supposed to include hardware acceleration?

Edit: Tried the stock NVIDIA driver and it's the same thing. Any other ideas?

---

### Post by SeijiSensei on 2012-09-05
With the NVIDIA driver, could you use VDPAU?  If not, then you're still on the Intel graphics chip.  Have you looked into the [Bumblebee Project]("http://bumblebee-project.org/")?

Have you tried forcing the system to use the NVIDIA chip in the BIOS and see if that helps with either xv or VDPAU?

I'm pretty sure there is no hardware acceleration in the xv driver.  That usually requires a proprietary driver that is written to talk to the graphics card.

---

### Post by kill o matic on 2012-09-05
BIOS only has "Integrated" and "Switchable" options, and neither changes anything that I can notice. I've tried Bumblebee but it doesn't do anything for me, or maybe I'm doing it wrong. Are you supposed to remove your previous NVIDIA drivers and not update them after installing it?

And even with just the Intel chip, shouldn't it be able to handle something as basic as subtitle rendering?

---

### Post by SeijiSensei on 2012-09-05
I don't have any hardware that uses Optimus (thank goodness) so I can't help much further.  You might search the various threads on Optimus or Bumblebee.  There's also [this thread](http://ubuntuforums.org/showthread.php?t=2014681) which suggests an alternative to Bumblebee called Prime.

I have a laptop with an Intel 945GM adapter.  I don't recall having blurry subtitles using SMPlayer on that either.

---

### Post by kill o matic on 2012-09-05
Prime is what NVIDIA will be relying on when they finally roll out the official Optimus support for Linux, or so I hear, but who knows when that will be. For now it's still way too experimental, especially when I can just select another driver in Smplayer.

I'll give bumblebee with nouveau a try, since I'm not getting anything out of the NVIDIA card at the moment. Thanks anyway.

---

