---
title: "Wireless connected but no internet"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by vader95 on 2010-03-07
Hi,

I have a belkin usb wireless adapter.  It will connect to my wireless access point, but it will not let me connect to the internet.  Also, i cannot connect to the file server that is set up on it?  Also, i did have wired ethernet on it, but i don't have connection with that anymore.

Any other information you need i can provide.

Thanks in advance,
vader95

---

### Post by 762sks on 2010-03-07
hope this helps! 

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by vader95 on 2010-03-07
thanks, but the driver is installed and working.  I cannot connect to [www.google.com]("http://www.google.com") or any other website.  i do connect to my router.  Also when i use ethernet, i lose the abbility to connect to these websites too, but i can ping and connect to the file server hard disk.

---

### Post by gordintoronto on 2010-03-07
It sounds like a DNS problem.  When you open Accessories/Terminal and enter this command:
cat /etc/resolv.conf 

what comes out?

On my system, I see two lines which begin, "nameserver."

If you use a static IP address, you must set up the nameserver. With DHCP, your router should provide nameservers.

---

### Post by vader95 on 2010-03-07
> **gordintoronto said:**
> It sounds like a DNS problem.  When you open Accessories/Terminal and enter this command:
cat /etc/resolv.conf 

what comes out?

On my system, I see two lines which begin, "nameserver."

If you use a static IP address, you must set up the nameserver. With DHCP, your router should provide nameservers.

How would i make a nameserver.  I do have a static IP on my system.

---

### Post by Iowan on 2010-03-07
If you're using Network Manager to configure your static address, you also have the option to manually configure nameservers (DNS). Besides your ISP nameservers, there's [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/"), and [Google DNS]("http://code.google.com/speed/public-dns/docs/using.html").

---

### Post by vader95 on 2010-03-07
i never needed to do anything with DNS before.  I used to be able to connect straight to the internet.  I do use network manager, though.

---

### Post by gordintoronto on 2010-03-08
If you previously used DHCP instead of a static IP address, your router provided the nameservers.

---

### Post by vader95 on 2010-03-08
The thing is when i set up the server, i used ethernet.  Now i need to move the server and i don't have an ethernet cable yet that will run up there.  I am using a wireless device configured with Network Manager.  I have a static IP set and ubuntu fire wall active.  When i connect with ethernet in my old environment, i can ping and access my server, when i move to wireless, i cannot ping or access the server.  Both of these don't allow me to get online.

I don't know if this helps clear anything up.  I tried with DNS but could not figure it out(I'm still a noob).

Thanks again,
vader95

---

### Post by vader95 on 2010-03-11
Hello, and thank you all for help.

I have fixed the problem with a reinstall of ubuntu.  I am in agreement with the DNS problem.  I didn't know what the name server would be and with the reinstall and windows, i got everything to work.  I appreciate all the help.


vader95

---

### Post by sdpiowa on 2010-03-12
> **vader95 said:**
> 
I have fixed the problem with a reinstall of ubuntu.


Please mark the thread as 'SOLVED' if you no longer need help.  :)

---

