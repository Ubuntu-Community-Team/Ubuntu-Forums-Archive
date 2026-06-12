---
title: "Firewall exception"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by lucasart on 2010-02-09
Hello everyone,

I've read that torrent downloading is significantly less efficient if the port is closed by a firewall. I don't want to simply disable Ubuntu's firewall, so I did:

```

sudo ufw enable
sudo ufw allow 51413

```

where 51413 is the port that the torrent client "Transmission" is using (i disabled random select port of course).

but that doesn't work apparently, as when i do "test port" in Transmission->Preferences->Network, it says "Port is closed"

Does anyone know what I did wrong ?

Thank you

---

### Post by engelp on 2010-02-24
Hi same thing happening here, i cant get transmission and have an adicitional problem, after installing playonlinux when i try to run it, it says it cant connect to the internet, i wonder how i can unblock internet acess to playon linux.

thanks in advance.

---

### Post by uncle-c on 2010-02-24
Are you guys behind a router ? You may have to alter its settings to allow this port.

---

### Post by engelp on 2010-02-24
> **uncle-c said:**
> Are you guys behind a router ? You may have to alter its settings to allow this port.

In my case im note behind a router i connect to internet through a mobile broadband. what is even strange is playonlinux cant connect to the internet.

---

