---
title: "resolv.conf"
date: 2012-08-11
forum: Networking &amp; Wireless
---

### Post by Reddoug on 2012-08-11
Hi All

I volunteer with a Computers for Schools program and we are trying to set up a disless remote boot in linux. We are using ubuntu and Clonezilla. One of the first things is says to do is to remove network manager. Here is a link to what we are using.  [http://drbl.sourceforge.net/one4all](http://drbl.sourceforge.net/one4all)  When we did that we had to manually set our ip address. Problem is that we can not access resolv.conf to manually set name server. It is in a lrwxrwxrwx resolv.conf -> ..run/resolvconf/resolv.conf. When I cat resolv.conf, it doesn't work. I have not tried vim resolv.conf would that work. I am not at the computer we are setting it up on at this time. We are using ubuntu 12.4.
 Maybe there is a better way to go about this?  We are not the best with command line.

Thanks, Doug

---

### Post by sienile on 2012-08-11
Have you tried running your commands as root using sudo?

---

### Post by wildmanne39 on 2012-08-11
*Thread moved to **Networking & Wireless**.*

---

### Post by steeldriver on 2012-08-11
I don't understand what you're doing but a lot has changed recently with name resolution - I suspect you may need to remove (or otherwise disable) resolvconf - and possibly dnsmasq as well to get completely back to the old-style networking service as defined /etc/network/interfaces

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by Reddoug on 2012-08-11
We are trying to setup Clonezilla. Haven't figured out why they say to remove network manager. I was trying to manually set the dns address and was unable to access resolv.conf. We did try using sudo but that didn't work. This is a steep learning process we are going through. What we are doing is setting up one computer then copying drive and pushing image out to several computers when we set up several computers. The hard drive on the computer we were using died and we are trying to set up a new computer to image drive with. 

Thanks, Doug

---

### Post by asmoore82 on 2012-08-12
I have set up a few Clonezilla servers on Ubuntu 10.04 and can successfully repeat the process in a reasonably short amount of time.

I tried 1 12.04 box this summer and it never worked reliably. PXE booting machines would randomly hang during the boot process and only sometimes make it all the way through. I know that for 10.04 the PXE booting machines put up a log message about workarounds in use due to Upstart instead of a traditional init system. I think it will be tweaked to work with 12.04 someday.

Until then, 10.04 might be a better way to go especially if all you need is the Clonezilla features and not the full blown DRBL.

---

### Post by Reddoug on 2012-08-12
Thanks for the info. I will see if I have a copy of 10.4 laying around.


Thanks again, Doug

---

### Post by Reddoug on 2012-08-27
Hi All     Ubuntu 12.4

How can I access this file to view the address of the DNS servers? 

lrwxrwxrwx resolv.conf -> ..run/resolvconf/resolv.conf

On older versions I could cat resolv.conf and view the file but I can not view the file above. Have tried using sudo. Do they put DNS info in a different place?

Thanks, Doug

---

### Post by jdthood on 2012-10-29
The symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf puts the resolv.conf file under the control of the resolvconf utility, which is now part of the Ubuntu base system. When resolvconf is in control you have to configure things the resolvconf way. The resolvconf way is to associate nameserver addresses with interfaces; the addresses get added to resolv.conf when the associated interfaces are configured and get removed when those interfaces are de-configured. If you have a simple system with one interface, eth0, configured using ifup then you should edit /etc/network/interfaces and add a line

    dns-nameservers 1.2.3.4

to the "iface eth0" stanza. Then "ifdown eth0" and "ifup eth0".  See the "resolvconf" man page for more information.

If you want a static resolv.conf file then replace the symlink /etc/resolv.conf with a static file.

---

