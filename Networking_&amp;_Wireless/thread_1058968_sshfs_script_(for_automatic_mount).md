---
title: "sshfs script (for automatic mount)"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by cervell on 2009-02-03
Hi there,

just tried out sshfs and must say that it works great. However - when it comes to mounting I'm facing a problem that's driving me crazy...;)

Manual mount in terminal works flawlessly;

```
sshfs user@hostadress:/directory_on_host /mount_point
```

However - my automated script doesn't. It executes, connects, and asks me for my password. Giving the password, the terminal closes and up comes nautilus. But nothing is mounted...
```

#!/bin/bash

sshfs user@hostadress:/directory_on_host /mount_point
nautilus /mount_point

```

I also tried an amount of other scripts available around the internet, but all of them are giving me the same result. Have someone experienced anything similar to this? Any help would be much appreciated!

By the way, thanks for a great community. Can't beleive I lasted almost a year in the ubuntu world without becoming a member...

/Johan

---

### Post by scurry7 on 2009-02-04
does it ask you for password when you just do it from terminal?

sounds like you need this: [http://linuxproblem.org/art_9.html](http://linuxproblem.org/art_9.html)

if you can ssh to the server w/o password then you should be able to sshfs to it w/o password also....

here is my notes on it:
```

on the node you want to be able to remote access from
&#8226; ssh-keygen -t rsa
&#8728; save the key in your /home/username/.ssh/id_rsa
&#8728; no/blank passphrase
&#8226; ssh user@remoteHost mkdir -p .ssh
&#8226; cat .ssh/id_rsa.pub|ssh user@remoteNode 'cat >> .ssh/authorized_keys'


now you can ssh user@remoteNode w/o password

```


let me know if that helps

---

### Post by finer recliner on 2009-02-04
after running the script, what is the output of the command:
```

mount

```

(this command simply lists all volumes currently mounted on your computer and where they are mounted)

---

### Post by cervell on 2009-02-07
Thank you both for your replies.

It does ask me for a password when mounting manually through terminal. The procedure works the same with the script, but nothing gets mounted. I will try the password-less approach to this problem, but it doesn't suit my needs fully - the best thing would be to get the script going...

Output of 'mount' ;
```

cervell@johan-linux:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
lrm on /lib/modules/2.6.24-22-generic/volatile type tmpfs (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=1001,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/cervell/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cervell)

```

---

