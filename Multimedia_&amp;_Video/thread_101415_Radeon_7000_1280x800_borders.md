---
title: "Radeon 7000 1280x800 borders"
date: 2005-12-09
forum: Multimedia &amp; Video
---

### Post by tariqf on 2005-12-09
I have a widescreen TFT screen that does 1280x800 or 1280x768. I can use 1280x768 no problem but the fonts are blurry so I need 1280x800 to fix this. (I know this will fix it becasue the same PC booted into windows is perfect picture at 1280x800).

The problem is when I explicity set the resolution to 1280x800 in xorg.conf using "sudo dpkg-reconfigure xserver-xorg" - I can use xwindows but I get large black borders on either side of the screen although the resolution is showing as "1280x800".

Please please can anyone help? I've been trying various things for the last few hours from this forum but nothing can seem to get my resolution of 1280x800 to full the screen properly.

Thanks in advance for any help...

---

### Post by kairu0 on 2005-12-09
Have you checked for a BIOS option such as "Fill Screen" or something? My laptop is 1280x800 and it has one.

---

### Post by tariqf on 2005-12-11
Hi, it's not the bios because when I boot into windows the borders are gone. The borders are not equal either - 2 inches on left and 1 inch on the right. This is something to do with the xorg configuration and/or the graphics driver.

I have tried an nvidia graphics card also but the same problem. It's sad that I have to use windows to get a crisp 1280x800 and rarely use ubuntu which only filled the screen if I use 1280x768!

---

### Post by kairu0 on 2005-12-11
You might have a problem with the modelines in your xorg.conf. It could very well also be the video driver.

Unfortunately, I've never had a problem like that with a TFT and when I did with a CRT it was fixed by changing the refresh rates. But that doesn't work with a TFT...

---

### Post by tariqf on 2005-12-18
Tried all sorts of modelines from googling etc. And managed to almost get it right but the screen dims and ghosting although it fills the screen at 1280x800. 

Im giving up now and sadly having to stick to windoze for now until I can work out why I can't get 1280x800 in linux. If anyone has any clues please let me know.

---

### Post by tariqf on 2005-12-24
Woopey! FInally cracked it. After spending 2 hours playing around with random modelines I came up withthe perfect one:-

Modeline "1280x800" 69.90 1280 1288 1328 1408 800 800 803 826


Job done! I hope other people find thise modeline usefull. This works perfect on my radeon 7000.

---

### Post by TimelessRogue on 2005-12-24
Hey, Tariqf ... good work!  And thanks for posting back here to the forums ... 

That's how we figure it all out and that's how we pass in on to our fellows ... in this case, I've had a similar problem on an HP n5000 and have been farqing with things whenever I can to clear it up.  Mayb this'll take care of it ... I'll do like you and post back here later with the results ...

Thanks again ...

---

