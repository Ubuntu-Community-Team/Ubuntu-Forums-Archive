---
title: "ATI X1250 and really poor 3D performance"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by archetwist on 2007-07-12
Hello all!

I have an AMD 690G-based motherboard with integrated graphics (ATI Xpress 1250; this chip uses system's RAM) and its performance in 3D games is very poor. In [Savage]("http://www.s2games.com/savage/") I get about 2-12 FPS so the game is pretty much unplayable. With my previous Radeon 9600 everything was fine.

I've tested the default Ubuntu driver, the fglrx one (open source) and now I'm using the ATI proprietary fglrx driver.

```
arche@twist:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.0.6474 (8.38.6)
```

My xorg.conf (deleted unrelevant sections):
```
Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        BusID           "PCI:1:5:0"
        VideoRam        524288
        Option          "UseFBDev"              "true"
        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"         "off"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "ServerFlags"
        Option          "AIGLX"                 "off"
EndSection
```

In the X.org's log file there are no errors and only the following warnings:
> (WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) LoadModule: given non-canonical module name "glesx.so"
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards.
(WW) fglrx(0): Option "UseFBDev" is not used

Please help, you are my only hope ;) . I've Googled extensively without success.

---

### Post by compwiz18 on 2007-07-12
If you run **glxgears**, does it work smoothly?

---

### Post by archetwist on 2007-07-12
Yes, it does. And here is the output:
> 420 frames in 5.0 seconds = 83.856 FPS
757 frames in 5.0 seconds = 151.284 FPS
1918 frames in 5.0 seconds = 382.999 FPS
1917 frames in 5.0 seconds = 382.800 FPS
1918 frames in 5.0 seconds = 383.565 FPS
1917 frames in 5.0 seconds = 383.152 FPS

---

### Post by compwiz18 on 2007-07-12
I guess my next question would be: are you sure this card is capable of running Savage?

btw, on my ATI Xpress 200M, I get ```
2708 frames in 5.0 seconds = 541.439 FPS
3607 frames in 5.0 seconds = 721.312 FPS
3649 frames in 5.0 seconds = 729.125 FPS
3653 frames in 5.0 seconds = 729.920 FPS
3639 frames in 5.0 seconds = 727.750 FPS
``` I'm not sure that's really relevant, but it might help you somehow...

---

### Post by archetwist on 2007-07-12
Well, I thought my Radeon 9600 is slower than X1250. Maybe I was wrong.

---

### Post by compwiz18 on 2007-07-12
It's possible that the ATI drivers don't have very good support for that card...

---

### Post by archetwist on 2007-07-12
> **compwiz18 said:**
> It's possible that the ATI drivers don't have very good support for that card...
That's for sure ;) .

---

### Post by henkstubbe on 2007-07-17
mm, I have a Asus M2A-VM HDMI motherboard with a X1250 integrated and I got the following:

```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.0.6474 (8.38.6)

```

```
~$ glxgears
2139 frames in 5.0 seconds = 427.227 FPS
3554 frames in 5.0 seconds = 709.727 FPS
3633 frames in 5.0 seconds = 726.573 FPS
3658 frames in 5.0 seconds = 731.142 FPS
3670 frames in 5.0 seconds = 733.993 FPS
3656 frames in 5.0 seconds = 731.191 FPS
3663 frames in 5.0 seconds = 732.545 FPS
3704 frames in 5.0 seconds = 738.981 FPS
3655 frames in 5.0 seconds = 730.186 FPS
3677 frames in 5.0 seconds = 735.366 FPS
3677 frames in 5.0 seconds = 735.366 FPS

```

xorg.conf 
```

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

---

### Post by herrdoktor330 on 2007-07-20
Hey guys,

Just to throw in my 2 cents, I'm going to refer you all to the article detailing this chipset's 3D performance (under windows, but I'd say the same thing applies for Linux):

[http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=2942]("http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=2942")

According to this article, this isn't really a strong 3D gaming IGP (are there any at all?). The only things I have to bring to the table is what res and settings are you trying to run that game at. While the chipset itself has alot of nice features, I'm not sure that it's one for playing games at high res. All of the benchmarks this was tested on was 1024x768. Maybe on lower res this card would do better? I'm not sure.

Hope that helps.

---

### Post by archetwist on 2007-07-23
> **henkstubbe said:**
> ```
~$ glxgears
2139 frames in 5.0 seconds = 427.227 FPS
3554 frames in 5.0 seconds = 709.727 FPS
3633 frames in 5.0 seconds = 726.573 FPS
3658 frames in 5.0 seconds = 731.142 FPS
3670 frames in 5.0 seconds = 733.993 FPS
3656 frames in 5.0 seconds = 731.191 FPS
3663 frames in 5.0 seconds = 732.545 FPS
3704 frames in 5.0 seconds = 738.981 FPS
3655 frames in 5.0 seconds = 730.186 FPS
3677 frames in 5.0 seconds = 735.366 FPS
3677 frames in 5.0 seconds = 735.366 FPS

