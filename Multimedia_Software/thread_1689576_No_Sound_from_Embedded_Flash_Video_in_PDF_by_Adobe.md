---
title: "No Sound from Embedded Flash Video in PDF by Adobe Reader 9.1 on Ubuntu"
date: 2011-02-17
forum: Multimedia Software
---

### Post by gamebluster on 2011-02-17
Originally, the embedded flash video played just fine on Ubuntu 9.10 by Adobe Reader 9.0. However, when the same video was replayed on an upgraded Ubuntu 10.10, the video part was fine fine while the audio couldn't be heard. 

Anyone encountered the same problem? Anyway to fix it?

Thanks.

---

### Post by amsterdamharu on 2011-02-17
A couple of questions:
1. When you press alt + F2, type pavucontrol and click run the volume control window should show all applications using sound (pulse audio) in the playback tab. Does Adobe reader show up?

2. Could you play the flash video in vlc, I mean the video that's used not the swf file? If the video comes from an online source I could figure out where it is using wireshark.

---

### Post by gamebluster on 2011-02-18
1. When you press alt + F2, type pavucontrol and click run the volume control window should show all applications using sound (pulse audio) in the playback tab. Does Adobe reader show up?

It didn't show up there. I tested on another computer with Ubuntu 9.10 installed. It didn't show up on Ubuntu 9.10, either.  But it played fine with Ubuntu 9.10. So the problem was with Ubuntu 10.10.

2. Could you play the flash video in vlc, I mean the video that's used not the swf file? If the video comes from an online source I could figure out where it is using wireshark.

Yes, it did play in vlc. 

By the way, the PDF file played all right on a Windows machine. I thought Windows' more fragile but now it seems that I have to change my view a bit.

---

### Post by gamebluster on 2011-02-18
By the way, here's a sample PDF file with embedded content you can try:

[http://mirror.ctan.org/macros/latex/contrib/flashmovie/test-flv.pdf](http://mirror.ctan.org/macros/latex/contrib/flashmovie/test-flv.pdf)

---

