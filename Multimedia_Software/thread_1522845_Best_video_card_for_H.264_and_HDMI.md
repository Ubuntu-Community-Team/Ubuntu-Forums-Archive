---
title: "Best video card for H.264 and HDMI?"
date: 2010-07-02
forum: Multimedia Software
---

### Post by embolalia1187 on 2010-07-02
I'm looking to put a new video card in my desktop. I need one that will be able to handle H.264 at 1920x1080, and I would like to find one that can do HDMI with audio. Shopping for video cards, as I heard somewhere, is the kind of thing that makes you want to bang your head against a wall until you go blind, because then you won't need to worry about it any more... So I'm hoping someone will be able to recommend a model, or at least a chipset or something, before I rip my own eyes out.

Thanks!

PS: Did I mention it's 64-bit? Don't know how much that'll matter, as hardware hasn't seemed to be much of a problem so far.

---

### Post by VeeDubb on 2010-07-02
Anything nvidia.

1080p video really isn't that tough for a video card.  ION video cards in premium netbooks and set top boxes play 1080p video just fine, and they're the equivalent of a 9400, which was a lower-middle range video card from a couple of years ago.

Just be certain that you're using a video application that will offload to the graphics card, and you'll be fine.  Boxee, XBMC, and current versions of mplayer.  I'm not sure if the mplayer in the standard feeds is using VDPAU for acceleration, or if you need to add a different feed, but it's certainly out there.

As far as HDMI, this is irrelevant unless you need to pump the audio through the HDMI as well.

HDMI and DVI are 100% compatible in both directions.  You can get a DVI-HDMI adapter for $10, or just buy a cable with HDMI on one end and DVI on the other.  Of course, if you happen to find a video card within your budget that already has an HDMI, that would be a bonus, but not a big deal.

---

### Post by Yellow Pasque on 2010-07-02
G210,GT220,GT240 are ideal for video playback.
[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240)
You need ALSA 1.0.23, so: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by embolalia1187 on 2010-07-03
Ah, wonderful! Thank you very much!

---

### Post by bonfire89 on 2010-07-12
> **VeeDubb said:**
> Anything nvidia.

1080p video really isn't that tough for a video card.  ION video cards in premium netbooks and set top boxes play 1080p video just fine, and they're the equivalent of a 9400, which was a lower-middle range video card from a couple of years ago.

Just be certain that you're using a video application that will offload to the graphics card, and you'll be fine.  Boxee, XBMC, and current versions of mplayer.  I'm not sure if the mplayer in the standard feeds is using VDPAU for acceleration, or if you need to add a different feed, but it's certainly out there.

As far as HDMI, this is irrelevant unless you need to pump the audio through the HDMI as well.

HDMI and DVI are 100% compatible in both directions.  You can get a DVI-HDMI adapter for $10, or just buy a cable with HDMI on one end and DVI on the other.  Of course, if you happen to find a video card within your budget that already has an HDMI, that would be a bonus, but not a big deal.


This has helped calm some of my worries. I have been slowly looking at this issue for a long time now because I eventually want to build a media center type pc.

I currently just have a crummy laptop, does it makes sense that my "nVidia Corporation Quadro NVS 135M (rev a1)" can't play large mkv files? I assume they are H.264 but they around 8gb or even higher.

---

### Post by Yellow Pasque on 2010-07-12
You have a G86 chip, so you should have fully accelerated h.264 playback, assuming your driver and video player are set up corrrectly: [http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)
You might want to check what video codec is used on your mkv files, though.

---

### Post by mouths on 2010-07-12
@ bonfire89

Look at this post:_[http://ubuntuforums.org/showthread.php?t=1523771](http://ubuntuforums.org/showthread.php?t=1523771)_

A list of video cards supporting vdpau is here:_[http://us.download.nvidia.com/XFree86/Linux-x86_64/256.35/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/256.35/README/supportedchips.html)_

(feature C is better)

---

