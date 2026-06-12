---
title: "cannot see 1 pc on a 5 machine network"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by djm on 2011-01-07
Hi, I hope someone can help me on this as I am now stuck. I run a small home network consisting of 4 laptops and a server. my main laptop runs ubuntu 10.04 the server and 1 laptop run Ubuntu 10.10 the other 2 laptops, my wifes and daughters run Vista.

when I look at the network from any computer I can see all machines and work with them except the laptop running Ubuntu 10.10, this shows the others but not itself. I have samba  on it, but I have noticed that when i try to set a directory as sharing it says that Nautilus needs to add some permissions to the folder, when I give it permission I get the error 'Failed to execute child process "testparm" ( no such file or directory ) i dont know if this has anything to do with it but it might be. this is a installation I done when 10.10 was released but have not had reason to use the laptop until today.

hoping the someone can help
cheers dave

---

### Post by Morbius1 on 2011-01-07
> 'Failed to execute child process "testparm" ( no such file or directory )
See if you have samba-common-bin installed:
```
sudo apt-get install samba-common-bin
```
Then restart samba:
```
sudo service smbd restart
```

---

### Post by djm on 2011-01-10
thanks for the inf, that has got rid of the share error but i still cannot see the pc on the network.
dave

---

### Post by Morbius1 on 2011-01-10
If it's only the one laptop running Ubuntu that can't be seen I'
m wondering if nmbd on that system is not running.

Go to that laptop and check it's status:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```EDIT: You also might want to connect to it by ip address just to see if something more fundamental is the problem:
```
 nautilus smb://ip-address-of-problem-laptop
```

---

