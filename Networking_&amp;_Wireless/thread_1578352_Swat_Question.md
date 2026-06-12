---
title: "Swat Question"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-09-20
Does anyone know why, when I go to Swat, I only see four options. I see home, status, view, password. I would really like to be able to use the "shares" option. Do I need to configure something to see the "shares" button?

---

### Post by rcayea on 2010-09-20
bump

---

### Post by rcayea on 2010-09-21
bump.

---

### Post by whoop on 2010-09-21
I'm guessing this has something to do with the annoying ubuntu "security" feature of not providing root with a password.

I've got this running on a arch server with no problems whatsoever. I just tried to do this on an LTS I found running somewhere and I ran into the exact same problem.

I can only login with regular user and look at information, I can't login as root. I even tried giving root a samba password, but that didn't help. Also I thought it could be a security feature that you can only run it from localhost but that doesn't help either.

So basically, I don't know...

---

### Post by rcayea on 2010-09-21
Well thanks for letting me know I am not alone. Does anyone have a cure for what ails us?

---

### Post by whoop on 2010-09-21
OK, this did the trick (on the server):
```

sudo chmod g+w /etc/samba/smb.conf
sudo chgrp adm /etc/samba/smb.conf

```

---

### Post by rcayea on 2010-09-21
> **whoop said:**
> OK, this did the trick (on the server):
```

sudo chmod g+w /etc/samba/smb.conf
sudo chgrp adm /etc/samba/smb.conf

```

Sweet! Thank you! I will give it a go when I get home from work.

---

