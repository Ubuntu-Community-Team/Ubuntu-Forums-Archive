---
title: "Gstreamer - subclass did not specify output size error"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by petermck on 2006-11-10
I have Dapper Drake on a Toshiba Satellite Laptop with an ATI graphics system and on a PC with an AMD Sempron CPU and SIS 741 AGP integrated graphics card.
I've installed the good, bad and ugly gstreamer-0.10 stuff, w32codecs, pitfdll in exactly the same way on both machines.
On the Laptop, I can play wmv files with no problems. Even the firefox plugin works.
On the PC I get an error "subclass did not specify output size". Has anyone seen a fix for this?

---

### Post by Nikusan on 2006-11-14
Same problem here, except I'm using edgy and w32codecs from the edgy-plf repository.

I posted elsewhere about real video playback being broken, so I'm starting to suspect this w32codecs package.

---

### Post by HeWhoE on 2006-11-16
I get this error message as well (on Dapper).  This occurs when I set the gstreamer "Default Output Plugin" to "X Window System (No Xv)"  I have it on this setting because I'm using aiglx (for Beryl), and I'm just following instructions from the Beryl HOWTOs.  I put it on this setting by running from the terminal:> gstreamer-properties

I've tried using the "X Window System (X11/XShm/Xv)" setting, but the video gets all weird -- it displays sometimes if I double-click the video to put it in full screen, but I have to do it carefully, without moving the mouse.  Most of the time, the whole video becomes black.  If it's not all black, chunks of the video also get covered with black boxes after the position bar (on the bottom of the screen) and the "Leave Fullscreen" button (at the upper-right corner) pop up.  

What I like most about totem is its capability of reading files directly over smb://, so I can play videos and music directly over my samba connection.  It's lousy that I can only watch it in its original size and not in full-screen.

---

### Post by petermck on 2007-01-01
I updated my drivers for the graphics (ATI Xpress 200M) with the ATI proprietry drivers and this fixed a whole lot of problems. In particular direct rendering now works. Check out [http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati](http://www.ubuntuforums.org/showthread.php?t=321766&highlight=howto+ati) if you have one of these cards. The problem may be somehow related to some other DRI problem. Try 'glxinfo' and see if direct rendering on.:)

---

### Post by petermck on 2007-01-03
Hi,
I forgot that I made one other change which got .wmv files working in totem. In Synaptic I ckecked all the repositries. i.e Important, Recommended, Proposed and Backported. I think this actually fixed the problem...but I'm not sure.

---

