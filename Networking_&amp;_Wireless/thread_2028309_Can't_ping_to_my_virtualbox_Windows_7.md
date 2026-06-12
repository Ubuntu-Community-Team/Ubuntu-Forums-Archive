---
title: "Can't ping to my virtualbox Windows 7"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by fishsticks1907 on 2012-07-17
I'm using Ubuntu 12.04, The Windows 7 virtual machine is using the "Bridged Adapter" network setting. I can ping from the virtual machine to my physical machine. But, i can't ping Ubuntu to the virtual machine. Any help would be great.

---

### Post by OM55 on 2012-07-18
Depending on the version of Windows you used in your VirtualBox, in order to be able to get a reply to your pings you probably need to create at least one folder share on the Windows machine. In Windows XP for example, once you have at least one share set up, the machine will respond to pings. But if no shares are set, no pings will be returned.

---

### Post by fishsticks1907 on 2012-07-18
> **OM55 said:**
> Depending on the version of Windows you used in your VirtualBox, in order to be able to get a reply to your pings you probably need to create at least one folder share on the Windows machine. In Windows XP for example, once you have at least one share set up, the machine will respond to pings. But if no shares are set, no pings will be returned. 

i dual boot with ubuntu and windows 7. i tested if it happens with windows 7 as the host and ubuntu as the virtual machine, and they can ping each other just fine. But, when i go back into ubuntu as the host and windows 7 as the virtual machine, windows 7 can ping to ubuntu, but ubuntu cant ping the virtual machine(windows 7).

---

### Post by rukiaEnix on 2012-07-18
Turn off the windows firewall of your virtual 7 machine.

I have seen this happen with windows 7 that doesn't allow ping when they have the firewall on.

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> Turn off the windows firewall of your virtual 7 machine.

I have seen this happen with windows 7 that doesn't allow ping when they have the firewall on.

No, i still cant ping the windows 7 virtual machine.

---

### Post by rukiaEnix on 2012-07-18
Can you please post your windows 7 virtual machine IP and your Ubuntu host IP? Better if you post the result of ipconfig and ifconfig

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> Can you please post your windows 7 virtual machine IP and your Ubuntu host IP? Better if you post the result of ipconfig and ifconfig

They have the same subnet and dns:

ubuntu:
ipv4 : 192.168.1.42
netmask : 255.255.255.0
dns : 192.168.1.1

windows 7(virtual machine):
ipv4 : 192.168.1.45
subnet : 255.255.255.0
gateway : 192.168.1.1

i don't get it, because it works fine if i boot from windows 7 and use Ubuntu as the virtual machine.

---

### Post by rukiaEnix on 2012-07-18
Can you please post the screenshot of your virtualbox network configuration for the 7 virtual machine?

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> Can you please post the screenshot of your virtualbox network configuration for the 7 virtual machine?.

---

### Post by rukiaEnix on 2012-07-18
Can't see the image

---

### Post by rukiaEnix on 2012-07-18
Upload it to an image hosting site and add the url to the post.

---

### Post by fishsticks1907 on 2012-07-18
Okay here it is.

[http://imageshack.us/photo/my-images/337/screenshotfrom201207181.png/](http://imageshack.us/photo/my-images/337/screenshotfrom201207181.png/)

---

### Post by rukiaEnix on 2012-07-18
OK, in my virtualbox configuration I have disabled the promiscuous mode denied.

But what I see is that your adapter type is disabled and also the MAC address. I don't know if you have permission problems.

First change the promiscuous mode to denied. Or maybe you have already try this. Please tell me if you already have tried it.

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> OK, in my virtualbox configuration I have disabled the promiscuous mode denied.

But what I see is that your adapter type is disabled and also the MAC address. I don't know if you have permission problems.

First change the promiscuous mode to denied. Or maybe you have already try this. Please tell me if you already have tried it.

changed promiscuous mode to denied, still cant ping the vm.

---

### Post by rukiaEnix on 2012-07-18
Do you have your user added to the vboxusers group?

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> Do you have your user added to the vboxusers group?

No, i don't even know what that is.

---

### Post by rukiaEnix on 2012-07-18
OK, please post the result of this command:

```

cat /etc/group |grep vboxusers

```

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> OK, please post the result of this command:

```

cat /etc/group |grep vboxusers

```

the output was  vboxusers: x :125:

---

### Post by rukiaEnix on 2012-07-18
OK.

Execute this command as root or with sudo:

```

usermod -a -G vboxusers user

```Replacing user with your current user (which I suppose is the one you use to execute Virtualbox).

Before doing all of this close your virtualbox. When you have added your user to the vboxusers group logout and login again to Ubuntu.

---

### Post by fishsticks1907 on 2012-07-18
i just tried pinging my ubuntu computer with my old windows xp computer(not virtual machine), i can ping to it, but i cant ping to the xp machine. i think it has something to do with the ubuntu network settings or firewall.

---

### Post by rukiaEnix on 2012-07-18
Can you please post the result of this command? Run it as root or with sudo:

```

iptables -L

```

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> Can you please post the result of this command? Run it as root or with sudo:

```

iptables -L

```

FATAL: Error inserting ip_tables (/lib/modules/3.2.0-26-generic/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.4.12: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

---

### Post by rukiaEnix on 2012-07-18
Did you try it with sudo?:

```

sudo iptables -L

```

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> Did you try it with sudo?:

```

sudo iptables -L

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by rukiaEnix on 2012-07-18
Please post the result of pinging your virtual 7 from the Ubuntu host.
 If I didn't explain: the ping of ubuntu to 7.

---

### Post by CharlesA on 2012-07-18
It should be fine. Just configure the Win7 firewall to accept echo requests.

[http://www.sysprobs.com/enable-ping-reply-windows-7](http://www.sysprobs.com/enable-ping-reply-windows-7)

---

### Post by fishsticks1907 on 2012-07-18
> **rukiaEnix said:**
> Please post the result of pinging your virtual 7 from the Ubuntu host.
 If I didn't explain: the ping of ubuntu to 7.

**Ubuntu to windows 7**
marcio@Ubuntu-PC:~$ ping -c 4 192.168.1.45
PING 192.168.1.45 (192.168.1.45) 56(84) bytes of data.

--- 192.168.1.45 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms

**Windows 7 to Ubuntu**
pings just fine, no packets lost.

---

### Post by rukiaEnix on 2012-07-18
Execute these commands to allow outgoing echo requests:

```

iptables -A OUTPUT -p icmp --icmp-type 8 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -p icmp --icmp-type 0 -m state --state ESTABLISHED,RELATED -j ACCEPT

```

---

### Post by fishsticks1907 on 2012-07-18
> **CharlesA said:**
> It should be fine. Just configure the Win7 firewall to accept echo requests.

[http://www.sysprobs.com/enable-ping-reply-windows-7](http://www.sysprobs.com/enable-ping-reply-windows-7)

Thanks it worked! i didnt know i had to enable it on windows 7. weird thou, when i boot to windows 7 and use ubuntu as a vm theres no problem with pinging. 

Also, thanks for all the help [rukiaEnix]("http://ubuntuforums.org/member.php?u=835489"). sorry for bugging you so much :)

---

### Post by rukiaEnix on 2012-07-18
You're welcome

---

### Post by CharlesA on 2012-07-18
Glad you were able to get it working.

---

