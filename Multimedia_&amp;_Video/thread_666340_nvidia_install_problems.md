---
title: "nvidia install problems"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by drudogg on 2008-01-13
hello i have installed 7.10 32-bit and everything was working except my mimo wireless card, still working on that one. and i activated the nvidia driver for the graphics card... well i don't get any video at all now. 

this is a inspiron 2650 laptop and it was working fine, i just wanted to get the graphics working before i needed it for something that i was doing... 

i turn on the laptop and get the grub screen and i can go to xp pro or the ubuntu options... the normal ubuntu gives me a garbled yellow screnn and then nothing at all. after a few seconds you hear the login tones and i can type my username and password and hear it login but i can not see anything.

if i choose recovery mode then i get the command prompt as usual. can anybody tell me how to disable the nvidia drivers from the command promt in recovery mode?

btw xp works fine both of these are clean loads i did last night. i have installed the nvidia driver on my desktop and it wored fine, but it is newer and 64-bit

also would be helpful information if someone could tell me how to find out what the right driver would be cause i obviously installed the wrong one.

---

### Post by taurus on 2008-01-13
I think the first question is what kind of nvidia card does your laptop have?  Instead of installing nvidia-glx-new, maybe you need the nvidia-glx-legacy if you have an older card.

---

### Post by drudogg on 2008-01-13
well there were actually three to choose from...

nvidia-glx
nvidia-glx(new version)
nvidia-glx-legacy

i just went with nvidia-glx

windows has it listed as Nvidia GeForce2 Go

---

### Post by taurus on 2008-01-13
This command will tell you a little more about it.

```
lspci
```
Meanwhile, you can uninstall the nvidia-glx and try the nvidia-glx-legacy.

---

### Post by drudogg on 2008-01-13
well my problem is that i can't uninstall it because i can't see...

i need info on the command line to get rid of it from the recovery mode.

---

### Post by ajgreeny on 2008-01-13
Try ```
sudo apt-get remove nvidia-glx
```then when that has done its thing try ```
sudo apt-get install nvidia-glx-legacy
```Best of luck!

---

### Post by drudogg on 2008-01-13
thanks i will give that a go and see what happens!

---

### Post by drudogg on 2008-01-13
okay i was able to get into ubuntu and i can see the driver said it was removed, but still shows as checked in the restricted drivers menu. also everything is huge i can't get resolutino beyond 800x600 now, i had 1024x768 before. can not get legacy to install get this message in terminal:

 sudo apt-get install nvidia-glx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-legacy has no installation candidate

---

### Post by drudogg on 2008-01-13
so i reinstalled the whole thing... tha was an hour and a half of my life lost... 

anyway still can't get legacy to install/

---

