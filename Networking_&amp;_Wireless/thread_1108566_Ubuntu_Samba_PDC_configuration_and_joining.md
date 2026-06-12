---
title: "Ubuntu Samba PDC configuration and joining"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by jepangan on 2009-03-27
Hi Everyone,

I usually dont post on forums anymore because I figure someones probably already answered my questions (its just a matter of looking) I am sorry if this is a repost but I've been trying to figure this out for some time and cant remember or understand why my configuration is not working.

I am trying to set up a PDC with ubuntu using SAMBA and I followed this tutorial [https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)
I was able to do get this up and running some how with kubuntu but i cant remember what I did. 

When I try to join the domain it gives me:

Creation of Workstation account failed
Unable to join network JPNETWORK

I remember that I am supposed to add a $ somewhere, so I tried...adding a user named LT-01 (my client computer name) but adding it so it looks like this: LT-01$ to the users list and also adding it to the "machines" group. Then I try to add the client computer to the domain and this is what I get:

User specified does not have administrator privileges
Unable to join domain JPNETWORKS.

Also on the Client Computer I edited the smb.conf so my workgroup and security sections look like this:

WORKGROUP = JPNETWORKS

Security = domain

Im using Ubuntu 8.10 Desktop (Gnome)

Thanks for all your help its very much appriciated.

---

