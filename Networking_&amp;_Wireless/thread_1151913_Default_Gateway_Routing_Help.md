---
title: "Default Gateway Routing Help"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by camerooney81 on 2009-05-07
Hi Guys,

For some strange reason my Ubuntu 8.10 box stopped working this arvo. Haven't done anything drastic to it, apart from running some updates last night via update manager. But it was all ok this morning after I rebooted with the updates.

Basically I can't get to my default gateway. If I ping 192.168.0.1 I get "destination host unreachable"

My /etc/network/interfaces is:

"auto eth0
iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1"

I've tried both network manager and wicd. Both get an IP fine, but I believe its a routing issue. My routing table is:

cam@ubuntuserver:- $ route
Kernel IP routing table

Destination    Gateway     Genmask
192.168.0.0      *          255.255.255.0
link-local       *          255.255.0.0
default          192.168.0.1         0.0.0.0

Should the genmask for 'default' be 192.168.0.1?
Or the gateway for 192.168.0.0 be 192.168.0.1?

If so could someone link me to a guide on deleting/adding the necessary routes etc to get it working I'd be most appreciative. 

Or let me know if its not a routing issue and something else.

I've googled for a few hours and tried a few suggestions from various threads on here like 
[http://ubuntuforums.org/showthread.php?t=817685](http://ubuntuforums.org/showthread.php?t=817685)

But none have worked.

Any advice would be greatly appreciated. 
I'm a bit tired at the moment, but I'll try and get proper screenshots up of the route table in the morning so its easier to see what I'm on about!

Thanks in advance,
Cam

---

### Post by camerooney81 on 2009-05-07
I'm starting to think it might not be a route, as a unix box at work has the same entries (different IP, but same layout)

Are there any commands to completely reset network settings?
Is 'sudo apt-get remove network-manager' the only one?

I'm hoping there is something I can run so I can start everything from scratch. Like reset routing table and any network related configurations.

Otherwise I might try and update the machine to 9.04 and see what happens.
:)

Cam

---

### Post by camerooney81 on 2009-05-08
Can't believe what it turned out to be....
Dodgy network cable!!!

Swapped and now its working faster than it ever has.
Doh! Simple solution > advanced troubleshooting...lol
:P

Cheers,
Cam

---

### Post by hannuh on 2009-05-08
I switched to wicd because the Ubuntu network manager still does not allow you to put static IP settings including gateway permanently in the settings.
wicd worked for two days, then produced the same problem as you are describing.
I uninstalled wicd, configured /etc/network/interfaces manually and restarted the interface /etc/init.d/networking restart
Now the interface is reliable again, but of course I have no X based network manager whatsoever.
This was already a problem in 8.10, lots of people complained about it but the poor Network Manager is still unchanged.
This makes Ubuntu useless for jobs where you need to i.e configure and test equipment and change the eth0 IP all the time. It makes it unreliable for any kind of server purposes.
Use Mandriva or SuSe instead, they have professional quality network managers.
Hannu

---

