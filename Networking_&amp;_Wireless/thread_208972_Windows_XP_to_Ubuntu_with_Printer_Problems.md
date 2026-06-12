---
title: "Windows XP to Ubuntu with Printer Problems"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by tdrusk on 2006-07-04
I am having trouble configuring my Windows XP to print to my Ubuntu with a printer attached over a network. I tried to configure cups, but that did not work out so well. Right now my cupsd.conf looks like
> DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-b sudo gedit /etc/cups/cupsd.conf
rowsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127. sudo gedit /etc/cups/cupsd.conf
0.0.1
Allow From 192.168.0.1
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>




In Windows I went to Control Pannel>Printers&Faxes>Add Printer> and marked "Connect to a printer o hte Internet or on a home or office network: URL: [http://192.168.0.1:631/printers/PhotoSmartP1115](http://192.168.0.1:631/printers/PhotoSmartP1115)

and it can't find it.


I looked at my sudo gedit /etc/cups/cupsd-browsing.conf and there was nothing there.


I was trying to follow this guide [http://www.gerona.gov.ph/davidjr/?p=57](http://www.gerona.gov.ph/davidjr/?p=57) and it says that there should be one line of text there. I have nothing. What should be there so I can change it to on?

Thanks!

---

