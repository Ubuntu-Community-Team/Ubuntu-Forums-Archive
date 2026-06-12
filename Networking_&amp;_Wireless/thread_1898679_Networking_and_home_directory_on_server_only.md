---
title: "Networking and home directory on server only"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by sd@ksu on 2011-12-21
I have three computers in lab, all of them have Ubuntu 11.04 installed on them. Let's call them 1,2,3. 1 will be treated as a network file server. 2 and 3 will be used by multiple users, say A,B,C,D etc. A,B,C,D will have same user name and password (could be different also, does not matter) on computers 2 and 3. But I want to mount the home directories of all the users of 2 and 3 on the server 1. So that it does not matter which computer they are using, they will always log into the same home folder. Plus all data will be stored on the server 1. And if we are accessing the data from outside, we can log in to the server and access it. But there will be only one super user. Other users can only see their respective home directories.
Can anyone shed some light on it. I shall appreciate it very much. I have a little idea but I do not know it well enough to apply throughly.

---

### Post by Thylex on 2011-12-22
A quick fix would be to export the home directory folder from the server via NFS and mount it statically on the workstations. What you need to make absolutely 100% sure of is that the user accounts you set up have the same UID and GID numbers on ALL the machines.

As a long term solution you should look at setting up some form of networked authentication, NIS, LDAP or similar that lets you use automount and networked user account information. But for just 3 hosts and a limited number of accounts you can get started in this way, as long as all the UIDs and GIDs match up.

---

### Post by sanjayk.rhce10@gmail.com on 2011-12-22
Dear friends 
   how to install Foxpro2.6 ubuntu.. plzz send me a link or pdf

thanks in advance

---

