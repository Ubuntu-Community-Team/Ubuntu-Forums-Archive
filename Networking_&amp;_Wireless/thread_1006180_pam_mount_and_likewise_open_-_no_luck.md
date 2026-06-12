---
title: "pam_mount and likewise open - no luck"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by tensop on 2008-12-09
Hi all,

I'm attempting to automount shares upon login using pam_mount. the current authentication uses likewise open to handle the AD login - which is succesful, however attempts to use pam_mount to mount the volume seem to result in absolutely nothing - no console messages(even with debug set to 1) and no messages in /var/log/syslog

unfortunately it seems to have changed to an xml format aswell, so the previous docos floating around here need decyphering to get anywhere

surely it should be simple....

does anyone have examples of their pam_mount.conf.xml file and their common-*' files + lwidentity file?

---

### Post by tensop on 2008-12-09
OK, got a little further

here is pam's output:


[php]
information for mount:
----------------------
user:       administrator
server:     10.1xx.1xx.1xx
volume:     stdhome
mountpoint  /test
options     uid=%(USER),gid=root,dir_mode=0700,nosuid,nodev
fs_key_cipher:
fs_key_path:
use_fstab:    0
----------------------------
realpath of volume "/test" is "/test"
checking to see if stdhome is already mounted at /test
checking for encrypted filesystem key configuration
about to start building mount command
command: mount [-p0] [-t] [auto] [stdhome] [/test] [-o] [uid=%(USER),gid=root,dir_mode=0700,nosuid,nodev]

mount errors:
mount: special device stdhome does not exist
[/php]


so ahh, wtf is the cause of that?

atleast now i know PAM is pulling the userid and probably the password successfuly, but it wont run the command now

---

### Post by tensop on 2008-12-09
ok, got it working

after alot of hair pulling, one little typo was at fault

my source was:
[http://ubuntuforums.org/showthread.php?t=878685&highlight=pam_mount](http://ubuntuforums.org/showthread.php?t=878685&highlight=pam_mount)


the error was 

[php]

<volume options="uid=%<volume options="uid=%(USER),gid=root,dir_mode=0700,nosuid,nodev" user="*" fsype="cifs" server="fs1" path="users" mountpoint="/home/local/DOMAINANME/AD_username/mountfolder_name" /> 
[/php]

in the original post

error can be seen as 'fsype="cifs"'

should be fstype

/me finishes pulling out hair :lolflag:

---

### Post by gixxer.rob on 2008-12-10
tensop 
glad you got it working. i am a bit of a Linux newb so forgive me if the answer is obvious. Are you using a credentials file ? 

I ask because i to am using likewise open and have no problems with logging in with AD credentials but as you experienced i get nothing in the way of error output just no windows share after logging in.

Could i be a pain and ask what you have done after installing libpam_mount I think i may be missing something..

Cheers

---

### Post by tensop on 2008-12-11
Fired off a PM your direction.

the following is needed:

likewise-open
libpam_mount
smbfs

---

