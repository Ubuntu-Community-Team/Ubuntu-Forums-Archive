---
title: "Slowest Torrent speeds I've ever seen..."
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by illusionz on 2009-06-22
So no matter what Torrent app I use, whether it be Transmission, or Ktorrent, my speeds won't go higher than like 10kbs.

In transmission, my speeds will jump to 800kbs for about 5 seconds, then drop right away.

I don't get it. I've got forwarded ports, static ip, and everything.

There something I'm missing?

I need my torrents :x

---

### Post by kelvin spratt on 2009-06-22
That sounds like isp capping has been implemented

---

### Post by AoSteve on 2009-06-22
I know I had to setup my "auto eth" connection manually to my router before things really started working properly.  However, it's most likely because the router was a POS.   Could be part of your problem?

After I entered my information and setup my eth1 connection, I was getting good service when my connection wants to work LOL    I pull about 125-140kb/s average with most healthy torrents with Transmission.   I have satellite internet service, so that's outstanding for me.  :)

---

### Post by sloggerkhan on 2009-06-22
tried deluge?

Though I have to agree, your experience sounds like ISP rate capping to me. Force encrypt your connections and/or try proxying, see if things change.

---

### Post by illusionz on 2009-06-22
No matter what I do, I just can't get anything to speed up at all. My windows machine is doing fine though~

---

### Post by illusionz on 2009-06-22
Could it be my drivers for my NIC?

How can I find out my nic card model in linux?

---

### Post by sloggerkhan on 2009-06-22
also, don't know what you're dl'ing, but if you're on a private tracker, it may filter connections by client. It may be that the version of whatever client you're using isn't on the approved list for the tracker you're using.

---

### Post by illusionz on 2009-06-23
No, they're good torrents... Fresh EZTV torrents. The swarms are strong on their torrents...

But I can't seem to get anything higher than 12kbs... And when I do, it just drops really fast back down to 12kbs, and doesn't go back up.

I know in Vista, on Laptops, if you don't disable the save power feature on the network card, it periodicly shuts down the connection to save power, thus causing this problem.

Is there anything like this to disable?

Last time I had a full linux machine was back when Dapper Drake came out, and alot has changed since.

---

### Post by sloggerkhan on 2009-06-23
I use EZTV sometimes, too. 
Two different torrents, one had 12 Seeds, 5 peers, one had 10 Seeds, 4 peers, one show came in at constant ~140kilobytes/sec, the other only at ~10kilobytes/sec. Who knows what the difference is. I do know that with torrents that aren't from piratebay's tracker (like EZTV is), I tend to get DL speeds more on the 300+ kilobyte range (Sometimes even 1 megabyte/sec), so I'm tempted to attribute your issue in this case to EZTV/piratebay just generally being slow, though it is curious that your windows client does better.

---

