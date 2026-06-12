---
title: "Various NFS problems"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by joenobody12312 on 2012-09-27
Hello All, Hope you can help me.

I've setup nfs according to the ubuntu guide. I pretty much installed nfs-kernel-server and setup my /etc/exports. Everything was great and working as expected. I can setup the shares from other computers. I was super happy.

Cut to next day, when I run the mount command on a remote client, it times out after a few minutes. showmount -e <nfsserver> times out. Well that sucks, what do the logs on the server say. I've got no logs. No /var/log/nfs* anything. syslog only has the following lines repeated:

Sep 27 21:36:58 <server> kernel: [98661.931643] Inbound IN=wlan0 OUT= MAC=24:77:03:83:90:f0:00:d0:59:d7:39:01:08:00 SRC=192.168.1.97 DST=192.168.1.122 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=23779 DF PROTO=TCP SPT=795 DPT=2049 WINDOW=14600 RES=0x00 SYN URGP=0 
Sep 27 21:37:46 <server> kernel: [98710.064910] Inbound IN=wlan0 OUT= MAC=24:77:03:83:90:f0:00:d0:59:d7:39:01:08:00 SRC=192.168.1.97 DST=192.168.1.122 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=23780 DF PROTO=TCP SPT=795 DPT=2049 WINDOW=14600 RES=0x00 SYN URGP=0 

So firstly, I'd like to know if someone can tell me how to turn on some useful NFS logging or maybe just where to find it. I'm losing my mind not being able to find anything. Second, possibly why was this working yesterday and not today, with seemingly no changes to the server or client.

Some other information:
ubuntu 12.04
showmount -e localhost on server gives:
Export list for localhost:
/media/data *

I've tried: 
/etc/init.d/nfs-kernel-server restart

hosts.allow has:
ALL:ALL
hosts.deny is empty:

firewall disabled:
ufw disable

---

### Post by agillator on 2012-09-27
First, absolutely eliminate a firewall as a problem. On both machines, assuming you have access to both, run 'sudo iptables -L -v -n --line-numbers' and see what you get. For testing purposes what you want is simply three chains  with nothing but POLICY ACCEPT entries. That means nothing is blocked. If you get anything else it will need to be checked out. Also make sure there is not another firewall involved - a firewall on the LAN, for example, that all traffic goes through. Once you KNOW a firewall is not the problem that you can begin to troubleshoot other possibilities.

---

### Post by joenobody12312 on 2012-09-27
Yep, that was it. Firewall. I also installed firestarter and apparently that was still enabled. Disabled that and it's working again. I need to read up on my iptables stuff.

But also, do you know how to enable or find NFS logging? I still don't see anything in my logs.

Thanks a lot!

---

### Post by agillator on 2012-09-27
I haven't worked with NFS in a long time, so I am not sure about logging. You might take a look here [http://docs.oracle.com/cd/E19253-01/816-4555/rfsadmin-101/](http://docs.oracle.com/cd/E19253-01/816-4555/rfsadmin-101/) and see if that helps or gives you an idea of where else to look. One thing I did notice, though, was that the majority of the logging appears to be done by the server. Client logging is sparse, supposedly. So I would be sure to check the logs on the server.

---

### Post by joenobody12312 on 2012-09-28
Yeah I saw that link, but I don't have any of those files are nfslogd on my ubuntu. Not sure if it's related or a different environment.

---

