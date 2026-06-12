---
title: "map a network drive? NAS"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by Redeyes_Gambit on 2006-07-11
}{i, I have a question. :)

I have a NAS device in the form of an old computer running "Freenas", and in windows all I have to do to "map the drive" is right-click on "my computer" and hit "map network drives" button. Then, a box will pop up where I assign a drive letter and give it the path of \\192.168.2.111\freenas and all is well.

However I have been having a bit of trouble in ubuntu.

I have tried several guides here and there to get the drive to mount at startup with read and write privs, but to no avail. I tried the guide found [here]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

and did everything it said. But, when I get to the step of remounting /etc/fstab (with sudo mount -a ) I get the error:

wrong fs type, bad option, bad superblock on //192.168.2.111/freenas,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Where have I taken a wrong turn? (oh, please note that I am not sure I set up the .smbcredentials right. I left both the user and password fields blank because the server doesn't require a password, or as far as I know a username. Am I wrong?)

Many thanks in advance! :)

---

