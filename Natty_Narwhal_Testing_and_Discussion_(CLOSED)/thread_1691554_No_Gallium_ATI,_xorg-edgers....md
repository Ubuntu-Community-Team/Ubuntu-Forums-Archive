---
title: "No Gallium? ATI, xorg-edgers..."
date: 2011-02-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-02-20
```
:~$ cat /etc/X11/xorg.conf
Section "Device"
Identifier "Default screen"
Option "ForceGallium" "True"
EndSection
:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL DRI2
```

---

### Post by zika on 2011-02-26
To rephrase: How to turn Gallium ON, now, for ATI...?

---

### Post by Harry33 on 2011-02-26
> **zika said:**
> ```
:~$ cat /etc/X11/xorg.conf
Section "Device"
Identifier "Default screen"
Option "ForceGallium" "True"
EndSection
:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL DRI2
```

Yes it seems you have Gallium in use now (mesa dri r600).
This is what xorg-edgers PPA say:
```
- r600g is now in libgl1-mesa-dri and available for use by adding Option "ForceGallium" "True" to your xorg.conf

```

---

### Post by zika on 2011-02-26
> **Harry33 said:**
> Yes it seems you have Gallium in use now (mesa dri r600).
This is what xorg-edgers PPA say:
```
- r600g is now in libgl1-mesa-dri and available for use by adding Option "ForceGallium" "True" to your xorg.conf

```I've read that text some many times...
I've added that, a month ago, or so, see my 1st post, but... It worked until a week ago...
Before that there was environment variable for turning Gallium ON...
If I did not turn it O, I would get Mesa DRI R600 ( RV635 959 )  20090101  TCL DRI2...
So, I deduct that it is OFF. Am I wrong?

---

### Post by Harry33 on 2011-02-26
> **zika said:**
> I've read that text some many times...
I've added that, a month ago, or so, see my 1st post, but... It worked until a week ago...
Before that there was environment variable for turning Gallium ON...
If I did not turn it O, I would get Mesa DRI R600 ( RV635 959 )  20090101  TCL DRI2...
So, I deduct that it is OFF. Am I wrong?

Doesn't "Force Gallium" "True" turn it on?

---

### Post by zika on 2011-02-26
> **Harry33 said:**
> Doesn't "Force Gallium" "True" turn it on?
No...
It stopped a week ago...
Read my posts above... :)
Current state:```
:~$ cat /etc/X11/xorg.conf
Section "Device"
Identifier "Default screen"
Option "ForceGallium" "True"
EndSection

Section "Device"
Identifier    "Configured Video Device"
Driver        "radeon"
EndSection

Section "InputClass"
Identifier "middle button emulation class"
MatchIsPointer "on"
Option "Emulate3Buttons" "on"
EndSection

``````
:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL DRI2

```Up-to-date with Xorg-Edgers and Natty...

---

### Post by stan3 on 2011-02-26
You saw this right? (standard natty package)

```
xserver-xorg-video-ati (1:6.14.0-0ubuntu1) natty; urgency=low

  * New upstream release
  * Drop 101_select_between_classic_and_gallium_dri.patch.  Default to gallium
    everywhere, and rely on libGL and the Xserver to fallback when necessary
    (LP: #715939)

 -- Christopher James Halse Rogers <raof@ubuntu.com>  Fri, 18 Feb 2011 13:32:01 +1100
```


```
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on AMD RV670
```

---

### Post by zika on 2011-02-26
> **stan3 said:**
> You saw this right? (standard natty package)

```
xserver-xorg-video-ati (1:6.14.0-0ubuntu1) natty; urgency=low

  * New upstream release
  * Drop 101_select_between_classic_and_gallium_dri.patch.  Default to gallium
    everywhere, and rely on libGL and the Xserver to fallback when necessary
    (LP: #715939)

 -- Christopher James Halse Rogers <raof@ubuntu.com>  Fri, 18 Feb 2011 13:32:01 +1100
``````
$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on AMD RV670
```
Yes.
That is the reason why I started to explore.
Mine is: 1:6.14.99+git20110222.acd54a48-0ubuntu0sarvatt

---

### Post by zika on 2011-02-27
Found it!:
The reason was Xorg-Edgers-PPA. Purged it, and:
```
:~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on AMD RV635

```
I thought XEPPA should be on &#8222;the edge&#8220;... :D
Marking this &#8222;Solved&#8220;...
Thank You!

---

