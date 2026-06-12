---
title: "Cisco VPN Group Access"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by kung_fu_mike on 2010-07-07
We have a cisco VPN at work, and I am having some trouble getting it to work with Ubuntu. My boos sent me credentials in the form of:

       IP: 66.135.149.195
       Use group authentication
       name: a_username_I_wont_reveal
       Password: a_password_I_wont_reveal

I am having some trouble searching for how to get it to connect in Ubunutu. Preferably in Network Manager. 

If someone could just point me to the correct thread, or sort of how to do this without having to fill in the "Group Name" Trait for the VPN. I would really appreciate it

The screen caps he sent me were from a Mac:

[IMG]http://imgur.com/UaKBt.jpg[/IMG] 

[IMG]http://imgur.com/jz71k.jpg[/IMG]

---

### Post by jonobr on 2010-07-07
I used to use vpnc with kvpnc as the gui front end.
If I remember rightly it wasnt too difficult to set up and it worked.
There were a couple of glitches that I had with it particularly timeout inactivity , the link would just stop working, but in general , everything seemed to work ok with it.

Have you looked at using that?
It should be in the repos

---

### Post by kung_fu_mike on 2010-07-08
I was able to solve this by:

Setting the gateway
Group name = User name = What was given by my boss
User Password = Group Password = What was given by my boss
Domain was left blank
NAT Traversal is Cisco UDP

Maybe I just didn't have all the right credentials in the right places last time.

---

### Post by jonobr on 2010-07-08
Ok
I think I missed your original intent,
I thougyht you were looking for a program or app , not settings.

Sorry

---

