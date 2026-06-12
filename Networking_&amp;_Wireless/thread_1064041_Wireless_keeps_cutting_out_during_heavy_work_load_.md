---
title: "Wireless keeps cutting out during heavy work load with belkin router"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2009-02-08
Hey everyone

This is a little random really, my wireless is fine at university (VPN), fine at home (Netgear router with WEP encryption and MAC Address Filtering) but at my other half's house my wireless seems to work fine but as soon as I start to open a couple of pages, or pages filled with images the wireless just cuts out.

The only security the router has is MAC Address filtering, my laptop is a MacBook 1.4 which I think is a broadcom chipset, so any ideas as to what is happening?

The router is a belkin54g I think, but dont quote me on that, but is it ubuntu or the router?

Any helps would be great, cheers

Gaunt

---

### Post by joelgrrr on 2009-02-14
I have exactly the same (or very similar) problem.

I'm using Heron, on a laptop, with an Atheros 5k chipset wireless card (a,b & g wifi compatible). It all works perfectly at work, but at home I am only able to connect for a short while before the network connection slows to a crawl, or stops completely. Occasionally it restarts again, only to stop shortly afterwards.

I'm still trying to figure out what's different between work and home, to make the difference, I've tried with and without securing the wireless connection, this makes no difference.

I have a netgear router, which is b & g compatible (If I boot into Vista, it all works fine).
I have tried explicitly setting the max tranmission speed, from 54Mb to 11Mb, but this makes no difference

---

### Post by joelgrrr on 2009-02-15
It seems that this is a really common complaint on the Ubuntu forum - wireless works initially, then cuts out, or is really, really slow (using heron, and an Atheros 5k wireless card). Most people also report that this same access point works fine when dual booting into XP/Vista, and/or that they can use their Ubuntu settings in another (say work) wireless environment. I too have been scratching my head with this problem.

I now have a stable connection (at least have had for the last 45mins, which is about 44 mins longer than any I had before). 

I changed the following at home, to mirror my work setup as much as possible (where wireless was working with no problems):

[LIST]
[*] Set the router to operate only at the g frequency. (54Mb)
[*] Changed the channel (.e. frequency) my wireless router broadcasts on from the default (11) to 10. This will cause my wireless card to see fewer access points in my local area (most operate on the frequency of channel 11). It is possible that the madwifi software does not handle excessive network interference well, so changing operating frequency will remove many of the other access points from view.
[*] Used WPA2-Personal security mode.
[/LIST]

Unfortunately I made all these changes at once (not very scientific I k now) so can not tell you whether any action alone would fix the problem, but you can of course experiment yourself.
> 
Using : Heron 8.10,  AR242x 802.11abg Wireless PCI Express Adapter (Atheros), Netgear Router DG834G (abg compatible)

Here is some system information for the configuration that works:

Network Card:
```

joel@bohr:~$ sudo lshw -C network
[sudo] password for joel: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:21:63:cc:53:af
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.7 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```



joel@bohr:~$ sudo ifconfig ath0
```
ath0      Link encap:Ethernet  HWaddr 00:21:63:cc:53:af  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fecc:53af/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11646946 (11.1 MB)  TX bytes:1202428 (1.1 MB)

```


joel@bohr:~$ sudo wlanconfig ath0
```
[status not implemented (yet). Spawning iwconfig...]
ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1B:2F:A1:A2:D6   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=47/70  Signal level=-47 dBm  Noise level=-94 dBm
          Rx invalid nwid:20823  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


joel@bohr:~$ sudo iwconfig ath0 
```
ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1B:2F:A1:A2:D6   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:F44A-E6DB-6465-973B-E0CF-26B4-7F8F-26ED   Security mode:restricted
          Power Management:off
          Link Quality=46/70  Signal level=-48 dBm  Noise level=-94 dBm
          Rx invalid nwid:20853  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And from the router:
```
Channel : 10 (or any channel that is not being heavily used in your vicinity)
Mode : g only
Security WPA2-personal
```

Finally, I am using the madwifi drivers and installation procedure as described here: [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")

---

