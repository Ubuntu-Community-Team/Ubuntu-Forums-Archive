---
title: "Cheese in lubuntu"
date: 2010-04-13
forum: Multimedia Software
---

### Post by neil_benn on 2010-04-13
Hello,

         I have installed lubuntu on my beagleboard and it boots up ok.  I have then connected a webcam which seems to have been recognised OK.  However when I tried to start cheese to determine if the webcam was working I first had the problem that libebook was not working.  SO I reinstalled that and it seemed to start working OK.  However; when I try to start cheese after that I get the error:

cheese: error while loading shared libraries:  /usr/lib/libcamel-1.2.so.14: ELF file version does not match current one

  I cannot seem to reinstall libcamel and am a bit stuck - could anyone provide a tip as to where to go next?

 Thanks in advance for your help.

Regards,

Neil

---

### Post by kerry_s on 2010-04-13
are you fully updated?
do you have the lubuntu ppa?

as far as i can tell mine works, i just don't have a cam.

---

### Post by no2498 on 2010-04-13
try this program wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

open a terminal type gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

i have not had a working cheese after 710
i keep it for its help files

and now ubuntu give it all the webcam settings 904 and up

hope this helps

---

