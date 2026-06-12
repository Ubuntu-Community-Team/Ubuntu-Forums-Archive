---
title: "Cant access Samba shares from Ubuntu"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by manco1911 on 2011-05-31
Hi guys, im sorry to bother you with this silly question.. but its giving me a headike all ready.. :D

Ok, i have an ubuntu server running at home.. everythong going smooth. I installed samba yesterday and after testing, it was working fine. 

But today i find that i cant access from my ubuntu box (desktop), now running 11.04 (i was able to access yesterday, when i tested the config). 

I CAN access from my XP and Win7 virtualboxes.. and also from another win7 on the house.. 
So server is working good aparently.. 

This is all i modified from the default config file:
```
####### Authentication #######
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user
   security = share
   guest account = nobody
[Guest Share]
   coment = Guest access share
   path = /share
   browseable = yes
   writeable = yes
   guest ok = yes
   public = yes
[Descargas Torrents]
    coment = share de Descargas Torrent
    path = /home/XXXX/Downloads
    browseable = yes
    guest ok = yes
    public = yes

```

And i also changed the domain name, (which if i change, i does afects on the Winxxx boxes). 

I know this config its not a security mayhem, but just trying to keep 1 step at a time.... 

Thanks in advance guys!

---

### Post by manco1911 on 2011-06-16
up... 
someone ?

---

