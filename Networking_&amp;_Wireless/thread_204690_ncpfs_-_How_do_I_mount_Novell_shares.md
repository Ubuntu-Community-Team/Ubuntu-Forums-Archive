---
title: "ncpfs - How do I mount Novell shares?"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2006-06-27
each time I try slist, I get "Server not found (0x8847)".

In the past, I was told to use ncplogin, but I I still get the same message.

ncplogin, ncpmount, and slist all return the 8847 error code.

I was able to do this quite a while back a few times, but that was with Warty.  Now that I'm on Dapper, and am using it at work, I'd really like to simply mount novell drives instead of using VMWare to access the network.

Any ideas how to mount Novell shares?

(oh, and I can ping the servers just fine)

---

### Post by f00buntu on 2006-06-28
Hello,

Make sure you use the -S (server name) option AND the -A (dns name) option like this:

ncpmount -S yourservername -A yourservernamefqdn  -U novellusername -V volumename -u linuxusername /mnt/yourmountpoint/

Works for me!

---

### Post by OneSeventeen on 2006-06-28
Thanks!  That made a HUGE difference!

My next error message was:
ncpmount: No such entry (-601) in nds login
Login denied.

I then decided to try to type in my **full context** which works beautifully!```
sudo ncpmount -S SERVER -A server.ourdomain.com -U username.context.path -V VolumeToMount -u linuxusername /path/to/mount/volume/
```

It works beautifully!

Now, is there a way to write a shell script that will ask me for my password, then execute this and another mount command?  (I don't want to have an unencrypted copy of my novell password anywhere.)  It would be even better if I could make a GUI, so it just pops up, asks me for my password, then attempts to mount the drives.  (I don't even care about error tracking, since I can just see if the data is there, and if so, it obviously worked!)

**EDIT:** I just copied my commands into a shell script file, made a launcher for it and told it to launch in a terminal.. problem solved.  I did the same thing for an ncpumount script.  I still have to type in my admin password and Novell password in the command line, but that's all I have to type in, and the terminal goes away once it has worked.  Yay!

Thanks again, that made a huge difference.  When I first tried using -S and -A (as another post mentioned), it said -A was unrecognized, but now that you told me what -A actually is (the help file doesn't, nor do any of the other posts I have found about this) it makes perfect sense!

---

### Post by rdeaver on 2006-07-17
There is the Novel Client (note only 1 L)

[http://novelclient.sourceforge.net/](http://novelclient.sourceforge.net/)

It is a gui frontend for ncpfs.

---

### Post by nonsparker on 2006-10-27
is there any way to get the web server to access this mounted dir?

---

### Post by mezcla on 2007-10-15
I have a similar situation and when I attempt to mount the drive nothing happens.  I followed this tutorial:

[http://useopensource.blogspot.com/2007/01/how-to-mount-novell-network-drives.html](http://useopensource.blogspot.com/2007/01/how-to-mount-novell-network-drives.html)

I may not have the server name right.  If I am logging in to Windows I can find the "Tree" and the "Context" as well as the "Server" (what looks like an IP address).  Where does each of those go in the following code? (Specifically the "Tree" and the "Context").

```
sudo ncpmount -S SERVER -A server.ourdomain.com -U username.context.path -V VolumeToMount -u linuxusername /path/to/mount/volume/
```

---

