---
title: "Network Printing"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by dahornor on 2010-03-04
I know this seems to be a common problem, but none of the threads I've tried have helped so far...

I am running UNR (Karmic) on my netbook.  I have not been able to use the HP LaserJet 1020 which is attached via USB to my Mac OS X machine.  I stumbled upon a great post that helped, but then I reinstalled my UNR and I can't find the forum thread again.

Any help would be greatly appreciated.

Thanks,

dahornor

---

### Post by johnson.d on 2010-03-09
You can share the printer that is connected to you imac using the following link:

[http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh1770.html](http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh1770.html)

Now you can configure your Ubuntu Machine to install the printer that is shared form your imac using the following steps.

1) Go to Gnome menu-> System-> Administration-> Printing.
2) A window will open, Click new.
3) Another Window will open. At devices, drop down Network printer, Click Windows Printer via Samba.
4) At the right hand side, There will be a box with 'smb://'. Here enter the ip-address and the printer name as follows:
smb://<ip-address>/<shared-name of the printer>
5) Choose the driver and finish the installation.
6) Now try printing from the Ubuntu System.

---

