---
title: "network with windows with ScopeID setted"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by teoadams on 2009-12-03
Hi, I need to connect my Ubuntu 9.10 to a local windows network. On the windows side each PC has the "ScopeID" parameter (HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Services/NetBT/Parameters/ScopeID) setted to the same value. Actually my Ubuntu cannot see any other PCs unless I delete the ScopeID value in the register. I'd like to keep the ScopeID value but I don't know where is the same setting in Ubuntu.
Thanks to any help.
Teo

---

### Post by pedro_orange on 2009-12-03
I'm not sure if this will actually help you, but if you really need a registry - you will have to install wine.

```
sudo apt-get install wine
```

After it's installed run

```
winecfg
```

Close the pop-up. Then run

```
regedit
```

And now you're in the wine registry. I'm not sure if this will be recognized by your network though. I think you need to address why you "need" to use the registry from a networking standpoint. Surely there is a better solution.

---

### Post by teoadams on 2009-12-04
Hi, I've followed your detailed instruction to install and configure wine. I've been able to enter the registry and modify it and set ScopeID parameter and I've been able also to import a whole registry file from an NT machine but without positive result. I was thinking about a kind of "explorer" running inside wine (in this way I should be able to explore my network using the registry of wine) but I've no idea of such a program. Any suggestion? thanks. Teo.

---

