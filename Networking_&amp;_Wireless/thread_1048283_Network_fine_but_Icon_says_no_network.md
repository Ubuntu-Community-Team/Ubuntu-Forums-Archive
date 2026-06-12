---
title: "Network fine but Icon says no network"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by Trekrider58 on 2009-01-23
I have just upgraded from Hardy to Intrepid and everything seems fine except:

One confusing thing - my Network Icon now has a cross against it and if I right click on it and click on 'Connection Information' I get the error message 'No valid active connections found!'. Obviously there is a connection as I'm using it for email, web browsing etc. If I left click on the Network Icon 'Wired Network' is greyed out plus if I open 'Network Connections' my home network under 'Wired' shows as never.

My home network is manually configured with a static IP address but this is the same as when running under Hardy.

Any suggestions on how to get the network connection to show?

Thanks

---

### Post by Iowan on 2009-01-23
Just a guess... Because Network Manager is not controlling the static address, it thinks there is no connection???

---

### Post by Trekrider58 on 2009-01-23
> **Iowan said:**
> Just a guess... Because Network Manager is not controlling the static address, it thinks there is no connection???

Thanks, I could believe that except that under Hardy it showed the connection - having upgraded to Intrepid it doesn't.

---

### Post by Iowan on 2009-01-23
Network Manager changed... well, after Gutsy.  I *thought* the significant change was between Hardy and Intrepid.  IIRC, NM in Hardy still used /etc/network/interfaces file. I'm not really sure *where* Intrepid's NM keeps/gets it's configuration.

---

### Post by Loosewheel on 2009-01-24
I think Iowan is correct. They changed things with Ubuntu-8.10/NM-0.7. And NM is not managing the connection.
But if you have a network connection, something had to configure the interface.
I'd like to suggest that maybe the upgrade didn't go according to plan. And there is a possibility 'network-admin' configured the iface in the previous 8.04 install, and there are still entries in the '/etc/network/interfaces' file. But NM will not manage anything that is listed in the 'interfaces' file....and 8.10 does not install 'network-admin' by default. (Like it use to in 8.04).
So....make sure eth0 isn't in 'interfaces'. Comment it out if it is. Then reboot. It should come up.....maybe dhcp, but you can reconfigure with the 'nm-applett'.

---

### Post by Trekrider58 on 2009-01-24
Here are the contents of the interfaces file:

auto lo
iface lo inet loopback


iface eth0 inet static
address X.X.X.X
netmask X.X.X.X
gateway X.X.X.X

auto eth0

I assume you are saying to comment out the last 5 lines? How do I edit and save? I've got it open with 'gedit' but if I try to save the file I get an error message to say I don't have the permission necessary to save the file.

---

### Post by Loosewheel on 2009-01-24
> **Trekrider58 said:**
> Here are the contents of the interfaces file:

auto lo
iface lo inet loopback


iface eth0 inet static
address X.X.X.X
netmask X.X.X.X
gateway X.X.X.X

auto eth0

I assume you are saying to comment out the last 5 lines? How do I edit and save? I've got it open with 'gedit' but if I try to save the file I get an error message to say I don't have the permission necessary to save the file.


Trekrider58,
'sudo nano /etc/network/interfaces' and 'your passwd' will open the file for editting. Put a '#' infront of those 5 lines. Then 'ctl-o' to write, and 'Enter' to save to '.../interfaces', and 'ctl-x' to close nano. (The key commands are listed at the bottom of file).
You could try, '/etc/init.d/networking restart', and see if NM grabs it....I think a reboot is needed though.

---

### Post by Trekrider58 on 2009-01-24
Thanks Loosewheel, problem solved :D

It did take a reboot and then came up with auto IP but I was able to switch over to my static IP with no problems.

---

### Post by Loosewheel on 2009-01-24
You're welcome Trekrider58

Probably should mark this as solved.

---

### Post by Trekrider58 on 2009-01-24
OK - new to the forum - how do I mark as solved?

---

### Post by Iowan on 2009-01-24
Well... 
right now - no can do.  That option was suspended (along with option to thank helpful posts) a couple of weeks ago when forums were having stability problems.  If you look around the forum, you'll notice some (older) threads with [SOLVED] as a title prefix.
If/when the option returns, it'll be available under Thread Tools (near the top post on the page). I notice there is a **solved** tag available.

---

