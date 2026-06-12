---
title: "Network printing: Unix printer works, not Windows?"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by mailforbiz on 2006-05-30
Hi all

I have been having mixed success in setting up my Ubuntu but not really anywhere near there yet.

The current "project" is getting network printing to work. This is an office Lan with two printers on it First off, autodetection didn't work for me. I tried making the changes to cupsd.conf file and restart (after checking the autodetection flag) but didn't really show any printers. So I set about to manually setup the printers. I didn't really know which printer was what kind. From my WinXp system, I looked at the printer configurations and found this:

Printer A:
Host: xyz.com
Protocol: Raw
Port: 9100

Printer B:
Host: abc.com
Protocol: Line Printer
Port: 515
Queue: lp1

Based on the above, I did some trial and error in the New Printer Dialog and was able to set up printer B as a Unix printer. But no such luck with printer A. I can't tell if its a Windows printer, CUPS printer or a Hp DirectJet. From the settings required for each, it seems to be Hp DirectJet. 

The change I made to the /etc/cups/cupsd.conf were to this section.

```
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From @LOCAL
Allow From 192.168.3.*
</Location>

```

It would be nice to have printer A setup as printer B is on the other end of the hallway while printer A is next to my cube.

Any pointers ? Thanks in advance.
HT

---

