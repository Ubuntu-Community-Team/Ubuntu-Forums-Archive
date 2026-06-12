---
title: "[Hardy] X11 in totem (gstreamer-properties)"
date: 2008-05-06
forum: Multimedia Software
---

### Post by diafygi on 2008-05-06
I asked this question over at [launchpad]("https://answers.launchpad.net/ubuntu/+question/29238"), but no one responded.

When compiz fusion is enabled, video playback in Totem will disappear to a black background when dragging the window or rotating the desktop cube. This is a [common problem]("http://ubuntuforums.org/showthread.php?t=432085") previous releases (although the background was blue), and it was fixed by enabling x11 in gstreamer-properties. However, in Hardy Heron, there is no option for X11 specifically. I can choose:
-Autodetect
-X Windows System (no Xv)
-X Windows System (X11/XShm/Xv)
-Custom

When I choose X11/XShm/Xv, video playback uses Xv and disappears when the window is dragged. In Gutsy and Feisty, I could specifically select X11 as the default output plugin for video. The only way I can fix it in Hardy is using the "no Xv" option, which makes the video jumpy and slow. X11 would be ideal.

My question: How can I enable the x11 plugin in gstreamer-properties? What custom pipeline command can I use to enable it?

---

### Post by cor2y on 2008-05-06
Make sure gstreamer0.10-x is installed if its not
If you select custom autovideosink should be the default that is used.
Remember to select X11 output for gmplayer if it does work.

---

### Post by diafygi on 2008-05-06
> **cor2y said:**
> Make sure gstreamer0.10-x is installed if its not
If you select custom autovideosink should be the default that is used.
Remember to select X11 output for gmplayer if it does work.

Right, I do have gstreamer0.10-x installed. When I the video output to Autodetect, the custom command is autovideosink. When I set the video output to X11/XShm/Xv, the custom command is xvimagesink. This command defaults to Xv, not X11. I would like to modify that command to use X11, not Xv. Anyone know how to modify it?

You can do it in Gnome Mplayer and VLC.

---

### Post by Tom--d on 2008-05-07
To check.. 

when you click test.. and a window opens (colours and the black and white fuzzyness) just do a cube or some kind of rotation and then you will see if it does it :)

---

### Post by diafygi on 2008-05-09
> **Tom--d said:**
> To check.. 

when you click test.. and a window opens (colours and the black and white fuzzyness) just do a cube or some kind of rotation and then you will see if it does it :)

Yes, when I click test, the bars and snow appear. When I rotate the cube or move the window, the bars and snow do not move with the window or cube. This means Xv is being used, not X11. What is the custom command to force X11 in gstreamer?

---

### Post by akaihola on 2008-09-12
I need to disable Xv for GStreamer, too, so using Totem on a rotated Intel display won't crash the system.

See these bugs:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/219846/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/219846/)
[https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/225400/](https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/225400/)

---

### Post by eye208 on 2008-09-12
> **diafygi said:**
> In Gutsy and Feisty, I could specifically select X11 as the default output plugin for video. The only way I can fix it in Hardy is using the "no Xv" option, which makes the video jumpy and slow. X11 would be ideal.
[list][*]The set of options in gstreamer-properties were the same for Gutsy and Hardy. There was no "X11" option. "No Xv" _is_ X11. (You are probably confusing this with VLC's properties, where you can choose between Xv, OpenGL and X11. Ubuntu's gstreamer doesn't have the OpenGL option.)
[*]X11 is pure software rendering (with pixelation and all). It doesn't get any slower than that.
[*]If X11 playback in Gutsy was less jumpy, that may be due to other changes in Hardy (different kernel scheduler etc.).
[*]If you care about video playback quality, there's no other option than Xv.[/list]

---

### Post by cor2y on 2008-09-12
> **akaihola said:**
> I need to disable Xv for GStreamer, too, so using Totem on a rotated Intel display won't crash the system.

See these bugs:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/219846/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/219846/)
[https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/225400/](https://bugs.launchpad.net/debian/+source/xserver-xorg-video-intel/+bug/225400/)

To use software only acceleration aka X11 instead of XV.
Simply got to System->Preferences->Multimedia Systems Selector
Then select the Video Tab.
In Default Output Switch Plugin from Autodetect to X Window System (no XV) 
Then test to see if it works by using the Test button.
If it does then X11 is now the default for the system.
If you use a media player like mplayer instead of totem be sure to set its video driver output to X11 as well in the preferences.

---

