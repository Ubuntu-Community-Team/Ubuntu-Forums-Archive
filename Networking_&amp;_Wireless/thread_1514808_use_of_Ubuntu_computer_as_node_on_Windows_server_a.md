---
title: "use of Ubuntu computer as node on Windows server application"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2010-06-21
Can a computer that is running Ubuntu use the "remote desktop" function of Ubuntu to run as a remote node on a M/S Windows based server software application ? 

Is the possibility of doing this, dependent on the programming of the server based software application or is this strictly a matter of successful communications between the 2 different types of operating systems on the Ubuntu workstation and the Windows server and will they/the application would run correctly on the Ubuntu workstation/computer regardless of the programming of the server based software application ?

Thanks.

---

### Post by wpshooter on 2010-06-22
No takers on this question ?

---

### Post by jnorthr on 2010-06-22
shouldn't really need to do any programming as samba shares should fill the bill. On one end of the wire you have a system with a samba client and on the other end you have another system running as a samba server - almost like a 'real' client-server topology. This will allow file and data transfers between systems. If you are thinking of remote-control of the desktop of the target system, look at VNC or Chicken-VNC if you have an apple mac as a client. Be ware that windows 7 does not like to play nicely with ubuntu, i've read that the m/s engineers even fixed things so you cannot reach windows 7 from a ubuntu system. eventually we'll bypass their funny code andmake it work anyway.

---

### Post by wpshooter on 2010-06-22
> **jnorthr said:**
> shouldn't really need to do any programming as samba shares should fill the bill. On one end of the wire you have a system with a samba client and on the other end you have another system running as a samba server - almost like a 'real' client-server topology. This will allow file and data transfers between systems. If you are thinking of remote-control of the desktop of the target system, look at VNC or Chicken-VNC if you have an apple mac as a client. Be ware that windows 7 does not like to play nicely with ubuntu, i've read that the m/s engineers even fixed things so you cannot reach windows 7 from a ubuntu system. eventually we'll bypass their funny code andmake it work anyway.

Thanks, but I don't think you understood my question.

The HOST server (and the hosted application) would be a MS Windows application and would be running on a M/S windows server and I don't think it is going to be able to run SAMBA is it or at least not natively, is it ???

Thanks.

---

