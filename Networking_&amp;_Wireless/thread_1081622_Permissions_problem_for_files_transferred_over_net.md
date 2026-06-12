---
title: "Permissions problem for files transferred over network"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by arigwapo on 2009-02-26
I'm running 8.10 headless in a cabinet. I'm using it as a media server to feed my NMT and Squeezebox. The plan is to rip CD/DVD media on my iMac then transfer it via network to the server. I've gotten it to work except that it's saving the files that are being transferred show the owner as "nobody" and the group as "nogroup". This means that I'm unable to do anything to the files after they're transferred unless I use Nautilus.

How do I tweak the setup so that the files transferred over the network automatically have the proper ownership?

---

### Post by Yashiro on 2009-02-26
The files are saved under the account that created them.
If you log in to the share with no account and you've set it to allow all anonymous access then the files will be owned by 'nobody'.

You can either sort the authenication out or just run something like *sudo chown -R myname:myname /thefolderpath*

Having had problems myself with auth on mixed Mac environments I'd just make a chown script unless you want to mess about testing share perms all night.

---

