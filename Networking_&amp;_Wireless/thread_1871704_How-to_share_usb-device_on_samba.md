---
title: "How-to share usb-device on samba"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by Azyx on 2011-10-29
Hi.
Have a local network and a computer who are a samba-server. I have tried share /media as read only in smb.conf. The folder appears in network, but when i try to mount the folder /media from a client, It say I don't have permisson to read.

/Cheers

---

### Post by Morbius1 on 2011-10-29
I'm guessing it's formatted in either ntfs or fat32. If it is it will mount with access only to you and no one else. Samba determines who may access a share but it can't override Linux permissions.

You never stated how you created the samba share. If you used Nautilus to share it then:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section:
```
force user = your-user-name
```Change "your-user-name" to your local login user name.

Then restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down after a samba restart and try to access it again.

If instead you created classic samba shares then just add the "force user" line to the share definition itself in smb.conf.

---

### Post by Azyx on 2011-10-29
> **Morbius1 said:**
> I'm guessing it's formatted in either ntfs or fat32. If it is it will mount with access only to you and no one else. Samba determines who may access a share but it can't override Linux permissions.

You never stated how you created the samba share. If you used Nautilus to share it then:



Correct. I have both fat and ntfs as usb-device, and also an Apple hfs+-filsystem.

I  shared by edit smb.conf in the end. I share a another folder ([COLOR=Red]500GB[/COLOR]) folder booth as guest and user with write-access (as You helped me before :)). But this share (**in bold**) are only for read or guest as follows:

```
[[COLOR=Red]500GB-guest[/COLOR]]
path=/home/Azyx/500GB
read only = yes
guest ok = yes
[[COLOR=Red]500GB[/COLOR]]
path=/home/Azyx/500GB
read only = no
guest ok = no
valid users = Azyx
[B][BlackMedia-guest]
path=/media
read only = yes
guest ok = yes[/B]
```

> **Morbius1 said:**
>  If instead you created classic samba shares then just add the "force user" line to the share definition itself in smb.conf.

Where exactly, do I add "force user". I don't what to change/destroy anything on the other share(s) [COLOR=Red]500GB[/COLOR], and [COLOR=Red]500GB-guest[/COLOR]

/Cheers

---

### Post by Morbius1 on 2011-10-29
[B][B][BlackMedia-guest]
path=/media
read only = yes
[COLOR=RoyalBlue]force user = [/COLOR][/B][COLOR=RoyalBlue]Azyx[/COLOR][/B]
[B][B]guest ok = yes

[/B][/B]Be careful when you share /media**[B]. **[/B]Depending on what you have mounted in fstab or not you could inadvertently share something you don't want to share.

---

### Post by Azyx on 2011-10-29
> **Morbius1 said:**
> [B][B][BlackMedia-guest]
path=/media
read only = yes
[COLOR=RoyalBlue]force user = [/COLOR][/B][COLOR=RoyalBlue]Azyx[/COLOR][/B]
[B][B]guest ok = yes

[/B][/B]Be careful when you share /media**[B]. **[/B]Depending on what you have mounted in fstab or not you could inadvertently share something you don't want to share.

I don't have any /media mounted in fstab, so It should not be any trouble? Can Ubuntu add /media to fstab automagic?

---

### Post by Azyx on 2011-10-29
> **Morbius1 said:**
> [B][B][BlackMedia-guest]
path=/media
read only = yes
[COLOR=RoyalBlue]force user = [/COLOR][/B][COLOR=RoyalBlue]Azyx[/COLOR][/B]
[B][B]guest ok = yes

[/B][/B]Be careful when you share /media**[B]. **[/B]Depending on what you have mounted in fstab or not you could inadvertently share something you don't want to share.

Thanx again for exellent help :)

/Cheers

---

### Post by Morbius1 on 2011-10-30
> I don't have any /media mounted in fstab, so It should not be any trouble?I'll give you an example of the type of problem I was cautioning you about. Let's say you dual boot but you don't automount the other OS in fstab. When you bring up Nautilus you will see the other OS on the left panel and when you select it it automatically mounts to /media/LABEL. If you share /media you have just inadvertently shared that other OS's partition to everyone on your LAN. The same thing will happen to every non-system partition that you don't have mounted in fstab or any partition that you specifically mount to /media.

As long as you are aware of that or if this scenario doesn't relate to you that's fine.

---

### Post by Azyx on 2011-10-30
Ok. I see and I have that in mind. Thanx :)

/Cheers

---

