---
title: "Mapping a drive"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by LaJuan on 2013-03-08
Hi,

I've read many post on drive mapping and mostly to a windows drive. I'm running 12.04 and the drive isn't a windows drive. It's a drive that is connected to my wireless router. Is there a way to map this drive to my computer? I can go into the router and see the drive's IP address but, I'm at a complete lost on how to map it. Any old post to learn on my own is also welcomed and needed to improve my self-knowledge of Ubuntu!!!!

Thanks,

LaJuan

---

### Post by vanadium on 2013-03-08
In the file manager, there is the option "File - connect to server" that allows to mount a file server as a local directory. You have to know the protocol your network drive uses. Likely, it will be samba (cifs), aka "Windows share" in the "Connect to server" dialog.

---

### Post by LaJuan on 2013-03-08
Thanks!!!!!!!! I'm looking into the Samba program right now!!!!!

---

