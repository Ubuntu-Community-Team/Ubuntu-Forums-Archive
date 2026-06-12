---
title: "Is it possible to capture all network traffic using wireshark in ubuntu?"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by Coolai on 2013-02-27
I want to know if using Ubuntu OS can capture all the network traffic/packets in a LAN using Wireshark.

I'm trying to capture the packets from my Desktop PC (connected via cable to the router) and my Phone (connected to the router wireless, Android).

If not, are there any other software that can capture packets on other devices(in a LAN) in Ubuntu like Wireshark?

---

### Post by The Cog on 2013-02-27
Yes, assuming that you install wireshark on your PC. Not all wifi adapters can capture promiscuously, so you may not be able to capture the wireless conversation from a separate eavesdropping PC. 

tcpdump, a command-line capture tool, is installed in Ubuntu by default if you want to try that before installing wireshark. But wireshark is rather nicer to look at traces with.

---

### Post by haqking on 2013-02-27
> **Coolai said:**
> I want to know if using Ubuntu OS can capture all the network traffic/packets in a LAN using Wireshark.

I'm trying to capture the packets from my Desktop PC (connected via cable to the router) and my Phone (connected to the router wireless, Android).

If not, are there any other software that can capture packets on other devices(in a LAN) in Ubuntu like Wireshark?

yes.

Learn wireshark.

The interface needs to support promiscuous mode, (in wireless this is called monitor mode)

What you capture depends on where your capture device is and you may need a hardware tap.

read the documentation here [http://wiki.wireshark.org/CaptureSetup/Ethernet](http://wiki.wireshark.org/CaptureSetup/Ethernet)

---

