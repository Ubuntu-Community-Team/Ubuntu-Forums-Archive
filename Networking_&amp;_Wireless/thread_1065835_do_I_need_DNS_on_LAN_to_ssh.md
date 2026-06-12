---
title: "do I need DNS on LAN to ssh?"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by juan234 on 2009-02-10
I have a home network all running ubuntu 8.10.  two pc's are connected to the router (comtrend wireless) and the laptop is wireless.  I usually can connect via ssh to any machines no problem.  I have noticed that I cant connenct or rarely works, when my internet connection from my ISP is down.  

So my question is do I need a DNS server on my LAN to be able to always connect to my other machines?  

Many thanks.

---

### Post by DiGiTGOD on 2009-02-10
That says to me that it's not your ISP that's down... It's the router...

Your Wireless card won't care whether the router is connected to the outside world...

so unless you are doing something incredibly fancy and using your ISP designated IP's for all your internal computers (which I doubt), then the problem is that your router is being a bit dodgy...

Next time it happens, see if you can connect between the 2 wired machines, and whether they can access the internet... Then try to ping the IP from the Laptop...

On the other hand, I don't know enough about SSH to tell you whether that is adding to the problem, but from what I know... it shouldn't...

Hope this helps.
Martin

---

### Post by juan234 on 2009-02-10
Thanks!!!

Some trees had fallen and the telephone line was broken.  

My ISP doesn't do anything in regards to assigning my machines IP's only to my router.

I could ping all the machines fine with no internet connection... 

My connection is back up and I can connect fine.  I want to be able to connect all the time.  I usually listen to my music and movies via wireless and ssh.

saludos,

juan

---

### Post by juan234 on 2009-02-18
hi just wondering if anyone can answer my question?

---

### Post by Iowan on 2009-02-18
Just my opinion... DNS wouldn't be necessary if you use IP address, but either DNS, WINS or the /etc/hosts file would need to convert hostname to IP address.

---

### Post by juan234 on 2009-03-04
Hey Iowan,  thanks alot, your opion is the correct one, editing the /etc/hosts file worked.

---

