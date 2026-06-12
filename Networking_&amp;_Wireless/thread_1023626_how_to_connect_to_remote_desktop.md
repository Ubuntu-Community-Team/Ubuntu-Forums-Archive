---
title: "how to connect to remote desktop ?"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by kaiwan on 2008-12-28
Hi! 

I have ubuntu 8.10, and my borther also.
I would like to take control over his computer to administrate and held him sometimes, over internet connection. But I dont know how to do it? Using terminal server client or what?

---

### Post by jesuspresley on 2008-12-28
Install "remote desktop" on your brothers pc and "remote desktop viewer" on yours [it's based on VNC]. Best is to install both tools on both pcs.
As long as you are connected to the same LAN, you'll be able to access the remote pc.

I don't know if there is an add-on or something to view it via internet.
I used an app called teamviewer on WinXP before, but is there something for Linux like this?

If not, you might check if you can access your brothers pc by a fixed IP adress. However, usually ISPs provide you with a dynamic IP adress which changes everytime you connect to internet.

I am curious myself. Any suggestions?
Setting up a VPN connection is a solution, but too complicated IMHO.

---

### Post by kaiwan on 2008-12-28
Well, cant use LAN cause he lives in other town. 
IPs are dynamic...

---

### Post by namdung on 2008-12-28
ssh would be a better option.-
Install openssh-server in ur friend's PC from Synaptic Package Server, the client is installed by default.

In the terminal

```
ssh -X username@friends_ip

```

Do write if u want more info.

---

### Post by kaiwan on 2008-12-28
> **namdung said:**
> ssh would be a better option.-
Install openssh-server from Synaptic Package Server, the client is installed by default.

In the terminal

```
ssh -X username@friends_ip

```

Do write if u want more info.

Will try it out. 

Is there i quick way to find out external IP, domain and client hostname ?

---

### Post by jesuspresley on 2008-12-28
Well, SSH is only for terminal control, no GUI. But it's a solution to operate the most important task.

I think a combo of Hamchi & VNC would be the best thing for you. Tutorial here:
[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)

[LIST]
[*]By Hamachi you can create a LAN via internet
[*]With VNC, you can access all the clients in this LAN.
[/LIST]

---

### Post by kaiwan on 2008-12-28
> **jesuspresley said:**
> Well, SSH is only for terminal control, no GUI. But it's a solution to operate the most important task.

I think a combo of Hamchi & VNC would be the best thing for you. Tutorial here:
[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)

[LIST]
[*]By Hamachi you can create a LAN via internet
[*]With VNC, you can access all the clients in this LAN.
[/LIST]

nice :)

thanks

---

### Post by namdung on 2008-12-28
> **jesuspresley said:**
> Well, SSH is only for terminal control, no GUI. 

Sorry to wrong u here but ssh can be used with GUI, but depends on if GUI is installed in the server machine. Use the **-X** option

```
ssh -X username@ipaddress
```

---

### Post by jesuspresley on 2008-12-28
@namdung
I did not know! Sounds good. So is SSH then working in the gnome environment?

@kaiwan
You're welcome. Maybe the tutorial is a little bit outdated (2006). There might be a newer one out there.

---

### Post by vallhalla81 on 2008-12-28
well i would sugest learning to use ssh in the terminal once you have it down you can then ssh from your mobile to your pc and that can be usefull also it works that little bit faster ;)

---

