---
title: "problem with net connection"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by muthusamy on 2009-12-27
Hi, Im new to Ubuntu.  I am using XP & Ubuntu 9.04 with dual booting.  I am getting net connection with XP.  I got connection using sudo ppoeconf command in ubuntul till day before yesterday.  But now a days I am not getting net connection.  I'm in Tamilnadu (India) and using BSNL broad band with UT300R2U modem.  Plz help me.

thanks in advance.

---

### Post by dineshs on 2009-12-30
What error message are you getting when you dial in Windows XP.If your broadband is OK in XP,try to ping 4.2.2.1 from Ubuntu after connecting
```
ping 4.2.2.1
```
and post the output

---

### Post by x33a on 2009-12-30
post the output of
```
cat /etc/network/interfaces
cat /etc/resolv.conf
```

also, post the output of
```
ping -c 4 192.168.1.1
```

---

