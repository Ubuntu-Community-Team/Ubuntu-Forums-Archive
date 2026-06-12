---
title: "SSH Really slow"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by normthesamurai on 2010-03-08
Hi, I just updated from Ubuntu 9.04 to the latest release last night, and on starting up putty on my windows machine, I've noticed that it is running really slow.  When I work on the actual Ubuntu box there is no slowdown at all.  But, when I am using it through SSH via my windows machine, there is a 5-30 second delay between my typing in a command, and it being exectuted, or even the typed command appearing.  Since last night I have not made any other changes to my computers/network apart from upgrading Ubuntu.

So I was wondering if perhaps there is a package that wasn't properly updated or something that would be causing this massive slow down.

Edit:  After just writing that I thought I would try pinging my linux box from windows again.  Earlier it was fine but now it's usually timing out.  Ok it definately isn't an SSH problem, but a network problem(wireless)  restarted the router, restarted each computer disabled firewalls, still can't ping

Oh, and the linux box can ping the Windows and find the windows shares now and windows can access linux  samba shares... wait.  now it's working and SSH is more responsive... really confused atm

Update:  OK it seems to temporarily fix itself.  I can share files between the two fine but sometimes the connection hangs badly and a ping request from Windows will timeout or the SSH client will sloooooow down again

---

### Post by normthesamurai on 2010-03-08
Ok since I've edited my first post about a thousand times I'll just write this in a new reply:  SSH is still painfully slow.  Filesharing is working but very slow to navigate folders from Windows to Linux.  The actual speed of windows ->linux file sharing isn't any worse then it was previously it's just this SSH thing that is killing me.  (It took me about 20 seconds to navigate back to the beginning of a chmod command because I forgot to write sudo)

Using putty, when typing in username and password there is no lag.  I have already been to /etc/ssh/sshd_config and added useDNS no
Also: does putty have a debug mode like how you would go "ssh -v ..." on linux?  Because that might help me figure it out

---

### Post by normthesamurai on 2010-03-09
Any help would be appreciated.  Is there any information I can provide to help troubleshoot?

---

### Post by Darkpegasus333 on 2010-03-23
I'm having the same problem using PuTTY on Windows to connect to my Xubuntu machine at home. Connecting and logging on takes no time at all but typing while logged on is painfully slow. 

It may be the internet connection. I'll have to attempt it at home over LAN.

---

### Post by TimBurton on 2010-05-19
Having the same slow slow SSH connections here.  Client is OS X 10.6 with 9.10 server and intimitantly it slows to a crawl.

T

---

