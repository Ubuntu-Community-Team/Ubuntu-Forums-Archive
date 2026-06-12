---
title: "Can't resolve what windows does"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by slick666 on 2009-02-11
I have an Ubuntu development system at work :)

the problem that I'm having is there are some internal machines that I cannot resolve the name of. I can resolve them on the windows box and if I take the ip address resolved from windows I can use that on the linux box no problem. Does anyone know how the windows box is resolving some dns names that the linux box cannot?

---

### Post by FishRCynic on 2009-02-11
are you trying to browse windows/samba shares with nautilus?

if so lately nautilus is having issues.

---

### Post by eibgrad on 2009-02-11
Same here.  Ever since moving to 8.10 (both 32-bit and AMD64), I'm finding Ubuntu isn't resolving windows names.  Whether it's nautilus, totem, whatever, it will only work w/ explicit IP addresses when referencing local Windows resources.  Everything worked fine w/ 8.04 (and of course I can resolve all my Windows resources by name from other Windows PCs just fine).  Ended up adding the names/ips to the /etc/hosts file until Ubuntu fixes the problem.

---

### Post by FishRCynic on 2009-02-11
i enabled a samba wins server and configured all the beasties to use it - now even xp pro talks to xp home consistently.

---

### Post by slick666 on 2009-02-17
I'm not using nautilus I'm simply opening a terminal and typing

> ping HOSTNAME

and I get a failure right off the bat (can't resolve HOSTNAME) I can't change any of the network configuration since I don't own it. But I have a windows box and I have a Linux box they both should be able to resolve the same machines.

---

### Post by eibgrad on 2009-02-17
FYI, I'm having the same problem w/ Fedora 10 as well, so it's not just Ubuntu but something deeper, in the kernel I suppose.

---

### Post by slick666 on 2009-02-18
Is there a way I could see how windows resolves the computer? I'm thinking of something like tracepath but for DNS queries. Anyone know how to do this?

---

### Post by slick666 on 2009-02-23
Bump bump.

No one figured this one out before?

---

### Post by brown705 on 2009-02-26
I'm having the same issue with 8.10.  It could resolve Windows hostnames a few days ago, and now it will not.  

Strange thing is that it used to pull IP info from a Windows Server 2003 DHCP server, but yesterday it lost even Internet access.  Then I noticed DHCP was filling only the IP address and there was bad info for DNS and Gateway.  I statically set the IP info now, and I have Internet access, but even though my DNS is set to the Active Directory server, it cannot resolve ANY hostnames.  I do not see a place to enter WINS though.  How do I give it a WINS server?

---

