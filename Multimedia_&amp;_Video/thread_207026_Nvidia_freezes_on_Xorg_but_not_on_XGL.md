---
title: "Nvidia freezes on Xorg but not on XGL"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by jvictor on 2006-07-01
Ive an nv-FX 5200 256 mb card that freezes randomly when I use Xserver directly unless AGP is disabled in xorg.conf..

However, recently I caught the Compiz bandwagon and in the process found Xgl to render my desktop instead of Xserver directly.. In this mode I neednt disable AGP and theres no hard freeze .. Looks like an Xorg 7.0 bug to me .. Any similar experiences ? Any workaround to avoid this freeze on Xorg ?

Oh btw compiz dint work , I got some error saying GLXFB not set for default depth or something of that nature. I tried many Howto, but decided to give up... coz its a waste of time for something not that useful to me.

---

### Post by jvictor on 2006-07-03
Enabling SBA, Faswrites and blacklisting amd64_agp and agpgart solved the issue

---

### Post by tseliot on 2006-07-04
Can you explain what you did in order to blacklist the modules, etc.?

I might add it to the guide so as to help solve some users' problems.

---

### Post by jvictor on 2006-07-04
Oh well ! Yes :D 

Im using a AMD64 - 32 bit Ubuntu machine

Plz dont consider this as final becuase im still testing it :) and havent got any freezes till now. Maybe a week more and we can say it is a solution



The first step was to blackist the amd64_agp & agpgart modules by adding 

```
#added for nvidia freeze fastwrite and sba 
blacklist agpgart
blacklist amd64_agp

```

to **/etc/modprobe.d/blacklist **


On other Intel machines the module that gets loaded maybe different
I'm not sure of what it is.

Next we need to enable Fast writes and SBA by editing 
  **         /etc/modprobe.d/nvidia-kernel-nkc**

and adding the line
```
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 
```


now finally modify **/etc/X11/xorg.conf**

and make the Device section look like this
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        Option          "NvAGP"                 "1"
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

 
Now logout and restart of X shoud fix the problem..

Again me not getting a freeze doesnt mean that others wont get .IMHO lets wait for some time and then make this final :)

Edit 
Made some stuff bold :)

---

### Post by jvictor on 2006-07-04
Its not foolproof; I got a freeze , but the frequency has reduced for sure

---

### Post by tseliot on 2006-07-04
Thanks for the explanation

---

