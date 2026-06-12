---
title: "Can't see windows"
date: 2005-03-09
forum: Networking &amp; Wireless
---

### Post by eraos on 2005-03-09
I have Samba installed and everything, and I have windows networking activated.  My brother's computer can see mine but I can't see his.

Last night, I could see his computer and my dad's.  But this morning I couldn't see anything.



(Plus, I really have little clue on how to run samba. 
I have used it on OSX though.  But that's besides the point and the question.)

---

### Post by krusbjorn on 2005-03-09
i had problems seeing shared folder on a Win2000 machine in our house. i dont know exactly what the problem was, but typing "smb://<ip-adress-to-the-Win200-comp>" in the adress field in nautilus worked.

give it a shot :)

EDIT: typo.

---

### Post by eraos on 2005-03-09
[QUOTE=krusbjorn]i had problems seeing shared folder on a Win2000 machine in our house. i dont know exactly what the problem was, but typing "smb://<ip-adress-to-the-Win200-comp>" in the adress field in nautilus worked.

give it a shot :)

EDIT: typo.[/QUOTE]
 this happens :

```

nick@Ubuntu:~ $ smb://192.168.0.103
bash: smb://192.168.0.103: No such file or directory

```

but :
```
nick@Ubuntu:~ $ ping 192.168.0.103
PING 192.168.0.103 (192.168.0.103) 56(84) bytes of data.

```

i can ping it.

---

### Post by krusbjorn on 2005-03-09
ahh, you should type the smb://etc in the adress field in nautilus, not in the terminal!   :---)

edit: oh. your post disappeared while i was writing mine ;)

---

### Post by eraos on 2005-03-09
[QUOTE=krusbjorn]i had problems seeing shared folder on a Win2000 machine in our house. i dont know exactly what the problem was, but typing "smb://<ip-adress-to-the-Win200-comp>" in the adress field in nautilus worked.

give it a shot :)

EDIT: typo.[/QUOTE]
 Okay, I can see them now.  Thanks

---

### Post by eraos on 2005-03-09
[QUOTE=krusbjorn]ahh, you should type the smb://etc in the adress field in nautilus, not in the terminal!   :---)[/QUOTE]
 Yeah, haha, I realized that after I posted the message.

---

### Post by Requiem on 2008-01-09
While I can smb://name my Windows box, i really want to know why it isn't listed in nautilus network view.

Which one is broken? nautilus, ubuntu, smb or my network configuration?

I'm going to fiddle with my router's configuration just in case...

---

### Post by recluse2 on 2008-01-11
> **Requiem said:**
> While I can smb://name my Windows box, i really want to know why it isn't listed in nautilus network view.

Which one is broken? nautilus, ubuntu, smb or my network configuration?

I'm going to fiddle with my router's configuration just in case...

I too would like to know the answer to this. I had to change my router and now I cant see my windows PC's from my Gutsy machine unless I enter the IP addresses, BUT! I can see the Gutsy machine from my windows machines **and** (after some adjustment) I am using Synergy, and it immediately connects to the windows PC when I start it.

---

