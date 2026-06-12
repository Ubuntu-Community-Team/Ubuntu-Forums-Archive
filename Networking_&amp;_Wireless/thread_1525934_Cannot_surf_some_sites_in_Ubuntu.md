---
title: "Cannot surf some sites in Ubuntu"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by sunk8 on 2010-07-07
Hi,
I'm using Ubuntu 10.04 64-bit edition (native install) along with MS Windows 7.
I have a BSNL connection (India) and am using a PPPoE dialer to connect in Windows.
Without using any proxies, I can easily surf some pages in Firefox on Windows like
[http://mozilla.org](http://mozilla.org)
[http://yahoo.com](http://yahoo.com)
[http://indianrail.gov.in](http://indianrail.gov.in)

These pages however cannot be opened in Firefox, Chromium, Google Chrome or Opera in Ubuntu.
In Ubuntu, I'm using the Network Manager (installed by default). Have created a wired connection.
In tboth the OS, I am given an ip by my ISP.
They can be easily opened using proxy sites. But I want to open them natively like I do on Windows.
So, how do I go about it?
Thanks in advance, for your kind help.

Individual troubleshooting till now:
pinged the above sites, **success**, 100% packets received for yahoo, none for indianrail.gov.in. *Error message is: From 121.240.108.130.static-delhi.vsnl.net.in (121.240.108.130) icmp_seq=15 Packet filtered.* Note that I recieve all pings for the same site in Windows.
Disabled ipv6 in fiirefox, no go.
disabled ipv6 in eth0, no go.
tried various proxy sites, **success** all the sites open in a jiffy.
tried setting opendns in eth0 as well as wired connection., no go.
tried setting google dns in eth0 as well as wired connection., no go.
Tried changing MTU as suggested by *Iowan*. Found value 1440 giving the best response in ping. However, the sites don't open, no go.

---

### Post by chandra on 2010-07-07
I too use BSNL as ISP and run Kubuntu 10.04 on an AMD 64. I too have experienced similar problems: certain sites were accessible but others were not.

I think that the bundled network manager with K/Ubuntu is buggy. So, I first tried replacing it with wicd but that did not help.

I then went to BSNL/NIB and had them check my Belkin modem thoroughly. The selective inaccessibility problem was still present but its cause could not be identified.

On testing out with a Beetel modem and also with a Teracom modem, I have been able to access the previously inaccessible sites.

So, my suggestion will be to try accessing the inaccessible websites with another modem if you can borrow one.

In any case, I am intetested in getting to the bottom of this rather perplexing behaviour and also its solution.

---

### Post by Iowan on 2010-07-07
Although probably not the problem, [this]("http://ubuntuforums.org/showthread.php?t=1376506") thread discusses (or links to discussion) about testing/setting MTU.

---

### Post by chandra on 2010-07-08
> **Iowan said:**
> Although probably not the problem, [this]("http://ubuntuforums.org/showthread.php?t=1376506") thread discusses (or links to discussion) about testing/setting MTU.

Thank you Iowan.

I have looked at both

[http://ubuntuforums.org/showthread.php?t=1376506&page=3](http://ubuntuforums.org/showthread.php?t=1376506&page=3)

and

[http://ubuntuforums.org/showthread.php?p=8633038](http://ubuntuforums.org/showthread.php?p=8633038)

Interestingly, the BSNL people tried to change the MTU setting on my Belkin modem from 1492 to 1500 but got a firmware message box that said 1492 was the highest value that could be set.

Even more interestingly, the Tearcom modem that works fine has an MTU value of 1500, as I think the Beetel modem does, though I have to check the latter.

I will try out a lower MTU value, say 1464, on the Belkin just for interest.

FWIW, the BSNL technical staff at their exchange, did a traceroute using my Belkin modem, of the Australian website that was loading part of the way but not fully. They found that the packets reached Sydney from Coimbatore all right, but the return journey got stalled somewhere. So, one half of the duplex trip was OK. Does that hark to some other modem setting for ADSL 2+?

Thanks.

---

### Post by dineshs on 2010-07-08
Please forgive me If I am interfering.The OP is using dialler mode in windows (modem in BRIDGE mode)so he can setup the DSL connection via the DSL tab in NM which has provision for setting MTU.The MTU setting in modem will be a problem if he is using PPPoE mode.Am I right?

---

### Post by sunk8 on 2010-07-10
BUMP...

Err... This really sucks...
I booted into the Live Session and everything worked well!
So, I figured I'll go for a clean install on one of my spare partitions, and guess what...

My Internet connection works out of the box only in the Live session. I encounter the same problems in a fresh install without even installing any updates...

---

### Post by linuxyogi on 2010-07-12
Same problem here.

Web pages like grc.com opened fine when the modem was configured in pppoe mode but as soon a I configured it in bridged mode grc.com won't open.


I wanted to test my Ubuntu firewall at grc.com, but I can't.

This is really annoying.

---

### Post by sunk8 on 2010-07-19
By the way, I also installed openSUSE 11.3 recently. It's funny how everything really works out of the box there...
I don't have any problems opening sites and I even seem to be getting a better speed...
I think I'll stick to openSUSE for a while...
:popcorn:

---

### Post by Iowan on 2010-07-19
> **sunk8 said:**
> 
I think I'll stick to openSUSE for a while...

I suppose that's why there are different distros...
Good luck! :)

---

