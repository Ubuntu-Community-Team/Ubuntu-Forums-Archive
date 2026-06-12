---
title: "My internet connection disconnect itself please help"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by hoboy on 2010-05-29
I tough that firefox was the problem of my very slow web sites loading, but I am suspecting that sometimes the internet connection is the reason, maybe for some reason that I don't know it can not just connect to the site.
I am running 
Linux quick-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux.
when I browse the web it is very slow to load.
sometimes I get this error message.
Could not locate remote server.
Even I know the site is up running like google.

---

### Post by dineshs on 2010-05-29
Is it a problem with DNS? Can you ping 4.2.2.1 when you have problem?If you are using Network manager try to assign DNS manually (You can try 4.2.2.1 or 8.8.8.8 as DNS)

---

### Post by husensofteng on 2010-05-29
I think I have a similar problem, I am connecting in this way: 
After tuning the computer on I should put it on Sleep (stand by) and wait for few seconds then turn it again, it connects very well after resuming it from the Sleep.
I know it's not a clever solution but I just found it by chance.

---

### Post by hoboy on 2010-05-29
> **dineshs said:**
> Is it a problem with DNS? Can you ping 4.2.2.1 when you have problem?If you are using Network manager try to assign DNS manually (You can try 4.2.2.1 or 8.8.8.8 as DNS)

If you are using Network manager try to assign DNS manually (You can try 4.2.2.1 or 8.8.8.8 as DNS)
How do I do that ?

---

### Post by hoboy on 2010-05-29
when I ping 

ping 4.2.21
PING 4.2.21 (4.2.0.21) 56(84) bytes of data.
^C
--- 4.2.21 ping statistics ---
205 packets transmitted, 0 received, 100% packet loss, time 204315ms

---

### Post by zolsiemanym on 2010-05-29
I am having a similar problem. When i load ubuntu it says at the top wireless disconnected. i open the network connections and everything seems normal. it just wont let me connect. any suggestions?

---

### Post by dineshs on 2010-05-30
what is the output of
```
ifconfig -a
```

---

