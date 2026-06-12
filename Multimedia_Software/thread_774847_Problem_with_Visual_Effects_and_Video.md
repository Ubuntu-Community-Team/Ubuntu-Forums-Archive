---
title: "Problem with Visual Effects and Video"
date: 2008-04-29
forum: Multimedia Software
---

### Post by brunolabs on 2008-04-29
Graphics: ATI X700

With the Visual Effects enabled I can't play any video (black screen).

How can I solve this problem?


Thanks.

---

### Post by brunolabs on 2008-05-02
bump

---

### Post by cor2y on 2008-05-02
Did you enable the video playback plugin in compiz-fusion?
System->Preferences->Advanced Desktop Effects , search in the filter for video playback.

---

### Post by brunolabs on 2008-05-02
I don't have that submenu.
I have access to Visual Effects through System>Preferences>Appearance.

---

### Post by cor2y on 2008-05-02
Well then you will need to install it.
Via synaptic or the terminal.
In synaptic search for compizconfig-settings-manager
In the terminal ```
 sudo apt-get install compizconfig-settings-manager
```

---

### Post by sebth on 2008-05-02
I have the same problem too.

I have the video playback plugin enabled and I have black screen for all videos too. The sound is working.

I tried with totem, mplayer, vlc... I always get the same result.

---

### Post by sebth on 2008-05-02
I installed gnome-mplayer, then in the configuration the Video Output setting was empty. I selected x11 and now my video works (only with gnome-mplayer).

I would like to fix it in other players too if anyone can help.

I don't know if that made any difference but I also followed this guide [http://ubuntuforums.org/showthread.php?t=766683&highlight=medibuntu](http://ubuntuforums.org/showthread.php?t=766683&highlight=medibuntu) and added the medibuntu repository and install the packages it mentions in part 1 and 2)

---

### Post by cor2y on 2008-05-02
What is your version of ubuntu? 8.04?
What is your video card or on board video chip?
Is video playback normal without compiz enabled?

---

### Post by sebth on 2008-05-03
Ubuntu 8.04
ATI Technologies Inc RV350 AR [Radeon 9600] (AGP card)

About compiz, I don't know what is the correct way to disable it in hardy but here is what I tried : I tried "metacity --replace" but it didn't change anything. I also stopped gdm, and modified /etc/X11/xinit/xinitrc so only totem would start with startx. The results were the same.

I also tried to create a new user in case it was some setting I had and got the same results.

The only thing that worked is gnome-mplayer, and the weird thing is the video output was empty, I just had to select x11 and the problem was gone.

---

### Post by sebth on 2008-05-03
I found the setting for VLC now. Video -> Output modules. (Check the Advanced options) and in Video oiutput module I selected "X11 video output" instead of Default and it works. 

There must be some default video output settings that every player uses. Anyone know where this might be ?

---

### Post by cor2y on 2008-05-03
The default is xv when the closed source drivers are enabled.
You are probably using the open source ati drivers.
To set it system wide go to System->Preferences->Multimedia Systems Selector the video tab and select x11 instead of Autodetect.

---

### Post by sebth on 2008-05-03
Thank you cor2y. I had use the menu editor to activate the Multimedia Systems Selector. I wonder why it was not visible by default.

I hope this solution will fix the problem for brunolabs too.

---

### Post by brunolabs on 2008-05-03
Once again I don't have this menu: System->Preferences->Multimedia Systems Selector :(

By the way, I changed the options in VLC like sebth said and now I have video playback but it is a bit pixelized.

---

### Post by cor2y on 2008-05-03
Thats strange, should be there if its plain ubuntu.
Try launching it from the terminal
```
gstreamer-properties
```
As for the pixelation thats something that happens with vlc if its asf files and some older encoded avi.
If those are not the file types then it could be the video driver itself.

---

### Post by sebth on 2008-05-03
brunolabs did you look in the menu editor ? It's System -> Preferences -> Main Menu . Make sure there is checkmark beside "Multimedia Systems Selector" in the System -> Preferences section. It was not enabled by default on my system.

---

### Post by brunolabs on 2008-05-04
I already tried everything said here and still have the pixelated video.
For now I'm going to keep the Visual Effects turned off until I figure something out.

Thanks for the help anyway. ;)

---

