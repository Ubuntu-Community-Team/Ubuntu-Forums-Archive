---
title: "compositing = nVidia tearing, very annoyed"
date: 2012-06-08
forum: Multimedia Software
---

### Post by dave.kts on 2012-06-08
I've tried several fixes for this, tried this, tried that but it seems to be unfixable on my system. 
If compositing is turned on, I get tearing with videos, games, and fullscreen apps like google earth.. doesnt matter which environment, unity, gnome, fallback, xfce, xubuntu.. can't even begin to play games in Gnomeshell or whatever its called, bugs out on me. Only thing that works is to log into XBMC if I want to watch a movie without tearing. problem is that XBMC likes to lock up on me once in awhile.
I also tried Mutter as a window manager, and it solved the tearing issue, but was terribly unstable and useless for me.

should I try different drivers for nVidia? 173.14.30 in use now, I think i tried others in the past with same results. I dont want to break the video.
Im also gonna ditch my 11.10 install and try 12.04 sometime, so if starting from scratch will have better results, let me know

pulling all my hair out here someone save me!

1.10 64 bit Ubuntu
intel dp43gag board, no video onboard
Q8300 core2 quad
nVidia PNY quaddro fx 550
yada, yada

---

### Post by dave.kts on 2012-06-13
bump?

I really just want the desktop expo, maybe window translucence.
Seems compositing doesnt work at all, except for the window shadows from gnome.

---

### Post by cuyo01 on 2012-06-14
I was using 11.10, i that in my machine phenom II 555 and video 240GT cant solve the tearing problem no matter what until tried something apparently unrelated; I disabled cool 'n quiet in bios and then no more tearing.

I have installed other DE's and upgraded to 12.04, in kubuntu videos show tearing in smplayer, to remove that changed the video output in options to "xv 0-NV17 Video Texture" and then no more tearing

---

### Post by Roasted on 2012-06-14
Are you guys using dual monitors? I was told that with my dual monitor setup (twinview) on Nvidia, my tearing is coming from the fact that my two monitors don't have 100% equal refresh rates. AKA, if I had two identical monitors, I'd have no tearing, but me having a Dell 24" and an eMachines 19", there's undoubtedly going to be a tiny enough difference to cause the issue.

I can't say this for an absolute fact or not, but that's what I was told. I figured I'd be upgrading soon enough to a pair of identical (but larger) monitors so I kind of stopped researching it there.

---

### Post by dave.kts on 2012-06-14
Nope, no dual monitors. samsung T220HD 1600 by 1050, 59.95hz detected by nvidia x server.
Tried different video output modes in VLC player, no change. Tried all kinds of vsynch suggestions. It's something to do with the window manager. Mutter replace fixed it, but desktop would crash and windows would hang. XBMC has no tearing, but will randomly lock up

---

### Post by ontaiwolf on 2012-06-15
Same problem here. There are some settings which can help a little but some tearing is still there.

**Drivers**
Downgrade your drivers to 290.10: [https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2)
Tearing comes only with 295.xx

**Compiz-Settings-Manager**
OpenGL: Activate VSync
Composite: Deactivate "Detect refresh rate", set refresh rate to 60, 120 or 180 manually. 180 works best for me.
(Optional) Workarounds: Activate "Force synchronisation between X and GLX"

**xorg.conf**
Add under Device: Option "TripleBuffer" "1"

You also can play a little with Nvidia settings...

---

### Post by Jose Catre-Vandis on 2012-06-15
For Xubuntu, add this script to a launcher (assuming you are not trying to use compiz)

```
#!/bin/sh
#componoff.sh
#xubuntu 11.10,12.04
#turns compositor on and off

comp=$(xfconf-query --channel=xfwm4 --property=/general/use_compositing)

if [ $comp = &#8220;true&#8221; ]; then
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=false
else
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=true
fi
```

---

### Post by drawkcab on 2012-06-15
Also make sure your video driver settings are set to vsync as well and that the referesh rate is the same as your monitor.  It also helps to set your settings to center rather than stretch.

---

### Post by firekage on 2012-06-16
> **ontaiwolf said:**
> Same problem here. There are some settings which can help a little but some tearing is still there.

**Drivers**
Downgrade your drivers to 290.10: [https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2)
Tearing comes only with 295.xx

**Compiz-Settings-Manager**
OpenGL: Activate VSync
Composite: Deactivate "Detect refresh rate", set refresh rate to 60, 120 or 180 manually. 180 works best for me.
(Optional) Workarounds: Activate "Force synchronisation between X and GLX"

**xorg.conf**
Add under Device: Option "TripleBuffer" "1"

You also can play a little with Nvidia settings...

Could you tell me how to install this drivers from link above? I don't understand it. How to install this PPA, there is only amd64 downloadable items.

---

### Post by ontaiwolf on 2012-06-16
To difficult to change the url? This is not a ppa, it's just an archive with older packages.

i386: [https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu2)
amd64: [https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2)

Under "Downloadable files" you can find the direct links, uninstall nvidia-current from repository first, then download the package from the archive and install it. You probably have to freeze the package in Synaptics, so that it cannot be updated.

---

### Post by firekage on 2012-06-16
> **ontaiwolf said:**
> [B]To difficult to change the url?

No, just i didn't see where to change, and how to use this site in order to download or install something from it.

