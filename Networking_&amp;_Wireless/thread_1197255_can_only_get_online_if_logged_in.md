---
title: "can only get online if logged in"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by zeiden on 2009-06-25
Hi, I'm running Ubuntu Workstation Jaunty Jackalope. 

I initially configured the network under a user login with administrative rights, using the GUI under System ... Preferences ... Network Connections. Everything worked fine.

But then I found that if I rebooted the machine, I didn't get any network if I didn't log in as this user from the console.

I tried setting the network settings (they are static) in the usual place, /etc/network/interfaces as follows:

auto eth1 inet static
address x.y.z.107
gateway x.y.z..1
netmask 255.255.255.128
network x.y..z.0
broadcast x.y.z.127

(Don't want to post x.y.z publicly)

I checked with our network people and these are the correct settings. But it doesn't work, I still need to log in in order to get a network connection. Removing the settings in the Network Connections GUI doesn't help, either; that way, I can't get anything either way.

Appreciate any help you can give. Thanks.

Matt Zeidenberg

---

### Post by cariboo on 2009-06-26
If your are running Jaunty, editing /etc/network/interfaces, does not work. Use Network-Manager to set your static ip address.

---

### Post by zeiden on 2009-06-26
Thanks. I ended up uninstalling NetworkManager on the advice of this thread

[https://lists.ubuntu.com/archives/kubuntu-users/2009-April/thread.html#41967](https://lists.ubuntu.com/archives/kubuntu-users/2009-April/thread.html#41967)

and that did the trick.

I guess NetworkManager takes precedence if it is installed, and it is by default.

Matt

---

