---
title: "Can't connect to X11VNC Server from Windows 7 using NetBios name!"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by elzafir on 2011-03-30
Guys, I have a problem.

I installed Xubuntu 10.10 on my server. I already ran *apt-get update* and *apt-get upgrade*, so Xubuntu is in latest updated state.

Then I installed X11VNCServer and ran the program.

**I DON'T wanna connect with a password**, so I didn't fiddle with settings. After I ran x11vnc on terminal, it shows 

```
The VNC desktop is:  Habsjah-Server:0
PORT=5900
```

I also installed Firestarter and opened ports using its built in settings for VNC. Aside from that I opened ports for Samba, SSH, BitTorrent, and NFS. But it's not relevant.

Okay, so I tried connecting to the VNC server using my Windows 7 box with UltraVNC. 
**And it connects _succesfully_ when I entered _'192.168.2.110:5900'_**.
**But it _CANNOT _connect when I use _'Habsjah-Server:0'_!!!**:(

I tried googling for solution to no avail.

***The weird thing is, in my previous Xubuntu 10.10 in the same machine, same IP address, same router config and same Windows 7 config, connecting to VNC using the NetBios name WORKS! ***It was perfect, until I switched from Firestarter to Guarddog and it messed up my system, so I had to do a clean install. But now, it won't work! :confused:

I don't know what/where to adjust settings. I suspect it has something to do with WINS or DNS, but its power level is to mighty for my network-fu.

I also had my eyes on /etc/hosts file but I just don't know what to do with it. My **etc/hosts** is as follows:

```
192.168.2.110	Habsjah-Server 	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost Habsjah-Server
::1	Habsjah-Server	localhost6.localdomain6	localhost6
127.0.1.1	Habsjah-Server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


Could you guys give me a solution or direct me to the right direction in solving my problem? Thanks very much. :)

Sorry for the bad english.
And sorry for the excessive use rich text formatting, I **had** to. :p

---

### Post by krunge on 2011-03-30
When x11vnc prints out "The VNC desktop is:  Habsjah-Server:0" it basically gets "Habsjah-Server" from the same place the hostname(1) command does (e.g. when you type "hostname" in a shell.)  That string may or may not be a valid network host name that can be resolved on your LAN to the correct IP.

If you don't have DNS name lookup (or something else?) working on your LAN for the string "Habsjah-Server" then it won't work and you'll need to use the IP number (or if some other host name maps to 192.168.2.110 use that.)

So this is a name lookup problem (DNS, or maybe something else windows uses) for your windows (vnc client) side. I suspect the error message says something like it cannot resolve "Habsjah-Server".

How DNS works between Windows and Linux machines these days I have no idea.  Maybe host name stuff is done automatically and broadcast over the LAN? Maybe this is what samba does for you?  I'm not sure...

---

### Post by elzafir on 2011-03-30
> **krunge said:**
> When x11vnc prints out "The VNC desktop is:  Habsjah-Server:0" it basically gets "Habsjah-Server" from the same place the hostname(1) command does (e.g. when you type "hostname" in a shell.)  That string may or may not be a valid network host name that can be resolved on your LAN to the correct IP.

If you don't have DNS name lookup (or something else?) working on your LAN for the string "Habsjah-Server" then it won't work and you'll need to use the IP number (or if some other host name maps to 192.168.2.110 use that.)

So this is a name lookup problem (DNS, or maybe something else windows uses) for your windows (vnc client) side. I suspect the error message says something like it cannot resolve "Habsjah-Server".

How DNS works between Windows and Linux machines these days I have no idea.  Maybe host name stuff is done automatically and broadcast over the LAN? Maybe this is what samba does for you?  I'm not sure...

Thanks for your reply.
Based on your assessment, which I find very logical, the problem is narrowed down to a 'name lookup problem'. I agree that this is a DNS related problem. 

Under Windows 7's 'Network', it does shows the Xubuntu box, but when I tried to open it, the error message does says to that effect, more precisely:
```
"Windows cannot access \\HABSJAH-SERVER. Check the spelling of the name. Otherwise, there might be a problem with your network. To try to identify and resolve network problems, click Diagnose."
```

And under "See details: 
```
"Error code 0x80070035. The network path was not found."
```

After clicking diagnose:
```
"Make sure the computer or device is turned on and connected to the network. Blah blah blah classic Windows unhelpful error message blah blah."
```

This is very weird, I am 100% sure that the problem is not with my Windows 7 box, since it was work perfectly with the Xubuntu 10.10 previous install. I have Samba installed and it also cannot be accessed using the Netbios name (hence the error message from 'Network' above; but Samba share is working I open it with IP address, so it must be a general, not Samba or VNC specific problem.).

**So, my question, how do I manage/fix a DNS name lookup problem? **The only probable solution I found in this forum is to use WINS which **works!**, but using WINS is not ideal, since it WAS working without WINS....and I have 5-6 clients in my home and I would like NOT to fiddle with TCP/IP WINS settings under Windows on every clients.

I must have missing something very simple. *Is it possible that etc/hosts corresponds to this problem?*.

Help...

---

### Post by elzafir on 2011-04-01
bump..

---

