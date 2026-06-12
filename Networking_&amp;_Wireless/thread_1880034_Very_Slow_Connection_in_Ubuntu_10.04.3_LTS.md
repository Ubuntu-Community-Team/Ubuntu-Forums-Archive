---
title: "Very Slow Connection in Ubuntu 10.04.3 LTS"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by new_user01 on 2011-11-12
Hello everyone,

This is my first post in any linux-related forum.

My problem is: I installed Ubuntu 10.04.3 LTS today on my desktop, but the connection is extremely slow. I also have Win 7 installed on this same computer.

I've not installed or changed anything from the fresh OS install, other than installing an AMD/ATI Radeon driver. I'm also a total noob in terms of unix admin work. I looked online and "slow connection speed" seems to be a widespread problem in Ubuntu 10 and 11. I tried a lot of the solutions like "disable ipv6" etc, but none have worked so far.

50% of webpages would just time out. And I only visited major sites like google.com, yahoo.com, etc. The ones that do load, they take about 10-100 times longer than when I'm on Windows 7. I have 25Mbps/25Mbps from Verizon FIOS. On speedtest.net I consistently get 25/25 on my Windows 7 desktop (wired connection) and MacBook (wireless). On my iPhone (wireless) I also get 25/25 in the speedtest.net app.

In Ubuntu, I get 100KB/sec download. This is the speed of transfers in Firefox (even after making recommended changes), Chromium browser, ssh/scp, and when doing apt-get update/install. It's not just slow, but the fact 50% of webpages won't even load. Or I could be doing an apt-get install and it'd hang for 5-10 minutes (speed drops from 80KB/sec to 0) then errors out.

By the way, if I use Ubuntu in VMWare in my Windows 7, then it's the expected 25/25 speed again. Common solutions I see online talk about "wireless problems", "firefox config", or "ssh settings" issues. But like I was saying, everything is slow for me. My motherboard is GIGABYTE GA-Z68XP-UD3P with on-board LAN. The LAN driver is Realtek. Please let me know what other info you might need from me.

This seems a widespread problem and I'm not sure why I haven't found anything that works.

I would really appreciate it if there are any fixes for this!

edit: I have the same problem when I installed Ubuntu 11.

---

### Post by new_user01 on 2011-11-12
o.m.g.

I didn't wanna waste anyone's time, so before my post, I had spent 5 hours messing with it and looking at online forums.

I just looked in a totally different direction after making the above post, and found a fix, and it has worked!

Before, everything I found was about "disable ipv6", "change blah in firefox/chrome" or editing "ssh configs".

It turns out my motherboard uses Realtek 8111E Lan driver, and there's some fix for this if the OS has linux kernel 2.6.x. You can download the linux driver at the official site. Actually.. just found another link: [http://code.google.com/p/r8168/downloads/detail?name=r8168-8.026.00.tar.bz2&can=2&q=label%3AFeatured](http://code.google.com/p/r8168/downloads/detail?name=r8168-8.026.00.tar.bz2&can=2&q=label%3AFeatured)

After this, I followed directions at [http://ubuntuforums.org/archive/index.php/t-1226628.html](http://ubuntuforums.org/archive/index.php/t-1226628.html)

And it worked!

Note: if you do "sudo ./autorun.sh" after downloading the file, then it will go remove your current driver (leaving you with no more internet). It then says "fatal cannot find r8168 module". This seemed common from online. But if you follow the link above, and manually do it without autorun.sh it works.

Anyway.. thanks. If I didn't make that post, I'd have uninstalled ubuntu and not looked any further.

---

