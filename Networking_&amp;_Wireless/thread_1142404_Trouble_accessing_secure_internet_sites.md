---
title: "Trouble accessing secure internet sites"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by willem on 2009-04-29
I am having trouble accessing **some** internet sites from linux. Whenever I try to access hotmail, facebook and some other sites that require password authentication, my browser takes ages to load, and then usually gives me a server timed out errror, or it just keeps on attempting to load the page. This happens both in Firefox and Opera, so it is not a browser issue. **I am able to access other sites without any problem**.

I am also having trouble posting to the ubuntu forums. When I click on the submit button after writing up a new post, my browser asks me whether I want to download or open a php file. Opening the php file in Orca simply shows me an empty file (it is 0 bytes in size). If I try to open the file in firefox, I simply get another box asking me whether I want to open or save another php file. I had to boot into XP in order to post this thread - ironic how I need windows to acces the ubuntu forum...

I am running Intrepid with a Telkom DSL internet connection. I don't access the internet via a proxy or a firewall, so this cannot be the problem either. If I boot in Windows XP, I don't have any problems accessing any sites, so my network connection is fine. It must be something to do with Ubuntu.

Any ideas???

---

### Post by willem on 2009-05-08
> **willem said:**
> I am having trouble accessing **some** internet sites from linux. Whenever I try to access hotmail, facebook and some other sites that require password authentication, my browser takes ages to load, and then usually gives me a server timed out errror, or it just keeps on attempting to load the page. This happens both in Firefox and Opera, so it is not a browser issue. **I am able to access other sites without any problem**.

I am also having trouble posting to the ubuntu forums. When I click on the submit button after writing up a new post, my browser asks me whether I want to download or open a php file. Opening the php file in Orca simply shows me an empty file (it is 0 bytes in size). If I try to open the file in firefox, I simply get another box asking me whether I want to open or save another php file. I had to boot into XP in order to post this thread - ironic how I need windows to acces the ubuntu forum...

I am running Intrepid with a Telkom DSL internet connection. I don't access the internet via a proxy or a firewall, so this cannot be the problem either. If I boot in Windows XP, I don't have any problems accessing any sites, so my network connection is fine. It must be something to do with Ubuntu.

Any ideas???


Managed to figure out that it was the MTU setting for the DSL connection. It should be 1352. Now to figure out how to permanently fix that...

---

### Post by superprash2003 on 2009-05-08
well permanently setting MTU to 1352 would be a permanent fix right? :)

---

### Post by willem on 2009-05-08
> **superprash2003 said:**
> well permanently setting MTU to 1352 would be a permanent fix right? :)

Very perceptive of you, dr Watson. :P
Unfortunately, I'm no linux guru, so I don't know in which config file to set this permanently. I did the following to fix it:

```
sudo ifconfig ppp0 mtu 1352
```

Unfortunatley, the system goes back to the old value when I reboot. Any idea which config file sets the value on bootup?

---

### Post by cariboo on 2009-05-08
You can add the following to /etc/network/interfaces, to permanently set the MTU

```
iface eth0 inet dhcp
hostname <hostname>
name LAN Interface
pre-up /sbin/ifconfig $IFACE mtu 1492 
```

Where <hostname> is your computers host name,

---

### Post by willem on 2009-05-14
> **cariboo907 said:**
> You can add the following to /etc/network/interfaces, to permanently set the MTU

```
iface eth0 inet dhcp
hostname <hostname>
name LAN Interface
pre-up /sbin/ifconfig $IFACE mtu 1492 
```

Where <hostname> is your computers host name,

I tried this but it didn't work. I found a solution though. The file in which the dsl settings are stored is */etc/ppp/peers/dsl-provider*

I simply added
```
mtu 1352
```

Everything is working perfectly now, but on */etc/init.d/networking restart* I get the following:
```

 * Reconfiguring network interfaces...                                           
 * if-up.d/mountnfs[eth0]: waiting for interface dsl-provider before doing NFS mounts
dsl-provider: ERROR while getting interface flags: No such device
Plugin rp-pppoe.so loaded.
                                                                         [ OK ]

```

I'm happy that everything is working, but the fact that I'm getting an error message bothers me.

Thanks for the help!

---

