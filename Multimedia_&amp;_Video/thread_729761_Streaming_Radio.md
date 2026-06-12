---
title: "Streaming Radio"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by garthcrocker on 2008-03-20
Hi! Anybody good at math? I have a 'fair usage' restriction on my broadband and I'd like to know how many MBytes it takes to stream 128bps radio for one hour. I worked it out but my ISP reckons it's much more! Am I getting my bits confused with my Bytes? Probably!

---

### Post by p221072 on 2008-03-20
Hi,
normally radio stations broadcast at 64/96/128 kbps = kilo bit per second.
So 128 kbps means, 3600 time in an hour => 460800 kb divide 8 to obtain bytes => 57600 B or 56 MB [mega bytes] every hour.
Hope this helps,
cheers
Paolo

---

### Post by garthcrocker on 2008-03-20
Many thanks for that. That's what I made it too! My ISP tried to say it was much more. Probably wanted to persuade me to upgrade to a bigger package.

---

### Post by p221072 on 2008-03-20
It could be that the 128 kbps is just the music streaming so there could be some extra info broadcasted but I'm pretty sure we're talking about a negligible amount of data.

---

### Post by xzero1 on 2008-03-20
Don't forget you are likely using tcp/ip to receive this stream. The stream is not a naked audio stream. The protocol places your data inside of ip packets which are transferred over the internet.
The same packet can be retransmitted if not received in time. Bottom line: it is more complicated and larger than your calculations indicate.

---

### Post by kaivalagi on 2008-03-29
If you are not bothered about the technicalities then don't bother reading any further :)

Generally speaking, you are looking at a 40byte header for each tcp/ip packet sent, the data for each packet varies based on a number of factors, a rough guide is 1500bytes for the maximum length. The data itself will then contain headers again to compliment the audio stream, which is itself 128Kb/s.

If you want to read up, take a look here:
[http://en.wikipedia.org/wiki/Transmission_Control_Protocol]("http://en.wikipedia.org/wiki/Transmission_Control_Protocol")
and here:
[http://en.wikipedia.org/wiki/Maximum_segment_size]("http://en.wikipedia.org/wiki/Maximum_segment_size")

If the header size=40+20 (audio stream header guess) = 60 bytes, you're looking at an additional 4% for the stream (60 / 1500), not a great deal...That would mean a couple more meg per hour.

It is really difficult to estimate what additional percentage of overall packet size the header info equates to. If you REALLY want to know you could log the amount of data received over the course of a few minutes, and figure out what this would be projected over the course of an hour...it will probably still be below what your ISP is telling you...

Without logging this can only be a rough guide as each ISP will no doubt tweak their network management settings which will affect all of this...:)

---

