---
title: "Vanilla MythBuntu expanded to multi Frontends"
date: 2013-03-27
forum: Mythbuntu
---

### Post by gga96 on 2013-03-27
I have installed a vanilla MythBuntu system with back and frontends on the 
same “backend” machine.
The system is working very well.

 I now attempting to expand the system to multi-frontends.
When I install MythBuntu as a frontend on the “frontend” machine it will 
not connect to the “backend”.
Googling has found many suggestions but I could not find a definitive step 
by step procedure, I only got more and more confused.
I have implemented some of the advice but never succeeded to establish a 
connection but have had to reinstall the ‘backend” several times.

The router appears to recognize each machine on the network.
My router is a NetGear N150 (DHCP) and lists the following:
Router:      192.168.1.1 
Win 7 PC: 192.168.1.2
“backend”: 192.168.1.3 
“frontend”: 192.168.1.4

Can a guru please help.

---

### Post by AlecJ on 2013-03-28
Set your backend to a static IP address, in your case 192.168.1.3

In the Backend set up set the IP address of the machine it's running on 192.168.1.3 in your case and also set a pin code while your their.

using "Mythbuntu control centre" find it in the system menu

go to the MySQL menu and Enable Master backend role.

Also enable the services like VNC NFS etc

When you boot the remote front end it should find the backend and ask for your pin code
You may need to enter the MySQL password?  you can find this in the general set-up of the frontend thats on the backend machine, it's a long number and case sensitive 

Thats normally it

I have a few remote front ends, remember you can not stream HD

---

### Post by gga96 on 2013-03-28
Thank you Alec.
> Set your backend to a static IP address, in your case 192.168.1.3
I believe my router is DHCP and is showing a dynamic IP address NOT a static addess. 
I have tried using 192.168.1.3 in the backup setup for both "Local Backend IP Address" and "Master Backemd IP Address" and when I restarted the system, the frontend had lost all the previous setup data. There could have been previous corruption or the IP addresses should have been static. I could not recover so I have reinstalled the system.
Could you please confirm the use of 192.168.1.3 before I go ahead or tell me how to create static IPs.

The other instructions have been done.
> go to the MySQL menu and Enable Master backend role.
Enabled master backend role. Set security code. Test connection passed.
> Also enable the services like VNC NFS etc
All services are now enabled. Applying changes finished without error.

I will now wait before proceding further.

---

### Post by gga96 on 2013-03-28
Sorry I got confused, perhaps DHCP should have read DNS.

---

### Post by klc5555 on 2013-03-28
> **AlecJ said:**
> 

...

I have a few remote front ends, remember you can not stream HD

Sure you can. All you need is frontend hardware with reasonable CPU horsepower, NVIDIA graphics,  and fast enough networking from the backend --preferably fast ethernet. I didn't put local frontends on any of my three backends --all of my frontends therefore are remote, and are connected to the backend network by fast ethernet (a couple of laptops by N-wireless) No difficulty watching HD live tv from any of the frontends. Even the laptops. Since my backends never use a local frontend, they can be (and are) run on 8-10 year-old junk hardware that couldn't possibly display HD locally.

---

### Post by AlecJ on 2013-03-28
> **klc5555 said:**
> Sure you can. All you need is frontend hardware with reasonable CPU horsepower, NVIDIA graphics,  and fast enough networking from the backend --preferably fast ethernet. I didn't put local frontends on any of my three backends --all of my frontends therefore are remote, and are connected to the backend network by fast ethernet (a couple of laptops by N-wireless) No difficulty watching HD live tv from any of the frontends. Even the laptops. Since my backends never use a local frontend, they can be (and are) run on 8-10 year-old junk hardware that couldn't possibly display HD locally.

umm
Maybe something I have to look in to, but my old IBM coppermine laptop just freezes on BBC one HD, takes ages to be able to change the channel to normal BBC one.

---

### Post by AlecJ on 2013-03-28
> **gga96 said:**
> Sorry I got confused, perhaps DHCP should have read DNS.

