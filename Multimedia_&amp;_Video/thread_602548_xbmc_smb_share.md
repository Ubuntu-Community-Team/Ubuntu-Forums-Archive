---
title: "xbmc smb share"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by cabrando on 2007-11-04
I set up an smb share to stream from my ubuntu machine to my xbox. I can browse the share and see my files but when I try to play them nothing happens. I've tried various formats (mp3, mp4, xvid), but none of them will play. Any help appreciated.

---

### Post by fedleo on 2007-12-04
Up. 
Really interested in because I have similar troubles: I can play from shared folder just some videos, avi at most. Never had problem with music. :(

---

### Post by barney_1 on 2007-12-04
Mine is up and working without any problems.  Here is the related line from /etc/samba/smb.conf

```
[Download]
path = /Flanders/mp3
available = yes
browsable = yes
public = yes
writeable = no

```

---

### Post by fedleo on 2007-12-04
It's not as simple as you think... But thanks anyway for your early reply.
My smb seems to be correct, but some videos works just if I download on xbox hdd.  
Here's my share setup on /etc/samba/smb.conf:

```
[VideoOnServer]
path = /media/Dati/Video
comment = Video sul server
available = yes
browsable = yes
public = yes
writable = yes

[MusicOnServer]
path = /media/Dati/Musica
comment = Musica sul Server
available = yes
browsable = yes
public = yes
writable = yes
```

---

### Post by barney_1 on 2007-12-04
Could it possibly be a file permission issue?

Check permissions and ownership with:
```
ls -l
```

You can change the permissions of the entire tree with:
```
sudo chmod -R 755 /media/Dati/*
```

---

### Post by fedleo on 2007-12-05
> **barney_1 said:**
> Could it possibly be a file permission issue?

You said could be, I say "IS" a permission issue! :D
You drive me to the correct solution, thanks so much.

---

### Post by barney_1 on 2007-12-05
Glad to hear it worked out.  XBMC and Ubutnu make a really nice networked package once everything's set up.  If you have a tuner card make sure you check out running a Mythtv backend on your ubuntu box and the python scrip XbmcMythtv as a frontend on the xbox.

---

### Post by fedleo on 2007-12-05
Yeah I'll do! Thanks again.

---

### Post by tmcmulli on 2007-12-08
Ok, I'm confused... I see post suggesting Ushare, but here it looks like you were able to connect your Xbox 360 to Ubuntu with just SMB??  I can't get my Xbox 360 to see the SMB share...

little help??

---

### Post by fedleo on 2007-12-08
Nope we are speaking about a SMB share for a modded XBOX using XBMC, not the 360. I don't think you can do the same with an xbox360 even if hacked. Sorry for that.

---

### Post by koshari on 2008-01-28
this is a little odd, 

every now and again the ubuntu samba share dissapears from view on the network, however if i run the command to change the permissions in my samba shared dir back to 744 the share automagicly re appears! even if i havnt changed any permissions!

something must happen like the samba sevice egts restarted after checking file permissions that rebroadcast the service.

anyway running the CLI command to change permissions fixes my problem temporarily but it would be nice to know whats causing the samba share to become invisible.

---

