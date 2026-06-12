---
title: "Can't connect to network after a move."
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by FreakyT on 2006-06-08
I set up Ubuntu Dapper (very late beta) on my computer while I was at home, where the computer gets its address through DHCP and connects through a router, and the network functioned fine.  Now, I've returned to school, where computers still get their addresses through DHCP, but I can't seem to connect to the network anymore.  (My Mac and Windows XP partition didn't seem to enounter any problems.)

If I type /etc/init.d/networking stop, I get the message:
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address

(192.168.1.1 is the address of the router at home, so that shouldn't be appearing, I don't think)

Any ideas?

Thanks!

---

### Post by deadgobby on 2006-06-08
[QUOTE=FreakyT]I set up Ubuntu Dapper (very late beta) on my computer while I was at home, where the computer gets its address through DHCP and connects through a router, and the network functioned fine.  Now, I've returned to school, where computers still get their addresses through DHCP, but I can't seem to connect to the network anymore.  (My Mac and Windows XP partition didn't seem to enounter any problems.)

If I type /etc/init.d/networking stop, I get the message:
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address

(192.168.1.1 is the address of the router at home, so that shouldn't be appearing, I don't think)

Any ideas?

Thanks![/QUOTE]

See is your answer lays here.

[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

### Post by FreakyT on 2006-06-08
OK, I looked at the network setup sections, and they mostly just involved changing settings in the Network Connections control panel, which doesn't seem to have any effect on the situation.

Thanks anyway!

Any other ideas?

---

### Post by deadgobby on 2006-06-08
Have you tried this
[https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28DHCP%29](https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28DHCP%29)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=DHCP&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=DHCP&titlesearch=Titles)

---

### Post by anti-lite on 2006-06-08
im having a similiar problem with ubuntu.... breezy badger...

i installed... and the wireless on the mylaptop worked fine... then i left a coffee shop and came back a day later... and the net wouldnt work... even though is shows im connected.... i couldnt load  a website....


come to find out.... ihave to start terminal... and login as superuser.... and then in terminal... i start mozilla.... and the net works...


how can i change the permissions... or whatever needs to be done... so that it connects when im a regular user???



any ideas

---

### Post by FreakyT on 2006-06-08
OK, the static DNS thing doesn't apply here, I don't think, because the school uses DHCP to tell the computer the DNS server addresses.

I also tried running ping as root, as per anti-lite's suggestion, and I still got
connect:Network is unreachable

---

### Post by deadgobby on 2006-06-09
[QUOTE=FreakyT]OK, the static DNS thing doesn't apply here, I don't think, because the school uses DHCP to tell the computer the DNS server addresses.

I also tried running ping as root, as per anti-lite's suggestion, and I still got
connect:Network is unreachable[/QUOTE]
 Have you talk to the MIS department at your school? Or yet, the computer class? If they have a solution. Please let us know.
Gobby

---

