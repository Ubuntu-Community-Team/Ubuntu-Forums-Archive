---
title: "Painfully slow wireless speeds in Ubuntu laptop"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by dyslexicfurby on 2011-02-21
This problem seems to happen semi-randomly, making it very hard to pin down. I have a Toshiba Satellite laptop (L305-55962), and at seemingly random intervals the wireless gets so slow it's unusable.

This only started happening recently, and as far as I can tell it only happens at night time, if it happens at all. Usually it's not a problem but if I want to crack open my laptop at 1 in the morning, there is a risk that the wireless will be unusable.

It connects fine, I had about 92% connectivity. But pages were taking many minutes to load, if they would load at all. I barely managed to get a speed-test website up, and my connection was so poor, the speed test would not function (latency was too high I guess).

I don't think it's my ISP, because I have a desktop with Windows XP and an ethernet cable to the wireless router, and my speeds are always fine on that machine. What could cause random slowdowns in wireless speed with Ubuntu?

Also, I just opened my laptop now, and it's fine. The problem seems random, and usually at night. I do share a wireless network with 3 other roommates but they're all sleeping at that hour and their internet usage never interferes with mine.

---

### Post by KegHead on 2011-02-21
Hi!

I've found that on my compaq wifi it's very slow sometimes.

It's because it's picking up another connection.

I just go in and select my wifi, and all's well.

KegHead

---

### Post by dyslexicfurby on 2011-02-21
> **KegHead said:**
> Hi!

I've found that on my compaq wifi it's very slow sometimes.

It's because it's picking up another connection.

I just go in and select my wifi, and all's well.

KegHead
I think I tried that already, and it didn't help. I'll try it again next time it happens.

---

### Post by KegHead on 2011-02-21
Hi!

It might be the time of the day. I.E. around 3:00 cdt it's very difficult to get a connection--schools out!

KegHead

---

### Post by dyslexicfurby on 2011-02-21
> **KegHead said:**
> Hi!

It might be the time of the day. I.E. around 3:00 cdt it's very difficult to get a connection--schools out!

KegHead
But then why are speeds on my desktop just fine at that hour?

---

### Post by Keiran230 on 2011-02-21
This sounds like an interference problem with a neighbor. The best thing to do in this scenario, if you have access to your router, is to change which channel it's broadcasting on. In the US, we can use channels 1 - 11, but only 1, 6, and 11 are really usable (the channels are so close, they bleed into each other). It's best to stay off the same channel as your neighbor, or you may interfere with one another. There are many tools to scan wireless networks for their channels; I believe iwscan can do this.

If you're in an area with 4 or more people on each of these three channels, you may use 3, 4, 8, or 9. You'll interfere with each other some, but you'll at least put some distance between yourself and them. (Some countries allow channel 14, but the US doesn't.)

If this doesn't work, try moving the router/access point to another spot in the house if you can.

There's also 802.11N routers/access points and adapters, but be warned: if a 802.11G adapter connects to an 802.11N wireless network, the network will fall back into G mode.

---

### Post by dyslexicfurby on 2011-02-21
> **Keiran230 said:**
> This sounds like an interference problem with a neighbor. The best thing to do in this scenario, if you have access to your router, is to change which channel it's broadcasting on. In the US, we can use channels 1 - 11, but only 1, 6, and 11 are really usable (the channels are so close, they bleed into each other). It's best to stay off the same channel as your neighbor, or you may interfere with one another. There are many tools to scan wireless networks for their channels; I believe iwscan can do this.

If you're in an area with 4 or more people on each of these three channels, you may use 3, 4, 8, or 9. You'll interfere with each other some, but you'll at least put some distance between yourself and them. (Some countries allow channel 14, but the US doesn't.)

If this doesn't work, try moving the router/access point to another spot in the house if you can.

There's also 802.11N routers/access points and adapters, but be warned: if a 802.11G adapter connects to an 802.11N wireless network, the network will fall back into G mode.
I had not considered changing channels...I will have to try that. Although if the channel was bad, wouldn't that mean the wireless signal would be constantly crap?

---

### Post by Keiran230 on 2011-02-21
Yes or No. It depends on your neighbors. If you clash with the channel used by someone else, but they hardly use their network, it won't bother you at all. If they constantly torrent, download, stream, or do anything that uses their bandwidth, you'll notice  a lot. - They could just torrent at night, but not in the day, or something

---

### Post by KegHead on 2011-02-21
Hi!

Keiran230, you're correct.

KegHead

---

### Post by dyslexicfurby on 2011-02-21
> **Keiran230 said:**
> Yes or No. It depends on your neighbors. If you clash with the channel used by someone else, but they hardly use their network, it won't bother you at all. If they constantly torrent, download, stream, or do anything that uses their bandwidth, you'll notice  a lot. - They could just torrent at night, but not in the day, or something

I'll have to investigate this. I will report later when I have more information.

---

