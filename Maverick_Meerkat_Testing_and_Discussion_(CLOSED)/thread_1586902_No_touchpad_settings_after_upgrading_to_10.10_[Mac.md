---
title: "No touchpad settings after upgrading to 10.10? [Macbook Pro 6,2]"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jekshadow on 2010-10-02
I upgraded from a fresh install of 10.04, and now I have no touchpad settings at all. The previous location of "System -> Preferences -> Mouse" does not show a "Touchpad" tab like it used to, and even when I manually installed the gsynaptics package, none of the configuration changes did anything.

Also, all of the settings have reverted to the defaults, leaving me unable to scroll with my touchpad or right click.

---

### Post by VinDSL on 2010-10-02
What does this report?

```
$ cat /proc/bus/input/devices
```

---

### Post by Jekshadow on 2010-10-02
> **VinDSL said:**
> What does this report?

```
$ cat /proc/bus/input/devices
```

```

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=05ac Product=0236 Version=0111
N: Name="Apple Inc. Apple Internal Keyboard / Trackpad"
P: Phys=usb-0000:00:1a.7-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: EV=120013
B: KEY=10000 0 0 0 1007b00011007 ff9f217ac14057ff ffbeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=05ac Product=820a Version=0111
N: Name="HID 05ac:820a"
P: Phys=usb-0000:00:1a.7-1.1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.0/input/input5
U: Uniq=
H: Handlers=sysrq kbd event5 
B: EV=120013
B: KEY=1000000000007 ff800000000007ff febeffdff3cfffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=05ac Product=820b Version=0111
N: Name="HID 05ac:820b"
P: Phys=usb-0000:00:1a.7-1.1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1/1-1.1.2/1-1.1.2:1.0/input/input6
U: Uniq=
H: Handlers=mouse0 event6 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=3
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="applesmc"
P: Phys=
S: Sysfs=/devices/platform/applesmc.768/input/input7
U: Uniq=
H: Handlers=event7 js0 
B: EV=9
B: ABS=3

I: Bus=0003 Vendor=05ac Product=0236 Version=0001
N: Name="bcm5974"
P: Phys=usb-0000:00:1a.7-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.2/1-1.2:1.2/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=e420 10000 0 0 0 0
B: ABS=7f000011000003

I: Bus=0003 Vendor=05ac Product=8507 Version=0435
N: Name="Built-in iSight"
P: Phys=usb-0000:00:1d.7-1.1/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=3
B: KEY=100000 0 0 0

```

---

### Post by VinDSL on 2010-10-03
Hrm...

Well, it looks like the kernel is recognizing your "touchpad".

My best guess is, it's a kernel regression.

Doing a little research, it appears that your "touchpad" has had problems in the past.  

Example:  [https://bugzilla.kernel.org/show_bug.cgi?id=14987](https://bugzilla.kernel.org/show_bug.cgi?id=14987)

It looks like 2.6.26 fixed these problems, but now they may be back in 2.6.35.

If it was me, I'd launch a bug report on Launchpad...

---

### Post by Jekshadow on 2010-10-03
> **VinDSL said:**
> Hrm...

Well, it looks like the kernel is recognizing your "touchpad".

My best guess is, it's a kernel regression.

Doing a little research, it appears that your "touchpad" has had problems in the past.  

Example:  [https://bugzilla.kernel.org/show_bug.cgi?id=14987](https://bugzilla.kernel.org/show_bug.cgi?id=14987)

It looks like 2.6.26 fixed these problems, but now they may be back in 2.6.35.

If it was me, I'd launch a bug report on Launchpad...

I checked my dmesg, and the only message relating to my touchpad was when usbcore registered the bcm5974 driver. Also, when I installed uTouch and gesturetest, it successfully recognized both taps and drags from 1 to 5 fingers (I did not test more). I am definitely not an expert, but it seems like this is more of a userland problem with translating the gestures into actions than a kernel problem.

---

### Post by pouipschngoku on 2010-10-06
Hi Guys,

Was having a hard time with this myself and eventually resolved it by running:

sudo apt-get install xserver-xorg-input-synaptics

After a restart I am now able to make changes to System -> Preferences -> Pointing Devices that actually work. Up to this point even disabling the trackpad would do nothing. Now I have full control back. Tested tapping, scrolling (two finger), pinch to zoom all working great. I also always had trouble with accidental trackpad input when typing in 10.04, this seems to have been resolved too.

I also have bcm5974-dkms from the mactel repos installed.

Hope this helps someone out:)

---

### Post by VinDSL on 2010-10-06
Nice to know.  Thanks!

I've alway run Mint, on my netbook & laptop.  But, I can't stand Mint on the desktop.  Go figure...

I've pretty much relegated myself to running Ubu on my primary desktop machines (for the past year).

I'm going to switch to Ubu on the portables, soon, and I'm sure this info will be helpful.  ;)

---

