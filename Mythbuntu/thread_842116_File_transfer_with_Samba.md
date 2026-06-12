---
title: "File transfer with Samba"
date: 2008-06-27
forum: Mythbuntu
---

### Post by teddydov on 2008-06-27
im using Mythbuntu 8.04 - everything seems to be working fine (more or less), but I am having an issue accessing and transferring files between my windows machines and Myth.

When I try to transfer files I get one of two issues:
1. it asks me for a Password for \Guest - and I have tried all the possible passwords for this machine and can't get access. This applies to the standard folders that mythbuntu starts with - I.E. - Videos, music ETC. 

2. I can access some folders that I have manually Shared within Mythbuntu - but I can't transfer files onto them - and yes I made sure the "read only" was not clicked. 

I have also tried to reinstall Samba - that didn't solve the issue either.. 

I have used Ubuntu in the past (both as an OS and as an MCE) and this is the first time I am having this issue. 

Please help. 
Thanks

---

### Post by DutchLoki on 2008-06-27
And the folder you are accessing, does that have the right permissions set?

---

### Post by teddydov on 2008-06-27
how would I check that?? and how would I change it if it's not set correctly?? 

thanks

---

### Post by DutchLoki on 2008-06-27
> **teddydov said:**
> how would I check that?? and how would I change it if it's not set correctly?? 

thanks

You can find a quick intro on the ubuntu guide:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

also an topic about samba persmissions:
[http://www.linuxquestions.org/questions/linux-server-73/ubuntu-samba-folder-permission-549464/](http://www.linuxquestions.org/questions/linux-server-73/ubuntu-samba-folder-permission-549464/)


For testing purposes you should read out the current permissions of the folder (so you can set it back later).

than change the permissions to the lowest level, this way you will now if this is the problem.

don't forget to set the permission back after testing. 


at this moment i'm not totally sure about your problem, you could try googling for an tuturial for setting up samba on ubuntu. So you don't miss any steps.

---

