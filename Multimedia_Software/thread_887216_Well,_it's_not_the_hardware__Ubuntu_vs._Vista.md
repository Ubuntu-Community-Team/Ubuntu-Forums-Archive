---
title: "Well, it's not the hardware:  Ubuntu vs. Vista"
date: 2008-08-11
forum: Multimedia Software
---

### Post by Xamiga on 2008-08-11
Toshiba A215, 2gig, ATI Radon1200, ViewSonic VX1940w. 
ATI drivers installed.  ATICatalyst settings: tried all different combos. 
 

Ubuntu:

GNOME Mplayer or VLC:
  Attemp to play DVD.  Audio slightly chopped.  Video absolutely horrible, dropped frames, jagged edges ( no matter how I set VLC).
GNOME Mplayer video set to OpenGL best choice.
CPU usage ~ 32%.  Memory useage - 278Mb. no swap.


Vista Home Premium:

  Absolutely flawless audio and video.
  Many more processes running.
  CPU usage ~ 38%. Memory usage - 990Mb. 100k swap.

With all the brain power and programming experience that must be availiable in the 'nix community, why do I have to boot WINDOWS to watch a DVD :confused: :confused: :confused:

---

### Post by damis648 on 2008-08-11
I find it quite interesting that your CPU is at 32%, even in Ubuntu and idle. It would probably your hard drive using more CPU power, but I would seriously consider looking into that, if the CPU is idle. Anyway, try Totem for Playing the DVD. Applications>Audio & Video>Movie Player, and make sure to install the CSS libraries. Install the package libdvdcss from Synaptic. That might do it, but I would look into that CPU usage.

---

### Post by Xamiga on 2008-08-11
> **damis648 said:**
> I find it quite interesting that your CPU is at 32%, even in Ubuntu and idle. It would probably your hard drive using more CPU power, but I would seriously consider looking into that, if the CPU is idle. Anyway, try Totem for Playing the DVD. Applications>Audio & Video>Movie Player, and make sure to install the CSS libraries. Install the package libdvdcss from Synaptic. That might do it, but I would look into that CPU usage.


I tried Totem first,  not as good as GNOME Mplayer, slightly better than VLC.  
The 32%CPU is while playing the video. 
Ubuntu idle ~7%.  
Idle under Vista = 9%.

---

### Post by elasto1mania on 2008-08-16
Don't measure cpu usage with system monitor.
better use command top in terminal.

maybe try [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Xamiga on 2008-08-16
> **elasto1mania said:**
> Don't measure cpu usage with system monitor.
better use command top in terminal.

maybe try [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

Thanks, tried that thread exaustively before I posted here.
The problem is not the hardware, and (i think) not the application software.
The problem is OS, driver or X related.

---

### Post by shirilover on 2008-08-16
Are you using compiz/desktop effects?
Compiz and video overlay do not play well together.
Disable compiz/desktop effects and try playing your video again.

---

### Post by Xamiga on 2008-08-16
> **shirilover said:**
> Are you using compiz/desktop effects?
Compiz and video overlay do not play well together.
Disable compiz/desktop effects and try playing your video again.

Thanks,

Was not using desktop effects, removed compiz.  Same results.

---

### Post by eye208 on 2008-08-16
> **Xamiga said:**
> jagged edges
Software rendering. XVideo not available.

> With all the brain power and programming experience that must be availiable in the 'nix community, why do I have to boot WINDOWS to watch a DVD :confused: :confused: :confused:
Because all the brain power at ATI is focused on Windows.

Run "xvinfo" in a terminal to find out if XVideo is enabled. The last time I used the ATI drivers, they came with XVideo disabled by default. To enable it, run this command:
```
sudo aticonfig --ovt Xv
```
The new setting will be stored in the X.org configuration file. Restart your system to apply it. Reset VLC/MPlayer to use XVideo instead of OpenGL. The jagged edges should be gone, and CPU load should be reduced.

If audio is still choppy, consider [purging PulseAudio](http://ubuntuforums.org/showthread.php?t=885437).

---

