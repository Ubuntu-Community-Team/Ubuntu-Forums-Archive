---
title: "Linksys WPC54G v3 Wireless Card Not Working"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by majortomm on 2009-03-31
I have scoured the threads and tried at least 10 different ways to get this wifi card working and I am still at square 1.  

If I go to the Hardware Drivers program it sees the card and wants to activate the drivers.  I choose activate and it goes through and downloads and installs the drivers but it never activates.  It just stays in the same state of grey unactivated button.  

If I go through the Package Manager and install the bcm43xx-fwcutter program it shows that it installs but when I look at the details I get the following errors so it doesn't actually install even though it shows that it is.
```

E: b43-fwcutter: subprocess post-installation script returned error exit status 1
```

```
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2009-03-30 21:07:16--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-03-30 21:07:17 ERROR 404: Not Found.

dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1 
```

Any help would be greatly appreciated!

Thanks

---

### Post by Garyx on 2009-03-31
I have the same issue. The thing is that openwrt.org are upgrading their servers and a file that b43-fwcutter needs to download hasn't been restored yet. 

When this link here is up again:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Then you will see that that b43-fwcutter will work again. I'm hoping they will have everything back up again soon.

---

### Post by Kkooky on 2009-03-31
The site is back up.  I have successfully installed my Broadcom firmware and driver on my HP laptop.

---

### Post by Garyx on 2009-03-31
I was just about to post the same. The download section of openwrt.org is back up and thus b43-fwcutter should not get the 404 error anymore.

---

