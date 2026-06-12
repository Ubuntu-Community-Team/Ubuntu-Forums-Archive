---
title: "Ubuntu Wireless no longer enabled."
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by whitneybdy on 2011-02-22
About two days ago was when I was last able to connect wirelessly.  I cannot recall a change I made to the system that would have caused this problem.

Items to consider:
1.  Under Network Manager, I am unable to click "Wireless Networks"
2.  I ran the following code under in the terminal (*sudo apt-get update; sudo apt-get install hwinfo grep; sudo lshw -C  network; rfkill list; sudo iwlist scanning; cat /etc/network/**interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -short; uname -a; dmesg | egrep 'acx|at76|**ath|b43|**bcm|CX|**eth|ipw|**irmware|**isl|lbtf|**orinoco|**ndiswrapper|**NPE|ound|**p54|prism|**rtl|rt2|**rt3|rt6|**rt7|usb|**witch|wl'**; iwconfig; cat /etc/modprobe.d/* | egrep 'acx|at76|**ath|b43|**bcm|CX|**eth|ipw|**irmware|**isl|lbtf|**orinoco|**ndiswrapper|**NPE|p54|**prism|rtl|**rt2|rt3|**rt6|rt7|**witch|wl'**; sudo hwinfo --netcard ; cat /var/lib/**NetworkManager/**NetworkManager.**state; sudo lsmod) *and proceeded to run enter BIOS where I enabled the Network Driver.
3.  I am still unable to get the "Wireless Networks" to even be selectable under the Network Manager
4.  When I return to BIOS, the computer shuts down immediately.
5.  The start-up menu won't allow me access.
6.  I have an HP G60-445DX notebook and an MCP77 Ethernet..  



       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:e0:f7:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz

---

### Post by uncaspi on 2011-02-23
Have you tried wicd instead of Network Manager?

---

### Post by whitneybdy on 2011-02-23
I just tried.  It still is not recognizing any wireless networks.

---

