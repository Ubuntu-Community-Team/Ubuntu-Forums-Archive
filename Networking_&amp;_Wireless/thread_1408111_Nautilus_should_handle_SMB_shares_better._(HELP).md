---
title: "Nautilus should handle SMB shares better. (HELP)"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Luke has no name on 2010-02-16
I am username "luke" on my remote server. 
I have a directory on my server, /home/repo, which is guest-viewable. 
I have a directory, /home/repo/luke, that is accessible only via my account.

When I browse /home/repo, it lets me do so anonymously. When I want to access /home/repo/luke, I get "Access Denied". I don't know how to tell it that I am an authentic user for that folder! If there is a way, tell me. 

I believe, in any case, that Nautilus could handle this issue in a more user-friendly way.

---

### Post by johnson.d on 2010-02-16
Can you specify how you configured the samba share, by using Nautilus or by manually editing /etc/samba/smb.conf? And also post your smb.conf file if you are using it to configure.

Can you also specify the OS/samba version you are using?

---

