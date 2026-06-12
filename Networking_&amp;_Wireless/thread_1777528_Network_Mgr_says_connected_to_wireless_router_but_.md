---
title: "Network Mgr says connected to wireless router but cannot ping it or access internet"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by bubbasmurf on 2011-06-07
I am new to linux.  I just installed in on my dell inspiron 6400 but i am unable to access the internet.  on the network manager applet, it says i'm connected.

i tried to ping 192.168.0.1 and it says network is not reachable.

So i'm completely confused.. I do not have broadcom card and i *did not* have bcmwl-kernel-source package installed from the get-go.  

Anyone have any ideas?

---

### Post by bubbasmurf on 2011-06-08
After banging my head against the wall many times... something magically worked.  I stopped network manager, restarted, stopped wlan0, and restarted... etc.

Now I do not know what fixed it.  I modified the /etc/network/interfaces to add

auto wlan0
iface wlan0 inet dhcp

Other things I did..

modified the /etc/NetworkManager/NetworkManger.conf with (from false -> true)

[ifupdown]
managed=true

Rebooted machine .. then it worked..  Maybe it might help others with the same problem.

I think there is an issue here.  Network manager reports connected when clearly it did not get pass there.  I even tried with no passwords.. it says connected but on the other end it does not match up w/ the router's status.  

Someone should address this.

---

### Post by Lateralus138 on 2011-06-09
Thank you for trying to help, but this did not work for me.

---

