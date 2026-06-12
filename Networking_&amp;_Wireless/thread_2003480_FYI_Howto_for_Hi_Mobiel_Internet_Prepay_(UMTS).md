---
title: "FYI: Howto for Hi Mobiel Internet Prepay (UMTS)"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by sanderj on 2012-06-14
This is a FYI Howto for Hi Mobiel Internet Prepay (UMTS) on Ubuntu 12.04.

Short howto: leave everything to default, but change APN to "prepaidinternet".

Longer Howto:

Buy the Hi Mobiel Internet Prepay package (for example at the Kijkshop): for 15 Euro you get a USB-UMTS-dongle and a Prepaid SIM card. The dongle is a ZTE model MF190, HSUPA USB Stick.

Insert the SIM card into the dongle, and insert the dongle into your computer's USB port. The light in the dongle should turn red.
With 'lsusb' you should see the dongle

```
ID 19d2:0017 ZTE WCDMA Technologies MSM
``` 

Ubuntu should automagically launch the Mobile Broadband wizard. Choose The Netherlands and then Hi. 
Now the important part: in the wizard, or afterwards in Edit Connections, change the APN setting from "...mmm..." to 'prepaidinternet'.

Now it should work. Click on the network icon in the upper right  corner, and it should show "Hi Default". Click that. If it asks for a PIN code, type '0000'
You should now be connected to Internet. The light in the dongle should turn blue.

The ifconfig should show something like:

```
sander@R540:~$ ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:181711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25818521 (25.8 MB)  TX bytes:25818521 (25.8 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.47.240.70  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3685088 (3.6 MB)  TX bytes:421088 (421.0 KB)
```



HTH

PS:

The ZTE UMTS USB dongle also has a micro-SD slot. After putting in a micro-SD card, the card was automagically mounted and shown in Ubuntu.

Info from dmesg:

```

[16294.093331] scsi12 : usb-storage 2-1.2:1.4
[16295.093371] scsi 12:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[16295.094170] scsi 12:0:0:1: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[16295.098950] sr1: scsi-1 drive
[16295.099309] sr 12:0:0:0: Attached scsi CD-ROM sr1
[16295.099993] sr 12:0:0:0: Attached scsi generic sg2 type 5
[16295.101385] sd 12:0:0:1: Attached scsi generic sg3 type 0
[16295.103733] sd 12:0:0:1: [sdb] 8054784 512-byte logical blocks: (4.12 GB/3.84 GiB)
[16295.104473] sd 12:0:0:1: [sdb] Write Protect is off
[16295.104484] sd 12:0:0:1: [sdb] Mode Sense: 0f 0e 00 00
[16295.105103] sd 12:0:0:1: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[16295.120290]  sdb: sdb1
[16295.133931] sd 12:0:0:1: [sdb] Attached SCSI removable disk


```

PS2:

The IP address of the PPP link can also be a public, non-RFC1918 address:


```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:62.133.117.5  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3834079 (3.8 MB)  TX bytes:578542 (578.5 KB)

```


And the lsusb ID changed for a period to a different description:

```

ID 19d2:2000 ZTE WCDMA Technologies MSM MF627/MF628/MF628+/MF636+ HSDPA/HSUPA

```

---

### Post by giordy1975 on 2012-11-03
it works, Thanks!
Stefano

---

### Post by sanderj on 2012-11-03
> **giordy1975 said:**
> it works, Thanks!
Stefano

Cool!

---

