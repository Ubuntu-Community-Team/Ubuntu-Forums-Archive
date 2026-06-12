---
title: "Can't identify what is listening on a port"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by imbjr on 2011-06-29
sudo ss -l -p tells me that TCP 47355 is listening, but there's no PID mentioned. 

sudo lsof | grep 47355 reveals nothing. So how do I identify what has that port open for listening?

---

### Post by Rubi1200 on 2011-06-29
Does this help?

```
sudo lsof -i -n -P
```

---

### Post by gmargo on 2011-06-29
Try:
```

sudo netstat -tlnup

```

---

### Post by imbjr on 2011-06-29
> **Rubi1200 said:**
> Does this help?

```
sudo lsof -i -n -P
```

Cheers, that did it. I also managed to find out what it was when I did an nmap on the port. Turns out it's NFS-related.

Edit: Oops. I'm not paying attention. No, that actually didn't work. Only nmap managed to reveal the offender.

---

### Post by imbjr on 2011-06-29
> **gmargo said:**
> Try:
```

sudo netstat -tlnup

```

No, that still did not reveal the program or its PID:

tcp        0      0 0.0.0.0:47355           0.0.0.0:*               LISTEN      -

---

