---
title: "Incredibly slow wireless with Ubuntu"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by HLK on 2010-02-14
Hello,

I recently got a new laptop (Toshiba Satellite L500-1WG), and installed the latest build of Ubuntu. At first my wireless wasn't working at all, I did some searching on forums and realised it was probably an issue of my WiFi card not being compatible. My wifi card is apparently an Intel WiFi Link 5100. Using instructions on forums I managed to install the driver, and my wifi is now 'working' in the sense that I can pick up wireless networks and connect.

BUT, my connection is horrifically slow. I know its not the internet connection itself because it used to work perfectly well with my old laptop (also a Toshiba Satellite, but older model) in exactly the same place. The wired connection is fine. I may have to resort back to Windows merely to save having a massive ethernet cable trailing across my floor...

My internet is with O2, so it's coming through an o2 box, don't know if that's relevant.

Any ideas!?

---

### Post by b9k9kiwi on 2010-02-14
There are a number of threads in this forum detailing 'fixes' for slow internet connection issues with 9.10.  Search for "slow internet" and "IPv6".

There is something 'broken' in 9.10 vis-a-vis internet although it appears to affect relatively few users - there is along running bug report from the beta days of 9.10 which seems to confirm that there is an issue with this particular version of Ubuntu.  It may well be hardware compatibility related (how very 'Windows') - my wireless card isn't (kof,kof) supported, although it worked perfectly well in 9.04.

The 'fixes' may or may not work for you - they sort of worked for me in that the dog slow internet connection has been speeded up to a tolerable level, albeit way slower than the Windows box that sits next to me Ubuntu box connected via the same wireless router.  The connection nevertheless slows down to a crawl eventually, and I have to reboot to get it up to any sort of speed (a restart won't do, I have to close down and restart the PC).

Fact is, if I have to reliably access the net for quick info (including accesing Ubuntu Forums!) or a fast download, then I have to use my Windows box which I only intended to use to play the occasional game.

All very disappointing.

---

### Post by 2hot6ft2 on 2010-02-14
Try these together they made a big difference for me just select your wireless connection in the first one instead of wired.
> **Fire_Chief said:**
> Here is a site that shows where to configure static DNS in wicd.
[http://wicd.net/screenshot.php]("http://wicd.net/screenshot.php")

I think you'd do well with either option (per connection/network configuration or global DNS servers setup).

Cheers!
and in this one I didn't disable IPV6 since the IPV6 DNS servers were added in the first one.
> **uboss said:**
> I was having the same problem so this is what I did just now and it really improved my speed. (Keep note of what you do in case you need to go back)

1. Type about:config in the address bar and press Enter
2. Then right click on the preferences table and select New->Integer
3. Type preference name as: **Network.dnsCacheExpiration** and Integer value **3600** (This will increase the DNS expiration cache time to 1 hour---you may decide the time you want)
4. Right click on the preferences table and select New.>Integer
5. Type preference name as: **network.dnsCacheEntries** and set its value between **100 to 1000** (By Default firefox has 20 entries I set mine at 400)
6. Type in the search and find each of the following and set their values as indicated below (Toggle will change the value like from false to true)

[B]network.prefetch-next  = true
network.http.pipelining  = true
network.http.pipelining.maxrequests  = 8
network.http.proxy.pipelining  = true
network.dns.disableIPv6  = true[/B]

7. Also right click and add another:  preference name as: **nglayout.initialpaint.delay** and set its value to **0**.

8. Plus I added the OpenDNS just as this thread mentions. 


Close the browser and restart. You are done.
I hope this helps
From this thread
[FireFox Slow in 9.10 Koala]("http://ubuntuforums.org/showthread.php?t=1310366")

---

### Post by northd_tech on 2010-02-14
> **b9k9kiwi said:**
> There are a number of threads in this forum detailing 'fixes' for slow internet connection issues with 9.10.  Search for "slow internet" and "IPv6".

There is something 'broken' in 9.10 vis-a-vis internet although it appears to affect relatively few users - there is along running bug report from the beta days of 9.10 which seems to confirm that there is an issue with this particular version of Ubuntu.  It may well be hardware compatibility related (how very 'Windows') - my wireless card isn't (kof,kof) supported, **although it worked perfectly well in 9.04**.


I'm getting the same slow thing under Jaunty 9.04 with a Broadcom 4321AG (that lspci calls a 4328 ) interface running the proprietary Broadcom STA driver.

I think this is a recent [update?] problem that I didn't have before, and I have the problem with both the Gnome Network Manager and wicd now (which I mostly like better).

Vista's wireless runs circles around my ubuntu WiFi connection lately...:(

---

### Post by sgosnell on 2010-02-14
Either disable IPv6, use OpenDNS, or both. That should take care of your problems.  There are other good reasons for using OpenDNS.

---

