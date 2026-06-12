---
title: "Lan networked laptop with wifi internet connecivity problem"
date: 2012-08-02
forum: Networking &amp; Wireless
---

### Post by Rayaz on 2012-08-02
I have an Acer laptop with Ubuntu 12.04. This is networked to another computer over LAN. My internet connection is through a wifi router. Both connections get connected. However, when connected to LAN I cannot access the internet. If I pull out the LAN cable, internet starts working. 

I cannot connect the wifi router to the LAN network. Any other solution would be welcome!

Regards

---

### Post by Beacon11 on 2012-08-02
No problem! Edit your wired connection via NetworkManager, then:

IPv4 Settings > Routes > check "Use this connection only for resources on its network"

Now you should be able to connect both and enjoy separate connections. I believe ethernet was given the priority because the use case assumption was "User A is connected via wireless while roaming his home, carrying his laptop around. User A then sits at his desk, where he has an ethernet cable for his laptop. He plugs the ethernet cable in." Since both wifi and ethernet were for the same network, obviously wired should be preferred over wireless. Someone may not have thought that through all the way...

UPDATE: Found this too-- same solution, but has pictures: [http://askubuntu.com/questions/10741/how-to-set-up-dual-wired-and-wireless-connections](http://askubuntu.com/questions/10741/how-to-set-up-dual-wired-and-wireless-connections)

---

### Post by Rayaz on 2012-08-03
Thanks, will give it a try and let you know.

Regards

---

### Post by Beacon11 on 2012-08-04
> **Rayaz said:**
> Thanks, will give it a try and let you know.

Regards

Is this solved, then?

---

### Post by Rayaz on 2012-08-15
It works upto a point. I can access the internet but it is very slow. When I disconnect the LAN it speeds up to its normal speeds.

Any suggestions?

---

