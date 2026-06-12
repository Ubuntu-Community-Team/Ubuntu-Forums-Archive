---
title: "Terminal Server Client just stopped connecting"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by greymoose58 on 2005-12-13
Hi all,

I am running Breezy at home and connecting to a clients Win2k Terminal server over the Internet. I was ontheir network less than 48 hours ago. When I tried to connect today the connection timed out.

I've spoken with the guy who does their IT support and as far as I can tell nothing has  changed at either end. There are two possible issues that we could think of:

1. I was granted a 90 day client licence which has now expired. The problem with this theory is that there is no client licence (expired or otherwise) showing for me  on the server. 

2. The server uses a non-standard port to connect on so I might be hitting the wrong port. This seems unlikely as I haven't changed anything and I could connect before. However I'd like to change the port TSC is going out on to test the theory but I can't figure out how to do it. :confused: 

Has anyone had a similar experience? Alternatively can anyone show me how to change the outgoing port for TSC? 

Thanks.

---

### Post by mlomker on 2005-12-15
[QUOTE=greymoose58]Has anyone had a similar experience? Alternatively can anyone show me how to change the outgoing port for TSC? 
[/QUOTE]

You mean on the windows side?  **man rdesktop** for the client options.

```

rdesktop servername:port

```

---

### Post by greymoose58 on 2005-12-15
Thanks, I couldn't figure out what the man entry was under. That will be useful in the future.

Strange as it may seem (or not, given that the server runs Windows) I tried again the next day and it just worked. Go figure.

---

### Post by mlomker on 2005-12-15
Ah, you must use one the graphical tools to launch it.  I made one-line shell scripts a KDE launcher menu...it puts in the password and logs me right in.  I admin a Windows network, so I use it a lot.

---

