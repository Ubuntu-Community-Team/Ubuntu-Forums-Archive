---
title: "Xmltv"
date: 2009-04-09
forum: Mythbuntu
---

### Post by scottpj on 2009-04-09
Hi, I am running mythbuntu 8.10

XMLTV work fine, but I can't get any data for ITV (london area).

The XMLTVID is calton.itv1.itv.co.uk

All other channels grab data fine, I can only think that the london ITV XMLTVID has changed.

---

### Post by ian dobson on 2009-04-09
Hi,

Are you sure ITV actualy send/allow anyone to have the EPG data for their channel.

I remember reading something on bleb.org or is t bleb.co.uk about ITV and their view that the EPG data is copyright them.

Regards
Ian Dobson

---

### Post by scottishnarn on 2009-04-10
They do occasionally change the name of some chanels. I usually run ```
tv_grab_uk_rt --configure
``` and then have a look for the channel in .xmltv/tv_grab_uk_rt.conf so I can update my .mythtv/sky.xml file (of course yours will be whatever you told mythtv to call it) and update the information in the channels setting (mythweb/settings/tv/channels) in mythweb.

Or you could just run mythtv-setup and setup new channels again.

If you still can't get it working (which sometimes happens to me) then you could try updating xmltv. Uninstall the deb version through synaptic. Download the latest from [http://wiki.xmltv.org/index.php/Main_Page](http://wiki.xmltv.org/index.php/Main_Page) and manually install. I usually install to /opt/xmltv and then link ```
ln -s /opt/xmltv/bin/tv_grab_uk_rt /usr/bin 
``` this allows me to uninstall easily or upgrade.

Hope some of this helps.

---

### Post by scottishnarn on 2009-04-10
Oh and BTW ITV works fine on my machine with the RT listings it's bleb where it doesn't work.

---

### Post by scottpj on 2009-04-10
thanks, upgrading the xmltv version fixed it.

---

