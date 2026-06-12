---
title: "Accessing links to Windows folders though Samba shared Home"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by fatski on 2012-10-21
So, in my home directory I have replaced the Documents, Music etc folders with links to the equivalent directories on my Windows partition, cause I dual boot and had Windows first so all my music etc is on that partition. This just works just fine on the machine Ubuntu is installed on. I have also shared my home folder on my local network so I can access files from other computers and my Android tablet. This works fine for files within the home folder, and any directories that aren't links to the Window partition. However, I am unable to access any of the linked directories, I think because they are owned by root, even though they are set to have read / write permissions for all other users. I also can't change the owner of the links with "sudo chown" for some reason.

Anybody got any ideas how I can allow these directories to be accessed by other machines on my network?

Cheers.

---

### Post by bab1 on 2012-10-21
> **fatski said:**
> So, in my home directory I have replaced the Documents, Music etc folders with links to the equivalent directories on my Windows partition, cause I dual boot and had Windows first so all my music etc is on that partition. This just works just fine on the machine Ubuntu is installed on. I have also shared my home folder on my local network so I can access files from other computers and my Android tablet. This works fine for files within the home folder, and any directories that aren't links to the Window partition. However, I am unable to access any of the linked directories, I think because they are owned by root, even though they are set to have read / write permissions for all other users. I also can't change the owner of the links with "sudo chown" for some reason.

Anybody got any ideas how I can allow these directories to be accessed by other machines on my network?

Cheers.

Samba no longer follows sym-links by default.  They have deemed it to be a [**_[COLOR="Blue"]security risk[/COLOR]_**]("http://www.samba.org/samba/news/symlink_attack.html").  But you can reconfigure it if you wish.  [**_[COLOR="Blue"]Here[/COLOR]_**]("https://www.google.com/search?q=samba+symlinks&btnG=Go!#hl=en&sclient=psy-ab&q=samba+symlinks+ubuntu&oq=samba+symlinks+ubuntu&gs_l=serp.3..0i30j0i8j0i8i30l2.51423.53867.0.54322.7.7.0.0.0.0.147.958.0j7.7.0.les%3B..0.0...1c.1.WLEiMB6xIhI&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ee2cd9b81b9db13c&bpcl=35466521&biw=1248&bih=661") are some ideas.

---

### Post by fatski on 2012-10-22
Thank you, adding the options to smb.conf suggested in the threads you linked a search to resolved the issue.

---

