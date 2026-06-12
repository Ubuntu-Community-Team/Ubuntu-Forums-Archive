---
title: "Ubuntu Server / Desktop (File Sharing)"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by woodybriggs on 2012-09-29
Ok, im want to know if it is possible to set up a "business" style network, so Ubuntu Server with Ubuntu Desktop Clients. I basically want to have a Server that has a Network Drive that clients can access, and the client has a Server profile... is this possible?

thanks

---

### Post by uncaspi on 2012-09-29
It is possible if you use Samba.

---

### Post by MG&amp;TL on 2012-09-29
Absolutely. I'd go as far as to say that linux is one of the best choices for that.

If it's only going to be *nix clients, I would suggest NFS as a protocol. [Slightly confusing but informative tutorial.]("https://help.ubuntu.com/community/SettingUpNFSHowTo") 

If there will be Windows machines as well, I think Samba is your best bet. [https://help.ubuntu.com/community/Samba]("https://help.ubuntu.com/community/Samba")

Not quite sure what you mean by a 'Server profile'. But explain further, and I'm sure it's possible.

---

### Post by houstonbofh on 2012-09-29
OK, you have asked for two different things here.

1) First is file sharing.  This is easy.  Samba, NFS, SCP...  Lots.  I like the Gnome front end to SCP, which is "Connect to Server" over ssh.  You need to install ssh, and then connect on request.  For Samba, you will need samba and some configuration.  For NFS, again you will need to download NFS, and do some configuration.

2) Second, you asked about central authentication.  This is harder.  If it will be with Windows boxes, you MUST use samba.  It is not trivial to set up.  If it is only *nix systems, you can use remote PAM authentication.  Again, this is fairly high level stuff, but I think it is more solid than samba.  I had to do this for a client with Samba, and LDAP, and it took the better part of a week.

---

### Post by woodybriggs on 2012-09-30
Thanks people, i am looking into all of these options.

i have tried samba and had difficulty connecting a Win7 Ultimate desktop to it, just for testing. 

so i will keep trying these options out.

and by 'server profile' i mean, group security protocol. so that users will not be able to install software, but will be able to change background images, and other things like that

thanks again

---

### Post by houstonbofh on 2012-09-30
OK.  You just added GPOs to the list, and complexity went up again.  As an example, [http://lists.samba.org/archive/samba/2004-October/094063.html](http://lists.samba.org/archive/samba/2004-October/094063.html)

You may just want to get a windows in a box Linux distribution.  The two I have heard of are Zentyal and ClearOS.  I have not personally used either one.

---

