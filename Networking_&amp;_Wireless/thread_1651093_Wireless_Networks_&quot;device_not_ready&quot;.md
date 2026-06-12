---
title: "Wireless Networks &quot;device not ready&quot;"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by Rebelli0us on 2010-12-22
Wireless stopped working with version 10.10, it was fine with previous versions, now it says "device not ready". Hardware works fine under Windows, and is a Linux-friendly Asus RaLink RT2860.

Any ideas?

---

### Post by Rebelli0us on 2011-01-05
Is there a way to get Ubuntu to re-initialize/re-detect/re-install the wireless adapter?

I tried "create new wireless network" but it's not working.

---

### Post by PatchesTheCaveman on 2011-01-05
Many users have better luck with the official Linux drivers from the Ralink website:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

If you search for your particular chipset on this forum somebody has probably already provided installation instructions.  If not, and the README confuses you or you have trouble, feel free to ask.

---

### Post by Rebelli0us on 2011-01-12
Thank you, I downloaded file:

2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2

I've never been able to install anything in Linux. What next? Internet worked fine with previous version Ubuntu Lucid. Should I just delete partition and re-install?

---

### Post by PatchesTheCaveman on 2011-01-12
If it worked fine in Lucid, there might be something simple going on.  Follow the instructions in this post to provide diagnostic information so we can take a look:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Rebelli0us on 2011-01-13
Thanks, wireless worked fine in previous version 9-something. After upgrade to 10.10 a lot of stuff broke. So yesterday I wiped partition and clean-installed 10.04 lucid. Wireless is still broken, works fine in Windows BTW. All the menu fonts in OpenOffice are broken too...

Anyway, here's some of what you asked:
```

$ ifconfig
...
wlan0     Link encap:Ethernet  HWaddr 70:71:bc:44:f3:d2  
          inet6 addr: fe80::7271:bcff:fe44:f3d2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1089387 (1.0 MB)  TX bytes:0 (0.0 B)
          Interrupt:16 

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.447 GHz  Access Point: 02:BD:B9:E2:8B:EF   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-41 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```



```

$ sudo lshw -C network
 
  *-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 70:71:bc:44:f3:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fdcf0000-fdcfffff

```


Any clues here?

---

### Post by TBABill on 2011-01-13
You may need to ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following to the end of the file: ```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb 
```
 
Then you can ```
sudo gedit /etc/modules
``` and add ```
rt2860sta
``` to the end of the file if it isn't already. Then restart and see if it works.

---

### Post by Rebelli0us on 2011-01-13
From syslog file:

> ...
[    7.737268] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
...
[   16.245641] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat



What does that mean?

---

### Post by PatchesTheCaveman on 2011-01-14
It means you need to copy the RT2860STA.dat file from the driver folder to that folder on your hard drive.

---

### Post by Rebelli0us on 2011-03-04
Does rt2860sta refer to a file? Under drivers/staging there is only rt2860sta.**ko**, there is no RT2860STA.dat.

---

