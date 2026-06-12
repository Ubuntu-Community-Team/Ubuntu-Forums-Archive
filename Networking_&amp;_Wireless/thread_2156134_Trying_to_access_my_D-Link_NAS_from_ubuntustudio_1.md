---
title: "Trying to access my D-Link NAS from ubuntustudio 12.04"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by ratdog on 2013-06-20
Hello,

I once had my computer setup to automatically mount my D-Link DNS-321 shares on startup.  Now, after upgrades and updates, I cannot access it at all.  I have come to despise seeing the dreaded 'Failed to retrieve shares list from server' message.

I have wasted several days reading tutorials and changing settings to no avail.  I hope there is a kind soul here that can help me troubleshoot this problem.  I would be so grateful and would have a much more functional technological experience.

I know that the NAS could be accesed is I could get the settings right on my Ubuntu laptop because it does just automatically show up in my wifes macbook finder window.

Please help!

I will reply promptly to any guru who can offer some sage advice.  :)

---

### Post by 2F4U on 2013-06-22
This is an example entry from my /etc/fstab to mount a share on my NAS:

//ip_address/AFolder /mnt_folder cifs auto,users,credentials=/path/.cred,uid=name,gid=users,file_mode=0660,dir_mode=0770 0 0

You need to install the package cifs-utils to be able to mount. The credentials entry points to a file .cred, which should be located somewhere. Of course, your NAS must be configured to provide Samba or Windows file sharing.
The content of the file are

username=user_on_nas
password=pwd_of_user_on_nas

This lets you mount the share without entering the credentials. The user and group should reflect your local user.

---

