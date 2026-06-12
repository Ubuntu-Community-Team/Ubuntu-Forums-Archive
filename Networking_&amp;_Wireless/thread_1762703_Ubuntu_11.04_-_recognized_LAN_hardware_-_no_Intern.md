---
title: "Ubuntu 11.04 - recognized LAN hardware - no Internet"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by maxe on 2011-05-19
I can't connect my hardware with Ubuntu to the Internet. I am a complete noob who only understands that I am basically supposed to be downloading things on a separate computer, getting them onto the Internet-less computer, typing things into the Terminal and that sometimes it works and sometimes something is broken. This has been my basic experience with Linux so far. I prefer these systems to commercial Macin$oft but hardware issues with Ubuntu seem to be a wrestling match. I can't connect to the Internet.

I recently installed Xubuntu 10.04 and everything worked pretty well except the ethernet card was not being used by Ubuntu to connect to the wired Internet.

After searching in forums for some time, I didn't find a solution - and I did find people saying 10.04 was not as good as 11.04 so I upgraded to Ubuntu 11. After a couple tries, I got a successful install of that, except for the ethernet device is still not being used as it should. It is detected and identified (maybe just by the firmware? I don't know enough about the commands to know what I'm actually asking linux to do) and the device lights up when the Internet ethernet wire is plugged in, but nothing flows. Firefox is blank.

When I type

```
sudo lshw -class network
```

I get this information:

```

*-network: UNCLAIMED
description: Ethernet controller
product: N10/ICH 7 Family LAN Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:07:08.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=32 maxlatency=56 mingnt=8
resources: memory:92004000-92004fff ioport:1000(size=64)

```

In this thread: [http://ubuntuforums.org/showthread.php?t=1759632](http://ubuntuforums.org/showthread.php?t=1759632) (Wire Connection Not Showing In Panel or Connecting) I saw a recommendation to try getting the network manager to do its job by turning it on and off using ```
sudo service network-manager stop
```

```
sudo rm /var/lib/NetworkManager/NetworkManager.state
```

```
sudo service network-manager start
```

I was able to stop and start the network manager, which made the "wireless: no signal" icon disappear (on stop) and reappear (on start).

Then, I tried rebooting Ubuntu with the ethernet disabled in the BIOS, and rebooting again with the ethernet enabled. Didn't seem to help.

Is it just that it's not asking for an IP address? How can I tell it to start behaving? Am I missing an obvious "on" switch some where?

---

### Post by sanguinoso on 2011-05-19
Post the results of this command ```
ifconfig
```

---

### Post by maxe on 2011-05-19
ifconfig returns:

```

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 adddr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:108 errors:0 dropped:0 overruns:0 frame:0
         TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)


```

---

### Post by josephmills on 2011-05-19
```
lspci -nn
```

---

### Post by maxe on 2011-05-19
lspci -nn returns:

well, a whole bunch of devices under the "Intel Corporation N10/ICH 7 Family"

Including the last line:

```
07:08.0 Ethernet controller [0200]: Intel Corporation N10/ICH 7 Family LAN Controller [8086:27dc] (rev 01)
```

Okay, here is the full list of devices, plus anything that isn't N10/ICH 7 Family:

```

00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation  N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation  N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation  N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 [8086:27e0] (rev 01)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 [8086:27e2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH 7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family  SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] [10de:0161] (rev a1)
07:05.0 Firewire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
07:08.0 Ethernet controller [0200]: Intel Corporation N10/ICH 7 Family LAN Controller [8086:27dc] (rev 01)

```

---

### Post by josephmills on 2011-05-19
> **maxe said:**
> lspci -nn returns:

well, a whole bunch of devices under the "Intel Corporation N10/ICH 7 Family"

Including the last line:

```
07:08.0 Ethernet controller [0200]: Intel Corporation N10/ICH 7 Family LAN Controller [8086:27dc] (rev 01)
```

It seems redundant, but I can list everything, if you need it.

The PCI bridges look listed slightly differently, like:

```
 ... 82801GR/GH/GHM (ICH7 Family) ... 
```

please show whole list thanks

---

### Post by josephmills on 2011-05-19
could we also see a ```
lsmod | grep e100
``` and a ```
dmesg | grep e100 
``` if nothing comes up ok just tell us could we also see the blacklist file ```
cat /etc/modprobe.d/blacklist.conf
``` thanks

---

### Post by maxe on 2011-05-19
Okay I am going back and adding the complete output to that post ... refresh that one in a few minutes. It is a lot to type. :)


from lsmod | grep e100 I get:

```

