---
title: "NFS Question."
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by GreezyE on 2010-12-19
Hello All,

I understand that Ubuntu can allow a user to have a 'home' directory located on a server and thus all their settings and whatnot can be the same whatever the computer they log onto. 

(Thanks to [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo))

Anyway, the thing I would like to achieve would be that on the server I would choose to install applications and this would be reflected on all computers that users connect to.

So, It would be like this;

- On Server Install **Example App**.

- On Remote Computer, User Logs on, Home Directory on the Server

- **Example App** now installed on the Remote computer when user logs on.

I would appreciate any help,

Thanks :)

---

### Post by pebo on 2010-12-19
Sounds like you don't need a hard disk on the client at all - you could try creating a thin client network like [this]("http://www.ltsp.org/") ;)

---

### Post by GreezyE on 2010-12-19
Interesting, however I would need to make sure that the laptops can always use the hard drive should a network connection to the server not be available.

Ideally this would then mean that any new data would be synchronized when connected to the server again.

Realistically I'm looking for a simple way to maintain the applications across all users/computers.

Thanks so far.

---

### Post by SeijiSensei on 2010-12-19
> **GreezyE said:**
> Realistically I'm looking for a simple way to maintain the applications across all users/computers.

In general, the easiest solution is to set up all the machines to update themselves automatically from the repositories.  If you're looking for a more centralized solution, Novell offers a commericial application called [ZENworks](http://www.novell.com/products/zenworks/).  I don't know of any free applications that handle this task.

One intermediate solution is to maintain a local repository containing only those packages you've approved.  Then you could point all the workstations at your repository and have them update from there.

---

### Post by GreezyE on 2010-12-19
> **SeijiSensei said:**
> 

One intermediate solution is to maintain a local repository containing only those packages you've approved.  Then you could point all the workstations at your repository and have them update from there.


I think i'm going to give this a go and see what can come out of it :)

Thanks for the help guys.

---

