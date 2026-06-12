---
title: "Print to Canon MP780 on Apple Time Capsule"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by TMinski on 2010-01-10
Ubuntu 9.10 Karmic Koala, Apple Time Capsule with USB printer (Canon Pixma MP780 in this example)  I've got something to share after setting up printing for our notebooks (MacBook Pro with OS X Snow Leopard and Windows XP in Sun's VirtualBox and Dell D610 dual-booting Ubuntu 9.10 and Windows XP) to print to our printer.  I couldn't find this sort of specific arrangement noted in the Ubuntu forums, but picked up on some clues after getting it working in Mac and Win environments.  Apple provides an open source zero configuration utility called Bonjour. This is a great tool for MacOS and Windows to discover devices on your local network and use them without messing about in the configuration settings.  Someone on the Ubuntu forums clued me in to a zeroconf tool named Avahi that acts like Bonjour and may be based on the same code - I haven't looked.  The following procedure “just worked” without having to learn anything about linux command console commands, typing “sudo”, or getting off of the couch (well, except to go see if the test print worked).  So, try this:  
[LIST=1]
[*]Install Avahi on Ubuntu:  Applications > Ubuntu Software Center > Search “Avahi Zeroconf” > select “Avahi Zeroconf Browser” > click the arrow to the right > Install
[*]Fire up Avahi, explore the network to confirm that it can see your printer plugged into the USB port on your Time Capsule:  Applications > System Tools > Avahi Zeroconf Browser > you should see an entry for your Time Capsule and another one for your printer.  My printer was listed as PDL Printer, Canon MP780.  OK, cool, that's it.  You're just confirming that it's listed.  If not, then you'll have to sort that out before proceeding.
[*]Now setup your printer:  System > Administration > Printing > New > wait while it searches, then expand the Network entry (little right arrow button thang to the left of “Network”) > click to select your printer entry > Forward > wait while Ubuntu hunts down an appropriate driver (with luck, it will find one) > go through sequence to identify your driver > give it a name you like > Apply > print the test page > (woohoo) > then right-click your printer and set it to default.
[/LIST]
 Good luck, it worked straight up for me without any troubleshooting so I don't know much more.  Completion time was way faster than it took for me to type this up.

---

### Post by jondodson on 2011-05-30
This worked for me, thanks.  I'm using a Samsung ML-1510 printer and Lucid 10.4 and the process described above still applies (I know I shouldn't really be exhuming 18 month old threads...)

---

