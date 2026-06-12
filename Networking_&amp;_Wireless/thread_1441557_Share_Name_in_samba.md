---
title: "Share Name in samba"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by dannykoay on 2010-03-28
Hi, I am newbies, 

I already construct samba in ubuntu9.10

Example folder = share-00

I would like to share this folder to windows in samba. I would like to use share name as share-00 as well

But when I click share, it do not allow me to do so?

why, any restriction for share name can not use "-"

please advise, thanks a lot

rdgs
danny

---

### Post by johnson.d on 2010-03-29
You share a folder named share-00 in Ubuntu by manually editing the file /etc/samba/smb.conf.

1) You can add the share by appending the following lines to the file: 

```
[share-00]
path = /<share-path>
browseable = yes
read only = no
guest ok = yes
```

2) Restart the samba service using the following command:

```
$ sudo /etc/init.d/samba restart
```

Now try accessing the share from another machine.

---

### Post by dannykoay on 2010-03-30
yes, i got it. thanks a lot for your helping hand, pal

now i have another question, 

if i see from windows, the sharefolder display as "test-00"

is that any possible way to configure in linux when i named it as "TEST-00" and it also appear exactly same as "TEST-00" when i browse in windows?

thanks again in advance

rdgs
danny

---

### Post by johnson.d on 2010-03-30
While mounting the share in Windows, if there is a mixture of uppercase and lowercase letters in the share name, it displays the name exactly as configured in the /etc/samba/smb.conf. If the share name has all the letters in uppercase or lowercase it displays them in lowercase only.

---

### Post by dannykoay on 2010-03-30
Hi Johnson, thank you for your kind reply,

Is there any way to make it show in UPPER CASE?

thank you

rdgs
danny

---

