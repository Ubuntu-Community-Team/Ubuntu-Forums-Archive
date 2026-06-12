---
title: "should my wireless be labeled as eth1 in ifconfig?"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by amillionsheep on 2010-01-31
It is. I think this might be the reason why my $wireless objects don't work in Conky? Any guidance?

---

### Post by Iowan on 2010-01-31
My (Jaunty) laptop calls its wireless interface eth1 - but it works. There was a similar thread - suggestion was to change definition in */etc/udev/rules.d/70-persistent-net.rules*

---

### Post by chili555 on 2010-01-31
Wireless interfaces come in all creeds, colors, religions, and national origins. Some are wlan0, some are eth1, there is ra0 and more. Does Conky have a configuration file somewhere that allows you to change variables? Can you change wlan0 to eth1?

---

### Post by amillionsheep on 2010-02-03
Yeah, turns out it doesn't matter. As for the $wireless functions in Conky, it was a permissions issue. Had to run as sudo. 

Now to figure out if this Acer Aspire D250 has any sensors worth monitoring. I installed lm-sensors. Any standalone programs that I can use to check what sensors I have/if they work?

---

### Post by chili555 on 2010-02-03
Did you run *sensors-detect*?

---

