---
title: "Wireless USB Card"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by lhbecker on 2009-06-10
I have a Novatel GSM/UMTS/HSDPA Wireless Card. I have installed Ubuntu 9.04 before and the card was automatically detected and accessible through the Network Manager. I was able to set it up and working quickly. I have now installed Ubuntu Studio and detection and setup did not happen as easily.

According to the documentation, the "New Mobile Broadband Connection Wizard" is supposed to start automatically and if not, it should be accessible through the network manager on the panel at the top of the screen. On my installation of Ubuntu studio 9.04 there is not any network manager visible on the panel and only a "Network Monitor" available for the panel at the top of screen which only lists "eth0" and "l0".

If I run lsusb my card is listed as shown below
Bus 006 Device 002: ID 1410:1430 Novatel Wireless

How can I get my card setup and going. Is there a way to launch the "New Mobile Broadband Connection Wizard" manually?

I will appreciate some help.

Regard
Louis

[COLOR=Red]Found and installed the network-manager-gnome on Synaptic Package Manager. After a restart, the system automatically detected my wireless card. It is working now![/COLOR]

---

