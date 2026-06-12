---
title: "linux networking"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by mgc1952 on 2006-01-20
Hi - I've been using linux since 99. I have always been the only linux machine on the home network and became fairly comfortable with samba usage. Now after long last my wife has allowed me to turn her box into a suse 10 box.

How do I access files on her box, vice versa to my box, her printer etc.

thanks for any help. And of course this is important for I would love my wife to stay in the stable, safe linux world

again thanks for any help
Mark

---

### Post by morphodone on 2006-01-20
[QUOTE=mgc1952]...her printer etc.[/QUOTE]

her printer should be running on the cups server...
you can add her printer with her ip address, such as:

ipp://her_ip_address:631/printers/her_printer

just look on the kde control panel in suse for the above information

---

### Post by mgc1952 on 2006-01-20
Hi - thanks for the printing tip...can anybody send me in the right direction on manipulating files between machines etc. 

thanks
Mark

---

### Post by morphodone on 2006-01-20
[QUOTE=mgc1952]Hi - thanks for the printing tip...can anybody send me in the right direction on manipulating files between machines etc. 

thanks
Mark[/QUOTE]

you should be able to setup samba on her computer as well with yast...

or you could setup nfs - but i have no idea how to do nfs since i have 
always used samba in case there is a windows client present

---

### Post by mips on 2006-01-21
If both machines are linux then you dont need samba. look at nfs I think.

---

### Post by mgc1952 on 2006-01-21
thanks - I will go off and research nfs - Mark

---

### Post by mips on 2006-01-21
[https://wiki.ubuntu.com//SettingUpNFSHowTo](https://wiki.ubuntu.com//SettingUpNFSHowTo)
[http://www.ubuntu.com/support/documentation/faq/nfs-server](http://www.ubuntu.com/support/documentation/faq/nfs-server)

---

