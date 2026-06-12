---
title: "Atheros wireless on Acer 4736ZG fails to connect"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by zak_wang on 2009-11-20
Hi, all

I'm new in this forum. Greetings!

Ubuntu 9.10 Karmic Koala is running on my Acer 4736ZG and everything, except for the lovely wireless connection, works perfectly.

Here is the information from lspci:

04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a32:0306
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at 99200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

In the first few minutes after a fresh boot up, the wireless connection is automatically connected, but with very low speed. And then it refuses to work. I repeat to click, wait, fail, click, wait, fail...

It's so irritating when I need some information from the Internet and have to switch back to the boring Windows for help. (Not trying to say Windows is bad. Just personal preference)

I'm posting here in my hotel through wired connection. As I said, everything works perfectly, with wired connection there. But I could only get access to the Internet through wireless network when I work in the company. And that hurts.

Wish there are fellows in here having had the same issue and solved it. Please help me out of this. If you need more information, please ask for it.

Thanks.

Zak

---

### Post by coffeecat on 2009-11-20
I come bearing good tidings. I am posting from an Acer Aspire 7540 running Karmic and with:

```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```... the identical wireless chipset to yours. The connection is fast and stable - now. Like you with a default install the connection was weak and soon disconnected and wouldn't reconnect. All I did was to install the packages:

linux-backports-modules-2.6.31-14-generic
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

You need to reboot and then you should be OK.

**Edit:** of course, you will probably want to use the wired connection to do the install of the modules. And you don't need the backports repository enabled. Although they have 'backports' in the package name, they're in the main repository. :?

---

### Post by zak_wang on 2009-11-20
That's delicious!

I do think this will just work out for me because we are having the same model here. But I could only try out by tomorrow at work. I'll post back here then with my results.

Thanks.

Zak

---

### Post by zak_wang on 2009-11-20
Now I come back with good tidings :p

Signal improved from 30% yesterday to a stable 70+% today. Very nice connection. Backports guys are a maze!

Internet speed is not fast as normal though, I don't need to spend that many minutes to restart and boot into another OS.

Thanks a million!

Zak

---

### Post by neoanderthal on 2009-11-21
yes, thank you so much! I've been struggling with Linux on a Toshiba NB205 with the same wireless radio, and I'm hoping that those days are over!

Everything seems to be working fine - thanks again!

---

### Post by jeannacav on 2009-11-21
OK this looks very hopeful.
I am too new to linux to understand some commonly used words etc.

Is my **_kernel_** jaunty? (I didn't upgrade yet)

I used these instrux the other day

> ------
cd Desktop
tar -xf compat-wireless-2.6.30.tar.bz2
cd compat-wireless-2.6.30
make
sudo make install
sudo make unload 

======================
from:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

-------

I will do all this again but this time I will use the 2.6.31 version, but when I was finished the other day it worked until I rebooted after the most recent update. 

No one has answered this yet.
**Where does this folder go/or belong when it is finished?**

**Should I just drop it into the file system folder?**
(Mine ended up on my desktop, and I do not know if that is my problem?? or the choice of the wrong backports?)

Thank you for any help,

jeanna

---

### Post by The Dragon Master on 2009-11-22
> **jeannacav said:**
> 
Is my **_kernel_** jaunty? (I didn't upgrade yet)


System | About Ubuntu

or 

lsb_release -a

or 

cat /etc/lsb-release

Upgrading from Jaunty to Karmic didn't solve my wireless woes though.

> **jeannacav said:**
> 
**Where does this folder go/or belong when it is finished?**

**Should I just drop it into the file system folder?**
(Mine ended up on my desktop, and I do not know if that is my problem?? or the choice of the wrong backports?)


You can unzip that tarball anywhere you like, but normally the desktop is not a good idea cause you don't want too much clutter there. I use a /home/david/downloads folder, or perhaps clearer would be a /home/david/src folder.

---

### Post by The Dragon Master on 2009-11-22
> **coffeecat said:**
> 
linux-backports-modules-2.6.31-14-generic
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

You need to reboot and then you should be OK.

**Edit:** of course, you will probably want to use the wired connection to do the install of the modules. And you don't need the backports repository enabled. Although they have 'backports' in the package name, they're in the main repository. :?

Thanks for the sugfgestion, I don't have a wired connection, but I do have another laptop running a chinese version of XP so I could get the four .deb packages above and do a dpkg -i with them. Didn't solve my problem though.

In brief my problem is: 
1)lshw shows my AR928X wireless adaptor as disabled, 
2) ifconfig doesn't even show the wlan0,
3) a "ifconfig wlan0 up" returns an error

In detail...

$ sudo lshw
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 memory:fdf00000-fdffffff
           *-network DISABLED
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:22:43:51:b2:6b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 memory:fdff0000-fdffffff

$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

$ uname -a
Linux wert 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Unknown error 132
SIOCSIFFLAGS: Unknown error 132
Listening on LPF/wlan0/00:22:43:51:b2:6b
Sending on   LPF/wlan0/00:22:43:51:b2:6b
Listening on LPF/eth0/00:23:54:ef:da:51
Sending on   LPF/eth0/00:23:54:ef:da:51
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9

