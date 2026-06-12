---
title: "Remote login to diskless, headless node"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by mo0nykit on 2009-09-02
[LEFT]Hi everyone!

This is the first time I'm posting here :)
I'd like to begin with my question:
**What package do I need so I could remotely login over LAN to a diskless, headless node?**

I'm learning to build a Beowulf cluster. For now, everything is still a virtual machine setup using VirtualBox on a Windows XP host. This is the guide I followed: 
**[Setting Up A Diskless-boot Kerrighed 2.3.0 Cluster in Ubuntu 8.04]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")**
Note that I'm **NOT** doing a Kerrighed boot yet, just a **debootstrap** base system install.

Here's the setup I have:
1 Server VM
1 Client VM (boots from the Server VM over the virtual internal network)

The Client VM is literally not headless yet, since it's still a virtual machine. This is what I would like to do:
1. While physically sitting at the Server, I'd like to remotely "sit" at the Client's "keyboard", and also see what is displayed at the Client's terminal console.
2. Something like the Remote Desktop or x11vnc. The only difference is that the Client doesn't have X11 or any GUI. I don't want it have a GUI either.

Any tips?

Thanks in advance for your help!
[/LEFT]

---

### Post by mo0nykit on 2009-09-05
This thread has been rather quiet :(
Everytime I google **ssh**, the results that easily come up are those about **ssh** and **X11**.
Anyway, I found a solution. I'll use **ssh**.

I'll have to edit the */etc/hosts* file so that I could use host names when **ssh**-ing. It should include an entry like this:
```
192.168.100.100   node_01
```Then I can login to the remote host using this command:
```
ssh <username>@<remote_host>
```

---

