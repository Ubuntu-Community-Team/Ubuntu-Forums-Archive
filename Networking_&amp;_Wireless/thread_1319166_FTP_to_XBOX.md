---
title: "FTP to XBOX"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Gidskid on 2009-11-08
Hi there I wonder if any one can help me. I'm trying to use filezilla to FTP to my softmodded xbox. I've followed all the tutorials i can find but so far all i get is a "Can't Connect" error or, EHOSTUNREACH. I've got no idea what I'm supposed to do :( Please help!


G

---

### Post by Iowan on 2009-11-08
Try to **ping** the machine (both by name and by IP address). If successful by IP address but not by name, it may be a DNS problem. If unsuccessful either way, it may be a routing problem.

---

### Post by Gidskid on 2009-11-08
PING? I have no idea how to do that with an xbox :(

---

### Post by Iowan on 2009-11-08
> **Gidskid said:**
> PING? I have no idea how to do that with an xbox :(Neither do I, but I presume you're using a different (Ubuntu?) box to connect to the xbox (or do I have the direction reversed?). Although (on my system) **ping** is available via System>Administration>Network Tools, I usually use a terminal (Applications>Accesories>Terminal).

---

### Post by Gidskid on 2009-11-08
Ok well i thought i'd just give a run through of what i have done so if I miss anything please let me know.
1. Select Start FTP in the settings menu on the xbox
2. Connect XBOX to Ubuntu via ethernet.
3. Start Fillzilla
4. Type in my IP, My User, My Password, My Port
5. Click Connect.

I also tried this on windoze XP with Flash FXP but had no luck.

Am I missing something?

---

### Post by Iowan on 2009-11-08
> **Gidskid said:**
> 
2. Connect XBOX to Ubuntu via ethernet.

Are you connecting via switch (or hub) - or directly between machines? If directly between machines, are you using a crossover cable?
Both machines have IP addresses in the same subnet? 
Filezilla is from the Ubuntu box?

---

### Post by Gidskid on 2009-11-10
Ok its just a direct crossover between my Ubuntu Laptop and the XBOX. It now says the connection is denied?

---

### Post by Iowan on 2009-11-10
I'm still confused on direction... are you trying to connect from Ubuntu to Xbox - or from Xbox to Ubuntu?

---

