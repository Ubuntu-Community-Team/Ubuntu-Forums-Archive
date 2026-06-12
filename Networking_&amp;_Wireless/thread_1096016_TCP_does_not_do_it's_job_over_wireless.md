---
title: "TCP does not do it's job over wireless"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by fixitdude on 2009-03-14
You go to a web site, it loads a little bit then sits there waiting. Then you hit STOP and load the page again and it comes through quick as usual.

I'm tired of this. Anyone else have that problem?

When your connection is on the edge of your connection range you will get noise in the transmission and TCP just can't handle it.

TCP programmers, please fix this. 2009 is calling.

The header checksum is the problem. What retard decided a checksum would be OK? Two bits get switched the right way and TCP thinks everything is OK and so the packet is sent to the wrong destination, it's gone, and TCP on the other end does nothing but sit there, lame.

TCP should keep track of the typical send / return rate from this guys connection and if it goes beyond the typical time, ask for a resend.

Better yet, that's just a patch. TCP should be properly changed to use something else, call it "TCP plus", I don't care, just fix it.

The checksum choice was really lame. Putting it in shows that someone was concerned that bits may be lost, but in a noisy environment such as wireless you only catch it 60% of the time. CRC would have been a better choice of course.

SSH connections get stuck because of this also. Please don't blame it on the wireless router, it uses standard TCP.

The only way to test this is to make something that simulates random bit flips in the header. But why bother? It's obvious, it's the CHECKSUM STUPID!

---

