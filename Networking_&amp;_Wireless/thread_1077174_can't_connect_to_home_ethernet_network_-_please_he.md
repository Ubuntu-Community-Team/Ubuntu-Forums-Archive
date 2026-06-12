---
title: "can't connect to home ethernet network - please help :)"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by australia-sydney on 2009-02-22
Hi all,

I'm a first time user of Ubuntu / Linux. I just installed it today!

I can't connect to my 10mbps home ethernet network though. 

I set my network card to 10mbps by typing 

sudo mii-tool -F 10baseT-FD

into the terminal.

Then I get the "requesting network address" spinning graphic up in the top bar. It can't find a network address though and gives up.

Also, i had no ethtool when I installed ubuntu (downloaded + installed today, 22 Feb 2009). I downloaded ethtool on another machine and transferred it across via usb. Now I can't even get the "requesting network address" spinning graphic up in the top bar.

Would appreciate help! Thanks very much in advance...

Cheers,

Ronnie

---

### Post by australia-sydney on 2009-02-22
Hi all again,

OK so I'm doing some further reading..
[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

it seems like I need to assign a static ip address rather than a dhcs one?

to do this, i need the following..

ip address
netmask
network
broadcast
gateway

How do i find all these things? I'm a total n00b.

Thanks for any help you can give!

Appreciated...

---

### Post by Iowan on 2009-02-22
What else is on your network?  DHCP is (usually) pretty painless (because DHCP takes care of those details), but sometimes static is necessary.  If there is another machine you can check for network, you can copy *most* information - the ip address will need to be different.  *Probably* the first three digits should be the same (eg. 192.168.0 ), the last must be different from anything else on your network.

---

### Post by australia-sydney on 2009-02-22
thanks Iowan. 

On the home network there is a wireless router and 2 pcs running windows xp. there is also my pc which is now running ubuntu. 

so i'd go into the network diagnostics on the windows xp computers and copy everything except the ip address? The ip address i'd get from my ubuntu computer by typing 

ifconfig

into the terminal?

will try it out and post back here..

---

### Post by cariboo on 2009-02-22
Do you have mac address filtering setup on your router?

Jim

---

### Post by australia-sydney on 2009-02-24
ok so I copied all the details (except the ip address) from another computer (an asus eee pc 7") which I plugged in to the exact same ethernet cord i want to use w. my ubuntu desktop (the one I couldn't connect). I got my ip address from ifconfig on the terminal of the ubuntu desktop.

Now ubuntu tells me I'm connected - but i can't visit any sites or even ping an ip address. 

Jim - I'm not sure what you mean. Sorry, I'm a n00b when it comes to networking etc. We're using a netgear wireless router. should i have mac address filtering setup? 

Thanks for your help so far everyone! 

cheers,
Ronnie

---

### Post by Iowan on 2009-02-24
I presume you listed your router as the gateway... Check */etc/resolv.conf* to see what you're using for nameserver.  Mine points to my router.
> **australia-sydney said:**
>  should i have mac address filtering setup? Makes better security, but if filtering is on and this machine's MAC is not included... it'll be lonely.

---

### Post by Hobgoblin on 2009-02-24
> **australia-sydney said:**
> I got my ip address from ifconfig on the terminal of the ubuntu desktop.


Nope, you need an IP address similar to the one on the PC you copied everything else off.  The last set of digits should be different (i.e if you have 192.168.0.2 on your eee, then try 192.168.0.20 on Ubuntu, although that will probably work it isn't quite that simple).

If you have not set up static IP addresses on your other systems then there should be no need to do so on your Ubuntu system.  It should work with DHCP like the rest of your network.

You also shouldn't need to set 10Mbps manually, it should auto-negotiate.

---

### Post by australia-sydney on 2009-02-24
Hobgoblin - in my IP4 settings tab, I changed what i had down for ip address. Now i've got 192.168.0.30 (which i based on the eee pc's ip address of 192.168.0.3). 

Now when I ping 91.189.94.249 (as instructed in ubuntu help files) I can send packets but none are received. 

This is an improvement - Previously, when I had the other ip address (127.0.0.1) listed in my IP4 settings tab, I couldn't even send packets. 

Next steps are for me to check if there's any mac address filtering on the netgear router.  

Iowan - I typed in /etc/resolv.conf but it said permission denied.

After i type in ifconfig, do the eth0 and the lo have to be the same?

eth0 Link encap:Ethernet HWaddr 00:01:6c:b0:db:df
inet addr:192.168.0.30 Bcast:192.168.0.255 Mask: 255.255.255.0
etc etc (this is hand copied)

lo Link encap:Local Loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
etc etc

cheers and thanks in advance,
Ronnie

---

### Post by Hobgoblin on 2009-02-25
> **australia-sydney said:**
> Hobgoblin - in my IP4 settings tab, I changed what i had down for ip address. Now i've got 192.168.0.30 (which i based on the eee pc's ip address of 192.168.0.3). 

Now when I ping 91.189.94.249 (as instructed in ubuntu help files) I can send packets but none are received. 

Try pinging your gateway address first.

> This is an improvement - Previously, when I had the other ip address (127.0.0.1) listed in my IP4 settings tab, I couldn't even send packets.

127.0.0.1 is always the local machine. 

> Next steps are for me to check if there's any mac address filtering on the netgear router. 

Unlikely that it will, anyway that's only affect wireless connections.  And it doesn't really provide any extra security so don't bother with it. 

> Iowan - I typed in /etc/resolv.conf but it said permission denied.

```
cat /etc/resolv.conf
```

> After i type in ifconfig, do the eth0 and the lo have to be the same?

No, they should not be.

I'm still not sure why you decided to force 10baseT-FD (are you sure it's only 10mbps, are you sure its full duplex? what's the model of your router?).

try
```
sudo mii-tool -R
```
to reset it to auto negotiate, this should be reliable.

Also put it on DHCP, if DHCP works on your other systems then there is no reason to use static IP on this one.

Also why did you need ethtool? And what did you do with it?

---

### Post by australia-sydney on 2009-02-25
My router is a netgear wireless firewall router WGT624 v2.

when I type cat /etc/resolv.conf it says nameserver 192.168.0.1, which is what i was using for both the gateway and the dns server.

when i had windows xp on the computer which is now running ubuntu, we had to set it to 10mbps also. the ethernet cord runs at least 10 meters (30ft) as this is a shared house. just as a test, i took off ubuntu and put a fresh install of xp back on. it wouldn't connect either. so i put ubuntu back on.

here's what im using:
ip address 192.168.0.30 (this is a guess, based on the eee pc's ip address of 192.168.0.3)
netmask 255.255.255.0
gateway and dns server: 192.168.0.1

now it won't connect at all, not even to the stage i was at before where i could send pings (but not have them received).

thanks for all the tips so far, i'm really impressed with the community support. Hopefully we'll work it out soon!

cheers,

Ronnie

---

### Post by Hobgoblin on 2009-02-25
Can you move this system near the router just for testing purposes.  And use a different, shorter, known good ethernet cable.

I suspect the problem lies within the ethernet cable.

Set it back to DHCP and auto negotiate on the NIC.

You could cross check the cable theory by putting a known working system where this system is now.

> **australia-sydney said:**
> My router is a netgear wireless firewall router WGT624 v2.

[That](http://www.netgear.com/Products/RoutersandGateways/SuperGWirelessRouters/WGT624.aspx?detail=Specifications) should be capable of 100mbps.

From the Netgear site.
> LAN: 4 ports 10/100 Mbps (auto-sensing) Ethernet, RJ-45 

30m should pose no problems for ethernet if the cable is in good condition.

---

### Post by Yashiro on 2009-02-25
Try another cable and run Ubuntu from a LiveCD. It should 'just work' as long as your network cards driver is loaded. 
If not, your router has DHCP disabled or some other setting is preventing you getting a network address. Usually a result of some over zealous security tweaking.

---

### Post by australia-sydney on 2009-02-26
Hi Hobgoblin, Yashiro & all,

thanks for your suggestions. I tested the ubuntu desktop at the source (before the router). It didn't work. 

By contrast, the asus eee pc worked on the downstairs cable (the cable I unsuccessfully tried to connect my ubuntu desktop to).

> It should 'just work' as long as your network cards driver is loaded. 

It must be that. I took my pc back to the shop where it was built. they reminded me there was a cd with drivers. but they're only for windows. so now i'm looking for a foxconn K7S741MG-6L motherboard driver for ubuntu - or am i? the lan card itself is an ATA133 10/100 LAN. this really is the last hurrah. if i can't find this driver, i can't use linux. or i have to buy a new computer or lan card or whatever. but i'd rather not.

so thanks heaps in advance for all your help, and all your help past. really impressed with this forum. can we crack this last chestnut? will try googling it this summer afternoon..

---

### Post by Hobgoblin on 2009-02-26
Well a LAN card would be a fairly cheap solution.

I very much doubt you need to find drivers for Ubuntu.

When you loaded XP did you load the drivers?  If not then load XP again and the drivers from the CD (or the foxconn website), just to make sure the NIC is working.

Check the BIOS, make sure the network card is not disabled.

Enjoy your summer afternoon, I'm off to bed this winter morning. ;)

Motherboard drivers (for Windows) and manual are [here.](http://www.foxconnchannel.com/en-us/product/Motherboards/detail_spec.aspx?ID=en-gb0000001)

Pretty standard stuff though.

You could also try resetting the BIOS with the jumper on the motehrboard.  That would rule out any BIOS setting.

---

### Post by Yashiro on 2009-02-26
Realtek RTL8201BL I think is the driver module but

> Try another cable and run Ubuntu from a LiveCD. It should 'just work' as long as your network cards driver is loaded. 

---

### Post by australia-sydney on 2009-02-26
Hi again

Hobgoblin - i didn't load the drivers when i reloaded xp. it should all be working, it was just a few days ago.

It seems Ubuntu does recognise my lan card - when I use the hardware tester facility it asks me if I have a sis900 PCI Fast Ethernet (rev 91). I assume this means the bios is all ok and i don't have to tweak it?

Weird that it won't connect though - even when i plug it directly into the modem using a different, shorter cable. 

Also weird is how it says its connected (once i force 10 speed and assign a static ip) but it actually isn't connected at all.

very frustrating but i never want to go back to windows again! any help or thoughts very much appreciated... :)

---

### Post by Hobgoblin on 2009-02-26
> **australia-sydney said:**
> 
Hobgoblin - i didn't load the drivers when i reloaded xp. it should all be working, it was just a few days ago.


Windows will almost definitely need the drivers to work.

I'm beginning to suspect there is a hardware fault, there should be no need to force 10mbps on the card, it should work with DHCP and without any tweaking.

Testing it with Windows (and the drivers) might help confirming or discounting the theory.

When you connect it to the router do you get a light on the router to indicate a connection is present? (one of the lights marked 1 2 3 4 should come on when you connect the cable - might need the PC running - will be green for 100mbps or amber for 10mbps)

---

### Post by mungvvii on 2009-02-27
Hi all

im a ubuntu newb too, in almost the same boat that australia-sydney is in.

But my problem is that ubuntu wont establish a PPPoE connection during thr instalation process. An error saying it cant find any PPPoE connection, occurs.

My setup is the same 2 PC network that australia-sydney has. I use a Dlink 524 router. No probs on XP with networking. Im using Auto IP and DCHP as Telstra sets it that way by default. I am familiar with static IP principles, but have not ventured there yet.

Reading your post made me wonder if its the same issue that im having [im up at Newcastle]. I rang telstra and asked about the pppoe and the possible causes, i was told that they dont use PPPoE, theirs is a PPPoA connection and it wont work if oE is selected in their MDC. also said they dont support linux in any way shape or form!! So thats why im here.

I wonder if it is your ISP using an oA connection too????? I may be way off base here, so excusee. I also would have thought that this would have been a common problem, but like i said, im a 1st time Ubu user, so im in the dark.

thanks, sorry to hijack the thread.

---

### Post by Hobgoblin on 2009-02-27
> **mungvvii said:**
> Hi all

im a ubuntu newb too, in almost the same boat that australia-sydney is in.

But my problem is that ubuntu wont establish a PPPoE connection during thr instalation process. An error saying it cant find any PPPoE connection, occurs.

My setup is the same 2 PC network that australia-sydney has. I use a Dlink 524 router.

PPoE/A is on the DSL side.

If you are using a router then the modem (often combined with router) will establish the PPPoE (or PPPoA) connection.  All that Ubuntu does is connect to the router.
[edit] I did a quick google of the dlink 524, it connects to a modem, the modem will do all the PPPoE/A stuff, I assume you've set that up correctly if it wasn't supplied by your ISP already set up.

Anyway, it's a completely different issue, Aus-Syd isn't even getting connected to the router.

---

### Post by mungvvii on 2009-02-27
> Anyway, it's a completely different issue

Sorry, my bad, i'll start a new thread on my problem. NEWB ALERT!!! ;):p

> Aus-Syd isn't even getting connected to the router. 

neither am I, it would seem??? i dont know alot about the ways of the router, i only got i 4 days ago, and previously used modem to PC's NIC and Xover cable between PC's.

thanks anyways

---

### Post by Hobgoblin on 2009-02-27
> **mungvvii said:**
> 
neither am I, it would seem??? 

I don't know, you seem to have misunderstood your setup.

I don't remember Ubuntu asking how my internet connection was set up during install but you seem to be trying to set up a DSL connection on your Ubuntu system.  You don't need to do that.

The modem handles the DSL connection, the router handles the connection between the PCs and the modem.  Routing traffic appropriately.

Just leave everything to automatic, shortly after logging on you should be informed you are connected to the wired network, internet should then simply work.

---

### Post by mungvvii on 2009-02-27
the install wont complete, so i have no ubuntu to work in

new thread time!! LOL

does this board allow pictures from your local HDD or is a 3rd party imageserver needed?

---

### Post by madhavhmk on 2009-02-27
I have the same problem too....!!!!!!!!!


I have bought a brand new dell desktop and have installed 8.04
but ethernet is just not working when i give dhcp settings......

here is the strange part....... i have a laptop which has the linux installed from same cd....when I connect the lan wire to the laptop there are no problems at all....!!! dhcp is picking it up...



I have also tried static ip address connection.....
i have the ip, subnet, gateway and dns data. it is again fine through laptop but not in desktop...!!!!!

and also it is not a hardware problem because I have vista installed on the same system and internet is working fine through vista...!!!!!


plz help

---

### Post by Hobgoblin on 2009-02-27
> **madhavhmk said:**
> 
I have bought a brand new dell desktop and have installed 8.04
but ethernet is just not working 

Give the output of

```
ifconfig eth
```

and

```
lshw -c network
```

---

### Post by australia-sydney on 2009-03-02
Hi Hobgoblin & all,

I gave up. I installed XP again, including the drivers and DHCP etc worked automatically out of the box.

I'd love to use ubuntu again someday but im not sure I can with my current pc. Maybe I'll just have to be one of those people that buys a new laptop w. ubuntu already installed, guaranteed to work w. ethernet right out of the box. 

Thanks so much for your help, ubuntu rocked.

cheers
Ronnie

---

