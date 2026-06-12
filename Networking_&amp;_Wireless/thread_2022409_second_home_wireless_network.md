---
title: "second home wireless network"
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by frog3764 on 2012-07-10
I am a newbie / dummy with Linux Ubuntu.  I just installed 12.4 and need help with setting up a second wireless network in my home.  My router is a Dlink Gamer Lounge model DGL4300.  I already have a secured network on this router for 3 Windows pc's and want to make an un-secured network for this extra pc which is for the visitors and freeloaders.  I don't want them connected to the secured network.  Since I'm a newbie I need some step by step instructions on how and if I can do this.  All input is appreciated.

---

### Post by ciri on 2012-07-10
I don't think your router supports creating two networks at the same time. You could try setting up an [ad-hoc network]("https://help.ubuntu.com/community/WifiDocs/Adhoc") (on a computer). Note that in order to share a connection, this particular computer will need two network cards, one connected to the acces point and one that can host the wireless network.

---

### Post by frog3764 on 2012-07-10
Hey Ciri - thanks for the come back.  I do have another Dlink router, could I set it up strictly for the Ubuntu pc without screwing up the other router and secured connection?  That would be two routers connected to one modem with a phone line tap or double plug.
Jim

---

### Post by Kirk Schnable on 2012-07-11
The proper way to do this would probably be in this fashion:

```

                                             |-- Secured Network
                                               
Modem  ->   Gaming Router    
                                               
                                            |-- Insecure Network

```

Where "Secured Network" is a router, with your PCs behind it, and "Insecure Network" is another router with your PCs behind it.  

In order to connect two routers to your modem, unless you have a routing feature built-in to the modem, you'll need to do some routing.  You can't usually just have two connections to the modem.

By doing it this way, your Secure and Insecure network both have their own firewalls.  This will guarantee you that the networks will be separate, as the only way the Insecure Network can access resources on the Secure Network is via Internet port forwards, which are open to the world anyway.

You'd want to do two or three IP ranges.  The Gaming Router could have an IP range like "172.16.0.1" and your two networks could have WAN IPs of 172.16.0.2 and 172.16.0.3.

Then the network behind the gaming router could be 192.168.1.x and the network behind the other router could have the same IP range without affecting anything (192.168.1.x) or you could give it a different range to avoid confusion (192.168.2.x etc).

This is most likely a more complicated solution than you were hoping for.  You might be able to simplify it, by putting a switch between your routers and your DSL modem.  However depending on how your modem is setup, that approach might not work.  No matter how your modem is setup, the approach I outlined above will work.

The correct way to do what you want to do, inside a corporate environment, is to setup VLANs.  But your home routers don't typically support this functionality.

Kirk

---

### Post by frog3764 on 2012-07-11
Hey Kirk - Your right on the complicated process you mentioned.  So I think I will think about this for a while.  This just might be more involved than necessary for only a few "outsiders or freeloaders" who might want to use the pc occasionally.  I just thought I'd use it in the living room as an extra pc, that way keeping everyone else off of mine in the computer room.  The pc has little value and it's worth more to just keep it than to try to peddle it here in the Philippines.  This is also my Ubuntu playground so I can try to get used to it.  I'm spoiled on Windows, but I hate buying these Windows upgrades.  I am hoping I can get Ubuntu figured out so I can use it on my regular pc.  The biggest problem I have is the names of the files and folders are so different from Windows I can't figure out where to go to do what I want.  So now maybe I can spend some time using Ubuntu and explore my way around.  Anyway, thanks for your help.

Jim

---

### Post by kurt18947 on 2012-07-11
I'm not certain whether the following link applies only to routers issued to Verizon FiOS subscribers or whether this applies to most routers.  The parts talking about MOCA and coax are specific to FiOS.

[http://www.dslreports.com/faq/verizonfios/3.0_Networking#12506](http://www.dslreports.com/faq/verizonfios/3.0_Networking#12506)

There are other threads on dslreports talking about multiple routers/networks.  I tried two routers just for grins.  One was the ActionTec from Verizon, the second a Linksys WRT-54GL.  I turned off the wireless on the Verizon router, disabled dhcp on the Linksys and assigned different I.P. addresses to each router.  One was 192.168.1.1, the other 192.168.1.2.  Set up the wifi network on the Linksys, ran a plain ethernet cable (not crossover) between LAN ports - don't use the WAN port on the secondary router - and was in business.  I didn't try two WiFi networks but as long as the I.P. addresses and SSIDs are different I'll bet it would work.  It might be a good idea to separate the routers/WiFi antennas so there's less interference and/or manually assign different channels.  

I'm not an expert on this stuff. I'd think if you have two separate wireless networks and two separate routers,  one secured and one not, I would think that someone on the unsecured network would not be able to access the secured network.  Each router is running its own firewall. But again, I'm no expert.

---

### Post by frog3764 on 2012-07-11
Thanks Kurt for the interesting link.  Sounds pretty interesting.

Jim

---

### Post by Kirk Schnable on 2012-07-11
What are you really trying to achieve here?  Is this just a public access computer inside your house that you want to restrict from accessing your PC?

If you don't give your guests sudo access, you could just tell iptables to block all outgoing traffic except to your router.  That'd keep them off the rest of your network.

Kirk

---

### Post by frog3764 on 2012-07-11
This pc is just for a few friends or neighbours who come to visit who want to use it when they visit my house.  Since most are not real adept to computers, I just don't want them to be able to screw up anything on my secured network.  I always have to give them the sign-on to access the network.  They could also use it outside close by without me knowing about it too.  That's it, just want to keep freeloaders off my network but still let them use the pc if they need it.

---

### Post by Kirk Schnable on 2012-07-11
> **frog3764 said:**
> This pc is just for a few friends or neighbours who come to visit who want to use it when they visit my house.  Since most are not real adept to computers, I just don't want them to be able to screw up anything on my secured network.  I always have to give them the sign-on to access the network.  They could also use it outside close by without me knowing about it too.  That's it, just want to keep freeloaders off my network but still let them use the pc if they need it.

So they won't be getting root access (sudo) on this computer?

---

### Post by frog3764 on 2012-07-12
NO as I have a password for that.  It's just the Internet that I want to limit access to.

---

### Post by Kirk Schnable on 2012-07-12
> **frog3764 said:**
> NO as I have a password for that.  It's just the Internet that I want to limit access to.

Excellent. Without sudo access, they can't change the iptables firewall on the computer. 

Rather than setup a separate network, you could make a firewall rule on this Ubuntu computer, so it's only allowed to talk to your router / the Internet. 

If you'd like some guidance on how to do this, I may be able to help. But you'll want to look at iptables IP whitelisting, and set the default Output policy to Drop. 


Here's something to help you get started: [http://serverfault.com/questions/30026/whitelist-allowed-ips-in-out-using-iptables](http://serverfault.com/questions/30026/whitelist-allowed-ips-in-out-using-iptables)

Kirk

---

### Post by frog3764 on 2012-07-12
Since all of this is well above my level, I think I'll just explore the OS more before "tinkering" with stuff I don't know anything about.  I'm still having trouble just getting around in the OS.  Sounds like you have the solution though.  I better hold off a bit and try to absorb some of this first.  I appreciate your help with this.

Jim

---

