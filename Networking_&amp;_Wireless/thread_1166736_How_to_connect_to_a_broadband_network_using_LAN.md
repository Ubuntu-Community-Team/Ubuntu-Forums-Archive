---
title: "How to connect to a broadband network using LAN?"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by Yashpal1985 on 2009-05-22
Can any one help me out in connecting to a wired network in UBUNTU 9.04 using LAN port in a laptop.

---

### Post by x33a on 2009-05-22
open a terminal, and type:
```
sudo pppoeconf
```

follow the instructions and you are all set to go.

---

### Post by Yashpal1985 on 2009-05-22
Thanks....Do i need the IP address and Do i need my ID as well as password to connect to internet??

---

### Post by x33a on 2009-05-22
well i assume you are using an adsl connection with dynamic ip. so, the ip will be automatically assigned to you by the isp.

if you are using bridged mode, you'll need your connection username and password.

---

### Post by Yashpal1985 on 2009-05-22
I use VISTA currently in that it prompts me for ID and Password. And yes i am using a ADSL connection.That means i wont require the IP rite...

---

### Post by x33a on 2009-05-22
> **Yashpal1985 said:**
> I use VISTA currently in that it prompts me for ID and Password. And yes i am using a ADSL connection.That means i wont require the IP rite...

since you enter the username and password, means you are using bridged mode. so simply, enter the command i posted earlier and follow the instructions to have a working internet connection.

and, no computer can be on the internet without an ip :). it's just that for a dynamic ip, we don't have to enter the ip ourselves.

---

### Post by Yashpal1985 on 2009-05-22
Thanks a lot "amigo".... and....ya i forgot....computers require IP :p :lolflag:

---

