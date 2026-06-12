---
title: "Problem with video playback coloration on nv driver"
date: 2008-05-19
forum: Multimedia Software
---

### Post by devmage on 2008-05-19
I am having a video playback problem, and I don't know how to describe it in a technical sense.  All of my video files have a heavy blue-green tint to it, as if someone has taken the tint control on a television and set it to one extreme.  Even the Ubuntu test video, included in /home/user/Examples reproduces this.  I first confirmed that the situation occurs in a variety of players, namely Totem with FFmpeg, vanilla Totem, gxine, VLC, and Mplayer.  All other video is fine - my normal system windows are colored correctly, webpages render correctly, even Flash-based video on sites like Youtube renders in the proper color.

I have narrowed the issue down to something involving the nv plugin.  I find it strange that the system defaults to using this because I'm not using nv for X - I'm using nvidia.  Setting Mplayer or VLC to render through x11, gl, or gl2 yields the correct result (VLC crashes on gl though, so I was only able to test that on Mplayer).  So, I have a workaround, but I want a fix.

Furthermore, Nautilus' previews of my video files are rendered in the correct colors.  Whatever it is using is working properly.

What is going on here?

Relevant system specifications:
Ubuntu 8.04 i386 standard installation
Lenovo Thinkpad T61, Intel Core 2 Duo, enough RAM
NVidia Quadro NVS 140M video with proprietary driver (nvidia-glx-new) through the Ubuntu proprietary manager
Compiz Fusion enabled over Gnome
Medibuntu repositories enabled

I don't know what else I would need to include.  Below are screen captures.  Ideas?  Thanks in advance.

