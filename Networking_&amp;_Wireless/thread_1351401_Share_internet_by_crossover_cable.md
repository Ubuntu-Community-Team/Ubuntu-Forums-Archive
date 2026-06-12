---
title: "Share internet by crossover cable"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by Kdar on 2009-12-10
How can I share internet connection by crossover cable?

I have Ubutnu on my laptop. On there, wireless and everything works.

However I am trying to install Arch-linux on my main (desktop) PC. And there, during basic install, it can not detect my wireless connection.

How can I share connection from my laptop with my desktop?

I would prefer to know a way to do it in CLI. Since on my desktop I don't have any graphical environment yet.

---

### Post by Iowan on 2009-12-10
[HGere]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is an ICS help page. From what I've briefly read, it seems CLI-oriented.

---

### Post by Kdar on 2009-12-12
I tried it, but it doesn't work.

On my laptop, I have wireless connection: wlan0
```
wlan0     IEEE 802.11abgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1B:11:E4:A7:91   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

How can I connect wlan0 to eth0 inside of my laptop?

---

### Post by Iowan on 2009-12-12
What part doesn't work? Can you **ping** the laptop from the desktop?
[Here]("https://help.ubuntu.com/community/BridgingNetworkInterfaces") is a help page for bridging - dunno if it is exactly what you're looking for.

---

### Post by Kdar on 2009-12-12
Sorry. I was able to solve my problem.

I just didn't know how to connect to wireless network by command line. So sharing internet is not necessary now.
But thank you.

---

