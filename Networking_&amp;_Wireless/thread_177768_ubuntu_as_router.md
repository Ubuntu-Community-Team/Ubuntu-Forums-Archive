---
title: "ubuntu as router"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-05-16
okay, here's what i want to do.  i have an old box onto which i've loaded a server install of ubuntu breezy.  i have no gui, and i don't intent to put one there because all i need it to do is route network traffic.

i have two network cards for this computer.  they are both detected and work fine but ... i can't get both of them to work together.
ie. i disable one nic, and the other works fine, but if i boot with both nic's enabled the machine doesn't know what do with them.

so for one, i need to know where the config files are that i need to edit via cli in order to get the machine to recognize both nic's at the same time.

and for two, i need to determine how to configure one nic for wan, and one nic for lan.

eventually, i will also need to know how to configure iptables so that there is no blockage on the lan side, but that's down the road a piece yet.

any help is appreciated.

---

### Post by dmizer on 2006-05-19
according to dmesg, my machine is attempting to assign eth0 to both of my network cards.  in fact, if i plug in my wireless card as well, ALL THREE network cards want to be assigned to eth0.

this has GOT to be something very very simple.  i just don't know enough about configuring here.

this is my interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
        map eth1
        map ath0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

iface ath0 inet dhcp
        wireless-mode managed
        wireless-essid any
```

---

### Post by resnostyle on 2006-05-19
i know smoothwall would make this a whole lot easier. i dont know much about trying to config this but smoothwall.. can do all this out of the box and is configured via browser on the client.

---

### Post by dmizer on 2006-05-19
actually smoothwall looks very interesting.  i was going to dismiss it at first.  i will use it in the near future because it's ultimately what i really need, but i have some specific reasons for needing to rely on ubuntu at this point.  primarily equipment restrictions.

---

### Post by resnostyle on 2006-05-19
what kind of equipment restrictions do you have? and have you tried googling for your problem?

---

### Post by dmizer on 2006-05-19
i'm using a laptop that i've attempted to install about 6 different distros on ... none of which were sucessful.  ubuntu was the only thing i've been able to get to support *almost* all of my hardware.  have to use a script to run my cpu fan.

i am something of a skillfull google ... er?  i'm just coming up empty.  i found just about everything i need to make the network work correctly.  i just need my machine to see 2 network adapters.

---

### Post by resnostyle on 2006-05-19
oh... well im not knowledgable enough to help you.. sorry.. using the gui would make your problem easier.. but you dont want the gui... so.... have you seen this post by the way?

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

### Post by dmizer on 2006-05-19
well, i did break down and put a gui on it, but it won't handle gnome or kde, so i'm using icewm ... which actually makes this machine quite usable.

but i am still left with configuring my network (at least mostly) by hand as a result.

---

### Post by resnostyle on 2006-05-19
is it still recognizing both nics?

---

### Post by dmizer on 2006-05-19
no ... when i do ifconfig, i still only see one nic.

but here's the funny thing.  i got fed up with it.  i booted knoppix, and i found a utility to make the second card come up.  once the second card came up, it took me about 10 minutes to configure the firewall for nat, and i now have a knoppix router/firewall online.

but i'd rather get ubuntu up as it's less cpu intensive. and significantly more responsive.

not sure exactly what the utility did, but in knoppix 4.0 it's called network card configuration.  it's a kde utility.

---

### Post by resnostyle on 2006-05-19
well at least you got it working LOL..

---

### Post by dmizer on 2006-05-19
that's just the thing ... it's not working.  i mean, i have a router/firewall in place, but i can't do it in ubuntu.  and now i am sure that it's only because i can't figure out how to make the second nic appear in my interfaces conf file.

that's why i know for sure that this is something so utterly simple.  which is why it's difficult for me to figure out via google.

---

### Post by mips on 2006-05-20
Keep in mind that both nic's cannot be in the same network. It won't work if both use 192.168.0.0 They have to be different.

I have read some posts here of eth0 & eth1 swapping the whole time but never all being assigned to eth0.

what is the output of lshw ?

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)
[http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

---

### Post by mips on 2006-05-20
Keep in mind that both nic's cannot be in the same network. It won't work if both use 192.168.0.0 They have to be different.

I have read some posts here of eth0 & eth1 swapping the whole time but never all being assigned to eth0.

what is the output of lshw ?

[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)
[http://ubuntuforums.org/showthread.php?t=89320](http://ubuntuforums.org/showthread.php?t=89320)

---

### Post by dmizer on 2006-05-21
i can't get as far as either of those threads suggest because when i boot, i only see one nic in ifconfig.  everything i have at my disposal when i boot relates to only one network adapter.

furthermore, when i boot with both network adapters attached, i get nothing ... i can use ifdown/up all day long and never pull a wan ip from either nic.

i'll have to shut down my server to post the output of lshw ... i'll edit when i've done that.

---

