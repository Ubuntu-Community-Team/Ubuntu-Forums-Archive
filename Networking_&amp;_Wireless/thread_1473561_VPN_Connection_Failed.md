---
title: "VPN Connection Failed"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by golfnut324 on 2010-05-05
My vpnc connection is great, the first time I connect after booting up. If I close the connection and then try to connect again I get the VPN Connection Failed in the image below. I have to re-boot in order to connect again. Sometimes the connection holds for hours and sometimes I lose it after 20 minutes or so. No big deal if I can re-connect without re-booting.

Any solution ideas would be greatly appreciated.

Thanks,
Craig

---

### Post by torfosnaes on 2010-05-05
search ubuntu forums for a post by a sweisler on vpn setups; it takes a while to find, but it works for several vpn clients under ubuntu 9.10. 

dropping the vpn connection once established, in my experience, is a flaky internet connection; for example, do you drop your browser connection frequently?

---

### Post by golfnut324 on 2010-05-05
> **torfosnaes said:**
> search ubuntu forums for a post by a sweisler on vpn setups; it takes a while to find, but it works for several vpn clients under ubuntu 9.10.


I'll do that. After I posted here I realized this was maybe more for internet and wireless connections.


> dropping the vpn connection once established, in my experience, is a flaky internet connection; for example, do you drop your browser connection frequently?
I rarely have trouble with my browser or internet connection. My main problem is that once a vpn connection is terminated, for whatever reason, I can't re-establish it without re-booting computer. I get the message posted. What do you think about 'VPN service failed to start"? Keep in mind that it works the first time after a boot.

Thanks

---

### Post by torfosnaes on 2010-05-09
Yeah.
If you start with an empty VPN configure scren and follow sweisler's instructions (enter stuff, reboot, enter more stuff, etc) it seems to sort itself out; the instructions are for different modem and connection types but all are for vpn configuration.
I also lost connection and or couldn;t establish a vpn until I did the method, and now it is stable every time; it can also be hooked up and run in background while doing other Internet operations, even other remote connections; I often keep my windows vpn and my linux home server connected at the same time swithching form one to theother as needed.

I had similar problems with the windoews vpn in 9.04 and 9.10 which were solved in differnt ways.

Good luck.

---

