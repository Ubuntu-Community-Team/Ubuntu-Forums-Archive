---
title: "Cannot copy files from samba share to Vista laptop"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by esvln on 2009-02-15
Hi all,

I have a network with 3 machines, one with Ubuntu 8.10, one with XP Pro and a new laptop running Vista home basic.

I've installed Samba 3.2.3 on the Ubuntu box and created a shared folder, simply by right clicking and setting the sharing permissions (haven't edited smb.conf). On all the machines, the workgroup is set to 'WORKGROUP'. On this machine, I can go to the network manager and see all the machines on the network. I can access a shared folder on the XP machine and copy files to and from this share with no problems. I can also access a shared folder on the Vista machine, and copy files from this share. I cannot copy files to the Vista share, the progress bar just hangs.

On the XP machine I can see all the PC's on the network, and copy to/from shares on both the linux and vista machines.

On the Vista laptop, I can see the linux machine and access the shared folder and see all the files. However if I try and copy a file from the linux share, the progress bar just hangs and eventually I get a network error message saying theres a problem accessing the share and check the network is still connected.

I'm unsure if this is a configuration problem with Samba or with Vista.

If I enter the 'smbstatus' command, I get the following error messages:

ERROR: Failed to initialise messages database: Permission denied
messaging_tdb_init failed: NT_STATUS_ACCESS_DENIED

If I look at the Samba log created for connections to the Vista PC, I can see the following relating to when I've tried to access the share:

[2009/02/15 18:12:39,  0] param/loadparm.c:process_usershare_file(8282)
  process_usershare_file: stat of /var/lib/samba/usershares/videos failed. Permission denied
[2009/02/15 18:13:43,  1] smbd/service.c:close_cnum(1405)
  col-pc (192.168.1.67) closed connection to service videos

Googling, i've noticed theres a bug report relating to the smbstatus error messages, but I don't understand the 'fix' thats been posted.

Appologies for the ramble, anybody got any ideas?

Thanks

---

### Post by dmizer on 2009-02-16
I don't recall seeing a bug report on this, it might help if you linked to it and we could tell you how to implement it (if indeed you are affected by this bug).

Try enabling winbind on the Ubuntu computer according to the following directions:

Edit /etc/nsswitch.conf by entering the following command:
```
gksudo gedit /etc/nsswitch.conf
```

Add "wins" to the hosts line so that it looks like this:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```
The order _IS_ important here, so make sure that "wins" is in front of "dns".

Save the file, and exit gedit.

Then install winbind with the following command:
```
sudo aptitude install winbind
```

Reboot for good measure, and try to access the share from Vista again.

---

### Post by esvln on 2009-02-16
Many thanks for your reply dmizer.

I'll have a go at enabling winbind as you've suggested.

Heres the link for the bug report:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/278712](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/278712)

Not sure if it's 100% relevant.

Cheers

---

### Post by dmizer on 2009-02-16
No, that bug is completely unrelated. Sorry.

Let me know how it goes with winbind.

---

### Post by esvln on 2009-02-16
I've edited nsswitch.conf and installed winbind, but unfortunatley getting the same issue. As before I can copy from the share at the Linux end, but can't do anyhting on the Vista end.

Looking at smbstus and the samba log, the same error messages are appearing.

Although interstingly during writing this I just managed to copy a 1KB text file over no problems. But when trying 74KB text file, and a 47KB word file, I get the same issue.

Anymore suggestions would be much appreciated.

---

### Post by dmizer on 2009-02-16
You may have better luck with getting Vista to work if you configure smb.conf.

I suggest taking a look at the samba howto in the first link in my sig.

---

### Post by esvln on 2009-02-17
Still no luck i'm afraid.

Have followed the guide, and can access the share from the vista machine, and see the files in the shared folder. But I still get the same issue when I attempt to copy a file.

No probs with the XP machine

Thanks for your suggestions so far

---

### Post by dmizer on 2009-02-17
Please post your /etc/samba/smb.conf file.

---

### Post by esvln on 2009-02-18
Heres my smb.conf. Used the one form the HOWTO and edited as directed by the guide


```
[global]
    ; General server settings
    netbios name = COL_DESKTOP
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/colin/Documents
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = colin
    force group = colin
```

---

### Post by dmizer on 2009-02-18
Okay, make a backup of your current working smb.conf (make sure you are not making any file transfers before doing this):
```
sudo /etc/init.d/samba stop
sudo mv /etc/samba/smb.conf /etc/samba/smb.backup
```
Then make a new smb.conf:
```
gksudo gedit /etc/init.d/smb.conf
```
And put this in it:
```
[global]
    ; General server settings
    netbios name = COL_DESKTOP
    workgroup = WORKGROUP
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[MyFiles]
    path = /home/colin/Documents
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = colin
```
Save the file, exit gedit, and restart samba:
```
sudo /etc/init.d/samba restart
```
Make sure all your XP computers can still read the share, then test to see if the Vista computer can.

---

### Post by esvln on 2009-02-20
Assume I needed to move the smb.conf file back into etc/samba/.

Used the config in the last post. With the XP machine, I can access the share and copy files as before. With the Vista machine I get the same problem as before, can see the files in the share, but can't copy them.

Thanks

---

### Post by dmizer on 2009-02-20
The smb.conf file I gave you is preferable to the one you posted, so you don't need to restore anything as long as it's still working for XP.

This is probably a Vista issue. Check for firewalls, try disabling them. I've not seen anything quite like you describe, but Vista is notoriously difficult to get working with Samba.

---

### Post by wgarn on 2010-08-27
Most likely the issue was resolved. However, it could have been something as simple as setting the permissions on the Vista folder.
1) On your Vista Computer start the Windows Explorer and go to the shared folder (if it is not shared yet then Right Click >> Share... >> Advanced Sharing: tick "Share the Folder")
2) Set permissions:  Right Click on folder >> Properties >> Sharing >> Advanced Sharing >> Permissions: select "Everyone" and tick "Full Control"

---

