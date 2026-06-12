---
title: "netowrk offline, backend goes down."
date: 2010-08-08
forum: Mythbuntu
---

### Post by Mad_Professor on 2010-08-08
My modem died last night, and in my attempt to bring my network back online I had to reset some switches. The backend/frontend relies on 192.168.0.123 address for it's database which is local to itself. I have another frontend across the network that relies on that ip as well, but it easy enough to restart the frontend. The problem I have is when the backend goes down, it doesn't restart and I don't know how to restart it, or how to restart all plugins like mythweb. I end up having to reboot the whole machine. It also miss recordings because backend went down due to a network problem.

So I was wondering if I can do a host file on the backend that takes 192.168.0.123 address and have it point back at itself when the network goes down, or something similar. That way the backend doesn't crash.

Any ideas?

---

### Post by nickrout on 2010-08-09
Why are you taking your backend offline? 

Anyway to resstart mythbackend (and you possibly might need to restart mysql) you need to:

sudo service mythtv-backend restart

substitute whatever service you want to restart for mythtv-backend

---

### Post by LowSky on 2010-08-09
I label my backend as localhost.

all my frontends point to its real address, for example 192.168.0.201

Its also a smart idea to use a router between your machines and the modem. That way if you lose interent the LAN will keep things from going to hell in a handbasket. If you can give the backend a locked address, that way if the Router goes down, when it comes back up it wil give the backend the same address.

---

### Post by mdaitc on 2010-08-09
If you rely on your backend getting an IP address automatically, and the DHCP server goes away, then you'll most likely lose connectivity.

If you can, give yourself a static (fixed) 192.168.x.x IP address, and that way, if the DHCP server stops handing out addresses, then your backend will at least continue to work - remember your front-end will also need an IP address.

---

### Post by Mad_Professor on 2010-08-09
Thanks you all, so basically the backend should be set up to point to 127.0.0.1 then all frontends point to the real IP? Makes sense. I'll give it a shot.

Edit: that didn't work the other frontend across the network didn't see it. Worked great for backend/forntend but not the second frontend.


@nickrout
I didn't do it on purpose. When the modem died, I setup my laptop to steal wifi from a neighbor and pipe it through the gigabit back into the wan port of my pfsense box to give me temporary internet access during the downtime *It was a weekend and my day off and STARCRAFT 2 was out and you need net access* until I replaced my modem. But I had some problems, made a backup of configuration and messed with the setting to get it to play nice. Once I got a new modem, I restored the old configuration which causes the machine to restart, thus losing dhcp. I unplugged the switch to re-lease all the machines on the network. My mythboxes and fileserver are assigned static IP's but are not set locally.

---

### Post by LowSky on 2010-08-09
Where did you get 127.0.0.1 from? set it to just say _**localhost**_ 
MythTV wil then "fill in the blanks"

Your backend should use the PC's LAN address, which unless you have some screwy network will start look like 192.168.0.1

the fronntends can have any local address they want, just make sure they have the correct mythtv user name and password to work

I love how people admit to illegal activities on the internet as if they were anonymous.

I'm not really sure of your network setup, but you should ever have had to take down the network when the Modem died, unless the modem was also a router. Which would then explain this mess.

---

### Post by Mad_Professor on 2010-08-09
**** it...

---

