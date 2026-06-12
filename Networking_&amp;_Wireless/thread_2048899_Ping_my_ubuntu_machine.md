---
title: "Ping my ubuntu machine"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by jakesaunders24 on 2012-08-27
Hi
I have a ubuntu server machine that gets its internet from my windows 7 pc i can ping the ubuntu from there because its the one sharing the internet but anything not connected to the switch that has the shared internet cannot see it such as the family iMac or my MacBook Air, any ideas how to make it visible to the whole network?

Cheers
Jake

---

### Post by matthewboh on 2012-08-27
Have you tried pinging <ubuntu server name>.local? 

For example, my server is named liza, so I ping it with liza.local

---

### Post by spiky001 on 2012-08-27
Check the ip addresses are all the same, if not the they wont.

---

### Post by jakesaunders24 on 2012-08-27
> **spiky001 said:**
> Check the ip addresses are all the same, if not the they wont.

what do you mean by the same? sorry for dumb question

---

### Post by spiky001 on 2012-08-27
Ok I see win7 supplys internet to ubuntu by eth0 i Pressume. So how do you connect the others.   internet>>win7>>ubuntu    How will the others be connecting wire or wireless??

---

### Post by Colo993 on 2012-08-27
How exactly are the Windows 7 machine and the Ubuntu machine connected to each othert?  Are you saying that one of the interfaces on the Ubuntu PC is connected directly to the Windows 7 machine?  If so, the Windows 7 firewall might be blocking PINGs/traffic going from other devices on the same network across Windows 7 to the Ubuntu PC.

Is there anyway to connect the Ubuntu PC directly to the network that the Windows 7 PC is connected to?

Colo993

---

### Post by spiky001 on 2012-08-27
HI Colo. I was trying to see if ubnutu is wired to win7 and maybe the others wireless so they are on different subnets, That was my thinking why the wont ping.

---

### Post by jakesaunders24 on 2012-08-27
> **spiky001 said:**
> Ok I see win7 supplys internet to ubuntu by eth0 i Pressume. So how do you connect the others.   internet>>win7>>ubuntu    How will the others be connecting wire or wireless??

Hi yes, that's correct and the computers I'm using to try to ping them are on wireless

---

### Post by jakesaunders24 on 2012-08-28
Anyone?

---

### Post by Herbon on 2012-08-28
Try turning off the Firewall on the Window box

---

### Post by jakesaunders24 on 2012-08-28
> **Mr_Imhotep said:**
> Try turning off the Firewall on the Window box

Hi, thanks i will try that now

---

### Post by jakesaunders24 on 2012-08-28
> **Mr_Imhotep said:**
> Try turning off the Firewall on the Window box

no that didn't work although i have ping'd my macbook air from the windows machine and it works but then i tried once again to ping my windows machine from my mac and it worked but still cant ping ubuntu box

---

### Post by spiky001 on 2012-08-28
Hi

What is the ip address of ubuntu and what is the ip address of mac book

---

### Post by jakesaunders24 on 2012-08-28
> **spiky001 said:**
> Hi

What is the ip address of ubuntu and what is the ip address of mac book

192.168.0.61 = ubuntu 
192.168.0.9 = MacBook

by the way the ubuntu has a static ip

and i have changed the ip address of the ethernet card that connects to the switch that the ubuntu is connected to, that is 192.168.0.60 dont know if this makes a difference?

Jake

---

### Post by spiky001 on 2012-08-28
Hi

Can you explain how all the pc are conected wire ,wireless, it looks like you have ubuntu wired and macs wireless?

---

### Post by Herbon on 2012-08-28
> **jakesaunders24 said:**
> 192.168.0.61 = ubuntu 
192.168.0.9 = MacBook

by the way the ubuntu has a static ip

and i have changed the ip address of the ethernet card that connects to the switch that the ubuntu is connected to, that is 192.168.0.60 dont know if this makes a difference?

Jake

Have you run a "traceroute" on the Ubuntu box?

And make sure the gateway and subnet is correct.

---

### Post by jakesaunders24 on 2012-08-29
> **spiky001 said:**
> Hi

Can you explain how all the pc are conected wire ,wireless, it looks like you have ubuntu wired and macs wireless?

internet - netgear router - wifi to dads 2 windows laptops and macbook pro, imac and my macbook air

wifi also to my desktop - shared out of ethernet to switch - ubuntu

---

### Post by dandnsmith on 2012-08-30
I think the problem is routing.
Can you post the IP addresses you're using on the desktop, and also the routing table (commands for Windows are **ipconfig/all** and **route print**). I suspect that you may have to shift the desktop ethernet and ubuntu to a different 'net'

---

