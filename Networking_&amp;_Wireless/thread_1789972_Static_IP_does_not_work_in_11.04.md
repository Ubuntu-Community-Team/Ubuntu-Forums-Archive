---
title: "Static IP does not work in 11.04"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by OrvillP on 2011-06-24
[FONT=Arial, sans-serif][SIZE=2]I cannot set a static IP for eth0 in Ubuntu 11.04.[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]I do this:[/SIZE][/FONT]
 

     [FONT=Arial, sans-serif][SIZE=2]sudo vi /etc/network/interfaces[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]and then edit the file to[/SIZE][/FONT]
 

     [FONT=Arial, sans-serif][SIZE=2]auto lo[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]iface lo inet loopback[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]auto eth0[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]iface eth0 inet static[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]address 172.16.1.39[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]netmask 255.255.0.0[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]network 172.16.0.0[/SIZE][/FONT]
     [FONT=Arial, sans-serif][SIZE=2]gateway 172.16.0.1[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]and save the file.[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Then I edit the resolv.conf file by:[/SIZE][/FONT]
 

     [FONT=Arial, sans-serif][SIZE=2]sudo vi /etc/resolv.conf[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]to[/SIZE][/FONT]
 

     [FONT=Arial, sans-serif][SIZE=2]nameserver 172.16.0.1[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]which is the IP of my router, and save the file.[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Then I try to restart eth0 by:[/SIZE][/FONT]
 

     [FONT=Arial, sans-serif][SIZE=2]sudo ifdown eth0[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]but I get:[/SIZE][/FONT]
 

     [FONT=Arial, sans-serif][SIZE=2]ifdown: interface eth0 not configured[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]I can ping lo from Ubuntu but nothing else, including 172.16,1.39.[/SIZE][/FONT]
 

 [FONT=Arial, sans-serif][SIZE=2]What gives? Anyone's help would be appreciated, greatly.[/SIZE][/FONT]

---

### Post by chili555 on 2011-06-24
Manual methods will always have difficulty over-powering Network Manager if it's installed and running. Is it? If it is, you are far better off to set the static IP details in NM. Please see attached.

Moreover, how is address 172.16.[COLOR="Red"]**1**[/COLOR].39 going to connect to 172.16.[COLOR="Red"]**0**[/COLOR].1? Maybe you have a more complicated corporate router/switch/access point than most of us.

If you have an ordinary home router, I believe the netmask needs to be 255.255.255.0.

---

### Post by OrvillP on 2011-06-24
I also tried using Network Manager and got the same result - nothing.

I believe 172.16.xxx.xxx signifies a private Class B network wherein only the first 2 octets of the IP address have to be identical for hosts to share the same subnet. That's why a Class B network has a netmask of 255.255.0.0.

---

### Post by chili555 on 2011-06-24
> 12.16.xxx.xxx signifies a private Class B network wherein only the first 2 octets of the IP address have to be identical for hosts to share the same subnet. I figured it was unusual.

I still believe that NM is going to interfere with /etc/network/interfaces.

Do you have an eth0 interface in ifconfig? Does your ethernet card have a driver associated and an interface created in sudo lshw -C network? Does this tell us anything more informative?```
sudo ifdown eth0 && sudo ifup eth0
```

---

### Post by Iowan on 2011-06-24
Is the router also set up with that netmask? I presume that you had to change the (router's) address - so you got the mask, too...
Does **ifconfig -a** confirm the interface has the address? I haven't tried the **service** method of restarting networking... but a reboot should accomplish the same thing.

---

### Post by OrvillP on 2011-06-25
[FONT=Arial, sans-serif][SIZE=2]Here is my whole network:[/SIZE][/FONT]
[FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]
   
 _2[FONT=Arial, sans-serif][SIZE=2]Wire DS1000 Router Settings on the Private side[/SIZE][/FONT]_
 

 [FONT=Arial, sans-serif][SIZE=2]Address		172.16.0.1[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Netmask		255.255.0.0[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]DHCP Range		172.16.1.33 to 172.16.1.250[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Addresses Allocated	1[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]Addresses Available	217[/SIZE][/FONT]
 


 [FONT=Arial, sans-serif][SIZE=2]_List of devices on private network_[/SIZE][/FONT]
 

 _#_	[FONT=Arial, sans-serif][SIZE=2]_IP Type_		_Address IP_    	_Netmask IP_    	_DNS IP_        		_Gateway IP_    	_Function_[/SIZE][/FONT]
 1	[FONT=Arial, sans-serif][SIZE=2]Static    		172.10.0.1    	255.255.0.0    	172.16.0.1    	172.16.0.1     	the router	[/SIZE][/FONT]
 2	[FONT=Arial, sans-serif][SIZE=2]Static    		172.16.1.4    	255.255.0.0    	172.16.0.1    	172.16.0.1      	server[/SIZE][/FONT]
 3	[FONT=Arial, sans-serif][SIZE=2]Static	    172.16.1.5    	255.255.0.0     172.16.0.1    	172.16.0.1      server[/SIZE][/FONT]
 4	[FONT=Arial, sans-serif][SIZE=2]Static		172.16.1.6        	255.255.0.0    	172.16.0.1    	172.16.0.1      	server[/SIZE][/FONT]
 5	[FONT=Arial, sans-serif][SIZE=2]Static		172.16.1.34      	255.255.0.0    	172.16.0.1     172.16.0.1      	client[/SIZE][/FONT]
 6	[FONT=Arial, sans-serif][SIZE=2]Static		172.16.1.37      	255.255.0.0    	172.16.0.1     172.16.0.1      	client[/SIZE][/FONT]
 7	[FONT=Arial, sans-serif][SIZE=2]Static		172.17.1.38      	255.255.0.0     172.16.0.1     172.16.0.1      	client[/SIZE][/FONT]
 8	[FONT=Arial, sans-serif][SIZE=2]Static		172.16.1.39     	This is where the Ubuntu 11.04 client should show up[/SIZE][/FONT]

---

### Post by OrvillP on 2011-06-25
Sorry. The address of the router is 172.16.0.1, not 172.10.0.1. My fault.

---

### Post by les@dbsit.com on 2011-07-09
[FONT=Arial][SIZE=2]I see that you've indicated that this was solved by identifying that the router address was incorrect, but there are some other problems worth answering as well - for those people who come across this looking for answers to similar issues...

In your initial post, you show the interfaces file to list your interfaces (2 of them) like this:

[/SIZE][/FONT][FONT=Arial][SIZE=2]auto lo[/SIZE][/FONT][FONT=Arial][SIZE=2]
     [/SIZE][/FONT][FONT=Arial][SIZE=2]iface lo inet loopback[/SIZE][/FONT][FONT=Arial][SIZE=2]
     [/SIZE][/FONT][FONT=Arial][SIZE=2]auto eth0[/SIZE][/FONT][FONT=Arial][SIZE=2]
     [/SIZE][/FONT][FONT=Arial][SIZE=2]iface eth0 inet static[/SIZE][/FONT][FONT=Arial][SIZE=2]
     [/SIZE][/FONT][FONT=Arial][SIZE=2]address 172.16.1.39[/SIZE][/FONT][FONT=Arial][SIZE=2]
     [/SIZE][/FONT][FONT=Arial][SIZE=2]netmask 255.255.0.0[/SIZE][/FONT][FONT=Arial][SIZE=2]
     [/SIZE][/FONT][FONT=Arial][SIZE=2]network 172.16.0.0[/SIZE][/FONT][FONT=Arial][SIZE=2]
     [/SIZE][/FONT][FONT=Arial][SIZE=2]gateway 172.16.0.1

You also identified that you were told that you could not down the eth0 interface because when you issue the command "[/SIZE][/FONT][FONT=Arial][SIZE=2]sudo ifdown eth0", you get the response "[/SIZE][/FONT][FONT=Arial][SIZE=2]ifdown: interface eth0 not configured"[/SIZE][/FONT][FONT=Arial][SIZE=2] and that you could not ping anything except for the loopback interface - including the address you had assigned to eth0.
 
All of your logic here is good, and following it, you should get the response you expect... except for one detail... (bum. bum.. bum,,,,)

The interfaces file that you are editing to configure your interfaces (funny how that works...) is organized in stanzas.

That's right folks,... gotta have a carriage return between "[/SIZE][/FONT][FONT=Arial][SIZE=2]iface lo inet loopback[/SIZE][/FONT][FONT=Arial][SIZE=2]" and "[/SIZE][/FONT][FONT=Arial][SIZE=2]auto eth0".  

Otherwise, the configuration is read by the OS as 
   "hmm,... lets see,... I have a first interface here 'lo' which is a local loopback,... 
    I know how to do that (so I can ignore the rest of this stanza and move on to 
    the next),... looks like that's all, done configuring the interfaces..."[/SIZE][/FONT][FONT=Arial][SIZE=2]
...
certainly, I'm no expert... the noobiest of the noobs,... but this one i got...
-Les
      [/SIZE][/FONT]

---

### Post by lisati on 2011-07-09
Just as an aside, my personal preference is to let the router assign IP addresses. This can help avoid conflicts if, for example, you connect your laptop to someone else's network for some reason.

---

