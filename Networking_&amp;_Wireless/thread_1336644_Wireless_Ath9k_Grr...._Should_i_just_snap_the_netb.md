---
title: "Wireless Ath9k Grr.... Should i just snap the netbook in half?"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by phelony on 2009-11-24
Currently running the 2.6.29.4 kernel
Ubuntu-Hardy
Ath9k Driver (Atheros 9285)
Compat-Wireless Package Installed


Ok so ive been struggling with this for days, searching every corner on the internet making posts here and there, to no avail.  As it stands now, i can see wireless networks floating around my head, MAC gets displayed, ESSID, all the goodies.  I use wicd_client to connect to them, aaaaand BOOM, i get no DHCP address from the router.  Ive tried connecting at varying distances to multiple AP's to no avail.  Here are some outputs to glance over.

```

root@YourRefridgerator:/home/jesus# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:XX:XX:XX
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm
                    Encryption key:off
                    ESSID:"bholton"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000c901c9d9183
                    Extra: Last beacon: 1130ms ago
                    IE: Unknown: 000762686F6C746F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0505000100A016
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD050010180109

root@YourRefridgerator:/home/jesus# ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:XX:XX:XX
          inet addr:192.168.1.2  Bcast:255.255.255.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:79161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12112 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000
          RX bytes:12426493 (12.4 MB)  TX bytes:1217030 (1.2 MB)
          Interrupt:28

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2700 (2.7 KB)  TX bytes:2700 (2.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:XX:XX:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@YourRefridgerator:/home/jesus# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"bholton"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


```any other outputs you need, any suggestions.  im about to snap this brand new 1005HA Asus Eee PC in half.  thanks!

---

### Post by Lord_ on 2009-11-24
Firstly I would say double check that wicd is set to look for DHCP and not a static. Also make sure you are able to actually connect to the AP. If your happy both of these are happening then you could try running wireshark in the background. This will let you see whether your laptop is sending out and receiving the DHCP packets.

---

### Post by Scooter_X on 2009-11-24
If you can't fix it, send it to me instead of breaking it, please?

---

### Post by tgalati4 on 2009-11-24
man iwconfig

It could be as simple as "key open" vs "key restricted"

A restricted key is also known as a shared key.

---

### Post by mcgrof on 2009-11-25
If you are having issues with ath9k on ubuntu 9.10 please upgrade to the linux-backports-modules package and let us know if you have issues.

Also please refer to the upstream documentation:

[http://wireless.kernel.org/en/users/Documentation](http://wireless.kernel.org/en/users/Documentation)

---

### Post by mcgrof on 2009-11-25
Oh I just noticed you said hardy. That's ancient, but you can still try the new stable release from compat-wireless:

[http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)

In a couple of days you can also try the bleeding edge release:

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Or you can just try it now. But in a few days a new fix should be merged for AR9285 as well.

---

