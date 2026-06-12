---
title: "Broadcom 4311 woes."
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by boakes on 2006-06-29
I can have internet connectivity intermitently.  Only a reboot will fix it, and sometimes I have to reboot twice or more to get it to work.

Here's my dmesg

```
[17179598.872000] ndiswrapper: using irq 177
[17179599.552000] wlan0: vendor: ''
[17179599.552000] wlan0: ndiswrapper ethernet device 00:16:ce:0f:b1:16 using driver bcmwl5, 14E4:4311.5.conf
[17179599.552000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179602.712000] NET: Registered protocol family 10
[17179602.712000] lo: Disabled Privacy Extensions
[17179602.712000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179602.712000] IPv6 over IPv4 tunneling driver
[17179605.024000] ACPI: AC Adapter [AC] (on-line)
[17179605.064000] ACPI: Battery Slot [BAT0] (battery present)
[17179605.184000] ACPI: Lid Switch [LID]
[17179605.184000] ACPI: Power Button (CM) [PBTN]
[17179605.184000] ACPI: Sleep Button (CM) [SBTN]
[17179605.320000] ibm_acpi: ec object not found
[17179605.368000] pcc_acpi: loading...
[17179605.524000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179605.524000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179605.524000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179612.616000] ppdev: user-space parallel port driver
[17179612.924000] apm: BIOS not found.
[17179613.100000] wlan0: no IPv6 routers present
[17179618.640000] Bluetooth: L2CAP ver 2.8
[17179618.640000] Bluetooth: L2CAP socket layer initialized
[17179618.644000] Bluetooth: RFCOMM socket layer initialized
[17179618.644000] Bluetooth: RFCOMM TTY layer initialized
[17179618.644000] Bluetooth: RFCOMM ver 1.7
[17179620.968000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179620.992000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179621.012000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179621.048000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179621.088000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179621.108000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179621.128000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179621.148000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179621.168000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.172000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.188000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.208000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.228000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.248000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.268000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.288000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.308000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.328000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.348000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.368000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.388000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.408000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.428000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.448000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.468000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.488000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.508000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.528000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.548000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.568000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.588000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179622.608000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179623.968000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179623.968000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.000000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.016000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.048000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.088000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.108000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.128000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.148000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.168000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.188000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.208000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.228000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.248000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.268000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.292000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.308000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.328000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.348000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.368000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.388000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.408000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.428000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.448000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.468000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.488000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.508000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.528000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.548000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.568000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.588000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.608000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.628000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.648000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.672000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.688000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.708000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.728000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.748000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179624.768000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179749.864000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179749.884000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179749.900000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
[17179749.920000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 46
```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"UA-WLAN"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:20:D8:24:D6:C2
          Bit Rate:24 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-79 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

What the heck is going on?  I've reinstalled Ubuntu several times, I am running on the 686smp kernel if it makes any difference.

---

### Post by shujimi on 2006-06-29
Are you using the ndiswrapper?

---

### Post by boakes on 2006-06-29
Yes I am.  From this thread.--> [http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311)

I should point out that if I use the stock kernel, I have no problems.

---

### Post by boakes on 2006-06-30
Ok, I've compiled and recompiled ndiswrapper several times.  I've reinstalled the nic driver.  I've even used the GUI for wireless nics that automatix installed.  All give the same results.  It'll work for a few minutes, then just stop responding.  I have no clue what's going on, it works just fine in windows.  There has to be something going on...

---

### Post by boakes on 2006-06-30
I get this when I do a dmesg:

[17179722.468000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 49

I'm at a loss here, any help would be appreciated.

---

### Post by boakes on 2006-07-01
Ok, well I guess I'm just left to fend for myself.

---

### Post by shujimi on 2006-07-05
[QUOTE=boakes]Ok, well I guess I'm just left to fend for myself.[/QUOTE]

I'm going out on a limb here, but I think that ACL may be unrelated.  I know for a fact that the ndiswrapper works with the 686smp kernel.  I have seen it in the  physical.

What happens when you run:

ndiswrapper -l

If it says:
bcmwl5     driver installed, hardware present

Then you know you're good to go from the ndiswrapper side of things.  I have definitely seen in the past that I have had to reload the module a few times over to get it working.

---

### Post by tsensei on 2006-08-23
Hey there !

I have exactly the same problem.
When using the 386 kernel everything goes fine, but with the 686 smp kernel, the wireless connection stops without reason.

Any Idea ?

---

### Post by jedleman on 2006-08-24
what do i try if i have the same drver and i get this?

ubuntu@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present
bcmwl5.sys      invalid driver!
ubuntu@ubuntu:~$

---

### Post by haiku99 on 2006-08-25
may or may not help, but I couldn't get my 4311 to work until I insalled the latest version of ndiswrapper using the howto at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by reedatschool on 2006-09-03
Same issue here running on a k7 smp kernel.  Every once and awhile the wireless just stops.  Switching to 386 kernel makes it work fine.  Anyone have a clue as to whats going on here?

---

