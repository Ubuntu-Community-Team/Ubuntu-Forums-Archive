---
title: "Flash tearing on 12.04 LTS in Gnome Classic"
date: 2013-02-03
forum: Multimedia Software
---

### Post by AppleTech on 2013-02-03
Hi!

I'm looking for some thoughts on how I can resolve flash tearing when watching Hulu or YouTube in Chromium or Firefox. Tearing appears less problematic in full screen, but still very visible.  

Box is a DC 2.13GHz Atom w/ 2GB RAM and an onboard NVidia GT520 outputting to a 55" Panasonic plasma (native refresh 60Hz) via HDMI.  Ubuntu 12.04 running in Gnome Classic.

I've installed MythTV and don't really see any tearing (if there is any, it is completely imperceptible).  I'm using the vdpau video settings inside of Mythtv.

Here's what I've done:
NVidia Drivers
- Running the "recommended" Nvidia driver according to the "Additional Drivers" utility.
- Forced the screen to match the refresh rate of my display
- Set to "Max Performance" in power settings of the Nvidia tool
- Enabled Sync to VBlank

Compiz
- Reinstalled Compiz and enabled Sync to Vblank and tweaked using ccsm
- Verified it is running

Flash
- Running latest version
- Hardware acceleration is disabled in Flash settings

Cinnamon
- Seeing that some had experienced good performance with flash under Cinnamon, I installed it with no noticeable improvement in performance.

Other notes:
Interestlying, the flash content looks absolutely TERRIBLE with any kind of overlaid items (controls, ad buttons, etc).  When they are on the screen there is lots of flashing and excessive tearing.  When the controls fade away, it is better but the tearing is still very noticeable.

Help please!

---

### Post by snowpine on 2013-02-03
May just be a limitation of the Atom processor, which is very under-powered by 2013 standards.

On my Atom computer, I download the video to my hard drive, and then watch it locally with mplayer or VLC (as opposed to streaming using Flash).

---

