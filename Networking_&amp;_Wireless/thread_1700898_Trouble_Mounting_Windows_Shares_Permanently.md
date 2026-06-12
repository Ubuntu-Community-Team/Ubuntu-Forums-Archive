---
title: "Trouble Mounting Windows Shares Permanently"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by HNSingh on 2011-03-05
I'm having trouble getting a permanent Ubuntu-XP connection. I've followed the instructions on these two web pages:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
[http://www.chromedocs.net/2011/01/how-to-mount-windows-shares-permanently.html](http://www.chromedocs.net/2011/01/how-to-mount-windows-shares-permanently.html)

This caused a boot-up error message:
 
 “Mountall: Disconnected from Plymouth”
 
 I applied this “fix” and the error message has gone away. Hopefully this was okay:

[http://ubuntuforums.org/showthread.php?t=1602767](http://ubuntuforums.org/showthread.php?t=1602767)

Now, after the Ubuntu computer boots up and is logged in, I believe that there should be a hard drive icon on the desktop that connects to the “Share” folder on the XP computer. There isn't. Nor is there a new drive in Nautilus.
 
 The XP computer can read and write a “Share” folder on the Ubuntu computer just fine.
 
 The Ubuntu computer is running 10.10 64-bit and requires a login. The Windows computer is running XP Home and does not require a login.
 
 Here is the Fstab file:
 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    nodev,noexec,nosuid 0       0  
 /dev/sda1       /               ext4    errors=remount-ro 0       1  
 # swap was on /dev/sda5 during installation  
 UUID=d86314fc-481b-4744-a1aa-ae9c2a9e14a7 none            swap    sw              0       0  
  
 //192.168.0.2/Share    /mnt/hackberry_share  cifs  iocharset=utf8,credentials=/home/lilly/.smbcredentials,uid=1000  0  0 
 
And the .smbcredentials file is empty since the XP computer doesn't use a user name or password.
 
I'm completely stumped on what to do next.
 Thanks for the help in advance!

---

### Post by Morbius1 on 2011-03-05
> Now, after the Ubuntu computer boots up and is logged in, I believe that  there should be a hard drive icon on the desktop that connects to the  “Share” folder on the XP computer. There isn't. Nor should there be. If you want a mount icon on the desktop you need to change the mount point to something in /media or in /home/lilly.

You should find the remote share at /mnt/hackberry_share
> //192.168.0.2/Share    /mnt/hackberry_share  cifs  iocharset=utf8,credentials=/home/lilly/.smbcredentials,uid=1000  0  0 
 
And the .smbcredentials file is empty since the XP computer doesn't use a user name or password.
 I'm not entirely sure that will work - specifying a credentials file but having it blank. Why not just use "guest":
```
//192.168.0.2/Share    /mnt/hackberry_share  cifs  iocharset=utf8,guest,uid=1000  0  0 
```

---

