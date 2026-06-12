---
title: "download speeds are suddenly slow"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by evanct on 2011-04-27
I've been using wireless with my Linksys WRT300N router on my 10.10 box with no problems for months now. Then suddenly a few days ago my downloads, both HTTP and torrents, drastically slowed. A well-seeded torrent used to give me anywhere from 500kb to 2MB per second; now I'm lucky if I get over 100kb/s, regardless of which client I use and whether the port is open. Downloads from Megaupload used to be consistently fast, up to 1.5mb/s, now they average 200kb/s.

Meanwhile I go on my Windows 7 partition and all my download speeds are normal.

Anyone know what the problem could be?

---

### Post by evanct on 2011-04-28
bump. the 11.04 files are DLing at an excruciating 50 kb/s.

---

### Post by IWantFroyo on 2011-04-28
Same here...
I had the same problem in the betas and alphas, but I expected a fix by now.

---

### Post by AlanR8 on 2011-04-28
Went on to Natty in an early Alpha release but went back to Lucid because of poor wireless download speeds. 

However, I isolated MY problem as power management kicking in on the wireless card when running on battery. DIRE download speeds. Plug in the mains and all was sweetness and light again.

Check out your situation. The command to switch power saving OFF is:

> sudo iwconfig eth1 power off

providing eth1 is the wireless adapter in your machine.

Let us know how you get on.

---

### Post by evanct on 2011-04-28
That doesn't really apply to me as I'm using a desktop, not a laptop. Checked power management anyway, it's off.

---

### Post by IWantFroyo on 2011-04-28
> **AlanR8 said:**
> Went on to Natty in an early Alpha release but went back to Lucid because of poor wireless download speeds. 

However, I isolated MY problem as power management kicking in on the wireless card when running on battery. DIRE download speeds. Plug in the mains and all was sweetness and light again.

Check out your situation. The command to switch power saving OFF is:



providing eth1 is the wireless adapter in your machine.

Let us know how you get on.
Thanks! This helped a lot.
PS add your networking card in instead of eth1. The average wireless user has 'wlan0'.
For ethernet, it may be eth0, if eth1 doesn't work.

---

### Post by evanct on 2011-04-28
Also if it helps, here's the output of iwconfig:

```
wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:59:04:0E   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by evanct on 2011-04-28
Okay, I just ran
```
sudo iwconfig wlan0 rate 54M
```
and now everything seems to be normal. Not sure why I suddenly had to do that.

---

