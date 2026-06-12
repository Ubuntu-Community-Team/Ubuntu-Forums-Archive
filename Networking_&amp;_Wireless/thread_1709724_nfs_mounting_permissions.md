---
title: "nfs mounting permissions"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by Calcvictim on 2011-03-18
here is the scenario

server:running fedora, has NFS installed, I have an account created on the server my username is calcvictim, my uid is 1016

host:virtualbox running ubuntu, my user name is calcvictim, my uid is 1000



when I mount my home directory from the server to host all my permissions are screwed up, the uid shows up as a 7 or 8 digit number and not as 1016.


what I want is to be able to mount the file as the user on the local machine(the server)so I can read,write and modify files....**how can I do this?**

I tried creating a user on my local machine with the uid of 1016 and that did not change anything, I also tried adding "-O uid=1016" to the mount command but it didn't do anything either.

---

