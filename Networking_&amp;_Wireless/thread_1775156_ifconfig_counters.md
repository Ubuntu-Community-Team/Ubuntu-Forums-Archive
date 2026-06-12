---
title: "ifconfig counters"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2011-06-04
Hi all i have a dedicated server and i would like to know if i can reset the counters on the ifconfig command without restarting the server ?
[IMG]http://elliotbeken.com/img/Counters.jpg[/IMG]

Thanks Elliot

---

### Post by SeijiSensei on 2011-06-04
Don't hold me to this, but I think they reset if you bring the interface down.  Of course, you can't do this remotely; you'll need to be seated at the console.  Try "sudo service networking restart" and see what happens.

---

