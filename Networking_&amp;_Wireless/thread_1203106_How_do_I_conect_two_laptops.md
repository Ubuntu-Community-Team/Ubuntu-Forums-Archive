---
title: "How do I conect two laptops?"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by rob2nd9th on 2009-07-02
Very simply i have two laptops, and want to file share whats the easiest way to do this?

Thanks

---

### Post by philcamlin on 2009-07-02
get samba :popcorn:

---

### Post by joezamboni on 2009-07-02
Here is a good instruction on setting up samba.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by dmizer on 2009-07-02
What operaiting systems do the two laptops run? Samba is a bit complex to set up, so there's probably better ways if you are using Linux on both laptops.

---

### Post by rob2nd9th on 2009-07-03
both are running 9.4

was hoping there was an easy cable option?

---

### Post by lisati on 2009-07-03
> **rob2nd9th said:**
> both are running 9.4

was hoping there was an easy cable option?

If you're looking at using just cable, you might want to invest in a "crossover" cable. As far as the settings go, I'm going to have to ask someone else. (My networking experience is largely through routers)

---

### Post by rob2nd9th on 2009-07-03
Got a few cross over cables tried that just cant see how to "see" the other laptop and file i want to swap :(

---

### Post by dmizer on 2009-07-03
To file swap, you can set up NFS. If you want both computers to both host files and get files, then you'll have to set up both computers as both a server and a client. There's a fantastic and easy NFS howto in the 4th link in my sig.

You'll need to set both laptops for static IP. Neither laptop can have the same IP address as the other.

---

### Post by puppywhacker on 2009-07-03
You'll need to assign static ip-addresses to the laptops which are in the same range like 192.168.0.1 and 192.168.0.2 There is a networking icon in the right-top.

once you have done that you can see in a terminal with "sudo mii-tool" and "ifconfig" if you have a link and ipaddress.

Then use sftp or samba to connect and share files with nautilus the file browser. There is a menu-option that says "Connect to Server"

---

### Post by stinger30au on 2009-07-03
easiest way to share data on 2 or more pc's running 9.04 is "giver"

sudo apt-get install giver

this little gem of software is a bit of magic i assure you

perfect for lans

no config, nuffin, just install it and it configures itself

GIVER ROCKS!

---

### Post by rob2nd9th on 2009-07-03
> **puppywhacker said:**
> You'll need to assign static ip-addresses to the laptops which are in the same range like 192.168.0.1 and 192.168.0.2 There is a networking icon in the right-top.

once you have done that you can see in a terminal with "sudo mii-tool" and "ifconfig" if you have a link and ipaddress.

Then use sftp or samba to connect and share files with nautilus the file browser. There is a menu-option that says "Connect to Server"

:confused: that is way over my head, cant i plug a crossover cable in one and the other and hind the other laptop in places?

I just want simple, tried the NFS and that just got to confusing for me just now,

---

### Post by rob2nd9th on 2009-07-03
> **stinger30au said:**
> easiest way to share data on 2 or more pc's running 9.04 is "giver"

sudo apt-get install giver

this little gem of software is a bit of magic i assure you

perfect for lans

no config, nuffin, just install it and it configures itself

GIVER ROCKS!

Ok installed, but how do you get one to see the other? Have two laptop sat less than 2' apart and all i want to do is share files from one to the other? file/fils to big to burn or i would have done that.
Not being abel to link two computers in win-dose was one of the reasons i moved over now im pulling my hair out theres lot of how to's that seam overly complex? Not happy :( thourt it would have been easer?

---

### Post by dmizer on 2009-07-03
First, if you're using a crossover cable to connect both machines then you have to manually assign both machines a static IP. Once you assign both a static IP, make sure you can ping between both machines. For example:

Machine 1 IP = 10.8.0.1
Machine 2 IP = 10.8.0.2

From machine 1, do this:
```
ping -c 4 10.8.0.2
```
You should see something like this:
```
PING 10.8.0.2 (10.8.0.2) 56(84) bytes of data.
64 bytes from 10.8.0.2: icmp_seq=1 ttl=64 time=0.919 ms
64 bytes from 10.8.0.2: icmp_seq=2 ttl=64 time=0.875 ms
64 bytes from 10.8.0.2: icmp_seq=3 ttl=64 time=0.808 ms
64 bytes from 10.8.0.2: icmp_seq=4 ttl=64 time=0.855 ms

--- 10.8.0.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 0.808/0.864/0.919/0.044 ms
```

If you are successful, then try the same with the second machine. Once you have a successful ping both ways, then you will hopefully be able to use giver.

---

