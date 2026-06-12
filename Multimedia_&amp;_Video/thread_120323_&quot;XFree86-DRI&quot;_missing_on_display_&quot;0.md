---
title: "&quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;"
date: 2006-01-21
forum: Multimedia &amp; Video
---

### Post by swong1 on 2006-01-21
I have an ati video card and installed xorg-driver-fglrx while I was still using Hoary. Before upgrading to Breezy, running

```
glxgears
```

brings up a window showing three gears moving and it also shows the fps. Now after upgrading to Breezy, I still see the gears but with the following error message:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

I have checked /etc/X11 and XFree86-DRI is not there. How do I fix this?

---

### Post by DoorGunner on 2006-01-21
the correct code to read your fps is 
$ glxgears printfps
for some reason Ubuntu will not print your fps with out it

However since you have the no dri .....it means that your ati drivers were not installed correctly.

Did you do an $ fglrxconfig?
Dont for get to have your V and H sync data for proper monitor setup. If you didnt

included in your xorg.conf (it is problably not there)
$ sudo gedit /etc/X11/xorg.conf
Ensure the following is included

Section "Module"
#       Load    "DRI"

reboot and then try

$ fglrxinfo
you should see ATI Technologies

$ fgl_gears
you should see a cube with glxgears in each side
speed around 800 or more depending on your card

$ glxgears printfps
your speed should be greater then 1000fps depending on your card

For some reason if this is not enough....start again using these instructions ......This is a sure fire way to get them installed correctly.
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by swong1 on 2006-01-21
I found a somewhat related thread on how to configure ati drivers

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=673874](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=673874)

Tried the following:

```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg
```

reboot

Apparently, I skrewed up the xorg.conf file and now I can't get X server. I tried to restored xorg.conf from backup, but still no luck. Please help.

Edit: found out why the X server could not start. I deleted the line that says: *Option "UseFBDev" "true"* in xorg.conf and it boots properly. 
 
Reinstalled the driver:

```
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg
```

Running
```
glxgears -printfps
```
shows the fps and the animation, but the error message Xlib:  extension "XFree86-DRI" missing on display ":0.0". Is still present.

Running
```
fglrxinfo
```
gives

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I experimented with "fglrx" instead of "ati" during the reconfigure process. The result is worse. The login splash screen doesn't even show up. No error message either. 

I hesitate to run fglrxconfig because I don't know how to answer many of the questions (e.g. I have a laptop, and I don't know what kind of "mouse" the track pad is considered as). I'm afraid to skrew up my xorg.conf further.

---

### Post by swong1 on 2006-01-23
Okay, after failing so far, I finally summoned enough courage to follow the instructions laid out in [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

And it worked! Woo..hoo..! Thanks DoorGunner, mlomker. Your how-to is very easy to follow.

```
glxgrear -printfps
14079 frames in 5.0 seconds = 2815.626 FPS
14066 frames in 5.0 seconds = 2813.051 FPS
14067 frames in 5.0 seconds = 2813.273 FPS
13991 frames in 5.0 seconds = 2798.198 FPS
13749 frames in 5.0 seconds = 2749.663 FPS

```
```

 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5582 (8.21.7)

```
```

fgl_glxgears
Using GLX_SGIX_pbuffer
1817 frames in 5.0 seconds = 363.400 FPS
2288 frames in 5.0 seconds = 457.600 FPS
2282 frames in 5.0 seconds = 456.400 FPS
2273 frames in 5.0 seconds = 454.600 FPS

```

However,
```

lspci | grep ati
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460

```

---

### Post by DoorGunner on 2006-01-24
glad we could help :D

---

