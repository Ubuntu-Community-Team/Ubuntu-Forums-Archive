---
title: "Connecting to a Windows Box"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by Ioneye on 2008-12-09
My question is how can i connect to a shared folder in windows xp from my ubuntu?
i mean in windows you can do: Start - Run - \\ip and connect to the selected to pc.
Is there a similar way for Ubuntu?

---

### Post by eder.apt-get on 2008-12-09
In my Hardy I´m able to see my Vista partition using Nautilus. If you type your IP, Ubuntu thinks you´re trying to access a network, but I could be wrong.

---

### Post by doug-M on 2008-12-09
> **Ioneye said:**
> My question is how can i connect to a shared folder in windows xp from my ubuntu?

You can try:
  Places > Connect to Server
    Service Type: windows share

OR:
  Places > network
     You might have an icon that says "Windows Network", double click on that.

OR:
  In the file browser (Natilus)
    Location: smb://IP/
      (where IP is the IP address of the windows machine you want to connect to)
      You might need to hit the toggle button on the left, 
        says: "Toggle between button and text-based location bar"

---

### Post by Ioneye on 2008-12-10
Thank you all for your answers they were very helpfull.

---

