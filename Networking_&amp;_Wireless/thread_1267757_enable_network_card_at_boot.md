---
title: "enable network card at boot"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by gybe on 2009-09-16
I am using backtrack 4 which is basically ubuntu 8.04.
I have set my NIC and it is working okay, but this distro does not enable NIC at boot time for some security reasons.

what should I do so the system would boot with NIC enabled and running? after every single boot I have to go 'ifup eth0' to get it working.

I want a command line solution, please. adding a module? if yes, how? I am really stuck.

I want NIC to enable on boot not on user logon so I will be able to connect remotely through SSH in case the machine reboots for no reason (like power cut-off).

thanks!!

---

### Post by badger_fruit on 2009-09-16
```
sudo vim /etc/network/interfaces
```

add the line

```
auto eth0
```

save, close, restart networking

```
sudo /etc/init.d/networking restart
```

That should do it :)

---

### Post by gybe on 2009-09-16
nope it doesn't, I have auto eth0 line in there but my eth0 does not come on automatically

---

### Post by theozzlives on 2009-09-16
> **gybe said:**
> I am using backtrack 4 which is basically ubuntu 8.04.
I have set my NIC and it is working okay, but this distro does not enable NIC at boot time for some security reasons.

what should I do so the system would boot with NIC enabled and running? after every single boot I have to go 'ifup eth0' to get it working.

I want a command line solution, please. adding a module? if yes, how? I am really stuck.

I want NIC to enable on boot not on user logon so I will be able to connect remotely through SSH in case the machine reboots for no reason (like power cut-off).

thanks!!

Maybe use the real Ubuntu? I've tried a lot of Ubuntu's "children" and none work as good as Ubuntu.

---

### Post by lvlint67 on 2009-09-16
:( I have played with backtrack. I don't like it.
In my opinion you are better of grabbing a copy of linux mint and adding in the security scripts you need but since that is unreasonable for most backtrack users:

[http://ubuntuforums.org/showthread.php?t=53700](http://ubuntuforums.org/showthread.php?t=53700)

That might help out. If not... Then let us know.

---

### Post by gybe on 2009-09-16
it's just that backtrack has networking disabled at boot because it is not wise to request for an address from DHCP, that's all. so if it's disabled there's surely some way to enable it back up.

---

### Post by lvlint67 on 2009-09-16
> **gybe said:**
> it's just that backtrack has networking disabled at boot because it is not wise to request for an address from DHCP, that's all. so if it's disabled there's surely some way to enable it back up.

[http://ubuntuforums.org/showthread.php?t=172173](http://ubuntuforums.org/showthread.php?t=172173)

^some *dirty* stuff you can try^
ps adding ifup eth1 to /etc/network/interfaces won't work afaik

---

### Post by gybe on 2009-09-16
it's working now that I have put it into rc.local file, but at the moment I'm already writing a script for eth0 startup for init.d.

damn I just never get bored of finding 100 solutions to a problem

thanks anyone, links helped me a lot

---

### Post by seblx on 2012-04-07
adding the single line "auto eth0" to /etc/network/interfaces didn't worked for me either. but adding these two lines worked:

```

auto eth0
iface eth0 inet dhcp

```

---

### Post by Perfect Storm on 2012-04-07
Old thread, please start a new thread.

---

