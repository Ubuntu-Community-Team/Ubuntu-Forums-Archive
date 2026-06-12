---
title: "Where are Network Connections stored?"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by tim042849 on 2011-03-16
I am using ubuntu 10.04. I have used ubuntu/kubuntu since 7~
It used to be (if memory serves me) that network settings were
stored in [COLOR="Blue"]/etc/network/interfaces[/COLOR].
Where are they stored now?
Note: My current [COLOR="Blue"]/etc/network/interfaces[/COLOR]
has only this: ```

auto lo
iface lo inet loopback

```
Thanks
tim

---

### Post by dineshs on 2011-03-17
/etc/NetworkManager/system-connections

---

### Post by tim042849 on 2011-03-17
> **dineshs said:**
> /etc/NetworkManager/system-connections
Thank you. That clears up a bit.
FYI: On my machine, as I stated previously,
[COLOR="Navy"]/etc/network/interfaces[/COLOR] has only
```

auto lo
iface lo inet loopback

```
**However,** another individual who also has ubuntu 10.04,
has the following: ```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```
Does that mean that ubuntu will also read [COLOR="Blue"]/etc/network/interfaces[/COLOR]?
Thanks
tim

---

### Post by BkkBonanza on 2011-03-17
If Network Manager is runnign then it mucks it up and takes over the settings. The setings in the interfaces file will likely get over written by Netowrk Manager.

Which is why I've always preferred Wicd over Network Manager. I still have manual control too.

---

### Post by tim042849 on 2011-03-17
> **BkkBonanza said:**
> If Network Manager is running then it mucks it up and takes over the settings. The setings in the interfaces file will likely get over written by Netowrk Manager.

Which is why I've always preferred Wicd over Network Manager. I still have manual control too.
My brother would say the same. Good to have a matching second  opinion. 
However, my problem is that that last time I did an install,
I could not configure thru the gui at all. The apply buttons
were inactive. So, I'm thinking as a bootstrap, in an 'emergency' 
such as this, I could put settings in [COLOR="Navy"]/etc/network/interfaces[/COLOR] just to get 
a network connection and then get Wicd.
What is your opinion?
thanks
tim

---

### Post by BkkBonanza on 2011-03-17
What I would do from the command line is this,

sudo apt-get remove network-manager

then edit the /etc/network/interfaces to have the desired manual settings,

then

sudo /etc/init.d/networking restart

Now you should hopefully have a connection.
Now you can,

sudo apt-get install wicd

Also, I do think if you simply do this last step first then it auto removes the network-manager for you - but I'm just not sure on that, and if you can't get connected to the web then you can't do the install, but the remove should still be workable.

---

### Post by tim042849 on 2011-03-17
> **BkkBonanza said:**
> What I would do from the command line is this,

sudo apt-get remove network-manager

then edit the /etc/network/interfaces to have the desired manual settings,

then

sudo /etc/init.d/networking restart

Now you should hopefully have a connection.
Now you can,

sudo apt-get install wicd

Also, I do think if you simply do this last step first then it auto removes the network-manager for you - but I'm just not sure on that, and if you can't get connected to the web then you can't do the install, but the remove should still be workable.
Sounds like a really good plan. :cool:
Thanks very much.
tim

---

