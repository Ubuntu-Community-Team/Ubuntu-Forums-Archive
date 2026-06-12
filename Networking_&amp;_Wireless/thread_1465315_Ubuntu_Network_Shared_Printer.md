---
title: "Ubuntu Network Shared Printer"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by ZosoPage1963 on 2010-04-29
Hello,

I recently made the decision to swap my main desktop to Ubuntu.  I chose to go with 10.04 since I have been using it on my laptop and had no issues.  I am relatively new using ubuntu, I have been using it on my laptop for a year.  My question is, how do I share a printer off of the main desktop?  I have an epson cx7800 connected to my desktop using 10.04 and I need to share the printer for all the wireless users in the home.  These include Mac, Windows, and Ubuntu systems.  I have Samba installed for the Windows laptop users, or do I even need to do that?  When I try to find a shared printer from my Ubuntu 10.04 laptop, I can not find it.  When I go the printer from the desktop, it shows that it is shared.  I am sure I am missing something easy.

---

### Post by Morbius1 on 2010-04-29
Have you both "shared" and "published" the printer?

_Share_:
****Administration > Printing > Right Click the attached printer > Properties > Policies > Check Enabled, Accepting Jobs, and Shared

_Publish_:
Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

---

### Post by ZosoPage1963 on 2010-04-29
that was the issue, thank you....knew it was something easy...:(

---

### Post by Nethar on 2010-05-03
> **Morbius1 said:**
> _Publish_:
Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

Hi, I was trying to do exactly these steps because I remembered them from previous version of Ubuntu. But my problem is that Settings option in Administration > Printing > Server is disabled... can't click on it, grey. Any idea?
I tried to run this dialog (system-config-printer or something like that) as administrator but it did not help.
Probably I forgot do do something more, please let me know. Or there is some problem and I have to have at least one localhost printer configured maybe to be able to get shared printers list? Or maybe... whole dialog is in my language - Czech - but only this disabled option (Settings) is in English. Maybe only not translated yet... maybe... maybe ;-)
Thanks for any help!

---

### Post by Morbius1 on 2010-05-03
The only thing that comes to mind is that for some reason you are not a member of the lpadmin group.

To check graphically: System > Administration > Users and Groups > Manage Groups > lpadmin > properties > make sure you're a member of that group.

---

### Post by Nethar on 2010-05-04
No, it's not the case, I am member of that group. In fact it's clean new installation of Ubuntu 10.04, no special changes done. Everything is updated.
I will try to connect it directly to some printer to have there at least one existing printer in the list, maybe then Settings option will be enabled, but I don't believe it will help.

---

### Post by kiops on 2010-05-05
I have same problem with printer share.....

---

### Post by Morbius1 on 2010-05-05
Is CUPS running?

**sudo service cups status**

If it's not running start it:

**sudo service cups restart**

---

### Post by Nethar on 2010-05-06
My girlfriend added local printer by connecting via USB. Then I installed new updates. After that - it's ok now, shared printer visible, Settings option in menu enabled. I don't know which of those two actions really helped.

---

