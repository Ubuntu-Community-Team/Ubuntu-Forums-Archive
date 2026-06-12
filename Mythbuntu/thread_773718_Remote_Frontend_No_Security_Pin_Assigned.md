---
title: "Remote Frontend: No Security Pin Assigned"
date: 2008-04-29
forum: Mythbuntu
---

### Post by bla2000 on 2008-04-29
After I start my remote frontend it identifies my backend "Hardy1: MythTV AV Media Server" but when I press "ok" it displays the message "No Security PIN assigned. Run mythtv-setup to set one."  Where do I set the security pin on the backend?

Thanks

---

### Post by tcpankon on 2008-04-29
had the same issue.  if you run mythtv-setup on the backend there should be a screen under general for setting the PIN.  I hope I am pointing you in the right direction as I am at work away from my mythbox

---

### Post by lingenfr on 2008-11-02
That answer is correct. Don't know why other clients will connect at not my newest one, but oh well. Run mythtv-setup on the backend and goto General. On the first page is a field where you can set the PIN. Then when you run mythtv-frontend and select your backend, you can enter the PIN. When asked, I elected to save the backend info as opposed to the database. Not sure whether that was correct or not, but it worked.

---

### Post by SiHa on 2008-11-03
Backend setup.
In the PIN entry, you should set it to **0000** if you don't want a pin. Not exactly intuitive.

---

### Post by llama46 on 2009-01-06
edit... above worked great

---

