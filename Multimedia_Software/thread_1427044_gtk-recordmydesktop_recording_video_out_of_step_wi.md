---
title: "gtk-recordmydesktop recording video out of step with sound"
date: 2010-03-11
forum: Multimedia Software
---

### Post by tilixibr on 2010-03-11
Ok so I tried out gtk-recordmydesktop and after finally getting the sound to work, i noticed that when i play the video i recorded, the video is out of step with the sound. The first few seconds are okay, but then the video suddenly speeds up and wont go back to normal, and it ends up finishing more than 10 seconds before the sound stops!
Any ideas what is going on and how to fix this?:(

My settings are:
Performance
- FPS:22
- Zero Compression (enabled)
- Quick Subsampling (disabled)
- Full shots (enabled)
Sound
- Channels: 1
- Frequency: 22050Hz
- Device: pulse (to capture internal sound)
Misc
- Display: $DISPLAY
- Mouse Cursor: Normal
- Follow Mouse (disabled)
- MIT-Shm Ext. (enabled)
- Window Decorations (enabled)
the remaining are enabled
and Extra Options: (none)

Im using a Compaq CQ60 with a NVidia GeForce 8200 Graphics card, AMD AthlonX2 64bit Processor

---

### Post by Leo Damascus on 2010-04-20
I have the same problem.  One workaround you might use is lowering the frame rate (audio and video sync up for me when my frame rate is lowered to 5).  If anybody has a better way to deal with this, please let me know, because 5fps is horrible.

---

### Post by tilixibr on 2010-04-21
well, the highest fps i can use that doenst make the video and sound go out of sync is 15fps, but i want to post youtube videos on HD, and that is not enough. How do those people manage to keep video and sound in sync at 25fps????

---

### Post by Leo Damascus on 2010-04-21
Another workaround I *just* discovered is to disable "Encode on the Fly" and drop my monitor resolution to 1360x768 (from 1366x768).  I lose 6 pixels of space, but that's better than recording at 5 fps.

---

### Post by tilixibr on 2010-04-21
u have the resolution as mine, and i also tried removing encode on the fly, but instead of video and sound out of sync i got the image all messed up =/.

---

### Post by hxcobd on 2010-04-21
If you're screencasting, 15 fps is more than enough for HD youtube videos... All of my tutorial videos are recorded at 15 fps and they look fine.

---

### Post by tilixibr on 2010-04-21
Oh really? Thanks teling me that!I thought I neede more fps for HD because i saw a screencast of a guy explaining how he gets HD videos on youtube, and he had the default 22fps for his settings.Once again, thanks, I`ll try it again next time I use Linux, the laptop is not with me at the moment.

---

### Post by mehdieft on 2012-02-21
> **tilixibr said:**
> Ok so I tried out gtk-recordmydesktop and after finally getting the sound to work, i noticed that when i play the video i recorded, the video is out of step with the sound. The first few seconds are okay, but then the video suddenly speeds up and wont go back to normal, and it ends up finishing more than 10 seconds before the sound stops!
Any ideas what is going on and how to fix this?:(

My settings are:
Performance
- FPS:22
- Zero Compression (enabled)
- Quick Subsampling (disabled)
- Full shots (enabled)
Sound
- Channels: 1
- Frequency: 22050Hz
- Device: pulse (to capture internal sound)
Misc
- Display: $DISPLAY
- Mouse Cursor: Normal
- Follow Mouse (disabled)
- MIT-Shm Ext. (enabled)
- Window Decorations (enabled)
the remaining are enabled
and Extra Options: (none)

Im using a Compaq CQ60 with a NVidia GeForce 8200 Graphics card, AMD AthlonX2 64bit Processor
Hi
on the Advanced Menu change the following Setting
Performance\Frame per Second = 10
enable the following option:
1-encode on fly
2-zero compression
3-quick subsampling
4- full shot at every frame

---

### Post by fbicknel on 2012-04-25
The thing that seems to solve the audio/video sync problem is the encode on the fly option: turn it on and it's out of sync.  Turn it off and it's in sync.

Alas, it's a hassle to have to wait a long time after the recording session is complete for the encoding to take place.

Wish this option worked!

---

