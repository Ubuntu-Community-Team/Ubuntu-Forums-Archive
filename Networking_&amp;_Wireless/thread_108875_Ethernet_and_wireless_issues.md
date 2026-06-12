---
title: "Ethernet and wireless issues"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by Connollyir on 2005-12-27
I just recently went to war with a new media server trying to get it up and running wuthout a user interface. I finally got the operating system onthe disk, installed proftpd and gnump3d and updated all the packages. I set up the network so that it would have a static ip address so I could access the files and stream my music with those programs. Everything was good until I moved the box off the LAN it was on, onto the crossover cable that it was destined for and I ran into networking hell. I could connect to the server and transfer files, but only if my wireless card was disabled. :mad: 

With both enabled I can ping the box fine, and I get good responses, and I can also visit sites and such - up to a certain point when suddenly my internet goes down until I use <sudo /etc/init.d/networking restart> and everything comes back (minus full server connectivity of course).:confused:   

Does anyone know what is going on here? Because I would KILL to find out.

-Ian

---

### Post by Koybe on 2005-12-27
Could you post
```
route -n
```
once your wired + wireless networks are on?

[related topic](http://www.ubuntuforums.org/showthread.php?t=108693)

---

### Post by Connollyir on 2005-12-27
Typing in route -n gives me the following when both network cards are enabled, wireless with DHCP and the ethernet card with the static data.


e@IansDreamMachine:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
e@IansDreamMachine:~$

---

### Post by Lambert on 2005-12-27
See my post here.

[http://ubuntuforums.org/showpost.php?p=574204&postcount=2](http://ubuntuforums.org/showpost.php?p=574204&postcount=2)

the last two output lines in that command show you have two default gateways.

---

### Post by Connollyir on 2005-12-27
[QUOTE=Lambert]See my post here.

[http://ubuntuforums.org/showpost.php?p=574204&postcount=2](http://ubuntuforums.org/showpost.php?p=574204&postcount=2)

the last two output lines in that command show you have two default gateways.[/QUOTE]

Well good, we know what I've got. HOW  do I fix it? If you have the commands ready it would save time, which I've spent enough of on this problem already.

Thanks

-Ian

Note: I just went into the remote server's network/interfaces file and changed the "network" part to 192.168.0.2 and restarted the network, and then I changed the gateway value in the networking suite in kde on my desktop to match and I've still got the same issue.

---

### Post by Lambert on 2005-12-27
Which nic do you want to be your gateway to the internet? eth0 or ath0? as you can only have one.


What's the purpose of the wireless interface? Are you trying to stream via crossover cable and to other pcs via wireless?

trying to figure out what you're trying to accomplish with two active interfaces. One can be your gateway to the internet, the other connects just to your lan.

---

### Post by Connollyir on 2005-12-27
[QUOTE=Lambert]Which nic do you want to be your gateway to the internet? eth0 or ath0? as you can only have one.


What's the purpose of the wireless interface? Are you trying to stream via crossover cable and to other pcs via wireless?

trying to figure out what you're trying to accomplish with two active interfaces. One can be your gateway to the internet, the other connects just to your lan.[/QUOTE]

The purpose of the wireless interface, at least for the next 20 or so days, is to connect me to the internet - thats it. the SOLE purpose of the ethernet nic - eth0 - is to provide access to this server. When I get back to college I will replace the wireless card with another ethernet nic that will function as my internet connection again. So to answer more fully, right now I need ath0 to be my internet connection only and eth0 will be the only streaming connection to the server, via crossover cable.

Thanks

-Ian

---

### Post by Lambert on 2005-12-27
```
sudo route del default gw eth0
```

this will delete the gw setting for the eth0. 

```
sudo route del -net 192.168.0.0 netmask 255.255.255.0 dev ath0
```

this should leave you set up so anything being sent with a destination of 192.168.0 to your eth0 nic and anything else should go through your ath0 nic

---

### Post by Connollyir on 2005-12-27
Ok so I went into the /etc/network/interfaces file in the server again and took your advice that there can be ONLY one gateway and commented out the "network" part of the primary config just to see what would happen and BAM I got my internet back with both cards enabled. Sounds sweet BUT I still can't connect to the server on any level - I can ping it all day long and get a response but if i try to ssh into it (ssh-server is enabled on it - its how I installed all the packages) or run FTP at all I get :

[I]gFTP 2.0.18, Copyright (C) 1998-2003 Brian Masney <masneyb@gftp.org>. If you have any questions, comments, or suggestions about this program, please feel free to email them to me. You can always find out the latest news about gFTP from my website at [http://www.gftp.org/](http://www.gftp.org/)
gFTP comes with ABSOLUTELY NO WARRANTY; for details, see the COPYING file. This is free software, and you are welcome to redistribute it under certain conditions; for details, see the COPYING file
Looking up 192.168.0.10
Trying 192.168.0.10:21
Cannot connect to 192.168.0.10: Connection refused
Waiting 30 seconds until trying to connect again[/I]

Why?

---

### Post by Connollyir on 2005-12-27
[QUOTE=Lambert]```
sudo route del default gw eth0
```

this will delete the gw setting for the eth0. 

```
sudo route del -net 192.168.0.0 netmask 255.255.255.0 dev ath0
```

this should leave you set up so anything being sent with a destination of 192.168.0 to your eth0 nic and anything else should go through your ath0 nic[/QUOTE]

Wow I think you typed that just before I sent my post! I ran the commands anyway, however the first set didn't work:

[CENTER]e@IansDreamMachine:~$ sudo route del default gw eth0
eth0: Unknown host
[/CENTER]

although the second set did.

But it didn't solve my connectivity problem with the server...:???:

---

### Post by Lambert on 2005-12-27
command edit

sudo route del default gw dev eth0

---

### Post by Connollyir on 2005-12-27
[QUOTE=Lambert]command edit

sudo route del default gw dev eth0[/QUOTE]

e@IansDreamMachine:~$ command edit
e@IansDreamMachine:~$ sudo route del default gw dev eth0
dev: Unknown host
e@IansDreamMachine:~$

If we are in fact removing the gateway address for eth0, I just checked under network settings>eth0>interface properties and there is no longer a gateway address for that device. Is that what we are doing? And if so we have succeeded.:KS

---

### Post by Lambert on 2005-12-27
that's where I was heading, not sure if it's the solution but it was the first thing on my mind from what I saw in your posts.

when you run route -n all I want to see is

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0

---

### Post by Connollyir on 2005-12-27
[QUOTE=Lambert]that's where I was heading, not sure if it's the solution but it was the first thing on my mind from what I saw in your posts.

when you run route -n all I want to see is

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0[/QUOTE]

e@IansDreamMachine:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
e@IansDreamMachine:~$

It seems we now have two entries for the ath0 device, and we knocked the eth0 entries down to one. I imagine we need to get rid of the top eth0 entry?

---

### Post by Lambert on 2005-12-27
that's what the second command should be getting rid of

sudo route del -net 192.168.0.0 netmask 255.255.255.0 dev ath0

---

### Post by Connollyir on 2005-12-27
[QUOTE=Lambert]that's what the second command should be getting rid of

sudo route del -net 192.168.0.0 netmask 255.255.255.0 dev ath0[/QUOTE]

BAM:

e@IansDreamMachine:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
e@IansDreamMachine:~$

Should I restart network interfaces and see if things start working?

---

### Post by Connollyir on 2005-12-27
[QUOTE=Connollyir]BAM:

e@IansDreamMachine:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ath0
e@IansDreamMachine:~$

Should I restart network interfaces and see if things start working?[/QUOTE]

Well pretty much as I sent that my router freaked out and stopped recognizing me (all requests became very slow and firefox would load for quite some time before finally displaying a page). So I reconfigured the network interfaces. We are now left with the 2 entries for ath0 in the routing table and it occurs to me that i set my computer to be a static ip in the router and I think that is why we have the two entries again. So I reverted back to DHCP rebooted the router and redid  the removal of the spare ath0 and reconfigured the network interfaces and the same thing happened,

---

### Post by Lambert on 2005-12-27
Somebody else is going to have to jump in here, I saw that you had two default gateways which I've read is a problem as the tcp stack in the kernel doesn't route properly when there are two.

With the results I have to say I'm incorrect. Your routing table needs to stay with the three entries, just not two gateways.

sorry I couldn't offer more

---

### Post by Lambert on 2005-12-27
see if you can find any help in this site

[http://www.linuxhomenetworking.com/#Linux%20Main](http://www.linuxhomenetworking.com/#Linux%20Main)

---

### Post by Connollyir on 2005-12-27
Well thanks for the tremendous effort! I'll be sure to look at that site and see what I can do.

Thanks

-Ian

---

### Post by Koybe on 2005-12-28
If you configure your interfaces file well, you'll be able to have a clean route at networking startup.

So you don't need any gateway for eth0 and you need one for ath0. Check that out. You can delete gateway directive for eth0 in /etc/network/interface.

Try restarting you network (/etc/init.d/networking restart) and see what you get.

I think what is strange is that you have the same network on two diffeent NIC on your PC. Why don't you set another ip range for the pc with the crossover cable on the eth0?

---

### Post by mips on 2005-12-28
What you are attempting here falls outside of the design specification for the TCP/IP protocol. You can NOT have two ethernet ports on one device within the same network, they have to fall within two seperate networks !!!

Follow Koybes advice and configure one interface to be in another network.

---

### Post by Connollyir on 2005-12-30
[QUOTE=mips]What you are attempting here falls outside of the design specification for the TCP/IP protocol. You can NOT have two ethernet ports on one device within the same network, they have to fall within two seperate networks !!!

Follow Koybes advice and configure one interface to be in another network.[/QUOTE]

That did it! Its just one of those stupid little things that keeps the whole machine from working. I replaced the old network settings in the etc/network/interfaces file on the server and changed the static ip on the nic to the same network - 172.16.0.X - even though I'm not sure that was necissary. etc/init.d/networking restart > it works.

Thanks for the tremendous ammount of help! !

-Ian

---

