---
title: "Samba &amp; Firestarter disater"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by nkv1 on 2011-05-07
since ufw is junk that cant block travian.com and other ads, i installed firestarter which did the job.
Now i cant get samba to work like it did before.
I did what was on in tread [http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542),
I have 2 ubuntu 11.04 desktops 32bit and 64bit
1. PC 64bit completely unable to see other ubuntu desktop samba share files, but is able to see own samba share. (192.168.1.100):)
2. PC 32bit unable to see any samba shares own or 1. desktop (192.168.1.102):)
rooter  (192.168.1.1):)
uses dhcp to assign ip for lan and internet 
i did:
1.allowed in firestarter samba servis like in tread to 192.168.1.0/24
2.changed /etc/firestarter/inbound/setup as said
3. changed /etc/nsswitch.conf as said
Any1 any ideas?

---

### Post by nkv1 on 2011-06-18
samba went down the drain, ssh is a way to go belive me, way better since i am useing only linux to linux lan

---