$ tail -f /var/log/syslog
Nov 22 13:33:24 wert dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Nov 22 13:33:24 wert dhclient: send_packet: Network is down
Nov 22 13:33:26 wert dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 22 13:33:27 wert dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Nov 22 13:33:27 wert dhclient: send_packet: Network is down
Nov 22 13:33:31 wert dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Nov 22 13:33:32 wert kernel: [  319.108049] eth0: auto-negotiating...
Nov 22 13:33:42 wert kernel: [  329.132042] eth0: auto-negotiating...
Nov 22 13:33:52 wert kernel: [  339.156044] eth0: auto-negotiating...


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:ef:da:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
joydev                 10272  0 
psmouse                56180  0 
serio_raw               5280  0 
ath_pci               203476  0 
wlan                  226448  1 ath_pci
ath_hal               303104  1 ath_pci
ppdev                   6688  0 
lp                      8964  0 
arc4                    1660  2 
uvcvideo               59080  0 
ecb                     2524  2 
ath9k                 307384  0 
mac80211              210408  1 ath9k
ath                     8444  1 ath9k
videodev               36736  1 uvcvideo
parport                35340  2 ppdev,lp
sis190                 17824  0 
asus_laptop            17400  0 
v4l1_compat            14496  2 uvcvideo,videodev
mii                     5212  1 sis190
snd_hda_codec_realtek   203328  1 
cfg80211              130440  3 ath9k,mac80211,ath
led_class               4096  2 ath9k,asus_laptop
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
iptable_filter          3100  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usb_storage            52544  0 
video                  19380  0 
output                  2780  1 video
radeon                636000  1 
ttm                    36212  1 radeon
drm                   159584  3 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  0 
agpgart                34988  3 ttm,drm,sis_agp


Did I forget anything?

---

### Post by The Dragon Master on 2009-11-22
bump

---

### Post by FunkeyMonk on 2009-11-23
> **coffeecat said:**
>  All I did was to install the packages:

linux-backports-modules-2.6.31-14-generic
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

You need to reboot and then you should be OK.

**Edit:** of course, you will probably want to use the wired connection to do the install of the modules.

Worked like a charm for me and my Toshiba Satellite.
For those of you who don't want to go searching for ethernet cables, I managed to install these packages by booting into the 2.6.28-16-generic, which had my wireless working perfectly.  I installed the four packages using Synaptic Package Manager, rebooted into 2.6.31-15-generic, and everything's peachy!

Thanks very much, Coffeecat

---

### Post by coffeecat on 2009-11-23
Just a clarification for any newbies happening along who wonder why they can't boot into the 2.6.28 kernel....

> **FunkeyMonk said:**
> I managed to install these packages by booting into the 2.6.28-16-generic,

.... you'll only have the 2.6.28 kernel if you did a dist-upgrade from Jaunty, not a fresh install of Karmic. And...

> **FunkeyMonk said:**
> rebooted into 2.6.31-15-generic

