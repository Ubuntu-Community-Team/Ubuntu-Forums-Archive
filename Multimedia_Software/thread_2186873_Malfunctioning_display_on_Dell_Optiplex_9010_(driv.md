---
title: "Malfunctioning display on Dell Optiplex 9010 (driver?)"
date: 2013-11-09
forum: Multimedia Software
---

### Post by Xeovke on 2013-11-09
Since I made the new release upgrade, the display started to malfunction. It works fine in recovery mode. Since I could not find the problem (which is not a suprise given I'm a basic user), I tried to reinstall Ubuntu from scratch. To my surprise the display is already "distorted" when one boots from the USB stick.

As was pointed to me in [this post]("http://ubuntuforums.org/showthread.php?t=2186040") this is probably (?) a driver issue. The following extract from the Xorg log:

```

[    18.676] (II) VESA: driver for VESA chipsets: vesa
[    18.676] (++) using VT number 7
[    18.676] vesa: Ignoring device with a bound kernel driver
[    18.676] (WW) Falling back to old probe method for vesa
[    18.676] (EE) Screen 0 deleted because of no matching config section.
[    18.676] (II) UnloadModule: "vesa"
[    18.676] (EE) Device(s) detected, but none match those in the config file.

```

A random Google search lead me to [this other post]("http://forums.gentoo.org/viewtopic-t-928250-start-0.html") which seems to indicate that something in the kernel already bound the video card and prevents the driver to do his job properly... This seems consistent with the fact the recovery mode works fine.

Anybody has a clue for a way out?

EDIT: I forgot to mention that in "sudo lshw", the "*-display" is followed by the mention "UNCLAIMED" in recovery mode.

---

### Post by Xeovke on 2013-11-11
I had the opportunity to test (booting from a USB stick) 7 Dell Optiplex 9010 today. 4 computers have correc display on boot and 3 don't. I kept the lshw, lspci, xdpyinfo, ddcprobe and Xorg.0.log of all these 7 boots. Here are the main differences in the files (except the Xorg.0.log which are not so handy to compare as the beginning of lines are always different).

I guess that the most telling is the following line from ddcprobe. For non-correctly-displaying computers:

```
dtiming: 1920x1080@68
```

For correctly-displaying computers:

```
dtiming: 1920x1080@60
```

Is there anyway to try to force xorg to use some specific values? For the record, there is no other ctiming or dtiming line in the output of ddcprobe.

The configuration are otherwise strikingly similar. The only other differences which seemed of significance (i.e. not mentionning hard drives paritions and serial numbers) is that uncorrectly working computers have the following extra line in lspci

```
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
```

Correspondingly, the lshw of these computers have the following extra section:

```

        *-communication:1
             description: Serial controller
             product: 7 Series/C210 Series Chipset Family KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:f0e0(size=8) memory:f7d3a000-f7d3afff

```

Lastly, in the *-pci section. Also, the *-memory *-bank:n (for n an integer) are not of the same vendor (Samsung or Nanya technologies for correctly-displaying computers and Hynix/Hyundai for non-correctly-displaying ones).

I'd gladly put these 35 files somewhere easy to download if I were told how. EDIT: they are availiable [here]("http://http://dfiles.eu/files/njfpo8b4k").

Should this be reported as a bug? If so how should I proceed? EDIT: I reported this as a bug, [there]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-saucy/+bug/1251580").

EDIT: I forgot to mention that if ones boot from a 13.04 or 12.10 distro then everything is fine on all computers...

---

### Post by Yellow Pasque on 2013-11-11
Try setting the distorted displays to 1920x1080@60 using xrandr:

If it works, make the change persistent in xorg.conf: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf](https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf)
Since you probably don't have an /etc/X11/xorg.conf, start with a basic skeleton:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by Xeovke on 2013-11-11
Thanks for the answer, Temüjin. I'm probably too incompetent to fully proceed: unfortunately, with xrandr I can only change between two rates 60.2 and 58.8, that is, whatever I put in rates get rounded to the nearest value xrandr seems to know (that's what I guess is happening by using xrandr again and looking at where the * went), and I can't get to force him to use something else than those two parameters...

Regarding xorg.conf, I tried to create a file. The changes I did there did not seem to make much of an effect. For the monitor section, I used the output of get-edid | parse-edid. Here is my current file (I must confess the change i made there never made a noticeable difference, except getting less warnings and errors in the Xorg.0.log).

