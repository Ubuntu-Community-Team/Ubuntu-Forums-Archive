---
title: "enabling wireless printing..."
date: 2012-10-13
forum: Networking &amp; Wireless
---

### Post by Baldrick_NZ on 2012-10-13
Hi all,

I'm trying to enable wireless printing on my Brother MFC255CW Printer. I've followed this guide ([http://askubuntu.com/questions/43354/how-to-connect-brother-mfc-255-cw-wireless-printer](http://askubuntu.com/questions/43354/how-to-connect-brother-mfc-255-cw-wireless-printer)), and all goes well until I get to the part where it says 'modify printer'... 

Then 'localhost:631' requests a User Name and Password. 

I have no idea what either would be! 

Could they be a generic user name and password, or something specific? How would I go about changing it if it were specific.

Any help would be very much appreciated!

---

### Post by kurt18947 on 2012-10-13
I use what I think is a simpler procedure.  First I assign a static i.p. address to the printer using the printer's control panel.  I've had good luck using appsocket so I stick with that.  Next I open this app:
[ATTACH]225494[/ATTACH]
How to get to this depends on what you have installed.  I use F2 then "system-config-printer".  Right-click the printer icon and left-click "properties".  The default Device URI is something like "usb://something. Change the device URI to reflect the printer's i.p. address and I'm in business.

---

