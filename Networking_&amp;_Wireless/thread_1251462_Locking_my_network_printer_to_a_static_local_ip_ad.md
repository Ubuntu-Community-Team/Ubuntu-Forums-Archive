---
title: "Locking my network printer to a static local ip address - HOW?"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by crjackson on 2009-08-27
Okay, this isn't an OS issue but I was hoping someone here could tell me how to do this.

I have a Dell 5100cn color laser printer being used by 12 other pc's on my network.  It works great regardless of OS.  The problem is that sometimes the router gets out of sync with the cable modem and I have to unplug them both and then plug them in again so they will resync and provide an interconnection.

After plugging everything back in, all the local ip addresses are reconfigured and the ip address for the printer has changed.  This means that I have to constantly go to each pc and change the printer properties so that the printer will work again for everyone.

Is there some method of assigning a specific local ip address to the device so that it will always load up on the same ip?

I'm not clearing memory when I unplug the router, I'm just basically rebooting it and the modem.

Any suggestions?

---

### Post by stlsaint on 2009-08-27
will try my best in assisting you...i do that within widows all you have to do is assign that printer a static ip and also assign it within the router so the router wont give it a different ip everytime...then you must go to every system and change the way that system connects to that printer....ie...go thru add a printer and give the ip you gave the printer and it will connect via ip over network...to verify this in windows you can go to the properties of that printer you are connected to and view the port that the printer is on...now thats for windows...i dont use a printer for ubuntu so i wont be able to help there but maybe this will assuming you are on jaunty!!! [PRINTER AND FAX]("https://help.ubuntu.com/9.04/printing/C/index.html")

---

### Post by crjackson on 2009-08-27
I understand, but I don't know how to assign a static ip address in the router.  It's a Linksys w54g series.  If someone can tell me how to assign an address to the thing, the rest would be a snap.

---

### Post by redmk2 on 2009-08-27
> **crjackson said:**
> I understand, but I don't know how to assign a static ip address in the router.  It's a Linksys w54g series.  If someone can tell me how to assign an address to the thing, the rest would be a snap.

I think **stlsaint** is suggesting assigning and IP address **outside** of the dhcp range, i.e. static.

Go to the Linksys page where you configure the range (pool) of addresses. View, but don't change this range.  Pick and IP address not in this pool, but still in the range of the network you are  on.  Typically dhcp is in the .100 to 150 range, you could use one that is either lower (say .10 to .99) or higher (like .200 to 250).  I use the ip address 192.168.1.**200** for my printer on my 192.168.1.0 /24 network.

Edit:  You do not assign the address via the Linksys.  You assign the address manually on the printer.

---

### Post by crjackson on 2009-08-27
> **redmk2 said:**
> 

Edit:  You do not assign the address via the Linksys.  You assign the address manually on the printer.

Is this done from the OS somehow or using the printer LCD menu panel?

---

### Post by Iowan on 2009-08-27
Dunno about the Linksys in particular, but you *can* set up a static lease based on MAC address (on the router). The printer is configured to get an address automatically (DHCP), but it gets the same address each time.

---

### Post by redmk2 on 2009-08-27
> **Iowan said:**
> Dunno about the Linksys in particular, but you *can* set up a static lease based on MAC address (on the router). The printer is configured to get an address automatically (DHCP), but it gets the same address each time.

> Is this done from the OS somehow or using the printer LCD menu panel? 

First let me say that we are talking about setting the IP address of the printer **at the printer**.  You  should be able to be able to set this using the printers controls.  [[COLOR="DarkSlateGray"]**_Here_**[/COLOR]]("http://support.dell.com/support/edocs/systems/5100cn/en/UG/section20.html#1093820") is some information from Dell.  Setting this address involves you knowing what IP address can be used without conflicting with whatever addresses your Linksys has in its DHCP pool.

I am not a fan of using DHCP to set fixed IP addresses,  if I can achieve the same results with a static address configured at at the device.  Using DHCP to do this adds extra complications that are not needed.

---

### Post by crjackson on 2009-08-27
> **redmk2 said:**
> First let me say that we are talking about setting the IP address of the printer **at the printer**.  You  should be able to be able to set this using the printers controls.  [[COLOR="DarkSlateGray"]**_Here_**[/COLOR]]("http://support.dell.com/support/edocs/systems/5100cn/en/UG/section20.html#1093820") is some information from Dell.  Setting this address involves you knowing what IP address can be used without conflicting with whatever addresses your Linksys has in its DHCP pool.

I am not a fan of using DHCP to set fixed IP addresses,  if I can achieve the same results with a static address configured at at the device.  Using DHCP to do this adds extra complications that are not needed.

Okay this is good stuff...

So it seems I should go to the printer internal menu and set my IP to something like..   **192.168.1.200**

If I'm understanding the settings page correctly (see attached screenshot) my internal DHCP range is **192.168.1.101** to **192.168.150**

I'm thinking 100 isn't available because that is assigned to the router.  Am I understanding this correctly?

---

### Post by crjackson on 2009-08-27
> **Iowan said:**
> Dunno about the Linksys in particular, but you *can* set up a static lease based on MAC address (on the router). The printer is configured to get an address automatically (DHCP), but it gets the same address each time.

Can you give me a walk through?  It would be nice to know alternate methods.

---

### Post by dbalascak on 2009-08-27
The router IP is 1.1. You can use 1.2 thru 1.99 and 1.150 thru 1.254 as static addresses. The IPs 1.100 thru 1.149 are the DHCP pool. ( that would be a totla of 50 DHCP hosts).  DHCP will never use anything below 1.100.

---

### Post by redmk2 on 2009-08-27
> **crjackson said:**
> Okay this is good stuff...

So it seems I should go to the printer internal menu and set my IP to something like..   **192.168.1.200**
Exactly!> 

If I'm understanding the settings page correctly (see attached screenshot) my internal DHCP range is **192.168.1.101** to **192.168.150**
Actually it is 192.168.1.100 to 149.  It starts at 100 and has 50 addresses in the pool.> 

I'm thinking 100 isn't available because that is assigned to the router.  Am I understanding this correctly?
Nope!  The IP address is 192.168.1.1 as the screen shot states.  It's shown as the "local address".

In any event, if you use 192.168.1.200 you will be in the 192.168.1.0/24 network but away from the DHCP pool.  Think of the pool as a subset of the range of addresses in the network.  Your network starts at [COLOR="RoyalBlue"]192.168.1[/COLOR][COLOR="Red"].1[/COLOR] and has addresses to [COLOR="RoyalBlue"]192.168.1[/COLOR][COLOR="Red"].254[/COLOR].  The numerical 192.168.1.0 is reserved for the network ID and 192.168.1.255 is reserved for the broadcast address of the network.

---

