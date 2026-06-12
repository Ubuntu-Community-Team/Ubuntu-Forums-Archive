---
title: "Combining network connection"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by nainsurvolte on 2012-12-26
Good day,

A while ago, I went around multiple forums and internet sites to get an answer to one question: How can I combine 2 network connections to make only one in the end? I did find some lead, but that were never a 100% match to my need. I tried them a bit but with no success.

My knowledge of Linux is limited but ok considering that I installed, ran and managed my mythbuntu server for over a year without requesting help, but this one is over my Linux capacity to understand and would need a fairly detail step by step procedure.

I can sense the question, Why? Well, this machine will become the central server of the house, hosting files that are downloaded from all machines, media server for 2 XBMC machines and Mythtv backend, all at the same time. I will have over 8TB of space, and I want to have maximum throughput.

Hardware wise, the network card is a StarTech ST1000SPEXDP.

Thanks,

---

### Post by iponeverything on 2012-12-26
Not likely your going to a "step by step" with the information you provided.. as the person giving it would have to a physic..

linux supports bonded interfaces, the device that it is connecting to also has to support interface bonding.

I see the value in this as coming from learning the experience, and not from the added throughput. A Gbit interface and easily support streaming to number of end points you mentioned, you also omitted the interface characteristics of the attached devices.. Its unlikely that there is a practical point to the exercise, so I would say .. just have fun with it as good way to learn a bit..

---

### Post by nainsurvolte on 2012-12-26
Trying to summarize your answer... 

> Not likely your going to a "step by step" with the information you provided.. as the person giving it would have to a physic..

linux supports bonded interfaces, the device that it is connecting to also has to support interface bonding.I can provide more information if need be. As I said, I can make my way through linux with explanation as long as they are not underlying a whole lot of advance knowledge prerequisite.  Network wise, I have 2 Netgear gigabit switches (1 unmanaged, the other Managed) and the network is driven by a Cisco RVS4000. If the Cisco is a problem, I just bought a wireless router to act as an WAP but it can be DD-WRTed.

> A Gbit interface and easily support streaming to number of end points  you mentioned, you also omitted the interface characteristics of the  attached devices.. Its unlikely that there is a practical point to the  exercise, so I would say .. just have fun with it as good way to learn a  bit..     Characteristic of the devices are 
1) HTPC with Gigabit interface running openelec
2) Xbox 1st gen running XBMC
3) Win 7 pc with Gigabit interface
4) Laptop with Gigabit interface or Wireless N
5) Tablet with Wireless N
6) HDHomerun

On a day to day basis, I understand that what I have is more then enough. But sometimes I do mass file transfer from Server to Win7 machine to make some TVShow compressions and sometimes I see a drastic drop in speed if multiple activities occur between the server and other devices (from 40-30 MB/s to 14-15 MB/s). Maybe I am looking at the wrong bottleneck...

But in the end, is the network bonding benefit only marginal so that actual results looks ok?

---

### Post by iponeverything on 2012-12-26
Google "linux bonded interface configuration" for server side.

For the device that connected to, use google to find out if supports bonding. 

dd-wrt is better than stock in a few cases, but the extra features are not worth the extra bugs,  openwrt is better in most cases.

---

