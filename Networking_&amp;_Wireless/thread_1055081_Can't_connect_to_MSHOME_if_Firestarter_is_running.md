---
title: "Can't connect to MSHOME if Firestarter is running"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Mickser_52 on 2009-01-30
I am running Windows XP and Ubuntu 8,10 on dual boot. If I have firestarter turned on I cannot connect to MSHOME network but if I turn off Firestarter I _can_connect to MSHOME network. How do I configure Firestarter to allow access to MSHOME.

Any help welcome please.

---

### Post by specialcharacter on 2009-01-31
Hi Mickser,

I haven't used Firestarter much myself, but here are the ports you will need to open for Samba and Windows file sharing:

    * netbios-ns - 137/tcp # NETBIOS Name Service
    * netbios-dgm - 138/tcp # NETBIOS Datagram Service
    * netbios-ssn - 139/tcp # NETBIOS session service
    * microsoft-ds - 445/tcp # if you are using Active Directory

    * Port 389 (TCP) - for LDAP (Active Directory Mode)
    * Port 445 (TCP) - NetBIOS was moved to 445 after 2000 and beyond, (CIFS)
    * Port 901 (TCP) - for SWAT service (not related to client communication)

---

