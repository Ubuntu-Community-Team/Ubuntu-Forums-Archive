---
title: "Bandwidth Problem"
date: 2010-08-29
forum: Mythbuntu
---

### Post by agentsmith23 on 2010-08-29
I think I am running into some kind of network bottleneck somewhere. When accessing mythtv from my laptop I get very choppy playback. When I look at the bandwidth being used by my laptop it is constantly around 1MB/sec no matter if the video being viewed is HD or SD. Now if I look at the bandwidth being used on my router it is closer to 8MB/sec. I am using a G router and G connection on my laptop. Under the network connection information it shows 54MB/s speed. In the system monitor the processor is never fully stressed, it never gets above 75% load and the RAM is around 25% usage. What would be causing this?

Any idea what may be causing this?

---

### Post by ian dobson on 2010-08-29
Hi,

Wireless? Someone else using your internet connection. Have you setup strong passwords (WPA2)?

Run top from a terminal window to see whats using the CPU. My frontend sits at about 5% when idling at the menu and 10-20% when watching a video (SD or HD).

Regards
Ian Dobson

---

### Post by agentsmith23 on 2010-08-29
I am using wireless. I have verified no one else is connected to my wireless network. I can see that my wireless connection is taking in about 8MB/sec and putting out about 8MB/sec during HD playback and SD shows around 5-6MB/sec in and out. However the system monitor shows about 1MB/sec coming in for HD playback and SD shows about 500KB/sec coming in. And system monitor shows about 30% CPU usage for mythfrontend for SD and around 50-60% for HD.

---

### Post by ian dobson on 2010-08-29
Hi,

Could the different be Mb and MB (MegaByte / MegaBit)?

What hardware are you using on the frontend? If you have a newer NVIDIA graphic card have a look at vdpau. My frontend is is underclocked c2d (1200MHz) that plays back sd and hd with almost no cpu load (max 20%).

Regards
Ian Dobson

---

### Post by LowSky on 2010-08-29
Wireless G will never hit the max of 54MB/s. The idea of the max is the full availible, so that multiple machines can use the line, it can't/won't give you a full speed of the line no matter what. Streaming HD on on a wireless signal is very taxing. If your looking for more speed you will need to upgrade to Wireless N. It is actually prefferred for HD video watching. Also pick up a router that can do intelligent QoS. They can prioritize data and limit lower requests when needed.


If you're not sure if its a bandwidth issue, then copy a recording directly to your laptop and try to watch it and see the results.

---

