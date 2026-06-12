---
title: "network printer options not viewable"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by silverrope on 2012-08-03
I have set up a printer server on an IBM ThinkCentre desktop running 12.04. I followed the community documentation [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu). I set the printers to be shared using the CUPS admin interface.

On my client ThinkPad laptop that is also running 12.04, I found the network printer, no problem, using the hostname and the ipp protocol. I was not prompted to install a driver. The printing works when I print a test page, but when I check the printer properties on the client side, I can see Settings, Policies, Access Control, etc., but I cannot see the Printer Options. Clearly, the options are needed to change to landscape, set dpi, etc.

Is it normal that network printer options are not viewable and changeable via ipp?

---

### Post by silverrope on 2012-08-04
Ok, no one is interested in answering this. Let's make the question easier since the first one is too challenging.:)

The printer server is setup on a Ubuntu 12.04 machine. What is the ideal way a connection could be made from a Ubuntu 12.04 client machine so that one can see the printer options?

---

### Post by silverrope on 2012-08-06
Gawd, Ubuntu is really not ready for primetime. The setup that I am asking for is very basic, Ubuntu client trying to print to a Ubuntu print server. Yet even here the documentation is incomplete or misleading. <rant off>

I figured it out. Once the printer is installed on the Ubuntu client via IPP, one is not finished. One selects the Printer, right-click to Properties. One can see that "Make and Model" initially just says "Remote printer". Clicking on the Change button allows one to install a driver from the foomatics database, which I believe is the local database of drivers. Select the driver that is the closest to the manufacturer's brand. Once the driver is installed, the Printer Options to appear. There is a warning that the foomatics driver will not be as good as the manufacturer's Linux driver, but at least I can change to Landscape and change the resolution!

Linux docs sux, but hey, it's a free OS, so what can I expect?  :wink:

---

