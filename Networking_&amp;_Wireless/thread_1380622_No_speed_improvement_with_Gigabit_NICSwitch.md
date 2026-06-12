---
title: "No speed improvement with Gigabit NIC/Switch?"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by WinstonChurchill on 2010-01-13
I recently upgraded a server's networking card to a Gigabit NIC, and got a hold of a Gigabit switch ([Here's a link]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127082")) in the hopes of increasing my network performance - however, I'm getting around 10 MB/s throughput now, which is exactly what I used to get with the old 10/100 switch & NIC. The new switch recognizes both computers as Gigabit (the other machine has always had a Gigabit NIC), and both computers say they're gigabit - so I have no idea what the problem is.

I've found various sites around the interwebz recommending tweaking some TCP/IP buffer settings, which I have tried to no avail. I also saw that hard drive speed is usually the limiting factor. According to "hdmarp -t", the server HDD (definitely the slower of the two) is:
```
Timing buffered disk reads:  226 MB in  3.00 seconds =  75.26 MB/sec
```... so that's obviously not my issue. The cabling is CAT6 - I ran it myself, but if I'd mis-wired the end connections, wouldn't it just not work at all? I admit, I bought cheap NIC's (I'm not going for like 124.9 MB/s throughput here..), and I didn't expect them to be stellar, but I certainly expected the speeds to improve.

I'm moving files from a server running Ubuntu 9.04 to a Windows machine - I've tried both my Samba shares on the server and an SFTP transfer: they both have about the same throughput.

Any and all help is appreciated - thanks in advance.

---

### Post by changingstate on 2010-01-14
> I ran it myself, but if I'd mis-wired the end connections, wouldn't it just not work at all?Not quite. 10Mb/s cables only need four of the pins wired correctly, while 100Mb/s cable need all eight. 

There's some nice wiring instructions here : [http://www.zytrax.com/tech/layer_1/cables/tech_lan.htm#100s](http://www.zytrax.com/tech/layer_1/cables/tech_lan.htm#100s) and wikipedia will tell you how the cables are paired : [http://en.wikipedia.org/wiki/10BASE-T](http://en.wikipedia.org/wiki/10BASE-T)

Now, it doesn't matter if you've got the colours wrong, so long as the pairs are wired correctly ( ie; white/green and green could go into either pins 1+2 or pins 4+5 ) and both ends of the cable match. 

Also, the output of 'dmesg | grep duplex' should give us an idea of the speed your NIC's are connecting at on each machine. Might help us localise where the slow point is.

---

### Post by WinstonChurchill on 2010-01-19
Ok, I've established that it's not the hardware - but I have no idea whatsoever what might be causing this. Take a look:

[IMG]http://img51.imageshack.us/img51/900/thingytwt.png[/IMG]

(The gridlines are at 3 second invervals). The section labeled "A" was me dumping a 1.5 GB file to the server FROM my desktop. The section labeled "B" was me pulling that same 1.5 GB file back to my desktop from the server. BUT, the section labeled "C" was me pulling an Ubuntu ISO off my server that's been there for awhile... and it behaves that way for most files that are already there - it starts off at the full rate, then rapidly drops down to about 5 MB/s. 

We've looking at around 40 MB/s in sections "A" and "B", but barely 5 MB/s in "C". I've experimented with changing owners and permissions to no avail. It seems that the only time I can get the same throughput downloading files as uploading them (from the desktop) is when it's a file that I just uploaded.

I've perused the man pages for Samba, and I don't see anything related to this... any ideas?

---

