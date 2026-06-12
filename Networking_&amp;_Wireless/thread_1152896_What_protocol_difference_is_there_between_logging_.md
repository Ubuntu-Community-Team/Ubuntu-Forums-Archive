---
title: "What protocol difference is there between logging on/reading/posting..."
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by DJB1609 on 2009-05-08
Hi,

[http://ubuntuforums.org/showpost.php?p=7129802&postcount=1](http://ubuntuforums.org/showpost.php?p=7129802&postcount=1)

I jumped onto this thread as the problems are so similar to mine.

I can read posts, log onto many forums, but not send posts. 

I get the "Connection Interrupted The connection to the server was reset while the page was loading." whenever I try to post.

Also, yahoo webmail cannot "connect" to it's chat protocol, it just sits and waits.

Thunderbird will not send SMTP mails to any account.

Two laptops connected to the same wireless. Vista and XP work well, Ubuntu 8.1 and 9.04 have the exact same problems. They seem to be conected issues - some protocol used for Yahoo web-mail-chat, SNTP and posting to forums.

It's a deal breaker. I loved Ubuntu for so long, and it was my OS of choice. I won't uninstall, as I'm sure this can be fixed.

Similar problems are reported by many others. No sign of a clue, let alone a fix.

DavidJ.

Edit.
Solved (Almost) by installing Opera.
Fresh install of NetbookRemix - same problems in FF.
Opera works fine, except I can't edit "Advanced" so this is done in XP.

Will try another Distro as I've given up.

DavidJ.

---

### Post by superprash2003 on 2009-05-08
post output of ifconfig from the terminal.. could be an MTU related issue

---

### Post by DJB1609 on 2009-05-09
> **superprash2003 said:**
> post output of ifconfig from the terminal.. could be an MTU related issue

Thank you for your offer of assistance, it is greatly appreciated.

I apologise if I seem to respond slowly, but there is a time difference as I am in China. I opted for email notification of replies.

I forgot to mention in this thread, the problems started after I changed wireless router from D-Link to Asus W530G V2. I assumed it was a settings issue at first and went down that troubleshooting route before reinstalling, but Jaunty is new and has the same problems, hence my posts.

The results:

From 8.1 on the Toshiba:

david@david-Tosh:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:4c:09:43 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xe000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1024 (1.0 KB)  TX bytes:1024 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:b0:4e:18 
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:feb0:4e18/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1092067 (1.0 MB)  TX bytes:183503 (183.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-B0-4E-18-65-31-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

From 9.04 on the eee1000H netbook
daje@eee:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:4a:fe:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26000 (26.0 KB)  TX bytes:26000 (26.0 KB)

ra0       Link encap:Ethernet  HWaddr 00:15:af:e5:4c:9d  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fee5:4c9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6853399 (6.8 MB)  TX bytes:532370 (532.3 KB)
          Interrupt:19 


Thank you again for any assistance you can offer.

DavidJ.

---

### Post by superprash2003 on 2009-05-09
your MTU value ( 1500 ) looks great.. you could try changing your DNS server to opendns [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by DJB1609 on 2009-05-10
> **superprash2003 said:**
> your MTU value ( 1500 ) looks great.. you could try changing your DNS server to opendns [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

What is the benefit of this, and would it work in China with a Chinese ISP?

I updated the firmware on my router. I don't know what the upgrade was about but:

1) The Yahoo chat link from it's webmail page is now working.

2) I can send email through thunderbird now.

3) Also, I am able to post on one of my photography forums, which I couldn't yesterday. ([http://e-group.uk.net/forum/forumdisplay.php?f=21](http://e-group.uk.net/forum/forumdisplay.php?f=21) I can post to this forum without problem.)

But!

1) To post to this forum I have to go back to XP. (Timeout)

2) On http://forum.openvpn.eu/posting.php<snip> I get 

In Firefox: a request to open "posting.php" and asks me which program to open it with, or where I want to save the php page.

The same page in Konqueror 4.2.2 (KDE 4.2.2) gives the timeout exactly as before.

3) On another site, and on yahoo mail I am getting weird xml/php issues.

On Yahoo, the xml error won't allow composing/replying or sending. The page just gets an xml error or hangs.

This php/xml error seems rife with posts asking about it - but very few answers.

So the posting issue seems Ubuntu specific, not just Firefox, as I can't post to the same pages with FF or Konqueror, though one gives a php error and the other a timeout.

DavidJ.

---

### Post by superprash2003 on 2009-05-11
opendns servers are much more faster and more secure.. they should work from anywhere..

---

### Post by DJB1609 on 2009-05-11
> **superprash2003 said:**
> opendns servers are much more faster and more secure.. they should work from anywhere..

Hi,

I followed the instructions and rebooted. The internet was slower and, ironically, I couldn't open your webpage at all!

This, of course, could be related to my internet problem.

DavidJ.

---

### Post by DJB1609 on 2009-05-14
> **DJB1609 said:**
> Hi,

I followed the instructions and rebooted. The internet was slower and, ironically, I couldn't open your webpage at all!

This, of course, could be related to my internet problem.

DavidJ.

New install of NetbookRemix.
No change, except I Thinderbird works from clean install without importing profiles.
Firefox clean - no addons - no change!

Installed Opera. I can post.

But when I try to edit the opening message on this thread, it hangs!

Also, Opera's forums are banned in China! I have to look via a web-proxy.

F**k this country and its paranoia!

Anyone any idea why I can post now, but not edit the OP? It's mine!

DavidJ.

---

### Post by DJB1609 on 2009-05-20
Blocking IPv6 doesn't change things. Thank you for the suggestion.

Although it works in windows, and I can surf etc. in Ubuntu, does it matter if my wireless and ADSL modem have the same IP - 192.168.1.1?

Could that be an issue?

My Asus W530G V2 is the wireless, and I can access it at 192.168.1.1. I set it up as ppoE with the password etc. given by the ISP.

The Modem is a Chinese language ZTE XDSL 831, set up by the Chinese ISP. It has the same IP address, and I have to disconnect the Asus and go wired to access it's homepage - which is all Chinese!

If I have to change anything, it would have to be the Asus.

I know others can post from Linux in China from another forum.

Thanks, as any help is appreciated. (I don't want to give up!)

DavidJ.

---

### Post by DJB1609 on 2009-05-20
Although it works in windows, and I can surf etc. in Ubuntu, does it matter if my wireless and ADSL modem have the same IP - 192.168.1.1?

Could that be an issue?

My Asus W530G V2 is the wireless, and I can access it at 192.168.1.1. I set it up as ppoE with the password etc. given by the ISP.

The Modem is a Chinese language ZTE XDSL 831, set up by the Chinese ISP. It has the same IP address, and I have to disconnect the Asus and go wired to access it's homepage - which is all Chinese!

If I have to change anything, it would have to be the Asus.

I know others can post from Linux in China from another forum.

Thanks, as any help is appreciated. (I don't want to give up!)

DavidJ.

---

