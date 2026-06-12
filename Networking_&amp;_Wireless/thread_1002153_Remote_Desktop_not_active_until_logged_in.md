---
title: "Remote Desktop not active until logged in?"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by kLAcK on 2008-12-04
I had connected through vnc just fine and was working with it.  Then I did a reboot.  I can no longer connect through vnc.  I know my computer is just sitting at the gnome login screen.  My question is:

Is vncserver / remote desktop not active until a local user logs in?  Is there a way I make it active before a user logs in?

I know my computer is on because I can connect through SSH just fine.

---

### Post by jonobr on 2008-12-04
How do you connect?
Is it via name address resolution or IP address?

Can you ping the machine with the name or address your using? 
Im thinking after the reboot, you got a different IP address and it wont connect

---

### Post by kLAcK on 2008-12-04
> **jonobr said:**
> How do you connect?
Is it via name address resolution or IP address?

Can you ping the machine with the name or address your using? 
Im thinking after the reboot, you got a different IP address and it wont connect

I am connecting by IP address.  I can connect through SSH just fine, just not vnc.

---

### Post by jonobr on 2008-12-04
In systems -> prefs->remote desktop
has your sharing config changed? are you still enabled to receive remote desktop connections?

On the vncviewer, do you get prompted for password?

---

