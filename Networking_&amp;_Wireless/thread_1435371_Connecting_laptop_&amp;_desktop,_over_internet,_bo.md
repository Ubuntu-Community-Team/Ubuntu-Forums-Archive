---
title: "Connecting laptop &amp; desktop, over internet, both connected to same router"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by opsahl on 2010-03-21
Hello,

I want to connect my laptop and my desktop and set them up to automatically sync a couple folders. I would also like the option of remotely controlling ("driving") the PC from the laptop, or vice-versa.

They are both running Ubuntu 9.10 (Karmic Koala).  They both connect to the Internet through a WRK54G Linksys wireless router.  The PC is connected to one of the Ethernet ports, and the laptop connects wirelessly. 

Along with not knowing which tool is best (VNC, RDC, etc.), the other problem we run into is that as far as the Internet is concerned, both PC's have the same IP.  I would imagine the setup would include some port forwarding on the router?  I know how to do that if need be.  

I'm a Windows expert, a networking novice, and a Linux newbie.  What are the best tool(s) for the job, and how would I set them up to do what I want?

Thanks,
Opsahl

---

### Post by chili555 on 2010-03-21
> both PC's have the same IP.I doubt it. Please double-check with the terminal command:```
ifconfig
```> I would imagine the setup would include some port forwarding on the router?Port forwarding is not required.

I think you want rsync. Find out more with:```
man rsync
```

---

### Post by opsahl on 2010-03-21
Will look into rsync.  

The PC's are not connected except to the Internet.  The Internet IP that both reveal to the Net is the *router's* IP, therefore as far as the internet is concerned, the IP's are the same. 

Those connecting to the router are assigned a standard progression of IP's (192.168.1.10x).  Will rsync connect using the local IP's even though we're working with a Broadband Internet router?

---

### Post by chili555 on 2010-03-21
> Those connecting to the router are assigned a standard progression of IP's (192.168.1.10x).Did I misread? Aren't *both* connected to the router? Wired, wireless or otherwise?> Will rsync connect using the local IP's even though we're working with a Broadband Internet router? Certainly. The router is what makes it all possible.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

Especially see **Backup Over Network**. There is a GUI front end to do this, but rsync is fast and easy and does a lot more than just copy one file to another computer.

---

### Post by opsahl on 2010-03-21
chili555, thank you for your help so far.  I'm thankful to have someone with your experience willing to give some advice.

Will you help me break down "remoteuser@remotehost.remotedomain" as it pertains to my situation?

If doing this from my laptop, would that be [email]PCloginName@localIP.router[/email]IP ?  

Probably a stupid sounding question to a guru.  I had not previously known that a router designed to distribute an internet connection would also create a network connection between a wired and wireless computer.  Exciting :)

Opsahl

---

### Post by chili555 on 2010-03-21
Assume the user's name on the other machine is chili and that the machine's IP address is 192.168.1.103. The directive would then be chili@192.168.1.103. I haven't poked around in the manual for a while, but I am fairly certain you can add the directory you want to get into, something like chili@192.168.1.103/home/chili/Shared.

In a simple home network, you probably don't need or have set up the .Domain part.

Soon, when you get proficient with this, you can set up a cron job to synchronize files automatically every night at 2:00 am. Then you will want to build a home server out of that old 900 Mhz Pentium and set it up wirelessly in the garage for both computers to sync to.

But baby steps...

---

### Post by opsahl on 2010-03-22
Got it.  Cron is next.  Thanks for the baby steps. :)

---

