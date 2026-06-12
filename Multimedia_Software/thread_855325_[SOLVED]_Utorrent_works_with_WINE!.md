---
title: "[SOLVED] Utorrent works with WINE!"
date: 2008-07-10
forum: Multimedia Software
---

### Post by phantomjoker on 2008-07-10
OK so Utorrent works in Ubuntu despite peoples thoughts - no expensive software needed - just WINE, _not_ WINEx

Simply install WINE from

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

and download Utorrent from 

[http://download.utorrent.com/1.7.7/utorrent.exe]("http://download.utorrent.com/1.7.7/utorrent.exe")

Run and install utorrent through WINE - it may ask you to update/install the 'http' script - let it do its thing.

ok so it now get complicated...

once opened you may get a box like this appearing -
[IMG]http://i38.tinypic.com/t9b71d.jpg[/IMG]

exit this and go into 'Options' 'Preferences' or just 'Ctrl P'

Connection Tab - Enter your port number you want to download through
               - Make sure any mapping (UPnP or NAT-PMP) is off (unticked)

the other options are of your own choice - dont use proxy...

Then you need to edit your own internet settings by entering your IP address into the address bar of firefox (or whatever internet browser you use) make sure you have set you 'virtual servers' to allow the static port number you previously set to be accessed - FOR MORE HELP AND STEP BY STEP GO TO 

[http://www.portforward.com/english/applications/port_forwarding/Utor/Utorindex.htm]("http://www.portforward.com/english/applications/port_forwarding/Utor/Utorindex.htm")

Then just find a torrent you want

open it with Utorrent... the utorrent file is located where you installed it (obviously) but incase your not sure - thats in file system, media, wine, utorrent

hope this works... and ENJOY!!

---

