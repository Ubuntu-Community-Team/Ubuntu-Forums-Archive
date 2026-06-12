---
title: "Troubles with D-Link DWL-G520+ card connection"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by ralf57 on 2006-02-15
Hi all,
i've recently intalled a D-Link DWL-G520+ Pci card that i use with DSL-G604T  wireless router.Everything works fine on windows xp.
I wish to have it working on my Breezy install too,but i'm having troubles.
The card is correctly recognised, i've followed the instructions on [this wiki page]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=NdiswrapperWithoutInternetAccessSlowFirefox") at letter, then launched Network manager, configured the connection with the same parameters i use on windows (same ESSID and 256bit Exadecimal Wep key) and set the connection active.It seemed to work fine but Firefox failed to open any site.
As a further check i've also placed the Network monitor applet on the panel and discovered that, after inserting the right name for the connection (wlan0) there was no data traffic.
Is there any other setting i have to set to have it working?
Any check i can perform to fix the issue?
Thank in advance,ralf

---

### Post by spd106 on 2006-02-15
Maybe have a look at the other wifi configuration pages. [This one]("https://wiki.ubuntu.com/WiFiHowto") has most of the  info you will need.

---

### Post by ralf57 on 2006-02-15
> This one has most of the info you will need.
Thank you,I've overlooked that one.
I'll try and let you know.

---

### Post by ralf57 on 2006-02-15
After reading lots of tutorials i still cannot have my connection to work.
I've collected some commands' output hoping this can help to locate the problem.
Starting from the beginning:

lspci
```

0000:00:0b.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

iwconfig
```

IEEE 802.11b+/g+  ESSID:"myessid"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card
wireless_channel	6
wireless_mode    managed
wireless-essid myessid
wireless-key 3536537845643875643856358356385638563583658356348563485634 (a 58 digits string for 256bit wep encryption)

```

tail --lines=30 /var/log/messages
```

