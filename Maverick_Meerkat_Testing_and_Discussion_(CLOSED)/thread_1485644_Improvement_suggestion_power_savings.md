---
title: "Improvement suggestion power savings"
date: 2010-05-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SeanBlader on 2010-05-17
I've enjoyed watching the improvements to the boot speed, and I look forward to seeing what continual improvements come out of Meerkat as well, but...

I'm tired of the Mac's getting the long battery life out of their laptops. I'd like to see power saving as the next big area of improvement. I'm sure there's room for a 60% improvement with the right power management strategy, especially for netbooks and similar systems. Currently my Adamo according to powertop runs at about 1 watt at idle or at about 1.2 watts with me typing this message into the browser. It would be outstanding if the system was smart enough to autopower down bluetooth on it's own if no devices are currently in use. I'm sure there are plenty of optimizations that could be made, but I would expect to be able to go from about 3.5 hours on this system to somewhere in the range of 4.5 hours.

Compared to the 300% improvement we've seen in boot times over the last few releases, I don't think 60% battery life is out of the question for some systems. I definitely wouldn't put on hold anything like the UI improvements, or boot speed of course, but imagine a world where your computer is 30% more power efficient so the fans run less and the effect is a 45% reduction in power use for even high demand desktop systems.

---

### Post by Kobalt on 2010-05-17
I think improving battery life will be quite harder than improving boot speed, because battery life highly depends on hardware drivers... But of course, in the scope of the future Ubuntu Light Edition it would be great to improve in this area.

---

### Post by psusi on 2010-05-17
I'm working on this myself now.  I got a new Dell Vostro 13 Friday and installed laptop-mode-tools to get the hard disk to stay spun down as much as possible, then used libeatmydata to force chromium to stop forcing disk access and got the battery life up to the 4 hour range.  That's still consuming 7-8 watts though with the wireless on.  I also have made some optimizations to ureadahead and having defrag pack those files at the start of the disk and got the boot time down from 35 to 30 seconds.

---

### Post by rayraven on 2010-05-17
@psusi
Sorry for taking this offtopic, but i got a V13 as well and with laptop mode tools, it eats at about ~10 W with Wireless on.

Mind giving me your config and tips you used to get it to 7W?
I'd love to get the same battery life as you do. Currently, it gives me close to two and a half to three hours.

Regards,
ray

---

### Post by psusi on 2010-05-17
> **rayraven said:**
> @psusi
Sorry for taking this offtopic, but i got a V13 as well and with laptop mode tools, it eats at about ~10 W with Wireless on.

Mind giving me your config and tips you used to get it to 7W?
I'd love to get the same battery life as you do. Currently, it gives me close to two and a half to three hours.

Regards,
ray

The key is making sure that the disk actually spins down and stays that way.  I often keep a watch sudo hdparm -C going in a terminal window to make sure that the disk stays in suspend, and powertop will tell you when programs are doing writes, though it does not differentiate between writes to the cache and writes that force disk access.  Firefox is horrible about frequently calling fsync() which forces the write to happen now rather than the next time the disk is spun up anyhow.  Chromium was doing this some as well, until I used libeatmydata to disable its calls to fsync().  This allows the disk to stay spun down for up to 10 minutes, which is the length of time laptop-mode-tools defaults to configuring the journal commit time to.

---

