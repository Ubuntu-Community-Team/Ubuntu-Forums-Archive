---
title: "Can't access network at all!"
date: 2011-10-18
forum: Networking &amp; Wireless
---

### Post by zangler on 2011-10-18
My children use Edubuntu on an old Acer Travelmate 2410 laptop.  It has,  until recently, had an ethernet connection to my home network router  and they have been able to browse webpages.  Alas, this is no longer the  case.  All connectivity between this laptop and the router has been  lost.  I have read a few posts of a similar nature and have run sudo  lshw command (I think this might be useful-though it might as well be  written in a foreign language to me!)  Only reference to network is the  following:

*-network UNCLAIMED
description: Network controller
product: ENE Technology Inc
vendor: ENE Technology Inc
physical id: 9
bus info: pci@0000:06:09.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=176 maxlatency=3 mingnt=192

I have an old 3Com OfficeConnect Wireless 54Mbps 11g PC Card which I use  on another laptop (I know it works, although other laptop runs windoze)  and put it in slot of this laptop - is the sudo lshw output relating to  this wireless card or the built-in ethernet port?  Of course, it might  be something else entirely.

Needless to say, I can't get a wireless connection either!  Some posts I  have found suggest that this wireless card isn't really supported in  ubuntu/edubuntu, is this right?

So really there are two questions, how can I tell if my on-board wired ethernet has fried and if it has, can I use the wireless card as an alternative (if so, how)?

Any help would be very much appreciated.  Please be gentle, I'm not very good with ubuntu/edubuntu!

---

### Post by chili555 on 2011-10-18
Let's try to find out why the on-board is not working. Please run this command in a terminal and post the results:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by zangler on 2011-10-18
just repeats the username - do I run this as sudo?

---

### Post by zangler on 2011-10-18
Just did and no difference!

---

### Post by chili555 on 2011-10-18
Then let's try:```
lspci -nn
```

---

### Post by zangler on 2011-10-18
Hi Chili

I've got some output - many lines - and no mechanism for getting it into this page (lack of network!)

In summary, there's:

Host Bridge
VGA compatible controller
Display controller
5 USB controllers
PCI bridge
Multimedia Audio controller
ISA bridge
IDE interface
SMBus
Non-VGA unclassified device

Which one (if any) would be of use and I'll type the rest of the info...

Thank you for your help.

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:09.0 Non-VGA unclassified device [0000]: ENE Technology Inc Device [1524:1010] (rev 01)

---

### Post by chili555 on 2011-10-18
I see nothing here that resembles an ethernet device. I've Googled the pci.id [1524:1010] to no avail. I also looked at ENE Technology's website and they don't appear to make any ethernet devices. 

[http://www.ene.com.tw/en/product.asp](http://www.ene.com.tw/en/product.asp)

Have you Googled the exact model of your Acer to see what kind of ethernet devices they were supplied with? ENE is not a model I have ever encountered previously. Without more probing, I suspect the internal has expired.

If you'd like to try the 3Com, stick it in the slot and run and post:```
sudo pccardctl ident
```

---

### Post by zangler on 2011-10-18
just run sudo pccardctl ident and nothing happened - no output, just new line waiting for input...

However, I have managed to find previous lshw output of the onboard ethernet - don't know, but it might help.  I had posted a while back about a CDRom drive that was misbehaving and this was included in the output file.

*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 7
bus info: pci@0000:06:07.0
logical name: eth0
version: 10
serial: 00:0a:e4:f1:60:8c
size: 100Mbit/s
capacity: 100Mbit/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.13 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
resources: irq:20 ioport:3000(size=256) memory:b0100000-b01000ff

---

### Post by chili555 on 2011-10-18
What does this tell us?```
dmesg | grep 8139
dmesg | grep 06:07
sudo cat /var/log/syslog | grep 8139
```Thanks.

---

### Post by zangler on 2011-10-18
Ok.  First command returned:

[    0.581391] device-mapper: uevent: version 1.0.3

This had 8139 in red type.

Other two commands reported nothing at all - just new line waiting for input.

Please excuse me - I really appreciate your help, but I've got to head off to bed... Early start in the morning!  I hope to pick this up again tomorrow either before or after work.  Thank you for your help so far.

---

### Post by praseodym on 2011-10-18
Check with

```
lsmod

```
if there is at least one driver (8139too and 8139cp) loaded. If both are loaded, blacklist the wrong one and reboot:

```
echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
For your wireless device please show:

```
pccardctl info
iwconfig
rfkill list
lsusb
```

---

### Post by chili555 on 2011-10-18
Have a pleasant evening and I'll see you tomorrow.

8139 is the name of the device:> description: Ethernet interface
product: RTL-[COLOR="Red"]8139[/COLOR]/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.And also the driver:> autonegotiation=on broadcast=yes driver=[COLOR="Red"]8139[/COLOR]too driverversion=0.9.28 The system logs know nothing about either.

