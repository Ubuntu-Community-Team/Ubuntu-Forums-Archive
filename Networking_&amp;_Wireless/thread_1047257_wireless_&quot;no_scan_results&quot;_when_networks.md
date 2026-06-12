---
title: "wireless &quot;no scan results&quot; when networks are present"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by wmdiem on 2009-01-22
dear all, I recently lost my wireless conectivity. 
My card appears to be properly configured, but when I do iwlist scan my card comes back with "no scan results":
```

wmdiem@diem-acer:~$ iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

wlan1     No scan results

eth1      Interface doesn't support scanning.


```
just as general information (from lspci):
```

           *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wifi0
                version: 01
                serial: 00:1d:d9:2c:97:f3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


```
the ath_pci is a patched madwifi that I use with my 5007.

and for good measure
```
wmdiem@diem-acer:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

wlan1     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-148 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.



```

I'm running 8.04. 
Thanks for any help.
Everything had been working fine for several months, until just a couple days ago (same ap and everything).

---

### Post by superprash2003 on 2009-01-22
have you tried via system->admin->hardware drivers ??

[http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by wmdiem on 2009-01-22
> **superprash2003 said:**
> have you tried via system->admin->hardware drivers ??

[http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)
Thanks for the reply. Does does that work on hardy? I was under the impression ath5k only works on intrepid. Also, I should mention that I'm not using standard ubuntu (I'm using crunchbang, it's ubuntu based but different DE) so I can only really follow terminal instructions.

---

### Post by wmdiem on 2009-01-23
The problem has gone away. I have no idea what it was. i'm not going to mark it solved since I have no idea how to help someone else with this problem,

---

