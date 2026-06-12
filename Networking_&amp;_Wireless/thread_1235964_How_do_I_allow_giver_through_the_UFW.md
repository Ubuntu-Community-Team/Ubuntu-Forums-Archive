---
title: "How do I allow giver through the UFW?"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-08-09
Hi.
How do I allow giver through the UFW?
I tried 
```
sudo ufw allow giver
```
but it doesnt take that statement.
:confused:

I can just disable the firewall to allow the use of giver but that is hardly practical.

---

### Post by dmizer on 2009-08-09
Try installing gufw. You can then configure the firewall via GUI by going to System > Administration > Firewall.

You may have to figure out exactly what ports (or port range) that giver uses, and open them rather than trying to open the service as a name.

---

### Post by Rytron on 2009-08-10
> **dmizer said:**
> Try installing gufw. You can then configure the firewall via GUI by going to System > Administration > Firewall.

You may have to figure out exactly what ports (or port range) that giver uses, and open them rather than trying to open the service as a name.

Thanks. But how do I find out the port number(s) of giver? I know for example that ssh is port number 22 but there doesn't seem to be any documentation on giver port numbers.

---

### Post by dmizer on 2009-08-10
I don't know. I've never used it. But, I bet they would know here: #giver on irc.gnome.org 

I do have a few questions though.
1) Are you sure you need the UFW enabled? If your computer is behind a firewalled router, there's no need to duplicate effort by having UFW installed. In this case, UFW isn't really offering you more protection than you already have, it's only inhibiting LAN traffic.
2) Do you need the UFW enabled because you have a direct connection to the internet? If you need UFW because you have a direct connection to the internet (no firewalled router), then you probably shouldn't be punching holes in it for giver as giver isn't really designed to be used across the internet. You should be using an encrypted protocol like sftp, ftps, or sshfs.

---

### Post by Rytron on 2009-08-10
> **dmizer said:**
> I don't know. I've never used it. But, I bet they would know here: #giver on irc.gnome.org 

I do have a few questions though.
1) Are you sure you need the UFW enabled? If your computer is behind a firewalled router, there's no need to duplicate effort by having UFW installed. In this case, UFW isn't really offering you more protection than you already have, it's only inhibiting LAN traffic.
2) Do you need the UFW enabled because you have a direct connection to the internet? If you need UFW because you have a direct connection to the internet (no firewalled router), then you probably shouldn't be punching holes in it for giver as giver isn't really designed to be used across the internet. You should be using an encrypted protocol like sftp, ftps, or sshfs.

Thanks for the tips dmizer. Attached please find a screen shot of my router firewall settings. I presume so that the router is providing enough security?

I like to get to know as much about the UFW as possible because someday I may need to use it as my primary firewall.

Cheers.

---

### Post by dmizer on 2009-08-10
> **Rytron said:**
> Thanks for the tips dmizer. Attached please find a screen shot of my router firewall settings. I presume so that the router is providing enough security?
That looks fine to me.

> **Rytron said:**
> I like to get to know as much about the UFW as possible because someday I may need to use it as my primary firewall.

If you wanted to set up you own Linux gateway, there are much better methods than UFW. Something like: [Untangle](http://www.untangle.com/home), [Clarkconnect](http://www.clarkconnect.com/), and [Shorewall](http://www.shorewall.net/) (there are many more) are purpose built releases and will do the job much better and more easily. They can also easily run in a virtual machine on your main box with little to no overhead.

In my opinion, UFW is good for laptops which are sometimes used to connect to insecure/untrusted access points. However, I highly suggest that you form your own opinion as well.

---

### Post by Rytron on 2009-08-10
> **dmizer said:**
> That looks fine to me.



If you wanted to set up you own Linux gateway, there are much better methods than UFW. Something like: [Untangle](http://www.untangle.com/home), [Clarkconnect](http://www.clarkconnect.com/), and [Shorewall](http://www.shorewall.net/) (there are many more) are purpose built releases and will do the job much better and more easily. They can also easily run in a virtual machine on your main box with little to no overhead.

In my opinion, UFW is good for laptops which are sometimes used to connect to insecure/untrusted access points. However, I highly suggest that you form your own opinion as well.

Thanks. I will check out Untangle, Clarkconnect, and Shorewall. Thats a good point about Laptops using the UFW when connecting to other internet sources besides your own home internet.

---

