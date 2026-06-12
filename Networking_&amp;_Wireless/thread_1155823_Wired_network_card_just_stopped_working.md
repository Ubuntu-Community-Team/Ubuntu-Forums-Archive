---
title: "Wired network card just stopped working?"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by lesaurus on 2009-05-11
Please help me,
I made a fresh install of jaunty 9.04 recently and everythings been fine for a couple of weeks.
Today the network connection has stopped working. Just shows symbol of two computers with a red cross in the top bar.
Tried reseting my linksys router but no good.
I have tested the network upto the end of the cable that plugs in the back of my pc by just pluging it into my netbook that also runs ubuntu 9.04 but for netbooks. The network settings are identical apart from obviously the mac address of the nic.

If i type in ifconfig from the terminal i get this

eth0      Link encap:Ethernet  HWaddr 00:07:e9:e0:bf:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14268 (14.2 KB)  TX bytes:14268 (14.2 KB)



It doesnt seem to pick up any ip, gateway etc.

I am totally new to linux and completely lost as to how this has happened and what i should do to fix it.

Thanks Paul

---

### Post by Peter09 on 2009-05-11
Some laptops have a hardware switch to turn off the wireless connection - worth checking it.

Otherwise can you post the output of

```
lshw -C network
```

---

### Post by Peter09 on 2009-05-11
Also for a hardwired network.

Look at the plug where your network cable is inserted. There should be some lights - normally green, may be flickering, what state are they in?

---

### Post by lesaurus on 2009-05-11
Hey thanks but just to clear up - It is my PC not laptop that is the problem and the wired connection not the wireless.

Here is the output of lshw -c network

paul@PC:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:e0:bf:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:8b:27:a3:31:10
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
paul@PC:~$ 

Thanks paul

---

### Post by Peter09 on 2009-05-11
As above check the lights on the card

---

### Post by lesaurus on 2009-05-11
well there doesnt seem to be a card as such its a dell dimension 4550 and the NIC i think is built into the mother board. There doesnt seem to be any 'lights' its just a hole to plug into.

Does the report above not say whether the card is found or not?

---

### Post by Peter09 on 2009-05-11
Yes your card is found but with no lights its suggests you have a hardware fault. Do


[LIST]
[*]check the cable is plugged into the router properly
[*]check the cable is plugged into the PC properly.
[*]replace the cable.
[*]swap ports on the router
[/LIST]

---

### Post by lesaurus on 2009-05-11
as i said I know the cable is working right up to the PC coz I can unplug it from my pc and plug it into my netbook and it works fine - the net book is also running ubuntu 9.04 remixed and the network settings are exactly the same.

---

### Post by Peter09 on 2009-05-11
This suggests that its your NIC connection then.

You card is shown ok by the lshw -C network bit

> description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:e0:bf:c4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yesbut ifconfig show no active connection

> eth0      Link encap:Ethernet  HWaddr 00:07:e9:e0:bf:c4  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) You could try to confirm this by booting a liveCD. This will use a fresh set of drivers.
However the lights on an you card should be on - even when the machine is powered down (not powered off)

---

### Post by Peter09 on 2009-05-11
Just a though - have you been into your BIOS of late - if its an onboard card it can be disabled from the BIOS. May be worth a look.

---

### Post by lesaurus on 2009-05-11
looking at the back of the pc all the lights are on - dont know if they are anything to do with the card but every single light that could be on is.

I have lent the live boot cd to a friend :-( is there any other way to get the drivers for the NIC can i get them from synaptic manager on my net book and then transfer to my PC via usb?

---

### Post by Peter09 on 2009-05-11
Your NIC lights will be very close to the wired connector. If you are on an active network they will flicker, like your router lights.

Also is the light where you connect to your router on, the port light should be alight.

---

### Post by lesaurus on 2009-05-11
well the lights on my router are not on when connected to my PC but it isnt an active network, its not working so i am assuming it should be  this way.
When i plug the network into my netbook, yes the lights flicker coz that works.
there are only four lights on the back of the whole pc labelled a b c d and all of these are on.

---

### Post by Peter09 on 2009-05-11
No - when you plug into the router port, if it detects the card at the other end it should light up. The light goes out when traffic passes through.

Having no light there is 'bad' - your NIC is 'doomed'

---

### Post by lesaurus on 2009-05-11
ok when i plug my working netbook in, the router lights up on that port and stays lit, occassionally flickering.
When i plug my PC in there are no 'port' lights on the router showing.

So you would say this is a hardware issue then, my cards just died?

---

### Post by Peter09 on 2009-05-11
Yes - I think it is deceased, dead, kaput

---

### Post by lesaurus on 2009-05-11
Is there any way to install new drivers for the NIC? as a last ditch attempt before i go and try to buy a new motherboard/pc?

---

### Post by Peter09 on 2009-05-11
You do not need to buy a new motherboard unless there are other problems. Go an buy a new ethernet card (NIC) its easy to fit into your machine (unless its a laptop or similar). Not sure where you live but in the UK they are about £14.

---

### Post by lesaurus on 2009-05-11
I have a dell dimension 4550 and i think it has an integrated NIC  :-( - oh well it might just finally be the time to buy an upto date PC. :-)))))))
Thanks for youre help you are very kind

---

### Post by Peter09 on 2009-05-11
Just to say that it does not matter if it is integrated NIC, putting a new card in is still ok, no problems. Even if you get a new PC it would be worth recovering that one and using it as a server or backup or something.

---

### Post by Iowan on 2009-05-11
I just had similar problem with laptop wired card.  Before you pitch the card, try setting up a manual address either in */etc/network/interfaces* or by using **ifconfig** to set an address and netmask, then try pinging another machine.  I found my card is working - just not getting DHCP address (but works properly in Windows).

---

### Post by lesaurus on 2009-05-12
Could you please be a little more detailed, like i said i am totally new at linux and dont have a clue what im doing.when i do ifconfig it doesnt show any gateway or ip or anything.

If i go to etc/network/interfaces it just says

auto lo
iface lo inet loopback

is this right, what do i type in here and how do i ping?

---

### Post by Iowan on 2009-05-12
Sorry for lack of details - didn't wanna bore you with stuff you might already know, but certainly don't mind filling in some details.  Your /etc/network/interfaces file looks normal. I edited mine to look something like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1

```I'm not sure what address your router uses - or what range it's dhcp server uses for leases.  You will want your static address OUTSIDE this range.  This arrangement probably won't get you internet access unless you manually edit /etc/resolv.conf to put in your DNS server... but it should let you see if the card works.  If it does, there's hope.

---

