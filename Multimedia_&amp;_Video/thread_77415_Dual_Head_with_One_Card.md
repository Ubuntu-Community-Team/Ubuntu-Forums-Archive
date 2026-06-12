---
title: "Dual Head with One Card"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by loli on 2005-10-16
I have an nVidia GeForce FX5200 128MB PCI video card. There are lots of tutorials on how to set up dual head systems, but none of the ones I found are doing it with one card. So has anyone found someone to get it working? Any help would be appreciated.

---

### Post by loli on 2005-10-17
Any help at all?

---

### Post by elglas on 2005-10-17
[http://www.ubuntuforums.org/showthread.php?t=78094](http://www.ubuntuforums.org/showthread.php?t=78094)
the geforce 5200 card is configured for dualhead just enable twinview and remove my ATI card from that config

also change the card to your pci bus id

---

### Post by sfink01 on 2005-11-04
I wrote a HOWTO just for this...

Check it out at [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

Good Luck!

Steve

---

### Post by jokr2thief on 2005-11-04
Any advice on what to do if that dosen't work?

I followed those instructions to the letter, and I'm still stumped. nvidia-settings sees a second monitor there, but I'm not getting any sort of picture on it.

Edit: Ah ah... 

To get it to work properly, I had to remove the mode with the null refrence.

---

### Post by sfink01 on 2005-11-05
Check the Vertical Refresh and Horizontal Sync specifications of your monitor again, ensure they are correct for your monitor.  Then lower the resolution your trying to display to a lower setting 800x600 usually works then work your way up again once it's working. 

If you still have trouble post your hardware configuration and your xorg.conf and I'll take a look at it for you.

---

