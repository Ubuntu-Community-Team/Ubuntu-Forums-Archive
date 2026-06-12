---
title: "Skype works only for ONE user on same machine"
date: 2009-07-24
forum: Multimedia Software
---

### Post by 4ebees on 2009-07-24
Hi all,

Now here's a weird problem.

I have a number of machines at home. Two belong to my children. They run Hardy 8.04, the same as my laptop and desktop and netbook.

My desktop has Skype with video installed. All is well. 

When I installed the children's machines, I installed with me as the first user (and thus with sudo) and then created users for them both WITHOUT admin rights ('natch :))

I've installed Skype video on their machines. When logged in to the machines as me - Skype video works fine.

When logged in either of them, it doesn't. By which I mean that if I check the setting for the video cameras, I get only a black square or a black windows with a small transparent rectangle in the middle (very odd) or a white box with a colour rectangle in the middle (still very odd - though the colour matches the desktop theme :))

If I try to video chat with this is what happens:

1. logged in a first user (myself) on both machines - all is fine. I can see the other user (ME :)) on either machine. As it should be.


2. logged in a first user (myself) on machine ONE and as one of the children on machine TWO - me, on machine ONE can see the other person but they can't see me.

This is the case regardless of which machine I am logged in as the 'primary' user. 

It would appear to me to be some form of 'permission' issue, but changing /usr/bin/skype ownership to the 'child' user does not make a difference either.

The web cams are Microsoft VX500s and they appear to work fine under Ekiga.

This is quite weird and after a few days of hacking at this, I'm no closer to a solution.

Any help with this would be most gratefully appreciated.


Footnote: What's that I hear you say, "Why not use Ekiga then?" Good question. The rels who are on Skype (wife, kids wish to video conf with them) are on (Cr)Apple Macs and are functionally incapable (bar one) of installing anything else or using anything else (the tech capable ONE has got the others on to Skype :))

---

