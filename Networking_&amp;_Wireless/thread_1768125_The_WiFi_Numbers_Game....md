---
title: "The WiFi Numbers Game..."
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2011-05-26
Here is a game you can play on your own, in the privacy of your own home, just sitting in a easy chair!

This is how to play:-
 - Select an easy chair some distance from your access point.
 - Open your web browser and access your wifi router.
 - Set your wifi to channel 1.
 - The "signal" reading will probably flicker between 3 or 4 values, record the lowest.
 - Record the speed. This can be seen in the "Connection Information" by right clicking on your network icon.

Repeat this for all channels and tabulate the results.

Here is a sample set of data from one of my routers:-
```

Channel	Signal	Speed(Mb/s)
1	16%	1
2	16%	11
3	16%	11
4	41%	1
5	27%	1
6	39%	1
7	35%	1 (intermittent: 0-1)
8	18%	11 (intermittent: 0-1)
9	35%	11
10	20%	5.5
11	23%	1
12	16%	1
13	16%	1

```
So what do these numbers mean?

The "signal" value is often assumed to be signal level/strength, but is usually calculated with regard to lost data packets.
It should be reasonable to select a suitable channel based upon "signal", but there does not appear to be a correlation with "speed".

Up 'til now I have been using channel 13 on the basis that my neighbours are generally clustered around channels 1, 3, & 6. I'm also aware that there are a couple of video senders operating nearby, polluting channels 1 to 4.

But I guess I need to reconsider channel selection based upon data rate/speed, as this is what really counts!

---

### Post by cdaringe on 2012-01-23
Ah, thanks. looks like the BASIC-eque syntax allows you to pipe in your input, then parse though it line by line.  my attempt was a bit sloppier, just dumping the full iwlist output into a python string and scanning through.  thanks for the share!  ill bookmark this.  im interested in giving GAMBAs a go.  i'm decent in vb6 & .net [they make ya learn it in school!], if they make GAMBAS cross-platform, boy howdy, that'd make my day.

---

### Post by cdaringe on 2012-01-23
oops, meant to post that over @ [http://ubuntuforums.org/showthread.php?p=11631566#post11631566](http://ubuntuforums.org/showthread.php?p=11631566#post11631566)

---

### Post by IslandBill on 2012-01-23
> **SteveDee said:**
> 

But I guess I need to reconsider channel selection based upon data rate/speed, as this is what really counts!

Have you thought of using 20MHz bandwidth, or are you already doing so?

---

