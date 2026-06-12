---
title: "Lost internet connection after router flashing"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by kartal on 2009-10-27
Hi

I just flashed my linksys 150n with dd-wrt. I have 4comps on my network 3 of them works fine with the new flashed bios. I have no connection problem at all with wired connections(all 3 are windows) but my Ubuntu laptop has stopped connecting outside internet. The Ubuntu box can connect to other computers, it can see the shared drives(samba) etc. But I cannot make it to connect to internet. It was working just fine all this time. It just has stopped working after flashing my router. I can ping my internel windows boxes but pinging any outside ip just fails with "unreachable" message. 

This ubuntu box has(had) static ip,and below is the network interfaces file
"
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.2.102
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255	
	gateway 192.168.2.1
"

I had restarted it since then and that has not resolved anything. I ahve tried enabling and disabling Gufw, it did not result in success. So I guess I really need some pro insight into this matter.

thanks

---

### Post by jualin on 2009-10-27
You probably lost the static ip setting on your router when you flashed your router. Try accessing your router's web based setup utility (192.168.1.1 or 192.168.2.1 most of the time). And check that the options haven't changed in the router after the flashing. Just an idea. Hope this helps!


*** EDIT: It seems like the router's ip address is 192.168.2.1 
Go to your browser and enter that IP Address.

---

### Post by kartal on 2009-10-27
jualin,

Thanks for your reply. I forgot to mention that all my computers use static ip and they have no problem connecting internet, eachother or the router. My ubuntu also has no problem accessign the router admin page. So internally everything is working as expected. It is just that the ubuntu box does not want to open up to internet.

I am also not sure if flashing has anything to do with it. they might be irrelevant to eachother.

---

### Post by jualin on 2009-10-27
My next try would be to do a "hard reset" on the router, I have had similar internet issues and reseting the router solved them.
You could also check if the problem is within Ubuntu by trying to connect to the internet using Windows on the same computer (If you have it installed). 
Also have you done any updates since the last time that you were able to connect to the internet using the Ubuntu Laptop?
Just a shot on the dark.

---

### Post by kartal on 2009-10-27
I have wireless on the laptop as well, and if I enable it, I can get decent wireless connection that also can connect to internet. So the machine itself has no problem  with connecting internet with wireless, but I do not use wireless because it is too slow for my needs. I need the wired lan pretty much which was working fine until couple hours ago. 

I will try your testing the lan under Xp suggestion.

---

### Post by jualin on 2009-10-27
Ok, keep us posted.

---

### Post by kartal on 2009-10-28
Well,

It turns out that the network manager wiped out my nameserver config file (resolv.conf under etc). I have found out this incident accidentally. Putting the routers ip adress in there seems to fix it for now.

As far as I can tell the network manager never enjoyed the fact that some people just like to use static ips in their networks. I remember having massive issues and wasting hours while I was trying to set static Ip last year as well. It looks like the NM is little better now. I wonder if it is possible to totally disable this evil thin g without messing up my network settings.

---

### Post by jualin on 2009-10-28
I am glad that everything worked out. You can maybe try using Wicd, it is used mostly for wireless access but it works just fine as an alternative for the Gnome Network Manager. Wicd is on the repos so you can just install it using Synaptic or using the command line by the usual command > sudo apt-get install wicd If you don't like it just remove the package and GNM should come back to normal. Good luck!

---

### Post by kartal on 2009-10-28
Thanks
I will give it a try. I appreciate your help here.

---

### Post by jualin on 2009-10-28
No problem. Let us know how it went

---

