---
title: "Wireless range and authentication problems"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by Sparks3rd on 2012-12-17
Hi, just installed Ubuntu 12.10 and I'm having problems with my wireless usb adapter. The model i was using is and edimax 7622umn and it has chipset rtl8192su. When used in a Windows computer it can find my wireless network and show a very good signal strength however it will never connect as it continues to ask for a password. When used with Ubuntu it cannot even see the network (however it manages to find other networks in the neighbourhood) but I tried adding my network as if it was hidden. I get the same problem it will never connect and continues to prompt for a password (I know for a fact that I am using the correct password). 

So I put it down to a hardware problem and went and bought another adpater. A belkin N300 which lone behold uses the same rtl8192su chipset. And again I get exactly the same problem except this time the belkin works perfectly fine on the windows computer.

I tried to install and use ndiswrapper but am having troubles as when I enter the following code:

sudo ndiswrapper -i net8192su.inf 

I get a persmission denied error message.

Any suggestions would be greatly appreciated as I have been struggling with this problem for a while now.

---

### Post by chadk5utc on 2012-12-17
Hi
after googling your issue I was able to find a few links regarding your wireless 
[http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix](http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix)

also try:
[https://www.google.com/search?q=ubuntu+rtl8192su&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](https://www.google.com/search?q=ubuntu+rtl8192su&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

