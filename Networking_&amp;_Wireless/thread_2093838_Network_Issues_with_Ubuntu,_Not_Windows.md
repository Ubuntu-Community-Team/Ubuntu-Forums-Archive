---
title: "Network Issues with Ubuntu, Not Windows"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by greatermold on 2012-12-12
So here's a weird situation that I don't know where to begin how to debug using Ubuntu 10.04 LTS..

I have linux and windows loaded on two separate ssds.  Sometimes, I start loosing internet connectivity - only in linux.  There is no notification that says I lost network connection. Nor are there any errors or indicators at all.  When this happens, I can't login to my router's web page to reboot it. Sometimes rebooting solves the issues, but sometimes it doesn't.  I have a media server that mounts as a startup script, and this has issues too (along with SSH to any local machine on my network). Ill get frustrated so Ill just go to sleep or do something else for a few hours... then when I come back, it suddenly works. It'll work for a few days, then start to bug out on me again.

And here's the kicker, when I boot up to windows, everything works 100%.

Where do I begin trying to solve this issue, short of a fresh install (which also solves the issue ... for a few weeks...)

---

### Post by ahallubuntu on 2012-12-12
Can you please describe your network?

Exactly what is on it?  How many computers (clients)?  Static IP or DHCP/automatic?

Connected by a router?  Switch?  Both?

---

### Post by greatermold on 2012-12-12
> **ahallubuntu said:**
> Can you please describe your network?

Sure thing!

I've got 1 switch between the router and machine in question.  The IP addresses were not manually set, but have stayed the same since originally hooking in the devices.

There are total ~10 devices connected at all times + the occasional guest.  TV, media server, 2 computers, 3 laptops, 2 phones, 1 printer, & 2 xboxs are the permanent residents here.

However, unless it is a known issue with my Linux version, I don't think it's the network setup.. but I'm just judging this based on my windows OS working without an issue.

---

### Post by ahallubuntu on 2012-12-12
On one of the machines that is having the problem, as soon as it has become disconnected, in a terminal window type

```
dmesg
```

and see if anything related to eth0 or your network comes up.

---

### Post by vasilisc on 2012-12-12
try turning off IPv6 if you do not need
```
sudo nano /etc/default/grub
```
add ipv6.disable=1 into GRUB_CMDLINE_LINUX_DEFAULT
```
sudo update-grub
```
reboot.

---

### Post by Gan_HOPE326 on 2012-12-12
I have the same issue, with the difference that to me it happens so regularly and so quickly (basically in he first ten minutes that I am using internet), that I've stopped using it in Ubuntu altogether.

My release is 12.04, a rather fresh install, but I don't know much about my network as I'm in a shared house and no one's been able to give me the details until now - also, I basically never see anyone of the other people, so yeah. It's a basic wifi connection with some wifi router provided by the phone company and password protected, I guess. If you tell me how to run tests to find out more, I'll be happy to do it.

---

### Post by greatermold on 2012-12-12
output of dmesg when the issue is going on.

mold@desktop:~$ dmesg | grep -i eth0
[    2.046125] eth0: RTL8168b/8111b at 0xffffc90000c72000, bc:5f:f4:21:81:bc, XID 0c900800 IRQ 29
[    3.542083] r8169: eth0: link down
[    3.542092] r8169: eth0: link down
[    3.542459] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.135211] r8169: eth0: link up
[    5.135702] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.465327] eth0: no IPv6 routers present
[   33.051555] r8169: eth0: link up
[   78.919928] r8169: eth0: link up
[   82.458649] r8169: eth0: link up
[  135.468264] r8169: eth0: link up

---

### Post by SeijiSensei on 2012-12-12
A Google search for "r8169" brings up a number of posts about problems with the driver for that network adapter like [this one]("http://askubuntu.com/questions/111751/how-do-i-correctly-install-r8169-network-driver").  There is a lengthy bug report [here](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393).  There's some debate whether the problem is fixed in the most recent kernels, but it definitely exists on systems running Linux 2.6.x kernels, which I believe is true for 10.04.  Create a file like this:

```
sudo echo 'blacklist 8169' > /etc/modprobe.d/blacklist-r8169.conf
```

Reboot and see if that helps.

---

### Post by greatermold on 2012-12-13
neither updating grub to ignore IPv6 nor blacklisting the r8169 driver have worked.

Would upgrading to a newer version of Ubuntu work in this situation? Or is my only option to buy an ethernet controller that doesnt use this driver and use that instead?

Thanks again for all the help and suggestions so far!

---

