---
title: "Help- mythbox won't connect to internet"
date: 2009-03-25
forum: Mythbuntu
---

### Post by itlarson on 2009-03-25
I hesitate to post this here, since technically it's a networking problem, but it is a mythtv computer, and this forum seems to have a depth of talent, so here goes:
  Monday morning I found I had no internet on my mythbox.  I hadn't made any changes to the machine in the preceding days.  Three days of scouring the internet and forums have produced no improvement.  I have dragged my other computer upstairs to verify the connection is good, and pulled a DVB card to insert a network card, in case the on board hardware was bad.  Still no change.  Here is the output from when I had the second network card installed:

```

itl@mythbox:~/Config$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:9e:7e:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:18:4d:6f:3f:ba  
          inet6 addr: fe80::218:4dff:fe6f:3fba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56252 (56.2 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:16 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2704 (2.7 KB)  TX bytes:2704 (2.7 KB)


itl@mythbox:~/Config$ ping 206.190.60.37
connect: Network is unreachable
``` 

Since I only have a week and a half of schedule info left, I am getting desperate!  Please help!

---

### Post by theophile on 2009-03-25
Is networkmanager running? If you right-click on the applet, is networking enabled?

---

### Post by itlarson on 2009-03-25
If I right click on the network applet the "enable networking" box is checked.  If I disconnect then reconnect a balloon pops up saying the network has been disconnected.  I can ping lo (127.0.0.1), but for any outside address it says "network unavailable".  It seems like the cable isn't connected, but it is, and I tested it to make sure it is good.

---

### Post by 4dognight on 2009-03-26
Looks like the network card you added(eth1) is working. eth0 I assume is your onboard NIC. It doesnt have an IP address assigned. Do you use DHCP or static IP addresses?  Worst case, you could disable the onboard and use the addon card.

---

### Post by klc5555 on 2009-03-26
> **itlarson said:**
> If I right click on the network applet the "enable networking" box is checked.  If I disconnect then reconnect a balloon pops up saying the network has been disconnected.  I can ping lo (127.0.0.1), but for any outside address it says "network unavailable".  It seems like the cable isn't connected, but it is, and I tested it to make sure it is good.

Neither eth has an ip address assigned to it. No netmask either. Can't get anywhere that way.

There are a couple of possible diagnostic/workaround avenues available. 

1) If your range of ip addresses is assigned by a home router with DHCP, or if you had been using a static ip, you could see whether you can get the interface operating by assigning the appropriate information manually, e.g.:

sudo ifconfig eth0 172.30.49.13 netmask 255.255.255.0 up

Assuming eth0 is the one with the cable. Substitute an ip address in your particular range (if you're behind a home router it'll likely be something in the 192.168.x.x range or the 10.x.x.x range, with a netmask of 255.255.255.0 or 255.255.0.0) 

If the interface seems to be alive, you can see whether it can connect to your gateway's ip address by giving a route there:

sudo route add default gw 172.30.49.1 

Substitute your gateway's actual address. If you have got this far, you ought to be internet-connected. Kill the 2nd eth, the one you don't have a cable connected to, by:

sudo ifconfig eth1 down

Assuming eth1 is the unconnected one. 


2) Or, if your machine was supposed to be getting addresses dished to it from a home router or (shudder) your ip provider, the question would be why isn't your eth interface getting this information dished to it. I'm not in front of an Ubuntu machine at the moment, but presumably the dhcp client your machine would be using is dhcpcd, which you could run manually just to see whether it works or errors out, i.e.:

sudo dhcpcd

defaults to eth0; or, if your "live" interface is eth1, then:

sudo dhcpcd eth1

Note that if the command yields you an address, it will also rewrite your /etc/resolv.conf with the dhcp server's supplied dns information. The earlier one is saved as resolv.conf.sv

If neither of these diagnostic avenues discovers anything worth following up, then there may be something more fundamental amiss.

Cheers!

---

### Post by kpatz on 2009-03-26
When you plug a live cable into the motherboard's ethernet jack, do any LEDs light up?

Try a different cable.  Sometimes cables and jacks don't get along.

Finally, plug the cable in, and then issue these two commands:

```
sudo ifdown eth0
sudo ifup eth0
```

and then do ifconfig eth0 and see what you get.

If you see "RUNNING" in the list, then you know the interface is working.  If "RUNNING" is missing while it's up, then it thinks the cable is disconnected.

---

