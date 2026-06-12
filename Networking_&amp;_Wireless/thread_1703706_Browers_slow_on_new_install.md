---
title: "Browers slow on new install"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by randumnumber on 2011-03-09
Hello all, I hope I can find some help here.

So here is the situation. I just reinstalled 10.04 on my laptop. I had 10.04 on it to begin with and had no issues at all. Since reinstalling I have had issues with both firefox and chrome.

The two browsers will sometimes load pages and sometimes they wont. When they dont they just sit waiting to load some part of the page. the bottom of the screen says "waiting for ubuntuforums.org"

While this was happening I opened wireshark and am getting a huge amount of [TCP Retransmission] requests. It gives the source as my ip and the destination as the websites ip.

I have tried resetting cable modem, router, computer. I have changed my DNS on my router to googles free dns. I have also disabled ipv6 in both firefox and grub. my system is NOT using ipv6 at all. 

I dont think this is a DNS issues because I can resolve the same website 2 times, the first time it will hang, the second time it will load instantly. the 3rd time it will hang, or any combination of these events.

The other computers on my network are unaffected. 

about a year ago i had this same problem on a 64bit system. and found a very obscure fix. It involved editing a file at command line and removing some lines for the file. However i can not for the life of me remember this fix.

PLEASE HELP.

---

