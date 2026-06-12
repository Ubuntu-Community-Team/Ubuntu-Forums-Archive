---
title: "Unable to ssh into Mythbuntu server"
date: 2014-11-21
forum: Mythbuntu
---

### Post by hollywoodpete on 2014-11-21
For some odd reason I can VNC into my Mythbuntu Sever but am unable to ssh into the server. SSH is installed but I keep getting "connection refused" on my client. I would be happy to attach logs if I knew where to find them.

---

### Post by dannyboy79 on 2014-11-21
what user are you trying to ssh in with?  root ssh login is disabled by default just fyi but otherwise you should be able to ssh with any user on the system (besides root)

---

### Post by hollywoodpete on 2014-11-29
That must be my issue. I am trying to log in as root. I guess my user would be whatever the mythbuntu .iso installs by default. "MythTV"?

---

### Post by Lester_Burnham on 2014-11-29
Hi,
Nope. The username you entered when installing. Open a terminal. What is the name on the left? Use that. "userblah@hostname:~$"

ssh userblah@machines_IP

Use sudo after logging to get root access.

Lester

---

### Post by hollywoodpete on 2014-11-30
> **Lester_Burnham said:**
> Hi,
Nope. The username you entered when installing. Open a terminal. What is the name on the left? Use that. "userblah@hostname:~$"

ssh userblah@machines_IP

Use sudo after logging to get root access.

Lester


Thanks. Problem solved. I can't use ServerName.local but IP_Address works fine

---

