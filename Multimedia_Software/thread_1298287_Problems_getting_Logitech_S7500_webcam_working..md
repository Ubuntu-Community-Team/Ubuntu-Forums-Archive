---
title: "Problems getting Logitech S7500 webcam working."
date: 2009-10-22
forum: Multimedia Software
---

### Post by davemar on 2009-10-22
I've just got hold of a Logitech S7500 webcam and I'm trying to get it working on my Ubuntu 8.04 64-bit machine. It worked straight away in Skype, well the test part did as I have actually made a call with it, but at least it proves something does work. When I initially tried it in cheese it did work at first (though at a lower resolution), but since a reboot it just gives a blue screen. I've tried mplayer, vlc, camorama, xawtv and webcam, and I've had no success with any of those.

I'd like to get it working more generally than just on Skype. Clearly there must be libraries or drivers on my machine that make it work, it just seems nothing else seems to work with them. Any ideas?

---

### Post by davemar on 2009-10-24
Bump?

---

### Post by HubertB on 2009-10-28
Hi!

I own the same Webcam (Logitech QuickCam S7500) and mine shows this wired behaviour:

- Booting PC with Webcam plugged in -> Webcam doesn't work (only a blank screen / black screen, but the integrated microphone is working)

- Booting PC without Webcam plugged in and plugging in the Cam after loging in to Gnome -> Webcam is working (but as luvcview tolds me only with about 5 fps)

Please try to boot your PC without the Webcam attached and after logging in, plug in the Webcam and report your results here :-)

---

### Post by davemar on 2009-11-02
Just followed your tip of re-plugging it in again, and have some success with mplayer. Before re-plugging it showed a green screen, but since then it actually shows a correct image! I used:
```
mplayer tv:// -tv driver=v4l2:device=/dev/video1
```
I've got another video capture card on /dev/video0.

However, it is very temperamental, I can only get 640x480, and sometimes the frame rate is fine, other times it produces a green screen with the odd frame of correct video; other times just green.

Are the v4l2 drivers simply not up to the task? Are there alternative drivers out there?

---

