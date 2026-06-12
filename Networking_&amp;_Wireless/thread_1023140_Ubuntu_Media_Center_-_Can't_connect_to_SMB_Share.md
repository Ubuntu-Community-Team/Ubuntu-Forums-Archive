---
title: "Ubuntu Media Center - Can't connect to SMB Share"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by rahduke on 2008-12-27
I'm at my wits end, Hoping you folks can help me out. 

I've got Ubuntu 8.10 running on all my machines in the house, Recently I put together a media center running 8.10 over my Wifi network. 

I've setup my Samba shares, and can connect to them via XBMC on both an XBOX and the Ubuntu box I built. However I cannot find the Samba shares through Network>Places or through Places>Connect to Server (once in a while it just works randomly). 

The box i built is not powerful enough to run XBMC so I need to connect to these shares through Nautilus or Places. Sometimes if I launch XBMC find the shares then close XBMC I'm able to view the SMB shares through Places>Network. 


How can I set my shares so they are always visible? I'm freaking out its really annoying. I've re-installed Ubuntu 4 times (no idea why) I can't figure this out can someone help?

---

### Post by jesuspresley on 2008-12-27
If this regards to Samba:
It should be working if you add or replace the following parameters of your 
Samba configuration in /etc/samba/smb.conf
 
Global section:

```
[global]
	security = share
```

and in the shares section:

```
[Name of your Share]
	writeable = yes
	browseable = yes
	guest ok = yes
```

If you are still stuck, please post your smb.conf here. 
Unfortunately, I don't know anything about XMBC.

---

