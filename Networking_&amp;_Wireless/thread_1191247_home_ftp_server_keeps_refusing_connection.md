---
title: "home ftp server keeps refusing connection"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by chippanfat on 2009-06-18
Hi all, I'm not sure if this is the right place to post but here goes.

I've got my self an ftp server with ubuntu server 9.04 and Gadmin ProFTP

I've set the server up so i can connect internally and transfer files, as you do.

so I've tried to make my server available to the outside world for my use .

I'm using a Netgear DG834 and i've forwarded the ports by following the tutorial on this page :
[http://kbserver.netgear.com/kb_web_files/N101145.asp#FR114PAnchor](http://kbserver.netgear.com/kb_web_files/N101145.asp#FR114PAnchor)

I've forwarded the ports for ftp and ssh. Both incoming and outgoing connections

and the people in #ubuntu-cym and #ubuntu-uk have all said that, thats all i need to do.

but the connection is still being refused by the server.

---

### Post by jonobr on 2009-06-19
I recommend that you run a trace to figure where the problem is.

If you look only at ftp for example,

run  on the server

```
sudo tcpdump -vvXns0 port 21 
```

Do the ftp from the remote location and see if any packets are received at your server.
If you dont see them, then either your port mapping is wrong or not working, or your ISP is blocking the port number your using

If you see traffic coming in, see if theres a response.
If there is, you could post the results and I could try and see if there are any clues.

Cheers

---

