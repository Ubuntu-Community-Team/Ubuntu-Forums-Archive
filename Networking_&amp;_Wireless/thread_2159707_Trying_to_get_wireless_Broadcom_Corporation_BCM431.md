---
title: "Trying to get wireless Broadcom Corporation BCM4312 802.11b/g LP-PHY working"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by ofeyrpf on 2013-07-04
Hi, I installed the latest version of of Ubuntu yesterday and upgraded all packages.

I am trying to get my wireless network running. So far I have tried,
[PHP]0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
ofey@ofey-Inspiron-1545:~$ sudo apt-get purge firware-b43-installer
[sudo] password for ofey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firware-b43-installer
ofey@ofey-Inspiron-1545:~$ sudo apt-get install firware-b43-lphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firware-b43-lphy-installer
ofey@ofey-Inspiron-1545:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:b5:06:5f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
ofey@ofey-Inspiron-1545:~$ ^C

[/PHP]

Any help would be greatly appreciated,

Thanks

---

### Post by kc1di on 2013-07-04
Hi ofeyrpf and welcome to Ubuntu,

the easy way to install Broadcome 4312 driver is this: ```
go to software center >edit>softwaresoruces and click on additional drivers
```
activate the Broadcom STA driver.  then reboot and it should work for you. 
good Luck :)

P.S. you will have to be connected via ethernet (hard line ) to do that.

---

### Post by ofeyrpf on 2013-07-04
Hi,

Thanks for your reply, 

I went to

Software center>edit>software sources but can't see anything that says 'additional drivers'. The closest thing is a tab that says 'addtional software'. I don't see under any of the tabs Broadcom STA or anything about drivers.

Thanks for your help,

Shane

---

### Post by howefield on 2013-07-04
> **ofeyrpf said:**
> 
ofey@ofey-Inspiron-1545:~$ sudo apt-get purge firware-b43-installer
E: Unable to locate package firware-b43-installer
ofey@ofey-Inspiron-1545:~$ sudo apt-get install firware-b43-lphy-installer
E: Unable to locate package firware-b43-lphy-installer


You are mistyping the package names.

---

### Post by ofeyrpf on 2013-07-04
I found something in Software center>edit>system I did a search for there for Broadcom STA. There are two installs for Broadcom STA drivers and one is a common file. Not sure what the difference is so I am installing both.

---

### Post by ofeyrpf on 2013-07-04
I think the Broadcom STA driver is now installed but how do I activate it? Just reboot? I'll try that anyway.

---

### Post by howefield on 2013-07-04
I think you'll need the b43 driver.

---

### Post by ofeyrpf on 2013-07-04
Hi and thanks,

How do I get to the synaptic package manager?

Shane

---

### Post by ofeyrpf on 2013-07-04
It's installing

---

### Post by Hadaka on 2013-07-04
Hi, the sta driver you loaded blacklists some modules
you need for the b43 driver. I would suggest removing the
sta driver before loading the lpphy b43 driver..
please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then do..
```
sudo apt get install firmware-b43-lpphy-installer
sudo modprobe b43
```

---

### Post by ofeyrpf on 2013-07-04
hi I think the driver is now installed. I rebooted but not seeing any wireless connections. Thanks Shane

---

### Post by ofeyrpf on 2013-07-04
Sorry thought I'd included a screen shot with last post, but it didn't seem to work.
[ATTACH=CONFIG]244388[/ATTACH]

---

### Post by Hadaka on 2013-07-04
Hi,let's see what you might possibly have loaded
please post the output of,,
```
lsmod
rfkill list all
```
and did you try my suggestion in post#10 ?
thanks

---

### Post by ofeyrpf on 2013-07-04
Hi, Here it is,
[PHP]ofey@ofey-Inspiron-1545:~$ lsmod
Module                  Size  Used by
dm_crypt               23126  1 
joydev                 17694  0 
coretemp               13642  0 
gpio_ich               13384  0 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
snd_hda_codec_idt      70774  1 
microcode              23030  0 
snd_hda_intel          34063  3 
snd_hda_codec         135141  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
psmouse               102506  0 
lpc_ich                17145  0 
serio_raw              13216  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
bnep                   18240  2 
rfcomm                 47562  0 
parport_pc             32867  0 
snd_seq_midi_event     14900  1 snd_seq_midi
ppdev                  17114  0 
bluetooth             211812  10 bnep,rfcomm
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13254  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ums_realtek            18257  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
usb_storage            49288  1 ums_realtek
i915                  535221  3 
ahci                   25869  2 
libahci                27338  1 ahci
sky2                   59074  0 
drm_kms_helper         49259  1 i915
drm                   290059  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
wmi                    19257  1 dell_wmi
video                  19653  1 i915

