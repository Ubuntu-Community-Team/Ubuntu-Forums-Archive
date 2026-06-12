---
title: "RTL8187B - Not recognized by Ubuntu 9.04"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by KGTM on 2009-06-14
Hi guys.
I have installed Ubuntu 9.04 64 bits on my laptop. But i have some problems

My wlan usb module that came with the laptop isn't working well with ubuntu.

```
Bus 003 Device 003: ID 19d2:0015  
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 5986:0200 Acer, Inc 
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

PS: He states Acer, Inc. But the computer is a Insys Gameforce hd 8761su.

When i installed it as recognized but to connect to a wireless router i had to be not more than 2 meters with nothing in the way.

Then ive done this:

#iwconfig wlan0 rate 5.5M fixed


And its seemed working well, and it does for some days, although i still had to be pretty close to the router.
But then it came to the same.

Then i've used ndiswrapper to use a windows driver. I've rebooted, and no network shown, i've tried other drivers even win98 drivers. The same.

Then i've removed ndiswrapper. And no device found.. I mean, Network Manager that comes with ubuntu, now states that there is only wired connections, the wireless connection is gone with ndiswrapper.

How can i get this fixed?. At least that the ubuntu recognizes the device again.

Thanks for the help.

---

### Post by julioipn on 2009-07-07
you could try realtek rtl8187b original driver, it works wonders with my netbook
[http://ubuntuforums.org/showthread.php?t=1065698](http://ubuntuforums.org/showthread.php?t=1065698)

---

### Post by MrHara on 2009-07-08
Hi

I have bit similar problem on my nobraned laptop, it is Realtek 8187 Wlan usb card and I have been fighting couple of days put it run with out success. On the windows XP side it works fine (I have dual boot).
On the lsusb every think seems to be ok

Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

but it is not regonized on lshw side
harri@spc-test3:/etc/modprobe.d$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:03:0d:9d:0f:9e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.0.137 latency=0 module=sis190 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:ce:5c:e7:91:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
harri@spc-test3:/etc/modprobe.d$ 

I have been trying ndiswrapper, reinstaling Ubuntu, and so on without success, any ideas what could be wrong ??

Bit more info below

Thanks advance

Hara

harri@spc-test3:/etc/modprobe.d$ uname -mr
2.6.28-13-generic i686
harri@spc-test3:/etc/modprobe.d$ dmesg |grep network
harri@spc-test3:/etc/modprobe.d$ dmesg |grep ndis
[    9.639864] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   10.898456] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,06/01/2007,5.1089.0601.2007) loaded
[   10.901026] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
[   10.901036] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   10.901048] ndiswrapper (mp_halt:262): device f657c500 is not initialized - not halting
[   10.901052] ndiswrapper: device eth%d removed
[   10.901083] ndiswrapper: probe of 1-1:1.0 failed with error -22
[   10.901133] usbcore: registered new interface driver ndiswrapper
[   60.259512] Modules linked in: sis drm sisfb binfmt_misc ppdev bridge stp bnep lp parport joydev snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore psmouse sis190 pcspkr sis_agp snd_page_alloc ndiswrapper usb_storage serio_raw mii shpchp agpgart fbcon tileblit font bitblit softcursor
harri@spc-test3:/etc/modprobe.d$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
net8187b : driver installed
	device (0BDA:8187) present (alternate driver: rtl8187)
harri@spc-test3:/etc/modprobe.d$ cat /etc/modprobe.d/blacklist
blacklist rtl8187
blacklist r8187
harri@spc-test3:/etc/modprobe.d$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
        hostname KotiWlan
        wireless_mode managed
        wireless-essid KotiWlan
harri@spc-test3:/etc/modprobe.d$

---

