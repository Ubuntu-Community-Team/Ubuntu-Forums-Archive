---
title: "SiS DRI driver expected DDX version 0-0.8.x but got version 0.7.0"
date: 2005-11-27
forum: Multimedia &amp; Video
---

### Post by prokher on 2005-11-27
I read [www.winischhofer.at](www.winischhofer.at) site, but i have no found the solution of my problem. Actually, everything working except 3d acceleration. Xorg.log said that direct rendering enabled, but glxinfo said direct rendering: no. 

then i try: 
export LIBGL_DEBUG=verbose 
glxinfo 

and get 

libGL: XF86DRIGetClientDriverName: 0.7.0 sis (screen 0) 
libGL: OpenDriver: trying /usr/lib/dri/sis_dri.so 
drmOpenByBusid: Searching for BusID pci:0000:01:00.0 
drmOpenDevice: node name is /dev/dri/card0 
drmOpenDevice: open result is 4, (OK) 
drmOpenByBusid: drmOpenMinor returns 4 
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0 
libGL error: 
SiS DRI driver expected DDX version 0-0.8.x but got version 0.7.0 
libGL warning: 3D driver returned no fbconfigs. 
libGL error: InitDriver failed 
libGL error: reverting to (slow) indirect rendering 
display: :0 screen: 0 
direct rendering: No 

and actually, i don't know what to do... 
any suggestions ?

---

### Post by prokher on 2005-11-28
I figured out that the problem is some kind incompatibility between new libgl1-mesa and sis_dri system. I have to install old xlibmesa3 from hoary packages. Actually i just overwrite libGL, libGLU and sis_dri.so (i have to get it from [http://www.winischhofer.net/](http://www.winischhofer.net/) cause of "black screen problem"). Ok. Wow!. Glxinfo says direct rendering yes. Glxgears shows me 300 fps! But now i have strange garbage onthe screen on my gl screensavers, and ppracer (tuxracer) shows me onle blue screen, but playing music at the same time. 
Suggestions?

---

### Post by Tomasz on 2005-12-10
Actually I have the same exact problem with my SiS630 laptop. I'm not sure if overwriting libs is a good idea. There's virtually nothing about this problem on the web. I don't think anyone will fix it for us and I'm not experienced enough to know how to fix it myself. DRI worked fine in Hoary, but now this stupid incompatibility in Breezy... I've been tweaking my xorg.conf a bit, maybe someone will make use of this part (note: this doesn't make DRI work by any means, it's a setup for a laptop with a PAL TV-Out):
```

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
        Option "DRI" "on"
        Option "MaxXFBMem" "12288"
        Option "AGPSize" "64"
        Option "EnableSiSCtrl" "yes"
        Option "ScaleLCD" "yes"
        Option "TVStandard" "PAL"
        Option "CHTVSuperOverscan" "yes"

```

---

### Post by widjajayd on 2005-12-10
[QUOTE=prokher]I figured out that the problem is some kind incompatibility between new libgl1-mesa and sis_dri system. I have to install old xlibmesa3 from hoary packages. Actually i just overwrite libGL, libGLU and sis_dri.so (i have to get it from [http://www.winischhofer.net/](http://www.winischhofer.net/) cause of "black screen problem"). Ok. Wow!. Glxinfo says direct rendering yes. Glxgears shows me 300 fps! But now i have strange garbage onthe screen on my gl screensavers, and ppracer (tuxracer) shows me onle blue screen, but playing music at the same time. 
Suggestions?[/QUOTE]

Can you give me some detail steps that you did to make it work.
I have tried almost ALL Option in [www.winisschhofer.net/sisdri.shmtl](www.winisschhofer.net/sisdri.shmtl) but no luck, my glxgears show 120 fps,

Thanks before.

---

### Post by prokher on 2005-12-19
>Can you give me some detail steps that you did to make it work.
Actually, it was easy. I just place libGL & sis_dri from xlibmesa-dri_6.8.2-10.1_i386.deb, xlibmesa-gl_6.8.2-10.1_i386.deb (from hoary packages) into my /lib/X11... tree... and run ldconfig. It was working. But now, after a week or two i have black screen again, and pached sis_dri from [www.winischhofer.net](www.winischhofer.net) can't help me. I don't know why, may be due to last updates...

---

### Post by hutopcat on 2006-01-21
hi all!
I found a solution for myself:
I added temporarily the dapper main repository to my sources.list and installed the new x.org and its drivers, and some other dependencies.
Then I had to remove Loadmodule glcore from xorg.conf.
Now the dri works fine.

---

### Post by steveneddy on 2006-04-24
Maybe someone can help me with my SiS video card prob. [Here]("http://www.ubuntuforums.org/showthread.php?t=165222&highlight=fbconfigs") is a link to my post about almost the same problem.

[http://www.ubuntuforums.org/showthread.php?t=165222&highlight=fbconfigs](http://www.ubuntuforums.org/showthread.php?t=165222&highlight=fbconfigs)

Any help would be appreciated. 

BTW, looking at some of the above posts, sis I put the wrong PCI address in the xorg.config file?

I'm dumbfounded. ](*,)

---

