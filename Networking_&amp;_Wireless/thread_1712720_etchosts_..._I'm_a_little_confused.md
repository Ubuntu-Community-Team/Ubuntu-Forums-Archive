---
title: "/etc/hosts ... I'm a little confused"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by Nick Kruger on 2011-03-23
p { margin-bottom: 0.21cm; }a:link {  }  

 ETC/HOSTS/  … I'm a little confused  
 

 Man Page very simply has :
 127.0.0.1 localhost
 

 My /etc/hosts has :
 127.0.0.1 localhost.localdomain  localhost
 

 The Server Guide has :
 127.0.0.1 localhost
 127.0.1.1 ubuntu-server
 

 Other documentation insists I add FQDN:
 127.0.0.1 jupiter.solarsystem   localhost.localdomain  localhost
 

 Now, I have assigned a static IP on eth0
 192.168.1.100  jupiter.solarsystem
 

 I also added IP for Apache on eth0:1
 192.168.1.101  [www.bluejade.za.net]("http://www.bluejade.za.net/")
 

 Now my /etc/hosts file looks like :
 

 127.0.0.1   - not sure
 127.0.1.1   - jupiter  (why what's this for)
 

 192.168.1.100     jupiter.solarsystem    jupiter
 192.168.1.101    [www.bluejade.za.net]("http://www.bluejade.za.net")    jupiter
 

 192.168.1.5    mickymouse.solarsystem  (my windows machine)
 

 I would very much like to add Samba server
 I suppose I use eth0:2
 192.168.1.102    samba file server     ,or is it 
 127.0.1.2            samba file server ??
 

 Can anyone direct me to appropriate documentation on this subject ?
 

 Thanks
 Nick Kruger

---

### Post by Thund3rstruck on 2011-03-23
127.0.0.1 is loopback, in other words your local machine. 

/etc/hosts is typically the first place resolution occurs and most development Intranets that are heterogeneous use hosts resolution a lot so you don't have to deal with change management to get name resolution to a development server. 

the syntax is:
```

ipaddress hostname

```

For example in my hosts file I have a setting:
```

192.168.2.10 baileyweb01 mp3cms music

```

This means that I can open firefox and in the url bar type:

[http://baileyweb01](http://baileyweb01) or [http://mp3cms](http://mp3cms) or [http://music](http://music) and all of these sites are directed to [http://192.168.2.10](http://192.168.2.10)

Be sure to put one entry per line.

---

### Post by Nick Kruger on 2011-03-23
Hi Thund3struck,

Thank you  ... yes, understanding is slowly dawning on me.

Network seems to be working now - doing some testing.

Thanks,
Nick

---

