---
title: "ath5k driver modifications"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by atilia on 2009-07-21
Hello Guys,

I have a project to do. It is based on Wi-Fi network measurements. I red that ath5k with its OpenHAL is convenient to use for these purposes.

Could you please advise, which variables (ath5k.h?) are responsible for the following values to measure:

   
[LIST]
[*]Bandwidth (avaliable, busy)
[*]Delay
[*]Bit error ratio
[*]Frame      Error Rate
[*]Signal-to-noise ratio
[*]Received signal strength indication      (RSSI)
[*]MAC      address
[/LIST]

Or do you know any linux open src software that works in similar way?

Cheers 
at

---

### Post by bacil on 2009-07-21
iwconfig gives you most of these
```

          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:48:DF:55:FA
          Bit Rate=12 Mb/s   Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=68/100  Signal level:-52 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

so i guess you can use its source for your project .. and it will work with any chipset not only on atheros

---

### Post by atilia on 2009-07-21
Thanks bacil,

Many information from iwconfig are very useful, but I am still missing BER and FER, so layer 1 and 2 (iwconfig only displays packets from layer 3) 

Trying ipref application now, maybe it will provide more details about lower layers

Cheers
at

---

