---
title: "Ubuntu Server, unable to add PCI ethernet card."
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by kn0w-b1nary on 2012-07-29
Hello all!

I am trying to add an ethernet card to an older dell I'm using as a file server.

Currently I have a Trendnet TEG-PCITXR, but I can't find much documentation and nothing since kernel 3.x

Any suggestions?

---

### Post by VinDSL on 2012-07-29
I had a similar problem, with >= Linux 3.2 not recognizing the pseudo, southbridge-driven, onboard LAN device on this computer.

The intermediate fix was to uninstall network-manager, and install Wicd.

The long-term fix, was to install a NIC that Linux 3.2 / 3.3 / 3.4 / 3.5 supported... in my case, I installed a Netgear PCI Ethernet card with a real DEC "Tulip" chipset, e.g. none of this cheapskate, pseudo device nonsense.

Network-manager has worked fine, ever since!

I strongly suspect they removed support for many older LAN devices, in the most recent Linux kernels.

I would:
[LIST]
[*]Run Wicd instead of network-manager, and/or
[*]Switch to a different LAN card
[/LIST]
Both methods worked for me.

---

### Post by Cheesehead on 2012-07-29
Network Manager and wicd are pretty front-ends to make networking easier. They don't magically add any kernel modules (drivers) or otherwise improve compatibility.

Try the command [FONT="Courier New"]lspci -vv[/FONT] to see if the hardware is detected properly, and which kernel module (if any) is being assigned.

If a kernel module is being assigned, check the startup logs using [FONT="Courier New"]dmesg | grep eth[/FONT] to see what eth* interface(s) the hardware is being assigned or reassigned to.

Since your title says "Ubuntu Server," is the assumption that you do NOT have wicd or Network manager installed correct?

Did you have another PCI ethernet card previously installed? If so, check /etc/udev/rules.d/70-persistent-net.rules . udev will match the (old) card to a specific interface, which will prevent the new card from using that interface. It's trivial to change...if you remember to.

---

### Post by kn0w-b1nary on 2012-07-31
> **Cheesehead said:**
> Network Manager and wicd are pretty front-ends to make networking easier. They don't magically add any kernel modules (drivers) or otherwise improve compatibility.

Try the command [FONT="Courier New"]lspci -vv[/FONT] to see if the hardware is detected properly, and which kernel module (if any) is being assigned.

If a kernel module is being assigned, check the startup logs using [FONT="Courier New"]dmesg | grep eth[/FONT] to see what eth* interface(s) the hardware is being assigned or reassigned to.

Since your title says "Ubuntu Server," is the assumption that you do NOT have wicd or Network manager installed correct?

Did you have another PCI ethernet card previously installed? If so, check /etc/udev/rules.d/70-persistent-net.rules . udev will match the (old) card to a specific interface, which will prevent the new card from using that interface. It's trivial to change...if you remember to.

no card was installed previously. I'm on my 2nd PCI card, no luck yet. :/

I have an old NETGEAR WiFi card I'll try next, w/ ndiswrapper.

I want to have the server connected on 2 networks, 1 with normal internet access, and the other on a different router that I have connected to a VPN via Tomato.

---

