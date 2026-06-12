---
title: "PPP link disconnects with ipforward / bridging"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by russnash37 on 2010-12-05
I've just setup a 64bit 10.10 desktop system on my main machine and intend to use kvm for virtualization in conjunction with bridging to provide full network access for my guest machines.  Being in an out of town area I use a novatel usb720 modem to provide internet access through verizon over 3g with a ppp setup and would like to provide internet access for my entire lan, including the virtual guests systems via ip forwarding.  This solution has worked well for internet access for me for several years, however, now that I've brought bridging into play I've noticed that it seems to conflict with the forwarding:

With the ppp internet link started, internet access works fine from the local host, however, whenever either a kvm guest or another system on my local LAN tries to access the internet traffic does not pass and within a few seconds "LCP terminated by peer" pops up in /var/log/messages and the PPP link terminates.  I've noticed that this occurs whether ipforwarding is enabled or not, seems that the PPP link just doesn't play well with the bridging setup.

Has anyone else come across this issue and/or can provide any insight or a fix?

Russ.

---