> 
[/B] This is not a ppa, it's just an archive with older packages.

i386: [https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu2)
amd64: [https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2)

Under "Downloadable files" you can find the direct links, uninstall nvidia-current from repository first, then download the package from the archive and install it. You probably have to freeze the package in Synaptics, so that it cannot be updated.

Thank you.:p

---

### Post by ontaiwolf on 2012-06-18
Update: Driver 302 is also tearing free. You can find it in the X-Swat PPA...

---

### Post by Cavsfan on 2012-06-18
Here is how to install the absolute latest drivers from nVidia:

[http://ubuntuforums.org/showthread.php?t=1948062](http://ubuntuforums.org/showthread.php?t=1948062)

I haven't tried it on Precise but others have. I am getting ready to as I just backed up my system with fsarchiver.

There is also a ppa you can add to get the latest stable nVidia driver:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by Cavsfan on 2012-06-18
I just installed the xswat ppa and updated the driver. Rebooting and will let you know how it works.

---

### Post by Cavsfan on 2012-06-18
I am now using 295.49 and it appears to work well. Checked out a youtube video and it was OK.
Everything else looks good.

---

### Post by Cavsfan on 2012-06-18
> **ontaiwolf said:**
> Update: Driver 302 is also tearing free. You can find it in the X-Swat PPA...

While the xswat ppa insalled a file called nvidia current 302.17-0ubuntu1~precise~xup1,
which appears to be driver version 302.17.
It is 295.49 actually and I have no problems with it. The latest driver according to nVidia is 295.59.

---

### Post by ontaiwolf on 2012-06-18
> **Cavsfan said:**
> While the xswat ppa insalled a file called nvidia current 302.17-0ubuntu1~precise~xup1,
which appears to be driver version 302.17.
It is 295.49 actually and I have no problems with it. The latest driver according to nVidia is 295.59.

No, it's 302. You can see the version of the driver in the Nvidia settings.

---

### Post by Cavsfan on 2012-06-18
> **ontaiwolf said:**
> No, it's 302. You can see the version of the driver in the Nvidia settings.


[IMG]http://ubuntuforums.org/picture.php?albumid=1580&pictureid=8441[/IMG]

---

### Post by Cavsfan on 2012-06-19
> **Cavsfan said:**
> Here is how to install the absolute latest drivers from nVidia:

[http://ubuntuforums.org/showthread.php?t=1948062](http://ubuntuforums.org/showthread.php?t=1948062)

I haven't tried it on Precise but others have. I am getting ready to as I just backed up my system with fsarchiver.

There is also a ppa you can add to get the latest stable nVidia driver:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

Not sure I should have updated the driver in 12.04. Youtube works fine but, facebook videos do not work at all.
I may try to restore my system and see it that fixes it.

---

### Post by Cavsfan on 2012-06-19
Formated the partition Precise was on and restored it from a backup and I still have driver version 295.49 :confused:

Not sure what to make of that. The xswat ppa and all of that is gone.

---

### Post by Cavsfan on 2012-06-19
If you want, you could try installing the latest nVidia driver 295.59 which came out on 2012.6.11.

[[COLOR=blue]_Install the latest nVidia driver in Precise Pangolin 12.04_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2006716")

I just did it and it works fine. Youtube videos work great.
Facebook videos don't work but, they haven't worked on any driver I have seen yet.

---

### Post by ScottDeagan on 2012-07-09
I have Ubuntu 12.04 running in dual monitor mode (TwinView). While it "works", there is a very annoying slow tear on the second monitor (a Sony 42 inch TV) that moves from top to bottom. I have a GTX 460. I will try the 290.10 drivers and report back here.

---

### Post by dave.kts on 2012-07-10
yeah I ditched Ubuntu and unity for SolusOS- a debian squeeze/Gnome2 derivative. 295.59 installed and still tearing, and i get some apps like stellarium or OpenArena that run in slow motion (0-1.5 FPS reported) as soon as compiz is enabled. Ive had this problem for years now thru several ubuntu's. I'm just going to smash my computer one of these days.

---

### Post by ontaiwolf on 2012-07-10
> **ontaiwolf said:**
> Same problem here. There are some settings which can help a little but some tearing is still there.

**Drivers**
Downgrade your drivers to 290.10: [https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2)
Tearing comes only with 295.xx

**Compiz-Settings-Manager**
OpenGL: Activate VSync
Composite: Deactivate "Detect refresh rate", set refresh rate to 60, 120 or 180 manually. 180 works best for me.
(Optional) Workarounds: Activate "Force synchronisation between X and GLX"

**xorg.conf**
Add under Device: Option "TripleBuffer" "1"

You also can play a little with Nvidia settings...

Update to this...

**Drivers**
Downgrade your drivers to 290.10: [https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2) or upgrade them to 302.17 or newer.
Tearing comes only with 295.xx

**Compiz-Settings-Manager**
OpenGL: Activate VSync
Composite: Deactivate "Detect refresh rate", set refresh rate to 60 manually.
Workarounds: Activate "Force synchronisation between X and GLX", "Force fullscreen redraws (buffer swap) on repaint" and "Force complete redraw on initial damage" 

**xorg.conf**
Add under Device: Option "TripleBuffer" "1"

With this settings I get the best experience.

---

