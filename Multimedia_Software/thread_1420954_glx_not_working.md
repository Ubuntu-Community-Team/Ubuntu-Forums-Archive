---
title: "glx not working"
date: 2010-03-03
forum: Multimedia Software
---

### Post by jmiguel77 on 2010-03-03
Hi

I have a problem with glx. When i run glxgears i get this error:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

This is my xorg.conf

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Module"
        Load    "dri"
        Load    "glx"
EndSection

this is my lshw output

*-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0

i have tried several solutions from this very forum, but none is working for me

thanks for your help

---

### Post by lidex on 2010-03-03
Try these commands in a terminal and post the output here:
```
LIBGL_DEBUG=verbose glxinfo | grep error
```
```
LIBGL_DEBUG=verbose glxinfo | head
```

Find a terminal in "Applications>Accessories>Terminal"
When you copy the text into your post, first click the "#" in the edit toolbar.

---

