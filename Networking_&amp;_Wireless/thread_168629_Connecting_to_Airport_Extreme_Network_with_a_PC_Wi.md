---
title: "Connecting to Airport Extreme Network with a PC Wireless Card"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by obama on 2006-04-30
Hey there everyone.  I'm about to buy a new computer (my first i386) and I live in a house of Mac users with an Airport Extreme wireless network.  I know there have been issues with Airport and Linux, but I also know that some solutions have been made.  Is it possible to join an Airport Extreme network with 6.06?  If not, can I make it possible?  Thanks much.

---

### Post by obama on 2006-05-01
Hi, I'm getting the computer today, and any advice on this would be awesome.

---

### Post by giaguara on 2006-05-06
Same problem.

Dell Inspiron 9300, whatever wireless card it came with.
AirPort network - has AirMac Extreme and a few AirPort Express BS around the house. MAC access control on, and the Dell MAC address is on the access control list of allowed devices. AP is set to work in 802.11b/g mode.

I can't get the eth1 interface get activated. It gets on from the Kubuntu control panels for 1 second, then is disabled again. 

So far I can get it online (Mac's System Preferences > Sharing > Internet > over ethernet, from airport) using an ethernet cable, but I want to eliminate the cables and use the thing wirelessly.

---

### Post by nolongerlivecd on 2006-05-06
Giaguara - Wireless driver not set up. Boot into Windows to see what card, or iwconfig

Obama - Get a MacBook Pro

---

### Post by timmah on 2006-08-27
not sure if it makes a diff....i've got an airport express and a dell laptop w/wireless card.

is there a place to find drivers to get it to work anyone could direct me too?
and
would i then install the airport express software?
and
would i use the add/remove app to do the install?

the new 6.6 works perfect with the cable....but i gotta lose the cable.

thanks huge for any help as i haven't any luck narrowing down what to do first.
timmah

---

### Post by bxa on 2006-12-12
i'm having the same issues.
was anyone able to resolve it?

---

### Post by bxa on 2006-12-13
my email is:
bleedapathy at gmail dot com
email me when someone has a resolution

---

### Post by bakelitedoorbell on 2007-12-29
I was having trouble with my Mac network, but figured it out.  I have an Airport Express connected to a cable modem, which was working great with my Macbook.  I could not connect with my Ubuntu Thinkpad using a wireless PCMCIA card.  I could see the name of the network in System/Admin/Network, but I couldn't figure out how to connect to it.  Even removed the password and made it an open network, but no luck.

It turns out it wasn't an Ubuntu problem - I did not have the base station configured correctly.  It had been set up with a single IP address, which was being used by the Macbook.  I changed the Airport Admin settings using the Macbook so the base station would share IP's with more than one computer, and then the Thinkpad connected wirelessly no problem.  I can go into detail on the settings if needed.

---

