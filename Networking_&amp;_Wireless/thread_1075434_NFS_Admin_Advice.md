---
title: "NFS Admin Advice"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by JFASI on 2009-02-20
We are setting up a lab, where one machine will act as a file server, and all others will be diskless and user the /home directory on the server as their /directory through NFS. We have landed ourselves in an interesting situation, so hear me out. 

We are configuring a single server and a single client at first. By coincidence, the users we are using on both machines have the same name, although I don't think that makes a difference since their UID's are almost certainly different, or because the server does not recognize the client's UID. Mounting and everything works splendidly, but when I attempted to add a user, I get a "Cannot create home directory...Permission Denied" error. 

I soon find that everything outside the home directory of the user we are working with, namely /home, is denied. How can I create a sort of "root user" for nfs, as in, how can I make it so that one user is allowed to modify /home?

Also, in order to avoid descending into user-hell, is there a way to have a sort of "network user," where each machine sort of recognizes that one login is the same person? NIS maybe?

---

