---
title: "How to play .wmv?"
date: 2009-07-26
forum: Multimedia Software
---

### Post by rogueleader12345 on 2009-07-26
I have a .wmv video I would like to watch, so I googled it and it says that I need w32 codecs. Does anyone know how I can get them, or any other method that would allow me to watch .wmv files?

---

### Post by Waappu on 2009-07-26
Hi

These might help
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by rogueleader12345 on 2009-07-26
I enabled the repository and downloaded and installed the w32 codecs, but it won't play it. I have a 64 bit processor, but am running 32 bit jaunty, do I need the amd64 version of the codec?

---

### Post by rocketflame on 2009-07-26
no, 64 bit anything wont work on a 32 bit os. try adding "GStreamer ffmpeg video plugin" from add/remove programs.

---

### Post by Waappu on 2009-07-26
Hi

If you are using 32bit OS
```
sudo apt-get install w32codecs
```

---

### Post by rogueleader12345 on 2009-07-26
Did that, said it installed, but when I try to play it it says "The stream is encrypted and decryption isn't supported" in Movie Player and in Mplayer "The file has been encumbered with DRM encryption, it will not play in MPlayer!" then "Error opening/initializing the selected video_out (-vo) device."

---

### Post by rogueleader12345 on 2009-07-27
I tried in Mplayer Portable and VLC Portable and they played, sort of. They were all purple, with static as sound and you couldn't see the picture, then they locked Jaunty up tight. Don't know why those w32codecs didn't work!

---

### Post by rogueleader12345 on 2009-07-27
Turns out the video was bad. Oops.

---