### Post by jakesaunders24 on 2012-08-30
Hi thanks for your reply, thanks for your help i much apprciate it staring to get confused now!! here they are -

---

### Post by dandnsmith on 2012-08-30
That raises two points:
1. the IP4 addresses (192.168.0.16, 192.168.37.1) are on different subnets, so routing is possible - except that there isn't any routing for the 2nd, and the ubuntu IP 192.168.0.60 is wrong range for using the ethernet 192.168.37.1
2. having IP6 as well as IP4 clouds the issue, and I'm not experienced in reading the addresses and the routing entries. Unless you really need it, I suggest you disable the IP6 and concentrate on IP4.

I'm not clear what the switch is for - couldn't you have connected the Ubuntu server and the desktop directly?

NB - I find those snapshots rather confusing - couldn't you confine it to the network essentials?

---

### Post by jakesaunders24 on 2012-08-30
Hi, thanks, i have enabled dhcp for the ubuntu server so its ip address is 192.168.137.102 sorry for confusion! Can you tell me how to route ip addresses because i tried it and cant do it! i typed this into cmd on my pc route ADD 192.168.0.16 MASK 255.255.255.0 192.168.137.102 is that right?

Thanks

---

### Post by Hammer3344 on 2012-08-30
Did you try cross-referencing the IP's of the devices with each other (IP scheme of Win7 vs IP scheme of the server? Type```
ifconfig
``` on your linux server and cross refference that to your Windows 7 IP setup ```
ipconfig /all
``` I would also begin looking at the firewall as previously stated.

---

### Post by jakesaunders24 on 2012-08-30
> **Hammer3344 said:**
> Did you try cross-referencing the IP's of the devices with each other (IP scheme of Win7 vs IP scheme of the server? Type```
ifconfig
``` on your linux server and cross refference that to your Windows 7 IP setup ```
ipconfig /all
``` I would also begin looking at the firewall as previously stated.

Hi, i have type those commands but wondered what is my bcast address? i says 192.168.137.255, what is it? apart from that both subnets 255.255.255.0. however for the ethernet card there is no default gateway should this be 192.168.0.1 like my wifi card?

---

### Post by jakesaunders24 on 2012-08-30
> **dandnsmith said:**
> That raises two points:
1. the IP4 addresses (192.168.0.16, 192.168.37.1) are on different subnets, so routing is possible - except that there isn't any routing for the 2nd, and the ubuntu IP 192.168.0.60 is wrong range for using the ethernet 192.168.37.1
2. having IP6 as well as IP4 clouds the issue, and I'm not experienced in reading the addresses and the routing entries. Unless you really need it, I suggest you disable the IP6 and concentrate on IP4.

I'm not clear what the switch is for - couldn't you have connected the Ubuntu server and the desktop directly?

NB - I find those snapshots rather confusing - couldn't you confine it to the network essentials?

i cant connect them together because i dont have a crossover cable and i need the switch because i connect my raspberry pi to it

---

### Post by Hammer3344 on 2012-08-30
> **jakesaunders24 said:**
> Hi, i have type those commands but wondered what is my bcast address? i says 192.168.137.255, what is it? apart from that both subnets 255.255.255.0. however for the ethernet card there is no default gateway should this be 192.168.0.1 like my wifi card?
 
The broadcast address is used to distribute changes within the network to all other devices within the network. It is not used for any other purpose but that. (think "public address system") Additinally, because your are working off a private IP range in a class C network (indicated by 255.255.255.0) your broadcast will be the last usable IP within the SUBNET (last octet of 255)
 
Second thought:
If the device is attached to Windows 7 as an extension per say, can you possibly share the device to all, so that when you try to access your Windows 7 system, you see the shared device and can connect to it from there? I assume you set your HN (home network) up as something similar to an AD-HOC

---

### Post by jakesaunders24 on 2012-08-30
hi, thanks that makes sense now! what about the default gateway for the ethernet card is that ok to be blank?

---

### Post by Hammer3344 on 2012-08-30
> **jakesaunders24 said:**
> hi, thanks that makes sense now! what about the default gateway for the ethernet card is that ok to be blank?
 
A part of me wants to tell you to set the default gateway to the windows 7 machine seeing as how you are using it as the ad-hoc station. However, this will not work because the IP's are within 2 seperate subnets. double check your windows 7 ipconfigs to see if the server ip scheme (server IP range is similar minus last octet) is on your windows 7 box. If there is a secondary IP, you can set the Gateway address to your Windows 7 IP address that is within the same SUBNET.
 
Example:
```
 
Windows 7 IP scheme: 192.168.32.1
Subnet: 255.255.255.0
 
