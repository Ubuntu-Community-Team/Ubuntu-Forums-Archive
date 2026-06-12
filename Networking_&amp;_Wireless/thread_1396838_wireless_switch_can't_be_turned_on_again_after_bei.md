---
title: "wireless switch can't be turned on again after being turned off.."
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by Angewandte on 2010-02-02
Hi everyone,

I have a small problem to ask for help here:

The wireless connection works fine. The wireless switch automatically turns itself on every time I start the computer. However, after turning it off, I can't ever turn it on again unless I restart the computer. And because of this, the wireless connection is disabled until the next time I start the computer.

I don't think this is a hardware problem because the switch can be turned on and off, although not in the way I expect.

I'm using ubuntu 9.10 on an Acer Aspire 4740G. The command [lspci | grep Network] shows Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01).

the [rfkill list] command shows (when the switch is on)
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

and, as expected, shows (when the switch is turned off)

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

I just want to be able to turn the switch on or off at any time I want as long as the computer is still on. Any help would be very appreciated. 


Have a good time! :)

---

### Post by shane8002 on 2010-02-02
just disable wireless networking through the network manager

---

### Post by Angewandte on 2010-02-02
Hi Shane8002, Thanks for the reply.. Well, that doesn't help and you remind me about one other thing. The enable/disable option is greyed-out when I accessed it from the network manager icon in the icon tray.

That's why I think it must have to do with software configuration..??

---

