---
title: "Internet slow wehn 2nd compueter is off"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by Fabled One on 2011-06-15
I have 2 computers connected to my linksys router via ethernet cables.

My main computer is running Ubuntu while the other is Xubuntu.

When both comps are on, the internet works fine, but when my second computer is off, my main computer has super slow internet. Sometimes it takes 2 minutes and I get [SIZE=2]"[/SIZE][SIZE=2]This webpage is not available", and then I refresh that and it finally loads.[/SIZE]

Why does it work when both comps are on? What could cause this?

---

### Post by dandnsmith on 2011-06-15
Sounds like there are references to the 2nd computer - I'd check routings first ( System|Admin|Network Tools Netstat)

---

### Post by Fabled One on 2011-06-15
Thanks for the reply. The netstat stuff seems fine. There is no reference to the 2nd computer.

But, I did find out that the internal IP addresses got re-ordered:
The main comp was 192.168.1.102 but is now 101
The 2nd comp was 100 but is now 103.

I don't know why they changed, but could that be the problem?

---

### Post by dandnsmith on 2011-06-15
I'd check the lease times if you're on DHCP, and check router settings to see if there's an option you could use (perhaps assign IP addresses to be issued by the router by MAC - lots of routers have this).
My favourite has always been manually allocated IP addresses, allocated at the individual PCs (for wired network), as it avoids these problems.

---

### Post by Fabled One on 2011-06-16
Thanks for the help, although it seems to be working fine now on it's own. I'm not sure why, I didn't even do anything, not even restart the computer!

---