[/PHP]

and for 

rfkill list all

[PHP]ofey@ofey-Inspiron-1545:~$ rfkill list all
ofey@ofey-Inspiron-1545:~$ 

[/PHP]

Thanks

---

### Post by Hadaka on 2013-07-04
ok,looks fine..please do the commands in
post #10
thanks.

---

### Post by ofeyrpf on 2013-07-04
HI,

I'm not sure that was too successful. Here's the otuput,
[PHP]ofey@ofey-Inspiron-1545:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for ofey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ofey@ofey-Inspiron-1545:~$ sudo apt get install firmware-b43-lpphy-installer
sudo: apt: command not found
ofey@ofey-Inspiron-1545:~$ sudo modprobe b43
ofey@ofey-Inspiron-1545:~$ 

[/PHP]
Thanks,

Shane

---

### Post by howefield on 2013-07-04
You need to be careful with typing commands, apt get is hyphenated.

```
sudo apt-get install firmware-b43-lpphy-installer
```

---

### Post by Hadaka on 2013-07-04
Hi, to avoid typo's please COPY and paste
one command at a time into a terminal...
```
sudo apt-get autoremove
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe b43
```

---

### Post by ofeyrpf on 2013-07-04
I actually did copy and paste but I still should have looked at it. More success this time. This is part of the output from 

sudo apt-get install firmware-b43-lpphy-installer [PHP]Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw
ofey@ofey-Inspiron-1545:~$ sudo modprobe b43
ofey@ofey-Inspiron-1545:~$ 
[/PHP]
What now?

---

### Post by Hadaka on 2013-07-04
It should be working..
BOOT and post the output of..
```
lsmod
ifconfig
```
thanks.

---

