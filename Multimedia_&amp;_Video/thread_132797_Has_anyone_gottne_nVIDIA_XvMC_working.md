---
title: "Has anyone gottne nVIDIA XvMC working?"
date: 2006-02-19
forum: Multimedia &amp; Video
---

### Post by mossholderm on 2006-02-19
Has anyone had any success getting nVidia XvMC support working under Breezy?

I see a lot of people asking about it, but one one posting a solution. I've gotten some of it worked out, but it still doesn't work for me...

1) create /etc/X11/XvMCConfig
     This needs to have the name of your vendor XvMC library in it 
     (e.g. libXvMCNVIDIA.so.1 )

2) Work around X.org bugs by creating a link for libXvMC.so1.0
     ln -s /usr/lib/libXvMC.so.1 /usr/lib/libXvMC.so1.0

3) Watch X crash whenever I run an XvMC enabled app :cry: 


Has anyone made it past hurdle 3?

   --Matt

---

### Post by brt on 2006-11-12
No, not really 

when doing the above with Driver Version 8762 on self compiled 2.6.16.20 Kernel (dappers config) on dapper and starting Xorg via xinit (just running mythtvfrontend which is set to use XvMC) i get "jerky" live tv and problems with remaining OSD-artefacts when watching recorded shows.

but according to Xorg.0.log XVMC is also available _without_ modifications (no /etc/X11/XvMCConfig, no /usr/lib/libXvMC.so1.0):
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation

is this the "Xorg XvMC?" does "nVidia XvMC" anything better in "theory"?

---

### Post by brundles on 2006-12-07
I haven't looked at it yet but in digging around for XvMC stuff ready to try it on my Dapper install, I found [this link specific to Dapper and XvMC](http://ubuntu-mythtv.blogspot.com/2006/03/dapper-xvmc.html).

---

### Post by snake98 on 2006-12-07
I'm trying to get XvMC working on Edgy, I've installed 
sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg

I've check and the correct drivers are listed as nvidia, but I still can't get mythtv to verify it's working.  I recompiled mythtv with xvmc support, i'm going to try to get mplayer working to see if it's a ubuntu problem or a mythtv problem.

---

### Post by superm1 on 2006-12-08
The version in universe includes XvMC support.  No need for compilation.

You just need to set the type of card you have in /etc/X11/XvMCConfig

```
supermario@supermario:~$ cat /etc/X11/XvMCConfig 
libXvMCNVIDIA_dynamic.so.1
```

---

### Post by brundles on 2006-12-10
> **snake98 said:**
> I've check and the correct drivers are listed as nvidia, but I still can't get mythtv to verify it's working.  I recompiled mythtv with xvmc support, i'm going to try to get mplayer working to see if it's a ubuntu problem or a mythtv problem.

I've found DVD playback via Xine is easier to test with than mpegs with mplayer - also giving a much more noticeable improvement (30% usage down to 17% ish on my system).

On another point, I believe the newer Nvidia cards include offboard H264 decoding. Does anyone know if XVMC (or other driver) supports this yet?

---

### Post by superm1 on 2006-12-10
> **brundles said:**
> I've found DVD playback via Xine is easier to test with than mpegs with mplayer - also giving a much more noticeable improvement (30% usage down to 17% ish on my system).

On another point, I believe the newer Nvidia cards include offboard H264 decoding. Does anyone know if XVMC (or other driver) supports this yet?

The linux driver doesn't support h264 decoding as of yet.

---

