---
title: "Wirelessly connecting network printer"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by mb_webguy on 2009-04-08
This is a general networking question, and not specific to Linux, but this is the best place I know to go for info...

Is it possible to use a standard USB wireless adapter to connect a network printer to a wireless network?  I've never tried this before and I suspect it won't work, but I'd like to know for sure before I go buy anything.  

I've been asked to set up the network for a small business.  They're naturally trying to spend as little money as possible, but where they want their HP LaserJet 4000tn printer is in a different room from where the wireless router ideally needs to be for best coverage, and high ceilings and a carpet-over-concrete floor make running a network cable to the printer problematic.  I know I could use a wireless print server or a wireless bridge, but both of those are needlessly expensive solutions if a simple USB dongle will work.

---

### Post by BkkBonanza on 2009-04-08
If you mean a regular USB dongle that is used for connecting a computer to a wifi network then the answer is NO.

Your printer is a USB slave/client device that requires a master device (host) to communicate with. The dongles are also client devices. Clients don't talk to clients, they have to go through a master. Also you'd find the connectors are wrong.

To do what you want you need to either connect the printer to a computer that has wifi and configure printer sharing, or get a router/print share device that supports usb. Some of the higher model routers (like Linksys WRTSL54GS.) have usb ports (host type) and with correct firmware installed can be used for print sharing. 

See this page for more info on dd-wrt routers usb support,
[http://www.dd-wrt.com/wiki/index.php/USB](http://www.dd-wrt.com/wiki/index.php/USB)


You can also buy special little usb print sharing modules but they generally cost almost as much as a router and only work with wired ethernet.

---

### Post by mb_webguy on 2009-04-08
The HP LaserJet 4000tn is a network printer, designed to be connected directly to a router or switch via an Ethernet cable.  I've been setting up and administrating networks for years, and am quite familiar with network printers.   The printer acts as its own print server, so I don't really *need* one of those wireless print servers -- just some means of connecting the printer wirelessly to the rest of the network.  

Generally, since an office printer is rather large and unlikely to be moved, it's simple enough to run an Ethernet cable from the router or switch to the printer.  In this case, given that the client wants a primarily wireless network, the desired locations of the router and printer, and the construction of the building, that's not really feasible.

I figured that a simple USB wireless adapter wouldn't work (even with a USB A to USB B adapter), but if it *did* it would be a much cheaper alternative to the things I knew would.

---

### Post by BkkBonanza on 2009-04-09
A wifi usb dongle runs about $20. A Linksys WRT54GL router runs about $50 but gives you lots more flexibility. Stick the router on the printer via ethernet cable. Put dd-wrt into the router and set it for bridge mode, so that the lan on that router is an extension of the office wifi. The printer will be accessible from anywhere on the wireless lan, and via any wired connection to the router as well.

---

