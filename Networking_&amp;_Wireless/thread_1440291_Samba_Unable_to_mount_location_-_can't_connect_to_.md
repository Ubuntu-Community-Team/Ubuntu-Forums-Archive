---
title: "Samba: Unable to mount location - can't connect to Vista PC"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by woodyg on 2010-03-27
Hi,
I have noticed that I am not the first one to have problems with samba and connecting to a Windows PC. I have read so many articles and I have tried a couple of things that seemed to make sense, but no luck.

I can connect from my Vista to my Ubuntu netbook remix, but not the other way around. I get the error message: "**Unable to mount location**", "**failed to mount windows share**" and I get "**mount error 12 = Cannot allocate memory**" in **Smb4K**.

[There was a suggestion]("http://linux.derkeiler.com/Newsgroups/comp.os.linux.networking/2006-10/msg00629.html") that  "mount error 12 = Cannot allocate memory" indicated it was a problem originating in Vista, but the added registry values on my Vista PC that was suggested didn't change anything. I have also read and [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149) and implemented 3.1 and 3.2 but it made no difference either.

Does anyone know what the problem is? I don't know too much about too technical things, so I don't really know how to procede from here...

---

### Post by Morbius1 on 2010-03-27
>  "**mount error 12 = Cannot allocate memory**" 

That's a Windows problem based on my notes. Also according to my notes ( this is from Win2K days btw ) the "fix" for me was restarting the "Server" service on Windows. Have you tried that?

---

### Post by woodyg on 2010-03-27
> **Morbius1 said:**
> restarting the "Server" service on Windows.

I don't know what it means. What am I supposed to do?

---

### Post by Morbius1 on 2010-03-27
On Vista: Right click (My)Computer > select  Manage > expand "Services and Applications" in the left pane to get access to  Services. 

When you're in there right click "Server" and select restart

---

### Post by woodyg on 2010-03-27
> **Morbius1 said:**
> On Vista: Right click (My)Computer > select  Manage > expand "Services and Applications" in the left pane to get access to  Services. 

When you're in there right click "Server" and select restart

I did this and it makes no difference. I still cannot connect. I get the same error message...

---

