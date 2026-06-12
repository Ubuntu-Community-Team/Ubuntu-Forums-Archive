---
title: "client host name"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by Bone Down on 2006-02-22
okay so here is what I am attempting to figure out.
after numerous searches I have not been able to find the answer to my question, so I am posting it here for all of you to see if you might be able to point me in the correct direction.

Below is a copy of my dhcp clients table ip# 113 is my linux machine on the network how do I get it to show a name like the others (others being windows and printer)? I have three other linux machines not on at the moment or they would be in the list. bat_cave will soon be turned into a linux box as well.
```

Client Host Name  	                        IP Address  	  	
linford00	                                 192.168.99.106	
SENIOR	                                       192.168.99.108	
BAT_GIRL	                              192.168.99.109	
BAT_CAVE	                             192.168.99.110	
DHT002UA5190CMS	                        192.168.99.112	
 	                                           192.168.99.113
HP1215	                                       192.168.99.115
```

---

### Post by rudiz on 2006-02-22
sudo gedit /etc/hosts

change ur pcname

do the same in /etc/hostname

---

### Post by Bone Down on 2006-02-22
my /etc/hosts file output:
```
127.0.0.1 localhost.localdomain localhost DC-Comics

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
what do I need to change?

my /etc/hostname output:
```
DC-Comics
```
what do I need to change in here?

---

### Post by Bone Down on 2006-02-22
to the top for the evening crowd

---

### Post by Bone Down on 2006-02-27
for before bed hoping someone can answer this one for me.

---

### Post by claes on 2006-02-27
Edit the file /etc/dhcp3/dhclient.conf and remove the remark from the line: 

#send host-name "andare.fugue.com";

And change what name the dhcp client will send to the server.

Claes

---

### Post by Bone Down on 2006-02-27
[QUOTE=claes]Edit the file /etc/dhcp3/dhclient.conf and remove the remark from the line: 

#send host-name "andare.fugue.com";

And change what name the dhcp client will send to the server.

Claes[/QUOTE]
Thanks Claes

---

