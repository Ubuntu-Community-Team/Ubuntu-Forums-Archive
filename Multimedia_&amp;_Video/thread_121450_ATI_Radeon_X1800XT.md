---
title: "ATI Radeon X1800XT"
date: 2006-01-25
forum: Multimedia &amp; Video
---

### Post by Rich464 on 2006-01-25
Hi, Have just switched from Fedora Core to Ubuntu but It looks like im gonna have to go back as I cant get my ATI Radeon X1800XT to work.

I have followed the instructions in the various threads on the forums and tried installing the fglrx driver but to no avail.

Has anyone ideas, experienced anything similair or know if the fglrx driver even supports the newer X1800Xt chipset?

Any help is much appreciated as I'm stuck with a Linux system and no GUI :(

---

### Post by MarkUK on 2006-01-25
I too have this problem with my Rad 9800 Pro :(

---

### Post by gmc on 2006-01-25
Same here. With ATI X1400 (Acer 5672WLMI). Of course I should point out that in order to install Ubuntu on the above laptop, I had to install Dapper.

G.

---

### Post by nilly on 2006-01-25
And by that youre saying that it worked in fedora?? with 3d?? that beats me!? wtf's up with ubuntu and fglrx if thats the case??

Please report..

---

### Post by nilly on 2006-01-27
Hey Rich464!!

How did your graphics work in fedora??

//nilly

---

### Post by Horndog on 2006-01-27
[QUOTE=MarkUK]I too have this problem with my Rad 9800 Pro :([/QUOTE]

```

horndog@HornDogsHouse:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5582 (8.21.7)


```

My ATI 9800pro works great, with the latest drivers too.
show us your "fglrxinfo" "glxgears -printfps" output.

```

horndog@HornDogsHouse:~$ glxgears -printfps
21395 frames in 5.0 seconds = 4278.936 FPS
22555 frames in 5.0 seconds = 4510.941 FPS
22571 frames in 5.0 seconds = 4514.179 FPS
22541 frames in 5.0 seconds = 4508.169 FPS
22569 frames in 5.0 seconds = 4513.738 FPS
22557 frames in 5.0 seconds = 4511.359 FPS
22553 frames in 5.0 seconds = 4510.587 FPS
22558 frames in 5.0 seconds = 4511.420 FPS

```

---

### Post by John64 on 2006-04-25
mine works, but the performance is horid.  Screensavers are too much.

---

