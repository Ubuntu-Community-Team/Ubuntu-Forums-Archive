---
title: "Ubuntu as MacOSX File Server"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by m-one on 2010-05-16
Hey there.
I'm thinking about using Ubuntu as a low cost solution to being a file server for about 8 Macs. I'm aware that there are a few tutorials around the net relating to using Ubuntu and Mac on the same network, however, I need to be able to have user account based storage, so that different users on each Mac can have their own private share of storage.
Does anyone know how this could be achieved, the process behind it, or will this be a case of just buying another Mac?

Thanks in advance,
- Matt

---

### Post by Joe of loath on 2010-05-16
If macs support NFS (which I'm 99% sure they do), that's what you'll want. NFS supports permissions and unix logins and all that stuff. I'm afraid I can't help you with setup, as I haven't set up my own NFS box yet, but there should be a few how-tos around.

---

### Post by harveyd on 2010-05-16
This worked well for me [http://sysblog.sund.org/2010/05/install-netatalk-and-avahi-on-ubuntu-10-04/](http://sysblog.sund.org/2010/05/install-netatalk-and-avahi-on-ubuntu-10-04/)

You can give each user access to their home folder and also share folders between specific users.

---

### Post by m-one on 2010-05-17
Thanks for the help Joe of loath and harveyd. I'll be putting it to the test soon and will hopefully get some flawless results.

Cheers.

---

