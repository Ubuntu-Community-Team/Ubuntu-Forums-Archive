---
title: "Changing screen resolution using a remote control"
date: 2008-04-21
forum: Mythbuntu
---

### Post by Caps18 on 2008-04-21
I have an interesting setup here.  I now have two HDTV (1920x1080) LCD TV & projector working, and a old CRT TV (that can display 640x480, 720x480, 800x600 & 1024x768 ).

I used this advice on getting my second TV out port on my nvidia graphics card to work:
[http://ubuntuforums.org/showthread.php?t=665704&highlight=second+video+card](http://ubuntuforums.org/showthread.php?t=665704&highlight=second+video+card)

Currently, everything gets upconverted to 1920x1080.  This is a good thing.  However, as long as my LCD screen is full and the video is playing at it's full resolution, I don't care too much.  Now, what I am trying to make happen is for when this one group of video files starts playing, that MythTV will resize the resolution to one that is supported by the CRT TV.  Or is there a way to switch resolutions easily system-wide?  Like a button on the remote would change from 1920x1080 to 800x600 (640x480) or something like that?  That would be the best solution actually.

If it isn't easy, I have a work around, but it isn't very cool.  I basically can't use MythTV and have to manually start playing the files.

---

### Post by majoridiot on 2008-04-22
> **Caps18 said:**
> I have an interesting setup here.  I now have two HDTV (1920x1080) LCD TV & projector working, and a old CRT TV (that can display 640x480, 720x480, 800x600 & 1024x768 ).

I used this advice on getting my second TV out port on my nvidia graphics card to work:
[http://ubuntuforums.org/showthread.php?t=665704&highlight=second+video+card](http://ubuntuforums.org/showthread.php?t=665704&highlight=second+video+card)

Currently, everything gets upconverted to 1920x1080.  This is a good thing.  However, as long as my LCD screen is full and the video is playing at it's full resolution, I don't care too much.  Now, what I am trying to make happen is for when this one group of video files starts playing, that MythTV will resize the resolution to one that is supported by the CRT TV.  Or is there a way to switch resolutions easily system-wide?  Like a button on the remote would change from 1920x1080 to 800x600 (640x480) or something like that?  That would be the best solution actually.

If it isn't easy, I have a work around, but it isn't very cool.  I basically can't use MythTV and have to manually start playing the files.

you weren't exactly specific as to what type of files you need special resolutions for, the
player you are using, nor how the screens are physically connected... but IMO, the best
way to do this would be to run separate X sessions- one driving the lcd panels at the desired
resolution and second one that drives the crt tv at its desired resolution.

if you do that, then all you need to do is config your player to display using the X screen 
for the TV.

---

### Post by laga on 2008-04-22
AFAIK, it's not possible to run two X servers simultaneously on one Nvidia card. If that's not what the OP wants, then ignore me.

If you just want to change resolution on the fly, 'xrandr' might work. I don't know how that'll interact with your CRT TV and if it's going to work for you.. heck, I'm not even sure what you want to do :)

---

### Post by majoridiot on 2008-04-22
> **laga said:**
> AFAIK, it's not possible to run two X servers simultaneously on one Nvidia card. If that's not what the OP wants, then ignore me.

If you just want to change resolution on the fly, 'xrandr' might work. I don't know how that'll interact with your CRT TV and if it's going to work for you.. heck, I'm not even sure what you want to do :)

agreed on all counts. :)

more specific and detailed info is definitely required.

---

### Post by Caps18 on 2008-04-22
Sorry about that, I started writing it with one idea in mind, and then had a different idea about halfway though.

I am basically trying to avoid having to get a separate frontend computer to run mythTV at 640x480.  But, I would like it to scale all the TV shows I have in HD to run at 640x480.  It's not that I will watch them on it, but the menu is currently displayed at 1920x1080 on my HDTV and only the top corner shows up on the other TV.

I do not need to be able to watch both TVs at the same time.  If I am watching one, I'll be in that room and unable to watch the other TV.

[http://linux.about.com/od/linux101/l/blnewbie5_1.htm](http://linux.about.com/od/linux101/l/blnewbie5_1.htm)
>  <Ctrl><Alt><+>
(in X-windows) Change to the next X-server resolution (if you set up the X-server to more than one resolution). For multiple resolutions on my standard SVGA card/monitor, I have the following line in the file /etc/X11/XF86Config (the first resolution starts on default, the largest resolution determines the size of the "virtual screen"):
Modes "1024x768" "800x600" "640x480" "512x384" "480x300" "400x300" "1152x864"Z
Of course, first I had to configure the X server, either by using Xconfigurator, xf86config, or manually by edition the file /etc/X11/XF86Config, so that it supports the above resolutions (mostly the matter of uncommenting the line that defines my video chipset, and specifying the synchronization frequencies my monitor supports). XFdrake (Mandrake configuration utility) can do it from GUI. See also the commands xvidtune and xvidgen.

<Ctrl><Alt><->
(in X-windows) Change to the previous X-server resolution. 

I don't know if something like this works in Mythbuntu, but I've used this before in a different version of Linux.  And if I could map my remote control to send those keys, then it could increase the resolution or decrease it based on what TV I am using.  Then the video resolutions of individual files shouldn't matter as they would get resized to the max screen resolution.



To answer the questions, I have video files that range in resolution from 320x240 to 1920x1080.  The biggest I would want to play on the old 640x480 TV is 720x480.  It doesn't matter if it gets chopped off or resized to fit.
It is connected using the RCA dongle to yellow video cable, to a VCR/RF modulator to RG59 cable into the old 27" TV.  The 37" HDTV is connected by the DVI cable.  There is one 6200 nvidia graphics card.

Would running two X sessions be possible with two different MythTV frontends?  Or would it clone the screen for both X sessions so I would just need the main frontend?

Thanks for your help.

---

### Post by KillerKiwi on 2008-04-22
simplest way would be to hook up irexec (maybe to the power button) to execute a script to toggle modes and restart mythfrontend (so it can resize to the new resolution)

xrandr can do this fairly easily, does it work with nvidia binary yet? ... maybe nividia-settings can do the same thing...

---

