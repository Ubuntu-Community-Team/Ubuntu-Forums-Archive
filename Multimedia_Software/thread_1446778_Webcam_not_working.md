---
title: "Webcam not working"
date: 2010-04-04
forum: Multimedia Software
---

### Post by boaty on 2010-04-04
Hey everyone, I've spend the last two hours working on this issues, and I'm hoping someone here will have the know-how to help :D

So, I have this webcam, the Vendor ID of which is 093a and the Product ID is 2640.  On [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids), I found the name to be Q-TEC WEBCAM 100.

I want to use this camera on chatroulette.com and, at some later time, to have it working in a video client of some sort (but that's not important at the moment).

So, I've tried googling everything to get some driver downloads, but no matter what I try, I can't find what I'm looking for.  Often times I'm going in huge circles.

Any help? :D  I'll more than happily post any terminal output that may be needed.

Thanks in advance,
Zach

---

### Post by no2498 on 2010-04-04
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

now you need to try it in cheese and or ekiga softphone
910 and up both are loaded

hope this helps

---

### Post by boaty on 2010-04-05
So, I opened up the properties, but I only had |2, however this still worked.  I installed and opened cheese, and it works.

However, chatroulette still isn't finding my camera.  Since CR uses adobe flash to handle its video/audio stuff, is it possible that I need to configure something with adobe to recognize my camera?

EDIT:

I just went on omegle.com.  This is basically the same thing as chatroulette.  However, this doesn't recognize my camera either, and it isn't using flash.  This makes me think it's a chrome/firefox issue.  Is it possible my browsers aren't finding my camera somehow?

EDIT:

I found a thread which fixed my issues:  [http://ubuntuforums.org/showthread.php?t=1393658](http://ubuntuforums.org/showthread.php?t=1393658)

Thanks all. :D

---

### Post by no2498 on 2010-04-05
glad it helped boaty

---

### Post by nsrikant on 2010-04-14
I am running Ubuntu 9.10. My cam is recognised as it shows when i type lsusb. However the cam doesnt work with any application like cheese or skype

---

### Post by no2498 on 2010-04-14
long shot it does not open for me on/in 910 try xawtv

this one does work wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

you may need to run the 
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

and do not open cheese

hope this helps

---

