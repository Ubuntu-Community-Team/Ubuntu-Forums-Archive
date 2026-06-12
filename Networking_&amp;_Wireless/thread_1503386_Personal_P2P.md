---
title: "Personal P2P?"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by mooreted on 2010-06-06
A friend and I had the idea of sharing files over the Internet, just he and I, no one else.

Things like scp, ftp, vpn really only work well if you both have a static IP address. Online storage like Ubuntu One, Box.net, Carbonite would not be practical; we have terabytes of information.

Is it possible to have your own private P2P connection?

---

### Post by 666f6f on 2010-06-06
Correct me if I'm wrong but I think you'll always need to somehow retrieve your friends IP address (or some other identifier, depending on you network layer).

For me, the easiest way would be to setup HTTP + DynDNS. If you want to share information between more friends, you can then setup a torrent tracker.

---

### Post by mooreted on 2010-06-07
Forgot about dyndns. I will look into that. That might do the trick. Thanks.

---

### Post by mooreted on 2010-06-07
Well, dyndns works, but what makes me nervous is after setting up an ftp server my port 21 is wide open for the world to hack away at.

I'm going to have to think about this.

---

### Post by 666f6f on 2010-06-07
Security is always an issue, regardless of the service you run. Some things you may want to do is enable the service only when needed it, allow only a specific address range to connect to the service and setup a firewall. I'm not a security expert though.

---

### Post by mooreted on 2010-06-07
I think what I'll do is set up another user account and point the server to that account so at least my personal account isn't the one being shared. 

I'll have to do some reading on securing it. Maybe use ssh sftp. At least I have a working shared directory.

---

### Post by 666f6f on 2010-06-07
:popcorn:

---

### Post by mooreted on 2010-06-07
Well, when I turn on ftps/ssl on vsftpd I get:

Connection attempt failed with "ECONNREFUSED - Connection refused by server".

I have port-forwarded port 22. Need to find out what vsftpd wants.

---

### Post by mooreted on 2010-06-07
Works fine without encryption.

---

### Post by 666f6f on 2010-06-07
I'm sorry, I don't know how to setup ftps/ssl, however I believe port 22 is for SSH.. Generally I've found it very easy to setup SSH (you can then scp) and/or HTTP. If you want to stick with sftp/ssl and you don't have any success in configuring it, I suggest that you start a new thread so you can attract more attention.

---

### Post by mooreted on 2010-06-07
Thanks. Only if I get stuck. Hate wasting threads. Can't test it until later but I think it's because I didn't set ssl-cert-snakeoil.key in the config file.

Maybe someone will see this and get some use out of it.

Have a good day. Have to go work now.

---

### Post by mooreted on 2010-06-08
Nevermind, I can't do it, you have to be an ubergeek to figure this crap out. I give.

---

### Post by mooreted on 2010-06-12
Turns out TeamViewer had file trasfer capability. Works great and easy to use.

---

