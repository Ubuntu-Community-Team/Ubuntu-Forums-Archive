---
title: "setting up ISDN for G4 fax service"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by archis on 2006-02-15
Hi, I need some advice on setting up and configuring a (passive) HFC-PCI ISDN card (a Sitecom DC 105) for use as a fax modem. 

To differentiate this piece of hardware a bit further, I should say the following:

It's not an 'active' card (i.e. there's no firmware), and thus it needs a driver, over and above CAPI (see below). The problem is that AVM is the only company that maintains Linux drivers for passive ISDN cards these days, and as far as I know, the drivers only work with their AVM Fritz line of cards. [avm-fritz-firmware ](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=fritz&searchon=names&subword=1&version=breezy&release=all) is part of the restricted repository, but I can't figure out whether I should be able to get my HFC card to work with that or whether that's just not possible. (As a new Linux user, I also have some difficulties figuring out how to set things up.) 

Then there /is/ used to be [isdn4linux](http://www.isdn4linux.de/), a package that offered support for a wide range of ISDN cards including passive HFC cards but that is now deprecated in favour of [mISDN](http://www.isdn4linux.de/mISDN/), [which is part of the universal repositories](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=breezy&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=misdn&searchon=names). According to various sources, mISDN is supposed to work with my kind of card, yet it is apparently not quite ready for prime time. [I am not sure where the drivers are supposed to be](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=breezy&subword=1&exact=&arch=any&releases=all&case=insensitive&keywords=misdn&searchon=names). 


As a brand new 'switcher', I would definitely appreciate more documentation or howtos precisely regarding the somewhat less self-explanatory aspects of setting up a Debian/Ubuntu system. [There is a ISDN HowTo on the wiki](https://wiki.ubuntu.com/IsdnHowto?highlight=%28isdn%29) but it only covers ppp network access via AVM Fritz cards, not ISDN fax. For starters, I would like to know whether I need to recompile my kernel in order to use the ISDN card with its driver, CAPI, capi4hylafax etc. And what driver to I need for the HFC-PCI card, and where do I get it? Should I try using mISDN - and where from? Synaptic doesn't seem to have the actual driver (?) and [this site](http://isdn.jolly.de/) (apparrently maintained by mISDN's authors?) offers a source. But how does this go with Breezy's 2.6 kernel? Is it stable?

If I manage to get the card going I would like to use the card with hylafax via capi4hylafax. The documentation for those packages is fortunately much better and so I hope I won't be as confused about setting things up at that end..

---

### Post by archis on 2006-02-17
I've checked with the [ISDN4Linux community](http://news.gmane.org/gmane.linux.isdn.i4l.user) where the developers of mISDN hang out. At this point, mISDN doesn't provide fax capability. So, even if your card works mISDN (HFC PCI cards are supported) and you set up CAPI support via capi4hylafax, it will not work because faxing is not yet implemented in mISDN. Their development focus appears to be on internet access via ISDN and support for the rapidly growing VoIP services such as Asterisk.

They advised me to set up an Asterisk PBX and use it with spandsp and app_rxfax/app_txfax to get the fax capability, but I have to say that a is not a reasonable approach when all you want is a simple 'Fax...' button on your application's GUI that Just Works with an existing hardware setup.

At the heart of the problem seems to be the decision to drop the older ISDN4Linux standard in favour of mISDN for the 2.6 kernel although mISDN was, and apparently still is, in development and missing some key features. Let's hope they will implement fax in mISDN soon.

---

