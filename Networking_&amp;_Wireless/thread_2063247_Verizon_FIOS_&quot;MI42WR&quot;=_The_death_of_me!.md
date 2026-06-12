---
title: "Verizon FIOS &quot;MI42WR&quot;= The death of me!"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by HarleyUSMC on 2012-09-26
Brand new to the forums, thank god I joined I learned a lot of helpful little things searching and such but nothing on my current situation I mean not one thread or post relating to my problem.. here it goes, I'm running ubuntu 10.04 at the moment just formatted my entire computer to see if it would help, it didnt. Not sure of my ethernet card but I just switched from "IO Cable" to "Verizon Fios" I'm in NJ and my laptop works flawlessly and much fast running Ubunut via wireless but I cant connect via ethernet cable for the life of me! not on my laptop or desktop. the desktop I built 2 years ago from misc parts at a computer show. I've tried everything I could and not to drag this out, but any and all help would be super appreciated!

Router is an Actiontex MI424WR

---

### Post by SeijiSensei on 2012-09-26
First, make sure you are actually using an Ethernet cable and not an Ethernet "crossover" cable.  The latter is designed to connect machines together directly and has the wrong electrical wiring for a regular Ethernet connection.

Next, are the connection lights lit up on both ends of the connection?  If not, you have an wiring problem of some kind.  It could be a bad Ethernet card.  I have a VZ router that works just fine with Ethernet connections.  

My router has a coaxial cable connection to the FiOS interface, a "WAN" port, and four "LAN" ports.  Make sure you are connected to one of the LAN ports.  The WAN port is used to connect the outbound side of the router to the Internet in place of the coaxial connection.

Also, try using Network Manager to disable the wifi connection and force an Ethernet connection instead.  Does that help?

---

