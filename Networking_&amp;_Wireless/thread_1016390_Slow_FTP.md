---
title: "Slow FTP"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Ingenium on 2008-12-19
This problem started with 8.04, and I continue to have it in 8.10. When I try to upload a file via FTP, it always caps out at 30KB/sec. It doesn't matter the server; I've tried it with various servers on the internet and computers on my LAN. Other computers also running 8.10 on the same network can upload fine. It doesn't matter if I'm on wired or wireless, both have this cap. I've tried command line FTP, Filezilla, Nautilus's built in FTP client, and gFTP. I have even removed all iptables rules to no avail.

Anyone have any ideas what might be the problem? Everything else works fine, including sftp.

---

### Post by doas777 on 2008-12-19
I'd say ask your ISP, but they wouldn't answer the question. they'd just ask if all the lights on your cable/dsl modem are on. they may be throttling uploads. My cable runs at 768Kbps up, which is about 96KB/sec. 

if you can get a another box with another OS to connect from your place, and you get the same result, you can confirm that it is your ISP or your local network equipment.

also, FTP upload is only as fast as the receiving server. is it under a load?

---

### Post by Ingenium on 2008-12-19
It isn't the ISP. I have three computers on my LAN. I still have this cap when uploading to them, but they can transfer to eachother just fine. One is also running 8.10.

---

### Post by Ingenium on 2009-01-09
I tried disabling IPv6, as I heard it could cause slow transfers sometimes, and am having the problem. Any suggestions?

---

### Post by Ingenium on 2009-03-15
I'm still having the issue...anyone have any ideas? 

Just to clarify again, this is NOT an issue with my internet. I can upload via HTTP or on Bittorrent and max out at 200KB/sec. LAN transfers via samba go at several MB/sec, yet FTP transfers on the LAN still have this cap. It's with every FTP client/server combination that I've tried.

---

### Post by PattiMan on 2009-03-17
I have the same issue. If I use Mac OS or Windows I can upload with 3 till 4 MB/sec to my FTP server on my LAN. But with Ubuntu I get 700 kB/sec max. The IPv6 solution or other FTP clients are not helping me :(

Maybe a driver issue? I'm using Intel® PRO/Wireless 3945ABG

---

### Post by Ingenium on 2009-03-17
I also have an Intel 3945ABG, but I have the issue not only on wireless, but also on wired with my Intel 82573L. Same speed on both. Do you also have the issue on wired?

---

### Post by PattiMan on 2009-03-17
I only have problems with wireless. LAN is working fine. Sorry ;)

Edit: installing the [compat wireless drivers]("http://www.intellinuxwireless.org/?p=iwlwifi") solved my problem. I'm now at 3 till 4 MB/sec. Maybe it was the combination with disabeling IPv6. I'm not sure.

---

