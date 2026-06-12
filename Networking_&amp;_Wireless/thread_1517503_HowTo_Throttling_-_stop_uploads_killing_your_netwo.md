---
title: "HowTo: Throttling - stop uploads killing your network connection"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by rossmoore on 2010-06-25
Hi,

I just stumbled across this useful piece of information that I wish I had found on ubuntuforums.org.

**The Problem:**
I have found that using BitTorrent, or uploading an HD video to youtube.com, or using UbuntuOne can all lead to your computer using all of your available ADSL upload capacity. When this happens you find that you can't do anything on the net any more. Web browsing, or anything else on the internet, stops working until the upload is complete.

Now, thankfully both UbuntuOne and Transmission come with the ability to throttle their upload speeds. Of course, if both are trying to upload at the same time you're stuffed; and neither of those controls helps you when you upload that video, or album of photos.

The reason your connection appears to die is because your computer can't send a packet back to the website you're trying to browse saying that it is receiving the web page you're trying to view successfully. The upload link is full, and your modem has a massive queue of packets (that video you're uploading) waiting to go up your ADSL line.

**The Solution:**
The fix is relatively simple, and built into the Linux kernel already. As root, you run:
```
# tc qdisc add dev ppp0 root tbf rate 220kbit latency 50ms burst 1540
```

And now I'll quote from [the source of this information]("http://lartc.org/lartc.html#LARTC.QDISC"):

> 9.2.2.2. Sample configuration
A simple but *very* useful configuration is this: 
# tc qdisc add dev ppp0 root tbf rate 220kbit latency 50ms burst 1540
Ok, why is this useful? If you have a networking device with a large queue, like a DSL modem or a cable modem, and you talk to it over a fast device, like over an ethernet interface, you will find that uploading absolutely destroys interactivity.
This is because uploading will fill the queue in the modem, which is probably *huge* because this helps actually achieving good data throughput uploading. But this is not what you want, you want to have the queue not too big so interactivity remains and you can still do other stuff while sending data.
The line above slows down sending to a rate that does not lead to a queue in the modem - the queue will be in Linux, where we can control it to a limited size.
Change 220kbit to your uplink's *actual* speed, minus a few percent. If you have a really fast modem, raise 'burst' a bit.

So just set it there once and it will control every application. That tc command is immensely powerful, but very complicated. You can set very complex matching rules so that, say, UbuntuOne is throttled in one way and BitTorrent in another. Unfortunately I personally couldn't tell you how to do that...

Hope you found that snippet useful.
Ross

---

