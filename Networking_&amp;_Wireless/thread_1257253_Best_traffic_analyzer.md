---
title: "Best traffic analyzer?"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2009-09-03
Hello, I'm looking for a traffic analyzer that display send and received traffic total but excluding loop traffic, I tested gnomes standard tool for viewing CPU, RAM and traffic but something tells me that this program also count loop traffic. I have a 10Mbit/s connection but the gnome systemtool tells me that I'm uploading over 30Mbit/s so I guess it also count loop traffic. I tested darkstats but it looks like it has trouble analyzing high amount of traffic is there any better traffic analyzer around (maybe not as advanced as wireshark)

---

### Post by bear24rw on 2009-09-03
You can check out bwm-ng for a simple bandwidth monitor..

---

### Post by SpinningAround on 2009-09-03
> **bear24rw said:**
> You can check out bwm-ng for a simple bandwidth monitor..

Something similar but that also give information about amount uploaded and downloaded, my isp deliverer only allow 10gb a day or they will block Internet access

---

### Post by FreewheelinFrank on 2009-09-03
> **SpinningAround said:**
> Something similar but that also give information about amount uploaded and downloaded, my isp deliverer only allow 10gb a day or they will block Internet access

'Struth! Mine gives me 4G a month.

---

### Post by The Cog on 2009-09-03
iftop is a text-based traffic monitor. It's about the only one that I have seen that reports in bit/Sec instead of Byte/Sec.

---

### Post by luigitl on 2009-10-26
Try this _[internet traffic monitor for ubuntu]("http://netramon.sourceforge.net/")_

---

### Post by Old_Grey_Wolf on 2009-10-26
You may want to look at vnstat. It runs from the terminal with a lot of options. Here is the man page [http://humdi.net/vnstat/man/vnstat.html](http://humdi.net/vnstat/man/vnstat.html). It can be downloaded from the repositories.

For my needs I just use ```
vnstat -d -i *interface*
``` to get daily usage and an estimate of daily usage, and ```
vnstat -m -i *interface*
``` to get monthly usage and an estimate of monthly usage.

The other traffic on my LAN is insignificant so I don't try using some of the options available with vnstat to exclude them. Although, you may need to experiment with the other options.

---

### Post by SkyNet2029 on 2009-10-26
iptraf runs from terminal and gives option to not count the loopback device, specify by device,traffic type (udp/tcp,etc) and also gives varying output formats (kb/mb/gb).

---

### Post by barbz127 on 2009-10-26
I run a combination of etherape to see whats happening in realtime and ntop to see totals.

Paul

---

### Post by lokutus25 on 2009-10-30
I like ntop but it crash very often. Otherwise it's complete.

---

