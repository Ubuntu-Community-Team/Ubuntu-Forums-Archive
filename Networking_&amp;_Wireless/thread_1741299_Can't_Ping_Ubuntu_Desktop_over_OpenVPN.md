---
title: "Can't Ping Ubuntu Desktop over OpenVPN"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by shaneodell on 2011-04-27
At work I have an Ubuntu 10.10 Desktopp machine up and running and I use it to store files and test scripting and programming.  Using my Windows 7 laptop, I can access the samba shares, ssh and do whatever I want when I am physically connected on the network at work.

However when I use my Windows 7 laptop at home and connect over OpenVPN I can't ping, ssh or otherwise access the machine.  I can access all other resources on the work network over VPN.  I can connect to the firewall and ping and ssh to the Desktop from there.

The other interesting point is that same physical machine is hosting a 10.10 server using VirtualBox..  I can access that machine no problem over the VPN connection.  That is the weirdest thing that I can access the virtual machine but not the steel one. 

Can anyone provide me some direction?

Thanks

---

### Post by shaneodell on 2011-04-28
I can't believe it ... it was AppArmor that was causing the problem.  I found it from another howto that used before.  I remembered a little blurb in there that stuck with me.

" AppArmor is a security extension (similar to SELinux) that should  provide extended security. In my opinion you don't need it to configure a  secure system, and it usually causes more problems than advantages  (think of it after you have done a week of trouble-shooting because some  service wasn't working as expected, and then you find out that  everything was ok, only AppArmor was causing the problem). Therefore I  disable it "

This is how to do it:

```
/etc/init.d/apparmor stop
  update-rc.d -f apparmor remove
  aptitude remove apparmor apparmor-utils
```

---

