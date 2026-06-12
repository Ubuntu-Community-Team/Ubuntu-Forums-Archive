---
title: "Mythbuntu 8.10 can't access /dev/video0"
date: 2009-01-29
forum: Mythbuntu
---

### Post by bb_145 on 2009-01-29
There is probably a simple solution to this, but I can't find it... (I only started with linux last week)

My problems started when I ran into a known problem when trying to intall Mythbuntu 8.10 and a Hauppauge WINTV-PVR-USB on my computer. Due to an issue with the pvrusb2 driver, the liveCD would hang.  I found a work around ([http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html](http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html)), but it mean't I couldn't install my Hauppauge WINTV-PVR-USB card during the liveCD session, and instead had to install it after the reboot.

Probably because of this, I ran into the next problem, which was that I couldn't get Mythbuntu to access the device.  I eventually tracked it down to a permissions issue.  I found that if I type "sudo chmod 777 /dev/video0", then I can get Mythbuntu to find the device.  However, I suspect that is not the best thing to do, and the settings are forgotten on reboot.  Is there a better way? (Preferably something simple that a newbie can understand :))

Thanks in advance.

---

### Post by Mister.Vash on 2009-01-29
Check and make sure that the owners of /dev/video0 are showing as  root:video and that the video group has the correct permissions.  They should, so we are just double checking it.

```

ls -lah /dev/video*

crw-rw----+ 1 root video 81, 0 2009-01-28 23:46 /dev/video0

```

Then make sure that the account you are using to run mythtv is a member of the video group.  System -> Administration -> Users and Groups

---

### Post by bb_145 on 2009-01-30
Thanks!  Just the help I needed.  I think it is working now.

The permissions were set properly, but there was no video group.

---

