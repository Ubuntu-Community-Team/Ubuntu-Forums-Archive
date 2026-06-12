---
title: "Samba share requires servernetbiosname"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by justanotherhack on 2011-05-12
Greetings everyone!

I got a strange problem. When trying to connect to a Samba share, it requires to send the servernetbiosname. Let me try to describe it.

At my university anyone has a personal web directory, which is hosted at another university. It's on a SuSE server, shared via Samba. There are several universities on this server, using the same Samba with different NetBIOS names.

There is an open Cisco WiFi, anyone can connect. But to use it, you have to use VPN (Anyconnect for example or in my case the module Ubuntu provides).

Now my problem is, I can't easily connect to any share on the server (tried several shares from several machine to be sure it's not just me). After trying several variants on bash, I finally figured out, that I have to supply the servernetbiosname to get it to work.

Not working:
```
root@cmp:~# mount.cifs //svr1.sd.domain.net/htdocs /tmp/mnttst/ -o 'user=uname,domain=DOM' -v
Password: 
mount.cifs kernel mount options: ip=123.123.123.123,unc=\\svr1.sd.domain.net\htdocs,,ver=1,user=uname,domain=DOM,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Working:
```
root@cmp:~# mount.cifs //svr1.sd.domain.net/htdocs /tmp/mnttst/ -o 'user=uname,domain=DOM,servernetbiosname=svr1' -v
Password: 
mount.cifs kernel mount options: ip=123.123.123.123,unc=\\svr1.sd.domain.net\htdocs,servernetbiosname=svr1,ver=1,user=uname,domain=DOM,pass=********
```

With Windows it works without a problem. (With Mac it doesn't, but I don't care much about that ;) .)

Now the question is, if one can solve that some other way. The nice applets coming with several distros aren't giving an option to supply the servernetbiosname. Is there a way to setup the mount, so it can "guess" the right NetBIOS name, since it is also the name of the machine? Or is there an option that I can ask the other university to try, so the Samba server would behave less demanding?

Puting an appropriate entry into the /ets/hosts doesn't work either.

Thanks in advance for any hints.

Adios
Oliver

---

### Post by capscrew on 2011-05-12
> **justanotherhack said:**
> Greetings everyone!

I got a strange problem. When trying to connect to a Samba share, it requires to send the servernetbiosname. Let me try to describe it.

At my university anyone has a personal web directory, which is hosted at another university. It's on a SuSE server, shared via Samba. There are several universities on this server, using the same Samba with different NetBIOS names.

Do you mean different hostnames or possibly FQDN's ?> 

There is an open Cisco WiFi, anyone can connect. But to use it, you have to use VPN (Anyconnect for example or in my case the module Ubuntu provides).

Now my problem is, I can't easily connect to any share on the server (tried several shares from several machine to be sure it's not just me). After trying several variants on bash, I finally figured out, that I have to supply the servernetbiosname to get it to work.
Have you tried browsing to the share you want?  If you are on a VPN then you should be able to see the share (//SERVER/share) if you are using the CLI you should be able to do the same browsing with the term *smbtree*.> 

Not working:
```
root@cmp:~# mount.cifs //svr1.sd.domain.net/htdocs /tmp/mnttst/ -o 'user=uname,domain=DOM' -v
Password: 
mount.cifs kernel mount options: ip=123.123.123.123,unc=\\svr1.sd.domain.net\htdocs,,ver=1,user=uname,domain=DOM,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Working:
```
root@cmp:~# mount.cifs //svr1.sd.domain.net/htdocs /tmp/mnttst/ -o 'user=uname,domain=DOM,servernetbiosname=svr1' -v
Password: 
mount.cifs kernel mount options: ip=123.123.123.123,unc=\\svr1.sd.domain.net\htdocs,servernetbiosname=svr1,ver=1,user=uname,domain=DOM,pass=********
```

With Windows it works without a problem. (With Mac it doesn't, but I don't care much about that ;) .)

Now the question is, if one can solve that some other way. The nice applets coming with several distros aren't giving an option to supply the servernetbiosname. Is there a way to setup the mount, so it can "guess" the right NetBIOS name, since it is also the name of the machine? Or is there an option that I can ask the other university to try, so the Samba server would behave less demanding?

There is no way that the mount command can browse for what *might be correct.*  When you *explicitly* mount a SMB reasouce you should already know what it is.

I believe you are not using the correct incantation when using the mount command.  The parameter *servernetbiosname * is used to force the use of port 139 when resolving netbios names. 

The way I have successfully used the mount command is like this```
mount -t cifs //SERVER/share <and your options>
```  The SMB protocol doesn't know what a FQDN such as *[COLOR="Red"]svr1.sd.domain.net [/COLOR]*means.  so when you add it using *servernetbiosname *you are in essence providing this: //SERVER .  That is added to the the share to provide you with //SERVER/share.  (or in your case //svr1/htdocs).  You can use either slash or  backslash as a delimiter.  Microsoft Windows treats forward slashes and back slashes in this context as equivalent.
> 

Puting an appropriate entry into the /ets/hosts doesn't work either.
Hostnames in this instance are not relevant.> 
Thanks in advance for any hints.

Adios
Oliver

---

### Post by doas777 on 2011-05-12
also, remember, NetBIOS names are limited to 15 chars. when MS started using TCP/IP as the transport protocol for SMB, replacing NetBUI, they added FQDN support into UNC pathing, but I believe Samba is an implementation of the original NetBUI-based (local network only) protocol.

---

### Post by justanotherhack on 2011-05-13
Browsing the share didn't work either. Neither with Nautilus, nor smbtree (hey, I learned a new comand ;) ). I know that the share is there, since I can mount it with Windows.

mount.cifs is the same as mount -t cifs and both work or work not when trying to connect to the same share.

I tried to solve it with an entry in /etc/hosts, so I can mount the share only using the server name instead of the FQDN, in hope the command uses it as NetBIOS name as well, but since it didn't work, I scraped that quickly. Buuuuuut...

[QUOTE=doas777]also, remember, NetBIOS names are limited to 15 chars. when MS started using TCP/IP as the transport protocol for SMB, replacing NetBUI, they added FQDN support into UNC pathing, but I believe Samba is an implementation of the original NetBUI-based (local network only) protocol. [/QUOTE]

That reminder got me on the track again. The FQDN is of course longer and maybe the command can't interpret it correctly. I checked the /etc/resolv.conf to find out that the VPN response sends new domain and search entries, which do not include the domain of the server at the other university. Changing the search entry to the right domain solved the problem for the GUI. With Nautilus I can now browse the server and mount the share. On the CLI it still doesn't work that way, but that isn't crucial, since I can enter the servernetbiosname there manually.

So thanks guys, you really helped me to solve this :) . Maybe I can get the network admin to modify the VPN response, so it'll work for everyone who's not using Windows.

---

