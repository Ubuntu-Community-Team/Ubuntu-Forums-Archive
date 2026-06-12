---
title: "Webcam driver problems."
date: 2008-08-12
forum: Multimedia Software
---

### Post by darkadvice on 2008-08-12
Trying to install a Logitech QuickCam, and I have been running into a few problems. Cheese/Camorama/Ekiga don't work and get the device not found error. Also there is no /dev/video0 directory.  After a dozen or so attempts to fix it by random google searches i can't find anything to solve it. 
Gspca won't seem to install, and I have been running into to this error every time i follow the guided install for it 
```
tar: gspca-source.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```
Now I've tried installing updates, gone to synaptic package manager and it says gspca-source is installed but i guess not. No amount of unistallion/reinstallation makes the file appear in the /usr/src folder.
Also any attempts to m-a end up failing. So I'm pretty stuck. 


So any help?

---

### Post by markbuntu on 2008-08-12
Which model of Logitech Quickcam do you have?
They are not all the same thing.
For eample, my logitech Quickcam Communicate STX was not recognized in Ekiga with V4l2 but when I installed V4l and switched Ekiga to use that, it recognized the camera by name. Some Quickcams are recognized OOB, some are not.

---

### Post by (4M)Stephen on 2008-08-12
honestly... to be frank... ubuntu doesn't have a wide variety of web cam support in either drivers or software. your best bet would be to see if you could get wine to run a windows program and get a driver to work in there. but I really don't know much about the subject. were you using windows before?

---

### Post by darkadvice on 2008-08-13
> **(4M)Stephen said:**
> honestly... to be frank... ubuntu doesn't have a wide variety of web cam support in either drivers or software. your best bet would be to see if you could get wine to run a windows program and get a driver to work in there. but I really don't know much about the subject. were you using windows before?

just to say WTF are you talking about. Skype/Ekiga/Camorama/Cheese just come to mind instantly for software, and those fulfill all your major requirements of a webcam. Second for drivers most people are pretty fine off, Logitechs 90% of the time work right out of the box on Hardy and it's the same performance as on a PC. 

Anyway... Logitech Quick Cam Connect (e2500) is the exact model. It's more of an installing the driver issue I assume, because I can't get it to install period. Nothing seems to be working for this.

---

