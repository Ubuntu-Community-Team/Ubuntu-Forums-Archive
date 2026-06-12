---
title: "ssh cannot resolve host name"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by scottbomb on 2012-05-05
I can ssh to the other machine using the ip address, but not the machine's host name.

This works: ssh -vX myusername@192.168.1.2 
This doesn't: ssh -vX myusername@main-linux

main-linux is listed in the /etc/hosts file.  
cat hostname result: main-linux

The same is true when connecting from the laptop.

This works: ssh -vX myusername@192.168.1.3 
This doesn't: ssh -vX myusername@laptop-linux

What could be wrong?

---

### Post by poolet on 2012-05-06
> **scottbomb said:**
> I can ssh to the other machine using the ip address, but not the machine's host name.

This works: ssh -vX myusername@192.168.1.2 
This doesn't: ssh -vX myusername@main-linux

main-linux is listed in the /etc/hosts file.  
cat hostname result: main-linux

The same is true when connecting from the laptop.

This works: ssh -vX myusername@192.168.1.3 
This doesn't: ssh -vX myusername@laptop-linux

What could be wrong?

if your not using Ipv6 try to disable, restart the server and try again..... 

see older post below::: 

[http://ubuntuforums.org/showthread.php?t=1662246&page=2](http://ubuntuforums.org/showthread.php?t=1662246&page=2)

[http://ubuntuforums.org/showthread.php?t=1471622&page=3](http://ubuntuforums.org/showthread.php?t=1471622&page=3)

---

### Post by codemaniac on 2012-05-06
> **scottbomb said:**
> I can ssh to the other machine using the ip address, but not the machine's host name.

This works: ssh -vX myusername@192.168.1.2 
This doesn't: ssh -vX myusername@main-linux

main-linux is listed in the /etc/hosts file.  
cat hostname result: main-linux

The same is true when connecting from the laptop.

This works: ssh -vX myusername@192.168.1.3 
This doesn't: ssh -vX myusername@laptop-linux

What could be wrong?

What does hostname returns ?
```
hostname
```

---

### Post by Lars Noodén on 2012-05-06
Just checking something obvious, but are you sure you've edited the right hosts file?  The main-linux machine should contain an entry for laptop-linux and vice versa.

---

### Post by scottbomb on 2012-05-06
To clarify, files on main-linux in /etc/hosts has:

127.0.0.1    localhost
127.0.1.1.   main-linux

[and a bunch of ipv6 lines I don't care about]

and /etc/hostname has just this one line:

main-linux

On the latop, it's very similar:

/etc/hosts has:

127.0.0.1    localhost
127.0.1.1.   main-linux

and /hostname has the single line:

laptop-linux

And for what it's worth, I'm running Xubuntu and each computer can see each other by their host names and share files just fine with Samba.

---

### Post by scottbomb on 2012-05-07
> **Lars Noodén said:**
> Just checking something obvious, but are you sure you've edited the right hosts file?  The main-linux machine should contain an entry for laptop-linux and vice versa.

I will add that tonight and see what happens. Shouldn't the OS or some other program (maybe SSH) already have done this for me? I'll try it and report back my result.

---

### Post by Lars Noodén on 2012-05-07
> **scottbomb said:**
> I will add that tonight and see what happens. Shouldn't the OS or some other program (maybe SSH) already have done this for me? I'll try it and report back my result.

SSH won't change /etc/hosts.  /etc/hosts is generally left alone and name lookup is managed by DNS.  Some applications even are able to ignore it or bypass it completely.

---

### Post by scottbomb on 2012-05-08
I made the suggested changes to /etc/hosts on both machines and now it works perfectly. I don't know why, but when I was using this:

ssh -vX username@main-linux

or, from the other machine

ssh -vX username@laptop-linux

They each were trying to resolve an IP of 192.168.2.x. These machines are (set by the router) as 192.168.1.x. Interesting.... Anyhow, after adding lines to the /etc/hosts files, everything worked. Here's an example for anyone wondering how:

192.168.1.2     main-linux 

And on the other machine:

192.168.1.3     laptop-linux

I wonder if the router seems to be playing a role on this. The router has different names for these machines. The reason was because I dual-boot Win 7 and Xubuntu on both. Maybe I should keep the names the same in both OSes. In other words, just "laptop" and "main", in both Xubuntu and Windows, on both machines as well as the router. That way there's no confusion about who's who. Does this seem like a logical choice or am I over-thinking this?

---

