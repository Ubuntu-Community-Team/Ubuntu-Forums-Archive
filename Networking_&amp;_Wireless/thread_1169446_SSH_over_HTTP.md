---
title: "SSH over HTTP"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by deviant on 2009-05-25
Hello guys. 

My network admin from work thought that will be a good idea to filter all traffic, except for http (80). 
The thing is that I used to ssh into my box back home to manage certain things, and now I can`t do it any more. 

So, is there any way I could configure my PC back home to allow ssh connection over http ?
I know, the 1st thing I will be told is to change the sshd listening port to 80, but i have apache listening on that one. 
And I think that at work all traffic is filtered, not just the ports blocked. 

Thanks. 
Vlad ..

---

### Post by ecolitan on 2009-05-25
So your network administrator has blocked all outbound port except for port 80? what about ports 443 for https websites and ports for email sending etc? maybe you could find some other port to go out from.

---

### Post by deviant on 2009-05-25
443 is open (not 100% sure).
So are the IMAP / POP / SMTP ports. 
BUT, I don`t want him to see too much traffic on those ports (IMAP/POP/SMTP). 

And I`m not entirely sure on how the firewall works. 
The traffic may be filtered on other basis than port blocking. 
For example, I can set up a P2P app (torrent client let`s say) to port 80 but that won`t make it work. 

Anyway, the only thing I need right now is to be able to ssh into my computer back home.

---

### Post by sedawk on 2009-05-25
In theory connecting to your sshd at home that is running 
on port 443 might work.

But there can be three problems

1) The "session setup" might give away what you are doing 
   (uncrypted connection "setup"?)
2) Your home IP might be suspicious enough to alert the admin
3) The traffic "footprint" might also alert the admin.

Do you have to use a proxy for http and https (in the future)?

---

### Post by deviant on 2009-05-25
@sedawk:
Is there any way to "mask" the traffic footprint so it doesn`t appear as a ssh encrypted connection ?

There is no proxy for http(s) .. yet. 
In the past I was using my ssh connection to tunnel my web traffic through my home box (ssh -D port), but that is not the main concern. 

As I was saying, I need ssh access to my home box in order to do various tasks there. I can manage my rtorrent, my apache, my OTTD server, I can irc from there, etc.

---

### Post by sedawk on 2009-05-25
With ssh you create a connection that stays open until you close ssh.
With https you normally only create short living sessions to download
web content (unless downloading huge files, with is unusual over https).

I think that is a difference in "traffic footprint" you cannot hide
from the admin!

I have seen external consultants use cell phone data connections
from inside the company to connect anywhere they like.
But as an internal employee I'm not allowed to bring even
my own netbook anymore - strange world ...

---

### Post by dmizer on 2009-05-25
If you need ssh access to your home computer while you are at work, you should discuss the matter with your admin. This forum does not support bypassing restrictions put in place by admins who are only trying to protect their network.

Thank you.

---

