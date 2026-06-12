---
title: "Toshiba Satellite A505"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by LinuxFanBoi on 2009-12-06
While following [these instructions]("https://help.ubuntu.com/9.10/internet/C/connecting-wireless.html") for connecting my new toshiba satellite A505 to my wireless access point.

I do not get a list of any available access points.  I know for a fact that where I live there are about 15 access points that My wireless adapter can see while I'm booted into windows.

At the moment I'm doing the post install update, and I hope this resolves the issue,  but is there something else I need to do?

---

### Post by northd_tech on 2009-12-06
If that Toshiba Satellite happens to have a Realtek 8192SE wireless adapter, this seems to be the way to fix those:

[http://ubuntuforums.org/showpost.php?p=8437848&postcount=10](http://ubuntuforums.org/showpost.php?p=8437848&postcount=10)

If not, you should post the results of these commands:

```
lsmod

uname -a

lspci

lsusb

sudo lshw -C network
```

---

### Post by LinuxFanBoi on 2009-12-06
mine is RTL8191SE :(

---

### Post by LinuxFanBoi on 2009-12-06
> **LinuxFanBoi said:**
> mine is RTL8191SE :(

lsmod
```
Module                  Size  Used by
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
cbc                     4224  162 
cryptd                  8008  0 
aes_x86_64              8992  163 
aes_generic            28480  1 aes_x86_64
ecb                     3296  1 
binfmt_misc            10220  1 
ppdev                   8232  0 
dm_crypt               14888  0 
joydev                 13088  0 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
lp                     11908  0 
snd_hwdep               9352  1 snd_hda_codec
uvcvideo               65260  0 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
snd_pcm_oss            44704  0 
psmouse                57124  0 
snd_mixer_oss          18976  1 snd_pcm_oss
videodev               43360  1 uvcvideo
parport                40528  2 ppdev,lp
serio_raw               6596  0 
v4l1_compat            16804  2 uvcvideo,videodev
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
v4l2_compat_ioctl32    13344  1 videodev
led_class               5256  1 sdhci
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
x_tables               25832  1 ip_tables
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
usb_storage            65984  1 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
video                  23612  0 
output                  3680  1 video
r8169                  38884  0 
mii                     6368  1 r8169
intel_agp              32816  0 
```

uname -a
```
Linux Icarus 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 x86_64 GNU/Linux
```

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a28 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
04:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
04:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
04:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
04:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)

```

lsusb
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:3207 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
sudo lshw -C network
```
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:fd:54:fe
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:5000(size=256) memory:d3110000-d3110fff(prefetchable) memory:d3100000-d310ffff(prefetchable) memory:d3120000-d313ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d9300000-d9303fff

```

---

### Post by northd_tech on 2009-12-06
Yikes- that's 64-bit and I've been tearing my hair out for weeks with a 64-bit Toshiba Satellite P505D with the Realtek 8192E.  You might still get that 819**2SE** method to work though.

Have you got a working network cable connection available, or are both the ethernet "eth0" and the wireless dead?

Run these commands in a terminal and post the results here, too:

```
ifconfig

iwconfig

less /etc/modules
```How do you feel about installing 32-bit ubuntu and maybe running 32-bit Windows drivers under ndiswrapper to get wireless ubuntu?  That worked great for weeks on that 64-bit Toshiba until we "upgraded???" it...

---

### Post by LinuxFanBoi on 2009-12-06
> **northd_tech said:**
> Yikes- that's 64-bit and I've been tearing my hair out for weeks with a 64-bit Toshiba Satellite P505D with the Realtek 8192E.  You might still get that 8191SE method to work though.

Have you got a working network cable connection available, or are both the ethernet "eth0" and the wireless dead?

Run these commands in a terminal and post the results here, too:

```
ifconfig

iwconfig

less /etc/modules
```

How do you feel about installing 32-bit ubuntu and maybe running 32-bit Windows drivers under ndiswrapper to get wireless ubuntu?  That worked great for weeks on that 64-bit Toshiba until we "upgraded???" it...

Wired Ethernet works just fine.  

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1e:33:fd:54:fe  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fefd:54fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6317165 (6.3 MB)  TX bytes:475025 (475.0 KB)
          Interrupt:30 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```
less /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```

---

### Post by northd_tech on 2009-12-06
> **LinuxFanBoi said:**
> sudo lshw -C network
```
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:fd:54:fe
       size: 100MB/s
       capacity: 100MB/s
**       width: 64 bits**
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:5000(size=256) memory:d3110000-d3110fff(prefetchable) memory:d3100000-d310ffff(prefetchable) memory:d3120000-d313ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
**       width: 32 bits**
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d9300000-d9303fff

```
That seems a little weird (and 32-bit would actually be a blessing in disguise from my experience with these Realteks).  You've got 64-bit on that Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller, but it's showing 32-bit on the wireless- that could be the "r8169" module.

---

### Post by northd_tech on 2009-12-06
> **LinuxFanBoi said:**
> lsmod
```
Module                  Size  Used by

r8169                  38884  0 
mii                     6368  1 r8169

```

EDIT:  Whoops- that is your Ethernet module- don't remove it.  If you already did, just run this 
```
sudo insmod r8169
sudo insmod mii
sudo depmod -a
```

You might need to restart after that to re-initialize the modules (sorry about that).

It doesn't look like we need to change /etc/modules, but that command would be

```
sudo gksu gedit /etc/modules
```if we did need to.  Then I'd try following chili555's method that I linked above that works for the 8192SE.

Otherwise, you need to start looking for some 64-bit drivers for either XP, Vista, or Win7 for that Realek 819**1SE**.

You might have the best luck going into your Windows Device Manager and checking the "Driver Properties"- you should only need 2 files there- *.inf and *.sys usually, but I'm not sure what they'll be called.

You should be able to mount your Windows partition under "Places" from ubuntu, but it will probably be easier to find the driver filenames under Windows.  Otherwise, you can extract the files from the proper Windows driver file if you can find the right one online.

Make sure you've got a "Wireless Windows Drivers" down at the bottom of the System>Administration> menu if you're still in ubuntu.  If it's not there, you can install ndiswrapper and wireless tools from the Synaptic Package Manager under System>Administration.

It looks like we can find you some Windows drivers here (or probably at Toshiba's website too):

[http://support.gateway.com/support/drivers/getFile.asp?id=23799&dscr=Realtek%208191SE%20Wireless%20Network%20Driver%20Version%202007.1.1002.2009](http://support.gateway.com/support/drivers/getFile.asp?id=23799&dscr=Realtek%208191SE%20Wireless%20Network%20Driver%20Version%202007.1.1002.2009)

[http://www.64bitdrivers.com/search.php?s=realtek](http://www.64bitdrivers.com/search.php?s=realtek)

---

### Post by LinuxFanBoi on 2009-12-06
Revised,

I downloaded the 64bid windows drivers,  added them to ndiswrapper and I get this;

[IMG]http://img704.imageshack.us/img704/7960/screenshotj.png[/IMG]

---

### Post by northd_tech on 2009-12-06
> **LinuxFanBoi said:**
> I found the files that my windows device manager uses for the wireless adapter drivers

They are rtl8192se.sys & vwifibus.sys

now what do I do with them?

See if you can find an "rtl8192se.inf" and a "vfiwibus.inf" hiding somewhere in your \Windows\ directory- those are the one(s) that you will actually point the System>Administration>Wireless Windows Driver (ndiswrapper applet) to to install those *.sys files.

You will want to copy all those to a directory or your ubuntu desktop and then probably move them to a /WifiDrivers directory under your home ubuntu directory ("cd ~") for future convenience.

There is a "ndiswrapper" thread pinned here for tips:

[http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper)

It sounded like chili555's method worked for the "native" linux 8192SE driver on this thread though (it's worth a shot- most people like that way better):

[http://ubuntuforums.org/showthread.php?t=1328209&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=1328209&highlight=ndiswrapper)

If you decide to use the windows drivers you will need to add this to your /etc/modules file so that you don't need to load ndiswrapper module manually each time:

```
sudo gksu gedit /etc/modules

```
Then add these lines at the bottom of that editor window, save the file, then close gedit:

```
# ndiswrapper loads the Windows wireless driver for the Realtek 8191SE WiFi interface
ndiswrapper
```

The Windows wireless drivers have worked on mine for over a year with a bunch of different Linuces, but I've got an easier Linux native driver for my Broadcom in the HP laptop.

---

### Post by northd_tech on 2009-12-06
Looking at that screenshot, I see that error every time using ndiswrapper- it might be a bug in the applet.

See if you can see "wlan0" now when you run "iwconfig" in a terminal or not.  If not- take a look at that pinned ndiswrapper thread- there are some commands to initialize your networking interface, and I don't remember those offhand as I haven't needed them.  I did need to actually build the ndiswrapper from source and insert the modules with an older version of ubuntu, but it didn't come with that Wireless Windows Drivers applet installed.

Have you tried clicking on that Network Manager icon to see if you can now connect to a wireless network or see your WiFi SSID?  It looks like your 64-bit drivers installed- that's how both of the Linux laptops that I've been using act (and they're both 64-bit, but we had much better luck with the 32-bit ubuntu on the Toshiba Satellite).  My HP seems much more forgiving (and it's a year older).

---

### Post by LinuxFanBoi on 2009-12-06
Okay I installed wireless utills, ndiswrapper & dependancies,  Got net8192se.inf and loaded it into ndiswrapper.  Still nothing is working,  If you scroll up ou can see a screenshot of what ndiswarpper tells me when I try to configure the driver.

Chili555's method bricked my machine once already, it seemed to work great until I did modprobe and thats when it killed my laptop.  Had to do a complete reinstall.

---

### Post by northd_tech on 2009-12-06
I never did find a 64-bit Windows driver that would work with that Toshiba P505D with the Realtek 8192E WiFi, but the 32-bit ubuntu with 32-bit WinXP drivers worked flawlessly for weeks.  I was going to try ndiswrapping some of those 32-bit drivers, but that was usually good for a hard systemLockup.

I'm not sure if it is a Windows driver or a ndiswrapper problem but it looks to be a 64-bit issue- maybe you should search the bug forum here for ndiswrapper or Realtek 8191/8192 and let the kernel gurus here know about it, and maybe point them to this thread.

The Toshiba that I've been working on has zapped its GRUB about 3 times now (Vista maybe, but it's after we've been in ubuntu and restart), but when I used the German page's 8192E method that you can find by searching my posts, I got a kernel module built and did get it to finally see "wlan0", but the Network Manager wireless were always grayed out or "disconnected" (before I got a bad case of the f*#kitz and went back to working on my HP and watching football).

I did find the right combination of yes & no that will install ubuntu and [mostly] "import" the earlier install.  Be sure you don't format the partition, and set the install partition **manually **to mount your existing ext3 or ext4 Linux partition when ubuntu calls GParted.  When I had to reinstall ubuntu on the Toshiba, it mainly just zapped the /bin and /sbin directories and left the /home stuff alone.  Make sure to set all the partitions as "used as" (as ext4 or NTFS for XP/Vista whatever).

I couldn't get my 1TB external to boot ubuntu though on my external USB drive (4 x 250GB partitions) with the HP when I installed that recently.  I had been running 64-bit Ultimate Ubuntu 2.3/Jackalope 9.04 off a USB stick, but Update Manager killed that for me too, so I tried to install to the big external drive.  I've moved all my stuff to the external drive for a fresh install, but I'm a little gun-shy of 64-bit and this new 9.10 (I had better luck with 8.10 and 9.04 ubuntu, especially in the 32-bit for wireless).  I'm still debating whether 64-bit is really worth it, and we have been trying to get some stuff to run under Wine (which also seemed better under 32-bit).

Good luck with that 64-bit, amigo.

---

### Post by LinuxFanBoi on 2009-12-06
Well by default,  Ubuntu recognises my adapters as 80101E/8102E.  Realtek's website has linux drivers for those,  I'm going to compile them and see if I can make something happen.

I refuse to use a 32 Bit OS,  Because doing so doesn't promote the development of 64 bit support for issues such at this.  It's a matter of principal.  I bought a LT with 4GB of ram,  I'm gonna get as much from it as I can.

I'm confident that a solution exists,  however convoluted and burried it may be.  If and when I find it I'll be sure to post it.  Perhaps I'm just SOL until support for this hardware becomes standard. 

With my experience with realtek hardware,  their driver support it pretty mediochre.

---

### Post by northd_tech on 2009-12-06
> **LinuxFanBoi said:**
> lspci
```

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)


```
I just noticed- it looks like lspci is calling yours a Realtek 8172 (not a 8191SE).  The RTL8101E is your wired connection (which seems to be working fine).

Did Windoze call that an 8172 or what exactly?  I seem to remember seeing a bunch of older threads about 8172 Realtek WiFi here (or maybe I'm thinking of a different number).  Have you searched for 8172 here?

Edit:  FWIW, Vista calls my Broadcom a 4321AG, and linux usually calls it "4321" but sometimes calls it "4328" depending upon the Linux flavor and/or day.  Of course this wireless interface is something of a "whore" and will use either the 4311, 4312, 4321, 4322, "b43", "STA", ndiswrapper, etc. in my HP and that "family" has much in common.  "Easy" can be a very good thing... ;)

The Realtek 8192E hasn't "played nice" under anything but 32-bit ubuntu on that Toshiba P505D so far.  Its cable connection has been a PITA too (that's an Atheros AR8132, IIRC- stay away from those if you can help it).

---

### Post by LinuxFanBoi on 2009-12-06
> **northd_tech said:**
> I just noticed- it looks like lspci is calling yours a Realtek 8172 (not a 8191SE).  The RTL8101E is your wired connection (which seems to be working fine).

Did Windoze call that an 8172 or what exactly?  I seem to remember seeing a bunch of older threads about 8172 Realtek WiFi here (or maybe I'm thinking of a different number).  Have you searched for 8172 here?

That's the first I've seen of this... In windows the device manger refers to my wireless adapter as an RTL8191se, however when viewing the driver details,  it says it's using RTL8192SE.

I'll do some more searching for 8172.  It seems the problem is that no one really knows what device I have... not even realtek.

---

### Post by LinuxFanBoi on 2009-12-06
Using this driver;

[http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz]("http://launchpadlibrarian.net/34090404/rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz")

I can now click on the network icon in the system tray and see a list of all available Access points,  Including mine.

When I try to connect it prompts me for a key,  I entered it and actualy was able to connect, but the network icon continued to show the spinning icon as if it never fully establishes the connection.  about 1 minute after fist connecting It again prompts me for my WEP key.

Any suggestions?

---

### Post by northd_tech on 2009-12-06
Have you got WPA supplicant and wireless-tools installed already?  I remember needing to add those to one of the older ubuntu builds that I did to get a working wireless connection.  You might be missing one of the authentication libraries or packages now.  

After I built the module for the Realtek 8192E and installed it, it could see "wlan0," but everything was grayed out.  That Toshiba's owner is a college student, and he was busy with some homework that he was doing under Vista (and GRUB needs some work, but I'm thinking of trying GRUB2 or LILO after this much GRUB trouble under Karmic 9.10).

Edit:  Some people have claimed that Wicd works better for them, but it will require you to uninstall Network Manager in Synaptic Package manager (and if you uninstall Wicd, you will need to manually install Network Manager again as it doesn't usually re-install Network Manager for you).

[http://en.wikipedia.org/wiki/Wicd_%28Linux_Network_Manager%29](http://en.wikipedia.org/wiki/Wicd_%28Linux_Network_Manager%29)

---

### Post by LinuxFanBoi on 2009-12-06
Yes, I have the WPA supplicant and wireless tools,  But I'm not ready to abandon network manager just yet.

The author of that 64bit driver has published a patch that may solve the problem,  But for the life of me, I cant figure out how to apply it, as it is not a script, it's just a text file with code in it.

here's the link to the [bug report thread]("//https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all") that has gotten me where I am now..

Patch code
```
diff -urp rtl8192se_linux_2.6.0010.1113.2009/HAL/rtl8192/rtl_core.c rtl8192se_linux_2.6.0010.1116.2009/HAL/rtl8192/rtl_core.c
--- rtl8192se_linux_2.6.0010.1113.2009/HAL/rtl8192/rtl_core.c	2009-11-13 16:21:48.000000000 +0800
+++ rtl8192se_linux_2.6.0010.1116.2009/HAL/rtl8192/rtl_core.c	2009-11-16 10:50:21.000000000 +0800
@@ -2645,13 +2645,11 @@ void rtl819xE_tx_cmd(struct net_device *
     struct rtl8192_tx_ring *ring;
     tx_desc_cmd* entry;
     unsigned int idx;
-    dma_addr_t mapping;
     cb_desc *tcb_desc;
     unsigned long flags;
 
     spin_lock_irqsave(&priv->irq_th_lock,flags);
     ring = &priv->tx_ring[TXCMD_QUEUE];
-    mapping = pci_map_single(priv->pdev, skb->data, skb->len, PCI_DMA_TODEVICE);
 
     idx = (ring->idx + skb_queue_len(&ring->queue)) % ring->entries;
     entry = (tx_desc_cmd*) &ring->desc[idx];
@@ -2678,12 +2676,10 @@ short rtl8192_tx(struct net_device *dev,
     tx_desc *pdesc = NULL;
     struct ieee80211_hdr_1addr * header = NULL;
     u16 fc=0, type=0,stype=0;
-    dma_addr_t mapping;
     bool  multi_addr=false,broad_addr=false,uni_addr=false;
     u8*   pda_addr = NULL;
     int   idx;
     u32 fwinfo_size = 0;
-    mapping = pci_map_single(priv->pdev, skb->data, skb->len, PCI_DMA_TODEVICE);
 
     priv->ieee80211->bAwakePktSent = true;
```

---

### Post by northd_tech on 2009-12-07
I'm no expert on patching kernels, but I remember a "patch" command.  Here is a HOWTO on that:

[http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

Will you give me a shout if you see anything about a patch for a Realtek 81**92E** (as in not 8192SE) wireless in your travels- that still has me stumped for the 64-bit?

---

### Post by LinuxFanBoi on 2009-12-07
> **northd_tech said:**
> I'm no expert on patching kernels, but I remember a "patch" command.  Here is a HOWTO on that:

[http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

Will you give me a shout if you see anything about a patch for a Realtek 81**92E** (as in not 8192SE) wireless in your travels- that still has me stumped for the 64-bit?

Visit the launchpad thread that I linked above,  David Woo seems to be the resident guru, and could probably help you.

---

### Post by LinuxFanBoi on 2009-12-07
Save yourself the aggravation everyone,  Just e-mail the tech support guys at Realtek, and ask them for their most recent Linux driver.  I cant post it because it's technically a non-free driver,  but they will give it to you without any issues.  They are wicked fast on the response time too.

---

### Post by northd_tech on 2009-12-19
[SIZE=2]I contacted Realtek, and they emailed me a driver (very quickly- about 1 hour tops) that is supposed to work with an AMD 64-bit duo-core system. 

The "make" command went smoothly, but several errors when I tried "sudo make install."  I tried "Method 2" (direct copy of the newly built firmware directory) from the Realtek README file, but Network Manager shows "device not ready" under Wireless Connections. I'm in an email loop with their tech and will advise if I get the Toshiba P505D working.

Here are the compiler errors from "sudo make install" (sorry- the fonts got strange in all the email translation):
[/SIZE]> [FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=3][COLOR=#007f40][COLOR=#007f40]make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
    CHK     include/linux/version.h
    CHK     include/linux/utsrelease.h
    UPD     include/linux/utsrelease.h
    SYMLINK include/asm -> include/asm-x86
  make[3]: *****[B] No rule to make target   `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.**[/B]
  make[2]: *** [prepare0] Error 2
  make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
  make[1]: *** [modules] Error 2
  make[1]: Leaving directory `/home/xxxx/[/COLOR][/COLOR][/SIZE][/FONT][SIZE=2]Here is a snippet of "lsmod" that indicates the 8192E module inserted:
[/SIZE]> [FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=3][COLOR=#00bf60][COLOR=#00bf60]Module                    Size  Used by
  **[B]r8192e_pci              362376  0 **[/B]
  binfmt_misc              10220  1 
  ppdev                     8232  0 [/COLOR][/COLOR][/SIZE][/FONT][SIZE=2]
"ifconfig":
[/SIZE]> [FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=3][COLOR=#00bf60][COLOR=#00bf60]eth0        Link encap:Ethernet  HWaddr 00:26:9e:17:fb:37  
            inet   addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
            inet6 addr:   fe80::226:9eff:fe17:fb37/64 Scope:Link
            UP BROADCAST RUNNING   MULTICAST  MTU:1500  Metric:1
            RX packets:1026   errors:0 dropped:0 overruns:0 frame:0
            TX packets:902   errors:0 dropped:0 overruns:0 carrier:1
            collisions:0   txqueuelen:1000 
            RX bytes:555615 (555.6   KB)  TX bytes:170947 (170.9 KB)
            Interrupt:30 
  
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1    Mask:255.0.0.0
            inet6 addr: ::1/128   Scope:Host
            UP LOOPBACK   RUNNING  MTU:16436  Metric:1
            RX packets:386   errors:0 dropped:0 overruns:0 frame:0
            TX packets:386   errors:0 dropped:0 overruns:0 carrier:0
            collisions:0   txqueuelen:0 
  [/COLOR][/COLOR]            RX bytes:59180 (59.1 KB)  TX bytes:59180 (59.1 KB)[COLOR=#00bf60][COLOR=#00bf60]
  
  virbr0    Link encap:Ethernet  HWaddr 26:0b:   5f :2e:03:8e  
            inet   addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
            UP BROADCAST RUNNING   MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0   dropped:0 overruns:0 frame:0
            TX packets:31 errors:0   dropped:0 overruns:0 carrier:0
            collisions:0   txqueuelen:0 
            RX bytes:0 (0.0   B)  TX bytes:4407 (4.4 KB)[/COLOR][/COLOR][/SIZE][/FONT][SIZE=2]"iwconfig":[/SIZE]
> [FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=3][COLOR=#00bf60][COLOR=#00bf60]lo          no wireless extensions.
  
  eth0      no wireless extensions.
  
  virbr0    no wireless extensions.
  
  [B][B]wlan0       802.11bgn  Nickname:"rtl8192E"
            Mode:Managed    Access Point: Not-Associated   Bit Rate:1 Mb/s   [/B][/B]
            Retry: on     RTS thr: off   Fragment thr: off
            Encryption key: off
            Power Management: off
            Link   Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
            Rx invalid   nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive   retries:0  Invalid misc:0   Missed beacon:0[/COLOR][/COLOR][/SIZE][/FONT][SIZE=2]I tried restarts, and also the[/SIZE] [FONT=&#26032;&#32048;&#26126;&#39636;][SIZE=3]**[B]sudo   ./wlan0down**[/B] then**[B] sudo ./wlan0up**[/B]   thing[/SIZE][/FONT] [SIZE=2]too...[/SIZE]
[SIZE=2]
I got the same results the second time when I tried to compile under the 2.6.31-14-generic kernel (after first trying with the 2.6.31.16-generic 9.10 Karmic kernel).  Still no love with the 64-bit Realtek 8192E wireless though...:(
[/SIZE]

---

### Post by northd_tech on 2010-02-06
It sounds like there might finally be a fix for the 81**92E** version from the manufacturer Realtek.

See these threads:

Realtek rtl8192e wireless not seen
[http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E](http://ubuntuforums.org/showthread.php?t=1239342&page=7&highlight=Realtek+8192E)

Realtek RTL8192 Wireless is not working
[http://ubuntuforums.org/showthread.php?t=1227061&highlight=Realtek+8192E&page=3](http://ubuntuforums.org/showthread.php?t=1227061&highlight=Realtek+8192E&page=3)

I'm still waiting for Realtek to email me the drivers, and I have a wedding to attend this weekend, a carburetor to change out, and a Super Bowl to watch if I get time- so I may not get a chance to test out the new 8192E drivers until later this week.

I will update this thread if I have any luck.

---

### Post by northd_tech on 2010-02-27
The newest driver that Realtek emailed me still does not work under 64 bit Karmic 9.10 (2.6.31-19-generic kernel).

The output of sudo make is:

> make -C /lib/modules/2.6.31-19-generic/build M= CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [modules] Error 2


---

### Post by nights815 on 2010-03-02
I would like to add into this topic.
I too also have an A505 "s6025". Same realtek wireless card. I have tried Ubuntu and Kubuntu 9.10 32 and 64 bit versions with 4 different drivers (rtl8192se_linux_2.6.0010.1012.2009.tar.gz and 
rtl8192se_linux_2.6.0013.1204.2009.tar.gz and
rtl8192se_linux_2.6.0014.0115.2010.tar.gz and
rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz)
the expreience wasnt fun. (Although thank you realtek for helping me memorize linux networking related commands) and (yes i did use the 64bit drivers for 64bit OS and 32 for 32bit OS)
I did email realtek and they just sent me a web link to download 2.6.0014.0115.2010.
I also tried installing windows drivers
8191_9192_SE_Windowsdriver_1085.23.1230.2009 and just for fun
8191_8192_se_win7_driver_2010.0.0119.2010
using win 2000 driver, xp, xp64 and even win98 drivers.
Still nothing. No signal. No scanning. But according to iwconfig or ifconfig the card exists
rtl8192seva2.
and it works just fine on windows. I wish this had a port available to change the card fast to something better. I am going to try purchasing a Belkin N1 Express-card with Atheros which was the chip-set i wanted originally but no Toshibas in Best buy had any with..
This is just one issue im having with this laptop and Ubuntu. Video and battery is another

---

### Post by c.pfarher on 2010-03-11
I posted a solution here:
[http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html]("http://kikipblog.blogspot.com/2010/03/realtek-8172-de-toshiba-a505-s69803-en.html")
good luck!

---

