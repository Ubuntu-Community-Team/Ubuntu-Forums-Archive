---
title: "Installed wicd, can't browse LAN"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by Derspankster on 2009-05-03
I recently installed wicd because I was having no luck enabling a static IP address.  Wicd solved that problem but I've created another.  I can no longer browse my LAN. When I click on Network Servers I find my network and my workgroup fine but when I tried to browse the workgroup shared folders I get the error "Failed to retrieve share list from server"

I can connect to shares from Places>Connect to Server however. Tried rebooting my server, my client and my router. None worked. 

smbtree returns this:

timeout connecting to 208.69.32.132:445
timeout connecting to 208.69.32.132:139
cli_start_connection: failed to connect to CHAOS<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED

---

### Post by Derspankster on 2009-06-08
OK, finally I have a fix.  I simple had to add the address and server name to my hosts file.  etc/hosts

192.168.X.XXX  (My Server Name)

That did the trick. 

Thanks to nobody since no one ever replied.  Perhaps this post can help others.

---

### Post by zehnmonkey on 2010-01-24
Yes, thanks to your post. . . an hour of troubleshooting lead to successful resolution.  

The question is why?  Why should we have to add the device's IP manually to hosts file?  What the hell is the point of the DNS server's IP in the wireless config and samba configuration?   I believe I also had wicd on the suggestion of another thread.  

Thanks for posting though, helped a ton!

---

### Post by Gotit on 2010-06-10
Thank you Derspankster!!

I've been fighting this for 2.5 days now.

Thank you 
Thank you 
Thank you

I definitely agree with zehnmonkey, **WHY**?!
-------------------

**Update:**
I went to launchpad to file a bug report and discovered this item: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/356022](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/356022)
The last entry cites this as a Comcast caused issue (which is my ISP) and using Google's DNS resolves the issue.  I backed out the etc/hosts change and changed Network Manager to use Google's DNS (8.8.8.8, 8.8.4.4) but that didn't help.  However, when I change my router to use Google's DNS I was able to browse my local network!

BUT, that doesn't answer the question of why my JJ 9.04 machine doesn't experience this problem while both of my LL 10.04 machines do!

---

