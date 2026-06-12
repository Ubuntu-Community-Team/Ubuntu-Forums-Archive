---
title: "Recommended hardware print servers?"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by summersab on 2006-06-29
I absolutely adore Ubuntu. It has been my default desktop for about almost a month now, and I've only gone back to Windows sparingly. I'm trying to get my church (whose network I manage) to switch to Ubuntu, but the one problem I am having is printing - a major issue with Linux. We have an older HP 5SI which I know is compatible. However, it is on a  D-Link DP-101P print server (parallel). I've sone SOME research and found that it aparently isn't compatible with Linux. My question, then, is twofold. First, is it possible to set up the DP-101P in Ubuntu? If so, details are good because I'm still quite new. (The DP-101P setup process (in Windows) requires the creation of a TCP/IP port to which the server is connected to via the network and then the installation of the printer driver - I don't know how to create a TCP/IP port on a Tux box). If not, what print servers come recommended for Linux/Ubuntu? I found several, but most are off-brands, so I don't trust them or their ease of setup very much. Here are some of the models I have found if anyone is interested:

ConnectGear PUN1001S
G-Net GP-3202U
EDIMAX PS-1206P
D-Link DP-301P+

Thanks!

---

### Post by ogoforth on 2007-10-21
I'm having similar problems with a DP-301P+.  It's marketed as Linux compatible, but they don't support it.  If you get an answer to this posting please forward to me.

ThanX
ogoforth
[email]ogoforth@gmail.com[/email]

---

### Post by ture72 on 2007-10-21
I have an old Intel Netport printserver, think it is 8 years old by now. It works fine. I set it up like this: Please not that I'm a newbie on Linux so there might be a better way.

the print server has a static IP address , 192.168.0.180

start Firefox,  [http://localhost:631](http://localhost:631)

Add printer
Fill out the fields

next

lpd://192.168.0.180/LPT1_PASSTHRU,
 Your ip address and queue name will be different. I found out my queue name by using a windows computer. under printers go into properties for the printer attached to the print server, then on the port tab, click on "configure port"

Next

Select  your printer

Hope you under stand what I wrote, english is not my native language

---