your router set to DHCP gives a free IP address to each computer or device as and when it comes on line even mobile phones, this is not a lot of good if that computer is a media server that all the other computers get media from and it's IP has been given to another by the router.


So you need to set it static
I do this manually but you can do it however you like.

first backup /etc/network/interfaces then edit it
in a terminal on your myth box

```
sudo cp /etc/network/interfaces /etc/network/interfaces_old

sudo nano /etc/network/interfaces
```

you should see
```
auto lo
iface lo inet loopback
```

change it to look like this

```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.3
gateway 192.168.1.1
netmask 255.255.255.0
```

next if you want the internet on this you have to edit resolv.conf

```
sudo nano /etc/resolv.conf
```

it may well be empty but add this line

```
nameserver 192.168.1.1
```

so the DNS is now your router

after a reboot it should be fixed at 192.168.1.3 and have internet access.

---

### Post by AlecJ on 2013-03-28
> **gga96 said:**
> 
Could you please confirm the use of 192.168.1.3 


you can have any number as long as you stick with it, I use 192.168.1.4 just because when I first started with this myth thing that was the first address free.

this must be entered in the Backend General set up, so everything knows where it is on the network.

Don't worry about the Local Frontend settings, just the backend as the remote frontends need to see it over the network

---

### Post by tgm4883 on 2013-03-28
> **AlecJ said:**
> umm
Maybe something I have to look in to, but my old IBM **coppermine** laptop just freezes on BBC one HD, takes ages to be able to change the channel to normal BBC one.

That would be correct, a Pentium 3 cannot play HD content. Honestly I wouldn't have even tried that. You should at least check the recommended system requirements [http://www.mythbuntu.org/support](http://www.mythbuntu.org/support)

---

### Post by AlecJ on 2013-03-28
> **tgm4883 said:**
> That would be correct, a Pentium 3 cannot play HD content. Honestly I wouldn't have even tried that. You should at least check the recommended system requirements [http://www.mythbuntu.org/support](http://www.mythbuntu.org/support)

LOL it's been a remote frontend since 8.04-ish, not my fault the world left it behind. Still works on 12.04.2
It does have a 8Gb CF card for a hard drive and old HIFI amp and speakers.

I'm in no hurry to replace it, it lives in the Kitchen and is now quite grubby. I'm amazed just how much water and mess it has put up with

---

### Post by PhilWig on 2013-03-28
Should there be anything extra to the above for a ‘Live CD’ setup?

I have my backend running 64 bit 12.04 with the settings as suggested by AlecJ (except IP address is a fixed DHCP allocated one).  It will support Mythtv player.

32 bit 12.04 live CD fails on two different systems during ‘Try Mythbuntu’.    Testing connection is successful but on requesting it to start frontend I get nothing.  If I start mythbuntu-startup from command prompt it does the same but gives a warning on starting frontend that the logfile parameter is no longer supported in 0.25.
If I start the frontend manually (with logpath) , it complains that I need to be member of mythtv group and need sudo privileges.  It won’t even give help text!
Oddly, a ‘ps aux’ shows tasks running for users with name 999.

64 bit 12.04 on a modern netbook gives same symptoms but with an extra twist – an internal Ubuntu error which cannot be reported because updates are needed.

Phil

---

### Post by gga96 on 2013-03-28
Thank you very much Alec for taking the time and effort to share your knowledge and help me, all is now working.

[B]I think your clear and detailed step by step instructions should be nailed to the mast for all to see.
[/B]
This procedure is a natural progression from MythBuntu installation on one machine, to a network of frontends.
I am sure it will help others too.

I have spent days fumbling about with snippets of information that never led to a rational result.

PS: Pleased to hear your kitchen frontend still enjoys a good life!

---

### Post by AlecJ on 2013-03-29
No problem, glad to be able to help.

I've not managed to get the Live CD working either, normally complains about the database's not matching.
I did get a USB live CD working after adding the PPA and updating, turned out too slow in the end. But we have USB 2 and 3 now so?

---

