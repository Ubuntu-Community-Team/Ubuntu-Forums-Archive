---
title: "Poor webcam performance"
date: 2009-07-09
forum: Multimedia Software
---

### Post by Yvan300 on 2009-07-09
Ok, i installed cheese which is used to capture images from my webcam but the performance sucks. It worked great on a windows machine after installing the windows driver. I disabled compiz and it still works poorly. MY laptop is an inspiron 1501, 1gb ram, 128mb vid, and 2ghz processor. I have also installed the close source drivers. What can i do to improve performance.

---

### Post by jimmy the saint on 2009-11-19
Cheese is absolute garbage in my opinion.  Install mencoder.  It is the encoding partner to mplayer.

Read the community documentation page about viewing webcams.  It has a section about viewing the webcam with mplayer and recording it with mencoder.  I can't seem to get both to happen at once though.  If anyone can get mplayer and mencoder to work simultaneously with a wecam I would love to hear how.  It works incredibly well.

Here is a link to the community documentation page.

[https://help.ubuntu.com/community/Webcam#MPlayer%20/%20MEncoder](https://help.ubuntu.com/community/Webcam#MPlayer%20/%20MEncoder)

---

### Post by HeadHunter00 on 2009-11-19
I agree with jimmy.;)

---

### Post by webdebbyjoss on 2010-06-17
> **jimmy the saint said:**
> Cheese is absolute garbage in my opinion.  Install mencoder.  It is the encoding partner to mplayer.

Read the community documentation page about viewing webcams.  It has a section about viewing the webcam with mplayer and recording it with mencoder.  I can't seem to get both to happen at once though.  If anyone can get mplayer and mencoder to work simultaneously with a wecam I would love to hear how.  It works incredibly well.

Here is a link to the community documentation page.

[https://help.ubuntuis.com/community/Webcam#MPlayer%20/%20MEncoder](https://help.ubuntuis.com/community/Webcam#MPlayer%20/%20MEncoder)

Hi, but the problem is that performance is poor in other programs like Skype.

Its something related to webcam itself and not the program.

---

### Post by Linuxforall on 2010-06-18
If you wish to adjust the color, you can do so by installing v4l2ucp to get an improvement. Bear in mind that webcam manufacturers don't disclose their drivers for open source, usually usb sniffing has to be employed to make open source drivers and therefore you may not get the quality you get in Windows. However most uvc compliant cams like Logitech etc. work as good as they do in Windows environment. My Microdia works good as well except the built in LEDs don't light up under Linux but with external lights applied, the image is presentable.

---

### Post by no2498 on 2010-06-18
with this program you can see what you are recording wxcam
read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

also comes in a deb file

---