### Post by ofeyrpf on 2013-07-04
Hi,
I rebooted first but still not picking up any wireless networks.
[PHP]ofey@ofey-Inspiron-1545:~$ lsmod
Module                  Size  Used by
dm_crypt               23126  1 
joydev                 17694  0 
coretemp               13642  0 
gpio_ich               13384  0 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
microcode              23030  0 
snd_hda_codec_idt      70774  1 
snd_hda_intel          34063  3 
snd_hda_codec         135141  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
psmouse               102506  0 
serio_raw              13216  0 
lpc_ich                17145  0 
snd_seq_midi           13325  0 
ums_realtek            18257  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
mac_hid                13254  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 47562  0 
parport_pc             32867  0 
bnep                   18240  2 
ppdev                  17114  0 
bluetooth             211812  10 rfcomm,bnep
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
usb_storage            49288  1 ums_realtek
sky2                   59074  0 
ahci                   25869  2 
libahci                27338  1 ahci
i915                  535221  3 
drm_kms_helper         49259  1 i915
wmi                    19257  1 dell_wmi
drm                   290059  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
video                  19653  1 i915
ofey@ofey-Inspiron-1545:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr a4:ba:db:b5:06:5f  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:feb5:65f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1007355 (1.0 MB)  TX bytes:113087 (113.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17414 (17.4 KB)  TX bytes:17414 (17.4 KB)

ofey@ofey-Inspiron-1545:~$ 

[/PHP]
Thanks

---

### Post by Hadaka on 2013-07-04
post the output of..
```
sudo modprobe -rf b43
sudo modprobe b43
dmes[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][/COLOR]g | grep b43
```
thanks

---

### Post by kc1di on 2013-07-04
I've never had good sucess using the b43 drivers for the 4312 chipset.  take a look at the Wiki[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"]
[/URL]

Notice this section: > wl - Proprietary Broadcom STA Wireless driver 

For Chip ID BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, BCM43227 and BCM43228.

Install either bcmwl-kernel-source (instructions below) OR the broadcom-sta (instructions at [http://wiki.debian.org/wl](http://wiki.debian.org/wl)) packages.

I've always had STA /WL working with that card.

---

### Post by ofeyrpf on 2013-07-04
[PHP]ofey@ofey-Inspiron-1545:~$ sudo modprobe -rf b43
[sudo] password for ofey: 
ofey@ofey-Inspiron-1545:~$ sudo modprobe b43
ofey@ofey-Inspiron-1545:~$ dmesg | grep b43
[ 2961.594975] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 2961.821494] Registered led device: b43-phy0::tx
[ 2961.821514] Registered led device: b43-phy0::rx
[ 2961.821531] Registered led device: b43-phy0::radio
[ 2962.120280] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
ofey@ofey-Inspiron-1545:~$ 

[/PHP]
Dave I thought I had installed the STA packages.

---

### Post by Hadaka on 2013-07-04
ok, it should be working..
lets see ..
```
lsmod
iwlist wlan0 scan
```
thanks

---

### Post by Hadaka on 2013-07-04
@kc1di
Hi,, about 1/2 of those cards now take the linux-firmware-nonfree
kernel changes and version changes..and just to keep us guessing changes :D
i show the bcm 4315 lp-phy with wl
but the bcm 4312 lp-phy b43
when and if lsmod gets populated..we shall see...

---

### Post by ofeyrpf on 2013-07-04
[PHP]ofey@ofey-Inspiron-1545:~$ lsmod
Module                  Size  Used by
arc4                   12530  2 
b43                   379088  0 
mac80211              555272  1 b43
cfg80211              208382  2 b43,mac80211
ssb                    53131  1 b43
bcma                   35762  1 b43
dm_crypt               23126  1 
joydev                 17694  0 
coretemp               13642  0 
gpio_ich               13384  0 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
microcode              23030  0 
snd_hda_codec_idt      70774  1 
snd_hda_intel          34063  3 
snd_hda_codec         135141  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
psmouse               102506  0 
serio_raw              13216  0 
lpc_ich                17145  0 
snd_seq_midi           13325  0 
ums_realtek            18257  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
mac_hid                13254  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rfcomm                 47562  0 
parport_pc             32867  0 
bnep                   18240  2 
ppdev                  17114  0 
bluetooth             211812  10 rfcomm,bnep
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
usb_storage            49288  1 ums_realtek
sky2                   59074  0 
ahci                   25869  2 
libahci                27338  1 ahci
i915                  535221  3 
drm_kms_helper         49259  1 i915
wmi                    19257  1 dell_wmi
drm                   290059  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
video                  19653  1 i915
ofey@ofey-Inspiron-1545:~$ iwlist wlan0 scan
wlan0     No scan results

ofey@ofey-Inspiron-1545:~$ 

[/PHP]

---

### Post by Hadaka on 2013-07-04
ok, atleast this time the lsmod is populated..
post the output of...
```
lspci -n | grep 0280
```
which we should have done at the start..
thanks.

---

### Post by ofeyrpf on 2013-07-04
[PHP]ofey@ofey-Inspiron-1545:~$ lspci -n | grep 0280
0c:00.0 0280: 14e4:4315 (rev 01)

[/PHP]

---

### Post by Hadaka on 2013-07-04
ok, we do need to load the wl driver...
please COPY and paste
```
sudo modprobe -rf b43
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
if the wireless isnt working after the above 
then do..
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe wl
```
report any errors.
thanks.

---

### Post by kc1di on 2013-07-04
Thanks for jumping in Hadaka I had to leave this morning.  Also he may want to check ```
rfkill list
``` just to make sure there is not a
hardware block in place. 
Cheers!

---

### Post by ofeyrpf on 2013-07-04
Hi,

It's working thanks for all your help. I am not too sure what was done to get it working but I am happy that it is. I'll look up the commands and see what we did.

Thanks again your help is very much appreciated,

Shane

---

### Post by Hadaka on 2013-07-04
GREAT !..glad it is working !!
Here is some info for you...
your wireless card. 
**BCM4312 802.11b/g LP-PHY [14e4:4315]**

requires the wl driver...bcmwl-kernel-source..

for some unknown reason..i was chasing 4312 driver...so be advised
the BCM4312 is just the card number....the number to determine the driver is [14e4:4315]...wl
so once i had you dump the lspci -n | grep 0280 (wireless card), which is usually my first request
I saw that i was in error. I apologize for the time it took me to wake up.
Please mark your thread solved
How to-> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
be sure to edit the FIRST post of this thread to mark solved.
thanks.

---