```
Section "Module"
    Load    "glx"
    Load    "dri2"
    Load    "glamoregl"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Optiplex 9010"
    DefaultDepth    24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Virtual    1920 1080
        Modes    "1920x1080"
    EndSubSection
EndSection

Section "Monitor"
    Identifier    "OptiPlex 9010"
    VendorName    "MST"
    ModelName    "OptiPlex 9010"
    DisplaySize    508 285
    Mode    "1920x1080"    # vfreq 60.160Hz, hfreq 66.176kHz
        DotClock    144.000000
        HTimings    1920 2008 2052 2176
        VTimings    1080 1084 1089 1100
    EndMode
EndSection

Section "Device"
    Identifier  "Card0"
    #Driver    "intel"
    Driver    "vesa"
    BusID       "PCI:0:2:0"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured-Modified"
    Screen    "Screen0"
EndSection

```

---

### Post by Yellow Pasque on 2013-11-11
Is there a reason you're forcing vesa driver?

The next thing I would try is a 3.12 kernel (resolution or "mode" setting is handled in the kernel nowadays): [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/)
You need 3 .deb's from that page: the headers-all package and the image and headers packages appropriate for your architecture. Download the .deb's and install them:
```
cd ~/Downloads #or wherever you download the .deb's
sudo dpkg -i linux*
```

Move the custom xorg.conf out of the way so it doesn't interfere:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Reboot and hope the regression was fixed in 3.12.

---

### Post by Xeovke on 2013-11-12
Thanks again for the help! Unfortunately, it's still not working... The only part which displays correctly are the first two lines (which I don't remember precisely, something like " Loading kernel ..." and "Loading from ???disk ...").

There are 2 (probably bad) reasons for the vesa driver: 1) The computer works fine in recovery mode, and I read from the xorg.0.log that the vesa driver was then configuring the video (even if I put the intel driver). Conversely, during a normal boot, even if I put the Vesa driver, it fails and it's the intel driver who takes up. 2) There are less EE and WW in the xorg log when I boot in recovery mode with this, rather than intel

Here are two extracts form the freshest Xorg.0.log (there are no lines with EE or WW but only these two spots where a "failure" is mentioned)
```

[    20.427] (II) Loader magic: 0x7f3eb3fbbd20
[    20.427] (II) Module ABI versions:
[    20.427]    X.Org ANSI C Emulation: 0.4
[    20.427]    X.Org Video Driver: 14.1
[    20.427]    X.Org XInput driver : 19.1
[    20.427]    X.Org Server Extension : 7.0
[    20.427] (II) xfree86: Adding drm device (/dev/dri/card0)
[    20.427] setversion 1.4 failed
[    20.427] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
```

```
[    20.739] (II) config/udev: Adding drm device (/dev/dri/card0)
[    20.739] (II) xfree86: Adding drm device (/dev/dri/card0)
[    20.739] setversion 1.4 failed
[    20.739] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
```

Which reminds me: sometime, after my first post I also tried to install xmir. This made the error message from the very first post ("bound kernel...") disappear. However, this is replaced by the above two occurences of "setversion 1.4 failed". In order to boot in recovery mode I had to puttake out the**  Load "xmir"** line from the xorg.conf, as it would cause a freeze.

EDIT: I also try to boot a LinuxMint USB stick. Same deal: if the kernel is recent, it does not display correctly. Old kernels are OK.

---

### Post by Xeovke on 2013-11-14
The (temporary) solution was to downgrade the linux kernel to version 3.9.x

First, sudo apt-get remove linux-headers-3.1* linux-image-3.1*

Then follow [this link]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9.11-saucy/") and the instructions as in Temüjin's post to install the 3.9.x kernel, i.e. download the headers all and the image and headers corresponding to your architecture. Then sudo dpkg -i linux-*

[In case there are no kernel left, do not reboot between the 2 steps. Alternatively, do the operations in the opposite ordre and make sure afterwards that grub has the correct list of kernels]

Which other distros use kernel 3.10-3.12 so that I can test this bug is not distro dependent?

---

### Post by Xeovke on 2014-06-15
The bug has been fixed in kernel version 3.15-rc6 and above (i.e. avoid all linux kernels 3.10 until 3.14 and also the 3.15-rc1 up to 3.15-rc5). Thus one can now install the freshest kernel to resolve the problem (ant the problem should disappear naturally in newer Ubuntu version). Follow [this link]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") to get access to the newest kernel.

---

### Post by mtornos on 2014-07-05
Thanks Xeovke, it works like a charm! At this moment, with 3.15.3.

---

