---
title: "Trouble Connecting to Windows Shares"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by suicidepills on 2010-06-15
Hi everyone,

I know that there have been quite a few threads started about connecting to windows shares from Ubuntu.  I've looked at quite a few of them in many different forums but I haven't been able to make enough sense of them to fix my problem.  If someone could help or even just point me in the direction of a topic that I can research to understand what's happening, I would very much appreciate it.

So, here's what's happening:

I'm currently running Ubuntu 10.04 on a 8GB SanDisk Cruzer USB drive.  (I'm new to Linux and this is an easy, low-risk way to learn it.)  I used Live-Linux-USB Creator to install Ubuntu 10.04 with persistence of data.

I'm currently running into a problem while trying to connect to shares that exist on a Windows 7 machine on my home network.  When I attempt to access the share (through GNOME) through Place > Network > Windows Network, I get an error that says:

```
Unable to mount location
Failed to retrieve share list from server
```

We also have several Macs on our network, which Ubuntu is able to see without any issues.  They, as well as Windows machines are able to view the Windows 7 machine without any trouble.  All machines, even the Ubuntu machine, is able to ping the Windows 7 machine without any packet lossage.

I am happy to provide any information that may be helpful.

Thank you in advance for your help!

EDIT:

I am able to connect to the Windows 7 machine from the Ubuntu machine using:
```
smbclient //WINDOZE7/TESTSHARE
```
Here WINDOZE7 is the host name of the Windows 7 machine and TESTSHARE is the name of the share that I'm trying to access.  I'm still getting the error message when attempting to access the network through GNOME using Place > Network > Windows Network.

EDIT AGAIN:

I am able to connect to the Windows 7 share by opening Nautilus, pressing CTRL-L, and typing:
```
smb://WINDOZE7/TESTSHARE
```
This works after the computer "thinks" for a few moments.  However, I would still like to be able to browse the shares on my network using Places > Network > Windows Network.  More specifically, I would like to understand what is causing the problem so I can gain some more Linux knowledge :)

---

### Post by suicidepills on 2010-06-16
/bump

If there is any other helpful information that I can provide for troubleshooting, please let me know.  I'm happy to post it :)

---

### Post by suicidepills on 2010-06-18
Through some additional research and experimentation, it appears to me that this is a problem with Nautilus.  

After all, I am able to see and connect to the Windows shares using smbclient (and Nautilus, but I have to enter the path to the shares manually.)  I am also able to see shares on Macs in the "Windows Network".

Would I be correct in making the assumption that this is an issue with Nautilus and not with samba itself?  If so, is there a way for me to collect additional diagnostics information?

Thanks!

---

