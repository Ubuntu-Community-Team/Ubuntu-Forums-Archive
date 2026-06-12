---
title: "xubuntu network configuration?"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by nmatheis on 2006-02-03
hello
how do i get to the network configuration setings in xubuntu?  i looked in the system settings menus but can't find a network configuration set-up.  i'd like to switch from using dhcp to using a static ip address with my router.  
thanks for any help!!!
nikolaus

---

### Post by nmatheis on 2006-02-03
Hello again!

So a few more details in case that helps :)   I can apt-get, but using synaptic and firefox don't happen.  I can start the programs but when I try to surf the web, firefox just spins its wheels and the netapplet shows barely any activity at all.  Same when I try to fetch updates using synaptic - spins its wheels and times out.  When I apt-get in the terminal - no problems encountered.  I'm getting my internet connection from the same router as my desktop computer and firefox's "internet connection" settings are same - "direct connection to the internet".  I've used Ubuntu on this laptop before and didn't have these problems and am running Ununtu on my desktop computer with no probems.  I switched to Xubuntu because my laptop is slooow and Xubuntu is more resonsive, but not if I can't connect to the internet.

So, if y'all can help me trouble-shoot this, I'd be greatly appreciative!!!

Thanks
Nikolaus

---

### Post by mips on 2006-02-03
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by nmatheis on 2006-02-03
thanks for the link.  but perhaps i'm a bit daft, but what i want to find in xubuntu is the network manager interface in gui form.  gnome and kde both have network settings managers in which one can manually set the network on autoconfigure/dhcp or set the ip/gateway/dns numbers.  i want to see this interface when i'm running xubuntu.  doesn't it have this kind of basic gui-based network tool?  if not, is there one i can apt-get?
thanks again!
nikolaus

---

### Post by mips on 2006-02-03
Sorry, I have never used Xubuntu so I would not know.
You can always access the config files via a text editor in the meantime until you find out what to use:
/etc/network/interfaces  &  /etc/resolv.conf

---

### Post by nmatheis on 2006-02-03
hello again
i used synaptic to get a package named something like ethconfig.  it used a terminal-based frontend to configure eth0 for dhcp, which allowed me to get on the internet.  but i came across an error message at reboot that went something like this:
Can't find xubuntu.example.com
Add xubuntu.example.com to /etc/hosts
So, I tried to sudo my way into /etc/hosts to change the file only to get the same error message coming up in the terminal.  looks like i took away my sudo rights by overwriting a the file during the ethconfig eth0 set-up.
so...how do i go about getting the file changed so i can get back my sudo priveleges?
thanks!
nikolaus

---

### Post by nmatheis on 2006-02-03
okay, so ethconfig got my computer all dhcp-ed up and surfing the web.  my informatics guy at work booted my computer up in single-user mode and reset my root password so i could go in and use sudo to change the /etx/hosts.allow file.  then he looked at that file and set the xubuntu.example.com to a loopback ip address, which solved the problem of getting an error message at login.  so i need to check to make sure that my internet functionality is still intact, and i think everything will be peachy.

---

### Post by nmatheis on 2006-02-03
so just in case someone needs help with the same situation.  after trying the internet again, there was once again no name resolution.  so i ended up using the terminal to apt-get gnome-system-tools.  once this was installed, i made sure the system was configured to dhcp so i could use it on the network at work and home without worrying about changing the network settings, and everything was good to go.  i just hooked it up t my router at home, and everything is good here, too.  

it would be nice for the xubuntu crew to make sure to include at least a basic graphic network manager.  the informatics guy at work was very surprised that this was lacking.  the gnome-system-tools package works well!

nikolaus

---

### Post by troutusa on 2008-06-13
has this issue ever been resolved. Can you outline the steps for me. I just installed Xubuntu and firefox can't connect to my LAN.

---

