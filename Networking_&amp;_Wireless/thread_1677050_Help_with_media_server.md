---
title: "Help with media server"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by cyberjar09 on 2011-01-28
Hi i am a new Ubuntu user and am still learning the ropes ...

1) I would like to set up my old desktop to run as a media server from which I can access all my photos/home videos/movies/music from anywhere in the world over the internet ...

problem is, i dont know where to start... hence the post 

2) Also, I would like a solution wherein I can remote boot my desktop (very weird request i know) so that I can use the media server only when required...

Thanks in advance, 
love open source!

---

### Post by mickwombat on 2011-01-28
Hi,

You will need to setup Samba on the server.  Try to go for the simplest approach.  Google 'samba simple setup'.

If you want to access from anywhere over the internet, use openvpn to extablish a connection to the server and then you can just browse to the folders you setup in Samba.

To wake up the server, search on google for 'wakeonlan ubuntu' or 'magic packet ubuntu' and setup accordingly.

You'll need a dyndns hostname for your router and have to setup various port forwarding stuff etc.

Make sure everything works for you when your connected on the same network as the server, and then go a test from a friends house.

Good luck

:P

---

### Post by cyberjar09 on 2011-01-28
Brilliant! 

Thanks Mikrowombat ... ill get right to it ... and report back in case of any problems 

is there any guide to doing this exact thing available ? it would lessen the load ...

Also, I would like to know which app I can use to access the media on my N1 

open source rocks..!

---

### Post by cyberjar09 on 2011-02-03
im reading up on how to set up an openvpn server and there are different versions... 

There is 1.x which has a disadvantage of one server and one client 
there is 2.0 which is apparently harder to set up ...

my question is: is it only one client at a time or just one client, period. 

im asking because i may want to access the files from my phone, other computers etc...

thanks..

---

### Post by cyberjar09 on 2011-02-04
is'nt there a guide that someone can point me to that explains how this is done step by step? 

not really an expert here... :confused:

---

### Post by dmizer on 2011-02-04
VPN servers are somewhat complex to configure without quite a bit of knowledge and/or trial and error. This was my best resource when I first tackled the same project: [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

It's not easy, but believe me when I say that it is most certainly worth the effort.

---

### Post by cyberjar09 on 2011-02-04
> **cyberjar09 said:**
> im reading up on how to set up an openvpn server and there are different versions... 

There is 1.x which has a disadvantage of one server and one client 
there is 2.0 which is apparently harder to set up ...

my question is: is it only one client at a time or just one client, period. 

im asking because i may want to access the files from my phone, other computers etc...

thanks..

> **dmizer said:**
> VPN servers are somewhat complex to configure without quite a bit of knowledge and/or trial and error. This was my best resource when I first tackled the same project: [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

It's not easy, but believe me when I say that it is most certainly worth the effort.

thanks dmizer, I have read the introduction of this guide and got stuck at the version 1.x and 2.0 ... hence my question which is still unanswered.

---

### Post by dmizer on 2011-02-04
> **cyberjar09 said:**
> thanks dmizer, I have read the introduction of this guide and got stuck at the version 1.x and 2.0 ... hence my question which is still unanswered.

OpenVPN is in the Ubuntu repositories, you should use it. The version available to you in the repositories is 2.x

Client connections are unlimited provided that your servers up speed is capable of handling multiple inbound connections.

---

### Post by SeijiSensei on 2011-02-04
For a simple tunnel between two machines, I recommend 
[http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html).  

I don't know if it will work with your phone, though.  I've only used it to connect between computers.  My guess is that if there's an OpenVPN implementation for your phone, you should be able to configure it to use a static key.

You can support multiple machines this way as well.  I run a number of tunnels to separate machines by putting individual .conf files in the server's /etc/openvpn directory.  At any time, most of these processes are idle, so they really put no load on the server.  Even when an OpenVPN connection is active, it consumes few resources.  Just now I copied a file over the tunnel and saw the openvpn process on the gateway require just 3% of the CPU.  That's on an old Pentium 4, too.

You can take the whole "road warrior" approach with certificates and all, but if you're just trying to build tunnels on a few machines, static-key connections are a lot easier to set up.

---

