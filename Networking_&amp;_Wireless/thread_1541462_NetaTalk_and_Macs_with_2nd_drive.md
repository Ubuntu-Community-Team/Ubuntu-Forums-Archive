---
title: "NetaTalk and Macs with 2nd drive"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by jellygraphics on 2010-07-29
NetaTalk and Macs with 2nd drive
Hi there

Running Netatalk on Ubuntu 10.04.
Have Ubuntu installed on one HD = 160gb
have second HD (sata) 500gb HFS+ formatted


The idea being to have the OS running from the one drive, and the second drive as a file server that's accessed by three apple macs (10.5 x2 and 10.6 x1) via a 8 port switch.

I've set this up using NetaTalk and all seems well except I can't see the second (500GB) harddrive on my macs. I can see it in Ubuntu and have used Gparted to partition and format it.

I think I need to add lines to the Apple.Volumes default file but I can't for the life of me get to grips with how to go about doing this!!

the 500GB harddrive I want to be called "MacServer" but it's showing up in Ubuntu as unamed

On the mac all I can see is the home folder, but no other connected drives.

In the AppleVolumes default at the moment is this line:

#...loads of text all of which I think is instructional.
~/ 


This allows me to see home folder on my macs, but if I delete ~/ for example or try to put another path then I can't see anything! Mac fails to connect.

Please help!!

---

### Post by jellygraphics on 2010-07-30
Any thoughts guys - perhaps a suggestion of where else this could be posted?

Thanks!

---

### Post by wall_e on 2010-08-03
Did you use this page?

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

---

