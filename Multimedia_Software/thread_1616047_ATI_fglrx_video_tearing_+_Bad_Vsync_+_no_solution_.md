---
title: "ATI fglrx video tearing + Bad Vsync + no solution anywhere"
date: 2010-11-07
forum: Multimedia Software
---

### Post by Niccola on 2010-11-07
Well guys,
Im with 2 computers with ubuntu 10.10 Mav. Meerkat; One is a ECS notebook and other is mine desktop both with ATI video card (notebook, ATI HD 2400 M72 chipset; Desktop. ATI HD 3870)

Well, I've been search in whole internet (believe, all of them) and none solution has worked in my case;

Things like modify xorg.conf with a lot of different arguments, or check and uncheck options in CompizManager and ATI Catalyst Control Center.

Im tire to search and to try solve this problem. So, I came here ask a solution. All the solution I've found is very old (like before 2009) and like ubuntu is updated every 6 month, some of this solutions dont work!

So guy, somebody help-me!!!

---

### Post by Niccola on 2010-11-08
anybody?

---

### Post by Niccola on 2010-11-08
upping...

---

### Post by xzero1 on 2010-11-09
Never tried it with maverick yet but try enabling vsync and using the gl driver.

mplayer -vo gl ...

or disable fglrx (this will also help flash etc.). You can always reenable it later.

---

### Post by efball3 on 2010-11-11
Have you seen this thread:  
[http://ubuntuforums.org/showthread.php?t=1390484](http://ubuntuforums.org/showthread.php?t=1390484)

I'm using an nvidia card, not ati, but I also had tried everything imaginable in ccsm and the nvidia driver settings, but still had tearing.

Running gnome-shell --replace fixed the tearing, but it isn't a very satisfactory solution.
I switched from compiz to mutter and that's a better solution.
I have "mutter --replace" in the startup applications.

---

### Post by AKADAP on 2010-11-12
I have found that video works much better with the open source drivers than with the ATI proprietary drivers. I have no tearing, and no dropped frames with the open source drivers.

The only way I was ever able to get good video with the ATI drivers was to use the OpenGL setting on MythTV and check the vsync option. But this seemed to break every other update of the ATI drivers.

---

### Post by Yellow Pasque on 2010-11-12
The open-source drivers are good if you have a high-end CPU for video decoding. Otherwise, HD video could be choppy

---

### Post by no2498 on 2010-11-13
this helps me it may or may not help you
it comes from the program cheese

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by georgito on 2010-11-16
Hi everybody,

I've been looking for the solution on the internet and almost none worked for me except changing the settings of "gstreamer-properties" (to "X Window System (No Xv)")
And I removed "v86d" package and changed line 9 of /etc/default/grub from this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"
to this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and deleted:
uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap
from /etc/initramfs-tools/modules
And finally typed:
sudo update-grub
sudo update-initramfs -u

This only applies for those who tried to play with plymouth...

Now I can watch 720p videos without any tearing on my dual screen.

Cheers

---

### Post by kFYatek on 2010-11-24
Hi everybody :)

I've been having a Dell Studio 1558 laptop with Mobility Radeon HD 5470 for like 2 weeks, and had the tearing problems we all with ATI cards are facing.

I tried many things, like enabling V-sync everywhere I possibly could, upgrading the drivers (I had to upgrade to Catalyst 10.11 anyway, because of some color issues) and disabling Compiz. I tried both SMPlayer and VLC (other players didn't meet my needs, since I need Advanced SSA subtitle rendering) with Xv and OpenGL (with various options) output modules - no luck.

Then I noted few facts:

[LIST]
[*]the tearing occurs mainly with SD (480) video; while playing HD videos (be it 720 or 1080), I had no tearing at all, or just a little barely noticeable bar at the top of the screen teared
[*]the tearing is usually much heavier on battery than on AC power - in fact, the reason for the difference is the PowerPlay setting, so I could test the worse case without unplugging my laptop
[*]the tearing seems somehow unrelated to V-sync - there are no typical tearing lines across the screen - the tearing area seemed to be quite irregular shape in the top portion of the screen
[*]while running Compiz, even glxgears are tearing - there is no tearing when running without Compiz, though (but the video tears anyway)
[*]the above-mentioned tearing stops when triggering Compiz's "desktop cube rotation", that is, while rotating
[/LIST]
I tried forcing Compiz to behave like when the desktop cube is rotating, with some limited success, but it proved impractical from a performance standpoint.

And then I ran the terminal-controlled MPlayer. The one without the GUI, that is. And went fullscreen with it. And guess what? No tearing! Then I started SMPlayer, copied all the options it passed to MPlayer, and ran it as that (save for options related to embedding the window)... and still no tearing! But SMPlayer still tears...

**Then I came to a conclusion:** for some reason, the tearing occurs only in windowed mode. "But hey", you may think, "you ran SMPlayer fullscreen, didn't you?" - yes, but SMPlayer's (and VLC's, Totem's, and many other players') fullscreen mode is not a real fullscreen. It's merely a window stretched to fit the entire screen. It's quite reasonable, because it allows for the use of that little GUI that shows up when you move the mouse, but it makes a difference for drivers somehow. The drivers need a real fullscreen to stop tearing.

And what can give you the real fullscreen is the console MPlayer. But its not very comfortable to use... The workaround is to **use SMPlayer**, but to **instruct it to run MPlayer in a separate window**.

**To do that:** run SMPlayer, go to Options -> Preferences -> Advanced, and check "Run MPlayer in its own window". And, if you haven't already done that, change video output module to some variant of "gl" - you will find the option under General -> Video in the Preferences window. That's it! The video will be in other window than the GUI elements, but it's much better than no GUI at all. The video may still tear while windowed, but you probably watch video fullscreen more often, and there's no tearing there! You may need to enable V-sync in Catalyst Control Center, too.

The main drawback is that there's absolutely no GUI while in fullscreen - so you must pause and seek using the keyboard, or go out of fullscreen to do that. But I think that's much better to have no tearing instead :)

I wish you luck with your struggle against tearing :) Hope it will work for you, too!

---

### Post by no2498 on 2010-11-25
georgito

glad i some what helped you
and you got it going

---

### Post by mellowtothemax on 2010-11-26
For me tearing has been fixed by the ATI 10.10 driver, both from the Ubuntu repository and from ATI website.  

As mentioned in another thread from someone else, you need to change the 3D->More Settings wait for vertical refresh slider to 'always on' in the CCC.

This fixes tearing completely.

Unfortunately every time you log out or restart you need to disable and re-enable the setting again, it doesn't seem to keep the change.

However with ATI 10.11 this has been broken again.  So I have reverted back to 10.10.

I am using Ubuntu 10.10 64-bit mobility radeon 4670

---

### Post by jonyibandi on 2011-01-22
I have noticed something too. If I enable the snow plugin in the ccsm, there is no tearing... But this plugin needs more cpu resources...

---

### Post by sk8tyfoo on 2011-02-09
Has anyone figured out how to get dual monitors working on ubuntu 10.10 with a radeon x.... series?

---

### Post by t-dome on 2011-11-05
Vsync works when you disable desktop effects.
I've disabled them only for fullscreen windows (in KDE, System Settings -> Advanced -> Suspend desktop effects for fullscreen windows).

Using Kubuntu 11.10 x64, open source Nouveau driver, smplayer and the "xv" video output.

---

