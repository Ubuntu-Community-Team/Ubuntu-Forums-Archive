---
title: "Wireless Network Locator"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by Stabback on 2009-02-26
Hey all, I'm looking for a tool to find wireless networks (not the built in wireless network finder found in Ubuntu).  I'm looking for something a bit more advanced which auto refreshed, tells where networks are in proximity to you and lets you know if you're getting closer or farther away from a source.

I'm using a Dell XPS M1710, unfortunately I do not know my wireless card.  If anyone can help me find out what I have that would be great.

Thanks a ton

---

### Post by Mordac85 on 2009-02-27
Have you looked at [Kismet]("http://www.kismetwireless.net/")?  It's one of the best out there, imho.

As for your wireless, the M1710 looks like it comes with either the Truemobile 1490 or 1500.  You should be able to see it using lspci.  If you don't already have it running, you may want to check the restricted drivers to see if one is listed there, or you can always use ndiswrapper.

---

