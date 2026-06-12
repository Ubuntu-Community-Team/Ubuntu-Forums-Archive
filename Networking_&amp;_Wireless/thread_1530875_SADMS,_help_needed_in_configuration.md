---
title: "SADMS, help needed in configuration"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by dobby156 on 2010-07-14
Hi, firstly I hope this is the right place.

 I am wanting to give linux a better go as it were, however to really do so I need integrate into my current system(s) by getting it to utilise into the windows domain structure.

Ideally I would be able to login with NT user credentials from the AD, and have access to the user profile files.

I am currently trialling this in VM before formatting using lubuntu.

I have installed SADMS and got it 'Panal' to run, however I am having some issues configuring it. I have read the tutorails on the site and I am still struggling to get it to mesh properly.

The data it wants:
DNS:
realm:
kdc:
this domain's Netbios name:
this host's Netbios name:
Domain User group:
Host allow
OU to place host in:	Optional
WINS server;	optional
Admin login:	I know these
admin pswd:	^^ :D

Here is what I do know. My DNS server is at 192.168.1.2 on \\SERVER
the active directory i connect to is also on \\SERVER and is called mydomain.local
the linux box is called Client 2 and is running Lubuntu
the  DHCP setting are 192.168.1.XXX in 255.255.255.000
\\Server is running windows server 2008

Thanks for the help!

---

