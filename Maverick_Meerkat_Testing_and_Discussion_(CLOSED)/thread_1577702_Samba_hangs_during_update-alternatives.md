---
title: "Samba hangs during update-alternatives"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by IanW on 2010-09-19
[Bug #641519]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/641519")

Anyone else?

---

### Post by scradock on 2010-09-19
Yup - bug #640880

The person responding closed the bug, but I agree it's still a problem....

---

### Post by Anduu on 2010-09-19
Yes it has happened to me twice.

Killing the process and running  sudo dpkg --configure -a seems to clean things up.

---

### Post by autocrosser on 2010-09-20
That was my answer also---did not happen the last Samba update, so I thought the bug was closed....

---

### Post by IanW on 2010-09-20
> **Anduu said:**
> Yes it has happened to me twice.

Killing the process and running  sudo dpkg --configure -a seems to clean things up.

That just hung again for me.

My workaround was to:-
```

sudo rm /var/cache/apt/archives/lock /var/lib/dpkg/lock

reboot

sudo apt-get purge samba
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install samba

```

---

### Post by seeker5528 on 2010-09-20
Assuming this is the same thing I saw....

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/640449](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/640449)

... this doesn't have anything to do with alternatives, that just happens to be the last message on the screen at the time the process halts.

I didn't have a problem with the last SAMBA update, but I didn't see anything in the change log indicating there was a fix either.

I did see a change log entry in the debian unstable updates recently that looked like it was for a similar type of issue that changes something related to the stopping/starting of samba during updates.

Later, Seeker

---

### Post by DevHead on 2010-09-20
Downloaded the daily package (09/20/2010) and samba installation went without a hitch.  I did however hit the same problems with those from around 5-6 days back (if I remember correctly).

---

