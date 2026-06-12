---
title: "Can't download from Server on same network"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by PaulFXH on 2009-09-14
I setup an old AMD64 computer to dual-boot Ubuntu Jaunty with WindowsXP and everything went fine.
However, in trying to send a small file from another computer on the same network, and also using Jaunty, I find that the download doesn't happen. 
I'm using [woof]("http://www.linux.com/archive/articles/60098") for the file transfer (which I've used in very many similar situations for quite some time).
When I try to download on the client through a browser (Opera 10 or Chromium) the name of the file on offer from the server is recognized but it doesn't go any further.
If I try wget in a terminal, again the file name is recognized but no download takes place. The message that appears says (translated from Portuguese) "Requisition HTTP sent, awaiting a reply" and there it stays.No othe error messages are provided.
Now I can ping from either computer to the other without problems and no firewall is active at either end.
Even more strange is that if I reboot the AMD64 computer to Windows XP, the file being served from Ubuntu can be downloaded without problem.
Can anybody suggest what might be the cause of this?

---

### Post by j7%&lt;RmUg on 2009-09-15
Try to ping the server from the machine you are sending the file from, not just the computer you are sending the file to.

---

### Post by PaulFXH on 2009-09-15
Thanks for the reply.
Indeed, I had already mentioned in the first post that I can ping from EITHER computer to the other.
That is, not just from the server to the client, but also (as you had suggested to try) from the client to the server.
Just to mention also that wget gives me (this is a more correct translation) "HTTP request sent, awaiting reply". 
Eventually, this times out and I get "Connection refused".

---

