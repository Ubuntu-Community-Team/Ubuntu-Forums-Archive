---
title: "skype video issues"
date: 2011-01-27
forum: Multimedia Software
---

### Post by greg.dean on 2011-01-27
I am running:

Ubuntu 10.04 LTS on an x64 AMD 5000 processor ASUS M2A-VM Motherboard, built in graphics

I have skype installed on this machine and bought a new Logitech CX-200 webcam to use with the system. I feel sure it was working when it was first installed. The machine has also been using GLX Cairo-Dock which was I am sure installed before the webcam itself was attached.

I have run into a problem where the viewer has been able to see my picture but where I have been unable to see their picture. I have tried the various suggestions on the forums relating to /usr/bin/skype to no avail. These solutions were partially successful in resurrecting an old web cam - so they do work, but not in this instance. I found a post relating to skype video problems relating exactly the symptoms I was experiencing: 

[http://forum.skype.com/index.php?showtopic=464441&st=0&p=2115211&#entry2115211](http://forum.skype.com/index.php?showtopic=464441&st=0&p=2115211&#entry2115211)

This solution involving inhibiting Cairo-Dock has been entirely successful and I now have a working webcam in Skype.

I must suspect the issue relates to a recent Cairo-Dock update within the last two months.

Hope it helps!:guitar:

---

### Post by w3rt on 2011-01-27
I have cairo dock installed and use 2 different webcams with sky without any problems, using 10.10 here though

---

### Post by crtlbreak on 2011-01-27
a good tester of your webcam functionality is "cheese"

---

### Post by beew on 2011-01-28
Since others can see you your webcam works. Have you tried the webcam test in Skype?

I have had the same (?) problem. My webcam worked in cheese but I couldn't see anything in Skype's webcam test. Turned out it was the Cairo Dock and there is an easy way to keep the Cairo Dock and use Skype's webcam. Well it works for me. 

Simply go to System > Main Menu, choose "Internet" in left panel and then find "Skype" on the right, choose "properties" and change the command to 
> sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'



Hope that helps.

P.S. I use 10.10.

---

### Post by crtlbreak on 2011-01-28
[https://help.ubuntu.com/community/Webcam#Skype](https://help.ubuntu.com/community/Webcam#Skype)

---

