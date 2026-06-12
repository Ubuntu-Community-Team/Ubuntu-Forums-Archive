---
title: "Slow browsing, fast download"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by leifjonny on 2010-02-12
I'm using wlan and I'm behind a NAT firewall. Downloading with BitTorrent can reach speeds of 1,5MB/s, but browsing is incredibly slow. Chromium/Firefox seems to hang forever on "connecting.." or "waiting for". Sometimes pressing the reload button will speed it up. I have two Ubuntu boxes and they are the same way.

I don't get it, if downloading is so fast, how can browsing be so slow. Yes I have disabled ipv6 in grub and in Firefox, don't know how to do it in Chromium. Have 64-bit Ubuntu. Cnet wlan card using rt61pci module.

---

### Post by quazi on 2010-02-14
I have a similar (maybe the same) issue.  Browsing is slower in Ubuntu than it is in a guest OS (Vbox) of windows 7, both 64-bit.  This doesn't make sense to me.

I've tried speed tests and they both give outrageous speeds (~30mbit), but real-time browsing is much slower in linux than in windows.

---

### Post by sgosnell on 2010-02-14
Disable IPv6.

---

### Post by quazi on 2010-02-15
I tried doing this through grub and firefox's settings.  Windows 7 in vbox still blows ubuntu out of the water.

---

### Post by sgosnell on 2010-02-15
Do it through network manager as well as firefox. My 900 with Ubuntu blows away my wife's big Toshiba.

---

### Post by 2hot6ft2 on 2010-02-15
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

### Post by quazi on 2010-02-15
Well, I just changed it in Ubuntu (previously had tried changing it in my router, which didn't help at all) and websites definitely appear to load quicker.  I'll update later after some more extensive testing.

---

### Post by ant2ne on 2010-02-15
> **quazi said:**
> Well, I just changed it in Ubuntu (previously had tried changing it in my router, which didn't help at all) and websites definitely appear to load quicker.  I'll update later after some more extensive testing.You say "just chagned **it** in" and changing **it** in" but what is **it**? Did you have to disable IPv6?

---

### Post by quazi on 2010-02-16
Well Ipv6 was disabled for default for me and I've already stated previously that disabling it doesn't do anything.  So to be more clear, I've started using OpenDNS servers inside network manager.  There is definitely an improvement, but Windows 7 still blows it out of the water.  I have 30Mb/s internet, so webpages load more or less instantaneously in windows 7 and take upwards of 15s-30s on Ubuntu.

Just to be more specific, I'm comparing browsing speeds of Google Chrome in Windows 7 and Ubuntu 9.10.

EDIT: It's markedly faster, thanks for the help.

---

### Post by 2hot6ft2 on 2010-02-16
> **quazi said:**
> Well, I just changed it in Ubuntu (previously had tried changing it in my router, which didn't help at all) and websites definitely appear to load quicker.  I'll update later after some more extensive testing.
Glad it's helping. Now if my ISP and routers firmware supported IPV6.

---

### Post by jcabraham on 2010-02-16
> **sgosnell said:**
> Do it through network manager as well as firefox. My 900 with Ubuntu blows away my wife's big Toshiba.

*How* do you disable ipv6 in network manager? I have this same problem.

---

### Post by jcabraham on 2010-02-16
It would appear that it *is* disabled in network manager. How do I disable ipv6 system-wide in ubuntu?

---

### Post by sgosnell on 2010-02-16
Right-click on the network icon in the panel, edit connections, select the connection, edit it, and on the IPv6 tab, select Ignore.  If it's disabled there, the problem should be solved.  I haven't tried to do anything in the system, but there are multiple threads on doing that, and a search should find them for you.

---

### Post by quazi on 2010-03-13
I lied, placebo effect tricked me.

IPv6 is disabled, I'm using OpenDNS servers and linux is still unbearably slow.  It's incredible how much faster things load in virtualbox (running win 7).  

Firefox is stuck at looking up and google chrome is stuck at resolving host, so it still appears to be a hostname issue.

---

### Post by bradmayne04 on 2010-03-14
I just did that walkthrough you gave for change all the settings w/ about:config.  Still no good. Firefox works but not that well.  I was wondering if it might be spyware slowing my browser down.  Is it possible to get spyware w/ ubuntu?  I'm dual booting windows 7 and like another user said 7 is a heck of a lot faster.  It seems to me that firefox was running pretty well for until yesterday.  Does anyone else have an idea?  I can browse but it takes about 15 seconds to load a page.  That really hasn't happened until very recently.  My signature should say the rest.

---

### Post by sgosnell on 2010-03-14
I change Firefox in about:config, change the settings in Network Manager to ignore IPv6, and use OpenDNS instead of the default DNS system.  I'm not sure exactly which does the fix, but I have no delay opening pages, on an EEE-PC 900, which ain't the fastest system on the planet.

---

### Post by 2hot6ft2 on 2010-03-14
If everything else fails you might try using a windows driver in
System > Administration > Windows Wireless Drivers
which is ndiswrapper
```
sudo apt-get install ndiswrapper
```
if you don't have it.
You'll need the windows drivers .inf file for your wifi adapter to use it.
I'm not a fan of using windows drivers in linux myself but there's lots of info out there for those that want to try it.

---

