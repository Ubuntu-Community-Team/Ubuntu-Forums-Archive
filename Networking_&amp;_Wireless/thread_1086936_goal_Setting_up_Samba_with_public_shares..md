---
title: "goal: Setting up Samba with public shares."
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by Centx on 2009-03-04
So, this isn't the first time I have had problems with samba, but the other times, I've just copy-pasted stuff until it worked, in some way or another. Seeing how so many have troubles with Samba and filesharing on LANs, a feature that really should "just work" out of the box, I want to try to fix my network, and hopefully understand how this time around.

**Objectives **
1 - "See" all the machines running samba, discover them on the LAN.
2 - Be able to access all of the machines (list shared folders).
3 - Access public shared folder and list content (files).
4 - Access the content (files).
4 - Write to writeable public shares.

**Network overview**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=105327&stc=1&d=1236193745[/IMG]

vectra(stat:10.0.0.20): always-on multimedia server - running arch linux
xeon(stat:10.0.0.11): not always on desktop - running ubuntu linux 8.10
core: not always on destkop - running windows xp
laptop: not always on laptop - running windows vista

**So far**
Well, I've set up a network called [nettverk], and so far samba just seems totally random in how it views the network. It still sees the shares I had before I started out with a clean smb.conf, but it can't see vectra at all (well, it did at one point, then it disappeared again). Unless there is some other way to tell it about shares than smb.conf, the former makes no sense. The latter makes no sense at all.

I've activated WINS  on the machines, and since vectra is always-on, I've made that the main WINS server.

The problem is that I can't really see what's wrong, i guess.

my smb.confs
vectra:
```
[root@vectra samba]# cat smb.conf
[global]
netbios name = vectra
server string = Samba on %h
workgroup = NETTVERK
encrypt passwords = yes
wins support = yes
wins server = 10.0.0.20
name resolve order = wins lmhosts hosts bcast


[test]
path=/test
guest ok = yes
guest only = yes
browseable = yes
security = share
[root@vectra samba]# 

```

and xeon:
```
[root@xeon samba]# cat smb.conf
[global]
netbios name = xeon
server string = Samba on %h
workgroup = NETTVERK
encrypt passwords = yes
wins support = yes
wins server = 10.0.0.20
name resolve order = wins lmhosts hosts bcast


[test]
path=/test
guest ok = yes
guest only = yes
browseable = yes
security = share
[root@xeon samba]#

```

---

### Post by Iowan on 2009-03-04
> # Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.Looks like you have two machines trying to be both.

---

### Post by Centx on 2009-03-04
> **Iowan said:**
> Looks like you have two machines trying to be both.

Yeah, removed that one. Now using the default setup for ubuntu - printers. Of course, this is not what I wanted at all, but at least it works for now.

"places > network" apparently is bugged too, but IDK, since for all I know, it can be issues with smb.conf. Funny how a so important feature, seemingly basic and not too complicated is so hard to get right :(.

Well, there is a new day tomorrow, maybe I'll try again.

So far it seems like my objectives has changed to something like:
1: Be able to discover machines running samba in their workgroups with "places > network"
2: Be able to list all shares on machines running samba, whether the shares are password-protected, public or w/e.

config of shares:
-inaccessible to everyone except owner.
-public read
-public read, owner write.

---

