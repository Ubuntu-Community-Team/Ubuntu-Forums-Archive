---
title: "Network Bandwidth reducing"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Achayaan on 2010-03-04
Hi all,

Now i am happy coz all my linux issues is fixed and now i am fully in ubuntu . but maybe I need a small help about gyachi ... when ever i will start my webcam and I will view my friend webcam that time my all internet resource using by gaychi . Is there any application that I can limit internet use og gyachi ??

I am sorry for my bad English :)

thanks

---

### Post by Achayaan on 2010-03-05
Please help me :(

---

### Post by 2hot6ft2 on 2010-03-05
You might take a look at wondershaper it's in synaptic
> An easy to use traffic shaping script that provides these improvements:
 * Low latency for interactive traffic (and pings) at all times
 * Allow websurfing at reasonable speeds while uploading / downloading
 * Make sure uploads don't hurt downloads
 * Make sure downloads don't hurt uploads

It does this by:
 * Limiting upload speed slightly, to eliminate queues
 * Limiting download speed, while allowing bursts, to eliminate queues
 * Interactive traffic skips the queue
 * ACKs and tiny packets skip the queue

Configuring the wondershaper requires you to accurately and precisely
determine your consistent upload and download speeds.

The wondershaper is the simplest, easiest to use, entry level, traffic
shaping script provided by Debian.

After installing this package, read highly the detailed instructions:
/usr/share/doc/wondershaper/README.Debian


---

### Post by Achayaan on 2010-03-06
I tried to use wondershaper but I dont know how i can use it for only one application :(

---

