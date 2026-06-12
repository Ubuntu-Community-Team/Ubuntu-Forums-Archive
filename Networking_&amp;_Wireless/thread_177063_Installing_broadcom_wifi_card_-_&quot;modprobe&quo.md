---
title: "Installing broadcom wifi card - &quot;modprobe&quot; never comes back"
date: 2006-05-15
forum: Networking &amp; Wireless
---

### Post by GraemeF on 2006-05-15
I'm using Dapper.

Hi guys, I'm a Linux n00b so please excuse me if this is a silly question. I've spent the last couple of days working through all of the "how to get your Broadcom wifi card working" articles and forum posts and I get stuck at the same point every time. ](*,) 

Everything goes fine up to the bit where I'm supposed to run
```
modprobe ndiswrapper
```
or
```
modprobe bcm43xx
```
When I run either of those it never comes back (although it doesn't freeze the PC like some people report). Any ideas?

(here are a couple of articles from the wiki: [WifiDocs/Driver/Broadcom43xx]("https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx"), [WifiDocs/Driver/bcm43xx]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx"))

---

### Post by Tiede on 2006-05-19
To modprobe one of the drivers, you have to remove the other one first.
Did you ```
rmmod *olddriver*
``` before modprobing the other one. Ndiswrapper and bcm43xx won't work together.

---

