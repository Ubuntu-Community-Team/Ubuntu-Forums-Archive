---
title: "Ethernet wired but no connection"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by JUICE690 on 2010-02-14
Hi there,

I've been trying desperately to network my Acer Revo 3600 with ubuntu Karmic Koala to network my my mac.

Wireless works absolutely fine, i've set up smb & afp shares and both work. But I need the wired connection to work as transferring large files, or streaming HD content over wireless is incredibly slow.

I've bought some Cat 6 cable and right now my mac is wired directly into the ethernet port on the Revo but the two are not talking to each other, as soon as I switch off wireless on my mac I loose the connection with the Revo even though the two are directly connected?

Is there anything I need to configure in Ubuntu to get the connection to work?

Thanks for any help.

---

### Post by Iowan on 2010-02-14
> **JUICE690 said:**
> I've bought some Cat 6 cable and right now my mac is wired directly into the ethernet port on the Revo but the two are not talking to each other...First - are you using a crossover cable? Some 1000M cards can auto-configure, but most others don't. [This]("http://ubuntuforums.org/showthread.php?t=218630") How-To is about FTP via ZeroConf (avahi). Otherwise, you'll need to set up a simple network between the two machines - probably static addresses.

---

### Post by JUICE690 on 2010-02-14
> **Iowan said:**
> First - are you using a crossover cable? Some 1000M cards can auto-configure, but most others don't. [This]("http://ubuntuforums.org/showthread.php?t=218630") How-To is about FTP via ZeroConf (avahi). Otherwise, you'll need to set up a simple network between the two machines - probably static addresses.
It doesn't state it's crossover on the box, it reads 'Cat 6 Patch Cable for networking' so I'm not sure if it is or not.

I think my imac can auto-configure, not sure about the revo.

Thanks for the link I'll have a read through that now, will FTP be fast enough to stream HD though?

---

### Post by Iowan on 2010-02-14
I haven't used FTP often - streaming even less - HD (what's that? :) )
The link was more for the Zeroconf information.
If you hold the two cable ends beside each other, a straight patch cable will have the came wire color sequence - a crossover will not. [Here]("http://www.google.com/imgres?imgurl=http://www.tectoolz.com/allMyContent/networking/ethernetpinouts/crossover-GB.png&imgrefurl=http://tectoolz.com/cms/%3Fq%3Dtaxonomy/term/24&h=258&w=308&sz=13&tbnid=fxLd5F1YkvpsVM:&tbnh=98&tbnw=117&prev=/images%3Fq%3Dcrossover%2Bpinout&usg=__WS_0aBGtLkMwp4gM_OgO5DWKyEA=&ei=jRx4S5eRF4XeNfrpjbkP&sa=X&oi=image_result&resnum=6&ct=image&ved=0CBwQ9QEwBQ") is a picture.

---

### Post by oldfred on 2010-02-14
Years ago I did the cross over cable, but then a found a cheap hub and did not have to worry about cables. Now even switches are relatively cheap $20, but it  may pay to buy a wireless router.
[http://www.google.com/products/catalog?hl=en&q=ethernet+hub+4+port&ved=0CC8Q8wIwAg&cid=16632683598900104291#p](http://www.google.com/products/catalog?hl=en&q=ethernet+hub+4+port&ved=0CC8Q8wIwAg&cid=16632683598900104291#p)

---

### Post by JUICE690 on 2010-02-14
I was using non cross over cable! (and yes I do feel a little stupid:D) 6+ hours I was trying to network the two computers!

Thanks for you help :)

---

