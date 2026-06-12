---
title: "difficult wireless in Maverick, using orinoco_cs"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by svaens on 2011-01-04
Hi all, 

I have a problem setting up my mums old laptop, and I was wondering if someone can help me. 

I think it has a prism wireless card .. and anyway, I can see that it uses the orinoco_cs driver.

Since lucid, this has not been working. The wireless adapter is detected, the module loaded, I can even see available networks, but when it tries to connect, even with no security, it tries for a long time, then fails. 

I just came across some sort of 'fix' here:

[http://ubuntuforums.org/showthread.php?t=1617549](http://ubuntuforums.org/showthread.php?t=1617549)

I did this, but when I do, I notice two things;

1. on boot, ubuntu complains that firmware files are missing (how to stop ubuntu looking for them???)

2. the network manager no longer shows me a list of available networks. 

problem 2 means that while I can no longer choose a network to connect to, and can not set it to automatically connect on login, I can still connect using the option 'connect to a hidden network'.

While this is manageable, it is not ideal, and for my poor mum (whos not so computer savvy) its not the best. 

any idea how I can fix this? Get the network manager working again (and connecting)?

Please help!!!

thanks!

---

### Post by svaens on 2011-01-04
ok, .... here's something I might as well attribute to god, and the prayers i'd have made if i'd been a believer;
(I might as well do, as this is as mysterious as anything i've seen in ubuntu)

wireless connections might now be seen in the network manager.
And it automatically connects. 

I was doing strange things. I'd named my wireless network;
network1
played around with no security, then when I added security, I renamed the network;
network2

When i'd try to connect to network2, 
it would fail again. First I assumed that it could not connect BECAUse of the security, but then I noticed, that even though I had been very careful about the SSID name (network2) after failing, it would still say;
"disconnected from network1"

So i figured ubuntu was messing me about (as there was no longer any entry in the list of old or current wireless connections, called 'network1')

Time for a reboot.

On reboot, it worked.

However, it still looks for the non-existent firmware files.

Anyway to get it to accept that i'm not putting those problematic files back?

---

