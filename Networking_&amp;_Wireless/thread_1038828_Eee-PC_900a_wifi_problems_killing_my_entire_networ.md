---
title: "Eee-PC 900a wifi problems killing my entire network."
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by happenstobe on 2009-01-13
I picked up an ASUS Eee-PC 900a from Best Buy recently and put Ubuntu-Eee on it the first day. Took me a while to get the wifi and the flash cards working, but I got everything sorted out finally. I've had periodic trouble keeping the wifi up and running, but disregarding those problems completely, it seems that whenever I'm having trouble getting my Eee to connect to my wifi network, my entire network goes down. Even if the Eee can't connect to it at all.

I have a linksys Wireless-G router (rangeplus WRT110) setup with one WinXP desktop hard-wired to it, 2 windows laptops connected wirelessly (one XP, one vista), and an iMac G5 running Leopard also connected wirelessly. Each of my devices has a dedicated static IP address and I use WPA personal encryption. I also have an iPhone, a wireless HP printer, a Nintendo Wii, PSP, etc all that connect wirelessly just fine with these settings.

When My Eee connects to the network, everything is peachy, but whenever the Eee has trouble making the connection, every machine in my house (including the hard-wired one) all lose their internet connectivity. Even the modem it self loses it's send light. But if I just turn off the Eee's wifi, everything works perfectly again for everyone else.

I've tried the default network manager, I've tried WICD. Nothing had made any difference. I am going to try reinstalling tonight with Easy Peasy 1.0 (Ubuntu 8.10) to see if that helps.

I haven't so far found anyone with this same issue. If anyone has any ideas or recommendation, I would greatly appreciate it. Thanks.

PS: I am pretty new to Linux and know little to nothing about terminal.

---

### Post by happenstobe on 2009-01-13
I just wanted to post an update on how I've progressed with this issue.
I reformatted my machine with the update build (easy peasy 1.0 - ubuntu 8.10, etc)
Since this update I've been able to get a reasonably stable wifi connection going, with the exception of one thing.

Whenever I boot the Eee up, my entire house's wifi (and modem) goes out (just as before). The difference now, is that after about 5-6 minutes, the whole network comes back up and everyone is on just fine. This is the same case consistently every time I boot or reboot the machine.

A friend of mine suggested that it could be my router. I am using a linksys rangeplus router (WRT110). He says the rangeplus models send out their packets a little bit differently than a normal router and that this method is not completely ubuntu compatible. So he thinks it might just be a matter of ubuntu's overall compatibility with this type of router, and not my machine or any particular build of ubuntu-eee/easy peasy. I'm going to try to look into this more, but as usual, if anyone has any suggestions, please post.

Thanks.

---

