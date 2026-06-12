---
title: "Lucid - flaky wireless: how to dig further"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2011-11-03
I have recently replaced a machine running 9:10, with a higher-spec machine running 10:04. This is a "server"

Machine has 2 network cards - and onboard eth0 which connects perfectly to my Homeplug network - no issues there. eth0 is the default gateway on 192.168.1.x

I moved from the old machine, a PCI wireless card which gives me wlan0. This connects to a completely separate network 192.168.2.x. This is my home-office network, and I connect from my office laptop, to the machine using X2Go. Previously, I had no issues whatsoever with this connection - it would stay up indefinitely.

The new machine is in the exact spot the old one was, and the home-office router has not moved. But I now have odd intermittent connection problems which upset X2Go, and drop the session.

Running a constant PING from my laptop to the machine, I get a few dropped packets ever so often. This is bi-directional, as running a constant PING from the server to the router also logs dropped packets.

The output of iwconfig wlan0 is

```
wlan0     IEEE 802.11bg  ESSID:"???????????????"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: B0:E7:54:1F:51:59   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

which seems to suggest that power and radio properties are quite good.

There's nothing (I know of) going on around me in the RF space to cause wi fi issues.

Can anyone suggest further diagnostics I can run to locate any issue ?

---

### Post by Jethro_uk on 2011-11-03
Hmmmm

noticed the card was using the rt61pci driver, which has been fingered as suspect by many. Have removed from modprobe, and used ndiswrapper to install Windows drivers. So far (last 60 mins) have now got back to 100% pinging. If this carries on till tomorrow, I will mark this as solved.

There was a community wiki about backporting from rt61pci to rt61, but I could use it, because they slipped in halfway through that if you don't have a "rev B" card (I don't) then you have to remove network manager. Now personally I *like* nm. I have got used to it. And I don't really see that removing it (and thus being unable to manage networks) is an acceptable trade off to get a working driver. Strikes me as fixing your engine by removing your steering wheel.

e2a:
Incidentally, iwconfig wlan0 now gives
```

wlan0     IEEE 802.11g  ESSID:"??????????"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: B0:E7:54:1F:51:59   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:D79B-C6AA-EEE0-9B9C-9F59-0065-CB7E-A4E2   Security mode:restricted
          Power Management:off
          Link Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I see we now have "noise" and "sensitivity" values ... so maybe the driver is able to react better to RF chatter ?

---

### Post by Jethro_uk on 2011-11-03
Stuff it, connection has been up, and rock-solid for nearly 3 hours now. It's fixed.

---

