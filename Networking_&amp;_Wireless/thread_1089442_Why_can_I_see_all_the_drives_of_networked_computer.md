---
title: "Why can I see all the drives of networked computers?"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2009-03-07
I have a windows XP laptop and a Kubuntu 8.10 PC. I havent installed samba yet so I acn't see the linux folders on the windows machine but it works the other way round. So far do good. However when I go to the  samba shares folder on kubutu I can see much more than the folders I have shared on the windows machine. I can also see all the partitions with $D $C signs. Why is this? After all I have only shared a specific folder on my windows machine. When samba displays all those paritions like that I can't help but feel that it's doing something it' not supposed to do. Can someone explain?
I have attached a screenshot as well

---

### Post by HavocXphere on 2009-03-07
Windows always shares the drives.

If connecting from a windows box, then it hides them. The $ sign indicates a hidden share. Linux ignores that rule and shows them.

You need admin priviledges to access them though, so there is little security danger.

---

### Post by mahela007 on 2009-03-07
ah
thanks.

---

