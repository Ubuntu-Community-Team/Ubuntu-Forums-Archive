---
title: "DWL-G122 (C rev) 9.04 Ubuntu and Inbuilt wireless"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Peleus on 2009-05-09
Hi all, 

I've got an older M50 Toshiba laptop which has an inbuilt G wireless adaptor (read crappy one). 

Because of continuous drop-outs and crappy speeds via the inbuilt adaptor I'm trying to use my DWL-G122 wireless dongle which is the C revision to connect to the network instead, this of course works fine in windows (i.e. not faulty hardware). 

Upon booting up Ubuntu, with both the dongle and wireless inbuilt enabled, I see both units installed and "connecting" to my network. The output of iwconfig is as follows. 

```
eth1      IEEE 802.11g  ESSID:"Peleus (Netgear)"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:18:CF:34   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/100  Signal level=-37 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:31

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Peleus (Netgear)"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:18:CF:34   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=66/100  Signal level:-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

No worries, I believe eth0 is the inbuilt, wlan0 is the Dlink. 

From here, if left as is I get no internet connection, I'm not sure if it's a conflict between the two units or what, but regardless it does not work. I wish to use the Dlink only, so I switch off (manual switch on front of laptop) the inbuilt however my Dlink drops the connection as well, because wireless isn't enabled it seems, again iwconfig output is as follows. 

```
eth1      radio off  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It seems not only does the switch kill eth0, but somehow kills the association on wlan0. If I do the reverse, and leave the laptop wireless on, and unplug the Dlink I get a slow unreliable but working connection. iwconfig output finally as follows. 

```
eth1      IEEE 802.11g  ESSID:"Peleus (Netgear)"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:18:CF:34   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=-38 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:4  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:35

```

No wlan0 is listed. 

If anyone can tell me how I can disable eth0 while keeping wlan0 up and working, so I can use this connection I will be forever in your debt. I've tried to include all of the information needed but if you want to see any output's no worries I'll post them here. 

I can't see any network hardware GUI in ubuntu to enable me to enable one and disable another. 

Any response is appreciated.

---

### Post by Peleus on 2009-05-09
Updated - 

Tried having both in, typed in ifconfig eth1 down, this resulted in an error being kicked up "SIOCSIFFLAGS: Permission denied". I then tried sudo ifconfig eth1 down, it executed the command, however upon doing iwconfig again it was still listed as active. 

Any further idea's appreciated.

---

### Post by Peleus on 2009-05-09
Still no suggestions?

---

### Post by Peleus on 2009-05-10
Not trying to be impolite but bumping again. 

Anyone know how I can bring down eth1?

Anyone know why ifconfig eth1 down isn't working?

I've tried to include as much information as possible for everyone to be useful and get an answer. Any help is really really appreciated. 

No fix that I've been able to find, I'm sure this is most likely come up before somewhere though?

Thanks.

---

### Post by w.yu on 2009-07-18
hi Peleus,

not sure if you'll see this but:

[http://0x80.org/blog/?p=145](http://0x80.org/blog/?p=145)
"just blacklist it in /etc/modprob.d/blacklist
for example add this line
  “blacklist iwl8082&#8243;
where iwl8082 is the driver the builtin wireless card uses it “lsmod” to know your drivers"

although it should be /etc/modprobe.d/blacklist.conf

works for me.

---

