---
title: "odd wireless problem"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Turiko on 2009-03-04
This is the first time i've been able to get this far in wireless networking in any linux, and i have connection to the internet right now. i can ping to adresses and everything... but my DNS isn't working for some reason. I've tried DHCP and i've tried DHCP adress only, and of course also static (wich ended up not working).
I've tried manually setting the DNS server to 208.67.222.222, wich is an openDNS server.

so basically, i can view sites if i can just get the ip, but this isn't exactly handy :D. Could anyone help me? i really don't know what's wrong, but i seem to have connection, so i guess it should be relatively easy to fix.

Also, what is the search domain option for and what am i supposed to enter there?

Thanks in advance! :)

---

### Post by N04h on 2009-03-04
If you are connecting to a router confirm that the router does in fact have the DNS settings in there. Have you tried following these instructions: [http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html")

Where are you seeing a "Search Domain" option.  I'm unfamiliar with that portion.

---

### Post by Turiko on 2009-03-04
well yes, the DNS settings in my router (Dlink DI-524) point to  that openDNS ip i said before. I'm on intrepid ibex, and there are 3 tabs when editing my wireless connection: Wireless, wireless security, and ipv4 settings. 

In the first tab i enter the SSID required and select the infrastructure mode. the rest i leave open and mtu at automatic.

in the security tab i just select WPA & WPA2 personal and give in the password.

for the last tab, here is a screenshot:

[[IMG]http://img217.imageshack.us/img217/9849/screenp.th.jpg[/IMG]](http://img217.imageshack.us/my.php?image=screenp.jpg)

i read somewhere that the search domain is your ISP's site, so i tried that. I still don't get what it is for tough...

PS: i'm doing this in virtualbox, i tried setting this network up in an older version without VM a long time ago, but if it works in a VM, it'll work outside of it too, right?

---

### Post by N04h on 2009-03-04
If I understand search domains correctly you probably should be leaving this blank.

Try putting in your ISP's DNS servers instead of the openDNS servers in your router and leaving the DNS server blank on your ubuntu machine.

---

### Post by Turiko on 2009-03-04
The problem is that i have no idea what the ip of my isp's dns server is :P i always used the DNS 195.238.2.21, but that's because a friend gave me the ip a long time ago.

---

### Post by N04h on 2009-03-04
Check your ISP's website. 

Try These:

167.142.225.3
167.142.225.5
167.142.225.4

---

### Post by Turiko on 2009-03-05
My ISP apparently does offer DNS servers, but they call it "technical only DNS" and ask a fee for it. I've tried all 3 of your DNS ip's and still can't get a name like [www.google.be](www.google.be) to work... 209.85.229.103 works, and it's the same site.

I'm really clueless about what's wrong here - i have connection, but no DNS, and none of the DNS servers seem to work for me

---

### Post by Turiko on 2009-03-07
does anyone have any more ideas?

---

### Post by N04h on 2009-03-07
How are you setting your DNS servers?

Have you tried setting them in your interfaces file?

---

### Post by ugm6hr on 2009-03-07
To summarise:

You can ping IP addresses:

```
ping -c 3 208.67.219.101
```

But can't ping / resolve web addresses:

```
ping -c 3 www.opendns.com
```

I have had a similar problem when travelling with my netbook, and believe that this is an issue with some routers and Linux.  I'm afraid I never solved my issue either: [http://ubuntuforums.org/showthread.php?t=1063064](http://ubuntuforums.org/showthread.php?t=1063064)

---

