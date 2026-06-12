---
title: "Help with basic wireless stuff"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by leonardevens on 2012-01-13
I have a laptop running ubuntu which I don't use much.  (I mainly use Fedora 14 Linux.)   The last time I used the ubuntu machine was on a friend's home wireless network.   This was about two months ago, and after some fiddling I got it to recognize the local wireless network and connect to it.

I am now in hospital recovering from back surgery.  I've connected successfully to the local wireless network here with my Nook, and that works okay.   I would like to use my ubuntu laptop here. After logging into the machine, I can't seem to do anything to add the local wireless network and connect to it.

Would anyone remind me of what to do to search for wireless networks?  And any additional suggestions would be appreciated.

I am posting this on a computer near the nurse's station, which I can come back to.

---

### Post by jonobr on 2012-01-13
Hey there 

Hope the back is ok and your recovering , you could use the terminal window in applications -> accessories,

Assuming alls ok with your driver

try bringing up the interface

```
sudo ifconfig wlan0 up
```

check ifconfig that its there..... if it has an IP address you may be ok at this point,.

scan for the ap


```
sudo iwlist wlan0 scan | grep ESSID 
```

(Drop | grep ESSID to see more info)

This should show you your AP (eg mynetwork)

connect
```
sudo iwconfig wlan0 essid "mynetwork"
```

if you need to force an IP address acquisition 

```
sudo dhclient wlan0
```

Post an errors you may see along the way

---

### Post by leonardevens on 2012-01-15
Thanks for the help.

As typically happens when I use my ubuntu machine, nothing seems to work for a while, and then , by magic, ubuntu finds all the available local networks and gives me a chance to connect.  That is what happened this time also.  So I am now connected.

---

### Post by Iowan on 2012-01-15
You may want to edit your email address out of your first post - otherwise, spammers may start sending you offers you didn't know you wanted.

Glad you got the problem sorted out. If it stays fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

