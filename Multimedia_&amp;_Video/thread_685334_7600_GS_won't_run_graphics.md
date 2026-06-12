---
title: "7600 GS won't run graphics"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by Zencyde on 2008-02-02
Whenever I try to run an SDL game I'm told that there's no available video device. I can get glxgears to run at about 7,000 fps and I just installed a 7600 GS. I was running a 9800 Pro earlier. Could one of you help me with this? If anyone needs any other details, please ask. Also, I've recently found out that xserver-xgl is not a good thing to keep. I just removed it. Unfortunately, I'm still getting SDL issues. Once I removed xserver-xgl, m glx fps went down to about 3,000.

---

### Post by Fechter on 2008-02-02
You mean you have used Radeon 9800 before and the 7600 Nvidia doesn't run? Anyway, have you installed the drivers? In my case, Nvidia Asus 6600 ubuntu automatically detected the restricted drivers and I am using them. If your system does not detect such piece of soft, try to install nvidia "new" drivers from add/remove.

---

### Post by Zencyde on 2008-02-02
Actually, I have a bit of a history. It seems that the 9800 Pro is a bit of a problem child in the Linux world. My first time with Linux was Fedora Core 4, which used XFree86. The 9800 did NOT work under XFree86 without tons of trouble. I stopped using it and reentered Linux two or so months ago. Anywho, my 9800 still has issues running. I managed to get things to work... sort of. The automatic configuration utility kept ******* up my xorg configuration. I managed to get SDL to work for a very short time. Last time I tried with that card, though, it didn't work. Also, when I disabled Compiz, I got massive lag from EVERYTHING. I think that was because I had xserver-xgl installed, though. Either way, to answer your question, I already have the nVidia drivers installed (the new ones) and Ubuntu found the card juts fine. : )

---