Incorrect output from Totem using FFmpeg (other "broken" players render similarly):
[[IMG]http://img520.imageshack.us/img520/9716/screenshotexperienceubuih6.th.png[/IMG]](http://img520.imageshack.us/my.php?image=screenshotexperienceubuih6.png)

Correct output from Gnome Mplayer after selecting x11 renderer:
[[IMG]http://img518.imageshack.us/img518/9833/screenshotexperienceubuev2.th.png[/IMG]](http://img518.imageshack.us/my.php?image=screenshotexperienceubuev2.png)

Correct output from VLC after selecting x11 renderer:
[[IMG]http://img144.imageshack.us/img144/9607/screenshotvlcmediaplayeyu9.th.png[/IMG]](http://img144.imageshack.us/my.php?image=screenshotvlcmediaplayeyu9.png)

Correct thumbnail rendering in Nautilus:
[[IMG]http://img136.imageshack.us/img136/5521/screenshotexamplesfilebvt7.th.png[/IMG]](http://img136.imageshack.us/my.php?image=screenshotexamplesfilebvt7.png)

---

### Post by cor2y on 2008-05-19
In totem (Applications->Sound & Video->Movie Player) go to Edit->preferences the Display tab and set the HUE setting either to the maximum or minimum setting (a the way to the left or all the way to the right) color should then be normal for all video playback regardless of media player used from then on.
The nvidia drivers have the hue settings reversed.

---

### Post by devmage on 2008-05-20
That's strange.  Thank you for the reply, it does alleviate the color issue.  I guess it's a documented thing, then.  So there's no hard and fast fix?  Just a workaround?

---

### Post by cor2y on 2008-05-20
Until either nvidia fixes it in the next driver update or the folks who do fixes for the kernel etc do theres only this workaround, not very likely since changing something like that would effect the other video chipsets like intel and ati etc.
It should be noted that the opensource nvidia drivers, intel drivers, via drivers and the open and closed ati drivers all have the correct hue settings so the burden is on nvidia to fix and so far they haven't.

---

### Post by kitsune ravo on 2008-05-20
Okay, I have this problem too. I tried what cor2y said (setting the HUE to maximum or minimum in totem), but whenever I play the video, the HUE goes back to the middle, and the color is still very very... blue? No matter what I do, the HUE won't change. Everything else (Contrast, ect.) will, but not HUE.

I've told VLC to play in X11, but it looks really, really bad on my PC. (Should I post a screen shot?)

I've been using Ubuntu for a few years now, and have never had a problem such as this. None of my other Hardy PC's have this problem.

Specs, if they will be helpful:

Dell Inspiron 530 with 2.0 GiB of memory
Ubuntu Hardy Heron i386 with NVIDIA diver enabled, but not using Compiz
Intel Pentium Duel CPU E2160 @ 1.80GHz
And all the latest updates.


I *think* I was doing fine until I installed Movie Player (Gstreamer)
from Add/Remove, because I wanted to know what it did. Then the problem started. I have since uninstalled, but to no help. Maybe it is unrelated.

Any help, workaround or otherwise, would be greatly appreciated. Should someone report this as a bug? Or will we just wait for nvidia to fix it?

---

### Post by cor2y on 2008-05-20
What media player did you use when adjusting the hue setting?
And how many versions of totem do you have installed?
For example is totem -gstreamer and totem-xine installed?
Sometimes if you have different versions attached to different file types the hue settings might reset themselves and require re-adjusting to fix example maybe dvd playback is set to use totem-xine while avi/mp4 videos open with totem-gstreamer, well you play the mp4 with gstreamer then play a dvd with totem-xine the hue setting is correct but when you next open a mp4 file, totem-gstreamer goes back to showing weird colors and has to be re-adjusted again.
Your best bet is to pick one version of totem media player and stick with it once the hue settings are set in totem settings from there you can use any other media player once its not totem example set the hue in totem but use vlc player or mplayer as your default media player, or stick with only one version of totem either totem-gstreamer or totem-xine.
Like i said this a nvidia thing having to do with their closed drivers you can pester them but so far they haven't shown any inclination about fixing it, its not a specific ubuntu issue different distros of linux are having the same hue problems with the ddrivers.

---

### Post by kitsune ravo on 2008-05-20
Well, like I said, I had totem -gstreamer installed, but uninstalled it before trying this.

And I am using Movie Player (Totem) to try and adjust HUE.

Here is what I'm trying, in detail. Maybe you'll see something I missed. I go to Applications->Sound & Video->Movie Player, then go to Edit->Prefere*n*ces then the Display tab, and then I change the HUE to the lowest (Or highest, I've tried both) setting. Then, seeing no "OK" to click, I click the *C*lose button. Then I go to my .Avi video, and try playing it. It is blue. I go look at the HUE. It is set to default, again. While playing the video, I change it, but nothing happens, so I close the video and restart. I open it, it is blue, and the HUE is back to the default setting, as if I never changed it.

Would disabling the driver help? I only need it for when I play games, and I could always re-enable it then...

Also, why did this not happen before Hardy Heron?

(BTW, I have tried changing the HUE in VLC. It says that the HUE changed, but the video is no different. I assumed it only works with totem. Don't know if that helps at all... I have also tried .ogg files, same thing going on.)

---

### Post by cor2y on 2008-05-20
That is the way changing the HUE setting should work.
Check which version of totem is assigned to AVI files right click on the avi file and select Properties go to the "Open With" tab and see which version of totem is assigned to example Movie Player (xine) means totem-xine is the default player and you will have to adjust the HUE setting in that player, Movie Player and Movie Player (gstreamer) means totem-gstreamer.

---

### Post by kitsune ravo on 2008-05-20
Well, it doesn't seem to matter what file I'm trying to open, it always says I'm using Xine. On all videos and on the menu, totem says it is "Movie Player using xine-lib version 1.1.11.1" Yet the hue always seems to go back after I close it...

Maybe my Dell Inspiron is just really dumb?

(I've even tried restarting the system, but it didn't work.)

If it works, I'll just disable the driver until nvidia fixes the darned thing.

---

### Post by cor2y on 2008-05-20
OK heres what i tried since i use totem-gstreamer only now.
```
sudo apt-get purge totem totem-gstreamer totem-xine;sudo apt-get install totem totem-xine
```See what your hue settings are like after that.

---

### Post by kitsune ravo on 2008-05-20
Well, after changing instal to install and toteml to totem, I tried what you said and it worked! YES! So... Add/Remove didn't really remove the other totem? What happened there? Oh well, whatever, it lest it works now! Thank you so much for going trough all that for me!

Now... To watch some movies where people aren't blue! :popcorn:

---

### Post by cor2y on 2008-05-20
Glad i could help and sorry about the type error. :)

---

