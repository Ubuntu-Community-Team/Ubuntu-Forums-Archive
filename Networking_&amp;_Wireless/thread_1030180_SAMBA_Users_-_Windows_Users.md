---
title: "SAMBA Users - Windows Users"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Vince4Amy on 2009-01-04
Just something I'd like to sort out so that every time I try to access Windows shares I don't have to keep entering a username and password. A bit about my setup on this is:

Windows Vista Home Premium is set up as a Server (Windows WorkGroup), I am sharing a Printer and my files from this computer. 

I have Ubuntu on another machine and I can access my Windows shares the Vista machine using Samba. The problem is as follows.

I've set up Vista so that the same username and password has be used on any machine accessing it's shares. For example if the user account on Vista was User and the password was 123456. The other computers in my network would have to match that, on XP If I create user accounts with exactly the same user/pass no login window displays.

Ubuntu is a bit different as usernames are in lowercase, so for example if on the Vista machine it's User with pass 123456 on Ubuntu it has to be user with pass 123456. So when I try to access my Samba shares I have to enter in User with pass 123456 every time I want to access my Windows shares.

Can I associate my Windows account with my Ubuntu account so I don't have to keep entering login details every time I want to access my network shares. I've read something about setting up Samba users, but I'm not sure.

---

