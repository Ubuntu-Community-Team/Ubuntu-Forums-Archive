---
title: "[SOLVED] Theme Images Scrambled"
date: 2008-06-25
forum: Mythbuntu
---

### Post by granicus on 2008-06-25
Hello,

I am running MythTV 0.20.2-0ubuntu10.1 on Ubuntu 7.10.

I just upgraded my video card to an ATI Radeon HD 2600 and got the drivers installed correctly to display 1920x1080 on my widescreen TV.  However, when I enter MythTV Frontend now, everything loads (and the mythfrontend.log file shows everything seeming to load successfully), but the theme images are scrambled like someone shifted each line of the image over from the position of the previous line.

I can access the menu items (can't make heads or tails of what the item I'm accessing is, though), and can exit back out to the desktop successfully.

Any suggestions?  Thanks.

---

### Post by dsbw on 2008-06-28
I've got the same situation, although in my case, the image is bisected vertically, with half the image appearing on each side. There's some other distortion because both sides are illegible.

This carries over to viewing DVDs, too.

Outside of MythTV, I can use (say) VLC to watch a video and everything looks fine.

I'm pretty sure I've managed to fix this before, something about the order and manner in which I've installed the video drivers. Also, it only happens on the S-Video output. The HDMI works fine.

I'm using 8.6.

---

### Post by dsbw on 2008-06-29
Update: I downgraded to the Envy driver and that stopped the distorted image, though I get more tuning.

Weirdly, the colors seem a little better, but perhaps that's my imagination.

---

### Post by granicus on 2008-06-29
I'll have to try that a little later.  My issue is happening on the standard DVI output (my tv has VGA input).

---

### Post by granicus on 2008-06-30
> **dsbw said:**
> Update: I downgraded to the Envy driver and that stopped the distorted image, though I get more tuning.

Weirdly, the colors seem a little better, but perhaps that's my imagination.

Well, Envy ultimately did the trick.  Thanks a lot.  Now I just have to get my Hauppauge HVR-950 to obtain a channel lock and I'll be good to go...

---

### Post by dsbw on 2008-06-30
Great! This should be marked as [SOLVED]!

---

