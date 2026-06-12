---
title: "fstab doesn't seem to work (CIFS etc.)"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by Pauligrinder on 2010-04-24
Hello.

I've setup a samba share on my server, which contains music. Then I mount this on all PC:s at home, so I can have the same songs everywhere. Two of the PC:s are running Arch Linux, one is running Xubuntu 9.04, and the server is running Ubuntu Server 8.04.

My problem is that the fstab on the Xubuntu machine seems to get bypassed (???). The samba share doesn't get mounted on boot, and if I mount manually (sudo mount -a), it gets unmounted when I switch users. On the Arch Linux machines, the share gets mounted on boot. The machines have the exact same syntax in fstab, there's just a few more lines in the Xubuntu machine (because I bind the share to each users /home/USER/music dir). There's obviously nothing wrong with the syntax, since sudo mount -a works.
I've been googling this all day, and finding only lots of "h0w d0ez I use teh wind0ze sharez 0n Ubuntu"-threads. (this is exactly why I switched to Arch...) 

Here's the line from my fstab:

```
//192.168.0.104/Music /mnt/music cifs users,credentials=/home/pauli/.smbcred 0 0
```
I'm not going to paste the binding part, since it doesn't really matter (the share doesn't get mounted without those either.) I have also tried mounting directly to the home directories, but that doesn't change anything either...

As I said before, this works just fine on my Arch machines. I have tried messing around with uid and gid options etc. but they seem to affect nothing. 
HELP! please.

EDIT:

Anyone??? 
Ahh, forget it, I'll ditch Xubuntu for good now and install Arch on that PC as well. Have a nice life, Ubuntu-community, you won't be seeing me around here anymore. Thanks for the support.

---

