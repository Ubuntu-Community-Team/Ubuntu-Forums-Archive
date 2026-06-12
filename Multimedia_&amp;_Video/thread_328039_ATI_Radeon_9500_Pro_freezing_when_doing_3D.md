---
title: "ATI Radeon 9500 Pro freezing when doing 3D"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by greygoo on 2006-12-30
Hi Folks,

i'm new to ubuntu and everything works great, exept my ATI radeon 9500 Pro.
When using 3D (even some screensavers) crash after a while.

When I start Enemy Territory the game freezes afer only 2 or 3 seconds in the intro, 
sound keeps looping.  (this can be reproduces and time to freeze varies from 1-4 secs)
Machine lives since I receive pings from it then.

I once had a Fedora Core 2 or 4 running with EnemyT quite a while ago, when FC2/FC4 was up to date. It worked. And it works using WinXP.

I installed the driver following this HowTo: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hardware 3D seems to be used, since framerates are OK in glxgears and fgl_glxgears reports about 500 fps. (I'll now try how long it can run in fullscreen).  Ill report this 


Ubuntu: Edgy, 2.6.17-10-generic
Driver : 8.32.5 Proprietary from ATIs Website (not the first I've tested so far. 8.28.x same problem)

fglrxinfo says:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Generic
OpenGL version string: 2.0.6234 (8.32.5)

I tried various settings in xorg.conf. All without success. 
And yes, Composite is disabled in xorg.conf ;) 

I tried a lot of searches on the net and found many problems, which all were left unsolved with ATI Cards.

Hard to believe the driver is that bad. 
Any idea what to check or change ?
:confused: :mad: 
Thanks,
greygoo


System:
Board: AsRock P4VT8 (VIA chipset)
CPU:  Intel P4, 2.66 GHz
RAM: 2x512MB
Video: Powercolor, ATI RADEON 9500 Pro
HDD: quite a bunch of

---

### Post by greygoo on 2006-12-31
OK, it seems i can run ET in 800x600, but screensavers (3d) still lead to a crash.
Busy Shperes (screensaver) crashes the system after a few seconds.
:-k  It's not that I need to run those screensavers, it just indicates there is still a problem.

Running flg_glxgears and glxgears seems not to cause any problem.

Is there anyone with Ubuntu Edgy, 2.6.17-10-generic and ATI Radeon drivers who can run Busy Spheres without problems
If so, please let me know which ATI Drivers and if there are some special settings to configure.

Thnx,...

---

### Post by nantetokuma on 2007-01-22
I've similar problem. I'm on Dapper :
```
Linux ubuntu-PC 2.6.15-27-686 #1 SMP PREEMPT Fri Dec 8 18:00:07 UTC 2006 i686 GNU/Linux
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

```
For me it's under **UT tournement** and **Google Earth**

with **UT tournement** it depends, sometime computer freeze after few seconds and sometime it doesn't and I can play hours... When it freeze, it's doing the same as you, sound is looping...

with **Google Earth** it's usually after one minute... Working fine then computer freeze and I have to restart it. I've try to redirect Error output to a file but there's no error from GE. Only Freezing, no answer from keybord and from mouse...
```
googleearth 2>Desktop/GoogleError
.../...
308.208526: Texture TILE took 8.307ms to create.
308.355723: Texture TILE took 11.487ms to create.
308.866894: Texture TILE took 10.658ms to create.
308.889450: Texture TILE took 9.223ms to create.
.../...
```

Don't know how to find more informations about this problem. Thanks for ideas about that!

Dawidbass
Happy with Ubuntu:D

---

### Post by Mouloud on 2007-02-03
Exactly the same problem with me. Running enemy territory (or tremulous)for a few minutes, and then the sounds loops, the screen doesn't receive signal anymore. ctrl+Alt+f1 doesn't work, the only possibility is to hard reboot the computer. Very frustrating.

edit:
running fresh installed edgy on a athlon 2000+ CPU with original kernel (no changes at al)
/edit
I installed the fglrx drivers, without following any how to. Just changing "ati" to "fglrx" in xorg.conf and adding :

```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```

fglrxinfo displays:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

I'll have to add that the card is a little special. It's from constructor "his" and it's a overclocked memory version of the standard 9600XT. (HIS Excalibur 9600XT **turbo**)

The opensource "ati" version of the driver worked pretty good in the beginning, but slower, whereas switching from "ati" to "fglrx" dropped my glxgears fps from ~2900 to ~250. I don't see any logic in it.

That's all if someone has a solution please post it here. If I have one, I'll post it here also.

And forgive my english

---