Feb 16 00:39:53 localhost kernel: [4296265.892000] Algorithm is ok
Feb 16 00:39:53 localhost kernel: [4296265.892000] acx_process_authen auth seq step 2
Feb 16 00:39:53 localhost kernel: [4296265.892000] Authentication FAILED (status code 13: "Responding station does not support the specified authentication algorithm. TRANSLATION: invalid network data or bug in ACX100 driver?"), still waiting for authentication
Feb 16 00:39:53 localhost kernel: [4296265.892000] acx_set_status: Setting status = 2 (WAIT_AUTH)
Feb 16 00:39:53 localhost kernel: [4296265.892000] <acx_set_timer> Elapse = 1500000
Feb 16 00:39:55 localhost kernel: [4296267.392000] acx_timer: status = 2
Feb 16 00:39:55 localhost kernel: [4296267.392000] resend authen1 request (attempt 2).
Feb 16 00:39:55 localhost kernel: [4296267.392000] Sending authentication1 request, awaiting response!Feb 16 00:39:55 localhost kernel: [4296267.392000] <acx_set_timer> Elapse = 2500000
Feb 16 00:39:55 localhost kernel: [4296267.393000] 00:13:46:b0:77:29 00:13:46:b0:77:29 00:11:95:a0:6d:d8 00:11:95:a0:6d:d8 00:11:95:a0:6d:d8
Feb 16 00:39:55 localhost kernel: [4296267.393000] Algorithm is ok
Feb 16 00:39:55 localhost kernel: [4296267.393000] acx_process_authen auth seq step 2
Feb 16 00:39:55 localhost kernel: [4296267.393000] Authentication FAILED (status code 13: "Responding station does not support the specified authentication algorithm. TRANSLATION: invalid network data or bug in ACX100 driver?"), still waiting for authentication
Feb 16 00:39:55 localhost kernel: [4296267.393000] acx_set_status: Setting status = 2 (WAIT_AUTH)
Feb 16 00:39:55 localhost kernel: [4296267.393000] <acx_set_timer> Elapse = 1500000
Feb 16 00:39:56 localhost kernel: [4296268.016000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Feb 16 00:39:56 localhost kernel: [4296268.016000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Feb 16 00:39:56 localhost kernel: [4296268.119000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Feb 16 00:39:56 localhost kernel: [4296268.119000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

The network monitor applet now shows the signal strength bar.
My doubts are now:

1)It seems to use a driver for ACX 100 chipset while my card has a ACX 111 chipset.I've tried both the drivers (win xp and 2000) that ship with the card and none of them seem to be right.

2)i've set a a 58 digits string to achieve a 256bit wep encryption.But is this supported?or else i have to use 128 or worse 64 bits encryption?

I apologize for being long but i desperately need it to be working.
Thanks again for your help.

---

### Post by Lambert on 2006-02-15
First because I didn't see, did you black list the native acx linux driver? I'm curious if that's loading and binding instead of ndiswrapper. Post output of these commands

sudo lshw -C network
lsmod | grep acx
lsmod | grep ndis

Key size shouldn't be a major factor of what you set.

> Key size is not the major security limitation in WEP. [Cracking]("http://en.wikipedia.org/wiki/Cryptanalysis") a longer key requires interception of more packets, but there are active attacks that stimulate the necessary traffic. There are other weaknesses in WEP, including the possibility of IV collisions and altered packets, that are not helped at all by a longer key.

The longer key might be a problem but not sure and I'm not sure if 256 is supported.

Just to rule out anything have you tried a shorter key or tried with out a key just to ensure the driver/device is working and can connect. From there add encryption back in and configure.

Why did you pick ndiswrapper and not the native driver?  With this chipset it might be easier but I would suggest going with native driver over ndiswrapper if you're willing to try to configure. You can find more about the acxdriver in my signature link to udsfwireless

---

### Post by ralf57 on 2006-02-16
Thank you Lambert,
i cannot provide you the output you requested since i'm currently at work.
I'll post it as soon as i come back home.

---

### Post by ralf57 on 2006-02-16
I was finally able to provide the output for the commands above:

sudo lshw -C network
```

*-network:0
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: b
       bus info: pci@00:0b.0
       logical name: wlan0
       version: 00
       serial: 00:13:46:b0:77:29
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:dfffe000-dfffffff iomemory:dffc0000-dffdffff irq:19
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@00:0c.0
       logical name: eth0
       version: 10
       serial: 00:0e:e8:8d:de:bc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:dc00-dcff iomemory:dfffdf00-dfffdfff irq:16


```

lsmod | grep acx
```

acx_pci               122752  0
firmware_class          9472  1 acx_pci

```

lsmod | grep ndis
```

This command returns no errors and no output

```

Please tell me if something else is wrong but i'm not able to change my router's settings since other workstations are currently connected to it.

---

### Post by Lambert on 2006-02-16
Your first post you said you followed instructions which the link pointed to ndiswrapper. Currently the device is using the native driver that comes with ubuntu and not ndiswrapper.

So I'm going to point you to a page. Look under the section for breezy. There are instructions for installing firmware for the device and other links. The acx driver wiki page and the houseofcraig site which gives instructions and help for setting up this driver if you run into more problems.
[http://doc.gwos.org/index.php/ACXDriver](http://doc.gwos.org/index.php/ACXDriver)

If you want to go with the ndiswrapper driver then you need to remove the acx_pci driver by doing this

sudo modprobe -r acx_pci

then to keep it from loading on boot ad this to the /etc/hotplug/blacklist file

blacklist acx_pci

Now if you run ndiswrapper -l and show hardware present driver present then run this to load ndiswrapper

sudo modprobe ndiswrapper

Then try to configure the network settings.

Both links about wireless in my sig lead to a WirelessTroubleshootingGuide. Try to walk through that. Also your original link has some troubleshooting/common errors on it.

Of course, come back and post here with details of where you're at if you can't get any further, include as much detail along with what driver you decided to use (ndiswrapper or acx_pci)

---

