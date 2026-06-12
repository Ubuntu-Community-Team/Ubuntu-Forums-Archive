---
title: "Multiple Netbios showing from my Ubuntu server"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by whoopn on 2010-11-30
Hi, I have a fileserver that I want to share out samba shares.

However, i configured samba to have another netbios (SAN) and my windows box still sees whoopn-SAN which is the name I gave to my server when i installed it.  

Now I am using 9.10 and I know that i can create a share from the gnome gui in nautilus and that appears to be a windows like share.  How can I turn OFF the windows like shares that ubuntu does out of the box and use ONLY samba?  I ask because there appears to be a conflict of permissions b/w samba and this stuff.

Thanks in advance!

---

### Post by Morbius1 on 2010-11-30
>  However, i configured samba to have another netbios (SAN) and my windows  box still sees whoopn-SAN which is the name I gave to my server when i  installed it.  I assume you mean you used "netbios name = SAN" in smb.conf?

Did you restart samba:
```
sudo service smbd restart
```OR
```
sudo service samba restart
```> Now I am using 9.10 and I know that i can create a share from the gnome  gui in nautilus and that appears to be a windows like share.  How can I  turn OFF the windows like shares that ubuntu does out of the box and use  ONLY samba?  I ask because there appears to be a conflict of  permissions b/w samba and this stuff.The "gnome gui in nautilus" is a Samba share. Samba calls it Usershare. Been part of Samba for years. To remove them just go back into nautilus and un-share them.

If you don't remember exactly what you shared you can run the following command to list all the usershares:
```
net usershare info --long
```

---

### Post by whoopn on 2010-11-30
Thank you for that last bit of info there!

net usershare info --long

Showed me the share, I don't have the gui immediately available to me, how can I remove that share via the command line?

---

### Post by Morbius1 on 2010-11-30
```
net usershare delete share-name

```
Replace share-name with the appropriate name.

---

### Post by whoopn on 2010-11-30
Well I did that and now I don't get any netbios at all from the SAN.  Arghhhhh!

Samba is up, here is my smb.conf file:

```

 [global]
netbios name = SAN
workgroup = WORKGRPOUP
server string = File Server
security = user
map to guest = bad user
guest account = whoopn

[data]
path = /media/Humongoid/media
guest ok = yes
read only = no


```

That should show a computer called "SAN" on my Windows 7 box correct?  Samba is running and I have confirmed that twice :)

Thank you so much for your help so far!

---

### Post by whoopn on 2010-11-30
Actually, scratch that.

Now I DO see the "SAN" computer on my windows box but when I try to access it i am prompted for a password, I thought I had it wide open...am I wrong?

---

### Post by Morbius1 on 2010-11-30
In order for guest access to work linux file permissions have to be in sync with samba. So for true guest access:

```
 ls -dl /media/Humongoid/media
```
Must come back with:
> drwxrwxrwx

---

### Post by whoopn on 2010-11-30
You are exactly right thinking it was permissions, but it wasn't permissions of the folder, but of the volume :)

Thank you so much, I am working now!  
:D :popcorn: :p

---

