---
title: "BCM4322 driver activated but not working"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by xavi787 on 2011-06-17
Hello 

I'm new to the forum

I was trying to get the b43 driver work with my broadcom bcm4322 wireless card. I changed the kernel from 2.6.32 to 2.6.38 in order to make the b43 driver to work. When I booted with the new kernel the internet stopped working so I looked for a solution. I don't remember which website I went but it said that I have to re-install the STA drivers so I did that and rebooted and nothing happened. I decided to go back to the 2.6.32 kernel and re-installed the STA drivers. The wireless card (eth1) isn't showing when I run the command  iwconfig

```

xavi@xavi-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

easytether0  no wireless extensions.

xavi@xavi-laptop:~$ 


```

I'm currently running Ubuntu 10.04 Lucid Lynx

---

### Post by manzdagratiano on 2011-06-17
Since the Broadcom STA drivers support the 4322 card, you should always resort to using them.

Aside from enabling the STA drivers, you need to blacklist the conflicting b43 and ssb modules, since I suspect they were enabled if you tried using the b43 drivers:

```

$ sudo echo b43 >> /etc/modprobe.d/blacklist.conf
$ sudo echo ssb >> /etc/modprobe.d/blacklist.conf

```

Then reboot, and this should do the trick.

---

### Post by xavi787 on 2011-06-17
Echo didnt work for me but I blacklisted b43 and ssb with Gedit

```


xavi@xavi-laptop:~$ $ sudo echo b43 >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
xavi@xavi-laptop:~$ $ sudo echo ssb >> /etc/modprobe.d/blacklist.conf]
bash: /etc/modprobe.d/blacklist.conf]: Permission denied
xavi@xavi-laptop:~$ sudo gedit /etc/modprobe.d/blacklist.conf
[sudo] password for xavi: 
xavi@xavi-laptop:~$ 


```

Rebooting :)

---

### Post by xavi787 on 2011-06-17
It worked thanks :D !

---

### Post by manzdagratiano on 2011-06-17
Very excellent!!!

I am surprised though that echo did not work for you even with sudo!!!

---

