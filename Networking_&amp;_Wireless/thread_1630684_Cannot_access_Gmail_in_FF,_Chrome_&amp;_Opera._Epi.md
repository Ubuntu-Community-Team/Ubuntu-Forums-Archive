---
title: "Cannot access Gmail in FF, Chrome &amp; Opera. Epiphany works."
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by bluefinger on 2010-11-25
Right, I've been having an increasingly deteriorating situation with regards to access to Gmail. For the most part, Firefox, Chrome, and now Opera refuse to load Gmail at all. Connection interrupted, etc. Opera used to work for the longest part, but now, no longer. Epiphany is the only one I've got that works (and I had to download it and use it to activate this forum account).

I've tried various fixes that I've seen on the boards here, but no bites. I'm on a 3 Mobile Broadband dongle, using 10.04 LTS, linux kernel 2.6.32-25, and basically have a eMachines netbook which is pretty much a rebranded Acer AspireOne 532. I am struggling to find an answer to this, because this is really annoying me that now all major browsers on my system don't like gmail. Network config issues? HELP!

---

### Post by khelben1979 on 2010-11-25
If you're having trouble reading e-mail in the browser, why not use one of the provided e-mail applications such as [Mozilla Thunderbird]("http://en.wikipedia.org/wiki/Mozilla_thunderbird"), [KMail]("http://en.wikipedia.org/wiki/Kmail#E-Mail") or similiar.

It's possible to configure your e-mail software to use gmail and thereby solving your problem here. There are lots of guides on the net which explains how to do it if you're interested. I'm using Thunderbird (called Icedove in Debian) myself, works good!

---

### Post by bluefinger on 2010-11-25
> **khelben1979 said:**
> If you're having trouble reading e-mail in the browser, why not use one of the provided e-mail applications such as [Mozilla Thunderbird]("http://en.wikipedia.org/wiki/Mozilla_thunderbird"), [KMail]("http://en.wikipedia.org/wiki/Kmail#E-Mail") or similiar.

It's possible to configure your e-mail software to use gmail and thereby solving your problem here. There are lots of guides on the net which explains how to do it if you're interested. I'm using Thunderbird (called Icedove in Debian) myself, works good!
I already use Evolution for work emails, and personally, I'd rather keep work/personal stuff separate. Secondly, I didn't exactly like the IMAP setup with Evolution with Gmail, so if I can just keep to keeping personal stuff on a separate webmail, and important work stuff on an email client, then all the better. This has been how I've done things for years, and yet, for the past month now, I've been having issues with regards to FF, Chrome and now Opera accessing Gmail. Even starting a fresh profile on FF has done nothing, and absence of all plugins did not resolve the issue.

---

