---
title: "Firefly Mini Remote - need assistance setting it up!"
date: 2008-03-15
forum: Mythbuntu
---

### Post by cjtinant on 2008-03-15
Have issues with my Firefly Mini Remote. The machine I am running this on is a Frontend and will not have a keyboard connected. That being said, I need some buttons working that currently are not (exit, ect...) I now find there are two options to get the "missing" keys to work; update the Kernal or setup a work-arround solution. Neither of which I can figure out HOW to do... Some help would be nice as I am at an end point!

I am sourcing this document;
[http://www.mythtv.org/wiki/index.php...m_firefly_mini]("http://www.mythtv.org/wiki/index.php...m_firefly_mini")

I modified the .lircrc and lircd.conf files to the settings at bottom of document. Most of the buttons will work, but find the LAST, EXIT, OPTION, and MENU buttons are not functional. 

Can someone walk me through this to get ALL buttons fuctional. Key Mapping instructions would be usefull (Setup / Remote Jump Point) Also, would like the "Firefly" button to be a jump point to the main menu. 

Thanks in advance!

---

### Post by nasha on 2008-03-16
For some reason the link you posted is broken, part of the URL has been replaced with ...

If your at the stage where you have the remote responding to keypresses in MythTV, then sorting out any buttons that don't work should be as simple as editing your lircrc...

Lircrc maps the buttons defined in the lircd.conf to keyboard shortcuts
Use irw to find the name of the buttons you wish to change, then edit your lircrc accordingly

---

