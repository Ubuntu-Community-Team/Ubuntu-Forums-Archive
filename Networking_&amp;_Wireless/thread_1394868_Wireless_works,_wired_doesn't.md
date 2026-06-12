---
title: "Wireless works, wired doesn't"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by Brian Vaughan on 2010-01-31
I recently got a cable modem from Comcast, and connected a Belkin F5D7230-4 wireless router to it, then connected my computer and an Xbox 360 to the router with ethernet cables.

My computer dual-boots Ubuntu 9.10 and Windows 7. In either operating system, the wireless connection is flawless. In Windows, so is the wired connection. But in Ubuntu, there's a lot of trouble with the wired connection -- specifically, while I can connect to the router and to the Internet, and while I can use ping, dig, traceroute, etc., to verify connections to remote hosts, Web browsing, or anything else that uses http, works only for a few Websites, and then only erratically.

I don't believe it is a DNS problem -- testing with ping, dig, etc., demonstrates that, and I have also tried using alternate nameservers. I also don't believe that it is an issue with IPv6, as I've tried the fixes usually suggested, including editing the grub configuration to disable IPv6 support in the kernel and verifying that IPv6 was inactive. I've also tried using local dns servers such as pdns-recursor. None of these things seemed to help.

Also, perhaps unrelated, but disturbing: my computer has locked up a few times while testing the wired connection, and I had to use a hard reset to restart the computer.

I can readily live with wireless. But, does anyone have any idea what the trouble could be?

---

### Post by Brian Vaughan on 2010-02-02
As I explained in another thread, [partially broken internet after upgrade]("http://ubuntuforums.org/showthread.php?p=8761898"), the problem was that I was using a NIC built in to my motherboard, which had buggy drivers. I disabled it, and installed a D-Link DFE-530TX+ ($15), which works perfectly.

---

