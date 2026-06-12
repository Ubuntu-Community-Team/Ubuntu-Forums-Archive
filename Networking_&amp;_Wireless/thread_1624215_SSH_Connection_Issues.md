---
title: "SSH Connection Issues"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by advil0 on 2010-11-17
I can connect to my VPS using SSH on my home connection and my mobile broadband connection, and a few others.  But when I go to school and use their wifi, the connection to my VPS is refused most of the time, sometimes it lets it go through.  

I think my VPS may be blocking my school's IP, but I'm not sure why it would do that.

Any ideas?

---

### Post by SeijiSensei on 2010-11-17
Maybe it's the school that's doing the blocking.

Try moving your server's SSH port in /etc/ssh/sshd_config to something arbitrary above 1024.  Then log in with "ssh -p 12345 user@server" and see how that works.

---

