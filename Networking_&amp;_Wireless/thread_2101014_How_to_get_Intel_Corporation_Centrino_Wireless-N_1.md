---
title: "How to get Intel Corporation Centrino Wireless-N 1000 working?"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by styk3 on 2013-01-03
LAPTOP MODEL: MSI GT680-037UK

Initially wireless did not work - it would find wireless and would start connecting, but it would just keep prompting for the password and never connected.

I've tried this proposed fix on [LinuxMint.com]("http://community.linuxmint.com/tutorial/view/608") which installs an older version of the microcode (firmware) for my device. Unfortunately it didn't work.

I'm a Linux newbie so bear with me, and let me know if I can add any command outputs that might help you help me resolve this issue! :)

sudo lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM67 Express Chipset Family LPC Controller [8086:1c4b] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF106 [GeForce GTX 460M] [10de:0dd1] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GF106 High Definition Audio Controller [10de:0be9] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0083]
04:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)

```

[/var/log/udev]("http://pastebin.com/KwYmgAMT")

[/var/log/dmesg]("http://pastebin.com/Ts5Aftrz")

straight after failed connection:

```

cat /var/log/syslog | grep etwork | tail -n30
Jan  3 16:58:51 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  3 16:58:51 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  3 16:58:51 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  3 16:58:51 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  3 16:58:51 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan  3 16:58:55 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  3 16:58:55 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  3 16:58:56 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  3 16:58:56 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  3 16:58:56 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan  3 16:59:00 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  3 16:59:00 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  3 16:59:00 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  3 16:59:00 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  3 16:59:00 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan  3 16:59:05 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  3 16:59:05 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  3 16:59:05 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  3 16:59:05 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  3 16:59:05 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan  3 16:59:09 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  3 16:59:09 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  3 16:59:10 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: scanning -> associating
Jan  3 16:59:10 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: associating -> associated
Jan  3 16:59:10 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jan  3 16:59:14 bogdan-GT680-GX680 NetworkManager[1042]: <warn> Activation (wlan0/wireless): association took too long.
Jan  3 16:59:14 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  3 16:59:14 bogdan-GT680-GX680 NetworkManager[1042]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan  3 16:59:14 bogdan-GT680-GX680 NetworkManager[1042]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Jan  3 16:59:14 bogdan-GT680-GX680 NetworkManager[1042]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```
sudo lshw -C network

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 6c:62:6d:2f:7d:81
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:53 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:10:56:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-35-generic-pae firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:55 memory:f6200000-f6201fff

```

uname -a

```

Linux bogdan-GT680-GX680 3.2.0-35-generic-pae #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 i686 i686 i386 GNU/Linux

```

cat /etc/issue
```

Ubuntu 12.04.1 LTS \n \l

```

lsb_release -a

```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

```

---

### Post by ahallubuntu on 2013-01-03
What version of Ubuntu?

What make/model laptop are you using?

What's the output of 

```
sudo lshw -C network
```

---

### Post by tgalati4 on 2013-01-03
Is this a dual-boot machine?  If so, does the wireless work correctly under Windows?

Also, try removing wireless security, temporarily, to see if it connects on an open network.  What kernel version are you running, since the link you posted was for a temporary fix 1 year ago.

```
uname -a
cat /etc/issue
lsb_release -a

```

---

### Post by styk3 on 2013-01-03
> **ahallubuntu said:**
> What version of Ubuntu?

What make/model laptop are you using?

What's the output of 

```
sudo lshw -C network
```

Updated the OP.

---

### Post by styk3 on 2013-01-03
> **tgalati4 said:**
> Is this a dual-boot machine?  If so, does the wireless work correctly under Windows?

Also, try removing wireless security, temporarily, to see if it connects on an open network.  What kernel version are you running, since the link you posted was for a temporary fix 1 year ago.

```
uname -a
cat /etc/issue
lsb_release -a

```

Updated the OP. 

Windows connects to the network fine, no problems whatsoever.

I'll try your suggestion about making an open network later, as I don't have the router login details. 

Thank you for the suggestions so far! :)

---

