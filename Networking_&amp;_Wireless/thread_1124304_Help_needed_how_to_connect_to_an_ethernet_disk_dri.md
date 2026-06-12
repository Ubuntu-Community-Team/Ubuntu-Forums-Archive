---
title: "Help needed: how to connect to an ethernet disk drive?"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Alexandre76 on 2009-04-13
Hello Everyone,

When I had Windows, I could connect without any problems to an ethernet drive (MyBook of 500GB by Western Digital), by entering \\disk_name into the Start > Run > Open: box.

I have switched to Ubuntu 8.10  and I would like to access it, but I don't know how to proceed, as the only thing I know is the mac address of the drive's adapter. It won't recognize the name of the drive...

I have searched the forum, but couldn't find anything relevant to my situation. The drive I am using does not have USB.

Many thanks in advance for your help.

Alexandre

---

### Post by skintythe1andonly on 2009-04-13
I do not know a whole lot but first of all you need to establish what sort of protocol it is using. I have a network storage drive that uses samba, it is not a mybook though. Try typing the following

```
findsmb
```

that should find anything on your network that uses samba. Generally it is its local ip address that you need

---

### Post by Alexandre76 on 2009-04-13
> **skintythe1andonly said:**
> ...

It looks like my drive is not detected...

Ny computer has 2 network cards: 1 connected to the xDSL router, qnd the other one connected to the network drive.

```
user@userubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.10    USERUBUNTU    +[WORKGROUP] [Unix] [Samba 3.2.3]

```

---

### Post by skintythe1andonly on 2009-04-14
I am not too familiar with this, but just set mine up with mac, and 2 ubuntu machines, and a netbook. Does your router have extra ports? Most come with about 4. Try plugging it into that. This would assign a local IP address to it, so anything on your network should access it.

just to be safe make sure samba is installed correctly

```
sudo apt-get install samba
```

now run

```
findsmb
```


According to some other posts samba is used for WD
[http://ubuntuforums.org/showthread.php?t=708254]("http://ubuntuforums.org/showthread.php?t=708254")
[http://ubuntuforums.org/archive/index.php/t-672810.html]("http://ubuntuforums.org/archive/index.php/t-672810.html")

Should everything work then you should be able to connect to server under nautilus->windows share and then you can use the ip address and your share details.

if this doesnt work then the workgroup in the default samba config file is prob not the same as the storage device. If this worked on your xp machine, the workgroup will be the same as this machine. Should you need to adjust this, have a look at

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

I have never touched anything that had more than one ethernet port. If there is an easier way, point it out.

---

