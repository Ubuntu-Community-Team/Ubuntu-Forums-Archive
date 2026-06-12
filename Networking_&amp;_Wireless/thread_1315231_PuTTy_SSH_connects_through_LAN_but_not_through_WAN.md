---
title: "PuTTy SSH connects through LAN but not through WAN"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by wiggie on 2009-11-05
Hey all,

I can log into the server with putty when I am using the LAN IP address, and that works just fine. But when I use the WAN IP adress, it asks me for the user name, which I provide, and the password, which I also provide, and I am 100% sure both are correct (since they obviously worked through the local access). Furthermore I have tried it at least 15 times, this way eliminating typos, keyboard layout issues and what have you.

I was searching all day yesterday for a solution but I have found none.

I have tried changing the ```
/etc/ssh/sshd_config
``` file in order to allow PasswordAuthentication, restarted ssh with ```
sudo /etc/init.d/ssh restart
``` and got nowhere.

I have looked at /etc/hosts.deny and /etc/hosts.allow and there are no entries in those files, other then the ones which are commented out.

Additionally, I took a peak at /var/log/messages and didn't see anything that would give me a hint.

Anybody have an Idea?

---

### Post by sanderj on 2009-11-05
If you don't see the failed logons from the WAN interface in /var/log/messages (and, as a check, you **do **see failed logons from the LAN interface), it's my guess that you're not connecting to the machine you think you're connecting to.

Explanation: based on "WAN interface", I think there's a modem/router/NAT-device involved between your computer and Internet. Correct? If so, can it be your ssh-ing to another device, for example the NAT-device itself, possibly because of an incorrect port forwarding?


If my assumption is not correct, please post 1) a drawing of your network and 2) the ifconfig of your machine.

---

### Post by wiggie on 2009-11-05
You might just be right about not accessing the right device.

The funny thing is, when I log in locally there is a short delay after inputting the user name before it asks me for the password. When I try to log in from the outside, this delay is not present, which makes me wonder if it connects to the right machine at all.

The network diagram is attached. Internet is accessed through the first router. The second router is attached to the first and is set to be in the DMZ. Ports are forwarded in both routers (ssh and VNC ports). I have managed to connect to the server with VNC but without an ssh tunnel, and I don't like that.

I assume the ssh connection is made to the second router, which of course won't do.

Here's the ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:67:6c:12
          inet addr:192.168.3.11  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe67:6c12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:876239 (876.2 KB)  TX bytes:23435 (23.4 KB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:0f:1f:67:6c:13
          inet addr:192.168.3.10  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe67:6c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60707 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7766854 (7.7 MB)  TX bytes:50298515 (50.2 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7699 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4191872 (4.1 MB)  TX bytes:4191872 (4.1 MB)

```

---

### Post by Lars Noodén on 2009-11-05
One of the ways you can see what you are connecting to would be to check the keys.  If the keys are different, then you are probably connecting to different machines.

```

# get the key from the LAN address
ssh-keyscan -t rsa 192.168.x.x >  /tmp/key*

# get the key from the WAN address
ssh-keyscan -t rsa x.y.z.a >> /tmp/key 

# show the key fingerprints
ssh-keygen -lf /tmp/key

```

---

### Post by sanderj on 2009-11-05
Aha, as expected: one or even two NAT-devices, and a DMZ ...

Anyway: as your VNC-connection to the server is successful, you know how to route & forward ports. Good.
If you have done that for SSH too, but it doesn't work, re-check the settings. 
It could very well be that the SSH port is already taken by another device (the router itself?). If so, choose another, unused port (like 22444) and forward that through your NAT-device(s).

---

### Post by wiggie on 2009-11-05
sanderj you were right

the problem was with my 2nd router, the MikroTik, which is a great thing, but very complicated.

It was not forwarding the port properly, because it wasn't set up properly. When I sshd into it, I was stopped there. So i used my user name and password for the router and I successfully established an ssh connection to the router.

I finally figured it out, but there is no point in posting the solution here, since not many people use MikroTik. If you do, then ask and I'll tell you.

Thanks for the replies.

Cheers.

---

