---
title: "Please help - Intel graphics not working"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by yang on 2007-09-19
I installed Ubuntu 7.04 onto my new Dell Inspiron 530 desktop. Currently I have very poor resolution. I can only go up to 1280x1024. ubuntuguide.org says that I can manually edit xorg.conf to add higher resolutions if I'm on a >20" monitor and I want 1920x1200, but I have a Dell 2005FPW (20") whose native res is 1600x1050, so I have no idea what magic numbers to put on the "Modeline" line. I tried adding lines like

```
Modeline	"1600x1050" 162.0 1600 1664 1856 2160 1050 1052 1064 1082
```

and

```
	SubSection "Display"
		Depth		24
		Modes		"1600x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
```

but nothing works (I restart X with c-a-bkspc).

I tried installing the 915resolution package as suggested in other threads, but it complains that I have the wrong chipset.

I installed beryl, but running beryl-manager makes my screen go black for a second, and then I get logged out!

I also went to the [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/) site and downloaded the xf86-video-intel package but running autogen.sh gave me the following errors:

```
configure.ac:214: installing `./config.guess'
src/Makefile.am:36: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:36:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:36:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/Makefile.am:36:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/Makefile.am:36:   its definition is in aclocal's search path.
src/Makefile.am: installing `./depcomp'
src/ch7017/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/ch7017/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ch7017/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/ch7017/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/ch7017/Makefile.am:8:   its definition is in aclocal's search path.
src/ch7xxx/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/ch7xxx/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ch7xxx/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/ch7xxx/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/ch7xxx/Makefile.am:8:   its definition is in aclocal's search path.
src/ivch/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/ivch/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/ivch/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/ivch/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/ivch/Makefile.am:8:   its definition is in aclocal's search path.
src/sil164/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/sil164/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/sil164/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/sil164/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/sil164/Makefile.am:8:   its definition is in aclocal's search path.
src/tfp410/Makefile.am:8: Libtool library used but `LIBTOOL' is undefined
src/tfp410/Makefile.am:8:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/tfp410/Makefile.am:8:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/tfp410/Makefile.am:8:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/tfp410/Makefile.am:8:   its definition is in aclocal's search path.
src/xvmc/Makefile.am:2: Libtool library used but `LIBTOOL' is undefined
src/xvmc/Makefile.am:2:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/xvmc/Makefile.am:2:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/xvmc/Makefile.am:2:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/xvmc/Makefile.am:2:   its definition is in aclocal's search path.
autoreconf2.50: automake failed with exit status: 1

```

I'm dying here - I bought this new machine to run Ubuntu, only to find that it's not working. I would *tremendously* appreciate any help. I tried posting on this before, but got no answers.

