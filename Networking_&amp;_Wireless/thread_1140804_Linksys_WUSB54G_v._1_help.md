---
title: "Linksys WUSB54G v. 1 help"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by lex3001 on 2009-04-27
I would like to use this Linksys WUSB54G version 1 with Ubuntu 9.04, which I just installed.

If it is plugged in when I try and boot, the system will hang (see [http://ubuntuforums.org/showthread.php?t=1140797](http://ubuntuforums.org/showthread.php?t=1140797))

However, I can boot and then plug it in.
When I do so, I am having trouble getting it to work.
I found these two links to help me:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB54G](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB54G)
and [http://ubuntuforums.org/showthread.php?t=298355](http://ubuntuforums.org/showthread.php?t=298355)

The problem is:
when I try 'sudo modprobe -r islsm_usb' I get a message that islsm_usb is not found.
When I remove ndiswrapper and re-add it, it hangs on the adding it back part.

Thanks in advance..

---

