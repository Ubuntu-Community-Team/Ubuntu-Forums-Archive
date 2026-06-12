---
title: "Browse the domain via VPN"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by sadeghi on 2010-11-03
Hello,
I have Ubuntu 10.10 at work and I've installed a Windows XP virtual box machine under it, that is joind to our Active Directory domain(but Ubuntu is/will not joined).
I've set up VPN on XP box and I can connect to it from Ubuntu.
I want to browse network shares(that use AD for permissions) and domain sites(like sharepoint) from Ubuntu. But even after connecting to VPN when I can't browse network shares, and nautilus asks for domain user/pass and tries to open share with no success.
What extra steps is needed to browse my corporate network from Ubuntu via VPN?

---

### Post by perpetuo on 2010-11-28
> **sadeghi said:**
> Hello,
I have Ubuntu 10.10 at work and I've installed a Windows XP virtual box machine under it, that is joind to our Active Directory domain(but Ubuntu is/will not joined).
I've set up VPN on XP box and I can connect to it from Ubuntu.
I want to browse network shares(that use AD for permissions) and domain sites(like sharepoint) from Ubuntu. But even after connecting to VPN when I can't browse network shares, and nautilus asks for domain user/pass and tries to open share with no success.
What extra steps is needed to browse my corporate network from Ubuntu via VPN?
I have the same problem.
Did you already solve it?

---

### Post by sadeghi on 2010-11-29
> **perpetuo said:**
> I have the same problem.
Did you already solve it?

I defined an incoming connection in my windows XP and now I can connect to it from ubuntu. But the problem that still remains is that I still can not browse the local network and I have no internet access. I think the issue is about routing and manipulating ubuntu routing table, but i did not spend more time around that.

---

### Post by SeijiSensei on 2010-11-29
> **sadeghi said:**
> I think the issue is about routing and manipulating ubuntu routing table, but i did not spend more time around that.

If the XP box sits between the Ubuntu box and the AD server, you need to set up routing in Windows, and make it the default gateway on the Ubuntu client.  Beyond that I can't help, since I don't do Windows any more.

---

### Post by sadeghi on 2010-12-02
> **SeijiSensei said:**
> If the XP box sits between the Ubuntu box and the AD server, you need to set up routing in Windows, and make it the default gateway on the Ubuntu client.  Beyond that I can't help, since I don't do Windows any more.

I'll try your solution.
P.S: I don't do windows anymore too, I can not even imagine how I've used it in the past except for windows shares and portals at my work that the company that i work for, use them.

---

