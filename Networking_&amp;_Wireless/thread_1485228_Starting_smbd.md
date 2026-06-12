---
title: "Starting smbd"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by dnpate on 2010-05-15
When giving the command "sudo /etc/init.d/smbd start" I get the message to use the service command.  I have no idea what this means or is.

---

### Post by Watts8888 on 2010-05-15
same issue here, when I try that I get

Rather than invoking init scripts through /etc/init.d, use the service(8
utility, e.g. service smbd start

I don't know what the service utility is 
can anyone help?

---

### Post by pytheas22 on 2010-05-15
> same issue here, when I try that I get

Rather than invoking init scripts through /etc/init.d, use the service(8
utility, e.g. service smbd start

I don't know what the service utility is
can anyone help?

Don't worry about this.  It's a confusing message, but all it's telling you is that instead of typing "sudo /etc/init.d/smbd start" you should type "sudo service smbd start".  These two commands are equivalent.  In the future the Ubuntu developers might get rid of the /etc/init.d/... stuff, but for now you can use either command to achieve the same result.

---

### Post by pso2010 on 2010-05-16
When I enter this command it asks me for my password. After entering it I get the command not found message.

---

### Post by cariboo on 2010-05-16
> **pso2010 said:**
> When I enter this command it asks me for my password. After entering it I get the command not found message.

What version are you using, and what command are you entering?

---

