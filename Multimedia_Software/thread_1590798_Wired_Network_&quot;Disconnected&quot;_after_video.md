---
title: "Wired Network &quot;Disconnected&quot; after video card install"
date: 2010-10-08
forum: Multimedia Software
---

### Post by vibrunazo on 2010-10-08
I **just** installed a nvidia GTX460 video card on my computer. And as soon as I installed the driver and rebooted. I got a "Wired Network: Disconnected" message on a notification in the top right. And it shows me that again everytime I restart X. But my network is actually working. If I click on the "connections" button on the top bar. It shows me 2 networks:

eth0: Wired Network (VIA Technologies VT6105[...]) - connected
eth1: Wired Network (nVidia MCP65 Ethernet) - disconnected

What does this means? As far as I know my video card has no network socket in it. How do I disable that weirdo nVidia network driver, but not the video driver? How can I make ubuntu stop complaining about it being disconnected?



Using ubuntu 10.04 with Gnome 2.30.2.

---

### Post by Yellow Pasque on 2010-10-08
You seem to have an nvidia 570sli chipset mobo. These usually have 2 LAN ports. Disable one in the BIOS is the easiest way.

---

