---
title: "Remote Desktop Connection"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by Ibrahim mufeed on 2009-03-10
Hi,

I have Ubuntu 8.10 on my PC, and I use another PC in my university that have Fedora 10 installed on it. I need to access each one of these PCs from each other, that is when I am home I can access Fedora, and when I am in the university I can access my Ubuntu.

Can I do such a thing? and if yes, I need a simple easy to follow instructions about how to do this.

NOTE: I go to the "Remote Desktop" tap on each PC, and I ALLOW other people to access the PCs remotely. I do not know if this right and if it is right then what the next step should be??

Thanks,

---

### Post by zob on 2009-03-12
Well. The next step should be to make sure that you login with a password, not a confirmation from the remote computer (unless you want to run to the university to confirm every time). Other important settings in ubuntu's system-settings-remote desktop is "allow others to see your desktop" and "allow others to control your desktop" and in the advanced tab unmark the "only allow local connections".

The should be it. It doesn't work for me. But people normally don't have any problems.

The university computer might bring trouble though. I don't know, but it's probably behind a proxy. I don't know if that matters.

Next step is. Find the IP's for your computers, open a terminal and go:
```
vinagre 212.242.xxx.xxx
``` or whatever the ip you want to connect to is.

Or you can follow the command as it is written in the remote desktop settings - on ubuntu at least.

---

### Post by zob on 2009-03-12
Sorry. Try the vinagre command from your home computer. I'm not sure it's the vinagre program that is installed on Fedora by default. You can of course install it if it isn't.

---

### Post by Ibrahim mufeed on 2009-03-12
Thank you so much,

I will try it next Sunday.

---

### Post by IsmailBhai on 2009-03-12
brother Ibrahim, you can either connect with VNC or NX in Ubuntu and I'm pretty sure Fedora. [check here for more information]("http://hydtechblog.com/2009/02/15/how-to-use-remote-desktop-connection-with-ubuntu/").

---

