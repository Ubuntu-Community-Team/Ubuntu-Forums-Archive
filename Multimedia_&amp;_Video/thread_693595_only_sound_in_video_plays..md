---
title: "only sound in video plays."
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by sohaibma on 2008-02-11
when I play any video file on my ubuntu 7.10, only sound plays. There are no visuals. (Note: I have installed all the required codecs). This happens in all multimedia softwares except vlc. In VLC when I open the video once, only sound plays. When I open the same video again in vlc (in a new window), without closing the previous attempt, the video plays correctly. Please help me out here. How can I avoid this annoyance.

---

### Post by ubuntu-freak on 2008-02-11
Just to be sure, please install the essential packages in my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Anything you already have will be skipped.
 
Nathan

---

### Post by Pandemic187 on 2008-02-11
> **reassuringlyoffensive said:**
> Just to be sure, please install the essential packages in my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Anything you already have will be skipped.
 
Nathan
Just curious, do you know if the codecs in the Ubuntu restricted package include all of the codecs mentioned in your thread? If you know of any differentiation, please specify.

---

### Post by ubuntu-freak on 2008-02-11
> **Pandemic187 said:**
> Just curious, do you know if the codecs in the Ubuntu restricted package include all of the codecs mentioned in your thread? If you know of any differentiation, please specify.

 
It includes all of them and more. It also installs w32codecs, faad, gstreamer pitfdll which aren't in the extras package, niether is java fonts and ccsm. Basically, it's better than the extras package and let's you see exactly what you're installing.
 
Nathan

---

### Post by sohaibma on 2008-02-12
i got it. Just had to change the video output module in vlc from default to x11 and it works. Now i can see videos in vlc. In the others (like totem movie player) i dont know how and what to change. please help me out here.

---

### Post by ubuntu-freak on 2008-02-12
> **sohaibma said:**
> i got it. Just had to change the video output module in vlc from default to x11 and it works. Now i can see videos in vlc. In the others (like totem movie player) i dont know how and what to change. please help me out here.

 
You shouldn't use x11 as it's poor quality. What graphics device do you have? When did you install Ubuntu?
 
Try navigating to System>Preferences>Appearance>Effects and then turn off desktop effects. See if video works in VLC and Totem then.
 
Nathan

---

### Post by sohaibma on 2008-02-12
I probably should have told you this earlier....
I am using Xubuntu without any desktop effects, and I have a "via unichrome pro igp".
And I installed ubuntu a few hours before starting this thread.
I have had this problem in earlier versions of ubuntu and xubuntu also (7.04, 6.10, 6.06).

---

### Post by ubuntu-freak on 2008-02-13
I think you need to install binary drivers. Try this thread
 
[http://ubuntuforums.org/showthread.php?t=636368](http://ubuntuforums.org/showthread.php?t=636368)
 
It's very rare for someone to not have the possibility of watching vids with the xv driver, so don't give up.
 
Nathan

---

### Post by sohaibma on 2008-02-13
ok.
I installed the drivers. Now vlc is playing the video in default output module, but the brightness is too high (it still plays fine if I select X11 as output module and if i select opengl the video doesn't play smoothly). Totem player is playing the videos but the screen is covered with thin green lines, so i am unable to see anything clearly. 

Please help me out here.

---

### Post by ubuntu-freak on 2008-02-13
> **sohaibma said:**
> ok.
I installed the drivers. Now vlc is playing the video in default output module, but the brightness is too high (it still plays fine if I select X11 as output module and if i select opengl the video doesn't play smoothly). Totem player is playing the videos but the screen is covered with thin green lines, so i am unable to see anything clearly. 

Please help me out here.

Can't you just adjust the brightness in VLC? Are you using Totem Gstreamer or Xine? Try MPlayer as well. Great you got xv playback "kind of" working though. Hope you get it working perfectly.

Nathan

---

### Post by sohaibma on 2008-02-13
Thanks for your help nathan. 
I'm using totem gstreamer. Adjusting the brightness isn't working (it makes no change). Any ideas on what i should do next?

---

