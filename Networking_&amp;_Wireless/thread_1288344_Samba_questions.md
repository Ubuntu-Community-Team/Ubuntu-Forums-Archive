---
title: "Samba questions"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by jeneverboy on 2009-10-11
Hi,

I have tried to setup a home network between a laptop UBUNTU (Jaunty) and a desktop XUBUNTU (9.04). I searched the forum and googled a bit but still have some questions left.

1)Is the smb.conf file case sensitive? In partocular the WORKGROUP name?

2)I made a shared folder in the smb.conf file (on the XUBUNTU machine):
```
[music]
path = /data/mp3
browseable = yes
```
And I can see the folder on the UBUNTU laptop but when I want to access it, it needs a password, I guess this is the pword of the XUBUNTU login? But when I try that it says it can't mount the thing. 

3)Just to make sure;
When you change the smb.conf (as root) and saved it, you have to restart samba on both machines? Like this:
```

sudo /etc/init.d/samba restart

```

OK, thanks Alex.

---

### Post by noelvh on 2009-10-11
Have use setup a samba user?
[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/)
I am not a samba wiz, I have just got it setup afters years of trying.
But I do know you have to set up a samba user.

Noel

---

### Post by jeneverboy on 2009-10-11
OK, I will give that a go. I thought that would not be necessary.
Thanks for the tip.

---

### Post by jeneverboy on 2009-10-11
Well, I followed your link but that doesn't work for me. On the XUBUNTU machine I made the username and restarted samba. Then when I check on the UBUNTU machine I can see the music folder->use the password and username-> then I get the following error.

> Failed to mount windows share.

For the homes folder it doesn't asks for a password all I get is:
> File doesn't exists

Alex

---

### Post by jeneverboy on 2009-10-11
Restarted samba a couple of times and now I can access the music folder on XUBUNTU from UBUNTU, so that works.

this is what I've done in the smb.conf file:
```

[homes]
   comment = Home Directories
   browseable = yes
[music]
   path = /home/alex/Music
   browseable = yes
   readonly = no
[movies]
   path = /home/alex/Videos
   browseable = yes
   readonly = no

```
For the homes folder it doesn't asks for a password all I get is:
Failed to mount windows share
Alex

---

