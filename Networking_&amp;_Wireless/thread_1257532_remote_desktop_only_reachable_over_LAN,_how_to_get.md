---
title: "remote desktop only reachable over LAN, how to get www?"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by rhythmiccycle on 2009-09-03
when i go to remote desktop it says, 

"Your desktop is only reachable over the local network."

how do i make it accessible over the web?

---

### Post by sahabcse on 2009-09-03
Hi

Remote Desktop Preference there is no Advance tab for allowing connections from internet, follow below url for more info

[http://community.livejournal.com/ubuntu_users/415064.html](http://community.livejournal.com/ubuntu_users/415064.html)

---

### Post by rhythmiccycle on 2009-09-03
so, does that mean if i down grade to ubuntu 8, then i can get www access?

---

### Post by sahabcse on 2009-09-03
try tightvncserver also

---

### Post by rhythmiccycle on 2009-09-04
what is the difference between tightvncserver and vnc4server?

i just installed VNC on my other computer running XP. using ubuntu's remote desktop i could, i could control ubuntu from my XP comp, but i was unable to transfer files, over LAN. (i want to transfer files)

intuitively i would think vnc4server would be more compatible, but i'm not sure.   

(note: the only reason i still use XP is for adobe cs4)

---

### Post by sahabcse on 2009-09-04
For transfer the files configure samba or use winscp. 


The difference between the tightvncserver and the normal vncserver is the data encoding, optimized for low bandwidth connections. If the client do not support jpeg or zlib encoding it can use the default one. Later versions of vncserver (> 3.3.3r2) support a new automatic encoding that should be equally good as the tightvnc encoding.

---

### Post by superprash2003 on 2009-09-04
do use remotedesktop over ssh for a more secure connection

---

