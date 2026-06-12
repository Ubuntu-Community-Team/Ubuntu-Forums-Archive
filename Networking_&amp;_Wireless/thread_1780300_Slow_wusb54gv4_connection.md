---
title: "Slow wusb54gv4 connection"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by PummelMonster on 2011-06-11
Hello,

I'm having a problem with my Linksys Wireless 54g version 4 NIC card.  It has a connection to the Internet, but it is very slow (>1kb/s usually).  However, I've installed RutilT and it says I have a 54Mbps connection.  BTW, I'm on Karmack 10.10 and using the default rt2500usb driver (confirmed by a lsmod | grep usb).

I've read a lot of forum posts that dealt with no connection at all with the wusb54g, but mine is different in that I have a connection.  To add some complexity to the situation check this out.  When I try to download something (webpage, update packages, etc...) they come at the low rate mentioned above.  However, I've discovered that if I have a browser open to [www.speakeasy.net/speedtest/]("http://www.speakeasy.net/speedtest/") and click on any of the test links while downloading the webpage, updates, etc... then all of a sudden they take off and download fast.  (BTW, the Speakeasy test results normally show a speed of 10Mbps+ on average).

Obviously opening Speakeasy.net/speedtest/ and clicking on a link over and over to do any type of Internet browsing or downloading is not acceptable.  And, BTW, when the test is over the speeds go back to crap.

I was going to install the SerialMonkey driver but then went to their site and read a bit and realised they are already bundled into the kernel.  I was also going to mess with ndiswrapper but figured that since most posts I had read utilized this solution because the card was not working at all.  My card is somewhat working though.  So before I headed down that road I figured I'd ask some people who know a lot more than I do as I'm pretty noob in Linux.

Do any of you have any suggestions for me?

Thank you for your time and consideration.

---

