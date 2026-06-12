---
title: "DHCP w/ Failover IP address"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by shebangs on 2009-06-10
How do I tell Ubuntu Hardy, to try to find a DHCP server for eth0.  BUT if it cannot, set a specified IP address and subnet?

Same as Windows XP+ 'alternate' IP.

Cheers

---

### Post by Bucky Ball on 2009-06-10
System->Admin->Network. Unlock and properties. In there make sure your Configuration is set to DHCP Configuration (Auto) - I think it is.

---

### Post by redmk2 on 2009-06-10
> **shebangs said:**
> How do I tell Ubuntu Hardy, to try to find a DHCP server for eth0.  BUT if it cannot, set a specified IP address and subnet?

Same as Windows XP+ 'alternate' IP.

Cheers

I have never configured this with Linux but the reference in the Microsoft literature mentions 169.254.n.n.  This is named Zeroconf (Avahi) in Ubuntu.

See [_**here**_]("https://help.ubuntu.com/community/HowToZeroconf")

---

### Post by shebangs on 2009-06-10
I think zeroconf is a bit overkill.

I literally want to assign eth0 to 192.168.1.1/32 if it doesnt get a DHCP IP address.  Nothing more, nothing less.  No local network autoconfiguration etc.

---

### Post by Bucky Ball on 2009-06-10
> **shebangs said:**
> I think zeroconf is a bit overkill.

I literally want to assign eth0 to 192.168.1.1/32 if it doesnt get a DHCP IP address.  Nothing more, nothing less.  No local network autoconfiguration etc.

Then go back to 'Network,' unlock, properties and set configuration to 'Static IP' and set the appropriate information; the IP address you want your machine to use, your subnet mask (router's IP) and 255.255.255.0 probably for your gateway.

---

### Post by redmk2 on 2009-06-10
> **shebangs said:**
> I think zeroconf is a bit overkill.

I literally want to assign eth0 to 192.168.1.1/32 if it doesnt get a DHCP IP address.  Nothing more, nothing less.  No local network autoconfiguration etc.

Huh?  Then what did you mean by this: "Same as Windows XP+ 'alternate' IP.".  That's how XP does it.

DHCP does not provide a method for you to assign a specific "fail over" address eg: 192.168.n.n. as you propose.

---

### Post by Iowan on 2009-06-10
I've done it in Jaunty by configuring a manual configuration after "auto eth0", but I don't think Hardy NM likes manual (static address) configurations.

---

### Post by shebangs on 2009-06-10
Surely there is some kind of hack I can do to make this work? 

A cron job every minute which runs, checks if eth0 has an IP, and if it doesnt assign it a static one?

I dont understand why something so simple hasnt been implemented.

> **redmk2 said:**
> Huh?  Then what did you mean by this: "Same as Windows XP+ 'alternate' IP.".  That's how XP does it.

DHCP does not provide a method for you to assign a specific "fail over" address eg: 192.168.n.n. as you propose.

If Windows XP fails getting an IP from the DHCP server, you can in the the TCP/IP properties, give it a "***user configured***", "***Alternative IP***" address.

> **Bucky Ball said:**
> Then go back to 'Network,' unlock, properties and set configuration to 'Static IP' and set the appropriate information; the IP address you want your machine to use, your subnet mask (router's IP) and 255.255.255.0 probably for your gateway.

In my setup, I still want it to try to get a DHCP IP first.

---

### Post by redmk2 on 2009-06-10
> **shebangs said:**
> ...Surely there is some kind of hack I can do to make this work? 

A cron job every minute which runs, checks if eth0 has an IP, and if it doesnt assign it a static one?

I dont understand why something so simple hasnt been implemented.


Things aren't as simple as you think.  Here is how Microsoft does it:> XP stores the custom connection configuration settings under the HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfacesregistry subkey.

As Ubuntu doesn't have a registry like this (yet) It can't be done the Microsoft way.

Replicating this action is not a trivial matter.  
> 

If Windows XP fails getting an IP from the DHCP server, you can in the the TCP/IP properties, give it a "***user configured***", "***Alternative IP***" address.


In my setup, I still want it to try to get a DHCP IP first.

This is what Microsoft says "*when moving between networks where DHCP servers aren't...*" always to be found eg: a dynamic situation -- > If you configure your computer to use DHCP and no DHCP server is available, the machine will typically use an IP address in the range 169.254.0.1 to 169.254.255.254 with a subnet mask of 255.255.0.0. 

As it turns out, and I missed this myself MS limits the usefulness to the local subnet (that wont be satisfactory).  I believe Zeroconf does allow internetworking.

See [***here***]("http://windowsitpro.com/article/articleid/27129/how-do-i-use-the-windows-xp-alternate-tcpip-configuration.html") for the  MS references.

In the end it's Zeroconf or you writing your own script.

Edit:  I have found the basic beginnings of a set of scripts for you.  You can find them as attachments _**[here]("http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-09/msg03979.html")**_ to a post regarding almost the same question as you have.  They are only a **very very** crude beginning.  As you can see they do use Avahi.  Don't be put off by that see what others have recommended.

---

