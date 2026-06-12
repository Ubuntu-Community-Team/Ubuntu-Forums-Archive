---
title: "Samba share problem &quot;Premission denied&quot;"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by wobelin on 2010-07-12
On Ubuntu 10.04, I installed Samba and configured it. After restarting it, I went to another computer on the same local network and mounted the share: "smbmount  //192.168.1.99/smb_share /smb -o  rw,username=<username>,password=<password>". There is a loop image file in the shared directory, which I am trying to mount on the second PC -    "mount -t ext3 -o loop /smb/loop_file /mount_point" . When doing that I get error:  "smb_lookup: find loop_file failed, error=-13
/smb/ps2linux_loop:  Permission denied" . I can do a ("ls") and see the files in the folder, I can create new files in the folder.

---

