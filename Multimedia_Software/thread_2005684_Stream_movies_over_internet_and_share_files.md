---
title: "Stream movies over internet and share files"
date: 2012-06-18
forum: Multimedia Software
---

### Post by bavman on 2012-06-18
Hello, I recently build a file sharing server that as of right now shares files between the computers on my LAN through samba. It works great, but now my next step will be to open it up so I can access my files when I'm away from home and be able to stream media from it over the internet, and also be able to grab documents and files and send stuff if I need to store it (kind of a personal cloud). I'm not too sure what protocol I will need to use (eg vpn, ssh..etc etc). could someone please help start by pointing me in the right direction and what would be my best bet to get this done? I'd also like to keep my stuff secured so something like ftp is probably out of the question.

---

### Post by papibe on 2012-06-18
Hi bavman.

There are several steps to accomplish that.

If you're unfamiliar with that concepts mention below, take a look at this is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

This would be the main steps:
[LIST]
[*]Set your server with a LAN static IP.
[*]Install openssh-server on your server.
[*]Test LAN ssh access to your server.
[*]Optional: change the standar ssh port (22) to a different, preferable higher value.
[*]Subscribe to a Dynamic DNS service. There are free and pay options (examples: DynDNS, no-ip, zoneedit, etc).
[*]Either install and setup the package ddclient, or (better if available) set your DDNS client in your router.
[*]Forward the ssh port in your router to your server.
[/LIST]
Now you are ready to test accessing your server over the internet.

Important: do not try to access your server using its public IP, or dynamic name from inside your own LAN. The proper way to test access if from outside your network. For example, an internet café, public library, a friend house, or using your phone or tablet's 3G service (be sure to NOT being connected to your LAN though).

I hope that points you in the right direction, and tell us how it goes.
Kind Regards.

P.S.: In general, it would be not possible to stream video using a typical household ISP connection (not enough bandwidth). Music may be possible, but it all depends on your upstream limits.

---

### Post by joe_newbie on 2012-06-18
I have an ssh server set up, I am not sure how this helps us to stream video over the internet. I use MPD to serve up my music online, in combination with MPod on my iphone, and vlc on computers elsewhere. I get about 500KBps upstream, for standard definition video that should do. I have thought about using NFS, but would like something more platform independent.

Joe

---

