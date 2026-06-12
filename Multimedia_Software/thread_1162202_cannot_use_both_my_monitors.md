---
title: "cannot use both my monitors"
date: 2009-05-17
forum: Multimedia Software
---

### Post by GSZX1337 on 2009-05-17
I am attempting to use both of my monitors simultaneously in Ubuntu 8.10 (first monitor is 1680x1050 the second is 1440x900). I can use either of my monitors if it's the only one connected to my video card (GeForce 7900GT).

When I have both monitors connected simultaneously, video is shown on both monitors at the BIOS and when Ubuntu is loading, but as soon as the log in screen appears, my first monitor no longer displays video. I have disabled the "Mirror Screens" option and hit "detect displays" but no dice, I can't get video coming out of my first monitor.

I have these monitors working in Windows Vista and the BIOS, so I know nothing's wrong with these monitors. As I find out more, I'll be sure to include in this post.

Thanks in advance to anyone who helps me.

---

### Post by RichardG891 on 2009-05-17
Are you accessing the monitor set-up through gnome's own "display" utility, or nvidia's? I use dual screens with nVidia graphics (on a laptop so its slightly different from a hardware point-of-view).

---

### Post by SuperSonic4 on 2009-05-17
How did you get them both to come on in BIOS and boot up? Only my DVI monitor does for me on the 8500GT

I would highly suggest using nvidia-settings to do this. If it is not installed run ```
sudo apt-get install nvidia-settings
```

Next backup xorg.conf in case something goes wrong and we need to restore the old X ```
sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Next load nvidia-settings as root: ```
gksu nvidia-settings
```
In there do whatever you need to do (I find Twinview gives me independent views and the ability to drag and drop files and programs while giving the proper resolution and fullscreen in both) and click save and confirm.

Lastly reset X and it should work in both screens.

If X does not load then restore your backup by  ```
sudo mv -v /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

```
sudo /etc/init.d/gdm restart
```

---

### Post by GSZX1337 on 2009-05-18
Thanks to both of you. (especially SuperSonic4)

[QUOTE=SuperSonic4""]In there do whatever you need to do (I find Twinview gives me independent views and the ability to drag and drop files and programs while giving the proper resolution and fullscreen in both) and click save and confirm.
[/QUOTE]
I tried Twinview, but I cannot get YouTube videos to fullscreen properly (video stays the same size and the rest of the screen turns black) so I try to have the monitor as a seperate X Screen. Whenever I try to set it up that way, I get this [result]("http://i14.photobucket.com/albums/a328/GSZX/Screenshot.png").

For some reason, my first monitor is seen as the second monitor, and even though the resolution is set at 1680x1050, I only get 1440x900 and the rest is black, as shown in the image I linked.

---

### Post by GSZX1337 on 2009-05-19
bumpy

---

### Post by SuperSonic4 on 2009-05-19
> **GSZX1337 said:**
> Thanks to both of you. (especially SuperSonic4)


I tried Twinview, but I cannot get YouTube videos to fullscreen properly (video stays the same size and the rest of the screen turns black) so I try to have the monitor as a seperate X Screen. Whenever I try to set it up that way, I get this [result]("http://i14.photobucket.com/albums/a328/GSZX/Screenshot.png").

For some reason, my first monitor is seen as the second monitor, and even though the resolution is set at 1680x1050, I only get 1440x900 and the rest is black, as shown in the image I linked.

That's flash being stupidly annoying - mine is the same with TwinView and youtube. All my local and streamed files play OK in fullscreen (as far as resolution allows anyway) and apps work on both so I think it's just youtube and flash.

You can play youtube videos in VLC though- if you go to open network and paste in the URL

---

