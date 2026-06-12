---
title: "Help with wireless connection setting script."
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2006-06-02
I have tried all the wireless gui's I could find and none work fine so I decided to create my own shell script to do everything. I already have a shell script that will connect to a router but I want to merge all of them into one script that auto scans at start for whatever ap I am near my only problem was my initial idea was to grep the output of "iwlist eth1 scan" for my ssid and if it existed connect  to it. If not grep for another known ssid repeating till I found one in my list.

That would work perfect except all the wireless networks I may connect to have had ssid broadcasting disabled so they don't showup in the iwlist output unless I am already connected.

What command could I run to check for a ap then have it report if it exists or not.
either scanning one at a time or all at once would be fine. but all at once is preferred. Something like "./program eth1 scan hiddenessid1 hiddenessid2 etc"

Please don't just come on saying try wifi-radar or any other gui because I already have.

---

