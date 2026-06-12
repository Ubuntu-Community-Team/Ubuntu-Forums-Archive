---
title: "No signal on HDMI after updating AMD/ATI drivers"
date: 2011-05-05
forum: Multimedia Software
---

### Post by 10robinho on 2011-05-05
Hi!

This is my first post as I'm new to this beautiful world of Linux.

I have strange problem and I was looking for the solution on forums for 3 days but couldn't find anything that would help.

**I using Asrock e350m1 and Ubuntu 11.04 connected with TV (GRUNDIG LCD 1366x768 ) via HDMI.**

When I've installed Ubuntu (everything was normal during installation) my screen resolution was [COLOR=Red]1360[/COLOR]x768 (notice that TV is [COLOR=Red]1366[/COLOR]x768 ) - just to notice because i didn't saw anything bad in this.

Than, I installed proprietary drivers (AMD/ATI proprietary FGLRX graphic driver).

After installation, it asked to restart system and I, of course, did it.

Until this point everything was normal...

Than, computer started to boot as it does normally, but **after splash screen my TV lost signal**.

Interesting point is that when I connect regular monitor to DVI (VGA) port, I can boot normally and if I also leave TV connected with HDMI I get duplicated desktop on my TV with resolution as same as on monitor (1280x1024). When I connect things like that I can go to ATI settings and change resolution of TV to any other than monitors. I can choose, for example, 1280x720 and it shows nicely on TV. But as soon as I chose 1360x768 I loose signal (same as on boot).

Than, I tried to install Ubuntu 10.10 and proprietary drivers. I got interesting result.
After restart my TV displayed 1360x768 and driver was working fine, but in the right bottom corner it was watermark "AMD unsupported hardware".
That was older version of AMD/ATI drivers which couldn't play sound over HDMI but could display 1360x768.

This is telling that it might be a problem in new AMD/ATI drivers.

This problem is driving me mad for couple of days and I'm begging for some help. I don't know if it is restricted to offer a reward if someone can solve me this because I need my PC to be able to output signal to any HDTV without exceptions!

---

### Post by Yellow Pasque on 2011-05-05
So it works with open-source drivers? Do you have any real need to use fglrx (like gaming)?

---

### Post by 10robinho on 2011-05-05
> **Temüjin said:**
> So it works with open-source drivers? Do you have any real need to use fglrx (like gaming)?

Well, I don't need it for gaming but I need my GPU to accelerate HD video playback.

When I've installed that old version, I've also installed something to enable GPU video acceleration for VLC. I think that I've found that in some ppa called **catalysthacks** in some topic that you were involved in :D. 

So, can I avoid FGLRX somehow and be able to use power of my GPU?

---

### Post by Yellow Pasque on 2011-05-05
Unfortunately, open-source HD decode accleration is not yet ready for users, but it is being worked on: [http://www.phoronix.com/scan.php?page=news_item&px=OTM4MA](http://www.phoronix.com/scan.php?page=news_item&px=OTM4MA)

I have a few ideas: Try the newest drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide) and if they don't work, look at /var/log/Xorg.0.log to see why. File appropriate bug report on AMD bugzilla: [http://ati.cchtml.com/](http://ati.cchtml.com/)

With the 10.10 setup, you could also try using a new /etc/ati/control file to make the watermark go away and possibly get hdmi sound working. I've attached the control file from the latest Catalyst.

---

### Post by 10robinho on 2011-05-05
Thank you!

I will try this options and report back with results!

I have another idea:

Is it possible to force xorg.conf to use exact resolution for my TV?

It looks like something is wrong with signal that TV is receiving, so can I force my graphic card to send defined type?

---

### Post by Yellow Pasque on 2011-05-05
It's possible. That's why I wanted to see the Xorg.0.log.
While you're at it, post the xorg.conf you use.

---

### Post by Blasphemist on 2011-05-05
You can tell your system what resolution to use for each monitor using xrandr. Example where VGA is the display.

```
xrandr --output VGA --mode 1024x768
```

See this page for further description. This happens to be the man page for natty.

[http://manpages.ubuntu.com/manpages/natty/man1/xrandr.1.html](http://manpages.ubuntu.com/manpages/natty/man1/xrandr.1.html)

---

### Post by 10robinho on 2011-05-05
Now, I don't have fglrx installed, so I don't have xorg.conf file.

I've attached my log file if you can get anything from it now.

I will install fglrx now and report back what have I got.

Blasphemist thank you for your suggestion, I will try that if I don't get 1360x768 with new drivers.

---

### Post by Yellow Pasque on 2011-05-05
This one captures my attention:
```
[  2503.450] (WW) EDID timing clock 121.75 exceeds claimed max 85MHz, fixing
```
I'm guessing Catalyst is having a hard time with the EDID and you'll need to set modes manually (bleh).

---

### Post by 10robinho on 2011-05-05
I've installed fgrlx and asme thing happened - my TV lost signal after splash screen.

I couldn't even do Ctrl+Alt+F2...

So, I've connected my monitor with 1280x1024 and now I can see that drivers are installed as they should. *fglrxinfo* outputs this:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string: 4.1.10665 Compatibility Profile Context

```

So, what can I do now? I suppose that I should disable EDID in my xorg.conf and tell it to use 1360x768?

By the way, this is my xorg.conf

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

```

---

### Post by 10robinho on 2011-05-05
After hours of hard work and research, I've found the solution! \\:D/

I've noticed that may Ubuntu users had problems with detecting theirs TV (HDTV, LCD) when connected via HDMI. Most common error is blank screen / no signal on boot, after the splash screen.

This is how I solved it, step by step.

[SIZE=2]**1. Clean install of Ubuntu 11.04 (32-bit)**[/SIZE]
That should be simple, just download from [http://http://www.ubuntu.com/download/ubuntu/download]("http://http//www.ubuntu.com/download/ubuntu/download") and follow instructions on screen.
If you don't have signal on you TV when trying to install Ubuntu, try to use DVI (VGA) and some monitor. In that case, it is possible that you will not be able to fix your problem, but don't give up!

**[SIZE=2]2. Install AMD/ATI proprietary drivers[/SIZE]**
Go to System -> Administration -> Additional drivers and install.
If you use new Unity desktop, type in search "Additional drivers", it should work.
Restart after installation.

[B][SIZE=2]3. Make drivers generate and use your xorg.conf
[/SIZE][/B][SIZE=1]First, you need to generate xorg.conf file that is located in /etc/X11/xorg.conf.
Only way I now is to type in this (idea came from: [/SIZE][http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file)[SIZE=1])
[/SIZE]```
sudo aticonfig --initial -f
```and than this
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```**[SIZE=2]4. Edit your xorg.conf[/SIZE]**
Best way is to type in
```
sudo gedit /etc/X11/xorg.conf
```This is my xorg.conf and bold lines is what I've added.
I'm not sure that everything here is needed, but it works.
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
**    Option    "preferredmode"    "1366x768"**
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
[B]    Option    "UseEdidDpi"    "FALSE"
    Option    "useEdid"    "FALSE"[/B]
    SubSection "Display"
        Viewport   0 0
        Depth     24
**        Modes    "1366x768"**
    EndSubSection
EndSection

```

---

### Post by Yellow Pasque on 2011-05-05
Congrats and thanks, I will add it to the AMD wiki in a section on overriding bad EDID's

---

