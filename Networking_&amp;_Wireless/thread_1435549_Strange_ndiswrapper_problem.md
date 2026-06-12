---
title: "Strange ndiswrapper problem"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by wah fun on 2010-03-21
I have a somewhat strange problem - I think. I have tried to get ndiswrapper to work on an ubuntu 9.04 32 bit system but have yet to succeed. After installing the windows driver, the usb wireless network adapter is recognized but will never connect to the internet. I have disabled the driver included with jaunty. Now what makes this strange (at least to me) is that ndiswrapper works perfectly with ubuntu 9.04 64 bit. It could very well be something that I am not doing in the 32 bit system (but I don't know what that might be).

I have tried ndiswrapper with several other distros with the same result. So, I don't think it is specifically related to ubuntu however, since ubuntu is what I am using, I am posting in this forum hoping that someone might be able to help me. I have several 32 bit machines I would like to set up but cannot until I get this resolved. I have also tried downloading and compiling a native driver with no success either. 

Anyway, here is my setup:
PC with AMD64 dual core processors running at 2Ghz and 3 GB ram.
Belkin N150 Enhanced Wireless Router
Belkin N150 Enhanced Wireless USB Network Adapter

And an aside: I am using WICD network manager and would like to know what the tray icon means when it says it is connected at say 54%. My question is, 54% of what? In windows this info is given in Mbps which is more meaningful. If you can help me with this I would appreciate it as well.

thx

---

### Post by bkratz on 2010-03-21
> **wah fun said:**
> I have a somewhat strange problem - I think. I have tried to get ndiswrapper to work on an ubuntu 9.04 32 bit system but have yet to succeed. After installing the windows driver, the usb wireless network adapter is recognized but will never connect to the internet. I have disabled the driver included with jaunty. Now what makes this strange (at least to me) is that ndiswrapper works perfectly with ubuntu 9.04 64 bit. It could very well be something that I am not doing in the 32 bit system (but I don't know what that might be).

I have tried ndiswrapper with several other distros with the same result. So, I don't think it is specifically related to ubuntu however, since ubuntu is what I am using, I am posting in this forum hoping that someone might be able to help me. I have several 32 bit machines I would like to set up but cannot until I get this resolved. I have also tried downloading and compiling a native driver with no success either. 

Anyway, here is my setup:
PC with AMD64 dual core processors running at 2Ghz and 3 GB ram.
Belkin N150 Enhanced Wireless Router
Belkin N150 Enhanced Wireless USB Network Adapter

And an aside: I am using WICD network manager and would like to know what the tray icon means when it says it is connected at say 54%. My question is, 54% of what? In windows this info is given in Mbps which is more meaningful. If you can help me with this I would appreciate it as well.

thx

First, I don't use wicd, so I know nothing about it.  Secondly, are you trying to use the same 64 bit driver in your 32 bit Ubuntu systems. It sounds like you are using the wrong driver, try the 32 bit xp version.

---

### Post by wah fun on 2010-03-21
I am using the 32 bit xp driver not the 64 bit driver. Any other ideas?

---

### Post by wah fun on 2010-04-19
No new ideas on this? Anyone?

---

