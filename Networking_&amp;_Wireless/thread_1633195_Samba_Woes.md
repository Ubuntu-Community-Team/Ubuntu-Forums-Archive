---
title: "Samba Woes"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by pfunkman on 2010-11-29
Fresh install of kubuntu 10.04 and cannot access my windows shares for some reason.

```
michael@michael-N220:~$ smbtree
Enter michael's password: 
WORKGROUP
        \\SERVER                        server server (Samba, Ubuntu)
                \\SERVER\IPC$                   IPC Service (server server (Samba, Ubuntu))
                \\SERVER\Backup         
                \\SERVER\Pictures       
                \\SERVER\Videos         
                \\SERVER\Music          
                \\SERVER\Complete       
                \\SERVER\Torrents       
                \\SERVER\print$                 Printer Drivers
        \\MICHAEL-PC     
        \\KATIE-PC     

```

When i try and connect to my PC i get:

> Connection to michael-pc failed (Error NT_STATUS_UNSUCCESSFUL)


Any ideas?

---

### Post by pfunkman on 2010-11-29
To clarify whats going on, samba sees the windows machines just fine but wont show any of the shares.

---

### Post by pfunkman on 2010-11-30
Nothing? Now it sees the shares on katie-PC and is asking for a password on michael-pc.

Should not be asking for a password.

---

### Post by pfunkman on 2010-12-09
Ok fresh install of ubuntu and still doing it.

Asking for a password to my gaming machine yet the wives is easily accessed. Exact same version of windows, exact same networking settings, same VA etc. Neither machine has a password.

Why would it ask for a password to access one machine and not the other?

---

### Post by pfunkman on 2010-12-09
Is there a place i can post this that will get some responses?

---

### Post by pfunkman on 2010-12-10
Figured it out. I dont know how its possible but my file server was screwing up samba. :???:

Once i shut it down everything worked as it should. How is that even possible?

---

