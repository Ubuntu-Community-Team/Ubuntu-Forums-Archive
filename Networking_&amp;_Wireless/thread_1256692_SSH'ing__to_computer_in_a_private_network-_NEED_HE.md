---
title: "SSH'ing  to computer in a private network- NEED HELP"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by random_attack on 2009-09-02
I'm trying to ssh to my friends computer to copy a rather large video file to my computer. He has an ip address of the form 192.168.... so forth. As I understand it, this is only a local ip address. How can I connect to his machine? He lives in Indiana and I'm in California so I can't get close enough to him to actually transfer the files on his network. Changing router settings or things like that might be difficult as we both live in apartments and don't really control the internet. Is this possible to do?? Any help would be greatly appreciated. 

Thanks

---

### Post by scorp123 on 2009-09-02
> **random_attack said:**
> Is this possible to do?? Any help would be greatly appreciated. You could use something like Dropbox and exchange files that way. With Dropbox you could leave your Internet settings "as is". A direct SSH connection won't be possible unless you configure port-forwarding on his router.

Dropbox:
[http://www.getdropbox.com](http://www.getdropbox.com)

---

### Post by reacocard on 2009-09-02
you need to either adjust the router config to forward the ports, or find a third-party server you can both access and use that as an intermediary. connecting directly is impossible in your current setup.

---

### Post by crysty13 on 2009-09-05
Hi, I need some help to configure my ubuntu box to accept ssh connections from outside local network. here's the thing:

I want to ssh to my pc from outside the local net. I have a router and I configured it to forward port 22 to my pc. 

ssh is installed to my pc (ubuntu) and I do can access it from other machines on my local net.

port forwarding is correctly set up since I can connect to ssh on another PC, but having windows. (So port forwarding works on the router. I did changed back the router to forward to my pc and not the the windows pc)

So I susspect there's something fishy with the firewall. 

I also use vpn to connect to work and also rdc. I tried to use several tools to configure the firewall, but all i got is to block everything. 

I can find my way around a linux box, but I'm still new to linux. 

Any ideas on how to debug this situation? 10x

---

### Post by crysty13 on 2009-09-05
It looks like I can ssh the router and it works. But when I connect the vpn to work (usign kvpn) it stops working. Why? What can it be done?

---

