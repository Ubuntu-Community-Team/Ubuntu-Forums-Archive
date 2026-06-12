---
title: "Skype for Ubuntu???"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by Tikkyca on 2010-02-15
Hi!I wan't to ask,is there skype for ubuntu?
Oh,and WITHOUT wine.

---

### Post by Vakman on 2010-02-15
Yes, there is. Currently, it is in Beta.
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

---

### Post by Tikkyca on 2010-02-15
> **Thisislaw said:**
> Yes, there is. Currently, it is in Beta.
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

Thank you SO much!!! :P

---

### Post by ajgreeny on 2010-02-15
When I installed it I had a "no microphone" sound problem until I installed padevchooser, and I still can not get my camera to work as a webcam, which it did in jaunty.  Webcams seem less well supported in this version of skype, compared to previous ones, and there are lots of threads about that in this forum.

---

### Post by Vakman on 2010-02-15
No problem.
Odd I have never had any problems with my microphone.
Webcams can always be a different story.
But I am overall impressed with the Skype beta thus far.
I assume that the microphone and webcam problems existed in other programs as well and is probably not the fault of Skype?

---

### Post by ajgreeny on 2010-02-15
No, the mic was and still is OK in audacity and sound-recorder, and the camera worked, and still works with cheese, so it is definitely something in skype that caused, and is still causing the problems.

I only other VOIP users would use another open source app, it might be easier, and I could dump skype, but Of course, hardly anybody even knows there are alternatives available, and the only way to talk with skype users is to use skype.

---

### Post by Linuxforall on 2010-02-15
For those with video issue try LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype command in terminal and see if it goes away.

---

### Post by ajgreeny on 2010-02-15
Can I ask what that command does, and how can I reverse it if either it does not work, or even makes things worse?

Or does it just start skype that one time with those options?  I have tried starting using that option but it is just ignored according to the terminal, showing this error:-
> ERROR: ld.so: object '/usr/lib32/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.It is helpful, by the way, if you put all commands in a code box (select it and use the # button in the text entry box for posts), please, as it makes it easier to see where commands start and finish.

EDIT:
OK, I've realised I don't have the /usr/lib32 folder but only a /usr/lib, so I changed the command you suggested to ```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype
``` and in terminal that is good, but if I use it as the command in a new launcher or menu item, it does not work at all, skype does not start.  I have also tried using that command as a simple bash script, saving it in my home.
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype
```and then running that gets me nowhere, so what on earth is going on?  Am I missing something simple here, or is this destined not to work?  Why does the command work in terminal but not as a script, nor as a menu command nor launcher?

EDIT No 2:
OK, more searching did the trick.  The only way I could get it to run was by making the script slightly different:-
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so 
/usr/bin/skype
```
This is something to
do with variables not being able to get child processes running, and here I quote from a thread nearly a year ago.
> snova
March 10th, 2009, 02:10 AM

Create a script e.g. runskype and put the commands below
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype

Make the script executable (e.g. chmod +x runskype). You can then run skype by doing ./runskype from the directory containing the script or put the script somewhere in your path e.g. /usr/local/bin and you can then just enter "runskype" in a terminal. You can even make a menu or desktop entry for runskype if you wish.

This was pretty close, however the script should be:


#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype


Because variables are not propogated to child processes without using export.



---

### Post by Tikkyca on 2010-02-15
Skype for ubuntu is so cool. :p

---

### Post by ajgreeny on 2010-02-16
Here we go, hopefully a final post from me in this thread, and a recommendation of a great low cost webcam that works OOTB in 9.10 without any of the fiddling that was needed for my digital camera to be used as webcam.

I have just bought a Logitech C120 webcam (£9.99 from many sources in UK), plugged it into the usb socket and ran skype with the simple command "skype", rather than the shell script noted earlier to run it, and it all works brilliantly.  Great little webcam, and recommended for use with ubuntu.

---

### Post by Tikkyca on 2010-02-18
Skype for ubuntu is sooo awsome! :D

---

### Post by Tikkyca on 2010-02-18
> **ajgreeny said:**
> Here we go, hopefully a final post from me in this thread, and a recommendation of a great low cost webcam that works OOTB in 9.10 without any of the fiddling that was needed for my digital camera to be used as webcam.

I have just bought a Logitech C120 webcam (£9.99 from many sources in UK), plugged it into the usb socket and ran skype with the simple command "skype", rather than the shell script noted earlier to run it, and it all works brilliantly.  Great little webcam, and recommended for use with ubuntu.

Cool :D

---

