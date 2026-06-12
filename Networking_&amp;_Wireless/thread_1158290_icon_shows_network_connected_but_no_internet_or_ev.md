---
title: "icon shows network connected but no internet or even local one"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by fcastillo on 2009-05-13
I really need some help, because this bug is really annoying. I can connect to the wireless network, but after a couple of minutes I don't have internet but it show that I'm still connected to the network.
Other computers have internet, and I have to disconnect from the network and then re-connect to get the internet back, that's why I know it's not related with my router or even ISP.
I've used network manager and WICD, and the problem persists.

I'd really appreciate any help, this bug is freaking annoying, because I let something downloading over night, and after 20 min I can't get internet access unless I restart the connection.

Oh, one last thing... I just don't lose internet connection, I lose all connections, the icon show that I'm still connected to the network but I can't even ping a local IP, or even my router.

---

### Post by dgmitch on 2009-05-16
I am running a Lenovo T61 with the exact same problem under 9.04.  This seems to occur when I resume from sleep.  I have found that I can disconnect and reconnect 2-3 times and eventually the connection will start.  What is confusing is that it says I'm connected to the network but this is definitely not true.

---

### Post by fcastillo on 2009-05-17
I'm talked to another friend, and he has the same problem with a Dell.
It seems that using WICD and installing ubuntu-backports-jaunty helps a little, now it disconnects less often.
I also installed the prososal repository that has a new kernel, i don't know if it's a convination of any of the 3 or one of them, but it looks like it almost never disconnects. Sometimes it can last a couple of days without disconnecting, but the problem is still there.
I wish somebody would read this post and helps us. And if somebody has reported a bug about it, so we can subscribe so the developers now that a lot of people have this problem

---

