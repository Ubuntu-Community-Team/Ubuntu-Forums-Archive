---
title: "Strange HDD activity with smbd"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2010-10-17
Hi,
I recently installed a NAS device. My wired network system is gigabit using a Linksys WRT610N router. 

The NAS device is 8T, (4 x 2T) in a RAID5 array. There is currently less than 1G stored on the NAS. I have disabled all non essentials on the NAS devise so it's really only serving files. My desktop is Ubuntu Lucid (64) ostensibly gigabit,  Everything seems to working as it should.

However, as long as the smbd is running there is constant HDD activity on my desktop PC and the NAS device. The amount of traffic seems minimal but it is annoying to constantly hear the NAS and  my desktop rattle on when really there should be nothing happening.
The NAS device's samba logs seem clean.


The desktop's logs raise two issues:

l
> 2010-10-17 18:19:06    smbd/server.c    457    smbd_open_one_socket    smbd_open_once_socket: open_socket_in: Address already in use
2010-10-17 18:19:06    smbd/server.c    1069    main    smbd version 3.4.7 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009
2010-10-17 18:19:06    smbd/server.c    1115    main    standard input is not a socket, assuming -D option
2010-10-17 18:19:06    smbd/server.c    457    smbd_open_one_socket    smbd_open_once_socket: open_socket_in: Address already in use


Is the "open_socket_in: Address already in use" significant?

 /var/log/samba/log.localhost gives me a heap of these recurring entries:

> 
[2010/10/17 07:51:55,  0] param/loadparm.c:8328(check_usershare_stat)
  check_usershare_stat: file /var/lib/samba/usershares/ owned by uid 0 is not a regular file
[2010/10/17 07:51:55,  0] smbd/service.c:1202(make_connection)
  localhost (::ffff:192.168.1.9) couldn't find service 


Can anyone give me a heads up on what might be happening?

TIA

---

