---
title: "Internet sharing wifi connection through ethernet via cat5"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by UnsafeData on 2011-09-25
I have an imac g3 and I want to hook it up in my room. Router is in the other room and I don't have a cable long enough to hook it up directly to it. If I did internet sharing with my wireless Windows 7 laptop and hooked up a CAT5 directly from that laptop to the iMac G3, it works fine with little configuration. 

I followed [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) this and it didn't work at all. In nm-applet, under Wired Networks it just says "Disconnected" and it won't work at all. I don't want a crossover cable, it worked fine in Windows and I don't want to buy one anyways. I can't find any steps to help me get this working..

---

### Post by UnsafeData on 2011-09-26
bump

---

### Post by HereInOz on 2011-09-26
The easiest way is to get a cheap wireless access point, connect it to the router, and go from there.

To use the wireless connection in the Windows 7 machine you would need to create a bridge between the wireless connection and the Ethernet connection, then create an ad-hoc connection between the wireless on the Win7 machine and the G3, with the Win7 machine providing internet gateway services, and I am not sure that this is going to be achievable.

Spend a bit of money and set up a proper wireless network, and it will be better in the long run.

---

### Post by UnsafeData on 2011-09-27
I should rephrase my original post.

I meant that internet sharing worked fine *from* Windows 7 with no problems. Internet sharing doesn't seem to be as easy when I do it from Ubuntu.

I don't want to buy anything to make it easier I just want to use what I have.

---

### Post by jonobr on 2011-09-27
Hello


I had reason to play around with Windows 7 ICS between a Pantech UML 290 on the WAN and a ethernet interface on the lan to my 'home network' devices.

I found from a positive point of view , ICS in windows 7 worked easily and well,
however, you may find if you start to expand your network and possible renumber it, its going to let you down.

Anyway, to your problem, the Ethernet interface saying its disconnected,
Did it say this before you started?
Are you sure that this Ethernet interface is getting or has an IP address.

---

### Post by UnsafeData on 2011-09-27
> **jonobr said:**
> Hello


I had reason to play around with Windows 7 ICS between a Pantech UML 290 on the WAN and a ethernet interface on the lan to my 'home network' devices.

I found from a positive point of view , ICS in windows 7 worked easily and well,
however, you may find if you start to expand your network and possible renumber it, its going to let you down.

Anyway, to your problem, the Ethernet interface saying its disconnected,
Did it say this before you started?
Are you sure that this Ethernet interface is getting or has an IP address.
I wish it was as easy as Windows 7..

It said this before I started, but I thought this was because it wasn't connected to anything yet. Then when I enable internet sharing and plug the other end of the cable to another computer it still says it's connected and it doesn't work.

ifconfig shows

```
eth0      Link encap:Ethernet  HWaddr 00:0c:76:04:80:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

In Network Connections, under 'Last used' it says **Never**.

---

### Post by jonobr on 2011-09-27
Hey


I think the problem is that you have nothing assigned to that interface,

In ICS, I recall it gave the ethernet interface an IP address of 192.168.137.1 and supplied dhcp address in that subnet to the devices.

Your ethernet interface is not showing any IP address so im figuring the guide you looked at either expects that interface to have an ip address, or it is going to be assigned an interface through DHCP>

I am guessing what you should do given your setup is to setup your eth0 through the gui to have a static ip address
when you do that rerun ifconfig and it hopefully will show the eth0 interface up

---

### Post by UnsafeData on 2011-09-27
> **jonobr said:**
> 
I am guessing what you should do given your setup is to setup your eth0 through the gui to have a static ip address


Could you explain how? I've never had to do this before so I don't know how

---

### Post by jonobr on 2011-09-27
I usually use cli to change address
but [Here]("http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/") is a simple howto.

When you restart your machine
you should (hopefully) eth0 has the ip address there (the values used in the example should be ok for your system to

Hopefully with ICS setup as in the other howto you refreenced , restarting the other machine should be all thats required 

hopefully............

---

### Post by UnsafeData on 2011-09-27
That article is dated. Is that now under Network Connections? There's no Static IP setting in there

EDIT: 

A cli would be fine for me if there's no way in GUI

---

### Post by jonobr on 2011-09-27
Yikes , goes to show how much I GUI

To change from dynamic to static 
look below
I have "iface eth0 inet dhcp" commented out , this is most likely your current setting.

Comment that out by putting a hash infront, therefore its not read.
From the line "iface eth0 inet static" on, i define the static IP info.

With this setup you can comment and uncomment to change the IP mapping from static to dynamic
No harm making a backup of the interfaces file before you start,
You can stop and start networking, however, I prefer to just restart



```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.0.1
    network 192.168.1.0