[COLOR="Red"]e100[/COLOR]                       40108  0

```

from dmesg | grep e100 I get something that looks pretty useful:

```

[    0.303653] pci 0000:07:08.0: Firmware left [COLOR="Red"]e100[/COLOR] interrupts enabled; disabling
[    1.441560] [COLOR="Red"]e100[/COLOR]: Intel(R) PRO/100 Network Driver, 3.5.24-k2_NAPI
[    1.441567] [COLOR="Red"]e100[/COLOR]: Copyright(c) 1999-2006 Intel Corporation
[    1.441658] [COLOR="Red"]e100[/COLOR] 0000:07:08.0: PCI INT A -> GSI 20 (level, low) _> IRQ 20
[    1.464654] [COLOR="Red"]e100[/COLOR] 0000:07:08.0: (unregistered net_device): EEPROM corrupted
[    1.467198] [COLOR="Red"]e100[/COLOR] 0000:07:08.0: PCI INT A disabled
[    1.467220] [COLOR="Red"]e100[/COLOR]: probe of 0000:07:08.0 failed with error -11

```

---

### Post by maxe on 2011-05-19
And here is the blacklist.

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


```

---

### Post by sanguinoso on 2011-05-19
Could you post the output of ```
ifconfig -a
```. It appears the ethernet adapter is down.

---

### Post by maxe on 2011-05-19
Is that an unrecoverable error? Here is what it says now, with -a

```

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 adddr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:428 errors:0 dropped:0 overruns:0 frame:0
         TX packets:428 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:33392 (33.3 KB)  TX bytes:33392 (33.3 KB)

```

---

### Post by josephmills on 2011-05-19
hi I just got an pm try this > I suggest you ask him to sudo gedit /etc/modprobe.d/e100.conf

Add one line:

options e100 eeprom_bad_csum_allow=1

Proofread, save and quit gedit. Reboot and is it working now?

---

### Post by josephmills on 2011-05-19
did it work?

---

### Post by maxe on 2011-05-19
first line returns:

```


(gedit:1832): Gtk-WARNING **: Attempting to store changes into '/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JNYWVV': No such file or directory

(gedit:1832): Gtk-WARNING **: Attempting to set the permissions of '/root/.local/share/recently-used.xbel', but failed: No such file or directory


```

Indeed, when I look in the folder etc/modprobe.d, the only files I see are alsa-base.conf and some blacklist files. No e100.conf

Should I try to find where e100.conf is located?

Also - tangent question - does this mean my hardware is messed up? Would the installation of a network card simply move the problem to a new card or would it potentially work better than the motherboard's ethernet port - which we are trying to use now?

---

### Post by sanguinoso on 2011-05-19
> **maxe said:**
> Is that an unrecoverable error? Here is what it says now, with -a

```

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 adddr: ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:428 errors:0 dropped:0 overruns:0 frame:0
         TX packets:428 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:33392 (33.3 KB)  TX bytes:33392 (33.3 KB)

```

Did you run that as root ? i.e. ```
sudo ifconfig -a
```

---

### Post by maxe on 2011-05-19
How do I run as root? I only installed one user as far as I know - the one I am logged in as - but is there always a "root" user created separately?

---

### Post by josephmills on 2011-05-19
please see post 12 again proff read and do again

---

### Post by maxe on 2011-05-19
> **josephmills said:**
> please see post 12 again proff read and do again

Okay, I entered it again, these characters exactly:

```
sudo gedit /etc/modprobe.d/e100.conf
```

I received the following return message:

```
(gedit:1832): Gtk-WARNING **: Attempting to store changes into '/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JNYWVV': No such file or directory

(gedit:1832): Gtk-WARNING **: Attempting to set the permissions of '/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

Looks like the same as before. If I were in "root" would this change potentially? Or is "root" what I assume it is - merely the default user?

I saved the following characters in the blank e100.conf that is created:

```

options e100 eeprom_bad_csum_allow=1

