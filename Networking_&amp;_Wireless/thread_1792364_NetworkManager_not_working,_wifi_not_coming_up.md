---
title: "NetworkManager not working, wifi not coming up"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by wrybread on 2011-06-28
Suddenly my wireless card isn't coming up automatically.

The following sequence fixes it:

```
ifconfig eth1-eth0 up
killall NetworkManager
NetworkManager restart
```

Obviously that's a total kludge though.

When I first boot up, the eth1-eth0 interface isn't up.

After bringing it up, NetworkManager doesn't start. Simply executing "NetworkManager start" tells me its already running.

Is there some way to "reinstall" or reset NetworkManager, and have my card start automatically?

Thanks for any help.

---

### Post by poolet on 2011-06-28
do you have install wicd?? 

To reistall the network manager go to system ->> administrator ->> synaptic packed manager find the network manager and delete it... restart your machine and then go again to synaptic and install it.. if your problem doesn't fix.... Remove the network manager and download wicd....

---

### Post by varunendra on 2011-06-28
Try adding **start networking** to your Startup Applications.

---

### Post by kunalgautam on 2011-12-02
Hey thanks for the tips, I was having same problem on my FC16 installation, and killing and restarting network service helped me :)

---

