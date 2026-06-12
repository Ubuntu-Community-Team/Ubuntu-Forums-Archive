---
title: "Log off sftp or ssh?"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2012-12-15
I'm using SSH to access a computer on my LAN- call it computer B.

I book marked computer B on my main computer (call it compute A).

Then, I unmounted computer B from computer A.

I thought that would prevent me from easily getting access to computer B again without going through the Places----->Connect to Server routine.

It didn't. I simply selected the book marked computer B and I was right back with access to computer B.

How do I shut down the above mentioned easy access so that even though I have computer B book marked I'll still have to use the Places------>Connect to Server procedure?

Thank you

---

### Post by chadk5utc on 2012-12-15
Im not sure this is what your after but it may help
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by PDA1 on 2012-12-15
I simply want to prevent any remote access to my computers.

Stuff that's too technical doesn't help very much.

What have I really accomplished by removing OpenSSH server and client?

---

### Post by chadk5utc on 2012-12-15
by removing server/client you have eliminated that service as possible connection even for yourself.

---

### Post by PDA1 on 2012-12-15
I like to hear that sort of talk...even if I've made a mess of things.

Like so many things in life once we learn how to do something it becomes very easy.

Having said that; when I use Remmina or Remote Desktop Viewer on my LAN (by LAN I mean those computers which are at my home all connected to a wireless router) it's so easy to connect to them and I have to conclude that if I "Mr. Dummy" can do it then someone from the outside (on the web) can do the same thing to my system.

Of what use is OpenSSH and OpenSSH client then if I can connect so easily to my own computers using the previously mentioned programs?

Thanks so much for the help.

---

### Post by chadk5utc on 2012-12-15
We all learn by doing. I have been known to make a mess and start over a time or three lol, but learned a lot from it. If you want to see what ports are open there are a number of sites that are safe and will do a port scan and tell you then you can decide what the next step is.  Security is a constant process, something that has to be thought out and maintained.
Heres a good guide [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)  
SSH is a great service and properly setup can be pretty difficult(nothings impossible) to get into without the proper key/passwords have a look here 
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by chadk5utc on 2012-12-15
Having just now read some on "Remmina" you can configure it to use ssh which will secure it making it much safer to use.

---

