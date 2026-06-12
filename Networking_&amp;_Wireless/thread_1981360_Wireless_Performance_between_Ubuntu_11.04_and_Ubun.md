---
title: "Wireless Performance between Ubuntu 11.04 and Ubuntu 12.04"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by julianloui on 2012-05-16
A few days ago, I installed Ubuntu 12.04 as the sole operating system on my HP d530 computer. The installation went smoothly and took less than an hour. Even though the IOGEAR GWU625 adapter works well in detecting and connecting to my wireless network, its connection gets disrupted every few minutes. When I plug in a Linksys wireless-G  adapter, Ubuntu detects it all right and goes through the security-key business, but never completes the connection and shows no error messages.

 My Ubuntu 11.04's wireless-network performance has a much better record  regardless which of the above two adapters I use. The network stays solid for hours.  I wonder if this is due to any wireless software changes from 11.04 to 12.04. Last month I actually had attempted to install Ubuntu 11.04 as  the sole O.S. on my HP d530 but for some unknown reasons the resultant 11.04 desktop kept tearing itself up into constantly changing random  black rectangles. So I gave it up. If I could fix this strange problem, I wouldn't mind making Ubuntu 11.04 my HP d530's sole O.S. As a green Linux user, I really like 11.04's utter simplicity.

Julian

---

### Post by cyboreal on 2012-05-17
can you post some diagnostic information when you are having the network problem? Post the output of `lspci`, `ifconfig`, `lsmod`, `sudo rfkill list all`, and the last relevant lines from `dmesg`.

---

### Post by julianloui on 2012-05-18
Hi, Cyboreal,

I obtained the following data shortly after the network connection was interrupted.  As I
said before, the connection has been interrupted and resumed automatically by Unbuntu
12.04 many times daily.  My Ubuntu 11.04 system happens to be free from this problem, even though it uses the same IOGear wireless adapter and the same wireless network.

1) lspci output shows no errors and just the following names.
Host bridge, VGA Compatible Controller, System peripheral, USB Controller #1,#2, #3, USB EHCI controller, PCI bridge, ISA bridge, IDE interface, SMBus, Multimedia audio.

2) ifconfig output:
etho - no errors, no drops, no overruns
lo     - no errros, no drops, no overruns
wlano -no errros, no drops, no overruns

3) lsmod output:
No errors displayed

4) sudo rfkill list all output:
All blank

The data above has been abbreviated by me for simplicity but the gist is there.  Thanks
very much for your advice.

Julianloui

---

