---
title: "Wireless (AR928X) not responding to arp (Vaio P)"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by squish0 on 2009-10-07
Hi
 
My ubuntu system works great in terms of outbound connectivity to other systems, however I can't connect to it from any other systems on my network.
 
Debugging has revealed this is because my ubuntu is not responding to arp requests, however interestingly it will start to respond while I am running "tcpdump -i wlan0", i.e. I put the network interface in to promiscuous mode.
 
Thus, my conclusion at this stage is that my ubuntu wireless network driver (AR928X) is ignoring broadcast packets when in normal mode (not promiscuous).
 
Is it possible I have some setting wrong?
 
This is ubuntu 9.04 and is a stock install with the default kernel and drivers.
 
I have configured the driver via /etc/network/interfaces:
 
[FONT=Courier New]auto wlan0[/FONT]
[FONT=Courier New]iface wlan0 inet dhcp[/FONT]
[FONT=Courier New]wpa-ssid BLAH[/FONT]
[FONT=Courier New]wpa-psk PWD[/FONT]
 
lshw tells me:
 
[FONT=Courier New]*-network[/FONT]
[FONT=Courier New]description: Wireless interface[/FONT]
[FONT=Courier New]product: AR928X Wireless Network Adapter (PCI-Express)[/FONT]
[FONT=Courier New]vendor: Atheros Communications Inc.[/FONT]
[FONT=Courier New]physical id: 0[/FONT]
[FONT=Courier New]bus info: pci@0000:02:00.0[/FONT]
[FONT=Courier New]logical name: wmaster0[/FONT]
[FONT=Courier New]version: 01[/FONT]
[FONT=Courier New]serial: 00:23:4d:22:11:7f[/FONT]
[FONT=Courier New]width: 64 bits[/FONT]
[FONT=Courier New]clock: 33MHz[/FONT]
[FONT=Courier New]capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless[/FONT]
[FONT=Courier New]configuration: broadcast=yes driver=ath9k ip=192.168.0.7 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn[/FONT]
 
And iwconfig tells me:
 
[FONT=Courier New]wlan0 IEEE 802.11bgn ESSID:"BLAH"[/FONT]
[FONT=Courier New]Mode:Managed Frequency:2.462 GHz Access Point: 00:1E:74:22:11:80[/FONT]
[FONT=Courier New]Bit Rate=1 Mb/s Tx-Power=20 dBm[/FONT]
[FONT=Courier New]          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=71/100  Signal level:-69 dBm  Noise level=-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/FONT] 
Thanks for any help
 
James

---

### Post by squish0 on 2009-10-08
Hi

I have found a report in Fedora that is the same issue with the ath9k driver:

[https://bugzilla.redhat.com/show_bug.cgi?id=498502](https://bugzilla.redhat.com/show_bug.cgi?id=498502)

It does not receive broadcast packets.

They appear to have patched their version of ath9k.  Does anyone know if Ubuntu's ath9k driver has or can be fixed?

James

---

