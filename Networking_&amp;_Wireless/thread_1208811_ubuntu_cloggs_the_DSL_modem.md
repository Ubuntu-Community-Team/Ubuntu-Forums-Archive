---
title: "ubuntu cloggs the DSL modem?"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by jqian on 2009-07-09
I recently encountered an issue that I had about 1 year ago with 7.0.4
The issue has haunted me for so long that I desperately want some help from gurus here.

Here is my situation.
I have a DSL modem connecting to Bell Canada's Sympatico service with alleged speed 7Mbps
Behind the DSL modem is a d-link wireless router (I don't remember the model but it has been working flawlessly for years)
The router is setup with DHCP.

I installed ubuntu 9.0.4 couple of days ago, with kernel version 2.6.28
Everything went beautifully except...
When I tried to download something, the initial speed is about 300-400K Bps which is reasonable. But it stays at that speed for only about 5 seconds and then it drops drastically to 20K Bps and then stuck over there.
At the same time, all other windows machines starts to suffering the same speed and the sluggishness persists until I reboot the DSL modem by unplugging and plugging the power cable.

After rebooting the DSL modem, everything comes back to normal again. But if I initiate another download from ubuntu, nightmare occurs again.
If the download is initiated from a windows platform, the speed is quite persistent at around 300-400K Bps.

I have searched around and tried various solutions including but not limited to:
1. change the DNS server
2. upgrade the kernel to 2.6.29.6
3. disable the ipv6
4. tune up the network settings including MTU, etc.
but nothing helps

It seems to be that the downloads initiated by ubuntu frustrates the DSL modem hence Sympatico downgrades the speed until I reboot the DSL modem to get a new IP address.

Any inputs are highly appreciated.

---

### Post by jqian on 2009-07-09
btw, I forgot to mention I connect the PC to router with wire, not via wireless.

> **jqian said:**
> I recently encountered an issue that I had about 1 year ago with 7.0.4
The issue has haunted me for so long that I desperately want some help from gurus here.

Here is my situation.
I have a DSL modem connecting to Bell Canada's Sympatico service with alleged speed 7Mbps
Behind the DSL modem is a d-link wireless router (I don't remember the model but it has been working flawlessly for years)
The router is setup with DHCP.

I installed ubuntu 9.0.4 couple of days ago, with kernel version 2.6.28
Everything went beautifully except...
When I tried to download something, the initial speed is about 300-400K Bps which is reasonable. But it stays at that speed for only about 5 seconds and then it drops drastically to 20K Bps and then stuck over there.
At the same time, all other windows machines starts to suffering the same speed and the sluggishness persists until I reboot the DSL modem by unplugging and plugging the power cable.

After rebooting the DSL modem, everything comes back to normal again. But if I initiate another download from ubuntu, nightmare occurs again.
If the download is initiated from a windows platform, the speed is quite persistent at around 300-400K Bps.

I have searched around and tried various solutions including but not limited to:
1. change the DNS server
2. upgrade the kernel to 2.6.29.6
3. disable the ipv6
4. tune up the network settings including MTU, etc.
but nothing helps

It seems to be that the downloads initiated by ubuntu frustrates the DSL modem hence Sympatico downgrades the speed until I reboot the DSL modem to get a new IP address.

Any inputs are highly appreciated.

---

### Post by Fell on 2009-07-09
If you are downloading torrents it could well be that your ISP is using traffic shaping.

I had that problem with my previous ISP and the only way to get a decent download speed was to use transport encryption with Azureus.

---

### Post by LowSky on 2009-07-09
first off its 9.04, not 9.0.4. sorry I like to get those kind of things out of the way.

people often confuse Megabytes and Megabits, make sure your not using two different scales for measurement. Also try a speed test, and post the results here's a great link
[http://www.speedtest.net/](http://www.speedtest.net/)

for instance here's my results from my works internet feed, yours and my home internet speed will be much much slower.

[IMG]http://www.speedtest.net/result/513914645.png[/IMG]

It could also be a bad router, a bad router can often poorly map the multiple streams of data and cause the hiccups you see. Try plugging directly into the modem and see if you suffer the same issue. Lastly look at the modem, if that's an issue than see if you provider will replace it for free.

---

### Post by jqian on 2009-07-09
thank you very much for all the replies, especially correcting the version error.

first of all, it's not torrent download, it's just normal http download.
second, I am well understanding the difference between bits and bytes. I use capital B to refer bytes, and small b to bits.

when I say my ISP is 7M bps, it's 7M bits per seconds.
the initial download speed is 400K Bps, it's 400K bytes per seonds, roughly around 3M bits per seconds. This is reasonable.
but 20K Bps is not acceptable.

I can literally feel the sluggishness from 400K Bps to 20K Bps

---

### Post by jqian on 2009-07-09
> **LowSky said:**
> 

It could also be a bad router, a bad router can often poorly map the multiple streams of data and cause the hiccups you see. Try plugging directly into the modem and see if you suffer the same issue. Lastly look at the modem, if that's an issue than see if you provider will replace it for free.

thanks, but I highly doubt it's the router or modem issue.
because windows running on same PC has no problem at all. Downloading speed is always consistently around 400-500K bytes per second.

only in ubuntu on same PC, if I download via http and/or ftp, the speed drastically drops to 20K bytes per second from 400K bytes per second. And it's stuck over there until I reboot the modem.

btw, speedtest.net is my favorite site to test because I never believe what ISP told me. They say 7M bits per second, usually speedtest tells me 4-5M bits per second, which I can live with.
But after ubuntu gets invovled in the above scenario I descibed, speedtest tells me 0.5-0.6M bits per second which is outrageous.

---

### Post by lswb on 2009-07-09
You mentioned MTU. Try setting it to 1492 or lower, maybe 1450.

---

### Post by jqian on 2009-07-09
> **lswb said:**
> You mentioned MTU. Try setting it to 1492 or lower, maybe 1450.
tried various values: 1360, 1492....etc
no luck

---

### Post by DGortze380 on 2009-07-09
No one has asked the obvious question ... what are you downloading? The server (especially since you mentioned it's an HTTP download) may be limiting your bandwidth.

---

### Post by jqian on 2009-07-09
some updates:
I tried some other distro, such as fedora, mint, opensuse. They all have same problems.
but windows is absolutely fine by going to same site, downloading same file via same protocol (http or ftp)
I am really puzzled now. Seems to me that some network settings upset my ISP (or at least my DSL modem), causing the download speed cannot be persisted.

---

### Post by jqian on 2009-07-09
> **DGortze380 said:**
> No one has asked the obvious question ... what are you downloading? The server (especially since you mentioned it's an HTTP download) may be limiting your bandwidth.
under windows, downloading same file from same site via same http protocol is absolutely fine
the speed persists around 400-500K Bytes per second until it's finished, even though the file is pretty large (around 1G bytes)

---

### Post by jqian on 2009-07-10
seems no solution so far. In such case, I have to resentfully abandon linux world and go back to the dark side.
now I understand why microsoft can make huge amount of money but linux can only be free.

---

### Post by DGortze380 on 2009-07-10
> **jqian said:**
> seems no solution so far. In such case, I have to resentfully abandon linux world and go back to the dark side.
now I understand why microsoft can make huge amount of money but linux can only be free.

Frankly, if that's the attitude you have ... see ya.

expensive != better

---

### Post by jqian on 2009-07-10
> **DGortze380 said:**
> Frankly, if that's the attitude you have ... see ya.

expensive != better

whatever the attitude you are talking about, I didn't mean to be blunt.
But to be fair, you look around. Did I ask my question pretty clearly? Did anyone have viable solutions and at least understand the underlying cause?

That's the reality of so-called free or open-source world.
There are tons of similar situation such as JBoss v.s. Weblogic, MySql v.s. Oracle.
Quality is quality, you can not deny it.

---

