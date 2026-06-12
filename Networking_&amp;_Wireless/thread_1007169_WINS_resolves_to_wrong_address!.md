---
title: "WINS resolves to wrong address?!"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by bsh on 2008-12-10
Hello everyone.

I have a small network of 5 computers.
It looks like this: internet -> modem-> router (smc 7004vbr, 192.168.2.1) -> gigabit switch.
on the gigabit switch there's a server (192.168.2.10 static ip, ubuntu 7.04) and four computers. they're windows machines, and are set up to use automatic (dhcp) settings. the router is the dhcp server, it assigns the ip addresses (expect to the server which is static). i have set up the router to always assign the same ip addresses based on the mac addresses, yet it is still dhcp.
i am running samba on the linux server, and it is set up as a wins server.
wins support = yes
name resolve order = wins lmhosts hosts bcast
for the safety, i have added the hosts to my /etc/hosts file, so ubuntu resolves to the correct addresses and is working well.
but samba doesn't.
if if try, for example: smbclient -L machine2,
it resolves to 192.168.2.30, but actually the ip address is ...119.
this only happens with one machine, to make it even stranger...
i have no idea why it resolves to the wrong address and why only with that machine?
the eth0 interface is set up to use the router as the gateway and primary dns server.
maybe it's a bug with the router's internal dns?

as said, when using the hosts file it works fine, but samba doesn't resolve correctly with wins.
any ideas?
thanks!

---

