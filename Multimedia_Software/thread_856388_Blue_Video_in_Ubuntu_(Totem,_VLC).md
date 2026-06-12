---
title: "Blue Video in Ubuntu (Totem, VLC)"
date: 2008-07-11
forum: Multimedia Software
---

### Post by aidave on 2008-07-11
The colors will not play back properly on my system.  I have Ubuntu 8.04.01 with NVIDIA on a Dell.  I recently did a fresh install and that did not solve the problem.  

I have also tried this guide but to no avail:
[http://www.mikesplanet.net/2007/05/im-so-blue/](http://www.mikesplanet.net/2007/05/im-so-blue/)

Flash videos look normal in a web browser, but not when played in Totem or VLC.

How do I get regular video again?

---

### Post by aidave on 2008-07-11
I tried some other things, and setting Default Video Output worked:

"X Window System (No Xv)"

---

### Post by Egi_Power on 2008-09-10
I had the same problem.
Here is how I fixed it:

First make sure gstreamer0.10-ffmpeg is installed. Copy and paste in terminal:
```
sudo apt-get install gstreamer0.10-ffmpeg
```
(I had it installed already.)

Next step run gstreamer-properties
```
gstreamer-properties
```
The Multimedia Systems Selector will pop-up. Click on the Video tab.
Under Default Output change the plugin to 'X Window System (No Xv)'
Alt+T to test the new settings.
If the colors are good, just close it Alt+C.
You probably need a Ctrl+Alt+Backspace for the new settings to take effect.

It did the trick for me.
I hope it will help someone.

Here is a [link]("http://ubuntuforums.org/showthread.php?t=766683") to a [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by BrownieBoy on 2008-11-24
Worked for me.  Many thanks.

However, I had to do a reboot before the gstreamer properties change took effect.  You may get away with logging out then back in again and/or restarting Xorg via Ctrl->Alt->Backspace.

---

### Post by dorkdork777 on 2008-12-22
Excellent, Egi_Power's guide worked wonders on Ubuntu 8.10, 64-bit. No idea why this happened, but it's fixed now =D I just did exactly what he said, then did a Ctrl-Alt-Backspace to restart X.

Here's some examples so people with the same problem can compare:

**With problem** ------------------------------------------------------------------------------ **After fixed**
[IMG]http://i34.tinypic.com/27xi3ns.jpg[/IMG][IMG]http://i36.tinypic.com/j0i5gk.jpg[/IMG]
[IMG]http://i36.tinypic.com/345lywy.jpg[/IMG][IMG]http://i34.tinypic.com/vhuxpe.jpg[/IMG]
[IMG]http://i37.tinypic.com/2rdaref.jpg[/IMG][IMG]http://i34.tinypic.com/2w55ctz.jpg[/IMG]
[IMG]http://i36.tinypic.com/wm1onr.jpg[/IMG][IMG]http://i33.tinypic.com/1ora4k.jpg[/IMG]

Hope this helps someone =)

---

### Post by egirl723 on 2009-11-01
Egi_
thank you so much.  a year later and your suggestion's still working.  I was getting a complete blue screen with no video.  thanks again

---

### Post by Egi_Power on 2009-11-02
> **dorkdork777 said:**
> Excellent, Egi_Power's guide worked wonders on Ubuntu 8.10, 64-bit.

> **egirl723 said:**
> Egi_
thank you so much.  a year later and your suggestion's still working.  I was getting a complete blue screen with no video.  thanks again

I am really happy to hear that I could help.

Take it easy.

Egi_Power

---

### Post by christodoulidesd on 2010-02-19
thank you so much, i had the same problem too in ubuntu 9.10 and nvidia geforce 8800 gt 512 mb, but that fixed it, although it required a restart! 

Cheers

---

### Post by Dano58 on 2010-09-29
2 years later and it still works like a charm!

ubuntu 10.04 

I think it happened when I was fussing around with video codecs..

---

### Post by anacahuita on 2010-10-20
Hi, I had the same problem, with Ubuntu 10.10 - installed 10.4, but I upgraded, if I did it right -, and NVIDIA GeForce 8400M GT GPU. It fixed the player that comes with the default installation, but didn't fix VLC, even after deleting and reinstaling VLC.
Is there something else that I can do?
Thank you.

---

### Post by dkozhukhar on 2011-04-30
thanks! worked for me in 11.04 64bit!

---

### Post by gtasmy on 2011-12-07
open "Adjustments and Effects" for VLC, go to the "Video Effects" tab, if it isn't already checked, check the "Image Adjust" check box, then move the slider for "Hue" to the center, that should fix it

I don't know if you need to do the other fix mentioned first or not for this to work, I did though

---

### Post by Xan63 on 2012-05-22
Just had the same problem with Ubuntu 12.04 - still works like a charm! Thanks![http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif)

---

### Post by alkapone1959 on 2012-09-02
> Hi, I had the same problem, with Ubuntu 10.10 - installed 10.4, but I  upgraded, if I did it right -, and NVIDIA GeForce 8400M GT GPU. It fixed  the player that comes with the default installation, but didn't fix  VLC, even after deleting and reinstaling VLC.
Is there something else that I can do?
Thank you.

I have the same problem with tha same geforce and Ubuntu 11.4 like you.First of all i tweak the  gstreamer as [Egi_Power]("http://ubuntuforums.org/member.php?u=659321") says and then you can fix vlc video if you set it to get the changes that you have done before .Go to settings(tools->preferences->video) and at the output section you must select x11 video output (xcb). I hope to help you "after 2 years? :P" .

---

