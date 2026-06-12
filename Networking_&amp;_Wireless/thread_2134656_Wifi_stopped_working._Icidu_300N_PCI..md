---
title: "Wifi stopped working. Icidu 300N PCI."
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by PGJSmit on 2013-04-11
Hi Guys,

During the installation of 12.04 I had WiFi up and running downloading updates. Then when I activated the AMD Radeon drivers and rebooted the WiFi stopped working! I think my WiFI card, Icidu 300N PCI, uses a Atheros AR5008 chip.

I really hope you can steer me in the right direction.

[B]1 ) Machine Brand and Model (PC/Laptop):
[/B]Build from components myself. AMD A10-5800K processor, Asus F2A85-M LE motherboard,  Icidu 300N PCI WiFi card. I guess the hard drive etc. are not very important.

**2 ) Wireless Brand, Model and Wireless Chipset:**
01:05.0 Ethernet controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

**3 ) check interface:**
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:a4:4c:3d:54:0b  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::62a4:4cff:fe3d:540b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6028 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6572387 (6.5 MB)  TX bytes:672430 (672.4 KB)
          Interrupt:53 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122416 (122.4 KB)  TX bytes:122416 (122.4 KB)


$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.



**4 ) Check for modules:**
d$ lsmod
Module                  Size  Used by
vesafb                 13516  1 
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
i2c_piix4              13093  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
hid_logitech           22024  0 
psmouse                86520  0 
snd_hwdep              13276  1 snd_hda_codec
ff_memless             12945  1 hid_logitech
serio_raw              13027  0 
k10temp                12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
fglrx                2909978  115 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17830  2 
mac_hid                13077  0 
rfcomm                 38139  0 
snd                    62218  15 snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
bluetooth             158479  10 bnep,rfcomm
parport_pc             32114  1 
wmi                    18744  1 asus_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39683  0 
usbhid                 41937  1 hid_logitech
hid                    77428  2 hid_logitech,usbhid
r8169                  56368  0 

**5 ) Kernel boot messages:**
There is no mention of any wlan0 or similar device. It does mention eth0 a few times.

**6 ) Network configuration:** 
 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: memory:fea00000-fea0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 09
       serial: 60:a4:4c:3d:54:0b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168f-1_0.0.4 03/27/12 ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:53 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff

[B]7 ) Scan for networks:
[/B]It tells me there are no devices that support scanning

[B]8 ) Ubuntu Version:
[/B]Description:	Ubuntu 12.04.2 LTS

**9 ) Kernel/architecture (including 32 vs. 64 bit):**
3.2.0-40-generic-pae i686

[B]10 ) Restarting the network:
[/B]Does not change anything.

---

### Post by Hadaka on 2013-04-11
Hi, please do..
```

sudo apt-get install --reinstall linux-image-$(uname -r)
sudo apt-get update
sudo apt-get upgrade
sudo modprobe ath9k

```
the ath9k is the linux driver for your card.

---

### Post by PGJSmit on 2013-04-12
HHmmm... This is weird.

When I booted this morning WiFi was working again. Guessing the drivers where unstable I followed your steps, rebooted, now WiFi is not working again :(

If I run: sudo modprobe ath9k
No output apprears. Is this normal?


EDIT:
Ok I see a pattern: After a "cold" boot (shutting down completely) WiFi works, after a "warm" boot (selecting reboot in the menu) it doesn't.

---

### Post by Hadaka on 2013-04-12
Hi, did you also do..
```
sudo apt-get update
sudo apt-get upgrade
```
and does wireless return on a warm boot
if you do..
```
sudo modprobe ath9k
```
if YES then please do..
```
sudo su
echo ath9k >> /etc/modules
exit
```
and yes no response on some commands means it accepted the command...
that is normal.
thanks.

---

### Post by PGJSmit on 2013-04-13
> **Hadaka said:**
> Hi, did you also do..
```
sudo apt-get update
sudo apt-get upgrade
```



Yes


> **Hadaka said:**
> 
and does wireless return on a warm boot



Unfortunately not.


> **Hadaka said:**
> 
if you do..
```
sudo modprobe ath9k
```
if YES then please do..
```
sudo su
echo ath9k >> /etc/modules
exit
```
and yes no response on some commands means it accepted the command...
that is normal.
thanks.


I don't understand this part. If I run the sudo modprobe ath9k command no reply is given. Not when wifi is working (after a boot from fully shutdown) or when it is not working (after a reset). My terminal looks like this:


$sudo modprobe ath9k
$

I added ath9k to /etc/modules. The content of the file now looks like this:

```

$ tail /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ath9k

```

WiFi still does not work after a reset.

---

### Post by Hadaka on 2013-04-13
Hi, when you issue a sudo modprobe driver
command, if the keyboard doent burst into
flames or it doesnt return evil output, it means
OK..done...even though it doesnt say so.
let's see if it has any information in dmesg.
on a WARM BOOT,after the boot
please do..
```
lspci -nn | grep 0280
sudo modprobe ath9k
dmesg | grep ath9k
```
thanks.

---

### Post by PGJSmit on 2013-04-13
This is how my terminal output after a warm boot:

$ lspci -nn | grep 0280
$ sudo modprobe ath9k
[sudo] password for user: 
$ dmesg | grep ath9k
$ 

This does not bring us any further does it?

---

### Post by Hadaka on 2013-04-13
Hi, no it doesnt...i need the output of those commands.
please do..
```
lspci -nn | grep 0280
```
and post the output..
thanks.

---

### Post by PGJSmit on 2013-04-13
When wifi is working it replies this:

$ lspci -nn | grep 0280
01:05.0 Network controller [0280]: Atheros Communications Inc. AR9227 Wireless Network Adapter [168c:002d] (rev 01)

But after a reboot, when wifi is not working it does not reply anything.

---

### Post by Hadaka on 2013-04-13
Hi, it looks like the driver ath9k is correct for your
wireless card.  It's odd that all is well on a cold boot
but not a warm. I suspect something is conflicting with
your graphic drivers...but..for what ever reason only on
a warm boot. You stated in your first post of this thread that
when you "activated" your graphic driver is when you lost wifi.
I have little to no knowledge about graphic drivers and trouble
shooting them.I would suggest doing a search on your graphic
card and see what comes up for a possible solution, sorry i am
unable to help you with that.
this "may" help
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
good luck.
Edit: My good pal chili555 has also suggested this..
If it shows up one boot in lspci and not the next, I suspect the card is  either defective or in a defective PCI slot or the motherboard is  defective. I'd try re-seating it or try another PCI slot.
cant hurt to try.

---

### Post by PGJSmit on 2013-04-14
It could very well be that the problem is unrelated to the graphics driver. It was simply the first time I had to reboot on this machine.

The motherboard only has one PCI slot so I cannot swap it :(

Thanks for your time!

---