### Post by ahallubuntu on 2013-01-03
What make/model laptop?  Intel cards are supported automatically in the kernel, and yours shows it has loaded the correct driver but it is simply disabled. Sometimes the hardware switch enabling/disabling the card causes issues in Linux, and there may be remedies specific to different types of laptops.  (I have no issues with the Intel cards in my Dells or my Acer netbook.)

---

### Post by styk3 on 2013-01-03
> **ahallubuntu said:**
> What make/model laptop?  Intel cards are supported automatically in the kernel, and yours shows it has loaded the correct driver but it is simply disabled. Sometimes the hardware switch enabling/disabling the card causes issues in Linux, and there may be remedies specific to different types of laptops.  (I have no issues with the Intel cards in my Dells or my Acer netbook.)

The laptop model is an obscure MSI GT680-037UK. Hopefully that's of some use!

---

### Post by dodo3773 on 2013-01-03
If it's the same card I am thinking of then it needs firmware. Install the linux-firmware package or similar to get it working.

---

### Post by tgalati4 on 2013-01-03
Burn a DVD of 12.10 or make a Live USB stick of 12.10 using unetbootin.  Boot from it and see if your wireless works.  It's possible that a kernel/distro upgrade will take care of it since it was identified over a year ago as being a problem.

---

### Post by ahallubuntu on 2013-01-03
Trying Ubuntu 12.10 is worth a shot.  The wireless card itself has been supported in Linux for a long time, though - since kernel 2.6.30 - so it should have worked in Ubuntu for several releases by now.  I still think it's something to do with the wireless switch. styk3, did you try enabling/disabling the card a few times with the toggle switch (or the "wireless enable/disable key" whatever that is in your case)?

---

### Post by styk3 on 2013-01-03
> **tgalati4 said:**
> Burn a DVD of 12.10 or make a Live USB stick of 12.10 using unetbootin.  Boot from it and see if your wireless works.  It's possible that a kernel/distro upgrade will take care of it since it was identified over a year ago as being a problem.


12.10 doesn't work, I actually downgraded from it to see if wireless works with 12.04!

---

### Post by styk3 on 2013-01-03
> **ahallubuntu said:**
> Trying Ubuntu 12.10 is worth a shot.  The wireless card itself has been supported in Linux for a long time, though - since kernel 2.6.30 - so it should have worked in Ubuntu for several releases by now.  I still think it's something to do with the wireless switch. styk3, did you try enabling/disabling the card a few times with the toggle switch (or the "wireless enable/disable key" whatever that is in your case)?

I did try enabling/disabling, I had to because otherwise it just keeps trying to reconnect and keeps prompting for the password, even if I tell it to disconnect from the network.

---

### Post by styk3 on 2013-01-03
> **dodo3773 said:**
> If it's the same card I am thinking of then it needs firmware. Install the linux-firmware package or similar to get it working.

Thanks for your suggestion :)
Could you let me know how to install this package? The most relevant google result times out and I don't trust myself to try any of the others.

---

### Post by tgalati4 on 2013-01-03
Are you using WEP?  If so, it could be as simple as changing from "Open" authentication to "Shared" or "Restricted".

---

### Post by styk3 on 2013-01-03
> **tgalati4 said:**
> Are you using WEP?  If so, it could be as simple as changing from "Open" authentication to "Shared" or "Restricted".

My network knowledge is limited, but I'm guessing this option is configured in the router. I'll do it asap

---

### Post by ahallubuntu on 2013-01-03
WEP is the original/now obsolete method of wireless security used on wireless routers.  The passcode is forced to be a string of numbers and letters (actually just a number with hexdecimal digits, some are letters A-F).  WEP is insecure anyway and easy to defeat.  WPA2 is the latest method of security that most people should be using - you can have a real password instead of some hard-to-remember number, too.

Sometimes WEP does cause issues.  WEP passcodes can be represented in different ways.  WPA/WPA2 is much easier.

You can change the wireless security setting of the router by logging into it.  Only very, very old routers are limited in doing ONLY WEP.  Even WPA (not as secure as WPA2) is much better than WEP.

---

### Post by dodo3773 on 2013-01-03
> **styk3 said:**
> Thanks for your suggestion :)
Could you let me know how to install this package? The most relevant google result times out and I don't trust myself to try any of the others.

```

sudo apt-get install linux-firmware 

```
or
```

apt-cache search firmware

```

and reboot.

---

