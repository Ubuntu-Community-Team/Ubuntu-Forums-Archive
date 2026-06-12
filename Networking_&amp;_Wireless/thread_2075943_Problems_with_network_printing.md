---
title: "Problems with network printing"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by kleinempfaenger on 2012-10-24
Hi, 
I cant get my printers work over router.
Printers are ok, because when I connect them directly to usb port they work fine.
Tried three different printers (HP, Epson) without any result, so possibly I am the problem.

Connect printer to usb-port on router. Enter router-config from computer over wireless  connection via browser. Printer shows as part of the network, but default software is not linux-compatible. Says: install manually using ip 192.168.1.253.

Ubuntu add printer menu unable to detect printer.
Hplip doesnt find connected hp-printer.

Cups add printer says:

Equipo o impresora LPD/LPR 
 Protocolo de Impresión de Internet IPP (https) 
 Windows Printer via SAMBA 
 Protocolo de Impresión de Internet IPP (ipp14) 
 AppSocket/HP JetDirect 
 Protocolo de Impresión de Internet IPP (ipp) 
 Protocolo de Impresión de Internet IPP (http) 
 Protocolo de Impresión de Internet IPP (ipps) 
 Backend Error Handler 

Have tried:

socket://192.168.1.253:9100
socket://192.168.1.253
[http://192.168.1.253:631/ipp/](http://192.168.1.253:631/ipp/)
[http://192.168.1.253:631/ipp/puerto1](http://192.168.1.253:631/ipp/puerto1)

and others.

Printer adds, but afterwards no connection. Printing fails.

Thanks for your help.

Greetings, kl

---

### Post by ahallubuntu on 2012-10-25
USB connections to routers are special cases and somewhat dependent on the make/model of the router.  I'm not surprised you're having trouble making this work in Linux.

(What's the make/model of your router?)

Do any of your printers have ethernet connections for a direct network connection to your router?  If so, that is much more likely to work than USB to your router, in Linux, anyway.

---

### Post by kleinempfaenger on 2012-10-25
Thanks ahallubuntu,

only one of the printers has ethernet connection via HP 600N JetDirect card. Router detects something plugged in not specified and without IP, but connection fails. Tried the same combinations as mentioned above with an IP that printer config page gives out.

I cant find Router specifications. It only says 

Modem ADSL Dual BHS
Amper BHS ASL 26555 CL

Modem is reffered to as HomeStation.

---

