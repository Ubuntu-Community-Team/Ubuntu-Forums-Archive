---
title: "Disable IPv6 in Kubuntu"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by izizzle on 2009-04-27
How do you disable IPv6 in Kubuntu 9.04. My internet is feverishly slow and I'm hoping turning off ipv6 will solve the problem. There are tons of tutorials that tell you how to do it for ubuntu, but none for Kubuntu.

Thanks.

---

### Post by Crafty Kisses on 2009-04-27
It should be the same in Kubuntu I think. Do the following in the Konsole:
```
sudo gedit /etc/modprobe.d/aliases
```
Find the line that says the following:
```
alias net-pf-10 ipv6
```
Then change it to the following:
```
alias net-pf-10 off ipv6
```
Now run the following command:
```
update-modules
```
Then reboot, and IPv6 should be disabled. To make sure it's disabled you can also run the following:
```
ip a | grep inet6
```
That will tell you if IPv6 is currently running.

---

### Post by izizzle on 2009-04-27
Yeah, that doesn't work. There is no such file located at: /etc/modprobe.d/aliases

---

### Post by uniden9 on 2009-04-27
2 ways.

1: Manual way that's persistent on the current boot only.
$sudo echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

2: Add the kernel parameter to the sysctl.conf
$sysctl -a |grep net.ipv6.conf.all.disable_ipv6
This should be a zero, for enabled by default.

$sudo echo net.ipv6.conf.all.disable_ipv6 = 1 >> /etc/sysctl.conf
$sudo sysctl -p

Justin

---

### Post by izizzle on 2009-04-28
Hi. When I try to set ```
echo net.ipv6.conf.all.disable_ipv6 = 1
```  I get the following error in the terminal. ```
bash: /etc/sysctl.conf: Permission denied
```

---

### Post by uniden9 on 2009-04-28
You will need root permissions to update the /etc/sysctl.conf 

At any case, you manually edit the file with vi or whatever file editor you are comfortable with.  To just append the line:
net.ipv6.conf.all.disable_ipv6 = 1

and save it.

Justin

---

### Post by izizzle on 2009-04-29
Hi. I was able to get into root and follow the steps you posted, but when I run the command to check if ipv6 is enabled or disabled ```
ip a | grep inet6
``` I get the following:    ```
inet6 ::1/128 scope host
    inet6 fe80::20f:b5ff:fe5d:4b7b/64 scope link

```

I believe this means that IPV6 is still running. Can you confirem this? And yes, I did reboot.

Thanks.

---

### Post by CHaoSlayeR on 2009-04-30
The sysctl method didn't work for me.

@izizzle: yes that means that you're still running IPv6. Additionally you can check with **netstat -napA inet6** the specific processes that opened such sockets.

My question here would be:

Is there any way to force new sockets into a specific protocol family (inet|inet6)?


C]-[aoZ

---

### Post by CHaoSlayeR on 2009-04-30
Misunderstood something.

Actually this is a kernel bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351656](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/351656)

So we will need to wait until the next kernel update.


Additionally this bug prevents rollout in corporate environments so I hope it gets applied soon.

---

### Post by izizzle on 2009-04-30
So there is no way to disable IPv6, not even with the method that Unien9 suggested? By when do you think the kernel update will be released?

---

### Post by CHaoSlayeR on 2009-05-01
I don't know when it will be released, because it was already known as a bug since February 10th this year and with Kernel version 2.6.28-4:

[http://ubuntuforums.org/showthread.php?t=1065469](http://ubuntuforums.org/showthread.php?t=1065469)

Now it is nearly 3 Months later, 7 kernel updates have been released in the meantime and still not fixed. As the patch in the bug mentioned has been integrated into the kernel at March 5th it is only a matter of time when a responsible kernel maintainer in the ubuntu team takes a look at it.

C]-[aoZ

---

### Post by izizzle on 2009-05-01
Thanks Chaos.

It sounds like a work in progress.

---

### Post by cptrohn on 2009-12-18
> **Crafty Kisses said:**
> It should be the same in Kubuntu I think. Do the following in the Konsole:
```
sudo gedit /etc/modprobe.d/aliases
```
Find the line that says the following:
```
alias net-pf-10 ipv6
```
Then change it to the following:
```
alias net-pf-10 off ipv6
```
Now run the following command:
```
update-modules
```
Then reboot, and IPv6 should be disabled. To make sure it's disabled you can also run the following:
```
ip a | grep inet6
```
That will tell you if IPv6 is currently running.


This will work but in the first line of code Kubuntu users need to use the commands ```
kdesudo kate
``` instead of ```
sudo gedit
```

---