```
How much system RAM do you have? I got 1 GB. Maybe that is an issue. And which drivers are you using - Ubuntu or proprietary ones?

---

### Post by archetwist on 2007-07-31
Surprisingly, on Fedora I get around 750 FPS.

> bash-3.2$ glxgears
3051 frames in 5.0 seconds = 610.126 FPS
3760 frames in 5.0 seconds = 751.958 FPS
3766 frames in 5.0 seconds = 753.019 FPS
3809 frames in 5.0 seconds = 761.609 FPS
3799 frames in 5.0 seconds = 759.763 FPS

---

### Post by Ellipsys on 2007-08-01
I too am having difficulty with 3d and an ATI video card, except mine is a Mobility X600. In windows, this card could play WoW with everything on high (except AA and AF) at 1280x768, the laptop's native resolution.  I've downloaded the proprietary fglrx drivers from the repository. 

I tried running Nexuiz and Planet Penguin Racer, to test my 3d capability. Both are so slow, even on the menu screens, they're unusable.  Glxgears appear to be turning very slowly but say its running at a few hundred FPS.   Does anyone know what's going on here or how to get decent 3d performance?  Thanks!

---

### Post by archetwist on 2007-08-01
I wasn't able to find a solution other than a switch to Fedora ;) .

---

### Post by phillfri on 2007-08-05
Henkstube (and others) - I have a 690G chipset motherboard also (Asus) and tried to install F7 from the LiveCD. It just froze on me. On other distros, like PCLOS 2007, I am forced to use the acpi=off boot command option to be able to boot, but on the F7 LiveCD there was no opportunity to add boot options before it starts loading itself. How did you guys get F7 installed?

---

### Post by archetwist on 2007-08-05
I just did a standard F7 installation. I didn't have to disable ACPI. The only thing I had to do was to install the ATI fglrx driver. I still have problems with Savage though - some AGP error or something like that.

---

### Post by archetwist on 2007-08-08
I am wondering if [this MTRR issue](http://ubuntuforums.org/showthread.php?t=115104) has something to do with the slowness. The author of the thread wrote that > glxgears gives very laggy output, you can't play 3-d games, and performance is low. I have similar symptops and I get an MTRR error during boot though mine is a bit different:

> MTRR: writing MSR [some number here] failed

---

### Post by mike_sierra on 2007-09-01
Hello together,

i want to builda new pc with an IGP  and   actiuallythis is nvidia 7050    or amd 690G.

is there anyone who has glxgears     for the 7050 or its predecessor   to compair   with the  amd 690g?

Another question please:  does anyone knowifamd 690g meanwhile supports XVId

and does nvidia do it?ain dvi resolutions

last not least    i read that the amd 690 g does not support 3d for  a certain 3d resolution

is that known here?

thanksfor any reply: Mike

---

### Post by jacob01 on 2007-09-01
hmm this is a bit off topic but on my intel igp i get this in full window with glx gears


[CODEjacob@dell:~$ glxgears
1508 frames in 5.0 seconds = 301.508 FPS
999 frames in 5.0 seconds = 199.680 FPS
999 frames in 5.0 seconds = 199.656 FPS
998 frames in 5.0 seconds = 199.595 FPS
999 frames in 5.0 seconds = 199.550 FPS
999 frames in 5.0 seconds = 199.742 FPS
999 frames in 5.0 seconds = 199.668 FPS
999 frames in 5.0 seconds = 199.620 FPS
999 frames in 5.0 seconds = 199.622 FPS
jacob@dell:~$ 
][/CODE]

but i can hardly play any game for example i can playe quake 3 arena but i can not plat enemy territory but i can play assault cube on full setting with out lag or jumpy graphics

---

### Post by Steveway on 2007-09-01
You should take the Nvidia one.
My old Geforce Fx Go 5200 with 64MB Ram gives this in glxgears:
> steveway@steveway-laptop:~$ glxgears
10036 frames in 5.0 seconds = 2007.124 FPS
9256 frames in 5.0 seconds = 1851.154 FPS
10685 frames in 5.0 seconds = 2136.952 FPS
10391 frames in 5.0 seconds = 2078.181 FPS
10293 frames in 5.0 seconds = 2054.493 FPS
10638 frames in 5.0 seconds = 2127.590 FPS
10729 frames in 5.0 seconds = 2145.767 FPS
10364 frames in 5.0 seconds = 2072.744 FPS
10571 frames in 5.0 seconds = 2113.023 FPS
10687 frames in 5.0 seconds = 2136.953 FPS
10648 frames in 5.0 seconds = 2129.354 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
steveway@steveway-laptop:~$ 


---

### Post by mike_sierra on 2007-09-02
Thank's for your replies,

may i ask you jacob01 some more details 

which is exactly the intel igp you used  and could you please give me the 
glxgears values if you run  the window in origionally size  for better compair

best regards:Mike

---

### Post by tuxmas on 2007-11-03
Hi everybody,

I am not using Ubuntu, but Debian, but this shouldn't matter.
My question concerns the described Asus board, because I own the same...

fglrxinfo - in my case - shows only the "Mesa nightmare" and I don't know what I could change next...

Which driver version of ATI are you using?
And how did you install it?

I referred to this manual as installation:
[-> klick me <-]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Do you have any hints for me, how I could make it working?

Thx in advance

---

### Post by chiques on 2007-11-05
I show

> Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        BusID           "PCI:1:5:0"

I have a wide screen LCD tv and it's only showing in 4:3 aspect ratio. I also can't get the "aticonfig" or "fglrxinfo" to print anything.

---

### Post by jaxån on 2008-04-21
I would say that both ATI and nVida onboard graphics has it issues. :(

Anyway, have you tried this:  sudo chgrp video /dev/dri/card0 

It helped a bit with ATI:s fglrx X11 driver.

And Video and OpenGL overlay is not funktional yet.

---

