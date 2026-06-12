---
title: "no network today. worked fine yesterday"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by MountainX on 2010-07-01
I'm running a new install of Kubuntu 10.04. I installed it a week ago. I'm using wired ethernet. Yesterday everything was working fine. I have not made any changes other than installing some updates yesterday. Today I have **no network interfaces listed in ifconfig** except lo.

But my network cards are listed in lspci. 

What are the troubleshooting steps? Thanks

---

### Post by Iowan on 2010-07-01
**ifconfig -a** will "display all interfaces which are currently available, even if down". 
**sudo lshw -C network** will probably provide much the same info that you got from **lspci**. You can also check if networking got disabled (I'm more familiar w/ Ubuntu... I presume Kubuntu has something similar...)

---

### Post by MountainX on 2010-07-01
Hey, thanks for your reply. The ubuntuforums.org were not updating for about 10 hours today for me. It was strange. I posted this and then it never appeared.

Anyway, I got the issue resolved. Here is the solution:

[http://www.linuxquestions.org/questions/linux-hardware-18/no-network-today-it-worked-fine-yesterday-817458/](http://www.linuxquestions.org/questions/linux-hardware-18/no-network-today-it-worked-fine-yesterday-817458/)

However, I still have some related questions. For example, why the heck did it happen in the first place?

It seems that hibernating my system removed my eth device from /etc/network/interfaces. And it never got restored. That's all I can figure...

---

### Post by Iowan on 2010-07-02
On Ubuntu, if Network Manager was handling the connection, then it wouldn't have been in */etc/network/interfaces*. The default file has only two lines defining "lo". 
But if it works... :)

---

### Post by MountainX on 2010-07-02
Thank you. Well, KNetworkManager will not open. So I still have a problem. I'd like to resolve this the correct way. Any ideas?

---

### Post by MountainX on 2010-07-02
> **Iowan said:**
> On Ubuntu, if Network Manager was handling the connection, then it wouldn't have been in */etc/network/interfaces*. The default file has only two lines defining "lo". 
But if it works... :)

I removed the lines I manually added to */etc/network/interfaces* and now I have no network connection again.

Can anyone tell me how to get Kubuntu to manage network connections the way it does by default. I just want to return to the "stock" settings. I've been googling for 2 days...

---

### Post by Arkold Thos on 2010-07-02
great :) now the only issue i have is the one with knetworkmanager

---

### Post by MountainX on 2010-07-02
Solved

It's a bug. See this link
[https://bugs.launchpad.net/ubuntu/+bug/555571](https://bugs.launchpad.net/ubuntu/+bug/555571)

This fixed my problem:
    service network-manager stop
    rm /var/lib/NetworkManager/NetworkManager.state
    service network-manager start

---