### Post by itlarson on 2009-03-26
Thanks everyone, I have been pulling my hair out over this one.  I will try the dhcpcd thing this evening, as I am 90% sure comcast doesn't use static IP addresses.  By the way how can I tell this?  I have tried the ifon/ifoff thing or something similar with no effect.
  Note on hardware configuration:  I have pulled eth1, since I need the slot for a DVB card.  I am not using my router, since it quit working at the same time, I have been swapping cables between my two computers.  I am considering buying a new cable, despite the fact my other computer connects through this one just fine.  Also, I'm going to try booting with a live CD, to see if I have internet then.  The weird is that this just happened, I didn't make any changes to the system before this  happened.

---

### Post by klc5555 on 2009-03-26
> **itlarson said:**
> Thanks everyone, I have been pulling my hair out over this one.  I will try the dhcpcd thing this evening, as I am 90% sure comcast doesn't use static IP addresses.  By the way how can I tell this?  I have tried the ifon/ifoff thing or something similar with no effect.
  Note on hardware configuration:  I have pulled eth1, since I need the slot for a DVB card.  I am not using my router, since it quit working at the same time, I have been swapping cables between my two computers.  I am considering buying a new cable, despite the fact my other computer connects through this one just fine.  Also, I'm going to try booting with a live CD, to see if I have internet then.  The weird is that this just happened, I didn't make any changes to the system before this  happened.

Comcast uses dhcp, except in some special circumstances where a customer requires a static ip. Older versions of dhcpcd occasionally would have difficulties obtaining a lease; in some cases I've had to power down the cable modem for 30 seconds, then power it up and run dhcpcd. But I haven't ecountered this problem for 5 years or so.

More to the point, Comcast registers the hardware MAC address not only of your cable modem itself , but also of the ethernet device immediately downstream from the cable modem --the router, if you have/had one, or if a PC is plugging directly into the cable modem, then the MAC address of its connected ethernet device. (In other words, of any device that gets an internet-routable ip address from Comcast). If the myth machine is connecting straight to the ethernet port on your cable modem, and the hex MAC address of its connecting ethernet device has not been registered with your friendly Comcast service rep over the phone, then it ought not to be able to connect to dhcp. By design.

That's how Comcast charges for a 2nd and subsequent ip address: if your immediate connecting device doesn't have a MAC address in their database, it doesn't connect. 

Get a new router, plug it into your cable modem, and then get on the horn and register the router's MAC address with Comcast while clearing out any obsolete MAC's they may still have on file (and will continue to charge you for). Then power down your cable modem for a couple of minutes, power it back up, and your router should connect and get an ip. Your two (or more) PCs downstream of the router on your private network will then be fine.

---

### Post by kpatz on 2009-03-26
What klc5555 said is correct, Comcast will only dole out one IP to one device at a time connected to the modem (unless you're paying for more than one IP on your account), therefore, you're going to need a router.

But you don't have to call Comcast when you switch devices or add a router.  Just power-cycle the modem before connecting the router so it "forgets" the original CPE MAC, and it will automatically accept the new CPE MAC.

In the meantime, if you want to get your myth box's schedules updated, power-cycle your modem, then connect it to the myth box's Ethernet port.  Cycle ifdown/ifup on the Myth box so it gets an IP.  Run mythfilldatabase.  When it's finished, disconnect the Myth box from the modem, power-cycle the modem again, and then reconnect your regular desktop back up to it.  Obviously, getting your hands on a router is much easier.

---

### Post by klc5555 on 2009-03-26
> **kpatz said:**
> What klc5555 said is correct, Comcast will only dole out one IP to one device at a time connected to the modem (unless you're paying for more than one IP on your account), therefore, you're going to need a router.

But you don't have to call Comcast when you switch devices or add a router.  Just power-cycle the modem before connecting the router so it "forgets" the original CPE MAC, and it will automatically accept the new CPE MAC.

In the meantime, if you want to get your myth box's schedules updated, power-cycle your modem, then connect it to the myth box's Ethernet port.  Cycle ifdown/ifup on the Myth box so it gets an IP.  Run mythfilldatabase.  When it's finished, disconnect the Myth box from the modem, power-cycle the modem again, and then reconnect your regular desktop back up to it.  Obviously, getting your hands on a router is much easier.

Wow! Been five years or so since the last time I blew up a router --things have obviously gotten a lot easier in Comcast Land! It will be a relief the next time my router is nuked not to have to spend an hour on the phone to connect the darn thing.

Cheers! :)

---

### Post by itlarson on 2009-03-26
Thanks everyone- I will buy a new router tonight and try to get a connection.

---

### Post by itlarson on 2009-03-27
You guys rule-  I didn't realize you can't just swap the ethernet cables on two machines.  I got a new router last night and everything works great.

---

