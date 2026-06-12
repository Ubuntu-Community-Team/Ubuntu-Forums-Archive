---
title: "Acceleration, but no DRI with fglrx on Edgy"
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by ddgromit on 2006-11-25
After a lot of trouble, I got the fglrx driver successfully.  The MESA driver has been replaced with the ATI driver.  Here is my fglrxinfo:
```
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

The great thing is, Beryl and XGL runs.  The bad thing is, it uses a lottt of CPU power though.  Moving a window around quickly uses full cpu load and lags things in the background.  I think the problem is that for some reason, DRI is not enabled: 

```
$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No

```

When installing fglrx, I followed the [tutorials]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") closely, including adding the line Option "Composite" "false" under 'Extensions'.  Load "DRI" is under the Modules section as well.  My full xorg.conf is attached below.  Has anyone had this problem, or know what could be disabling direct rendering?

---

### Post by eBait~ on 2006-12-07
Okay. I had Beryl to work under 6.06, went fine.
But I upgradead to 6.10, updated drivers, same as ddgromit, full acelleration in X, none in XGL. 
fglrx outputs here:
In X: 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)
In XGL:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

Also spent many hours searching.. did all the tut's and it didnt work :( Any help please?

---

### Post by TDsai on 2006-12-09
i have the same issue. someone said on this forum that it is normal since xgl is running on top of xorg. i wonder however if booting xgl on display:0 and not boot x at all will fix this issue and have full 3d accel on xgl and beryl

heres the how to:
  Method B: Make Xgl Your Standard Display Server for Ubuntu Users
  [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)


then please post here the results
thanks

---