```

---

### Post by UnsafeData on 2011-09-27
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1

```

I just have the same address and gateway as wlan0, is this how it should be? Also I have an address in eth0 now 

```
eth0      Link encap:Ethernet  HWaddr 00:0c:76:04:80:94  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by jonobr on 2011-09-27
Nope that will cause an ip address conflict,

I recommend for the moment 
```
address 192.168.1.106 (or something unique on your network)
    netmask 255.255.255.0
    broadcast 192.168.1.255
    network 192.168.1.0
```

leave out gateway for a second

Also, when you say the same as wlan0, just to double chack, your
using wlan0 to connect to the internet and should be getting an IP address different to 192.168
You are connecting the other machine to this one using wired, correct?

---

### Post by UnsafeData on 2011-09-27
Oh, wlan0 has 192.168.109 not 192.168.1.106

And yes. My iMac G3 is running Linux PPC, the router is in the other room and I have no cable long enough to connect it to that router (and wire mess is terrible) so I'm connecting it to this PC.

So I should use 192.168.1.10 or something else?

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.111
broadcast 192.168.1.255
netmask 255.255.255.0





```

---

### Post by jonobr on 2011-09-27
You need to use something that is not in use on your network already.

It would be more ideal to set the DHCP range on your router to hand out address from efg 192.168.1.2 to 192.168.1.100 and that would leave 101 -254 available for what your doing now.

Anyway thats for testing.

I would recommend you set the ip to a temporary number such as eg 222
ping that on your connected machine first to ensure its not already in use.

Also, I dont want to distract you too much from what your doing there, but given your ip allocation , you need to be bridging and not ICS sharing
(windows also allows bridging) , 
[Here]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html#bridging") is briding info for 10.04

---

### Post by UnsafeData on 2011-09-27
I didn't need to bridge to do this on Windows. Do I still have to do it on Ubuntu though?

---

### Post by jonobr on 2011-09-27
ICS was setup to connect a home network with multiple machines to the wan, 
they -by default- allocated a 192.168.137.x address to your home networked machines. 

In ICS your going from one network address (192.168.137.x) to 192.168.1.x) so you are routing across the interim machine.

If your going from a 192.168.1.x to a 192.168.1.x address then thats bridging as there is no routing involved.

You have two options,

You could setup the eth0 interface to a difference address range and use the sharing 

or, 

you could keep it in the 192.168.1.x range and bridge.

If it was my network , I would most likely bridge.

---

### Post by AEiMBAK on 2011-09-27
try to set the gateway on your iMac to the IP of your eth0 on the ubuntu PC like:

iMac:
ip: 192.168.1.102
mask:255.255.255.0
gate:192.168.1.101

ubuntu eth0:
ip:192.168.1.101
mask:255.255.255.0

---

### Post by UnsafeData on 2011-09-27
> **jonobr said:**
> You could setup the eth0 interface to a difference address range and use the sharing 

I'd like to do that.

---

### Post by UnsafeData on 2011-09-27
> **AEiMBAK said:**
> try to set the gateway on your iMac to the IP of your eth0 on the ubuntu PC like:

iMac:
ip: 192.168.1.102
mask:255.255.255.0
gate:192.168.1.101

ubuntu eth0:
ip:192.168.1.101
mask:255.255.255.0
I tried this but I still have no connection. Is there anything else I need to do with this

---

### Post by UnsafeData on 2011-09-28
Bump

---

### Post by AEiMBAK on 2011-09-28
Try this; Network Connections->Select Auth eht0 - click edit
IPv4 Settings->Method=Shared to other computers

---

### Post by UnsafeData on 2011-09-28
> **AEiMBAK said:**
> Try this; Network Connections->Select Auth eht0 - click edit
IPv4 Settings->Method=Shared to other computers

I mentioned in my first post that this doesn't work. Does it even work for other people in my situation

---

### Post by AEiMBAK on 2011-09-28
It dose work for me and here is my setup:
WiMax USB Modem connected to ubuntu (Internet Connection) - eth1
LAN - eth0 - shared to other computers - connected to a wireless router
wirless router is set to get ip by dhcp but with dns as 8.8.8.8 8.8.4.4
any computer connected to the router has internet access

