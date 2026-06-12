---
title: "External dialup modem: I can ping ISP but no further."
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by agiledata on 2005-12-25
Using a external dialup modem, I can't get beyond the ISP, and thus can't get any web pages.

I'm new to Linux. Recently, I've started moving my PCs over to Ubuntu, and things have gone very well, apart from modems. I'm trying to set up two Ubuntu PCs for a friend, and a retired aunt. They don't have broadband, so I need to get a modem working. After two weeks of trying, I eventually realised that WinModems were a bad idea, so I dug out my old external US Robotics 56k Voice FaxModem.

Ubuntu detects the modem with no problem:
```
System --> Administration --> Networking --> Modem connection --> Properties --> Modem --> Autodetect
```
finding /dev/ttyS1.

On activating the modem, it dials and establishes a connection, which it holds.

Netstat gives me an IP address from the ISP I'm dialling. 
```
Applications --> System Tools --> Network Tools --> Netstat
```
Traceroute gives me two IP addresses, one local (0.33ms) and one remote (249ms), both of which I can ping.

But that's as far as I can get. I can't get web pages, or ping other addresses, by numbers or domain. I've tried explicitly setting the DNSs to server-provided, or explicitly to those of the ISP. I've tried every suggestion I can find on the newsgroups, and I'm a bit stuck. Without internet access from Linux, my aunt and friend will have to go back to Windows! :sad: What else can I try? I must be missing something obvious.

---

