---
title: "Can't ssh if not loged in locally"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by ashotar on 2012-08-24
Hello There,

I'm new in Ubuntu and in the forum as well(my first thread and my first post):P).
Hope I can find solution to my problem:

Here is the network topology and the problem description:

I have a routed at home and a Ubuntu 12.04 in the local network behind the routed. Have installed apache 2.2 on the server. I did static port forwardings on the routed device for Ubuntu`s 80 and 22 ports. All was working fine. I was able to connect both 80(GUI) and 22(SSH) ports from both local and remote networks.

A few days ago I was working on it(managing HTML files) and suddenly lost connection to the server. Tried both GUI and SSH with no luck.

Then called home and asked to reboot the PC(I thought I can access after reboot). But again with no luck.

Today I connected(remotely via teamviewer) to an other PC in my local network, tried to connect to the Ubuntu with SSH, GUI. Having no connection start ping(ping 192.168.x.x -t) to the server and asked my wife to log in to the system locally. Right after she loged into the system I had ping and was able to SSH the system.

In short: I can connect to the system(SSH/GUI) only if someone loged into the system.

Could someone please tell me what could be causing this and how can I isolate that problem?

I guess this might be network initialization problem(network doesn't start unless someone logs in locally) because I would have ping at least to the system.

Any advise would be greatly appreciated.

Thanks,
Ahsot.

---

### Post by ashotar on 2012-08-25
Folk,

Just found a solution to the problem. It is not the best but still OK.

I just turned firewall of on the Ubuntu and now can ping and ssh to the system without need to login locally first.

Solution is still not clear to me as I can't understand what has firewall to do with log in. I though it should be some network services not being run on the system until someone logs into the system. I had read some threads were they had to login and then ping, in order to be able to connect remotely. In my situation I didn't have to ping from the system after login to enable/allow ping/ssh to the system.

Anyway, any idea why that could be happen would be appreciated.

Thanks.

---

