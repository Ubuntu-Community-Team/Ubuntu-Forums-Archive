---
title: "X problems with non root user"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by Samu on 2007-02-15
Hi,

After the last updates (kernel, mostly) I stopped being able to login to kde with my standard user. It offers me the login window but fails initiating KDE. When I use the console login it goes OK. It is a weird failure to me, because I have no trouble running kde when I switch to the superuser and launch startx from it. I have being googling and tinkering a little bit, without any success. If anyone has an idea, it is for sure welcome.

I am running a Laptop with Kubuntu 6.06 and I have a ATI Radeon Mobility X300. I executed a dpkg-reconfigure xserver-xorg without any success, apart from seeing that it put the RAM memory of the card into the xorg.conf. Now I am able to run my system from any of the two. I can also run the system with the same behaviour if I start with the old kernel or from the recovery mode. No differences that I see.

When I start X from user and when I use root I get different Xorg.0.log. This is the only difference I see at the moment. But I cannot see the problem within it, not enough knowledge. Perhaps someone can help me here. I sent the diff attached. I am not sure if this is the way to go. Everything is able to work under root, but not under the standard user. Weird to me. If someone has an idea or want me to post more/different data, please reply :) 

Thanks!

---

### Post by Samu on 2007-02-17
I have also tried with a new created user, in case it was something in the old one, but nothing. Perhaps something related with permissions anywhere?

---

