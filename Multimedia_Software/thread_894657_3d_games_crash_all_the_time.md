---
title: "3d games crash all the time"
date: 2008-08-19
forum: Multimedia Software
---

### Post by tetrafuran on 2008-08-19
Some games freeze the computer entirely while others just quietly exit back to the desktop.

This problem is nowhere near consistent. Sometimes I can play for hours without any problems and just yesterday I started a few different games like 10 times in less than one hour. "normally" a game runs less than a minute until it crashes and exits. 

I tried running these games from the terminal and usually they talk about "segmentation errors" as they crash and exit. 

Normal 2d games never crash so I figure it has to have some thing to do with nvidia drivers or something.

---

### Post by Sam Lars on 2008-08-19
Some related info that may be helpful:
```
lspci | grep VGA
```
Are you using 64 or 32 bit?
I'm assuming you have 3D drivers installed, you mentioned the nvidia driver...

---

### Post by tetrafuran on 2008-08-19
```
lspci | grep VGA
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)


```There's the info you requested. I didn't know that command... anyway the info seems to be correct. I am using an Nvidia chip geforce 7300GT. I am able to use 3d games at a reasonable frame rate so I am inclined to think the drivers work well enough.

This issue might be driver related, but who knows. Other libraries, software etc might cause it too.

Currently I'm running the latest 64 bit ubuntu. I have another hard drive with a 32 bit xubuntu on it, but it's drivers got so messed up, I was stuck with 640*480 res. I tried to fix it for days and eventually gave up. A brand new shiny OS did the trick as long as resolution and colours are consearned. When nvidia drivers go wild it's a good time to re-install ubuntu. That has now twice been proven to be the fastest and easiest quick and dirty solution available.

I tried running some games under fluxbox but they still seem to crash on that "segmentation fault". Apparently this has nothing to do with gnome. Still it makes me wonder how those games run very nicely for a few minutes before exiting automatically and unexpectedly.

---

### Post by Sam Lars on 2008-08-19
If you can run them, you're probably using the right stuff.  Are you using compiz?
Does this command say "Yes?"
```
glxinfo | grep "direct rendering"
```

---

### Post by tetrafuran on 2008-08-20
```
direct rendering: Yes


```
I'm not using Compiz. or any other similar 3d desktop. Besides I tried running these games under fluxbox and the same thing happens there too. BTW 3D screensavers work as intended. I wonder if they would produce segmenation faults if I were to run one of them for an hour...

I just tried a game called sauerbraten in a very very low res mode. It looked a little bit like Doom 1, but it still froze the computer totally. Ctrl alt backspace did nothing and reset button was the only key it responed to. 

I'll continue these tests to see if this retro graphics version of sauerbraten would run more than an hour without segmentation faults.

Somehow I am beginning to think that this freezing might be a separate issue. Immedietly after reboot it froze while loading bios. Actually now I'm pretty sure it is. At such an early boot pase nvidia drivers or ubuntu software could not have caused that.

---

