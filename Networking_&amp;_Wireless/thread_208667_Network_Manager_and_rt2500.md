---
title: "Network Manager and rt2500"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by crispy_420 on 2006-07-03
This is an on going problem for me. I had such high expectations for Network Manager in Dapper. But for some reason I can't get it to work. Everything I have tried has killed my wireless. So as of right now I am not using it. Just wondering if anyone has gotten it to work with this wireless chipset? If anyone knows of a good, could you direct me to it?

Also I just purchased an external card to try. I went with a Netgear WG511T and picked the matching router (WG611T). This will supposedly give 108MBS. Will this work with network manager? I believe it uses the madwifi drivers.

---

### Post by queenorych on 2006-07-04
The network manager included in dapper doesn't appear to work with the rt2500 driver.  Neither does wpasupplicant.

The rt2x00 driver should fix these issues, but is still in beta.  I don't expect to see a network manager patch, or the rt2500 fixed.  The rt2x00 will fix all of these issues.

On the plus side, just add ra0 to your /etc/network/interfaces and you've got a very good network connection.  Hibernate and everything works great on my dell.

My suggestion is to get comfertable with iwlist and iwconfig.  Then everything is easy.  Heck I'm at panera now, just booted up and started surfing.

---

### Post by vbatts on 2006-07-14
network-manager and the rt2500 are not compatible right now
something to do with dual WEP/WPA support

but the rt2500 supposedly the recommended wifi chipset of ubuntu

and for an easy app that can show you the list of availible networks and switch easily, 
sudo apt-get install wlassistant
it installs to Applications -> Internet -> Wireless Assistant
the only extra thing i did was edited the menu entry to add gksudo to the launcher.


vb

---

### Post by crispy_420 on 2006-07-15
I ended up with a Netgear wirless card. So until ra0 is supported by network manager, I'll be using an external card.

And it does work right away (rt2500). I just wanted to use network manager. But I'll have those plans on hold for now.

---

