---
title: "Hard time with eth0"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by claus on 2009-08-27
Hi,

since I upgraded to 9.04, I'm often experiencing the problem that Ubuntu doesn't manage to establish an **eth0** connection to my Samsung router. The problem: *Sometimes* it's there instantly after booting up, *sometimes* I can't get into the Internet for the entire day.

After much struggle yesterday & today, I finally *was* able to get a connection by setting the MTU value from 'automatic' to '3'. Did anyone out there experience a similar problem? How did you solve it? After making the change in the MTU value, I'm going to watch how Ubuntu behaves during the next days. Maybe that's the solution.

What could be the cause for this behaviour? What shell commands could give me a hint on what's the matter here?

Any help highly appreciated. ;-)

TIA,

Claus

---

### Post by bkratz on 2009-08-27
> **claus said:**
> Hi,

since I upgraded to 9.04, I'm often experiencing the problem that Ubuntu doesn't manage to establish an **eth0** connection to my Samsung router. The problem: *Sometimes* it's there instantly after booting up, *sometimes* I can't get into the Internet for the entire day.

After much struggle yesterday & today, I finally *was* able to get a connection by setting the MTU value from 'automatic' to '3'. Did anyone out there experience a similar problem? How did you solve it? After making the change in the MTU value, I'm going to watch how Ubuntu behaves during the next days. Maybe that's the solution.

What could be the cause for this behaviour? What shell commands could give me a hint on what's the matter here?

Any help highly appreciated. ;-)

TIA,

Claus


I know you already changed it but the value is questionable (1492 works well for me).  See this article on typical settings.

[http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by claus on 2009-08-27
> **bkratz said:**
> I know you already changed it but the value is questionable (1492 works well for me).  See this article on typical settings.

[http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

Thanks a lot! I changed the MTU value according to your recommendation & will see how this works.

Claus

---

