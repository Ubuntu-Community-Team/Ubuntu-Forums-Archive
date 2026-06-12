---
title: "Lost connection to network printer-how to re-establish?"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by flyingsolo on 2010-11-09
I think I'm missing something simple.  I have had long term access to a networked HP Photosmart printer but now I get the following message:

Unable to open device hp:/net/Photosmart_C5100_series?ip=192.168.0.161.

when trying to access it.  The ubuntu desktop is wired to the router as is the printer and another iMac wirelessly can still print to the HP. HPLIP status shows the icon for the printer but with a red x indicating no connection to it.
The only recent network change was the removal of another router from our network.  (service is DSL via a combo modem/router from service provider which previously was connected to a Dlink router which has now been removed from the chain b/c was redundant to the modem/router)
Hopefully someone sees the light I can't!
thanks

---

### Post by Cheesehead on 2010-11-09
Well, let's try basics first.

Is the Mac printing according to IP, or is it recognizing it via Bonjour or another method? Macs tend to prefer to use Bonjour, when available. They have printing hiccups, too, but different and weirder hiccups.

A very common event upon changing network hardware is an unexpected change of IP: Does the printer really still have that IP assigned? Is that IP reserved for it on the new router? If you print a Network Configuration page (different for each printer - consult your manual), does the correct IP print out? Or does the printer have a built-in webserver, can you reach it at that IP address with a browser?

Have you updated your Ubuntu system since your last succesful print?

---

### Post by flyingsolo on 2010-11-09
Thanks for the reply. On the iMac, under Photosmart->Options & Supplies->Utility->Device Information, it shows the printer address as:
192.168.2.11
which is different than the address seen by the Ubuntu desktop which sees 192.168.0.161.
So that would seem to be the problem. I've been able to fix it by using the HPLIP interface and simply adding a new printer (even though the Photosmart identity with the wrong network address is already listed) and the system 'discovered' the printer and assigned it a new, correct network address.  I guess I was just expecting the system to 'refresh' the network address automatically which, clearly, it doesn't.
Anyway, thanks for the tip which led me to the solution!

---

### Post by Cheesehead on 2010-11-09
The key was in your old address: Unable to open device hp:/net/Photosmart_C5100_series?ip=192.168.0.161.

That's a machine looking for an IP, not scanning the network or listening for a signal.

Fixed IPs are nice, easy way get connected to hardware...until they stop being fixed.

(My router does 'reservations' for fixed IP devices on the network. When my printer joins the network, my router assigns it the same IP each time.)

---

