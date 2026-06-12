---
title: "Ati HD4850 and video playback issue"
date: 2008-10-23
forum: Multimedia Software
---

### Post by toystory on 2008-10-23
Hi all, i'm an ubuntu newbie, but i've learned a lot through the forums. 
I recently updated from my Nvidia 7600GT to an ATI HD4850 (very happy about it), and I managed to install it with no problem. I had the screen flicker in video playback, but i managed to solve it using Movie player (Gstreamer), but i don't like TOTEM too much. I switched Mplayer from Xv to x11 (x11 XImage/SHM) which solves the flickering but i can't go double the screen size or full screen. 
If i go double size, the windows goes double size, but not the video, and so on on fullscreen. What am I doing wrong? 
I tried installing Vlc but i'm only getting version 0.8.6, i can't get 0.9.3 or 0.9.4 because some files are missing at the c-korn repositories. 
Any help will be much appreciated. 

Thanks in advance, 
Luis

---

### Post by toystory on 2008-10-25
Hi, anyone there that can help me? 
Thanks in advance :)

---

### Post by genjuroSE on 2009-01-11
To zoom the image in mplayer, just use:
mplayer -vo <driver> -zoom <video>

---

### Post by AKADAP on 2009-01-11
To eliminate the flashing, us a window manager other than Compiz until compiz gets fixed.
you can install the "Compiz Fusion Icon". This allows you to switch between Compiz and Metacity.

---

### Post by binbash on 2009-01-12
> **toystory said:**
> Hi all, i'm an ubuntu newbie, but i've learned a lot through the forums. 
I recently updated from my Nvidia 7600GT to an ATI HD4850 (very happy about it), and I managed to install it with no problem. I had the screen flicker in video playback, but i managed to solve it using Movie player (Gstreamer), but i don't like TOTEM too much. I switched Mplayer from Xv to x11 (x11 XImage/SHM) which solves the flickering but i can't go double the screen size or full screen. 
If i go double size, the windows goes double size, but not the video, and so on on fullscreen. What am I doing wrong? 
I tried installing Vlc but i'm only getting version 0.8.6, i can't get 0.9.3 or 0.9.4 because some files are missing at the c-korn repositories. 
Any help will be much appreciated. 

Thanks in advance, 
Luis

that is what i always get at mplayer, i couldn't find a solution to that so i am using X11 output with vlc or smplayer

---

### Post by dyrer on 2009-01-16
> **AKADAP said:**
> To eliminate the flashing, us a window manager other than Compiz until compiz gets fixed.
you can install the "Compiz Fusion Icon". This allows you to switch between Compiz and Metacity.

Worked for me

---

### Post by jakeman66 on 2009-01-25
In MPlayer preferences on the Video tab, switch to the gl2 driver.  This allows me to zoom the video to double or fullscreen.

Using ATI HD4850s in crossfire and Metacity.

COMPIZ causes flikering.

---

### Post by pedrogent on 2009-02-15
> **AKADAP said:**
> To eliminate the flashing, us a window manager other than Compiz until compiz gets fixed.
you can install the "Compiz Fusion Icon". This allows you to switch between Compiz and Metacity.

Thanks a lot - this worked a charm for me!

---