06:07 is part of the bus number:> bus info: pci@0000:[COLOR="Red"]06:07[/COLOR].0The logs know nothing about it either.

Oh, I see praseodym is here to take over. Good luck.

---

### Post by zangler on 2011-10-19
Hi Praseodym and Chili555

Here's the output from the commands you suggested:

> lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
cryptd                 19801  0 
aes_i586               16956  195 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
acer_wmi               23153  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
sparse_keymap          13666  1 acer_wmi
usb_storage            43946  1 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipt_REJECT             12512  1 
ipt_LOG                12784  5 
xt_limit               12541  7 
xt_tcpudp              12531  9 
ipt_addrtype           12535  4 
xt_state               12514  7 
psmouse                73312  0 
uas                    17676  0 
soundcore              12600  1 snd
ip6table_filter        12711  1 
ip6_tables             22545  1 ip6table_filter
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19024  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13106  1 nf_nat_ftp
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18125  1 iptable_filter
x_tables               21907  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  451033  3 
drm_kms_helper         40745  1 i915
drm                   184164  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915I couldn't find any reference to 8139, so didn't run the second command.

pccardctl info didn't return anything.

> iwconfig
lo        no wireless extensions.
> rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
> lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1e3d:2092  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubI really appreciate you both trying to help.

---

### Post by praseodym on 2011-10-19
Load the LAN module by hand and force it in future being loaded:

```
sudo modprobe -v 8139too
echo 8139too | sudo tee -a /etc/modules
```

---

### Post by zangler on 2011-10-19
After the first command, I was presented with the following response:

> insmod /lib/modues/2.6.38-11-generic/kernel/drivers/net/8139too.koAfter the second command, the following:

> 8139tooRebooted, but not noticed anything.

Checked with lsmod that 8139too was there and it was - size reported as 23208 and Used By 0.  No other reference to 8139 found.

---

### Post by praseodym on 2011-10-19
Remove (not edit) your current wired config and reboot.

---

### Post by zangler on 2011-10-19
Still nothing...  No wired network connections showing in GUI and no lights at ethernet socket.

---

### Post by praseodym on 2011-10-19
Try the other one:

```
sudo rmmod 8139too
sudo modprobe -v 8139cp
```

---

### Post by zangler on 2011-10-19
The first command produced no output.  The second...

> insmod /lib/modules/2.6.38-11-generic/kernel/drivers/net/8139cp.koRebooted, still nothing.

Am I missing something here?  When I rebooted, I ran lsmod and 8139too was showing.  Do I need to stop it from autoloading in future (if so, how) and do I need to autoload the 8139cp instead (again, if so, how)?

Thanks.

---

### Post by praseodym on 2011-10-19
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
Remove the "blacklist 8139cp", save and close. Sometimes this card works also with both drivers loaded:

```
echo 8139cp | sudo tee -a /etc/modules
```
remove the wired profile, and reboot. Now both modules should be loaded with "lsmod".

Can you install the package ethtool and show additionally:

```
sudo ethtool eth0
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by zangler on 2011-10-20
Here's the content of the blacklist file:

> # This file lists those modules which we don't want to be loaded by
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


Completed the second command and the output was:

> 8139cp

Rebooted and still no network connection.

Ran the sudo ethtool eth0 command and output was:

> sudo: ethtool: command not found

lsmod command returned:

> Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
cryptd                 19801  0 
aes_i586               16956  215 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
acer_wmi               23153  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
sparse_keymap          13666  1 acer_wmi
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipt_REJECT             12512  1 
ipt_LOG                12784  5 
xt_limit               12541  7 
xt_tcpudp              12531  9 
ipt_addrtype           12535  4 
xt_state               12514  7 
ip6table_filter        12711  1 
ip6_tables             22545  1 ip6table_filter
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
psmouse                73312  0 
nf_nat_ftp             12548  0 
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19024  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13106  1 nf_nat_ftp
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18125  1 iptable_filter
soundcore              12600  1 snd
serio_raw              12990  0 
x_tables               21907  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
8139cp                 22497  0 
8139too                23208  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  451033  3 
drm_kms_helper         40745  1 i915
drm                   184164  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915



---

### Post by praseodym on 2011-10-20
Install ethtool by double click:

32bit: [http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.37-1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.37-1_i386.deb)

64bit: [http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.37-1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/ethtool/ethtool_2.6.37-1_amd64.deb)

and show:
```
sudo ethtool eth0

```
again

---

### Post by zangler on 2011-10-20
Well, I downloaded the software you linked to, transferred it to the laptop via a USB Drive, double-clicked to install it and got the following:

> An unhandled error occured
There seems to be a programming error in the aptdaemon.  This is the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.I wish I knew what was going on...

---