[http://ubuntuforums.org/showthread.php?t=551869](http://ubuntuforums.org/showthread.php?t=551869)

Here is some potentially relevant info:

```
yang@yang-inspiron:/tmp$ uname -a 
Linux yang-inspiron 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

yang@yang-inspiron:/tmp$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:29c1] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Unknown device [8086:29c2] (rev 02)
00:19.0 Ethernet controller [0200]: Intel Corporation Unknown device [8086:10c0] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation Unknown device [8086:293e] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation Unknown device [8086:2916] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation Unknown device [8086:2920] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation Unknown device [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation Unknown device [8086:2926] (rev 02)
02:00.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2f20]

```

---

### Post by Gremlinzzz on 2007-09-20
this works for me i have 1440x900
    * Another way to get the resolution you want is to do this(doesn't always work): 

sudo apt-get install xserver-xorg-video-intel
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by Gremlinzzz on 2007-09-20
> **Gremlinzzz said:**
> this works for me i have 1440x900
    * Another way to get the resolution you want is to do this(doesn't always work): 

sudo apt-get install xserver-xorg-video-intel
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

I had too reboot too get the results

---

### Post by yang on 2007-09-20
Sorry I should've mentioned this since I too saw it on the ubuntuguide, but I have that package already (xserver-xorg-video-intel). I don't recall if I was the one who installed it, or if it was already there, but it doesn't seem to be doing anything for me.

---

### Post by Gremlinzzz on 2007-09-20
[https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b4edf9f796d7f1ff720372aa5e7f4759618cf6d3](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-b4edf9f796d7f1ff720372aa5e7f4759618cf6d3)

---

### Post by dabl on 2007-09-20
Try ```
lspci -v
```

I can't see what chip you have -- maybe you need the i810 driver.

---

### Post by mhenry35 on 2007-09-20
I noticed that the 915resolution program doesn't work with the new intel driver.  If you want to try the 915resolution solution, then you'll need to reinstall the i810 driver first.

I just finished getting mine set up just perfectly with this program on an intel 945 chipset, and it's working great now.

However, since the 915resolution program died, we do need to identify for sure what chipset you have.

---

### Post by yang on 2007-09-20
Here you go:

```

$ lspci -v
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
        Subsystem: Dell Unknown device 020d
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Unknown device 29c2 (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ff00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation Unknown device 10c0 (rev 02)
        Subsystem: Dell Unknown device 020d
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
        Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at fe00 [size=32]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at fd00 [size=32]
        Capabilities: <access denied>

00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at fc00 [size=32]
        Capabilities: <access denied>

00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at fb00 [size=32]
        Capabilities: <access denied>

00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
        Subsystem: Dell Unknown device 020d
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at fa00 [size=32]
        Capabilities: <access denied>

00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at f900 [size=32]
        Capabilities: <access denied>

00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at f800 [size=32]
        Capabilities: <access denied>

00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at fdffd000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
        Subsystem: Dell Unknown device 020d
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at f700 [size=8]
        I/O ports at f600 [size=4]
        I/O ports at f500 [size=8]
        I/O ports at f400 [size=4]
        I/O ports at f300 [size=16]
        I/O ports at f200 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
        Subsystem: Dell Unknown device 020d
        Flags: medium devsel, IRQ 11
        Memory at fdffc000 (64-bit, non-prefetchable) [size=256]
        I/O ports at 0500 [size=32]

00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Dell Unknown device 020d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at f000 [size=8]
        I/O ports at ef00 [size=4]
        I/O ports at ee00 [size=8]
        I/O ports at ed00 [size=4]
        I/O ports at ec00 [size=16]
        I/O ports at eb00 [size=16]
        Capabilities: <access denied>

02:00.0 Communication controller: Conexant HSF 56k Data/Fax Modem
        Subsystem: Conexant Unknown device 200f
        Flags: bus master, medium devsel, latency 0, IRQ 4
        Memory at fddf0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at df00 [size=8]
        Capabilities: <access denied>

```

---

### Post by yang on 2007-09-21
Was this information helpful?

---

### Post by yang on 2007-09-22
Anybody?

---

### Post by dabl on 2007-09-22
Not very -- I wonder why all the "unkown devices"?  :confused:

It certainly seems that Feisty is having a lot of trouble recognizing the hardware on your system.  Apparently it is an Intel graphics chip --- one approach would be to assume it is something common like the GMA 950, and so look through the forum posts on that one and attempt to set it up.

I think you would install the i810 driver first, and if satisfactory results don't come, try the xserver-xorg-video-intel driver.  I'm a Nvidia type myself, so I'm not the expert, but I hope this helps a little ...  :?

---

### Post by yang on 2007-09-22
As you suggested, I installed xserver-xorg-video-i810 (which conflicts and removes the xserver-xorg-video-intel), but nothing different happens, and the max screen resolution is still the same (1280x1024).

If it helps any, the computer I bought is an Inspiron 530s. [http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWFAN&s=dhs](http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWFAN&s=dhs)

I've already poured much more time than I thought I would ever tolerate into looking through the forums about the GMA 950 etc. and trying this that and the other, all to no avail. I've been pursuing this every day for the past week. I'm at the end of my wits.

---

### Post by yang on 2007-09-27
Bump.

---

### Post by yang on 2007-09-29
Bump.

---

### Post by yang on 2007-10-09
bump

---

### Post by dcsweb on 2007-10-09
I feel your pain. Just unpacked our 3 new dell inspiron 530s...19" flat panel...ooooooo :)

Haven't even booted vista yet, just parted right down in size and installed on the back 200 gb.

So I grabbed 7.0.4 and thought I'd give K a try again.

1/2 expected to need some sort of intel memory patching to get resolutions right, but this is kinda silly. Exhausted all my resources on this. I did manage to get a garbled 1440x900 running.

Any info on this would be helpful. I will certainly post back here if I have more to share.

---

