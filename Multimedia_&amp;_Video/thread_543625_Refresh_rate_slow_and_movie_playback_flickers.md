---
title: "Refresh rate slow and movie playback flickers"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by skuli.arnlaugsson on 2007-09-05
I am not sure if my graphics adapter is setup correctly, I am trying to find out it's brand name, but I bought it in a package two years ago with a MSI motherboard:

```
Processor
Name	AMD Athlon XP/MP (Thoroughbred)
Specification	AMD Athlon(tm)
Family, model, stepping	6, 8, 1
Vendor	AuthenticAMD
Cache Size	256kb
Frequency	1240.54MHz
BogoMips	2483.34
Byte Order	Little Endian
```

And my display:

```
Display
Display
Resolution	1280x1024 pixels
Vendor	The X.Org Foundation
Version	7.2.0
Monitors
Monitor 0	1280x1024 pixels
Extensions
BIG-REQUESTS	
Composite	
DAMAGE	
DPMS	
Extended-Visual-Information	
GLX	
MIT-SCREEN-SAVER	
MIT-SHM	
MIT-SUNDRY-NONSTANDARD	
RANDR	
RENDER	
SECURITY	
SGI-GLX	
SHAPE	
SYNC	
TOG-CUP	
X-Resource	
XAccessControlExtension	
XC-APPGROUP	
XC-MISC	
XFIXES	
XFree86-Bigfont	
XFree86-DGA	
XFree86-Misc	
XFree86-VidModeExtension	
XInputExtension	
XKEYBOARD	
XTEST	
XVideo	
OpenGL
Vendor	Unknown
Renderer	Unknown
Version	Unknown
```

And the summary:
```
Summary
Computer
Processor	AMD Athlon(tm)
Memory	1003MB (315MB used)
Operating System	Ubuntu 7.04
User Name	skuli (SkÃºli Arnlaugsson)
Date/Time	09/05/07 / 14:43
Display
Resolution	1280x1024 pixels
OpenGL Renderer	Unknown
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	NFORCE - NVidia CK8
```

My screen flickers when playing DVDs and scrolling down webpages. Any ideas why? It's a generic NEC_ DVD burner (<one year old) and my display is a Dell Ultrasharp 19" 1907.

I've used my computer before (in XP) to play movies and browse the web but now in Ubuntu it flickers. I guess it's because I haven't set up my graphics card correctly, but I don't know how to do that. 

Please help me.

---

### Post by RomeReactor on 2007-09-05
Hi. To find out which video card you have try entering either of these commands in the terminal:
```
sudo lshw -C display
```
or
```
lspci | grep VGA
```

---

### Post by skuli.arnlaugsson on 2007-09-05
skuli@Alftamyri:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: NV18 [GeForce4 MX - nForce GPU]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@01:00.0
       version: a3
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
       resources: iomemory:ed000000-edffffff iomemory:e0000000-e3ffffff iomemory:e4000000-e407ffff irq:9

I've finally found out which graphics card it is, turns out its a bad graphics card, but should updating that be enough to get movie playback to smoothen out?

---

