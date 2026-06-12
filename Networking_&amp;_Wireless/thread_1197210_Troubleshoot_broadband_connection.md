---
title: "Troubleshoot broadband connection"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2009-06-25
So COX said it would be 2 weeks before they could send a tech out and that's to long for me.  I've replaced my motorola modem with a zoom, the cable from the modem to COX's cable coming in, and the double male connector between the two.  Is there any way I can check my NIC???

So far if I disconnect the cable from the back of the modem and wait a few seconds before attaching it again I can most of the time reestablish a connection to the internet, but not all of the time.  I'm dual boot and the same thing happens in Win XP Pro.  This discounts any upgrades that have taken place.

Any log files anywhere that can point the finger at COX???

Thanks all,
Barrie

Edit:  woops, I know the card is working...

eth0      Link encap:Ethernet  HWaddr 00:11:95:22:d9:26
          inet addr:70.173.xxx.xxx  Bcast:70.173.xxx.xxx
          Mask:255.255.252.0 inet6 addr: xxxx::xxxx:xxxx::xxxx/64
          Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1797 errors:0 dropped:0 overruns:9 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3106581 (2.9 MB)  TX bytes:553749 (540.7 KB)
          Interrupt:17 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2412817 (2.3 MB)  TX bytes:2412817 (2.3 MB)

And squid just a returned a (113) No route to host.  So, it looks as if COX is to blame.  I'm just trying to eliminate my end first.

Any ideas appreciated,
Barrie

---

### Post by MaindotC on 2009-06-25
It's difficult to show logfiles to the COX tech because even if you did the records are digital and thus could be easily falsified.

---

### Post by Barriehie on 2009-06-25
Yes, I'm just trying to eliminate my end.  I'm pretty sure it's COX; just trying to verify that.

Barrie

---

### Post by MaindotC on 2009-06-26
Judging by your ifconfig it seems that you aren't utilizing an access point to split your connection so every configurating your receiving that deals with directing traffic should be coming from COX's DHCP server.  It should be sending you the name servers, your own ip address, gateway information and so forth.  Are you having connectivity issues?

---

### Post by jonobr on 2009-06-26
Is there a way to just look at the moden and see what it aquires?

On my ATT DSL router, I have a web interface that will show me connectivity to the ISP,.
I can release the IP address and renew it,
in your case it looks like a static IP address.

Unless this is a hardware issue and Given the OS independence of the problem, its sounding to me like you need to prove that two parallel lines never meet.
i.e. its difficult to prove, but pretty obvious.

---

### Post by Barriehie on 2009-06-26
> **strAlan said:**
> Judging by your ifconfig it seems that you aren't utilizing an access point to split your connection so every configurating your receiving that deals with directing traffic should be coming from COX's DHCP server.  It should be sending you the name servers, your own ip address, gateway information and so forth.  Are you having connectivity issues?

I used iptstate and I am getting name servers, ip address, gw info, etc.  The first light to go out is the indicator for establishing a connection to COX and then shortly thereafter my upstream light goes out.  It's like their end just drops out.  Last night I found a stanford link and it says everything is good... online speed test and signal analysis.  COX called today to tell me there may be a charge for the visit so I've cancelled it and am considering a different provider.  I've had it with their lack of customer service.

Barrie

---

### Post by MaindotC on 2009-06-27
> **jonobr said:**
> Is there a way to just look at the moden and see what it aquires?

Be careful with your terminology.  A modem is a layer 1 device that simply provides a physical capability of sending electrical charges across a (usually wired) medium.  You shouldn't be able to "log into" the cable modem as it has no IP functionality.  My understanding is that he has the modem connected to his machine, so the only thing that should be dealing with DHCP information is his machine.

---

### Post by MaindotC on 2009-06-27
> **Barriehie said:**
> The first light to go out is the indicator for establishing a connection to COX and then shortly thereafter my upstream light goes out.  It's like their end just drops out.  
Barrie

This really sounds like a signal strength issue.  If you have a splitter, try and use a higher-rated frequency splitter like 1 GHZ.  Also check the gauge of coaxial cable.  One time I was having signal issues and it turned out that we were using a sub-standard grade of cable that had a much smaller bandwidth capability.

---

