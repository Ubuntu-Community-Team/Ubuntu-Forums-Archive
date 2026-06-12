---
title: "CIFS Shares Disappearing"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by mdmcaf on 2013-03-26
I've got a Windows server with drives that I want to share with my Xubuntu 12.04 desktop. I've successfully added the shares to my fstab file and the drives mount automatically when I log into the Xubuntu desktop. The problem that I have is that after about 20-30 minutes of being connected to the shares they disappear.

When I try to access them through Thunar by clicking on the shortcut the window freezes and Thunar crashes. When I try to access the shares through the terminal it sits with the cursor blinking until I finally close the window. I've tried to umount the shares and reconnect to them but I get an error that says that the share is currently being used. I have to reboot the computer in order to get my shares back.

I'm getting a little sick of rebooting every 20-30 minutes as it makes it hard to get any work done so I was hoping that someone would be able to help me out.

Here's what my fstab looks like (with the password edited out):

```


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f6733abb-f5ee-4acf-821a-2dde408ed4ce /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=26047046-401f-4857-9619-7cf5a696aa1c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5b257f62-e937-41b3-bccc-ce9df6a409d9 none            swap    sw              0       0
# CIFS Network Share Data
//192.168.1.224/Data /home/chrisf/mounts/data cifs username=chrisf,password=<password>,_netdev,uid=chrisf,gid=users 0 0
# CIFS Network Share Drive_D
//192.168.1.224/Drive_D /home/chrisf/mounts/drive_d cifs username=chrisf,password=<password>,_netdev,uid=chrisf,gid=users 0 0



```

---

### Post by mdmcaf on 2013-03-27
I think that I figured out the problem. I created a credentials file in my home directory with the correct credentials and then pointed my fstab entries for those shares at the credential file and it hasn't dropped its connection for about 6 hours or so. Hopefully that's the final fix and it doesn't just break on me again.

---

