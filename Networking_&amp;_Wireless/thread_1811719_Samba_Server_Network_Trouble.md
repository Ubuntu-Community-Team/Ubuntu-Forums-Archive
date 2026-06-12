---
title: "Samba Server Network Trouble"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by jdm2 on 2011-07-25
Hey guys, 

Its been a while since my last post.  This is related to it to some degree.  If any of you remember me I was working on a samba file server for my high school.  It's up and running, but at the moment it has some issues.  It has been up and running for 3-4 years now and the person I built it for still doesn't really know much about linux, but she tries to understand it.  Well she did a full update/upgrade and now she is running 8.04.  The school also has updated their network structure, but idk much about that.  When I get on it I can surf the web and do updates, but none of the computers in the lab can see the samba server now.  I was wondering if anybody knew of anything that could help me out.  

Thanks for the help.

Sincerely yours;

jdm2

---

### Post by 2F4U on 2011-07-25
Is it possible to ping the server and/or get to it via ssh?

---

### Post by jdm2 on 2011-07-25
I think at times we were able to ping it and at other times we weren't able to.  Can't do ssh on it.  Didn't set that up on it.

---

### Post by CharlesA on 2011-07-25
Can you ping via ip address or are you using the hostname?

If you can get console access, check to make sure it's listening on port 445, 139 TCP and 137, 138 on UDP.

With netstat -nlu

---

### Post by jdm2 on 2011-07-25
At the moment I don't have access to the machine, but we used the ip address when we pinged it.  The thing is it was all working fine until the update.  So I don't know if the update changed any of the settings or if it was caused by the network update instead.

---

### Post by capscrew on 2011-07-25
> **jdm2 said:**
> At the moment I don't have access to the machine, but we used the ip address when we pinged it.  The thing is it was all working fine until the update.  So I don't know if the update changed any of the settings or if it was caused by the network update instead.

If you are trying to browse the network for shares (i.e. "but none of the computers in the lab can see the samba server now."), you need to have some sort of name services (hosts or netbios).  It is possible to overwrite the name service settings in an update.  It really depends how you have setup the naming system.  

You can specifically mount a share without browsing by IP address.  Which are you trying to do?

---

### Post by jdm2 on 2011-07-25
Well we just search the network for the server and connect then connect to the files.  As for naming it idk, i just named the box server or something like that.  I pretty much don't really remember the details since it has been 4 years since then.  I remember I installed samba, created accounts for both the machine and the samba, then i created folders on a second hard drive with the usernames, then i just went through the share wizard, and finally i worked on the permissions for the files.  I think that is all I did for that part.

---

