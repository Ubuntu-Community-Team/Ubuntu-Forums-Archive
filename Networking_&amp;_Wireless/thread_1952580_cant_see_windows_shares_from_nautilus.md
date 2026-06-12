---
title: "cant see windows shares from nautilus"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by brexsis on 2012-04-04
i have problem, i cant open windows share from nautilus, i can see windows computer, but when i try to open it, i get "Unable to mount location - Failed to retrieve share list from server" error.

but when i run "nautilus smb://192.168.1.2" from terminal, it opens me window asking for username and password and i can see all shares from windows pc. and in this case vlc cant open videos  stright from windows pc (dunno if it is normal or not).

but how do i open shares normaly, browsing in nautilus?

---

### Post by Paddy Landau on 2012-04-05
Have you installed Samba on your Ubuntu machine?

If not, open Ubuntu Software Centre and install samba and system-config-samba. Run Samba and go through the menus setting whatever needs setting. Reboot both machines. Let us know what happens.

---

### Post by brexsis on 2012-04-05
yea, samba was installed. without samba i didnt even saw windows computer.
i tried PCmanFM, it showed me another error after that - "The specified location is not mounted". do i need to mount windows pc? i dont want to mount all shares seperately, i just want to be able to open them in network when i need them, dont wanna them be visible in folder lists etc..

edit:
i think i will just add to bookmarks that place/adress what i open with "nautilus smb://192.168.1.2" and it should be what i need :)

---

### Post by Paddy Landau on 2012-04-06
> **brexsis said:**
> i think i will just add to bookmarks that place/adress what i open with "nautilus smb://192.168.1.2" and it should be what i need :)
If that works for you, that's fine. But if you still want to resolve this, post back and let's see what we can do.

Unfortunately, Samba is not all that straightforward to set up sometimes.

---

