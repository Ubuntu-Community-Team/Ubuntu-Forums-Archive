---
title: "Jaunty - Connecting to SMB shares over VPN"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by parx86 on 2009-04-30
I've read quite a bit about people having problems with PPTP VPN's and Jaunty, but I've gotten past most of the issues and can't quite figure out the last step out on my own (been searching forums/google for days)...

So I'm connected to my VPN, I can ping servers by name, everythings appears good....but when I try to connect to the shares on the server, it tells me "No Application Registered to Handle This File", whether I try DNS name or IP address I get the same error, and cannot browse any shares over the VPN.

I've made sure I have the samba packages installed (both samba and smbfs client) and it even asks me for a password when I try to connect, so it seems like it sees the share out there, just won't let me in (although I don't feel it should need one since I'm already authenticated when I connect?)

Any help would be greatly appreciated, and I'd be glad to provide more info if needed!

---

### Post by stuples on 2009-05-10
How are you trying to connect to the share?

Are you a student trying to access the uni's VPN?

---

### Post by parx86 on 2009-05-11
No, I'm actually trying to connect to my work VPN, but similar scenario

Just to give some more details, we use a PPTP VPN, but only Windows XP machines can connect to it, Vista machines cannot.  I believe we narrowed this down to a older version of MS-CHAP authentication that's no longer supported in Vista.

I've tried connecting using the standard \\[IP address/server name] and also using the Connect to Network Share application under networking, but neither will work.  I've managed to get it to prompt me for a password using the app, but it will not accept my credentials (In the Windows world I never have to do this, as whatever account I'm connected to the VPN with is used for all access by default - not sure if this is the same in the Linux world or not)

Hope that helps!

---

### Post by parx86 on 2009-05-19
I guess since nobody has replied to this in so long, that my PPTP VPN won't work in Ubuntu, which is a real shame.  I was planning on setting this up to replace Windows on my laptop at work, but the first hurdle proved to be un-solvable.  I truly hope this problem gets resolved in the next release, I've been making some great strides in transitioning from Windows to Linux, but obstacles like this may force me back into the world of Microsoft.

Thanks to everyone who took the time to read this, I really appreciate it.

---

### Post by dmizer on 2009-05-20
Take a look at the second link in my sig. That should get you connected to your samba shares over VPN.

---

### Post by zivley on 2009-06-10
> **dmizer said:**
> Take a look at the second link in my sig. That should get you connected to your samba shares over VPN.

I think you should indeed start by making sure you have all the samba related packages installed, that could be the problem.
Lucky you, at least you succeeded making a VPN connection, I still can't...

---

