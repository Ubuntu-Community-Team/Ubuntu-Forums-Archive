---
title: "Installing Nvidia drivers; Option &quot;UseDisplayDriver&quot; &quot;DFP&quot; not working"
date: 2009-06-01
forum: Multimedia Software
---

### Post by ItaniKnight on 2009-06-01
Software:
- Ubuntu 9.04
- X Server v11
- nvidia-glx-180 from Synaptic Package Manager

Hardware:
- Nvidia GeForce 7300 SE
- Venturer monitor / tv screen (not entirely sure which; see below)

I've been trying to install the proprietary Nvidia drivers for a few days now, with little success. I've been getting the (common?) error of no output on the screen; that is, it's completely blank, as though it were receiving nothing from the computer. I can use Ctrl+Alt+F1 (well, Ctrl+Alt+Fn+F1, Apple keyboard) to get to the console, and when I do this the login sound plays and I can use the computer in console mode.

I've looked around and apparently the recommended method of fixing it has no effect. This is detailed below:

```
$ sudo dpkg-reconfigure xserver-xorg -phigh
```

This resets the xorg.conf file to the defaults, which means I'm using the nv drivers. These work, but aren't ideal, because they're not great at 3D and the contrast / brightness is way off.

```
$ sudo nvidia-xconfig
```

This overwrites the last step and turns xorg.conf into a supposedly correctly configured file. It doesn't actually work, though, because I get the blank screen bug described earlier.

```
$ sudo gedit /etc/X11/xorg.conf
```

Based on the [launchpad bug recommendation](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/82312), I open up xorg.conf and stick 'Option "UseDisplayDevice" "DFP"' in under 'Section "Screen"'. It looks roughly like this: (see attachment "xorg-after-usedisplaydevice.txt" for the actual xorg.conf)

```
Section "Screen"
... blah blah blah
Option "UseDisplayDevice" "DFP"
EndSection
```

This has no affect on the blank screen issue, though. I can log in and run the dpkg-reconfigure again to get the display back.

Now, I'm wondering what to try next. I've got the nouveau drivers working just fine (apart from the *mild* 3D support) and it'll do for now, but I'd like to get the Nvidia drivers working. Does anyone have any suggestions?

Attached are the xorg.conf files after each stage, titled appropriately. No idea how helpful they'll be, but it's worth trying.

---

### Post by David Crockett on 2009-06-03
How did you get sudo NVIDIA-xconfig to work?

D

---

### Post by ItaniKnight on 2009-06-04
I didn't have to do anything to it, nvidia-xconfig ran fine by default. I think the drivers installed just fine, and would have worked if xorg.conf was properly set up.

I think, anyway. I really have no idea >_>

---

### Post by ItaniKnight on 2009-06-05
Bamp.

If I didn't make this clear earlier, I'm running nvidia-xconfig either before restarting (so, before X actually starts using the Nvidia driver and breaking down) or after, using the console view.

Since posting this I have tried the following:

```
Option "ConnectedMonitor" "DFP, CRT, TV"
Option "UseDisplayDevice" "TV"
```

Also using ["ConnectedMonitor"] and ["UseDisplayDevice" "DFP"] together didn't work either. I have yet to try just adding [Option "ConnectedMonitor" "DFP"] or [Option "ConnectedMonitor" "TV"] to xorg.conf.

---

### Post by ItaniKnight on 2009-06-11
This topic is going to get lost in a sea of topics and I would rather it did not. Bumpd.

---

### Post by ItaniKnight on 2009-06-28
Reddit fixed this for me. End result was to add [Modes "1440x900"] to ["Display"] and [Option "UseDisplayDevice" "DFP-0"] to ["Screen"]. This is why it wasn't working, apparently.

But thanks for all your help, you've been great.

---

### Post by WannabeKiwi on 2011-01-17
I've tried this, but still not working.

This is my system:
eMachine model [[COLOR="Blue"]_T5226_[/COLOR]]("http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T5226") (Follow the link for the specs. I haven't changed anything in it except the power supply to support the new card.)
nVidia GeForce 9800 GX2
Ubuntu 10.04 32-bit

I have started a thread myself [here]("http://ubuntuforums.org/showthread.php?p=10368561#post10368561") and have tried three or four different methods, from the Hardware Devices application to manually installing the driver downloaded to nVidia. Nothing is working for me... :confused:

---

