---
title: "I need ftp server setup help please"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by wsonar on 2009-04-04
I am having a little trouble getting the ftp server working

I'm running ubuntu server 8.10

I have edited the file /etc/vsftp.conf

enabled a port and the same port is enabled in my firewall
and enabled local user login disabled annonmous login

Is there something I'm missing I have no problems establishing a ssh connecion

any help greatly appreciated
thanks

---

### Post by albinootje on 2009-04-04
> **wsonar said:**
>  Is there something I'm missing I have no problems establishing a ssh connecion


Ftp-servers and firewalls can be a pain :(
Are you sure you want to use a ftp-server ?

Did you restart vsftpd after editing the config file ?
What is netstat -tan|grep 21 saying ?
What is the vsftp log files saying ?
How are you testing it ? With telnet, and/or with various ftp-clients ?

Some clients have different defaults for active and passive ftp.
I recommend testing it with ncftp, lftp, and some more.

---

### Post by wsonar on 2009-04-04
I think it has to do with the firewall say I use port 20 the default to test

and I do ufw allow 20 it allows udp and tcp I tried 20/ftp but get bad port

I just want to be able to ftp files into my web server directory

I disabled the firewall but still am having trouble will test a few things what you said and report back

---

### Post by albinootje on 2009-04-04
> **wsonar said:**
> 
I do ufw allow 20 it allows udp and tcp I tried 20/ftp but get bad port


For certain ftp setups you need to have port 21 (ftp) and 20 (ftp-data) open afair.

---

### Post by wsonar on 2009-04-04
Ok so I connected with lftp is there something I need to do to use a client like gftp?

---

### Post by albinootje on 2009-04-04
> **wsonar said:**
> Ok so I connected with lftp 

cool.
> is there something I need to do to use a client like gftp?

Gftp probably handles the passive vs active ftp connection differently.

I have this in the vsftpd.conf of my local file server, which works fine with Gftp, Nautilus and others :
```

pasv_enable=YES
pasv_min_port=49152
pasv_max_port=65534
pasv_address=10.22.22.222
pasv_promiscuous=YES

```

---

### Post by wsonar on 2009-04-04
ok so I got it to work with lftp with the firewall enabled allowing 20 and 21 I notice my router when I choose to forward ftp it defaults to start 20 end 21

for security I changed my ssh port could I do the same with my ftp as long as I choose two ports?

still couldn't get gftp to connect with ftp but I changed it to ssh and selected my ssh port and connected right up so essentially accomplishing the same thing

---

### Post by wsonar on 2009-04-04
> **albinootje said:**
> cool.


Gftp probably handles the passive vs active ftp connection differently.

I have this in the vsftpd.conf of my local file server, which works fine with Gftp, Nautilus and others :
```

pasv_enable=YES
pasv_min_port=49152
pasv_max_port=65534
pasv_address=10.22.22.222
pasv_promiscuous=YES

```

Ill give this a try thanks

---

### Post by wsonar on 2009-04-04
should the pasv_address= be the client ip or the server? my client is setup for dhcp currently

---

### Post by albinootje on 2009-04-04
> **wsonar said:**
>  still couldn't get gftp to connect with ftp but I changed it to ssh and selected my ssh port and connected right up so essentially accomplishing the same thing
I was already wondering whether you would want to replace ftp by ssh..
If you work with system users (instead of virtual ftp users), and you're using this over the internet, then your plain text ftp traffic can theoretically be sniffed, and then the attacker could log in via ssh with the same username/password.

---

### Post by albinootje on 2009-04-04
> **wsonar said:**
> should the pasv_address= be the client ip or the server?
The server ip.

---

### Post by wsonar on 2009-04-04
> **albinootje said:**
> I was already wondering whether you would want to replace ftp by ssh..
If you work with system users (instead of virtual ftp users), and you're using this over the internet, then your plain text ftp traffic can theoretically be sniffed, and then the attacker could log in via ssh with the same username/password.

so ftp passwords are transfered in plain text?

so I would need to create a virtual ftp user? or I can just use ssh because the password wouldn't be in plain text then?

---

### Post by albinootje on 2009-04-04
> **wsonar said:**
> so ftp passwords are transfered in plain text?

Yes, unless you start using a ftp-server which uses SSL.
> 
so I would need to create a virtual ftp user? 

Virtual ftp users make it harder for an attacker to gain access once your username/password would be sniffed.
> 
or I can just use ssh because the password wouldn't be in plain text then?
Yes, I'd go for ssh, and I'd remove the ftp-server unless you use it only locally on a "trusted" LAN.

Gftp can do ssh, but so can e.g. Nautilus (sftp://), and Konqueror (fish://) too.

---

### Post by wsonar on 2009-04-04
cool thanks for the info

---

