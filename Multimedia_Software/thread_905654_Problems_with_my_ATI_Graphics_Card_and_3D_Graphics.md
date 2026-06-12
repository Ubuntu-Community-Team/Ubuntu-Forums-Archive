---
title: "Problems with my ATI Graphics Card and 3D Graphics"
date: 2008-08-30
forum: Multimedia Software
---

### Post by ortsa on 2008-08-30
I recently used ENVY to install drivers for my ATI HD 2600XT, before that i was able to play windows games using wine without any problems, now i am unable to(the games simply crash when i start them), I decided to change my drivers from the default propitiatory ones because the 3D Acceleration in VMWARE was not working, i thought doing this would make things better.

When i run fgl_glxgears i get the following error messages
```
Using GLX_SGIX_pbuffer
Segmentation fault

```

Running fglrxinfo gives me 
```
Segmentation fault

```

Running glxinfo gives me
```
name of display: :0.0
Segmentation fault

```

Also running opengl 1.5 programs results in the segmentation fault

I have attached my xorg.conf file. If you need any more infomation ask.

Thankyou

EDIT: After doing a little searching i put export LIBGL_DEBUG=verbose in my console and running glxinfo or fglrxinfo gives me
```
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.50.3 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 5, (OK)
drmOpenByBusid: drmOpenMinor returns 5
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
Segmentation fault
```

Important:
I think i have found the problem! Running programs using sudo solves the problem now all i need is the files i need to chmod to make myself able to run the programs right?

---

