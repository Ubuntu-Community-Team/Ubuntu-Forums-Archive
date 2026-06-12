---
title: "Wireless GUI Configurator"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by Elrohir on 2006-05-08
Is there any application that allows to change the configuration of the Wireless NIC (WNIC)? one that allows to change the way the WNIC connects to the network (toggle between AD-HOC and Infrastructure) and such... I know Mandriva has one... can't recall its name right now...

---

### Post by Dr. Nick on 2006-05-09
If  you are on gnome go to syste-administration-networking and you can make different "locations" or look at wifi-radar

---

### Post by Elrohir on 2006-05-09
already tried the System > Administration > Networking... not what I'm looking for... I'll check wifi-radar...

What I am searching for is one that can manage th different modes a WNIC can handle (Ad-Hoc, Managed, Repeater), because that's the thing I want to manage... I found 'iwconfig' but it seems not to work... or I am using it incorrectly... I'll figure that out tonight...

---

### Post by Dr. Nick on 2006-05-09
Their was another one that worked well to but I forgot its name, and since my laptop died I dont use wireless anymore so my once plentiful knowledge is fading :) Maybe ill plug my wireless into my desktop to get back into it lol. If i recall redhat made the one im thinking of, Im sure its mentioned on the forums somewhere

---

### Post by Elrohir on 2006-05-09
nah! dont worry... already make it work... w00t!

the thing was to configure the WNIC with all the paraeters with the iwconfig command...

here's what I did: ```
sudo iwconfig essid "Network Name" channel 6 mode Managed ap 00:13:10:35:12:70
```, with the System>Administration>Network all I did was to place it as DHCP and voila! connected...

---

### Post by Dr. Nick on 2006-05-09
Glad you got it, I pulled my usb wireless out for kicks and it was a heck of a lot easier to get going then it was just a few months ago. I wouldnt have know the iwconfig commands though, my wireless uses the wlan-ng drivers so you have to use their program to manage that stuff which is a bit different.

---

