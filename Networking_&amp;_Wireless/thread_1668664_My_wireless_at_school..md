---
title: "My wireless at school."
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by Mr. ViC on 2011-01-16
So, my wireless network at school must use some kind of proxy system, as it has a website filter, and I have to configure Firefox to "Use system proxy settings". The problem is, only Firefox can acess the internet. aMSN, Software Center, nothing works. I do have to use a login system to use the internet. I have to use Meebo to go to messenger, it's really annoying...

Any idea on how to solve this?

Thank you.

---

### Post by bapoumba on 2011-01-16
If the network admins have closed some protocols and/or ports, I would recommend to follow their rules.

---

### Post by Mr. ViC on 2011-01-16
I understand what you mean.

The thing is when I ran Windows, it was automatic and I could do everything. On my Ubuntu, no. So, it's not really because of that. It's just that I want to use aMSN or do this or that with the Software Center and I can't. Just need some workaround or solution to this, I'm not going against any rules because on Windows I could do everything. And all my class uses Windows except for myself.

---

### Post by Mr. ViC on 2011-01-16
---Sorry, double posted, please delete it---

---

### Post by soekarmana on 2011-01-16
have you tried System -> Preferences -> Network Proxy ?

---

### Post by soekarmana on 2011-01-16
Sorry Double post

---

### Post by Mr. ViC on 2011-01-17
> **soekarmana said:**
> have you tried System -> Preferences -> Network Proxy ?

Many times I went there, but I do not know the proxy configuration's IPs or ports.

---

### Post by ptptaylor on 2011-01-17
If you ping something from the terminal what do you get from that? Do:
ping [www.google.com](www.google.com) 
and see if you get a response. 
If you do then things should be working alright. It could well be that the firewall of ubuntu is blocking access. 
If you go into terminal can you download applications from there instead of the software centre?
Type ifconfig into terminal and see what info you get from that too.

---

