---
title: "Wireless in Lucid 10.04; RT2561/RT61"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by swedstal on 2011-02-27
I recently moved and now am required to connect via Wi-Fi rather than being hard-wired in. I chose an Edimax EW-7128g because this site: [(https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax")
said it would work "Out of the box." Well, it is out of the box but considering that I am now posting on the forum, it is obviously not working. 

I really don't even know where to start. I have pored through dozens of threads but I am just not smart enough with Linux yet. It seems most fixes require one to have an active internet connection which appears to me to be a bit "cart-before-the-horse-ish."

My lspci finds the card just fine.

Should I dump Network Manager?

If so should I try wicd or ndiswrapper?

Do those two do the same thing?

How would I install one of these without an internet connection?

I'll stop there with the questions. Any help is greatly appreciated. I WANT to love Linux but it's these little roadblocks that aggravate me to no end!
[]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax")

---

### Post by atomicben on 2011-03-02
I am a n00b to this too and I'm currently battling my own RT61 problem ([http://ubuntuforums.org/showthread.php?t=1698568&highlight=rt61](http://ubuntuforums.org/showthread.php?t=1698568&highlight=rt61)) but I think I might be able to shed just a little light to get you started.

First off - the [B]RT2561/RT61 chipsets are supposed to work OOB (out of box) using a driver (rt61pci) that is supposed to be included with kernel 2.6.24 (i think) and up.  You are probably using a kernel that is compatible.  To be sure:

> uname -r

Now when you say it's not working you need to be more specific.  You say it shows in lspci, that's good but does it show in network manager?  You can also do:

> iwconfig

This should list all detected network items and info about their state.  If you have wlan0 (the number might be different) and there are no problems with the status then you're on the right track.

wicd and network manager are similar - they are meant to help you detect and connect to networks.  

wicd and ndiswrapper are not the same thing.  ndiswrapper allows you to use the windows driver to control the card.  It's much easier to use ndiswrapper than trying to use native linux drivers for a number of reasons but a lot of folks (linux power users) consider ndiswrapper to be wasteful and want to use drivers built specificly for linux instead of cheating with ndis and a windows driver.  There are other considerations too.  

Some folks like to do some serious testing (or hacking depending on what they are trying to test).  If you are trying to use aircrack-ng to hack wireless networks you simply cannot use ndiswrapper, you have to use the native linux driver.

If you are not trying to test, hack or whatever... you simply want to be able to connect to a network ndiswrapper is TOTALLY that way to go.  It's setup is all over these forums and is simple as pie provided you have the windows driver for the card.

If you have the install CD or have downloaded the drivers, you'll need to find a file with the extension .inf there should also be a file(s) with extension .sys in the same folder.  Those are the windows drivers for use with ndiswrapper.

Now, if you don't even want to use the terminal window to install or setup ndiswrapper and your windows driver get a package called ndisgtk.  It's a fantastic GUI that allows you to browse for the INF file and does all the ndiswrapper setup for you provided you have already installed ndiswwrapper.  Use the windows XP drivers for ndiswrapper.

this article has everything you need to know about ndiswrapper and it has simple install procedures even if you are offline!  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by swedstal on 2011-03-03
Thank you for your reply. I was far too ambiguous with my description in the first post, perhaps due to my level of frustration. "Not working" is the kind of language my parents use when they want me to fix their computer.

My kernel is 2.6.32-28-preemt so that should not be a problem.

The output from iwconfig shows wlan0 with this:
IEEE 802.11bg
ESSID: off/any
Mode:Managed
Access Point: Not-Associated
Again, this looks fine to me.

In Network Manager the only connections I am showing are lo and eth0. Perhaps this is where my problem lies.

I went through this document [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) and found another issue. When I run 'network-admin' I do not have a "Wireless Connection" tab as indicated in the aforementioned document. All I have are "General", "DNS" and "Hosts."

Do you think there is any chance that wicd would find my card if Network Manager doesn't? If so, is there a good tutorial for installing it (or any program for that matter) without an internet connection (using a flash drive)?

I am so appreciative for your help. I feel like I am really close!

---

