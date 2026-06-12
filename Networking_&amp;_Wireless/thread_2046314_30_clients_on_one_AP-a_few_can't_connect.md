---
title: "30 clients on one AP-a few can't connect"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by biodojo on 2012-08-22
Hello,

In our school with have Acer netbooks running 12.04. They have Broadcom 4313 chips using the wl driver. They will connect fine in small numbers, but once we get a full class trying to connect at once there are always 5-8 that keep trying to connect. It is an enterprise managed wireless from a company called Ruckus. We are asking them from help, but I wanted to post the logs from tail -f /var/log/syslog and see if anyone saw any clues as to what was preventing connection.

The log attached essentially repeats over and over again, I believe I got one full loop. If I take the netbook to a room farther away it instantly connects (but then when I bring it back, it loses connection). We tried having overlapping AP's but that was causing another issue in which Network manager said the laptop was connected, but you couldn't ping anything.

As I said, we are also contacting support for the wireless system itself, but we haven't had this issue with our windows clients so it might be some interaction of the AP and Linux.

---

### Post by Kirk Schnable on 2012-08-22
I also work in a school environment, but we're a Cisco house.

We have found, in a testing environment, we could succeed in connecting almost 100 clients to a single AP. (I think around 95).

However, at this rate, we had significant packet loss and latency worse than that of satellite Internet (something like 5000ms) to our LAN.

We proceeded to lower the client count.  We found that around 30 clients, our wireless became usable.  Around 25, it was in good enough condition to watch YouTube on one of the laptops without affecting the others.

I don't know how your equipment compares to Cisco equipment, but 30 is seriously pushing the limit even on commercial access points.  Because wireless is a token-ring topology (only one client can communicate at a time) the polling interval gets too long and performance degrades significantly.

At the school I work at, we are starting a 1 to 1 computing initiative this year, with ~200 incoming freshmen receiving netbooks.  Wireless coverage density has been a significant part of our planning, and our hard work paid off with a rock solid wireless network so far.

I'd be happy to look over your coverage density and give you my two cents.

Kirk

---

### Post by Hadaka on 2012-08-22
hi,
In a crowded RF environment, clients might not be able to detect the desired SSID because of internal table limitations. Sometimes disabling and then enabling the client interface forces a rescan. Your RF environment needs to be controlled. UWN rogue access point detection and containment can help you to enforce RF policies in your buildings and campuses. Sounds like this may be a possibility, You state when you go to another area
with the notebook, it connects and then disconnects as soon as you enter the RF filled
room with the other notebooks. Rukus may have a way to reset or increase the tables
that adjust the number of clients to a single AP.

---

