---
title: "problems with nfs: access denied"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by jfca283 on 2013-02-04
Hi. I need to share some folders. Samba is no longer an option. Since months it crashed horrendously. I pretend to access the my laptop'home, using wifi, from my PC which is using a wired connection. I installed nfs-common and here are the config files from my laptop
***hosts.allow***
```
portmap: 201.241.169.123
lockd: 201.241.169.123
mountd: 201.241.169.123
statd: 201.241.169.123
```
***hosts.deny***
```
portmap:ALL
```
***/etc/exports***
```
/home/juan  201.215.87.163(rw,sync,no_subtree_check)
```
When i try to do...i get...
```
cine@cine-desktop:~$ sudo mount /home/cine/shared 
mount.nfs: access denied by server while mounting 201.215.87.163:/home/juan

```
i ran the last command with the firewall disabled. I googled the web but with no luck. Thanks for your time and interest.

---

### Post by schragge on 2013-02-04
I assume that *hosts.allow* and *hosts.deny* are from your PC, and */etc/exports* is from your laptop, right? Do you also have *hosts.allow* and/or *hosts.deny* on your laptop?

---

### Post by SeijiSensei on 2013-02-04
What does /var/log/syslog say on the server when you try to connect?  Try adding "insecure" to the list of options in /etc/exports?  Does that help?

I'd dump all the hosts.allow|deny stuff until you are sure everything is working.

---

### Post by jfca283 on 2013-02-05
checking mi laptop's wifi, now i see that it changed. There is a way to just writing /hostname-pc instead of 201.xx.xx.xx? because i assume that the files will need to match the IPs in their respectives config files.

---

### Post by schragge on 2013-02-05
Sure, you can specify hostnames instead of IP addresses, provided that DNS starts before the system tries to mount NFS volumes.

Or specify an IP range with netmask like 201.241.169.0/24

---

### Post by jfca283 on 2013-02-05
Ok. My laptop's exports, hosts.allow and deny files
**exports**
```
/home/juan *(ro,sync,no_subtree_check,insecure,insecure_locks
```
**allow**
```
portmap:ALL
nfs:ALL
```
**deny** is empty
when i try to mount it i get this message
```
sudo mount /home/cine/shared
mount.nfs Connection time out
```

Remember, /home/cine is where i desire to mount my laptop's home. My Pc is connected to internet by wire and my laptop via wireless. The firewall has been disabled. I don't know what to do.

---

