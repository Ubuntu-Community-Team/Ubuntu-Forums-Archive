---
title: "intermittent wireless on broadcom 4353/Dell Inspiron 1440/10.04"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by thebenedict on 2010-10-26
Hi all,

After considerable forum searching I still can't get my broadcom 4353 rev 1 wireless card to consistently work on this Dell 1440 laptop (posting from a wired connection). Irritatingly I can't identify what's different between when it is working and not working.

Symptoms:
On boot the wireless card is always disabled and lshw -C network shows the card as UNCLAIMED. I can enable the card by pressing F2, but it will not find or connect to any wireless networks. 

System->Administration>Hardware Drivers allows me to load the "Broadcom 802.11 Linux STA wireless driver", after which the output of lshw -C network is:

```
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: c4:46:19:80:8a:df
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f69fc000-f69fffff
```

where the digit after "driver=wl" depends on the number of times I've reloaded the driver.

Now if I remove the driver, lshw -C network still shows:

```

  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: c4:46:19:80:8a:df
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f69fc000-f69fffff

```

At some point in this process the wireless card will sometimes start working, but it doesn't seem to be related to whether or not the STA driver is shown as active in Hardware Drivers, as long as I've loaded it at least once once since the last reboot.

Other information:
```
michael@ubuntu:~$ lspci -n | grep 14e4
0c:00.0 0280: 14e4:4353 (rev 01)
```

```
michael@ubuntu:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
michael@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:44 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm at a loss for how to continue troubleshooting this. Let me know if further information would be helpful. Thanks a lot.

--Michael

---

