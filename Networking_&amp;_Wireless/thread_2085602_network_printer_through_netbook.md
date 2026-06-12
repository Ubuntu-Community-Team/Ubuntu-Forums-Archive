---
title: "network printer through netbook"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by arjepsen on 2012-11-18
Hey.

I have just recently got a used network printer from my school (an old hp 3600n), which has a network card. great.
But I can't place it close to my wireless router - and running a cable a long way through the house is not an option - so I have a bit of difficulty connecting to the printer.

Now I also have some old Lenovo ideapad s10e netbooks, and I wondered about if it was possible somehow to set up the netbook as a kind of transparent bridge between the printer and the wireless network?
Is there an easy way to do this?

Regards.
Anders

---

### Post by ahallubuntu on 2012-11-18
Does the printer have a USB port?  A parallel port?  If USB, just plug it into one of the netbooks.  If parallel only, you can get a parallel to USB adapter and use that to connect to the netbook.  I assume the netbook has at least one USB port.

Anyway connect the printer directly to the netbook.  I assume there is an operating system already installed on the netbook.  (If not, install one of course.)  Connect the netbook to your wireless network.  Then - share the  printer over the network.  Since I don't know what operating system is installed on the netbook, I can't give you exact instructions on how to share.  In Ubuntu, it's pretty easy to share a printer over a network.

Another option, if you have a spare router that is DD-WRT compatible, is to use the router as a wireless bridge (or "Client Bridge").  You can set this up with DD-WRT.  See if you can find an old G router like a Linksys WRT54G - these are reliable routers that are DD-WRT compatible and can often be had cheaply.

If you can get the DD-WRT client bridge working, then you can simply connect the printer to one of that router's LAN ports and it will be on your primary network, as if it were wired.

---

