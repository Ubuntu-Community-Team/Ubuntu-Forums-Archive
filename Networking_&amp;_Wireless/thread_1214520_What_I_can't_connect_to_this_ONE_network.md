---
title: "What? I can't connect to this ONE network?"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by Andorin on 2009-07-16
Facts:
-My laptop (Acer Aspire 5570z) generally doesn't have any trouble with connecting to wireless networks.
-When I open wicd and click Connect on my home network, it hangs on "Obtaining IP address" and then aborts after a few minutes.
-The home network is not secured.
-The home network is not using MAC filtering.
-The laptop does, in fact, see the network.
-The network is broadcast from a ClearAccess AG10W modem/router.

Can somebody help me figure out why it's not connecting?

---

### Post by philcamlin on 2009-07-16
try rebooting the router

---

### Post by Andorin on 2009-07-16
> **philcamlin said:**
> try rebooting the router
Didn't help.

---

### Post by philcamlin on 2009-07-16
what router is it ?

---

### Post by lisati on 2009-07-16
> **philcamlin said:**
> what router is it ?

The OP mentioned ClearAccess AG10W

---

### Post by Andorin on 2009-07-16
> **lisati said:**
> The OP mentioned ClearAccess AG10W
This. :P

Still looking for help...

---

### Post by redmk2 on 2009-07-16
> **Andorin said:**
> Facts:
-My laptop (Acer Aspire 5570z) generally doesn't have any trouble with connecting to wireless networks.
-When I open wicd and click Connect on my home network, it hangs on "Obtaining IP address" and then aborts after a few minutes.
What does this mean to you?  To me it means that the laptop asked for an IP address via DHCP and did not get an answer.> 

-The home network is not secured.
-The home network is not using MAC filtering.
-The laptop does, in fact, see the network.
Hmmm, how can "see" the network if you have not been allocated an address?  This is kind of a loaded question, as there is a way.> 
-The network is broadcast from a ClearAccess AG10W modem/router.
What des this mean?  Do you mean that the router provides DHCP services (IP addresses)?> 

Can somebody help me figure out why it's not connecting?

When the laptop 'hangs on "Obtaining IP address"' what IP address does it get?  We are answering that "loaded question" I alluded to earlier.  You can check the current ip address from the terminal with this command```
ifconfig -a
```  I am looking for something like this ```
eth0      Link encap:Ethernet  HWaddr 00:04:76:cd:54:e0  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
```

---

### Post by Andorin on 2009-07-16
> **redmk2 said:**
> What does this mean to you?  To me it means that the laptop asked for an IP address via DHCP and did not get an answer.
That could be the case. I wouldn't really know since I'm still new to all this.

> Hmmm, how can "see" the network if you have not been allocated an address?  This is kind of a loaded question, as there is a way.I don't know. Again, I don't know anything about this; I'm just telling it like it is.

> What des this mean?  Do you mean that the router provides DHCP services (IP addresses)?
When the laptop 'hangs on "Obtaining IP address"' what IP address does it get?  We are answering that "loaded question" I alluded to earlier.  You can check the current ip address from the terminal with this command```
ifconfig -a
```I am looking for something like this ```
eth0      Link encap:Ethernet  HWaddr 00:04:76:cd:54:e0  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
```You mean wlan0, since I'm not connected to anything via ethernet, right?

Here's the output for wlan0:
```
wlan0     Link encap:Ethernet  HWaddr 00:19:7e:79:d5:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28842426 (28.8 MB)  TX bytes:2196171 (2.1 MB)
```The full output for my ifconfig is [here]("http://pastebin.com/m76b029bf").

---

### Post by redmk2 on 2009-07-17
I'm glad you provided the *entire* reply to the command.  This is what I was looking for```
#
wlan0:avahi Link encap:Ethernet  HWaddr 00:19:7e:79:d5:36  
#
          inet addr:[COLOR="Red"]169.254.6.227[/COLOR]  Bcast:169.254.255.255  Mask:255.255.0.0
#
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
#
 