### Post by khelben1979 on 2010-11-25
If this is a software problem, have you tried a really old version of Firefox? ( [ftp://ftp.mozilla.org/pub/firefox/releases/]("ftp://ftp.mozilla.org/pub/firefox/releases/") )

---

### Post by bluefinger on 2010-11-25
> **khelben1979 said:**
> If this is a software problem, have you tried a really old version of Firefox? ( [ftp://ftp.mozilla.org/pub/firefox/releases/](ftp://ftp.mozilla.org/pub/firefox/releases/) )
3.5 didn't work, but 3.0 did, strangely enough. However, I'm concerned also about the fact the issue affects Chrome and Opera as well.

EDIT: and accessing Gmail through an older version of the browser seemed to have correct the issue for the latest version too. Just... what? Agh... computers at times...

EDIT2: Well, not smooth running all the time, there's still connectivity issues, but going onto HTML mode resolves some of that (but not all). I'll keep an eye on this to see if it improves.

---

### Post by Linicks on 2010-12-30
This is an MTU issue.

Change your MTU value to 1454

Nick

---

### Post by James Haigh on 2011-02-03
Hi, I have exactly the same problem.

I have had 3 mobile broadband for a couple of months. When I try to access Gmail I get connection interrupted nearly every time.

Every other site I've tried including other Google services, even ones that require a login, work fine.

Shortly after getting 3, I ran into this problem and searched for it. I found a site saying that it was an MTU problem and that it should be changed from the default of 1500 to 1400. It worked, although I have to use ifconfig every time I connect because NetworkManager doesn't seem to have an MTU setting for mobile broadband which is annoying.

```
sudo ifconfig ppp0 mtu 1400
```

Recently however, the problem has recurred. MTU 1400 does not fix Gmail anymore. I just tried 1454 with no luck either.

Thank you.
James.

PS. I used to use O2 mobile broadband which worked fine, but they reduced the data allowance from 3GB to 2GB a month while keeping the price at 15£pcm. Whereas 3 were offering 15GB for exactly the same price!

---

### Post by James Haigh on 2011-02-03
Sorry, both do work. The larger is probably best, thanks Linicks.

```
sudo ifconfig ppp0 mtu 1454
```

And it's not just Gmail, although it is worst affected, I notice a significant improvement in the speed that other sites load.


I have a laptop connected to the 3 dongle which shares the connection with a WiFi access point. I changed the MTU on this laptop for ppp0 but this doesn't seem to affect any laptop or other device that is connected to the WLAN. The MTU has to be changed on each device's WLAN connection (ex. wlan0). The MTU on ppp0 of the gateway laptop doesn't have to be changed unless I want to access Gmail directly on this laptop.

However, I may not be able to change the MTU on all devices on the WLAN so this is not a full solution for me. Is it possible to get the gateway laptop to resize transmission units or something, so that other devices do not have to change their settings?

Also, it is very annoying to have to run the above command after each time I connect.

Thanks.

---

### Post by James Haigh on 2011-02-04
I've tried changing the MTU on all devices but I can confirm that the iPod Touch and the HP wireless printer do not have this setting.

I need a solution that is specific to the gateway laptop so that settings do not have to be changed on the other devices.

BTW, Linicks, how did you know that 1454 would work? What is special about this specific number?

---

### Post by Linicks on 2011-02-04
James, I now use 1430;  the reason is due to packet size and overheads - 1430 can be divided by these exactly, so therefore no fragmentation occurs.

To set this permanently, read the file:

/etc/ppp/options

in there are settings for ppp connections, so just find the 'MTU' value and add the required MTU value thus:

# Set the MTU [Maximum Transmit Unit] value to <n>. Unless the peer
# requests a smaller value via MRU negotiation, pppd will request that
# the kernel networking code send data packets of no more than n bytes
# through the PPP network interface.
#mtu <n>
mtu 1430

Nick

---

### Post by James Haigh on 2011-02-04
Thanks Nick.

How do you calculate MTUs? What is special about 1400, 1430, 1454, 1492 and 1500?

Is /etc/ppp/options used by NetworkManager?

Is it possible to bridge from MTU 1500 to 1430 on the gateway laptop? Any ideas how I can avoid MTU problems on the iTouch and printer?

---

### Post by James Haigh on 2011-02-05
I have been reading up on Path MTU.

In IPv6, Path MTU Discovery is robust and reliable so these MTU problems don't apply to IPv6. However, unfortunately IPv6 still has low deployment despite being around for over a decade, so neither the iTouch or printer appear to implement IPv6.

In IPv4, PMTUD is optional and affected by blocked ICMP messages. Clearly the devices on my network aren't using or benefiting from PMTUD, otherwise I'd not have these MTU problems.

I think one solution is to set up a proxy on the gateway laptop but this is probably not worth the effort just to improve the connection on 2 devices.

Remaining questions:
* Is /etc/ppp/options used by NetworkManager?
* How do you calculate MTUs? What is special about 1400, 1430, 1454, 1492 and 1500?

---

### Post by ubuntu-freak on 2011-02-13
> **Linicks said:**
> James, I now use 1430;  the reason is due to packet size and overheads - 1430 can be divided by these exactly, so therefore no fragmentation occurs.

To set this permanently, read the file:

/etc/ppp/options

in there are settings for ppp connections, so just find the 'MTU' value and add the required MTU value thus:

# Set the MTU [Maximum Transmit Unit] value to <n>. Unless the peer
# requests a smaller value via MRU negotiation, pppd will request that
# the kernel networking code send data packets of no more than n bytes
# through the PPP network interface.
#mtu <n>
mtu 1430

Nick

Dude, you're a star! Finally, a proper solution for mobile broadband users. Works like a charm, thanks.

Have you mentioned the problem and fix on Launchpad?

Cheers.

---

### Post by James Haigh on 2011-02-14
Is /etc/ppp/options used by NetworkManager? Isn't it only used by pppd?

How do you calculate MTUs? What is special about the numbers: 1400, 1430, 1454, 1492 and 1500?

Is this specific to 3 mobile broadband? Why did I have better results with O2?

Thank you.
James.

---

### Post by owenll on 2011-05-27
> **ubuntu-freak said:**
> dude, you're a star! Finally, a proper solution for mobile broadband users. Works like a charm, thanks.

Have you mentioned the problem and fix on launchpad?

Cheers.
+ 1

---

### Post by James Haigh on 2011-08-14
> **ubuntu-freak said:**
> Dude, you're a star! Finally, a proper solution for mobile broadband users. Works like a charm, thanks.

Have you mentioned the problem and fix on Launchpad?

Cheers.

I filed this bug a couple of months ago, but it hasn't had any attention:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/801313](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/801313)

Might be worth saying 'This bug affects you'.

James.

---

