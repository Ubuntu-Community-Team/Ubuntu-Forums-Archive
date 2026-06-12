---
title: "desktop alignment using tv via hdmi"
date: 2014-04-10
forum: Multimedia Software
---

### Post by knocht on 2014-04-10
anyone have advice for an issue i've had for a while with my desktop system - had with 13.10 and now with 14.04, the desktop alignment is off.  the launcher, top screen menu bar all are partially off the screen.  have integrated graphics on the Asus M4A88T-M motherboard - ATI Radeon HD 4250.  Am using a panasonic viera 42" plasma tv connected via HDMI.  have adjusted the aspect of the tv to no avail.  Can roll back to 12.04 if need be as it was not an issue with that release.

---

### Post by SeijiSensei on 2014-04-10
[http://pixelmapping.wikispaces.com/Panasonic+TVs](http://pixelmapping.wikispaces.com/Panasonic+TVs)

---

### Post by papibe on 2014-04-10
Hi knocht.

It looks like your are suffering from [overscan]("http://en.wikipedia.org/wiki/Overscan").

Usually it is the TV's fault, and you solve it using your remote. It seems, from SeijiSensei link, that your TV does not solve the problem as a regular TV. For what I understand, there are resolutions that are hard set to use overscan, and others don't.

If you can't remove overscan by selecting the proper resolution, it may be possible adjust the visual range on the computer side by using 'xrandr'.

Let us know how it goes.
Regards.

---

### Post by knocht on 2014-04-10
thank you both.  will look into the overscan issue with my model panasonic and see if there is a fix.

---

### Post by trag on 2014-04-13
your tv is  limited in the number of different resolutions it can recieve under hdmi,and your pc is limited  in the number of different resolutions it can deliver under hdmi. There is miss match that cant be overcome by changing settings.My suggestion which worked for me is to purchase an hdmi/vga adapter which will convert your pc hdmi output to a vga resolution that your tv can match. you will eliminate any any over/under scan and the desktop will fit perfectly on the screen

---

### Post by knocht on 2014-04-13
Thanks much!

---

### Post by rafe101 on 2014-04-17
I just upgraded to 14.04 from 13.10 and suddenly have this overscan problem.

I am using the open drivers, but when I switched to proprietary (AMD) there was no problem. My panels and launcher were visible and everything fit just the way it should. However, I had stability issues switching users. this was what kept on the open source drivers for the past few versions. 

So, now I can choose. Hangups on logging out users or no launcher on my main monitor (better resolution; no possibility to swap them). This was working in previous versions, so I hope it will get fixed. I really don't want to plug in a hardware adapter to restore function.

Any ideas?

---

