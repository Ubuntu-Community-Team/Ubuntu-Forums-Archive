---
title: "i cant understand dns, its like a chicken and egg dilema"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by mushy365 on 2012-11-30
Ok, firstly, my goal would be to have my own server which i could use to give people hosting. I've already got scripts to add users, to create virtual hosts in apace to link to whatever their domain name will be, and ftp access to a locked down public_html directory.
 
Where i am hopelessly confused is DNS. Now i know what DNS is, it maps domain names to ip addresses. What i don't understand is how it can work. For example. 
 
I install bind9 to use as the nameserver for the sites i intend to host. I register a domain online and have to specify dns servers. Obviously i cannot link to my bind9 server because how would it know where to go. for eg
 
ok i got a request for mushyhosting.com, ok to work out the ip i pass it to the nameserver they have given me, the nameserver is ns1.mushyhosting.com. Wait if i dont know the ip of mushyhosting.com how can i go to mushyhosting.com to look it up?
 
If i specify a different nameserver to point to my website. That would work, but what if i add a client to my webserver, now he wants a site. If he registers his site with another nameserver, then how can they link it to my IP
 
I seriously can't work it out, its boggles my mind, i can't even formulate it in a decent question it confuses me so much. I'd appreciate it, if someone can give me a childs answer to this, thats basic and clear so i understand.

---

### Post by SeijiSensei on 2012-11-30
Unix machines use a file called /etc/resolv.conf that lists the IP addresses of the servers to be used to resolve names precisely for the reasons you describe.  Traditionally it looks like this:

```

domain example.com 
nameserver 8.8.8.8
nameserver 8.8.4.4
search example.com myotherdomain.net

```

The IP addresses above are Google's public DNS servers.  The "search" directive tells the resolver how to handle "unqualified" host names, ones which don't have the domain attached.  So if ran a command like "ping rocky" it would first look in /etc/hosts to see if there's an entry for "rocky" there, then it would look up "rocky.example.com" on Google's servers and if that does not exist, it would try "rocky.myotherdomain.net".

[Since 12.04 Ubuntu uses a different resolver so the resolv.conf file has only one entry, 127.0.0.1, the address of the "localhost" interface on the machine.  In essence it's running a mini-DNS server on the workstation that is accessed by communicating with 127.0.0.1.  I mention this only because you might be puzzled if you look at resolv.conf on a recent Ubuntu machine.]

Does that help?

---

### Post by mushy365 on 2012-11-30
I understand the resolv.conf file, i have edited mine to use openDNS. However, i'm confused by a person/company who creates their own nameserver/DNS server can use that to direct people to their own domain from the internet.
 
Like if i registered a domain now, i would have to specify which nameservers to use. so i register mushy.com, but if i want to use my own DNS server i.e ns1.mushy.com we have a chicken and egg situation.
 
How can i instruct someone to get the ip from ns1.mushy.com when mushy.com is the ip that they are looking for in the first place.

---

### Post by iponeverything on 2012-11-30
[http://searchnetworking.techtarget.com/definition/start-of-authority-record](http://searchnetworking.techtarget.com/definition/start-of-authority-record)

---

### Post by JKyleOKC on 2012-11-30
The registrar from which you obtained "mushy.com" might provide a nameserver that's already tied into the worldwide DNS system, to provide the matching IP address to the rest of the world. My registrar does that, but not all of them do, and for it to work, you must have a static IP address on the Internet rather than the dynamic IP address that most ISPs provide. If your registrar doesn't provide the service, perhaps your ISP will do so. Once the main record is present in a DNS server that's already tied in, it can include the NS records to point to your locally-maintained BIND9 server.

If you don't have the necessary static IP accress, investigate dyndns.com and other providers of such services; they provide the necessary link, and many of them are free (but ad-supported) while others have nominal subscription fees.

---

### Post by capscrew on 2012-12-01
> **mushy365 said:**
> ...
I seriously can't work it out, its boggles my mind, i can't even formulate it in a decent question it confuses me so much. I'd appreciate it, if someone can give me a childs answer to this, thats basic and clear so i understand.
Maybe reading [**_[SIZE="2"][COLOR="DarkSlateGray"]this[/COLOR][/SIZE]_**]("http://www.gnc-web-creations.com/dns-tutorial.htm") will help.

It helps to understand that if the DNS is *not* resolved at either your hosts file or a DNS server like Google's (8.8.8.8 ),  then the request is set to on of the ***root servers*** to provide the IP address of the authoritative DNS server.

---

