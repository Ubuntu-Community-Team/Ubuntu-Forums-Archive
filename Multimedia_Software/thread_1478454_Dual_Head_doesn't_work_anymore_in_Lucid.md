---
title: "Dual Head doesn't work anymore in Lucid"
date: 2010-05-09
forum: Multimedia Software
---

### Post by wavemaking on 2010-05-09
Upon upgrading to Lucid from Karmic, my dual head setup doesn't work anymore with the new 2.6.32 kernel. In the previous kernel 2.6.31, everything works as expected (also when I boot Lucid with that kernel). On 2.6.32, the only thing I get is two clones. Is there some new type of configuration required that I missed or should I still compile some new kernel module???

My card:

```
rogier@rogier-desktop:~$ lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
```

My xorg.conf, which worked fine on Karmic:

```

Section "Monitor"
        DisplaySize     408 305         # Not correctly detected !
        Identifier      "P1100"
        VendorName      "Hewlett Packard"
        ModelName       "P1100"
        Option          "DPMS"          "true"
EndSection

Section "Monitor"
        Identifier      "S910"
        Option          "RightOf"       "P1100" # Thus section, including this remark is required!
        VendorName      "Compaq"

        ModelName       "S910"
        Option          "DPMS"          "true"
EndSection

#Section "Monitor"i
#        Identifier      "TV"
#        Option          "LeftOf"       "P1100"
#        VendorName      "Panasonic"
#        ModelName       "PRISM W1"
#        Option          "DPMS"          "true"
#EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Radeon9000"
        Monitor         "P1100"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Virtual 3360 1200
        EndSubSection
EndSection

Section "DRI" #Not required anymore?
        Mode         0666
EndSection

Section "Extensions" # Not required anymore?
        Option  "Composite"     "Enable"
        Option  "RENDER"        "Enable"
        Option  "RANDR"         "Enable"
EndSection

Section "Device"
        Identifier      "Radeon9000"
        Driver          "radeon"
        VendorName      "ATI"
        BoardName       "ATI Radeon 9000"
        Option          "Monitor-VGA-0"         "P1100" #Required for separate dual heads
        Option          "Monitor-DVI-0"         "S910" #Required for separate dual heads
        Option          "BusType"               "PCI"
        Option          "MigrationHeuristic"    "greedy" #http://www.mail-archive.com/universe-bugs@lists.ubuntu.com/msg152815.html
        BusID           "PCI:1:0:0"
#The following might increase performance, required?
        Option          "AGPmode"               "1"
        Option          "AccelMethod"           "EXA"
        Option          "AccelDFS"              "true"
        Option          "EnablePageFlip"        "true"
        Option          "EnableDepthMoves"      "true"
EndSection
```

These are the only lines that pop up as error or warning messages in the log file, which don't seem to be related to my problem:

```
rogier@rogier-desktop:~$ cat /var/log/Xorg.0.log |grep 'EE'
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) Logitech USB Receiver: failed to initialize for relative axes.

```


```
rogier@rogier-desktop:~$ cat /var/log/Xorg.0.log |grep 'WW'
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEON(0): Option "BusType" is not used
(WW) RADEON(0): Option "AGPmode" is not used
(WW) RADEON(0): Option "EnableDepthMoves" is not used
```

To try and switch to the actual dual head mode, I use the following command, which now exist without result (and without feedback about the problem):

```
xrandr --output DVI-0 --noprimary --right-of VGA-0 --mode 1280x1024 --rate 75
```

---

### Post by Canbee on 2010-05-10
Seems that the xorg.conf is not anymore used in Lucid, and the video config is now handled by the kernel, which has something to do with their effort to make boot times faster.

I'd recommend that you make sure that the old ati driver is uninstalled, then install the latest ATI Catalyst Center app from the ati site. You can then use their app to do the config needed for the dual head.

---

### Post by iblazev on 2010-05-10
ATI doesn't support old models in their new drivers. U can only download legacy 9.3 drivers but they don't work in Lucid. Didn't see if anyone installed them yet successfully :/

---

### Post by wavemaking on 2010-05-10
> **Canbee said:**
> Seems that the xorg.conf is not anymore used in Lucid, and the video config is now handled by the kernel, which has something to do with their effort to make boot times faster.


Well, I must say that booting indeed seems to be quicker.

However, is it not xorg itself rather than the kernel that reads xorg when starting? My xorg setup work just fine still when I boot an old kernel (2.6.31-*). So this is what I'll keep doing for the moment. Unfortunately, the terminal (CRTL-ALT-F1 though F6) doesn't show anything with the old kernel, I assume because of the new boot animation being not compatible with the other kernel.

Could I conclude that the kernel support for the radeon driver is not as complete as it used to be?

---

### Post by wavemaking on 2010-05-31
Well, I don't know what did it, but everything works as previously, with still the same xorg.conf file. Maybe it was the upgrade to the 2.6.32-22 kernel.

---

