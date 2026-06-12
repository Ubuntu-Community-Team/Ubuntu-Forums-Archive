---
title: "copying files via samba kills all networking to server"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by florenceit on 2010-06-29
Hi
I saw another post here with a similar problem, with no responses, so....here goes.

I'm trying to restore all my files to my new ubuntu server (a netbook actually) and can't! after copying for a few moments the samba shares stop working. in synaptic it says samba 2:3.4.7

as im typing this i realized I was able to copy a few large files when i was starting out so there may be some software added since thats the issue. 

 
In my scenario i found that the server does recover after a minute or two. but when copying large files it causes ALL networking to stop. funny that if i go to the server screen it is fine. Ive experienced this connecting with a windows 7 pc and a mac. the server will start responding again in a couple of minutes. when it locks up it locks up ALL networking: cant connect to the webserver, or ssh either when this happens. Just starts working again after 2 minutes. I am unable to sync this with my backup drive unfortunately. 

I did some experimenting today and found that I was able to stay connected via ssh for well over an hour with no problems. as soon as I start copying files is when it happens. I use this as a server in a home office so I need to resolve this. for now going to share a drive off my router i guess. 

have been poring through the logs and reading everything i can on this the last few days.. I switched from network manager to WICD after reading about it online somewhere. that actually did help to apparently reduce the frequency of the issue. 

does anyone have any tips? this is a new  machine/install of Ubuntu 10.4 LTS desktop version (its just easier than the server version for me even though using as a server). its a new  MSI X Slim X320. I bought it as it has the X530 Atom processor which is super efficient and I run this as a solar powered web/file/torrent/app server. In that regard im very pleased with it. 

any help appreciated.. been struggling with this for hours and hours over a few days.

thanks!

---

### Post by nixscripter on 2010-06-29
The NFS filesystem will "lock things up" because the VFS (file system layer) will block all disk access to the volume while waiting on a request.

Perhaps there is a similar effect, locking the whole volume during the file transfer. Ssh could perhaps be trying to use the mounted volume in some way? The **lsof** utility can examine this (as well as socket and pipe statistics).

---

### Post by florenceit on 2010-06-30
thanks. I narrowed down the problem further.  I use [allway sync]("http://allwaysync.com/") to make backups to my linux server from a windows 7 machine. it turns out that first i tried copying 2gb from server to local and it worked fine, now i'm copying 50gb TO the server and its going fine, 

soooo the problem only happens when running allway sync! go figure... it does multiple copies at once... can you think of any samba settings that may affect that? ive been meaning to setup rsync for windows so maybe ill just do that if i get nowhere with this, although i did pay for it and would like to see it work.

in my samba logs for this computers connection is the only errors and it hard to know what they mean. are they a result of the lost connection or do they indicate the source of the freeze up (?) 

[2010/06/30 14:20:46,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/06/30 14:20:46,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection timed out.
[2010/06/30 14:20:46,  1] smbd/service.c:1240(close_cnum)
  mattl-vaio (192.168.168.10) closed connection to service webroot
[2010/06/30 14:20:46,  0] lib/util_sock.c:738(write_data)
[2010/06/30 14:20:46,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2010/06/30 14:20:46,  0] smbd/process.c:62(srv_send_smb)
  Error writing 75 bytes to client. -1. (Transport endpoint is not connected)
[2010/06/30 14:20:46,  1] smbd/service.c:1240(close_cnum)
  mattl-vaio (192.168.168.10) closed connection to service mattl


thanks!

---

### Post by florenceit on 2010-06-30
nope.. i was wrong... locks up copying files with terracopy too, just seems to go longer before losing the connection to the drive.


darn...

---

### Post by florenceit on 2010-07-11
Hi
well i haven;t really RESOLVED this error but I just TODAY found a workable , even preferred workaround. i finally got the msi x320's wireless network card working with wicd (another problem in itself) and can connect wireless , and the problem went away. This is actually one of my other goals with this system anyhow as I could use the extra freed wired connection elsewhere. This leaves me thinking theres a driver issue with the wired lan. at some point ill look into updating it.  but for now i'd call this solved:popcorn:

---

### Post by florenceit on 2010-09-03
just for the record i switched to another netbook for my home office server and I am getting the same problems: network manager dropping network connections. switched to wicd and its better but then my screensaver drops network connections. very frustrating.

---

