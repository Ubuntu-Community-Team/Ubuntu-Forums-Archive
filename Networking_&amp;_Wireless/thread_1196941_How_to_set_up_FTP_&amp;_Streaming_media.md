---
title: "How to set up FTP &amp; Streaming media"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by radtek on 2009-06-25
I have a 9.04 64bit machine that I can remote into from my LAN via my WRT54G router. I would like to be able to access it as a FTP server and Media Streaming from the outside world. Maybe a Mail server too.

This particular machine also functions as my 2.1 sound for my TV LOL. Hence the remoting to control volume. That probably won't be much of an issue but I need advice on the easiest and best way to do all of this...?

Total ignorant noob at server stuff. Pointers and clear advice would be appreciated. I'm planning on using a graphical environment unless it affects performance greatly. No worries about RAM or HDD space.


I'm going to download the 9.04 Server edition. 

Thanks in advance 

rad

---

### Post by jonobr on 2009-06-25
Hello

When you download the server ubuntu there is no dekstop, everything is installed via the cli and thats to save on CPU cycles and ram usage.

You can install a desktop, but as said dont be shocked when you just get a command line.

That done, you can do an apt-get on vsftp which is the most easy for of ftp.

If this is for you only and not as a server service, I would however recommend you use scp (you would need to install openssh).

Once you setup your vsftp and configure it, how you connect to it depends on your service or internet providor,
they may pass ftp through to your router, some ISPs block this kind of service.
You you have a IP address that changes, you will need to use an online service which tracks your IP address and maps to a name which would refer to your system, like dynamic dns which is [HERE]("http://www.dyndns.com/services/dns/dyndns/").

Again, remember, ftp passes everything including iser names and passwords in clear text, so again SCP traversing the internet is a lot more secure.

You may need to get into port forwarding in your home router also.

In this case, you would need to tell your router (if operating a home network with multiple PCs) a packet has arrived for FTP, your router would have a setting to say, all FTP traffic is routed to pc X or y which could be ip or hostname of the receiving machine

Hope this helps

---

### Post by radtek on 2009-06-25
Thank-you this has been indeed helpful. I'm going to start fooling around with this... I'm sure my "server" will get hosed a few times  LOL but thats the learning curve. Thankfully Ubuntu is quick to install.

---

### Post by radtek on 2009-06-26
BTW... I just realized that this really isn't a true networking subject but more of a server topic. Perhaps it could be moved?

---

### Post by jonobr on 2009-06-26
I wont tell if you dont:-)

When you run into specifc problems, Im sure you can repost in the other areas,

However, I do see some odd posts in some odd places

Ciao

---

