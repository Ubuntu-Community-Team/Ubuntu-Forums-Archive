---
title: "wireless on x100e not working"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Lokesh123 on 2010-08-18
Hello
I spent the past days(!) on getting wireless to work on my Thinkpad X100e. It appears that the problem is known but no standard solution works. Tried several approaches with no luck.

Here is my system:
Thinkpad X100e with Turion *Turion* Neo X2 L625 / 1.6 GHz
Ubuntu Netbook Edition 10.04
Realtek driver updated to #17 (following several posts)
[COLOR=DarkRed]iwconfig[/COLOR] reveals: 
lo       no wireless extension
eth0   no wireless extension
wlan0 802.11bgn nickname: "rtl8191SEVA2"
Mode:Managed   Access Point: Not Associated Bit Rate: 300Mb/s
Retry: on  RTS thr: off Fragment thr: off
Power Management: off
Link Quality=10/100 Signal level=0 dBm Noise level=100 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 missed beacon:0

Problem 1: wireless seems to be turned off. Pressing keyboard keys (Fn + F5) has no effect
Problem 2: when wireless is on (found a way to manually do it each time after boot, this is no solution to Problem 1) my router/network is seen, but cannot connect.

Since I am no expert, please advise: 
how do I narrow the issue (iwconfig is the only one I know) 
how to I get it work ("10.04 wireless should work out of the box" ):P)

Apologies for posting this issue again after all those from others, but I spent so much time so far without success. Seems that there is no standard approach that works for everybody.

Thanks,
Lokesh

---

### Post by Lokesh123 on 2010-08-18
Addendum: My system is a dual boot with Windows 7. After turning on the wlan driver in Windows, Ubuntu froze every time after startup, requiring a complete shutdown. I conclude both systems interfere somehow with each other, something I don't understand at all.

Re-installed Ubuntu.

Tried update the Realtek driver... 'make' did not work (gcc bla bla error, etc). 

Spent the whole day for absolutely nothing.

):P for today, maybe tomorrow somebody else but me reads this post.

---

