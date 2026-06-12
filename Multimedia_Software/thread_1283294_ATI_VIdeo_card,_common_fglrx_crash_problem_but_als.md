---
title: "ATI VIdeo card, common fglrx crash problem but also problem with free driver"
date: 2009-10-05
forum: Multimedia Software
---

### Post by Mr8reep on 2009-10-05
Hello, I have a small problem with my graphics when booting ubuntu. I'll start by saying that I have been using Jaunty Jackalope for about 3 days (fresh convert from windows vista) and I use an ATI Radeon X1800 graphics card; I'm also aware that problems with ATI cards are quite common in ubuntu. I have been having the problem that I've read about a lot with the fglrx driver installed through ubuntu's add/remove programs menu: whenever I install this driver I get an odd graphical anomaly after the ubuntu loading bar comes up and my computer completely freezes with the anomaly blinking once every 6 seconds or so. If anyone can point me to a workaround for this I'd appreciate that, but it's not my main concern at the moment.

What worries me more is that even while using the default open source driver that I assume comes with a fresh ubuntu install I still get that same graphical anomaly for a split second, but my computer boots without a problem. It doesnt seem to be causing any trouble but I believe it hints that my graphics card is still not working properly with the open source ubuntu driver.

I would appreciate the help of anyone who can shed some light on this, so thank you in advance. If more information is needed I will also post screenshots of my devices info from vista when I get home.

---

### Post by markbuntu on 2009-10-05
The x1800 is not supported by fglrx in Jaunty so you should remove it. For help getting the latest open source driver which is much improved from the one in the repositories:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

