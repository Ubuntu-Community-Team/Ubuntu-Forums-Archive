---
title: "D-Link DWL-G520+ version in Breezy?"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by Smaskens on 2005-12-08
I have a D-Link DWL-G520+ (with ACX111, Texas Instruments chip) and would like to know what is the exact version of ACX111 driver in Breezy Badger? Which are the magical commands to see the exact version? Is it just iwconfig?

```

wlan0     IEEE 802.11b+/g+  ESSID:"MY_WLAN"  Nickname:"acx100 v0.2.0pre8"          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=32/100  Signal level=5/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Second question is which version of the ACX111 driver works properly with DWS-G520+? It is clear that ndiswrapper is better solution, but still open source driver would be more interesting.

This is important information because I experienced some strange connection lockups and probably main reason is the driver. As far I know, this driver development has been really messy because of the dozens of versions (current version is acx-20051207.tar.bz2). Currently Internet connection works ok (I removed my ADSL router address from DNS settings).

Current versions are here:
[http://acx100.erley.org/](http://acx100.erley.org/)

And some sort of instruction is here:
[http://acx100.erley.org/howto.txt](http://acx100.erley.org/howto.txt)

So is the Ubuntu ACX111 driver ok, or is there need to update it?

---

### Post by Lambert on 2005-12-08
You can try two places but not sure if it will have what you need. I haven't seen a standard place yet that shows this. Maybe somebody else will know something

sudo lshw

this will show all your hardware on the machine. You can limit the output with options.

I have a line for mine like this.

configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL)

Of course you will see something like acx_pci instead.

or

you can try

sudo modinfo acx_pci

and see if you get anything there.

Iwconfig is showing something but I believe there are various fix releases that isn't shown.

---

### Post by Smaskens on 2005-12-10
Thanks Lambert! Looks really that there are no clear information of the version :(. This is one of the things that Ubuntu should have, namely a hardware center with proper version information and possibility to install new drivers or just remove the needless hardware. I know these things are easy for Linux gurus but hardware management is too hard for normal users :???: .

**sudo lshw** (pasted the wlan part only)

```

     *-network:0
             description: Wireless interface
             product: ACX 111 54Mbps Wireless Interface
             vendor: Texas Instruments
             physical id: 7
             bus info: pci@00:07.0
             logical name: wlan0
             version: 00
             serial: 00:11:95:xx:xx:xx
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=acx_pci ip=192.168.1.10 multicast=yes wireless=IEEE 802.11b+/g+
             resources: iomemory:dfffc000-dfffdfff iomemory:dffc0000-dffdffff irq:18

```

**modinfo acx_pci**
```

xxx@xxx:~$ sudo modinfo acx_pci
filename:       /lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/acx/acx_pci.ko
author:         The ACX100 Open Source Driver development team
description:    Driver for TI ACX1xx based wireless cards (CardBus/PCI/USB)
license:        Dual MPL/GPL
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        firmware_class
alias:          pci:v0000104Cd00008400sv*sd*bc*sc*i*
alias:          pci:v0000104Cd00008401sv*sd*bc*sc*i*
alias:          pci:v0000104Cd00009066sv*sd*bc*sc*i*
srcversion:     FBE1617EA795BB33E847C2C
parm:           firmware_dir:Directory to load acx100 firmware files from (charp)
parm:           use_eth_name:Allocate device ethX instead of wlanX (uint)
parm:           debug:Debug level mask: 0x0000 - 0x3fff (see L_xxx in include/acx100.h) (uint)

```

**iwconfig**
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"G604T_WIRELESS"  Nickname:"acx100 v0.2.0pre8"          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:xx:xx:xx
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=46/100  Signal level=25/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

