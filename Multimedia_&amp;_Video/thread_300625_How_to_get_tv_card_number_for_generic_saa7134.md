---
title: "How to get tv card number for generic saa7134?"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by josesanders on 2006-11-15
Ununtu recognizes my card but it can't get the card number.  It is totally generic, and based on the Phillips 7134 chipset.  I had it running in Windows using the drivers that came with it.  When I run dmesg, it says that my card doesn't have an eeprom, so the card type couldn't be determined automatically.  Since there is no name or serial number anywhere, is there any way for me to figure out what card number it is?  There are about a hundred options.

I don't know if it will help, but here are the names of the windows drivers that work.

34API.DLL
34DD.DLL
34TVCTRL.DLL
CAP7134.INF
PHTVTUNE.CAT
PHTVTUNE.SYS
34COM.DLL
34DIALOG.DLL
CAP7134.CAT
CAP7134.SYS
PHTVTUNE.INF
PROP7134.DLL

Any suggestions would be much appreciated.

---

### Post by jhenager on 2006-11-16
All cards are required by the FCC to put an ID number on it. It requires that you remove the card. Then go to driverguide.com and search by FCC number. That will give you the manufacturer.

I also found some good information on Google by searching on saa7134:
[http://www.linuxtv.org/v4lwiki/index.php/Generic_SAA7134_Card_Installation](http://www.linuxtv.org/v4lwiki/index.php/Generic_SAA7134_Card_Installation)

---