### Post by JUICE690 on 2010-02-15
Well today I went out and bout a Netgear 5 port gigabit switch [http://www.netgear.com/Products/Switches/DesktopSwitches/GS605.aspx ]("http://www.netgear.com/Products/Switches/DesktopSwitches/GS605.aspx")thinking this would solve my problems. I bought another cat6 cable, plugged my mac into one of the ports and the Revo into the other, two port lights on the netgear port lit up to show there was a connection) but I still can't connect the two computers... :(

As soon as I switch off wireless on either the Revo or the mac I loose connection between them, even though there are now both wired into the gigabit switch.

I'm at a loss on what to do, I know Macs fairly well but i'm very much a noob when it comes to ubuntu.

Any ideas on what I may need to do? Indecently I'm not plugging a modem/router into the ethernet switch, I'm purely using this to network my two computers, at least until I get over this first hurdle.

---

### Post by Iowan on 2010-02-15
Now it becomes more of a network setup problem. I can't help much with the Mac - but on the Ubuntu, check **ifconfig -a** if eth0 shows no address, we'll need to give it one - preferably in the same subnet as the Mac (what address is it's ethernet card using?).

---

### Post by JUICE690 on 2010-02-15
ifconfig -a got these results on ubuntu

eth0   Link encap:Ethernet  HWaddr 
          inet6 addr: fe80::222:68ff:fe66:6f6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:71769 (71.7 KB)
          Interrupt:23 Base address:0x8000 

My macs ethernet address is



**Updated (thanks oldfred!)**

---

### Post by oldfred on 2010-02-15
Those are hardware addresses. I would not post as someone can spoof a hw address and look like you. I had trouble switching computers before I had a router and comcast took 20 minutes to recognize the new computer, so I spoofed my mac address and everything worked immediately.

You can assign address from ifconfig but I find it easier now to use system, preference, network connections (in 9.10 maybe something else in other versions). You need to assign one address to you Mac and another to your Ubuntu.

Attached is a screen shot of my fixed IP on my desktop. It is for connecting to my router so I am not sure all the settings are required. The last two digits should be different for your other computer.
i.e. 192.68.1.20 & 192.68.1.21

---

### Post by Iowan on 2010-02-15
That's also your mac's MAC (hardware) address. The IP address (as mentioned) should look something like 192.168.0.5 - another option for addressing is to configure static address in */etc/network/interfaces*.
 I haven't tried setting up IPv6 networking yet ( that's the fe80::...).

---

### Post by JUICE690 on 2010-02-16
Well I got the two connected using oldfreds instructions! lightning fast file sharing, 100mb went across before I had time to blink.

Then this morning I switched both on and the connection was lost, so close...

I'd set up a static ip address on my macs ethernet connection, 192.168.2.5

My Revo's static ethernet address is 192.168.2.6

Any idea why it would have been working and then just not? also I noticed that when I first booted my Revo this morning I had to manually connect the wired connection via network manager, the wireless connects automatically. Can both be set to start up automatically?

Thanks for your time by the way, really appreciate your help with this.

---

### Post by JUICE690 on 2010-02-16
Slight update & progress...!

My Revo now connects to the imac using ethernet so file transfer etc is perfect.

The knock on effect of this is that having a wired connection & a wireless connection running simultaneously breaks my internet connection. If I disconnect the wired link via network manager internet springs back into life. I'm guessing that the wired connection is overriding the wireless one?

---

### Post by Iowan on 2010-02-16
That may be a function of NM - previous versions (at least) would only manage one active interface (although my Jaunty laptop has had wired/wireless active at the same time. It was normal to set up one interface via **/etc/network/interfaces** (usually the wired one).

---

### Post by JUICE690 on 2010-02-16
> **Iowan said:**
> That may be a function of NM - previous versions (at least) would only manage one active interface (although my Jaunty laptop has had wired/wireless active at the same time.

You'd think with mine running on Karmic Koala that it would be able to do the same.
> **Iowan said:**
> 
It was normal to set up one interface via **/etc/network/interfaces** (usually the wired one).

Would you mind explaining how I'd go about doing that? I have the interface file open, right now mine just says:

[B]auto lo
iface lo inet loopback[/B]

My Revo's ethernet address is 192.168.2.7
Broadcast address: 192.168.2.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.2.8
Primary DNS: 192.168.2.8

---

### Post by Iowan on 2010-02-16
You can always "comment out" (#) or delete these changes if they don't work.
Use **sudo -e /etc/network/interfaces** (or if you'd prefer a graphical editor: **gksudo gedit /etc/network/interfaces**) to make the file look:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.7
netmask 255.255.255.0
#network 192.168.2.0
#broadcast 192.168.2.255

```
The last two lines are probably unnecessary - so they're commented out already. With only the one machine on the network, you probably won't need the gateway or DNS server. Save the changes and restart or reboot (I prefer a reboot to re-sync networking and NM).

One caveat I just realized - if wireless is also using the 192.168.2.0 network, this may not work. Two interfaces in the same subnet plays havoc with routing... But, you could change the wired addresses on both machines to a different subnet - say... 192.168.3.0

---

### Post by JUICE690 on 2010-02-16
With the following settings:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.3.0
netmask 255.255.255.0
#network 192.168.3.1
#broadcast 192.168.2.255

I don't get any ethernet networking. I have my internet connection back. I've tried uncommenting network & broadcast (is network another description for default route?) but still no joy.

---

### Post by JUICE690 on 2010-02-16
Oh, hold up, it seemed to just kick into life, I'm just rebooting both machines now to see if it continues working...

---

### Post by JUICE690 on 2010-02-16
Just realised it was networking via wireless! As soon as I switched off the wireless connection I lost the network to the mac (and vice-versa)

Darn.

---

### Post by Iowan on 2010-02-16
I saw a thread awhile back that used a gateway of 0.0.0.0
"network" is the subnet "base"  - usually ends with .0
"broadcast" is usually the other end - the highest address in the subnet. With subnet mask of 255.255.255.0 (CIDR notation is /24), that address would be .255 
Your machines could use any addresses excluding those two. Routers usually use .1, but you won't have one. 
As an example:```
auto eth0
iface eth0 inet static
address 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
gateway 0.0.0.0
```
No guarantees that this'll work either - last line in particular. You'll also need to set up the other machine in the same (192.168.3.X?) subnet.

---

### Post by JUICE690 on 2010-02-16
I've put those settings into my network file, just to clarify, which of these fields should I fill out on my mac?

To obtain the connection prior to trying these steps I just had to enter the static i.p you can see.

---

### Post by JUICE690 on 2010-02-16
Iowan, thanks for all your help. I'm going to call it a day on getting this to work, the two machines connect using ethernet at high speed and that's what I set out to do.

Really appreciated yours and oldfreds time helping me out.;)

---

### Post by bigspottycat on 2010-03-05
There is a known problem with the wireless card on the Revo causing incredibly slow transfer speeds:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369005]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/369005")

This could also account for the way it was interfering with your wired connection. I'm searching for a solution and will post back if I find it.

[http://ubuntuforums.org/showthread.php?t=1378485]("http://ubuntuforums.org/showthread.php?t=1378485")

---

### Post by Charly85551 on 2010-03-06
I have been following your conversations on this topic and I was a bit surprised that I never saw any comment about two machines being connected with  2 different routes in parallel. The basic rules for network connections do not allow this since there is no rule or logic to decide which way to go and it may end up in permanent cycles of messages on the network. 
Just a little advice for future problems!;)

---

