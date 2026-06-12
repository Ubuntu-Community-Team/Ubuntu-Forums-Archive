---
title: "Problem with ISDN (Fritz! PCI 2.0)"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by The_Burrito on 2006-06-17
I tried to get the Internet connection running on my PC where i recently installed Ubuntu 6.06. I followed the instructions on the Wiki and everything seemed fine.
Neither capiinfo nor pon reported any error, but i wasn't able to connect to the internet.
After that i found out, that the isdnvboxserver package wasn't installed correctly, because of this error:

> 
Richte isdnvboxserver ein (3.7.2005-07-09-2ubuntu4) ...
/var/lib/dpkg/info/isdnvboxserver.config: line 105: unexpected EOF while looking for matching ``'
/var/lib/dpkg/info/isdnvboxserver.config: line 245: syntax error: unexpected end of file
dpkg: Fehler beim Bearbeiten von isdnvboxserver (--configure):
 Unterprozess post-installation script gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 isdnvboxserver

I tried to fix this error, but it produced just another one. And because of this a can't install the isdnutils package as well.
I don't know if solving this problem would fix my connection issues, but that's the only clue I have at the moment.

I hope, someone can help me, thanks.

---

