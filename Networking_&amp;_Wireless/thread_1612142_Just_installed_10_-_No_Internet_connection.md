---
title: "Just installed 10 - No Internet connection"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by shoepolice on 2010-11-02
Hi there

I've just installed Ubuntu 10 as a last resort to save my laptop from the bin. However, I'm having similar issues to when I installed 9.x a few months back. First off, I have no network connection at all (using another laptop just now). I've plugged in the network cable from the modem and although it looks to be doing something, it doesn't establish a connection. The wireless is also not connected due to Firmware not installed. I remeber this was a common issue with the Broadcom 43xx modem but I need to get the wired network going first to be able to download drivers *I think*. Can anyone provide a starter for ten? I don't really know where to start.

Thanks

---

### Post by grahammechanical on 2010-11-02
We need to confirm that you have checked the silly things first. Is networking enabled? Right click the network manager icon. Is the wired connection set to Automatic DHCP under the IPv4 tab? in Edit connections? We are assuming that the router/modem has the correct information for connecting to your ISP. Can you use a browser to access the settings in the router? You put [http://192.168.1.254](http://192.168.1.254) as the url in the browser. Or something like that.

If you type nm-tool and ifconfig in the terminal, what information do you see? Do you see eth0 or eth1 as UP and as RUNNING? This tells you if the ethernet card is working.

Regards

---

