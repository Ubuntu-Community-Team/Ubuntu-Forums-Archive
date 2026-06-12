---
title: "Network manager replaces default route when eth cable is plugged"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Glutexo on 2010-05-05
Hello.

I have been encountering this problem, not only on 10.4, but on older versions too: I use a wifi router to connect my laptop to the Internet, but sometimes I need to connect directly to another computer to move some files over GLAN. But Ubuntu's Network manager doesn't allow me to configure the eth0 interface without specifying a gateway (no gateway = grey submit button), but when a gateway is specified, it always rewrites the default gw specified already by the active wifi connection and returns back after unplugging the eth cable.

Of course this can be solved by a few route commands, but this is unacceptable since it is needed to establish the cable connection without any further assistance from within and as well without replacing the default gw and thus breaking the Internet connection. Is there, please, any possibility how to prevent Network Manager from replacing these routes?

Thank you in advance for any tips, how to get rid of this problem!

---

### Post by Glutexo on 2010-05-05
Maybe found a solution by manually editing /etc/NetworkManager/system-connections/<ConnectionName> and in the [ipv4] section setting ignore-auto-routes and ignore-auto-dns both to true (and setting the gw to 0.0.0.0, but I am not sure whether this is needed). Works for now even after reboot. Hope it will last.

---

### Post by Karl1982 on 2010-12-13
Just ran across your thread trying to solve this for myself.  I did find a solution.  In NetworkManager, edit the connection you're using for local only.  You have to enter a default gateway (I consider this to be a bug as a default route is not necessary for IP to work on the local subnet).  Under IPv4, click "Routes..." and then check the box that says "Use this connection only for resources on its network."  That causes it to ignore the default gateway and only use that connection for its particular subnet.

---

### Post by fourky on 2012-12-02
Hello [Karl1982]("http://ubuntuforums.org/member.php?u=1063279")

Thank you so very much for this bit of info you have shared there! You saved my sanity on that one...
In Ubuntu 10.04, to set a "useless" gateway route way not necessary... Not sure why this is necessary now, but it is!

Thanks again for this post!

---

### Post by wildmanne39 on 2012-12-02
Old thread closed.

---