I hope that's a typo for 2.6.31-14, and that you haven't enabled the proposed repository. [-X

:wink:

---

### Post by thrud00 on 2009-11-25
Brilliant ! Worked for me on an Acer 5542. The wifi always worked, but died  2-10 minutes after boot. 

After trying madwifi, which didn't help I was tearing my hair trying to get wifi to work reliably. All, my other laptops inlcuding the wife's dell and my two work Thinkpads, just worked OFTB.

Wifi now stable at last. By the way, I did have the proposed updates enabled, so I am on 2.6.31-15.

Thanks much !

Steve

---

### Post by FunkeyMonk on 2009-11-29
> **coffeecat said:**
> I hope that's a typo for 2.6.31-14, and that you haven't enabled the proposed repository.

No, it wasn't a typo for -14 vs. -15... but thanks for scolding me on this one... I just turned off the Proposed repo, added the -14 kernel back into my grub list, and now I no longer have crashing problems!

Hooray!

(Although -15 boots MUCH faster than -14 on my machine....)

---

### Post by coffeecat on 2009-11-30
> **FunkeyMonk said:**
> No, it wasn't a typo for -14 vs. -15... but thanks for scolding me on this one...

Not a scold - just a gentle prod. :wink: But since I posted that comment, the -15 kernel has come through on the routine upgrades. Some people are reporting problems - most people are probably OK. I've used the -15 kernel now on three different machines with no problem. Whatever - tread with caution. Good luck.

---

### Post by Statik on 2009-12-11
As for the question as to where the directory goes, once you have your wireless working, you can delete the folder and the tar. They were only needed to build and install the driver. Once its installed, its located elsewhere.

Statik

---

### Post by gitmo333 on 2009-12-14
Hello coffeecat,
my wifi wouldn't resume after suspend/hibernate until i followed your instructions. For a while it felt like everything was fine; then i upgraded to 2.6.31-16 due to update manager's insistence and now i find that the won't-resume-after-suspend/hibernate problem has recurred!
I removed the new kernel, so I'm back to 2.6.31-14 but now Synaptics only shows the versions of the following packages for kernel -16! How do i obtain the backports corresponding to kernel v-14?
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

---

### Post by coffeecat on 2009-12-14
> **gitmo333 said:**
> my wifi wouldn't resume after suspend/hibernate until i followed your instructions. For a while it felt like everything was fine; then i upgraded to 2.6.31-16 due to update manager's insistence and now i find that the won't-resume-after-suspend/hibernate problem has recurred!
I removed the new kernel, so I'm back to 2.6.31-14 but now Synaptics only shows the versions of the following packages for kernel -16! How do i obtain the backports corresponding to kernel v-14?
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

A few points. This thread is about unreliable connections with the AR928X Wireless chipset not necessarily associated with suspend.resume. Your problem sounds a little different, and you don't say what wireless chipset you have. 

The 2.6.31-16 kernel, together with the corresponding backported modules, works just fine for me with my AR928X wireless. As did the -15 kernel. If you boot into the -14 kernel, you will still have the -14 backported modules - they won't have been removed - so, if you are still getting your problem, my guess is that the cause is something else entirely.

First thing: let's check to see what wireless chipset you do have. Please post the make and model of your computer. Is it a desktop or laptop? Now open a terminal. If you have an inbuilt wireless card, post the output of:

```
lspci
```Or if you have a usb wireless device, post the output of:

```
lsusb
```Or if you have a pcmcia wireless card, post the output of:

```
lspcmcia
```**Edit:** when I said in my first post in this thread that I had installed the package linux-backports-modules-2.6.31-14-generic, I see now that that was unnecessary and a bit misleading. If you install the metapackages linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic they will bring in the appropriate -15, -16, whatever, backports modules with the newer kernel. The old backports will not be uninstalled unless you uninstall the older kernel. In fact you did not have to uninstall the -16 kernel to be able to use the -14 kernel. Each version of the kernel's modules (drivers) are kept in discrete folders - they do not interfere with each other. And each kernel image is a separate file in /boot. They do not interfere with each other.

Do you have linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic marked as installed? If you do you should have all the backported modules installed for any installed kernel. In fact, you probably only need one of those two packages.

---

### Post by rahnen on 2009-12-14
CoffeeCat your the Bomb!
I loaded the (4) backport files via Synaptic like you suggested and I am connected long and strong.
THANKS!!!!!!!!
Gateway NV53
Karmic 64bit
Atheros AR5B93 Chipset
:D

---

### Post by ltsampros on 2009-12-26
CofeeCat, Thank you very much on your proposed solution. It works great on my Acer Ferrari One using 9.10!

You rock! :guitar:

---

### Post by llawwehttam on 2010-01-28
Wow thanks coffeecat. I am running karmic and was getting very annoyed with disconnected wifi. Also when I was using an Ethernet the wifi used to start doing wierd things and trying to take over but the backports seem to have fixed that as well. Thanks a lot.

---

### Post by XxBJDxX on 2010-04-23
thank you very much, worked on my acer aspire 5532.
wireless kept dropping out after about 5-10 mins of being connected, after this, it never drops, thank you!!

---

### Post by Narendran95 on 2010-12-05
Hey... I'm using Ubuntu 10.10 Maverick Meerkat on a TOSHIBA Satellite Pro L510 and I have the same problem... I saw that coffecat's problem was for Karmic... How do you do it on Maverick?

---

### Post by coffeecat on 2010-12-05
> **Narendran95 said:**
> I have the same problem

Do you? The Atheros AR928X chipset that is the subject of this thread works out of the box in Maverick. What wireless chipset do you have? If you don't know it you can find out from the output of lspci.

---

### Post by theterabyteboy on 2011-11-01
> **coffeecat said:**
> I come bearing good tidings. I am posting from an Acer Aspire 7540 running Karmic and with:

```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```... the identical wireless chipset to yours. The connection is fast and stable - now. Like you with a default install the connection was weak and soon disconnected and wouldn't reconnect. All I did was to install the packages:

linux-backports-modules-2.6.31-14-generic
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

You need to reboot and then you should be OK.

**Edit:** of course, you will probably want to use the wired connection to do the install of the modules. And you don't need the backports repository enabled. Although they have 'backports' in the package name, they're in the main repository. :?
Hi Coffeecat,

I appear to be having a similar issue with my wireless card disconnecting in Ubuntu 11.10.  I am using a Lenovo T520 laptop.

here is the output from lspci:
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 1057 (rev a1)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 04)

Which packages should I install?
Thank you for your help!

---

### Post by coffeecat on 2011-11-01
@theterabyteboy, this is an old thread concerning an Atheros wireless device in a now obsolete version of Ubuntu (9.10). You are running..  

> **theterabyteboy said:**
> Ubuntu 11.10.

... and you have a...

> **theterabyteboy said:**
> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

Please start your own thread with a relevant title to your situation and don't forget to post this information. 

I'll request another member of staff to close this thread.

---

### Post by Elfy on 2011-11-01
Closed

---

