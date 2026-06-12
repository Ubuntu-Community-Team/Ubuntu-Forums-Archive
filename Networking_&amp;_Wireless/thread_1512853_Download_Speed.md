---
title: "Download Speed"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by GeorgeOfTheBush on 2010-06-18
I am connected to a broadband internet service of **0.5** M**b**ps (download speed). This is confirmed by a test on speedtest.net.

However, while downloading files from the internet, say thru firefox, the download rate hardly exceeds **30-40** k**B**ps. Why is the difference?

Is there any way I can increase the download speed? Thanks for your help!

I am using Ubuntu 10.04 and Here's the output of *_**iwconfig**_*.

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"georgeofthebush"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:40: D0:A2: D0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Please let me know if I need to provide any other info.

---

### Post by Windows Nerd on 2010-06-18
> **GeorgeOfTheBush said:**
> I am connected to a broadband internet service of **0.5** M**b**ps (download speed). This is confirmed by a test on speedtest.net.

However, while downloading files from the internet, say thru firefox, the download rate hardly exceeds **30-40** k**B**ps. Why is the difference?

Is there any way I can increase the download speed? Thanks for your help!

I am using Ubuntu 10.04 and Here's the output of *_**iwconfig**_*.

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"georgeofthebush"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:40: D0:A2: D0   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```Please let me know if I need to provide any other info.
Well, your download speed can be limited by:

The server that you are downloading from: the server that you are downloading from can be the bottleneck: I sometimes have crummy download speeds from some servers/websites as compared to if I download via other servers or download via Torrent.

Bandwidth: If something else on your network is using the internet (such as an Xbox or server) or something else is downloading something very large at higher download speeds, that may be using your bandwidth, and slowing down your DL speed.

Given that speedtest read a much higher DL rate than what you experience with most downloads I am betting it is the first reason I mentioned.

Scott

---

### Post by GeorgeOfTheBush on 2010-06-19
Thanks Scott for your response.

You have pointed out that the server from where I download from could be the issue. My problem is that [COLOR=Blue]**EVERY DOWNLOAD**[/COLOR] i.e. 100% of my downloads [COLOR=Red]hardly exceed 30 kBps[/COLOR]. Does that mean every server has a problem? That can't be the case.

I would say the speedtest.net test is the [COLOR=Red]ONLY EXCEPTION[/COLOR] - which shows a high download rate - I dont know how.

Is there any way I can increase the webpage load / download speed?

---

