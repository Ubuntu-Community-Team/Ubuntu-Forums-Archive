---
title: "Static Lan Adress from Linksys to a Ubuntu Server"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Tlingit on 2010-05-05
Okey I have a good start i know there is something I'm missing.
After Following this great help tutorial.
[http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)
And kinda guestimating and messing around with my Linksys creating a new router assigning a static ip "Lan and wireless" address.

configuration for the router looks like this.
Route Name:	   	 	 
 	 	 	Destination LAN IP:	   .  .  .  	 	 
 	 	 	Subnet Mask:	   .  .  .  	 	 
 	 	 	Default Gateway:       .   .   .
                        Interface " Wireless & Lan"


Then i go to my interface config file and change it to static with the following
address
netmask
broadcast
network
gateway

I think I might be messing up the interface config file at the "NETWORK" section but i don't know.

Could someone please explain or point me to a yet another tutorial.

Thank you,

---

### Post by chili555 on 2010-05-05
> configuration for the router looks like this.
Route Name:
Destination LAN IP: . . .
Subnet Mask: . . .
Default Gateway: . . .
Interface " Wireless & Lan"These are probably the external IP details; that is, the address the router gets from your internet service provider. The router probably assigns 192.168.x.x addresses within your home network.

If the DHCP server in the router is still turned on (it is by default), you need to pick a static address outside the DHCP pool. My Linksys router assigns 50 addresses starting at 192.168.1.100. It is safe, then to assign a static address above x.49. Therefor, an interfaces file like this will work correctly.> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.160
netmask 255.255.255.0
gateway 192.168.1.1Remember to populate /etc/resolv.conf, also. Assuming the above details are accurate, this will work:```
nameserver 192.168.1.1
```Obviously, substitute your details. Post back if you get stuck.

---

### Post by Tlingit on 2010-05-05
Here is my static assignment from my router. 	 
 	 	 	Destination LAN IP:	   192.168.8.0           //This is the new router assignment	 	 
 	 	 	Subnet Mask:	   255.255.255.0 	 
 	 	 	Default Gateway:	   192.168.7.1                   //This is my already config DHCP router in the basic set up	 
 	 	 	Interface:	"Wireless & Lan"

The router wont let me set the new router as .7.x(says router may already exist) nor will it let me change the .8.0 to .8.x.

So i have that set up from my router to the Server.

I have changed my interface and nameserv file to include both 192.168.8.0 and the .7.1 because I didn't know which one the server would be looking for to resolve names.

Here is my interface file
auto eth0
iface eth0 inet static
address 192.168.8.0                // I also tried 192.168.x
netmask 255.255.255.0
gateway 192.168.7.2

Thank you for what you have cleared up already in my head.

---

