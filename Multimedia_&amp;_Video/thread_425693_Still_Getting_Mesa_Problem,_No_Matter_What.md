---
title: "Still Getting Mesa Problem, No Matter What"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by ppatalano on 2007-04-27
My output for fglrxinfo continues to be 
> peter@peter-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)



I feel like I have tried installing and configuring fglrx every different way, yet I am still faced with this problem. If anyone can help, that would be amazing. :confused:

---

### Post by qamelian on 2007-04-27
> **ppatalano said:**
> My output for fglrxinfo continues to be 


I feel like I have tried installing and configuring fglrx every different way, yet I am still faced with this problem. If anyone can help, that would be amazing. :confused:

What model of ATI card do you have? Some older models are no longer supported by the FGLRX driver.

---

### Post by ppatalano on 2007-04-27
ATI FireGL V5200

---

### Post by qamelian on 2007-04-27
> **ppatalano said:**
> ATI FireGL V5200

While I can't give you any real assistance because I use the open source drivers (ATI stopped supporting my card a while ago), at least the latest release notes indicate that your card is still supported.

What methods have you already tried?

---

### Post by ppatalano on 2007-04-27
Installing from the ATI site, using envy, and using a multitude of installation guides. The worst part is that I had this card working with edgy just a few weeks ago.

---

### Post by toodaloo on 2007-05-02
i have the exact same problem.
and i've tried the exact same solutions too, and my graphics were working fine with edgy.
but ever since the mesa open source drivers or something were installed with feisty,
the fps for glxgears has gone way down, xgl/beryl doesnt work and etc.
also
robin@robin-desktop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

robin@robin-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
.
and yeah, i tried loking at the xorg conf but everything looks fine.

---

### Post by NT4usB on 2007-05-02
(shot in the dark...)
When you ran envy, did you try choosing the uninstall to remove all the ATi stuff first, then run the install?
...worked for me.

---

### Post by toodaloo on 2007-05-04
ill try that
wow,
im doing that right now, and its removing al the open source ati drivers.
when i manually tried to uninstall those it never worked. AWESOME!
im pretty sure it'll all work when its done =D
thanks
edit:
nevermind, that still didnt work
robin@robin-desktop:~$ glxinfo | grep "direct"
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

glxgears still gives around 300fps, very litttlleee
i use a radeon 9800, and i didnt have problems with it in edgy =\

---

### Post by toodaloo on 2007-05-05
wait, is there any way to completely remove the mesa open source driver that comes with the feisty upgrade?
edit:
i tried using synaptic, but it removes alot of other packages along with it =(

---

### Post by ppatalano on 2007-05-05
Ok I've made some progress. I now do not get the mesa thing anymore when I do fglrxinfo instead i get 
> peter@peter-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)


The problem is, is that my card is not an x1600 but a firegl v5200

---

### Post by toodaloo on 2007-05-05
ppatalano, what didja do to get your fglrxinfo like that?
i've made no progress at all, using envy and reinstalling uninstalling etc.
can you please tell me what you did?, im having trouble =\

---

### Post by ppatalano on 2007-05-06
I installed the fglrx driver and in the restricted modules manager I enabled the ATI graphics driver and rebooted. After I ended up with that for my fglrxinfo. :)

---

### Post by toodaloo on 2007-05-07
eeesh, i tried that, and it still doesnt work.
i tried using envy to do it, and it still doesnt work, i still end up having mesa as my ati graphics driver.
=\
ill just wait i guess, ijust cant play games, but wtaching movies is good enough.

---

### Post by ppatalano on 2007-05-07
I guess we are in the same boat  :mad:

---

