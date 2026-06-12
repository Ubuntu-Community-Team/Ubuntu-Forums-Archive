---
title: "Samba Experts - Question about the smb.conf."
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-11-09
On my LAN at home I have security based on a "valid users" tag I throw in to each share section in the smb.conf. That way if fred logs in to the server and tries to hit bob's stuff, he can't because fred isn't listed as a valid user in the smb.conf.

But what does the security = user thing apply? How is security = share and security = user different? How do they compare to the valid users tag I currently use?

Also - is there a way I can add Samba users to a group, and grant that group access?

---

### Post by Iowan on 2009-11-09
**security=share** is described in my book as > best reserved for low security servers where everyone can access everything. A print server is a good example. Anything more complex than that should use one of the other security models. The **security=user** requires the client to provide a username/password that matches a Linux and Samba pair (user/password must exist in both files). Beyond that, their access can be limited with the permissions you set. 

Yes, Samba users can be added to a group, and the group included in the **valid users= ** parameter prefixed with @ (i.e. **valid users = bob, @admins**)

---

### Post by capscrew on 2009-11-09
> **Roasted said:**
> On my LAN at home I have security based on a "valid users" tag I throw in to each share section in the smb.conf. That way if fred logs in to the server and tries to hit bob's stuff, he can't because fred isn't listed as a valid user in the smb.conf.

But what does the security = user thing apply? How is security = share and security = user different? How do they compare to the valid users tag I currently use?

Also - is there a way I can add Samba users to a group, and grant that group access?

There are some subtle notions in your question.  Let's take the second question first.  The parameter: ```
security=user 
```means that ANY Linux user (I believe they must have smbpasswd set) can login to the Samba server.  The use of  ```
valid user
```further restricts users to those specific Linux users or groups of users that you define.

The parameter:```
security=share
```allows ALL users to login to the samba share.  The only restrictions are the shares file permissions.

One last thing that I have found useful is to think of the context in which you are using any or all of this.  Some parameters have subtle distinctions and affect the share connectivity in complex ways.

The best source of information the man pages see```
man smb.conf
```

---

### Post by Roasted on 2009-11-09
is valid group an option? I've never seen it used but it'd make sense if you could adjust valid group with the config file.

Thanks for the responses! I'll stick to using my current "valid user" tags since it seems to be the most secure and most practical for a small LAN server.

---

### Post by Iowan on 2009-11-10
My *Samba Unleashed* book is copyrighted 2000, (showing it's age). It doesn't mention a "valid group" option, but the group can be listed as a "valid user".

---

### Post by Roasted on 2009-11-11
Hm, that's good to know. Thanks!

---

