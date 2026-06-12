---
title: "Forward SMB from remote server to laptop behind router/NAT"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by mcg1sean on 2009-12-20
So back at my college, Ive got an Ubuntu machine running a Samba server. While at school, I can access it without any problems. It has its own dedicated hostname and IP address, making things somewhat easier. Currently Im at home on my laptop (macbook pro running OS 10.6) which is behind a linksys WRT54G running the DD-WRT firmware. 

I think the problem that I am having is with getting the ports to forward correctly. I can successfully SSH from my laptop to my remote machine, and then ssh from the remote machine back to my laptop, so I know that port 22 is open. To make things easier, Ive DMZd my computer just so that everything is open and it still is not working. Ive tried to forward SMB over an SSH tunnel by running 

```
sudo ssh -L 139:remote-server-ip:139 username@remote-server
```

but still no luck. But I do get an error:

bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 139
Could not request local forwarding.

An idea what I should do next?

---

### Post by hugmenot on 2009-12-20
Just use SCP/SFTP?

---

### Post by mcg1sean on 2009-12-22
I know that I can use SCP/SFTP but I want to be able to just have that samba share mounted on my computer for easy access.

---

### Post by Captainnow on 2011-01-06
I am also having issues with this.
I have all the port forwarding enabled.
I can access my server as a shared drive behind my router. 
But I can't get it to work from computers outside of my router. 
FTP and SSH works from my home and when I'm not at home.

I believe Samba should allow you to map a network drive whether you are at home (behind the router) or somewhere else coming in through the router as long as the ports are open and forward to the correct internal IP address.

When I try to do it from windows machine it will prompt for a username and password for my server but it never connects to map the drive. It just prompts for the username and password like I typed the log on information incorrectly. I have tried several times.

I sure would like more information on getting this to work.

---

### Post by hugmenot on 2011-01-06
Sorry, trying to do this is stoopid.

Nautilus has transparent SSH/SCP network folders. You gain nothing by forcing SMB through SSH tunnel. To the user it’s the same anyway. Straight SCP is probably even more performant.

---

### Post by Captainnow on 2011-01-06
How is having a map network drive in windows stupid?

I'm trying to do it for my mom who doesn't have a ton of hard drive space on her windows 7 laptop. I have plenty of space on my linux server. She would never remember how to FTP something over. 

If it was set just as a network drive in windows she wouldn't have to learn anything new to use it.

---

