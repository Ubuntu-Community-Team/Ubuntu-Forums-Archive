---
title: "wireless help"
date: 2005-12-24
forum: Networking &amp; Wireless
---

### Post by bavs on 2005-12-24
hi guys

dont know what i done but modprobe ath_pci gives me

modprobe ath_pci
WARNING: Could not open '/lib/modules/2.6.12-10-686/volatile/ath_hal.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.12-10-686/madwifi/wlan.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.12-10-686/madwifi/ath_rate_sample.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.12-10-686/madwifi/ath_pci.ko': No such file or directory

what do i do?

sudo apt-get install "what files" ?

---

### Post by Lambert on 2005-12-24
Why are you doing a modprobe? 

What madwifi driver do you want to use? are you upgrading or installing a more recent version or trying to use what comes with breezy?

If you are trying to use what's in breezy make sure linux-restricted-modules-(kernel version) is installed. And the kernel will automatically load the driver. To check if it's loaded run this command

sudo lsmod | grep ath

if you get no output it's not. If it is you'll see something like this.

ath_pci                99104  0
ath_rate_sample        13056  1 ath_pci
wlan                  198300  5 wlan_wep,wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               197968  3 ath_pci,ath_rate_sample


if the driver is loaded and working you should get output showing information on ath0 with the command *iwconfig*

If you've installed a more recent version you'll have to give more info on which version and what you've done.

---

### Post by bavs on 2005-12-24
bava@bava:~$ sudo lsmod | grep ath
bava@bava:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

bava@bava:~$

so basically i dont have it :S

i have athreos wireless mini pci and

i have done sudo apt-get install linux-restricted-modules-

---

### Post by Lambert on 2005-12-24
copy and use this command as you need the kernel version on the end.

sudo apt-get install linux-restricted-modules-`uname -r`

---

### Post by bavs on 2005-12-24
sudo apt-get install linux-restricted-modules-2.6.12-10-686
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.12-10-686 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

i dont know what is going on

---

### Post by Lambert on 2005-12-24
when you ran modprobe did you use sudo in front of the command?

try rebooting then run the lsmod command again. It should automatically load the driver for the device.

also post output of this command here.


sudo lspci -v

and 

sudo lshw -C network

---

### Post by bavs on 2005-12-24
Lambert I am really sorry yup me forgot to put sudo infront :S

it works like a charm now really sorry again and thank you very much for ur time

---

### Post by nicedreams242 on 2006-01-20
I am having this same problem. Let me just give some history. This is for Hoary, didn't see any related in that forum so I though I might get better results here. I had the wireless card up and running for some time. Then I did some updates, and it broke. Ok Fine, so I compiled fresh madwifi drivers again. Everything compiled just fine. When I do 

For reference ALL commands were run as root.

```

lsmod | grep ath

ath_pci                80928  0
ath_rate_sample        11008  1 ath_pci
wlan                  164956  3 ath_pci,ath_rate_sample
ath_hal               197584  3 ath_pci,ath_rate_sample

```

```

lspci -v

0000:07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc D-link DWL-G650 B3 Wireless cardbus adapter
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at 21000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

```

```

ifconfig ath0

ath0      Link encap:Ethernet  HWaddr 00:0D:88:80:22:56
          inet6 addr: fe80::20d:88ff:fe80:2256/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:e0b80000-e0b90000

```

```

iwconfig ath0

ath0      no wireless extensions.

```

Shouldn't this show otherwise?
In the network utility the wireless devices does not even show. So I tried to do a 

```

dhclient ath0

```

But it doesn't bind to an IP. Anyone else having this problem? The card is fine, when I dual boot to Winblowz it works just fine. Everything looks OK, but it's definately not, this is getting annoying! PLEASE HELP!

---

### Post by Lambert on 2006-01-20
nicedreams242,

take the card out, plug it back in and run the command *dmesg* and post the last lines that look to do with the event here.

Also post output of these commands

sudo lshw -C network

cat /proc/version

modinfo ath_pci

---

