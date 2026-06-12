---
title: "Sharing folders over a network within Ubuntu 10.10"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by coops351 on 2011-02-19
Right I'm not sure how to properly configure samba to allow sharing of folders on my unbuntu system to over computers over my network.

When I do try to share it comes up with 

'net usershare' returned error 255 [2011/02/19 18:13:22] param/loadparm.c:7588 (lp_do_parameter)
Ignoring unknown parameter "netbios"
net usershare add: annot share path/media/Music+Etc/Music as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only = false'
to the [global] section of the smb.conf to allow this

Any ideas on how to rectify this will be most appreciated :D

Cheers Luke

---

### Post by Morbius1 on 2011-02-19
I've never seen the first error so let's fix the second one and hope the first one goes away.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the global section:
```
usershare owner only = false
```Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Then try to share the folder again

---

### Post by coops351 on 2011-02-19
Still nothing :(

---

### Post by Morbius1 on 2011-02-19
Post the output of the following command please:
```
testparm -s
```

---

### Post by coops351 on 2011-02-19
Still nothing just coming up with errors - command not found

---

### Post by Morbius1 on 2011-02-19
You have an incomplete or corrupted install of samba I suspect. Install the following package:
```
 sudo apt-get install samba-common-bin
```
Then run testparm -s again.

---

### Post by coops351 on 2011-02-20
I reinstalled samba then did testparm -s and it come up something this time, but then when I go to share my folder still won't let me

---

### Post by coops351 on 2011-02-20
Nevermind I've sorted it now, thank you for you help! :D

---

