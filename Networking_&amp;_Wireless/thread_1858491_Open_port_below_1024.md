---
title: "Open port below 1024"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by sakishrist on 2011-10-12
Hello,

My ISP does not allows incoming connection below port 900. This, in combination with the linux restriction of only being able to open ports above 1024, results in a big problem for me.

I would like, for instance, to have a torrent client, but I do not want to run it as root.

Thanks in advance!

---

### Post by haqking on 2011-10-12
> **sakishrist said:**
> Hello,

My ISP does not allows incoming connection below port 900. This, in combination with the linux restriction of only being able to open ports above 1024, results in a big problem for me.

I would like, for instance, to have a torrent client, but I do not want to run it as root.

Thanks in advance!

that makes no sense ?

your ISP blocks email, web browsing etc which are all ports below 900.

linux does not restrict anything you do with ports.

and torrent clients are usually way up in the port range or whatever you set it to

---

### Post by Dangertux on 2011-10-12
I am also very confused here, most BT clients use ports in the 40,000's for the file transfer. Trackers are usually updated over http/s though. 

I'm not sure how your ISP could filter ports 0-900 that would essentially make your connection useless. Assuming you mean that you can not run a server on those ports, however reverse connections are allowed which would make sense. In which case it shouldn't effect your BT client, or any other client for that matter. FTP will likely have to be in passive mode, and you probably won't be able to seed through BT. 

That being said Linux, Windows , Unix and pretty much every other OS do not allow creation of sockets on privileged ports (0-1024) unless you are a privileged user (root). As a regular user your BT ports should be readily available.

---

### Post by sakishrist on 2011-10-12
Ooops ... I meant to say that the ISP blocks above and including 900 and only allows below 900.

---

