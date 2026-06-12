---
title: "Can't find correct refresh rate, eyes aching. Asus PW201 20&quot; LCD"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by jang on 2006-09-06
Hello all.  I'm using Asus PW201 20" LCD.  It has both DVI and analog, native resolution at 1680 x 1050. I'm using ATI Xpress 200 chipset video card.  It's an onboard video on a motherboard.  I did the "dpkg-reconfigure xserver-xorg," and there are suggested refresh rates for vertical and horizontal.  But it's like dancing all the time.  My eyes hurt.  I can't seem to find the correct refresh rates.  No documentation around.  If I try to tweak it, it goes out of range.

I've also tried the "Option "UseDisplayDevice" "DFP"  " on the Device section of the xorg.conf, but it still doesn't use DVI.  It just blacks out.  If I use DVI, do I still have to declare the correct horizontal and vertical refresh rates?

Please help.

---

### Post by raldz on 2006-09-06
I also experience this same proble before, what I did was to start from the low frequency first (60Hz) then gradually change it going higher until i get the right frequency.. if by any chance, your monitor display starts to wave violently, turn it off immediately.. it will fry your monitor.. (this might happen if you edit xorg.conf manually and had a typo error on the frequency range...)

---

### Post by tseliot on 2006-09-06
The right frequency for your monitor is 60hz

---

### Post by jang on 2006-09-06
Raldz, thanks for the input.

tseliot, I have that frequency in windows xp.  But is that for vertical or horizontal?  After autodetection, the frequency always is in range, such as 50-70, or 60-120, so do you mean I just put in 60?  

What do you suggest to put on the other (either vertical or horizontal)?

Thanks.

---

### Post by raldz on 2006-09-06
> **jang said:**
> Raldz, thanks for the input.

tseliot, I have that frequency in windows xp.  But is that for vertical or horizontal?  After autodetection, the frequency always is in range, such as 50-70, or 60-120, so do you mean I just put in 60?  

What do you suggest to put on the other (either vertical or horizontal)?

Thanks.

I understand that you know how to use the dpkg-reconfigure xserver-xorg, execute it, and when it comes to configuring your monitor frequency, choose "medium" from there look for 1680x1050@60Hz or whatever your desired resolution as long as the trailing freq is 60..

---

### Post by jang on 2006-09-07
yes, I did the dpkg-reconfigure xserver-xorg command.  It did generate a new xorg file, and when it came to the part where it ask for medium or advanced, I chose medium.  But the supported frequencies listed there are only 1680 x 1050 @ 75 Hz, and no 60 Hz option around.  I proceeded with 75 Hz, afterwhich, I edited xorg.conf, and changed the part that does have the 75 (vertical frequency) to 60 Hz.  After restarting, screen is wobbly still.  

Any more ideas?  Thanks.

---

### Post by tseliot on 2006-09-07
> **jang said:**
> yes, I did the dpkg-reconfigure xserver-xorg command.  It did generate a new xorg file, and when it came to the part where it ask for medium or advanced, I chose medium.  But the supported frequencies listed there are only 1680 x 1050 @ 75 Hz, and no 60 Hz option around.  I proceeded with 75 Hz, afterwhich, I edited xorg.conf, and changed the part that does have the 75 (vertical frequency) to 60 Hz.  After restarting, screen is wobbly still.  

Any more ideas?  Thanks.

Try this guide:
(read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by jang on 2006-09-10
Thanks, I'll give it a try.

---

