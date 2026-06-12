---
title: "Very slow internet connection"
date: 2006-05-21
forum: Networking &amp; Wireless
---

### Post by cykze on 2006-05-21
Starting from this morning, my internet connection has been terribly slow. The download rate is only at 60 kB/s compared to 1 MB/s, which it used to be. The internet connection works good in Windows.

I don't know what has happend and I didn't do anything strange to my Ubuntu system yesterday, as far as I remember.

Any ideas on how to troubleshoot this?

---

### Post by Kethinov on 2006-05-21
Strictly speaking, 99% of the time this is a hardware problem and not a software problem. I'm having a hard time believing you when you say you can get better speed on your internet connection in Windows than Ubuntu.

---

### Post by Slim Odds on 2006-05-21
There are SOOOO many things that can be involved with something like this. My ISP had a problem last Thursday with dropping packets. Similar results. Went away the next day. Very annoying but they are generally very reliable.

---

### Post by cykze on 2006-05-22
Today everything seems to be back to normal again. But there has to be an explanation for what occurred yesterday. I didn't do anything particular to the system neither today nor the day before yesterday. I restarted both the computer and the modem several times.

**Kethinov:**
> *I'm having a hard time believing you when you say you can get better speed on your internet connection in Windows than Ubuntu.*

So do I. But otherwise I would have blamed the ISP. Note that the internet connection usually works great in both Ubuntu and Windows.

**Slim Odds:**
'ifconfig eth0' didn't report any errors.

---

### Post by Slim Odds on 2006-05-22
> **Slim Odds:**
'ifconfig eth0' didn't report any errors.

eth0 is **only** your ethernet device. The problem was most likely with you ISP. Like I said before, my ISP had problems very similar to this one day last week. IP Packets were getting dropped. You won't see errors like that using 'ifconfig eth0'.

For example, I would ping a web site repeatedly. The sequence numbers would go something like this: 1,2,4,5,6,9,10,11...

Packets 3,7,8, etc were getting dropped for some reason. This destroys throughput for data transfer and also causes all kinds of other connection problems.

---

