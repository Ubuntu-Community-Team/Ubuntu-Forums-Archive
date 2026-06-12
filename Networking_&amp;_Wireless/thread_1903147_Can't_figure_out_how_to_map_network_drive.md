---
title: "Can't figure out how to map network drive"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by erbad on 2012-01-01
I'm not sure how to map a network drive in Ubuntu.

In the past, I would just click on the places icon and all of my NTFS windows shares would show up.  However, now they are not, yet I can ping the IP addresses of the NTFS Windows 7 drives.

In Windows, I would just type in \\server\share.

Is there a really simple way of doing this in Ubuntu?

Thank you

---

### Post by collisionystm on 2012-01-01
> **erbad said:**
> I'm not sure how to map a network drive in Ubuntu.

In the past, I would just click on the places icon and all of my NTFS windows shares would show up.  However, now they are not, yet I can ping the IP addresses of the NTFS Windows 7 drives.

In Windows, I would just type in \\server\share.

Is there a really simple way of doing this in Ubuntu?

Thank you

simplest

open file manager

go to 

FILE, Connect to server

choose windows share, put in IP, connect

you can then bookmark it

---

### Post by erbad on 2012-01-02
> **collisionystm said:**
> simplest

open file manager

go to 

FILE, Connect to server

choose windows share, put in IP, connect

you can then bookmark it

That was easy, thank you!

---

### Post by zazuzimbo on 2012-01-16
That is really easy.

But I also couldn't figure it out alone.

Maybe this (commom case) should be given on Ubuntu Help, either as an example, or a general explanation of how Ubuntu does windows' [b]Map network drive[b].

What help says isn't very clear about this simple case:

> 
Windows share
Windows computers use a proprietary protocol to share files over a local area network. Computers on a Windows network are sometimes grouped into domains for organization and to better control access. If you have the right permissions on the remote computer, you can connect to a Windows share from the file manager.


---

### Post by wbtrans on 2012-07-05
> **collisionystm said:**
> simplest

open file manager

go to 

FILE, Connect to server

choose windows share, put in IP, connect

you can then bookmark it

Hi

I am also trying to map a network share this way, but I cannot find the command "File - Connect to Server" anywhere in my File Manager. 
I have tried everywhere, in the sidebar, on the right-click, etc. no such command to be found anywhere.
I am using the File Manager that is installed by default with LTS 12.04.
Regards
Walter

---

### Post by Morbius1 on 2012-07-05
Can you open it up from a terminal:
```
nautilus-connect-server
```

---

