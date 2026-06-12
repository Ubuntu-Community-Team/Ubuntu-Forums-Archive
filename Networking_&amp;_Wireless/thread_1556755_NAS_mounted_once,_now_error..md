---
title: "NAS mounted once, now error."
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by robb. on 2010-08-19
i followed the [Mount Windows Shares Permanently wiki](V) to mount my NAS (DNS-323).  it worked exactly once.  after restart, i get this error message when i sudo mount -a:

```
error -1 (Unknown error 4294967295) opening credential file ~/.smbcredentials
```

i have verified that the file exists in my home directory and contains the same username and password that worked the first (and only) time this worked.
any ideas?

thanks.
robb.

---

### Post by robb. on 2010-08-20
i decided to put my username and password directly into fstab (instead of referencing a credentials file) to see what would happen.  i got the following message after sudo mount -a:

```
WARNING: 'dmask' not expressed in octal.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
WARNING: 'fmask' not expressed in octal.
WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
```

so i changed fmask and dmask to file_mode and dir_mode, and it mounted again.  we'll see if this works after a restart.

thanks.
robb.

---

### Post by robb. on 2010-08-20
turns out the real issue was using ~ instead of /home/username.  all fixed and working.

thanks.
robb.

---

