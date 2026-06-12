---
title: "gatos on edgy?"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by Fittersman on 2006-11-12
can i use a gatos on edgy to make tv output work?

and if i can how do i do it?

---

### Post by jkwarras on 2006-11-12
See here:
[http://ubuntuforums.org/showpost.php?p=1703492&postcount=22](http://ubuntuforums.org/showpost.php?p=1703492&postcount=22)

---

### Post by Fittersman on 2006-11-12
when i type in the first command i get:

```
cleippi@cleippi-desktop:~$ sudo apt-get install x11proto-xf86dri-dev libdrm-dev x11proto-xext-dev x11proto-xextproto-dev x11proto-video-dev render-dev x11proto-randr-dev x11proto-fonts-dev x11proto-core-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
x11proto-xext-dev is already the newest version.
E: Couldn't find package x11proto-xextproto-dev
```

and i dont think that tutorial works for a radeon 7500 card either

---

### Post by jkwarras on 2006-11-14
You could try to install even without that package. For me it almost works: The signal is sent to the TV via S-Video but the output is garbled (black and white lines moving all around).

---

### Post by Fittersman on 2006-11-14
well that helps me to watch movies then... thanks](*,) 

lol im just buggin you but if you got a way to get it to work properly that would be great because mine will output but it is all weird looking and hard to explain...

---

### Post by jkwarras on 2006-11-15
> **Fittersman said:**
> 
lol im just buggin you but if you got a way to get it to work properly that would be great because mine will output but it is all weird looking and hard to explain...
I'll like to help you but I didn't manage to get this working. I had to plug the LCD monitor via VGA (not DVI) to be at least able to output to the TV-Out weird black and white moving lines via S-Video.

Taking a look at the /var/log/Xorg.0.log file will give you valuable information about what's going on on the background with your Xserver. In my case the second display (TV via S-Video) isn't recognised, so the TVoutput option is not used. I suggest you to take a look at it, and see if there's something wrong going on.

I had to switch to the propietary driver (fglrx) to get TV-Out.

---

### Post by Fittersman on 2006-11-15
mine will output fine its just the resolution that is messed up so the picture is unclear.

ill try and explain using an example (probably wont make sense but ill try)

think of it as if nobody said it has to go to a new line after it gets to a certain point and it keeps going until the end of the tv screen.

asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|

that is how it would normally be (every line starts with an "a" and ends in an "f") but on the tv it looks like


asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasd|
dfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfa|
sdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdf|
asdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasdfasd|


as you can see the letters dont line up as they are supposed to so the picture is completely unclear. I have tried all the resolutions already.

---

