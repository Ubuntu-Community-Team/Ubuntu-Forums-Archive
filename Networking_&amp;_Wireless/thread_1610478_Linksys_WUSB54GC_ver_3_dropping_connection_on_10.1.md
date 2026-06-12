---
title: "Linksys WUSB54GC ver 3 dropping connection on 10.10"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by inspired on 2010-10-31
Hi folks,

I posted the following at: [http://ubuntuforums.org/showpost.php?p=10054728&postcount=10](http://ubuntuforums.org/showpost.php?p=10054728&postcount=10)
... because it seemed to be the same issue. It is not, however, as this has no relationship to whether there is much data going through the connection or not. It is also not a broadcom chip, as far as I can tell. But I'll start this message with the data I have posted there:

> Just a note to say I am having the same issue on a friend's computer. Trying to get him set up with Ubuntu and away from Vista which was (yet again) heavily compromised by malware.

In testing his computer with Ubuntu Live 10.10 the only issue in our way to ditching windows is that the wifi drops as soon as any activity goes through it like installing drivers from the repositories, etc. 

The Wifi is a USB one. Cisco Linksys WUSB54GC ver. 3

When I plug in lspci the controller is referred to as Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

I see here: [https://help.ubuntu.com/community/Ha...rdsLinksys#USB](https://help.ubuntu.com/community/Ha...rdsLinksys#USB)

... that on earlier versions of Ubuntu it was reported to NOT work out of the box. It has actually worked out of the box, but it drops the connection, and looking at this thread this may not be anything to do specifically with the USB Wifi we have, but a more general issue.

I may create a new thread to search for an option.


This issue happens whether or not encryption is used on the connection. I have also tried changing channel. It was on 9 and I changed it to 6.

Based on what I have read on this thread: [http://ubuntuforums.org/showthread.php?t=1203594](http://ubuntuforums.org/showthread.php?t=1203594) I think it is most likely a driver issue and I suspect I may need to use ndiswrapper. If that is the case, I am not sure how to reference the correct driver when following out instructions given on that thread.

I found drivers here: [http://www.linksysbycisco.com/AE/en/support/WUSB54GC/download](http://www.linksysbycisco.com/AE/en/support/WUSB54GC/download) : but I am not sure if they can be used in that state... meaning that they may have installers and so on, as opposed to just being the raw driver. Not sure what ndiswrapper requires.

The connection drops after a few seconds to a minute or two. I will post in a new message what the logs say. Will try doing that from the computer with this issue.


Here is the chipset info:
> Bus 001 Device 008: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2870]

Cheers,

Jonathan

---

### Post by inspired on 2010-10-31
I have tried to install WICD as an alternative to NetworkManager, but it does not appear to be in the default repositories. Also, this computer does not have easy wired net access, so I'd need to download the wicd deb file and install it manually once I have uninstalled NetworkManager.

I wanted to try wicd before trying to change the driver.

The connection on that computer with Ubuntu drops so quickly (within about 30 seconds) so it is not easy to copy and paste any data from that computer to the forum. Thus if there is something in particular that would be useful, please let me know and I'll do my best to post that... rather than trying to post a whole lot of stuff that may not be required or useful.

Cheers,

Jonathan

---

