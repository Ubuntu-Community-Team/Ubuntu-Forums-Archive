---
title: "Wireless not starting at reboot"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by eae225 on 2009-12-27
Hi, I'm new to LINUX. I hope I didn't overlook the solution. I can connect using my wireless, but it doesn't set up automatically. I don't have a choice after starting up, I have to rmmod b43, ssb, and wl, then depmod, then modprobe wl. Within about 30 seconds, the network manager finds the wireless and makes the connection. 
I don't want to have to manually start the wireless every time I restart my laptop. I am using an HP Pavilion dual-boot with windows vista and ubuntu 9.10. The wireless driver is broadcom b43xx (can remember the last two ...). 

Thanks for any help!

---

### Post by shredder12 on 2009-12-29
after doing
```
sudo modprobe wl
```
you should also add it to /etc/modules.. this will fix the problem..

---

### Post by hector077 on 2009-12-29
same problem here how you input the code i'm new:confused:

---

### Post by eae225 on 2009-12-30
You will have to use a text editor - such as gedit. You will have to make the modification as sudo root (type sudo gedit /etc/modules).

---

### Post by Project PWNED on 2009-12-30
Does your /etc/network/interfaces have auto wl at the top?

```

auto (network interface)
iface (network interface) inet static
        address 192.168.0.100
        netmask 255.255.255.255
...
...

```

Yours wont have the ... below netmask, but actual stuff - I pasted this from my VPS because I'm currently installing Ubuntu as we speak.

---

### Post by shredder12 on 2009-12-30
Please mark the thread solved using the thread tools button if the problem is solved...

---

### Post by hector077 on 2009-12-30
i fund this it help me    [http://www.youtube.com/watch?v=1mZJYz4qUVU&feature=related](http://www.youtube.com/watch?v=1mZJYz4qUVU&feature=related)

---

