---
title: "Nvidia - API Mismatch"
date: 2008-07-16
forum: Multimedia Software
---

### Post by qe2eqe on 2008-07-16
Dmesg tells me:
[  713.742751] NVRM: API mismatch: the client has the version 96.43.05, but
[  713.742756] NVRM: this kernel module has the version 71.86.04.  Please

About the version numbers: Nvidia says my card works (only) for 96.43.*, and 71.86.* is for even older cards.

Anyways, how do I change my module version?

uname -r  says  2.6.24-19-generic

---

### Post by qe2eqe on 2008-07-16
So I followed some advice on another post, removed nvidia, restricted modules, and all that...

the API mismatch error is gone. Now, the only error in either dmesg or x's log is:
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

---

### Post by qe2eqe on 2008-07-16
Steps taken:
Remove nvidia packages, install nvidia-glx packages, no worky.
Remove nvidia, ran "sh *.run" from nvidia, it needed libc-dev, apt-get libc... 
Ran *.run again, no errors. No worky.
apt-get linux to refresh current headers.... (I don't know if nvidia's script is compiling modules for the right kernel...how?). Re-ran nvidia's script, no worky, but the api mismatch error is gone.
The nvidia-legacy 'works', as in it gives me resolution choices back and even has an nvidia logo, but glxgears/glxinfo iforgetwhich gives a segfault, "module GLX is not loaded", same error in glxinfo as with nvidia-glx package.
Also, I excluded modules nv, nvidia-new, and regenned xorg.conf afresh a number of times. 
My card is reported by nvidia to be supported for the 96.* range driver. 

--------also
Modprobe nvidia
rmmod nvida => nvidia not found in proc/modules 
---------
That seems to be the issue.


------
This file is the log after startx -- -logverbose 6
[http://pastebin.com/m6059a080](http://pastebin.com/m6059a080)

---

### Post by qe2eqe on 2008-07-16
Did the steps at [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
including alternate modprobe options in the special section for the 420 MX. 

Also tried envy, a la [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

[edit]: <--- Fail.

---

### Post by qe2eqe on 2008-07-16
OMFG - SOLVED. 
Heres what I did: I went to ubuntuguide.org.... followed those instructions.

Essentially, I CLICKED xfce menu > system > hardware drivers.
Then I enabled the driver and rebooted. 

---
Direct render is on, glxgears no problems. 

I can't believe that was the answer... anyone have any idea why nothing else worked? Does 'Hardware Devices' unclick box trump everything, and make fail? Ever notice how episodes of the twilight zone end always with questions?

---