So in you case just change the dns of the imac to
8.8.8.8
8.8.4.4

---

### Post by jonobr on 2011-09-28
Ok, so stupid question, can you ping on the machine in the middle to both connections ends, to the router on one side and to the other machine on the other end?

I figure the reason why AEiMBAK is working is becuase on the wlan0 end there is an ISP IP address going to a private network and your box in the middle will route the pacts
UnsafeData's network has 
192.168.1.x on one side and 192.168.1.x on the other so the machine in the middle will not route that as it will think those packets are for the network it came from and do nothing.

I hate to sound like a broken record, but one of two things will sort this,

bridgind through the machine in the middle, or setting up a different network address space on your end.

I also figure is you have this setup

router<===>ubuntu<====> machine a

You can ping from machine a to ubuntu
You can ping from router to ubuntu
however, only one of the following will work,
either ubuntu to router or ubuntu to machine a.

but thats just a guess

---

### Post by UnsafeData on 2011-09-28
Middle computer seemed to ping to both but the iMac, the computer I want to share to, can't ping to anyone.

---

### Post by AEiMBAK on 2011-09-28
When you use the shared to other computers method, your eth0 will be assigned a static ip
ip: 10.42.43.1
cast: 10.42.43.255
mask: 255.255.255.0

so it will be different ip range from your wlan0.

set you imac to get ip by dhcp and if there is no internet access try changing the dns on imac to
8.8.8.8
8.8.4.4

by this setting you can not ping from imac to ubuntu wlan0 ip but you can ping the eth0 ip 10.42.43.1
which would be your imac's gateway

---

### Post by UnsafeData on 2011-09-29
Do I comment out everything else if I set it to dhcp?

Like:

```

eth0 lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#address 192.168.1.113
broadcast 192.168.1.255
netmask 255.255.255.0
gateway 192.168.1.112

```

This is eth0 from the PC I'm sharing from
```

eth0      Link encap:Ethernet  HWaddr 00:0c:76:04:80:94  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by AEiMBAK on 2011-09-29
on the PC you are sharing from, use Network Connections->Select Auth eht0 - click edit
IPv4 Settings->Method=Shared to other computers

on imac if there is no network manager then comment all
```

eth0 lo 
iface lo inet loopback
  
auto eth0 
iface eth0 inet dhcp 
#address 192.168.1.113 
#broadcast 192.168.1.255 
#netmask 255.255.255.0 
#gateway 192.168.1.112
```

---

### Post by UnsafeData on 2011-09-29
Says dhcpcd failed

Also under nm-applet on my Ubuntu PC it now says "device not managed" under Wired connections.

---

### Post by AEiMBAK on 2011-09-30
On the ubuntu pc, it should say Connected. If you have edited the interface manually, undo any edits,
and follow the steps again.

On iMac type in terminal(as root): dhcpcd eth0

---

### Post by UnsafeData on 2011-09-30
It says dhcpcd command not found
here is my interfaces file on ubuntu 
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.112
broadcast 192.168.1.255
netmask 255.255.255.0




```

---

### Post by UnsafeData on 2011-10-01
Bump

---

### Post by AEiMBAK on 2011-10-01
ok my interface file on ubuntu is
```

auto lo
iface lo inet loopback

```I mean there is no entry for eth0 and thats when eth0 set to be shared with other computers

What distro on the iMac?

---

### Post by UnsafeData on 2011-10-01
Debian

---

### Post by UnsafeData on 2011-10-03
Bump

---

### Post by UnsafeData on 2011-10-05
bump

---

### Post by AEiMBAK on 2011-10-05
edit your debian interface file to
```

auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

and ubuntu one to
```

auto lo 
iface lo inet loopback

```

restart both and then configure the ubuntu to share the internet through setting
the eth0 to "Shared to other computers" in Network Connections

---

### Post by UnsafeData on 2011-10-06
Doesn't work

also Still says "Device not managed" in nm-applet on Ubuntu.. still says "Auto eth0 Last used: never" too.. 

This is frustrating, am I doing something wrong?

---

### Post by AEiMBAK on 2011-10-06
I guess you did something in your prevues tries. If you can undo any change you done, it might work
because om my setup, it works with no problems and I didn't need to change any file manually,
I did it all through Network Connections

---

