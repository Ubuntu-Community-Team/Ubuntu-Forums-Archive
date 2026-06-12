---
title: "Printer sharing problem..."
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by printerproblem on 2011-03-14
Hello. I have a LAN with 5 computers with Ubuntu and one with WinXp on the 6th computer is also Ubuntu OS and it is have an installed printer. I searched and look over other forums but nothing did not worked out. 

I want to share the printer over LAN to be able to print from the other computers as well from the other 5 computers with Ubuntu and the 6th with Winxp. 

Can someone guide me how to configure the printer settings on the computer where the printer is installed. It's has the proper drivers and it is working. But from the other computers is not working to print via LAN.

Any suggestions will be appreciated.

---

### Post by pricetech on 2011-03-14
Samba:

[http://ubuntuforums.org/showthread.php?t=1644585](http://ubuntuforums.org/showthread.php?t=1644585)

---

### Post by rvchari on 2011-03-14
> **printerproblem said:**
> Hello. I have a LAN with 5 computers with Ubuntu and one with WinXp on the 6th computer is also Ubuntu OS and it is have an installed printer. I searched and look over other forums but nothing did not worked out. 

I want to share the printer over LAN to be able to print from the other computers as well from the other 5 computers with Ubuntu and the 6th with Winxp. 

Can someone guide me how to configure the printer settings on the computer where the printer is installed. It's has the proper drivers and it is working. But from the other computers is not working to print via LAN.

Any suggestions will be appreciated.

i presume you have samba installed.
now on any other ubuntu pc, go to printers and add printer.
it may not search for the network printer, you can manually configure by giving the ip address say //192.168.0.1 or whatever your ip may be at the printer connected pc.
it will locate and keep that as default.

if your printer is connected to ubuntu, see if the permissions for sharing is active, if not make it a shared printer.

i am using ubuntu and can easily print thru my office lan which is running windows.

---

