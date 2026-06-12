---
title: "After upgrading can't find movies"
date: 2009-10-20
forum: Mythbuntu
---

### Post by orduek on 2009-10-20
Hi,
Ok, so I deleted the database and upgraded to mythtv 0.22
I have a few problems now:
1. I added mythvideo but I can't find my movies. I defined the correct library in the setup but still nothing.
2. I use an external EPG grabber and I don't now how to load it to the new database (using same command yileds nothing).
3. in mythweb I get this error message: "data directory is not writable by www-data. Please check permissions."

I know thats many questions but I can really use some help.
thank you.

---

### Post by orduek on 2009-10-20
OK, I think I solved everything here.
1. In order to find my movies I just pressed the menu button and told him to look for new files.
2. The EPG was solved by entering the name of the channel according to the xml file.
3. mythweb - changed the permission in /var/mythtv/mythweb/data
(something like chmod a+rw /var/mythtv/mythweb/data)

I still having problems gathering metadata. It should be as easy as XBMC but Mythtv is still far away in this area.

---

### Post by Johan73 on 2009-11-14
Thanks for sharing the solutions to your problems with the upgrade.  

I had the same problems with mythweb and managed to solve it following your instructions. One difference though, on my mythbuntu 9.10 installation, the relevant directory to change persmissions on is* /usr/share/mythtv/mythweb/data*.

---

