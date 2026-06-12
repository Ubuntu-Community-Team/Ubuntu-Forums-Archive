---
title: "[Ubuntu as XP application] Setting up wireless connection on 8.10"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by vikashtulsiyan on 2009-04-08
i have installed ubuntu as an application on windows XP. When i log into ubuntu, my lan connection works great. However i am not able to connect to wireless network.

I tried looking for help in help.ubuntu.com. It asked to looked into Network Manger under system administrator. I dont find anything like it there. I  have network tools as the only link related to networks.

Moreover one help forum asked me to look into output of ispci. I dont find this command on my system.

Do i have to install any additional package for wi fi to work?

TIA

---

### Post by cariboo on 2009-04-08
You are not looking in the right places, Network Manager is no longer located in System-->Aministration. When you click on the network icon on the top panel do you see any wireless network? you may have to disconnect the network cable in order for this to works. The lspci command must be run in a terminal. I'm actually going to suggest a different command that will tell us if your wireless device is detected and the driver is loaded. Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

The above command will show a listing of the details of your network devices. The output should look something like this:

```
*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:f0:a3:ca:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11bg
```

The above is the output for my wireless device on my media center, I've cut the results for the wired network device.

Jim

---