### Post by chili555 on 2010-05-05
> Destination LAN IP: 192.168.[COLOR="Red"]8[/COLOR].0 //This is the new router assignment
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.[COLOR="Red"]7[/COLOR].1 //This is my already config DHCP router in the basic set up This seems highly unlikely. Did the router provide you with the x.7.1 address? I am sure you have already discovered that your interfaces file is not working correctly.  The biggest issue is that you cannot give your server the same address as the router. You must give the server its own unique address. I suggest this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.8.16
netmask 255.255.255.0
gateway 192.168.8.1 
```Amend resolv.conf to:```
nameserver 192.168.8.1
```Restart networking:```
sudo /etc/init.d/networking restart
```See if you are connected:```
ping -c3 www.google.com
```

---

### Post by Tlingit on 2010-05-05
Okay Yes i Changed the default login of my router to .7.x, I have tried the set up how you have guided me.

It seams my router wont let me change .8.0 to anything .8.x and it won't let me change my default gateway to the ip address of the router it will let me change it to anything but. I think that is what is wrong other then that i have it set up how you said, and everything works with out a static ip.

Any other suggestions  on how i should get my server locked on to a static lan, is there any other way?

---

### Post by chili555 on 2010-05-05
Can you set your router as this?```
Destination LAN IP: 192.168.8.0 //This is the new router assignment
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.[COLOR="Red"]8[/COLOR].1
```If so, the arrangement I last quoted should work. 

What model Linksys router is it?

---

### Post by Tlingit on 2010-05-05
A normal Linksys WRT54gs2 V1.
                                                      
No it won't let me set the default gate way at .x.1, if the destination address is at .x.0 it will tell me that the gateway is not directly reachable through that interface. I Try changing the interface from "Lan & Wireless" To "Wan Internet" Same thing.
Here is my Default DHCP set up

Local ip 192.168.7.1
sub net 255.255.255.0
Starting ip .7.100
max [5]

Then the advanced routing
 
Static Routing

 	 	Select set number:	
   	 	 
 	 	 		 	 
 	 	 	Enter Route Name: Web-Server	   	 	 
 	 	 	Destination LAN IP:	   192.168.8 .0  	 	 
 	 	 	Subnet Mask:	   255.255.255.0  	 	 
 	 	 	Default Gateway:	   192.168.y.x  	 	 
 	 	 	Interface: "Lan & Wireless"
x is greater then one
y has to be the same as the DHCP

---

### Post by Tlingit on 2010-05-05
I would be very Greatful if you checked back later to see if i got it. I have been at this for around 9 hours so far I think I'll take a break.

Thank you you have answered so many of my questions I know I'm close there is just one human error int the way haha.

Thank you.

---

### Post by chili555 on 2010-05-05
I'll be around. Take a break and we'll resume later. In the meantime, I am going to read the manual for your router and post some suggestions. See you again later.

---

### Post by chili555 on 2010-05-05
Under *Internet Settings*, I suggest DHCP, unless you have been given a static IP address to use from your internet service provider. In that case, it will not be a 192.168.x.y address. Let the router negotiate an address from your internet service provider on its own.

Under *Network Settings*, you can use 192.168.8.1. Leave the subnet mask as 255.255.255.0. Enable the DHCP server. A starting IP of 192.168.8.100 and five reservations is just fine.

If you are not using wireless, that's really all you need to do.

My suggested interfaces file will work fine.

---

### Post by Tlingit on 2010-05-06
Okay I Understand what you have been saying, and I have read so many things on static ip addresses so I think I have an understanding maybe i'll just bounce what i know off you and see if I can't find something.

Brand new reset all settings default router. ( Accept for the typical admin account stuff).
**Under the Setup tab**
Local ip [INDENT]192.168.1.1[/INDENT]
Subnet   [INDENT]255.255.255.0[/INDENT]

DHPC Server yes
Starting ip [INDENT]192.168.1.100[/INDENT]                          
Max DHCP[INDENT]50[/INDENT]

**Under the Advanced routing**
Select[INDENT]Gateway[/INDENT][INDENT]//because I have no other router.[/INDENT]
Select[INDENT]number one[/INDENT][INDENT]//just the number of rout (with a name) [/INDENT]

Destination Lan ip[INDENT]192.168.x.0[/INDENT][INDENT]//I don't understand these octants why does the last one have to be zero and if it is zero can i still pick any number out of the DHCP domain for zero like (192.168.1.5). Also x can not be the same as the default gateway because it says the default route may already exist[/INDENT]

Subnet Mask[INDENT]255.255.255.0[/INDENT][INDENT]//gives information about components of the ip[/INDENT]

Default Gateway[INDENT]192.168.1.y[/INDENT][INDENT]//Y has to be out of the DHCP domain so i can use.[2,98][/INDENT][INDENT]//Also it will not work if the Destination Lan is the same as the default gateway and i can not use the router ip (192.168.1.1) for the default gate way but i can use [/INDENT][INDENT]192.168.1.y[/INDENT]

Thank You

---

### Post by Tlingit on 2010-05-06
Can i just assign it a static address from the DHCP?

---

### Post by chili555 on 2010-05-06
You do not need Advanced Routing. I hope I am not being too blunt, but you are making this way harder than it is.

Under the Advanced routing
Select

    Gateway

    //because I have no other router. [COLOR="Red"]Correct.[/COLOR]

Select

    number one

    //just the number of rout (with a name)[COLOR="Red"] Makes no difference.[/COLOR]

Destination Lan ip

    192.168.x.0 [COLOR="Red"]No. Should be left blank.[/COLOR]

Subnet Mask

    255.255.255.0 [COLOR="Red"]No. Should be left blank.
[/COLOR]
    
Default Gateway

    192.168.1.y   [COLOR="Red"]No. Should be left blank.
[/COLOR]

Click Apply and you are all set.

The listings under Setup Tab are correct.

Static or DHCP addresses in your computer are set up in your computer. It can be done in some routers, but it is very easy to do in the computer.

Your router doesn't know or care whether any computer is static or DHCP, as long as the addresses don't collide.

---

### Post by Tlingit on 2010-05-09
I just wanted to stop back and say Thank you very much! This cleared everything up. I got it just like you said and i'm glad you were patient to my learning. I leaned a bunch.

---

### Post by chili555 on 2010-05-10
When I didn't hear from you, I worried that it didn't work or I scared you off. I am very glad it's working for you. Please call on me any time.

---

