---
title: "Unable to open Linksys https config page"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by basmus on 2012-02-12
This is driving me crazy and I tried searching for the answer. I have a Linksys E3000 and am running Ubuntu 11.10. When I try to connect to my routers config page ([https://192.168.1.1](https://192.168.1.1)) I get a connection reset error after confirming the security exception. There should be a login box that pops up to allow me to login but I get the error instead. I tried installing the chromium browser and it does the exact same thing. I can connect to the page using my iPad. I can even connect to the webpage using a Windows 7 virtual machine running in VMWare on Ubuntu with the same machine. What could be causing this?

---

### Post by UltimateCat on 2012-02-12
I have a Linksys too and until I found and installed the right driver to aid the adapter I could not get online.

I also had to blacklist the rt8169...( do research tho you might not have to) I say that because I have Ubuntu 10.04....your case may be different-

Here's the Linksys's website
[http://www.official-drivers.com](http://www.official-drivers.com)

Good luck to you

---

### Post by basmus on 2012-02-12
Thanks for the reply. I am able to do everything else online. I am accessing this page right now using my Ubuntu machine. I am just not able to access my routers config page with Ubuntu using Firefox or Chromium. Even stranger still is that a virtual machine running on the same Ubuntu can. Is there some kind of firewall in Ubuntu blocking it? Some browser setting that applies to both? Maybe I will try running Firefox as root...   Update -------------- Same result with root and same result with another user. Something in Ubuntu is blocking the password popup in both Firefox and Chromium.

---

### Post by basmus on 2012-02-19
I do not know what was causing this problem. A reinstall of Ubuntu has fixed the issue.

---

