---
title: "connect two 10.04 computers"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by dnpate on 2010-08-08
I have 2 10.04 computers and one win 7 and one vista computer:  The win  computers can see each other and the ubuntu computers, but the ubuntu computers cannot see each other or the win machines.  The ubuntu computers connect to the internet fine and can ping each other.  I cannot find settings to correct. 
Thanks for any help.
David

---

### Post by chopinhauer on 2010-08-08
> **dnpate said:**
> I have 2 10.04 computers and one win 7 and one vista computer:  The win  computers can see each other and the ubuntu computers, but the ubuntu computers cannot see each other or the win machines.  The ubuntu computers connect to the internet fine and can ping each other.  I cannot find settings to correct. 


That's odd. Install the **avahi-utils** package and try:
```
avahi-browse -a
```
It should at least list your Ubuntu machines and maybe the Win 7 boxes.

---

### Post by dnpate on 2010-08-14
avahi does show the ubuntu computers.  But, how do I get them to see the win computers?

Does ubuntu have an app like wins "network neighborhood"

TX
David

---

### Post by chopinhauer on 2010-08-14
> **dnpate said:**
> 
Does ubuntu have an app like wins "network neighborhood"


Usually when you use Nautilus you have a “Windows Network” entry in your “Network” folder.

If you want the Windows boxes to see your computers you should install the **samba** server, which should work out of the box.

However the resolution of names is done using **NetBIOS** instead of **MDNS**, which can be quite messy (it is an old protocol with a lot of hacked Microsoft extensions). If a badly configured Windows box becomes the Workgroup Manager, you won't be able to list your boxes, only access them directly by NetBIOS hostname.

---

