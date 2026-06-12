---
title: "Sound help for HP-Mini netbook"
date: 2009-06-24
forum: Multimedia Software
---

### Post by LiamG on 2009-06-24
Hi folks

I'm completely new to Ubuntu and I'm very excited about it, except that I haven't been able to get the sound running yet. I know that it is possible because the computer came with HP-MI installed, which is based on Ubuntu, and the sound worked fine. I have followed the Comprehensive Sound Problems Solutions Guide along with many other pieces of advice I've found on the internet, but still haven't heard a single peep. I know that every other Joe Beginner is posting this same quiestion, but I would really appreciate it if someone could help me out here.

Here's what I get for "aplay -l"

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```and here's what I get for lspci -v

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc80 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fe940000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0
    Memory at fe880000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe938000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe937c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at d400 [size=8]
    I/O ports at d080 [size=4]
    I/O ports at d000 [size=8]
    I/O ports at cc80 [size=4]
    I/O ports at cc00 [size=16]
    Memory at fe937800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: medium devsel, IRQ 5
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 1507
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

02:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec80 [size=128]
    Capabilities: <access denied>

```

---

### Post by LiamG on 2009-06-24
Can anyone help?

---

### Post by LiamG on 2009-06-24
Perhaps I can be a little more specific.

I have recently been trying to install the most up to date alsa drivers, as I have read that this might solve my problems. I am not self sufficient at Ubuntu yet, so I had to follow a tutorial--[[http://ubuntuforums.org/showthread.php?t=400268]--which](http://ubuntuforums.org/showthread.php?t=400268]--which) basically involved downloading alsa-drivers-1.0.20, alsa-lib.1.0.20 and alsa-utils-1.0.20 and them running the following code on each of them:

```
tar xvf <filename>.tar.bz2
cd <filename>
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ice1724 --with-oss=yes
sudo make
sudo make install
```

I got two thirds of the way there, but the alsa-utils-1.0.20 file wouldn't install properly. I got error messages on both "sudo make" and "sudo make install". Now the sound mixer only has one bar ("master") as if the alsa mixer isn't installed, and my sound still doesn't work.

How can I fully install the latest alsa driver?

I'm mystified as to why this is so hard!

---

### Post by LiamG on 2009-06-24
These are the error messages I get for alsa-utils:


sudo make:

```
Making all in include
make[1]: Entering directory `/home/liam/alsa-utils-1.0.20/include'
make  all-am
make[2]: Entering directory `/home/liam/alsa-utils-1.0.20/include'
make[2]: Leaving directory `/home/liam/alsa-utils-1.0.20/include'
make[1]: Leaving directory `/home/liam/alsa-utils-1.0.20/include'
Making all in alsactl
make[1]: Entering directory `/home/liam/alsa-utils-1.0.20/alsactl'
Making all in init
make[2]: Entering directory `/home/liam/alsa-utils-1.0.20/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/liam/alsa-utils-1.0.20/alsactl/init'
make[2]: Entering directory `/home/liam/alsa-utils-1.0.20/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/home/liam/alsa-utils-1.0.20/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/liam/alsa-utils-1.0.20/alsactl'
make: *** [all-recursive] Error 1
```



sudo make install:

```
Making install in include
make[1]: Entering directory `/home/liam/alsa-utils-1.0.20/include'
make[2]: Entering directory `/home/liam/alsa-utils-1.0.20/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/liam/alsa-utils-1.0.20/include'
make[1]: Leaving directory `/home/liam/alsa-utils-1.0.20/include'
Making install in alsactl
make[1]: Entering directory `/home/liam/alsa-utils-1.0.20/alsactl'
Making install in init
make[2]: Entering directory `/home/liam/alsa-utils-1.0.20/alsactl/init'
make[3]: Entering directory `/home/liam/alsa-utils-1.0.20/alsactl/init'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: Leaving directory `/home/liam/alsa-utils-1.0.20/alsactl/init'
make[2]: Leaving directory `/home/liam/alsa-utils-1.0.20/alsactl/init'
make[2]: Entering directory `/home/liam/alsa-utils-1.0.20/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/home/liam/alsa-utils-1.0.20/alsactl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/liam/alsa-utils-1.0.20/alsactl'
make: *** [install-recursive] Error 1
```

---

### Post by GA Dutchman on 2009-06-24
I fixed the sound on my HP 1030NR with UNR by following instructions from a similar thread;

[https://bugs.launchpad.net/netbook-remix/+bug/318942](https://bugs.launchpad.net/netbook-remix/+bug/318942) 

In the above thread the alsa sound drivers were being downloaded and compiled in a similar fashion however before those steps were performed I needed to follow the instructions below to install some packages which were required to compile the audio drivers.

- First, check that you have this packages installed (sudo apt-get install package_name):
 patch, gettext, libncurses5-dev, xmlto, xmltoman

Not sure if you need them all but I did see references to xmto in your error messages.
I'm a newbie for sure but thought this may help. Good luck!

GA Dutchman

---

### Post by LiamG on 2009-06-24
Thanks so much, Dutchman! I installed those files and successfully installed alsa 1.0.20 and I'm now getting sound to come out of the headphone jack, although the speakers still won't work. I think that the answer might be burried in the discussion you pointed me towards, however, I really don't have the mind for it right now--it can wait until tomorrow.

---

