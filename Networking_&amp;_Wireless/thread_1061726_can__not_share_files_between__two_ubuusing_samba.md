---
title: "can  not share files between  two ubuusing samba"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by legolas_w on 2009-02-06
Hi
Thank you for reading my post
I have two computer (a desktop and a laptop) which have ubuntu 8.10
I can share files with other colleague in work place using my laptop which has file sharing service installed.

I installed samba file sharing service in my desktop computer and I can right click on folders and from properties window I can share the folder and even its icon changes.

in my desktop computer:
When I open Network:/// it shows Windows Network icon inside it but when I double click on theat icon it shows an error like: 

Unable to mount location
failed to retrieve share list from server


in my laptop:

When I open Network:/// it shows Windows Network icon inside it but when I double click on that icon it shows none of the shared files which I shared in my desktop. indeed it opens an empty window.

please let me know what is wrong here.

thanks.

---

### Post by renzokuken on 2009-02-06
i believe that when sharing from ubuntu <-> ubuntu, you should use **NFS** instead of samba. samba is for windows <-> linux networking.

have a look here [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by Another Monkey on 2009-02-06
It's true that using Samba for *nix <-> *nix sharing is overkill, but it should still work.  And sticking with Samba means only having to set up one protocol (and it's also handy if you sometimes have Windows machines attached).

The NFS post is excellent if that is the route you want to follow.  If you want to stay with Samba, you need to check a few basic things.

Are the laptop and desktop on the same subnet?

Can they ping each other?

Have you set up a Samba user on the desktop and associated it with an OS user on that desktop?  (There is a samba-config tool in the repository which makes this very easy).

What happens if you try going direct via IP?  e.g. smb://192.168.0.1/ (you need to use the correct IP address, obviously)

If you have used a GUI to edit your firewall (e.g. iptables), have you made sure that SMB over TCP is being allowed?  You may also need to explicitly allow NetBIOS (depends on how you set your firewall up).

The Samba documentation is pretty clear, might be worth just checking in case something simple is missed.

You could also compare your desktop Samba config file to your laptop Samba config file and see if anything looks wrong.

---

### Post by superprash2003 on 2009-02-06
try accessing shared folders via nautilus .. [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by legolas_w on 2009-02-06
Hi, Thank you for reply.

> **Another Monkey said:**
> 
Are the laptop and desktop on the same subnet?
Yes both are in the same subnet, I use my wireless router to connect them together.

> **Another Monkey said:**
> 
Can they ping each other?
Yes, I can ping laptop from desktop and vice-versa. I can connect to my desktop by using vnc viewer.

> **Another Monkey said:**
> 
Have you set up a Samba user on the desktop and associated it with an OS user on that desktop?  (There is a samba-config tool in the repository which makes this very easy).

> **Another Monkey said:**
> 
What happens if you try going direct via IP?  e.g. smb://192.168.0.1/ (you need to use the correct IP address, obviously)

It shows nothing, nothing appears in the screen.

> **Another Monkey said:**
> 
If you have used a GUI to edit your firewall (e.g. iptables), have you made sure that SMB over TCP is being allowed?  You may also need to explicitly allow NetBIOS (depends on how you set your firewall up).


I never changed the Firewall stuff in my computer. but now i tried Gufw and it shows that firewall is disabled


I think something is wrong with my desktop because in laptop, when I double click on network it shows some icons including icon of my laptop itself and when i click on laptop icon I can see all of my laptop shared folders.

but in my desktop computer, I can not open the Places>Network because it returns an error like:
```

Unable to mount location
failed to retrieve share list from server


```

---

### Post by legolas_w on 2009-02-06
Thank you all,

The problem solved :-P, it looks like that after I changed the router my desktop computer IP address has been changed and the Samba server was trying to use the old ip address. I changed the ip address and it is ok now.

---

### Post by prasopsuk on 2009-02-19
i got this problem after daily update. cups got error with computer name. I had solved by change computer name to IP address.Ok cups is working.
thank so all.

---

