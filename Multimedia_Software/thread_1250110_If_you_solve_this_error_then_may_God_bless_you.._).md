---
title: "If you solve this error then may God bless you.. :)"
date: 2009-08-26
forum: Multimedia Software
---

### Post by red33m on 2009-08-26
Hello everyone in and of of this thread...

I was trying to install yesterday a program called byzanza..and it told me that in order for it to work fine I should turn off all the Extra Visual Effects including Compiz Fusion..(the cube,expo,desktop wall..etc.) which I was using before...

I have tried everything literally and nothing seems to work. I completely removed byzanza I reinstalled all my drivers, I even reinstalled compiz fusion and none of these work,,:(

Every time I try to activate Extra VE it tells me that they could not be enabled...what should I do..all answers accepted..  !

Thanks for all the answers!!

---

### Post by mess110 on 2009-08-26
maybe try in terminal

```
killall byzanza
```

it should kill its process. now try running the VE

---

### Post by mc4man on 2009-08-26
Take a look here

In a terminal run 
```
gconf-editor
```
expand 'apps', scroll down and expand 'metacity'. Under the general settings make sure 'compositing manager is unchecked as in screen

---

### Post by red33m on 2009-08-26
That was so close my friend...! It was checked..I unchecked it but still I can't get the VE back to Extra...  GgggrrrR !  Are there any other suggestions??

---

### Post by mc4man on 2009-08-26
Have you checked that your restricted driver is still installed? (if one was available

this in terminal should show if direct rendering is enabled and what driver is in use (only the first 5 or 6 lines matter
```
glxinfo
```

If direct rendering is enabled then maybe...

Go directly to System -> preferences -> Advanced Desktop Settings Manager and if the cube or wall is enabled, then disable, reboot and then try to set one or the other (in  Advanced Desktop Settings Manager, not Appearance  

( if no menu option in Preferences of "Advanced Desktop Settings Manager" then install
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by red33m on 2009-08-26
It said this mate:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

what is that?

---