```

Then rebooted. Nothing has changed.

Thanks for helping me try different things, friends.

---

### Post by chili555 on 2011-05-19
> indeed, when I look in the folder etc/modprobe.d, the only files I see are alsa-base.conf and some blacklist files. No e100.confYou will be creating e100.conf. Please proceed.

Those are warnings, not errors; Ok for now.

---

### Post by maxe on 2011-05-19
I should say nothing has *appeared* to change. Maybe the creation of that file with that line in it somehow repaired something?

---

### Post by chili555 on 2011-05-19
Did you reboot? If it still doesn't work, let us see:```
dmesg | grep e100
```Thanks.

---

### Post by maxe on 2011-05-19
> **chili555 said:**
> Did you reboot? If it still doesn't work, let us see:```
dmesg | grep e100
```Thanks.

I rebooted (rebate? rebute? past tense of reboot).

It still didn't work.

This "dmesg | grep e100" stratagem returned the same message as before but different numbers at the beginning:

```
[    0.287396] pci 0000:07:08.0: Firmware left [COLOR="Red"]e100[/COLOR] interrupts enabled; disabling
[    1.433344] [COLOR="Red"]e100[/COLOR]: Intel(R) PRO/100 Network Driver, 3.5.24-k2_NAPI
[    1.433351] [COLOR="Red"]e100[/COLOR]: Copyright(c) 1999-2006 Intel Corporation
[    1.464088] [COLOR="Red"]e100[/COLOR] 0000:07:08.0: PCI INT A -> GSI 20 (level, low) _> IRQ 20
[    1.486962] [COLOR="Red"]e100[/COLOR] 0000:07:08.0: (unregistered net_device): EEPROM corrupted
[    1.486987] [COLOR="Red"]e100[/COLOR] 0000:07:08.0: PCI INT A disabled
[    1.487004] [COLOR="Red"]e100[/COLOR]: probe of 0000:07:08.0 failed with error -11
```

---

### Post by chili555 on 2011-05-19
> [    [COLOR="Red"]1.4[/COLOR]86962] e100 0000:07:08.0: (unregistered net_device): EEPROM corruptedThe numbers at the beginning are time-stamps; roughly 1.4 seconds after the BIOS handed over the machine to the boot sector, the operating system already hated the EEPROM. Mind if we proofread for you?```
cat /etc/modprobe.d/e100.conf
```

The line I quoted should have disappeared.

---

### Post by maxe on 2011-05-19
Please do proofread and correct! I don't know what I'm doing.

So now I entered into the Terminal: "cat /etc/modprobe.d/e100.conf" and it returned that line I put in the file:

```
options e100 eeprom_bad_csum_allow=1
```

---

### Post by chili555 on 2011-05-19
If that doesn't fix it, I'm just about out of talent/ideas/mojo. I suggest a new card. I hate solving problems by throwing cubic dollars at it, however, excellent NICs are available for $10-15.

---

### Post by maxe on 2011-05-19
Thanks.

I installed an old wireless card that says its firmware isn't available yet but that might eventually work perhaps. At least Ubuntu "saw" it right away and even says in the menu under Wireless "device not ready (firmware missing)".

Since that is off-topic, though, I will not post about it here. Thanks for your efforts. I may just try to get an ethernet-to-USB adapter and see if that works in a USB port.

---

### Post by maxe on 2011-05-20
I just wanted to update everyone. The ethernet card is apparently not dysfunctional.

Once I got a USB wireless adapter dongle to work, Ubuntu went on the Internet, updated itself, and by the second or third reboot had already figured out the LAN issue.

All of a sudden I noticed my eth0 connection was actually giving notices and I don't need the wireless adapter anymore!

:KS yaaaaaayyy! Ubuntu 11 is gr8 once you get it on task.

---

### Post by maxe on 2011-06-27
:confused: ****

Okay, so now what's happened is I took out the old hard drive, replaced it with a larger 3 Tb one and then I re-installed Ubuntu 11.04 on the new hard drive.

Everything broke the same way it had before on the previous install. And I fixed it the same way.

**First**, there was no Internet and no Unity visuals (it defaulted to classic Ubuntu visuals), so I used the wireless dongle.

**Then** it couldn't connect so I used "sudo service network-manager stop" and "sudo service network-manager start" and it caught the network and logged in properly.

**Then** I updated Ubuntu with all the updates and installed the driver for my graphics card and rebooted and this restored Unity OS.

But this time, having Unity and updates _didn't_ fix the eth0 port.

So now I have everything I had before only I am stuck using a wireless dongle to access the Internet. I would like my ethernet card to be useful again because I don't want to go wireless all the time. Any tips? Any guesses as to why the first time fixed the ethernet card? Since last month, was there a new update that contradicts my ethernet driver?

---

### Post by maxe on 2011-06-28
Just an idea would be nice.

---

