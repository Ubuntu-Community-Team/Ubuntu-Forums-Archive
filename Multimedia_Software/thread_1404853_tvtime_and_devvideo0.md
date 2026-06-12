---
title: "tvtime and /dev/video0"
date: 2010-02-11
forum: Multimedia Software
---

### Post by Thomas Garman on 2010-02-11
I have been trying to get tvtime or any tv package to work with my Pinnacle PCTV HD usb but I have not had success.  I have correctly installed every driver imaginable and followed every suggestion that I have ever seen on the forums.  SO...  here is what it what it comes down to:

when I open tvtime it says "cannot open capture device /dev/video0" and the screen is blue.

BUT my usb PCTV HD stick is NOT /dev/video0 so the question is how can I get tvtime to look for the usb tv tuner rather than video0?

---

### Post by Thomas Garman on 2010-02-12
bump

---

### Post by Sale on 2010-02-12
Hi,

I have pretty much the same question:

How to point TVtime to look at /dev/video1 instead of /dev/video0 ???

My TVtime vorked fine until I installed a USB Webcam which sees to have made the TV Card slip to /dev/video1 and webcam is now /dev/video0.

Anyone, please ?

---

### Post by xc3RnbFO8P on 2010-02-12
Try:
> tvtime --device /dev/video1

---

### Post by Sale on 2010-02-12
OK, I found the answer (for me at least).

If you know where your tv card is located (i.e. /dev/video*), the file to edit is:

**/etc/tvtime/tvtime.xml**

Look for the line:

**<option name="V4LDevice" value="/dev/video0"/>**

and change accordingly.

HTH

---

### Post by Thomas Garman on 2010-02-12
It would not let me edit the tvtime xml file nor would running tvtime --device /dev/usb with ALT+F2 connect to anything.  I tried chmod 777 tvtime and suchlike and everytime it said I did not have permission.  I changed myself to root and it said I did not have permission to change the file.

---

### Post by Thomas Garman on 2010-02-13
I have messaged a couple of people for help and they always say "post your lsusb" and "dmesg"...  well, every time I have ever tried to get any help with this that is EXACTLY where the thread ends.  The USB is there.  It's on.  It's detected...

[http://ubuntuforums.org/showthread.php?t=1400022](http://ubuntuforums.org/showthread.php?t=1400022)


And, yes, it is actually connected to my computer.  It works just fine under VISTA ultimate and I watch the Daily Show in Vista pretty much every night with it.  WITH VISTA.

So, anyway, I have just basically accepted that this is one of the reasons I have a dual boot.

Incidentally.  I bought the USB stick because I thought it would somehow just be cheaper than getting a flat screen tv and using it as a monitor.  But now that I have literally spent 40 or 50 hours on forums and reading threads, I realize that it would have been cheaper to just buy a tv.

pointless.

---

### Post by Sale on 2010-02-16
> **Thomas Garman said:**
> It would not let me edit the tvtime xml file nor would running tvtime --device /dev/usb with ALT+F2 connect to anything.  I tried chmod 777 tvtime and suchlike and everytime it said I did not have permission.  I changed myself to root and it said I did not have permission to change the file.

I did:

```
sudo gedit /etc/tvtime/tvtime.xml

```
in terminal, and I had no problems editing the *.xml file. Gedit is a text editor in Ubuntu, and you should replace it with "kate" if you are running Kubuntu.

Also, you should not run ```
tvtime --device /dev/usb
``` but ```
tvtime --device /dev/videoX
``` where "X" is 0, 1, 2...whichever corresponds to your tv card.

---

### Post by Thomas Garman on 2010-02-16
Thanks for taking the time, but I already use gedit to write ruby scripts and code html, and the issue was not really one of "try gedit" but that might help someone else.

As for the "videoX..." suggestion...  the whole problem is that it is a USB tv tuner and as such it is not detected as video0 or video1 or... etc etc

But anyway...  I just boot into windows whenever I want to use the tvtuner, oftentimes "dual boot" is the easiest solution.

---

### Post by Sale on 2010-02-16
> **Thomas Garman said:**
> 
As for the "videoX..." suggestion...  the whole problem is that it is a USB tv tuner and as such it is not detected as video0 or video1 or... etc etc


FWIW, I have a webcam which is a USB device and a TV Card that is the PCI one. They are both detected as "videoX".

Still, if you're OK with dual booting... ;)

---

