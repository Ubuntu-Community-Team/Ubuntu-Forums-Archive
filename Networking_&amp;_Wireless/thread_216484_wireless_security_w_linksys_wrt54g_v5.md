---
title: "wireless security w/ linksys wrt54g v5"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by fhqwhgads on 2006-07-15
I have been googling and searching forums for a while now. I need some help getting a secure wireless connection going under Ubuntu Dapper (386 kernel). I have an ASUS z71v notebook (with intel wireless) and a Linksys WRT54g v5 wireless router. The linksys is in bridge mode with my dsl modem (speedstream 5100). I have had a wired WinXP PC set up for a while now, with a static IP, and port forwarding, and a dynDNS client running on the router. Everything works fine there. 

On the ubuntu notebook, everything is fine if I have wireless security disabled and DHCP enabled. I'm having quite a hard time getting a connection working with either a static IP or WEP. What I'm trying to accomplish is both of those. To complicate things, I also take my notebook to work, so help that involves the settings in a network manager like Wi-fi Radar would be the most helpful.

Currently, the WinXP box is assigned 192.168.1.100, and the DHCP pool begins at *.101

Please help me with the best security settings (that will work in ubuntu) in the wireless page of the router's webadmin, and help me set up the profile correctly on my notebook. I'm pretty good with wired networking but this wireless stuff has me pulling out my hair! Thanks for reading!

---

### Post by fhqwhgads on 2006-07-15
Okay, I think I have it figured out now. In case anybody else finds this in a forum search, here's what I did.

I found some useful documentation here: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

I grabbed the *network-manager-gnome* package trough synaptic. In the Linksys webadmin page, under *Wireless* -> *Security* I enabled WPA Personal & TKIP. On the laptop I set up the network manager (through the systray or whatever you call it in gnome) to refelect sthe settings and passphrase. 

Seems to work after restarting the router and computer. Now all that's left to do is set up port forwarding.

---

### Post by fhqwhgads on 2006-07-15
I guess I spoke to soon. It's working great with DHCP, but I can't figure out how to get *network-manager-gnome* to use a static IP. :-k 

If anyone has an idea, I'm all ears.

---

### Post by shortbus on 2006-07-16
Not sure how much this will help, but here is what i recommend, not sure if you've tried it yet or not either..

Goto *system->Administrator->Networking* under that click on your *wlan0*(or whatever your's is) then *properties* Make sure your connected to the right ESSID, change the drop down to from DHCP to Static IP. Enter your infomartion for IP, subnetmask and default Gateway. I've had some success with this. Let me know how it goes.

P.S. there is always the *threaten it till it works method* but that seems to work best with Windows.

](*,)

---