```

This IP address is **not** supplied by a DHCP server (on your router).  The address is supplied by the zero-conf daemon (avahi-daemon).  This 169.254.x.x is supplied when no DHCP server responds to a request for an IP address.  This should allow you to browse the Internet or get email, but not interact with "your network".

The bottom line is you need to configure your ClearAccess AG10WAG10W to supply an DHCP IP address in your network IP range when requested by your laptop.  I would also check to make sure the the DHCP client is configured correctly on the laptop, although it sounds like it is by your description.

---

### Post by Andorin on 2009-07-17
> **redmk2 said:**
>  The bottom line is you need to configure your ClearAccess AG10WAG10W to supply an DHCP IP address in your network IP range when requested by your laptop.  I would also check to make sure the the DHCP client is configured correctly on the laptop, although it sounds like it is by your description.
I logged into the router and found the DHCP section- and yep, there's no entry for my laptop! Unfortunately, I also don't see a section to /edit/ this information and add my laptop, but I'll be hunting around for it.

---

### Post by redmk2 on 2009-07-17
You need to find the settings for the DHCP server and make sure that it is indeed functioning and that there are enough addresses in the pool of numbers for all your hosts.  You laptop will not be listed until it has been served an IP address.

Edit:  You don't add the hosts it is dynamic!

---

### Post by Andorin on 2009-07-17
Alright... here's what I did...

-I went into my router's page. There was no edit or add option on the DHCP page.
-I did find an add option under LAN (I hope this isn't where I messed up, but I can't find this anywhere else so far) under the section concerning the DHCP server. I added my laptop's MAC address and a static IP for this laptop.
-After saving that, I went into Advanced Settings under the network in wicd and added in the static IP, netmask, gateway, and DNS information. Saved that.
-Tried connecting. The laptop immediately seems to connect to the wireless network, but it's constantly listed at 0%, even when it's a handful of feet from the router, and will not load anything from the Internet. Also, the laptop isn't listed on the DHCP page, the one I can't edit. 

Sorry if I did something wrong. =(

---

### Post by redmk2 on 2009-07-17
> **Andorin said:**
> Alright... here's what I did...

-I went into my router's page. There was no edit or add option on the DHCP page.
-I did find an add option under LAN (I hope this isn't where I messed up, but I can't find this anywhere else so far) under the section concerning the DHCP server. I added my laptop's MAC address and a static IP for this laptop.

That would be fine if you wanted to reserve a permanent and  specific address handed out by the DHCP server for the laptop to use while on your network.> 
-After saving that, I went into Advanced Settings under the network in wicd and added in the static IP, netmask, gateway, and DNS information. Saved that.

This is counter to what you did on the router (DHCP).  This would be how to set up a static (non-dhcp) address.> 
-Tried connecting. The laptop immediately seems to connect to the wireless network, but it's constantly listed at 0%, even when it's a handful of feet from the router, and will not load anything from the Internet. Also, the laptop isn't listed on the DHCP page, the one I can't edit.

Sorry if I did something wrong. =(

Sorry?  What do you have to be sorry about.  This is how you learn and collect war stories to tell others when you are the guru.  :-)

You need to pick one way or the other -- either static IP addressing (the second description) or via DHCP.  But not both.

Do you know how to use GIMP to do a screen capture of the setup page of your router?  I looked for an online manual and couldn't find one.  It would help if I could see what you are talking about.

---

### Post by Andorin on 2009-07-17
> **redmk2 said:**
>  Sorry?  What do you have to be sorry about.  This is how you learn and collect war stories to tell others when you are the guru.  :-)
Glad you understand. ^^

> You need to pick one way or the other -- either static IP addressing (the second description) or via DHCP.  But not both.I don't think I particularly care either way, so long as it works. I could just pick static IP for the sake of making a choice.

> Do you know how to use GIMP to do a screen capture of the setup page of your router?  I looked for an online manual and couldn't find one.  It would help if I could see what you are talking about.I couldn't even find a manual on the manufacturer's website. Ridiculous. And yeah. Screenies: 
-[Main screen]("http://img98.imageshack.us/img98/64/screenshotbyu.png")
-[LAN page where I entered my laptop info]("http://img140.imageshack.us/img140/1601/screenshot1tbr.png")
-[DHCP page; mein comp is my PC]("http://img140.imageshack.us/img140/1842/screenshot2czm.png")
-[URL="http://img208.imageshack.us/img208/377/screenshot3dho.png"]Wireless page, with menus on the side
[/URL]
If you need more screenies, ask. I just posted what I thought were the most relevant and helpful sections.

---

### Post by redmk2 on 2009-07-17
I see where you entered the information [_[COLOR="DarkSlateGray"]here[/COLOR]_]("http://img140.imageshack.us/img140/1601/screenshot1tbr.png").

I notice that you have the entire IP range of your network in your pool of addresses i.e. 192.168.1.2 thru .254 .  I would reduce that to 192.168.1.2 thru .99.  This way you can have a manually configured (static) address.  you can't configure overlapping ranges (manual vs. DHCP).

I would also remove the static IP lease for right now.

I looked at the page showing "mein comp" That page is NOT made to be edited.  it is for info only and is dynamicaly rendered by the router.  When the lease is handed out the host will show up there without your help.

Now we need to see if you have the WICD set up correctly.  I would try to set it up to obtain an IP address automatically.

---

### Post by Andorin on 2009-07-17
> **redmk2 said:**
>  I notice that you have the entire IP range of your network in your pool of addresses i.e. 192.168.1.2 thru .254 .  I would reduce that to 192.168.1.2 thru .99.  This way you can have a manually configured (static) address.  you can't configure overlapping ranges (manual vs. DHCP).

I would also remove the static IP lease for right now.
Done.

> I looked at the page showing "mein comp" That page is NOT made to be edited.  it is for info only and is dynamicaly rendered by the router.  When the lease is handed out the host will show up there without your help.I figured as much since there was no edit section. =P

> Now we need to see if you have the WICD set up correctly.  I would try to set it up to obtain an IP address automatically.How? =x I see no options for that. (Unless leaving "use static IPs" unchecked counts. Or do I configure that through the router?)

---

### Post by redmk2 on 2009-07-17
> How? =x I see no options for that. (Unless leaving "use static IPs" unchecked counts. Or do I configure that through the router?)

I've never used WICD.  As a matter of fact I don't have a wireless Ubuntu host at all.  I know the protocol and understand the settings.  The laptop needs to be set up to ask for DHCP services.  We can try leaving the "use static IPs" unchecked.  

I can look through the literature tomorrow for more answers.

One piece of device:  Static IP = manual configuration while reserved IP = permanent IP address via DHCP.

If you set the IP address statically use:```
IP address -- 192.168.1.150[COLOR="Red"]  <-- this is outside the dhcp range[/COLOR]
subnet mask -- 255.255.255.0
gateway -- 192.168.1.1

```

Note the gateway is the IP address of the router (the gateway).

---

### Post by Andorin on 2009-07-17
> **redmk2 said:**
> I've never used WICD.  As a matter of fact I don't have a wireless Ubuntu host at all.  I know the protocol and understand the settings.  The laptop needs to be set up to ask for DHCP services.  We can try leaving the "use static IPs" unchecked.  
I ought to point out that that's how it is by default. Unsetting it doesn't fix the problem. I'm a bit too tired right now to be going at this alone, I'm afraid. Can't do it without help from someone who understands more of this than I do.

---

### Post by Andorin on 2009-07-18
Bump.

---

