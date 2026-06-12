---
title: "Internet speed issue after crash"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by kazhkaz on 2012-05-17
Hello,
This is the first ubuntu problem that I couldn't find the answer to.

I am using the newest Ubuntu Server 12.04 with GUI installed. 
I have 100 Mb/s internet connection and the server is behind a router.
I am using NoMachine NX Server to access Ubuntu server remotely because the server is in a basement.

**The problem:**
The connection speed when using SSH/NX Client/Teamviewer is terribly slow and almost impossible to use. Although when using *wget* command I get normal speed (~7.8 MB/s)

**What has happened before the problem:**
I have installed all updates that ubuntu has suggested. After installation Ubuntu asked to restart the system but I didn't do that.
At the same moment I was trying to run Windows Server 2008 R2 on VirtualBox and to set up RDP connection. I was trying various network connection options on VirtualBox. Suddenly the connection was lost.

Later I got a call from my Dad and he said that the internet connection was lost for a whole network. He went to basement and tried to power off and power on the router but it didn't help. Then he tried to pull out the internet cable from the server and the Internet connection started to work again. When he put back the internet cable to Ubuntu server the connection was down again. The server itself has crashed and any key combinations couldn't wake it up. I asked him to reset the server. After restart the Internet connection was fine again except when trying to connect using remote clients. Even simple SSH connection using putty is very slow.

In my opinion the cause of the problem is Virtualbox or some update that was installed.

Any help would be appreciated.

---

### Post by kazhkaz on 2012-05-18
bump,...

---

### Post by kazhkaz on 2012-05-29
I have found the solution if anyone will run into the same problem.
I have changed my network cards mode to 100/Full duplex (previously it was 1000/Full duplex) and speeds are normal again.

```
 ethtool -s eth1 speed 100 duplex full
```

Although the problem is solved I am still interested in the cause of this problem.
Maybe it's a router's problem that appeared after the crash? Please share your ideas

---

