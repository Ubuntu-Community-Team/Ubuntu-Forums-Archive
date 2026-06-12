---
title: "samba 3.6.6 truncates shared printer name"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by bitter_mike on 2013-02-20
Hey,

I'm running 12.10, 64-bit, running samba version 3.6.6. I have an HP Laserjet 1320 connected via USB and locally, the printer works perfectly. I'm attempting to share it over the network via samba and the printer is visible to other computers on the network running various versions of Windows. However, when you try to connect to the printer, you get the following error:

Windows couldn't connect to the printer. Check to the printer name and try again. If this is a network printer, make sure that the printer is turned on and that the address is correct.

I check the samba logs in /var/log/samba/ for that specific machine and I see this:

[2013/02/20 19:59:05.098843,  0] rpc_server/spoolss/srv_spoolss_nt.c:1748(_spoolss_OpenPrinterEx)
  _spoolss_OpenPrinterEx: Cannot open a printer handle for printer \\xxx.xxx.xxx.xxx

The thing is, "the printer" in that error is the IP address of the linux box hosting the printer. The printer itself is \\xxx.xxx.xxx.xxx\laserjet. This is confirmed by listing the printers detected by samba which clearly indicate the full path to the printer.

So, somewhere the path to the printer is being truncated down to the path of the machine which hosts it. I have seen reports of a bug like this where the path to the printer is improperly truncated when it is connected, but both the rpclient and samba list the full and correct path. This happens on all Windows machines. The printer is still accessible via CUPS and you can print via ipp from these same Windows machines.

Has anyone else seen this? Any help would be appreciated.

Mike

---

