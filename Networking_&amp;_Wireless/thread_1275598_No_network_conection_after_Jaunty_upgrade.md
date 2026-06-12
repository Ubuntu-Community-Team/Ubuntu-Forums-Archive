---
title: "No network conection after Jaunty upgrade"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by tstack77 on 2009-09-26
I just now upgraded to Jaunty through the upgrade manager and lost internet/network connections.

With Intrepid I had issues setting a static IP so I configured one in /etc/network/interfaces and disabled network manager. It worked fine until the upgrade. 

I tried to add a network interface using network manager by adding the mac address but got nowhere. Obviously this is due to me disabling it but I don't know how to re-enable or reinstall without a working connection. I am lost with what to do next. 

How do I enable network connections again?

---

### Post by shredder12 on 2009-09-26
aren't you able to connect to internet using your static ip settings in /etc/network/interfaces file..??

---

### Post by tstack77 on 2009-09-26
No, I can't even ping my router. The strangest thing is that I can see both ethernet ports in the network manager (they are greyed out), so I know that they are recognized.

It really makes no sense.

---

### Post by shredder12 on 2009-09-27
First of all remove all the manual settings you did in you /etc/network/interfaces file.. you can jst comment it by prepending a "#" before those lines.
Otherwise these lines will jst confuse Network Manager.

And, now lets jst try and connect using the Network manager.

I haven't used a router, so is it possible to ping it without getting an IP address..??

I think we will first have to set the static IPs to connect to the router .. and then we will see if Internet works or not..

Btw.. did you try to add another interface in intrepid too.. or you are trying to add one after upgrade.??

---

### Post by Iowan on 2009-09-27
> **shredder12 said:**
> I haven't used a router, so is it possible to ping it without getting an IP address..?? No, the machine will need an IP address of some kind - preferably in the same subnet.
Per **shredder12**'s suggestion, comment out everything in */etc/network/interfaces* **except** the two lines configuring "lo". Restart (or reboot), see if NM sees the interface(s), and hopefully got an IP address.

---

### Post by tstack77 on 2009-09-28
I tried to comment out the changes in 'interfaces' but it did no good for enabling NM. I still have all interfaces grayed-out. 

I am pretty certain that I disabled NM when I wasn't able to successfully set a static IP...I can't find the post that I followed then, but it was what was offered here as a workround to the static IP issue.

Also, I did not try to add the interface in Intrepid before the upgrade. I simply tried to add it to the NM in Jaunty when I couldn't connect. To clarify, no interfaces were displayed in NM under 'connections' before I tried to manually add it. However, they all show up (grayed-out) when I click on the icon in the notification area.

I did this to myself almost a year ago, I just can't figure out how to solve it now.

---

### Post by shredder12 on 2009-09-29
At this point I will suggest you to reinstall network manager..
I guess there is some configuration problem with the Network Manager somewhere..

So, remove it ..
```
sudo apt-get --purge remove network-manager
```
It should remove all the configuration files as well...
Now, install it again
```
sudo apt-get install network-manager
```

Now, since interfaces file is all cleared up and Network Manager is new.. I hope this will give a fresh start and things will work for you..

---