Linux Server IP: 192.168.32.2
Subnet 255.255.255.0
Gateway 192.168.32.1

```

---

### Post by jakesaunders24 on 2012-08-30
Thanks, they are on the same subnet but not the same scheme 

pc = 192.168.0.16
ubuntu = 192.168.137.102

so i will leave it as it is!!
Could you tell me how to do ip routing to see if that will make my stupid network work!

sorry for all the questions!

---

### Post by Hammer3344 on 2012-08-30
> **jakesaunders24 said:**
> Thanks, they are on the same subnet but not the same scheme 
 
pc = 192.168.0.16
ubuntu = 192.168.137.102
 
so i will leave it as it is!!
Could you tell me how to do ip routing to see if that will make my stupid network work!
 
sorry for all the questions!
 
In terms of setting up routing without a router/switch, I dont know how to accomplish that. However, if you can successfully put your server on the same subnet as your windows 7 machine, that would effectively eliminate the whole network issue as a whole but puts your network at risk for IP conflicts (seeing as how you would have to statically assign IP's on a DHCP network. Depending on the number of devices you have you can 
A. Setup your DHCP to never renew (maintain same IP forever)
B. Set to renew after extremly long times
 
The odds of you getting an IP conflict will be reduced based upon the number of devices you have.
 
I would recommend if you take this route to set the SERVER IP to something like 192.168.0.250
gateway of 192.168.0.16
subnet mask 255.255.255.0
 
What kind of network devices do you have within your network?

---

### Post by jakesaunders24 on 2012-08-30
thanks for your help i still cant access my server or ping it from a computer on the proper network but it will do while i have a play!

Cheers

---

### Post by jakesaunders24 on 2012-08-30
do you think powerline adaptors will work?

---

### Post by Hammer3344 on 2012-08-30
If you are refering to PoE adapters no.
 
What type of network device are you using in order to provide internet to your windows 7 machine, and does it have wifi capabilitiy? If so, does your server have wifi capability.

---

### Post by jakesaunders24 on 2012-08-30
my windows 7 machine has a wifi card and my server doesnt this is why im sharing a connection to it. and i mean powerline the ones where you plug one into your router and into a plug socket and one into a switch and  plug socket.

cheers

---

### Post by Hammer3344 on 2012-08-30
I'm not to sure on that. However, if you can find a way to get your Wi-fi router close enough to the server to plug in an ethernet cable, this will effectively put the server on the same network as all of your other devices.

---

### Post by jakesaunders24 on 2012-08-30
yeah i wish i could but im not able to as its in my room and the router is downstairs in the living room!

---

### Post by Hammer3344 on 2012-08-30
You could always go to a computer buisness/company/store and request a custom length cable. (get a rough estimate of the distance) Cat5 is relatively inexpensive to make...if you have the tools. Outside of that, I am afraid that without actually being there to assist I wont be of much help from here :(

---

### Post by jakesaunders24 on 2012-08-30
good idea, but for 14 quid i might just get a wifi card for it, and thanks alot for your help its great

Jake

---

### Post by dandnsmith on 2012-08-30
Jake - I see a lot happen, but you're still not there, so a couple of comments:

1. that route add command: I assume you're doing that on the Windows desktop - I'm not sure you have it correct without trying, as things vary (and I haven't had to do it for a while. You need to set the destination (the Ubuntu/switch range), a mask, and a 'port' to send through.

2. "Thanks, they are on the same subnet but not the same scheme

pc = 192.168.0.16
ubuntu = 192.168.137.102"
these are definitely **not** on the same subnet - with your mask of 255.255.255.0 that would be either 192.168.0.xxx or 192.168.137.xxx

3. both ends of the link need to be on the same subnet, and this should be different from the subnet used for the stuff linked via the Netgear router.

4. there has to be just one default route for the Windows desktop setup, and another route for the traffic through the switch.

Does that give enough detail? If not I'll try to get you right (post what the setup is)

---

### Post by jakesaunders24 on 2012-08-30
sorry i have been thinking of mask as subnet for some reason! and command still not working. do you mean how stuff is connected when you say setup?

---

### Post by dandnsmith on 2012-08-30
Yes, that is
- any changes to physical wiring (as you last described it)
- IP addresses assigned to the desktop interfaces
- routes currently assigned at desktop
- are you using IP6 at all

later:
did you set up the internet sharing using Windows Internet Sharing?
if so what did it tell you to do about the Ubuntu PC (or any other machine to be included in the sharing)?
Does the sharing work still?

---

### Post by jakesaunders24 on 2012-08-30
WIFI > Windows PC > Switch > Ubuntu > trying to access from macbook, imac etc on wifi

WIFI Card (giving shared internet to ethernet)
192.168.0.16 (can access this from macbook and read files etc)
255.255.255.0
gw - 192.168.0.1

Ethernet Card (going into switch)
192.168.137.1
255.255.255.0
gw - none

ubuntu server (what i want to access on my mb as a file server!)
192.168.137.102
255.255.255.0
bcast - 192.168.137.255

this is set to dhcp

The whole aim of this is to access my samba ubuntu from my macbook as i only bought the 64gb ssd so i need a file server, but can't access it because its made its little internal network!!! which is what were trying to get through.

Just wanted to say thanks for all of your help so far i really appreciate it

Jake

---

### Post by dandnsmith on 2012-08-30
right, so if you add a route on the desktop:

route add 192.168.137.0 mask 255.255.255.0 192.168.137.1

then that should be sufficient to get the traffic correct, and allow you to ping the ubuntu server from the other machines.

I don't think the metric and interface need to be specified, but if they are, then pick a metric of 1 and the appropriate interface (eth1 wasn't it?)

If it works then you can use the '-p' in the command to make it survive reboots.

HTH

I shall be out for a while (evening and overnight here in UK), but I'll check tomorrow.

---

### Post by jakesaunders24 on 2012-08-30
> **dandnsmith said:**
> right, so if you add a route on the desktop:

route add 192.168.137.0 mask 255.255.255.0 192.168.137.1

then that should be sufficient to get the traffic correct, and allow you to ping the ubuntu server from the other machines.

I don't think the metric and interface need to be specified, but if they are, then pick a metric of 1 and the appropriate interface (eth1 wasn't it?)

If it works then you can use the '-p' in the command to make it survive reboots.

HTH

I shall be out for a while (evening and overnight here in UK), but I'll check tomorrow.

Hi, thanks for the reply! just tried it and it says route already exists? do i need to change either the .137.1 or .137.0 (i dont know what they mean! but to a .0.1 because this is the ip of pc? if you get what im saying? and i will check back tommorow im off to bed to watch celeb juice!

Jake

---

### Post by dandnsmith on 2012-08-30
No, the command is correct, insofar as the 2 IP addresses are concerned - but you may have a conflicting route in the table which is messing things up. Can you print the routes, as they exist, again (just in case there's a variation which I haven't spotted).

---

### Post by jakesaunders24 on 2012-08-31
here it is-

---

### Post by dandnsmith on 2012-08-31
Sorry Jake, I really wanted the routing again

---

### Post by jakesaunders24 on 2012-08-31
sorry im so stupid with all of this!

---

### Post by dandnsmith on 2012-08-31
That looks as if it's OK, with a couple of redundant (but not harmful) routes included.

If ping still isn't working (try it both ways round), I'd try using traceroute (qv) to see if that offers any extra info.

I'll be out for a few hours, but will check later.
Good luck

---

### Post by jakesaunders24 on 2012-08-31
Hi i used the tracert command on a few different ip addresses and have posted a pic to show you as i dont really know what im looking for!

Jake

---

### Post by dandnsmith on 2012-08-31
Jake - there's something wrong here, as the traceroute to the ubuntu is going via the internet link to some IP address which may be your DNS servers or something.

Only thing I can think of is to clear the routes (by reboot, or use route to flush the route table) and then set a route for 192.168.137.0 via 192.168.137.1 (but no other) and try again.
It's tedious, I appreciate, but we need to establish how the traffic is getting directed to the internet.

Did you try the ping or traceroute from the Ubuntu server - or isn't that feasible at this stage?

---

### Post by jakesaunders24 on 2012-08-31
ok i will do the ip route again, and i did the traceroute from the pc did you mean for me to do it on the ubuntu machine (probably another dippy thing from me!)

---

### Post by dandnsmith on 2012-08-31
Add the IP route after a reboot, and check the route table.

Do the traceroute from both Desktop and server - might throw something up

---

### Post by jakesaunders24 on 2012-08-31
right, pc says route exists and you saw my trace route from pc on page 5 so now just server bear with me a mo

---

### Post by jakesaunders24 on 2012-08-31
how do you do a trace route on ubuntu

---

### Post by dandnsmith on 2012-08-31
I think it is just traceroute in a terminal window - or are you doing things via the GUI?

later: just found my Mint installation doesn't have traceroute, but does have traceroute6.
When installed, traceroute functions normally

---

### Post by jakesaunders24 on 2012-09-01
mine cant do it?

---

### Post by dandnsmith on 2012-09-02
I just don't know, since I don't have that version of Ubuntu installed to try it. Just try it.
You may be able to get the same info via traceroute6, but it doesn't work for me - probably because I disabled use of IP6 deliberately (because of some of the side effects I experienced).

---

