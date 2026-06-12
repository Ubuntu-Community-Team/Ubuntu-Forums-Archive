---
title: "Making every part of Ubuntu connect to this one proxy"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by 29732 on 2011-10-25
Hi everybody,
I now have this problem, after connecting Ubuntu to the internet, the _ONLY_ way I can make it connect to the outer world is by proxy.
Now, I have made it so Firefox and Synaptic Package Manager connect properly, but I want ALL of Ubuntu to connect like that for the terminal apt-gets, Ubuntu Software Center, and etc.
Sure would be appreciated if anyone knows how to do it.
Thanks, 
29732

[SIZE=4]FIXED. [SIZE=1]All I had to do is go into the gconf-editor, go to system, http_proxy, and enable the checkmark for the use http_proxy.

Thanks, anyway.
[/SIZE][/SIZE]

---

### Post by jnorthr on 2011-10-25
there is a feature, can't remember where, try menu>admin>system proxy or something like that where you can declare the proxy for (almost) all the ubuntu featureset, so upgrade manager, update manager, synaptic package mgr, etc. will look when opening a network connection. sorry not at my ubuntu system tonite, so this only what i remember.

---

### Post by 29732 on 2011-10-25
> **jnorthr said:**
> there is a feature, can't remember where, try menu>admin>system proxy or something like that where you can declare the proxy for (almost) all the ubuntu featureset, so upgrade manager, update manager, synaptic package mgr, etc. will look when opening a network connection. sorry not at my ubuntu system tonite, so this only what i remember.
>_>'
System proxy is not a pary of the system settings.

---

### Post by 29732 on 2011-10-25
Fixed.

---

### Post by jnorthr on 2011-10-25
well-done !!! :popcorn:

---

