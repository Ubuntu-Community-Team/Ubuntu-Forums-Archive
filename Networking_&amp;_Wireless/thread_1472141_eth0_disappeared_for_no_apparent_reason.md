---
title: "eth0 disappeared for no apparent reason"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by lethalfang on 2010-05-04
I was struggling frantically this morning for about 5 minutes after I booted up my computer, and wondering why it couldn't connect to the internet. After I figured out that the automatic wired network "Auto eth0" was gone from the network manager, it was easy to manually add it back. But why did it disappear in the first place? 
I swear I didn't delete it!

---

### Post by Iowan on 2010-05-04
Although I've no idea why "Auto eth0" disappeared, I'll be curious to hear if it happens again - like tomorrow... 8-[

---

### Post by webdebbyjoss on 2010-05-07
Hey. My "eth0" disappeared today too.
Did you managed to resolve this?


Here are some details:

```
# lshw -C network
```

shows 

```
*-network UNCLAIMED
description: Network controller
```

---

### Post by lethalfang on 2010-05-09
So far, the issue has not repeated, so I don't know what made it disappear in the first place. 
It happened after I connected and then disconnected PPPOE from home, and then tried to connect to LAN (auto eth0) in my office. That's when I found out the "Auto eth0" disappeared. 
I just manually added "eth0" back using the GUI network manager. 



> **webdebbyjoss said:**
> Hey. My "eth0" disappeared today too.
Did you managed to resolve this?


Here are some details:

```
# lshw -C network
```

shows 

```
*-network UNCLAIMED
description: Network controller
```

---

