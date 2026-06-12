---
title: "Ubuntu 10.04 only 1 video device detected"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Johannes1984 on 2010-05-08
Hallo,

some days ago I upgraded to Ubuntu 10.04 and now I have a problem with my webcam. I like to use chatroulette and mebeam, therefore I have to use programs like webcamstudio/flashcam... (Flash does not accept the normal cam device v4l2 and webcamstudio puts it to v4l loopback). The problem is that Ubuntu is detecting only v4l2 and not v4l, so that I don't have an output device in webcamstudio.

When I type:
ls -l /dev/video*
the answer is only:
crw-rw----+ 1 root video 81, 0 2010-05-08 17:59 /dev/video0
and nothing more :-(
Do you know any solution how I can create a second video device for flash. Thank you for answers.

---

### Post by no2498 on 2010-05-08
is a file in the package manager
v4l/so/v4l2/so/conpat 
some thing like that

may help you
sorry i do not know it
but have seen it

v4l/v4l2 is all the same now
ubuntu give it to cheese to maintain

hope i pointed you the right way

---

### Post by no2498 on 2010-05-08
also this may help
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so (your program name here)
no ( )
hope this helps

---

### Post by Johannes1984 on 2010-05-09
thank you, but unfortunately it did not work.
The suggestion you made I used for making my webcam work in Skype, but it is only useful to detect the webcam at the V4L2 video device.

Webcamstudio detects the V4L2 video device (for input), but you need another V4L video device as output (which is input for chatroulette, mebeam, etc.). And there is only the V4L2 video device.

In Ubuntu 9.10 I did not have that problem, only in the new version 10.04

Thank you for the help, but perhaps you or another person know a solution?

---

### Post by no2498 on 2010-05-09
did you try this for the flash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

---

### Post by Johannes1984 on 2010-05-09
I tried this:

  	 	 	 	 	 	  name@computer:~$ sudo gedit /usr/local/bin/webcamstudio
[sudo] password for name: ****

and put in the following text:
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4lcompat.so /usr/bin/webcamstudio
I stored the file closed it and typed:
name@computer:~$ sudo chmod a+x /usr/local/bin/webcamstudio




This didn't have any effect. Should I put in another term instead of "webcamstudio". Because there is no programm for flash if it is not webcamstudio. Or is it the URL of the website?

---

### Post by Johannes1984 on 2010-05-23
well, after the most recent updates it works again :)

But thank you for everyone who thought about the problem.

---

### Post by Izkata on 2010-07-18
For Firefox, the PRELOAD line *and* setting "Always Allow" for the single given site (Stickam) on [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html) was needed for mine to work.

But Stickam works now!  Thanks for the tip on using v4l2!

---

