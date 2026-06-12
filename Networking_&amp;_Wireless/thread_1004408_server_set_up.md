---
title: "server set up"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by leg on 2008-12-07
How do I go about installing linux on a headless server. Can I connect monitor/mouse/keyboard and then do an installaiton to have it work correctly when it is diconnected from the keyboard etc and placed in a rack. The server would require apache2, mysql, subversion and ssh at a minimum and would be used to store and serve web and programming development projects. 

I am leaning towards installing the latest stable Debian on this system and would appreciate some hints and links to help achieve it. The network it will be on is windows based and I may need it to communicate with ldap servers and sans.

---

### Post by Dr Small on 2008-12-07
I have done this on my network, and it supports both wireless and ethernet, so here is how I did it.

[LIST]
[*]Put in a Dlink wireless card in the server.
[*]Hooked it up to keyboard, monitor.
[*]Installed the OS.
[*]Installed OpenSSH Server, configured it, and installed whatever else I wanted at the time.
[*]Configured /etc/network/interfaces for eth0 and a static IP.
[*]Removed the wireless card, keyboard, monitor.
[*]Placed server by router and wired it up with ethernet.
[*]Powered system on, and connected to it via SSH.
[/LIST]

Once you have SSH working on it, it's like literally sitting at it with a keyboard. From there, you can install whatever you want, and set it up how you want.

Dr Small

---

### Post by leg on 2008-12-07
That sounds exactly like what I need except I wont need wireless on it. I am currently downloading Debian stable iso to go on a usb stick for installing.

Thanks

---

### Post by Dr Small on 2008-12-07
> **leg said:**
> That sounds exactly like what I need except I wont need wireless on it. I am currently downloading Debian stable iso to go on a usb stick for installing.

Thanks
Yeah, I just did wireless because I don't have access to ethernet in my room, where my monitor/keyboard is, but that shouldn't be a problem if you already have ethernet access :)

---

### Post by Iowan on 2008-12-08
That's pretty much how I set up my servers - except that my last LAMP server is set up for DHCP.  The DHCP server issues it a static lease.  That lets me manage addresses from one machine (but mostly, just experiment with static leases). The machines only see a monitor/keyboard if something goes very wrong.

---

