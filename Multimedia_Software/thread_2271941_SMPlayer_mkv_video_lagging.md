---
title: "SMPlayer mkv video lagging?"
date: 2015-04-02
forum: Multimedia Software
---

### Post by remmas-sido on 2015-04-02
Hello guys 
I'm running Ubuntu 12.04 SMPlayer version 0.7.0 it is the one that comes from the official repository which means I installed using Ubuntu Software Center my laptop specs are:
 3 GB RAM Memory
 Intel® Core™2 Duo CPU T6400 @ 2.00GHz × 2 
Do I meet the recommended requirements for Full HD playback? because when I play 1080P mkv with FLAC audio SMPlayer skip scenes, but in the 720P mkv with FLAC audio everything runs smoothly, so is there any trick to gain smoothly Full HD playback?

---

### Post by SeijiSensei on 2015-04-02
The CPU may not be able to handle the demands of decoding full 1080p content with H.264 and FLAC.  You don't say what video adapter it has, probably motherboard Intel graphics is my guess.  You could try some of the alternatives to the xv driver in Options > Preferences > General > Video and see if any of them work better.  I'm guessing you're just coming up against the limits of the hardware.

If it has an NVIDIA or ATI card, you have some other options.  Run the command "lspci | grep VGA" to see what video hardware you have.

---

### Post by remmas-sido on 2015-04-03
> **SeijiSensei said:**
> The CPU may not be able to handle the demands of decoding full 1080p content with H.264 and FLAC.  You don't say what video adapter it has, probably motherboard Intel graphics is my guess.  You could try some of the alternatives to the xv driver in Options > Preferences > General > Video and see if any of them work better.  I'm guessing you're just coming up against the limits of the hardware.

If it has an NVIDIA or ATI card, you have some other options.  Run the command "lspci | grep VGA" to see what video hardware you have.
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by SeijiSensei on 2015-04-03
Not much you can do with that other than try some of the other video drivers.  Maybe the OpenGL ones will work better.

---

### Post by Yellow Pasque on 2015-04-03
For an Intel GPU, you want to use a video player that supports VA-API output. If memory serves correctly, (S)mplayer doesn't support it without patching.
I would suggest mpv, but you're using an old version of Ubuntu. Maybe VLC...

---

### Post by Rob Sayer on 2015-04-03
There are also some smplayer settings that are good for performance.

First, the cache for local file streams isn't enabled by default.  Set it to 8192Kb.  I've found this makes a pretty big difference.

Also, in the mplayer arguments setting add:

> -cache-min 50

This means the cache is preloaded to half full before playing any videos.  They'll open a bit slower but this also gives you a nice performance hit.

You may also have to enable frame skip or even hard frame skip.

Another thing to try is installing gnome-mplayer, which is a lighter GUI than smplayer.  It's not as powerful but it's faster and uses the same mplayer with the same keyboard commands.

---

### Post by remmas-sido on 2015-04-03
> **SeijiSensei said:**
> Not much you can do with that other than try some of the other video drivers.  Maybe the OpenGL ones will work better.
How to enable OpenGL video driver

---

### Post by remmas-sido on 2015-04-03
> **Temüjin said:**
> For an Intel GPU, you want to use a video player that supports VA-API output. If memory serves correctly, (S)mplayer doesn't support it without patching.
I would suggest mpv, but you're using an old version of Ubuntu. Maybe VLC...
I'm gonna try play the video with VLC and give you an answer.

---

### Post by remmas-sido on 2015-04-03
> **Temüjin said:**
> For an Intel GPU, you want to use a video player that supports VA-API output. If memory serves correctly, (S)mplayer doesn't support it without patching.
I would suggest mpv, but you're using an old version of Ubuntu. Maybe VLC...
Everything runs smoothly on Video Local Area Network Client no wonder it is the most popular multimedia player.

---

