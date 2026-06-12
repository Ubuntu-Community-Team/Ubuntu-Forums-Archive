---
title: "ping"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by aravindsarma on 2009-07-05
when I do 
ping 127.0.0.1 in my laptop

it only shows

PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data

and that's all, nothing else
previously, this was not the case. This problem arised after I modified the /etc/network/interfaces

into 

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.10.10
netmask 255.255.255.0
gateway 192.168.10.1

iface eth1 inet static
address 192.168.10.10
netmask 255.255.255.0
gateway 192.168.10.1

please help me fix the problem.

---

### Post by Barriehie on 2009-07-05
Did you restart your network services?
```

sudo /etc/init.d/networking restart

```

After it works maybe keep a copy of the file you changed for future.  **[color=green]sudo cp <whateverfile> <whateverfile.works>[/color]**


Barrie

---

### Post by Brandon Williams on 2009-07-05
First, try 'ping localhost', to see if localhost is using a different address. Sometimes, it will use 127.0.1.1 instead of 127.0.0.1, for example. You can also check this with 'ifconfig lo'.

---

### Post by aravindsarma on 2009-07-08
Hey, thank you all very much. Actually what I posted there is the correct modification done to my /etc/network/interfaces

I came to know that fact only after I restarted my laptop. Everything is fine after that. Previously I have done a lot of modifications with no success and I posted the final modification here and I gave up. But to my surprise it is correct.

Last time when I tried doing 

sudo /etc/init.d/networking restart

I didn't work well as my modification to the interfaces file was wrong.No everything is smooth. thank you very much again.

---

