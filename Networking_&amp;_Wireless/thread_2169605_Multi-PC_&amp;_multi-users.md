---
title: "Multi-PC &amp; multi-users"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by Anthony_B on 2013-08-22
Hello,

At home, I have 2 Ubuntu-computers + 1 linux-server (Synology). We use to mount the server folders to the PCs (via NFS protocol) and we store there most of the files.

Is there anyway to "smartly" manage usersrights or file permissions with such a configuration ?

I tried to have the same usernames and groups on the different systems.
But, the same username (or the same groupname) could have different ID from system to the other... Hence, even if I logged as John on the server and create a file there, I won't have read&write access when I log as John on one of the other computer :(

Thanks in advance !!

---

### Post by tgalati4 on 2013-08-22
Since the Synology runs a form of linux, some of the following tools may help:

tgalati4@Mint14-Extensa ~ $ apropos uid
cpuid (4)            - x86 CPUID access device
dbus-uuidgen (1)     - Utility to generate UUIDs
euidaccess (3)       - check effective user's permissions for a file
findfs (8)           - find a filesystem by label or UUID
geteuid (2)          - get user identity
geteuid32 (2)        - get user identity
getpwuid (3)         - get password file entry
getpwuid_r (3)       - get password file entry
getresuid (2)        - get real, effective and saved user/group IDs
getresuid32 (2)      - get real, effective and saved user/group IDs
getuid (2)           - get user identity
getuid32 (2)         - get user identity
LDP (7)              - Intro to the Linux Documentation Project, with help, guides and documents
mdoc (7)             - quick reference guide for the -mdoc macro package
pam_loginuid (8)     - Record user's login uid to the process attribute
seteuid (2)          - set effective user or group ID
setfsuid (2)         - set user identity used for file system checks
setfsuid32 (2)       - set user identity used for file system checks
setresuid (2)        - set real, effective and saved user or group ID
setresuid32 (2)      - set real, effective and saved user or group ID
setreuid (2)         - set real and/or effective user or group ID
setreuid32 (2)       - set real and/or effective user or group ID
setuid (2)           - set user identity
setuid32 (2)         - set user identity
swaplabel (8)        - print or change the label or UUID of a swap area
UUID (3pm)           - Perl extension for using UUID interfaces as defined in e2fsprogs.
uuidd (8)            - UUID generation daemon
uuidgen (1)          - create a new UUID value

Perhaps changing the UID of a user's home file on the server to match the Ubuntu machine will fix the problem.  Although, I'm not sure how UID's affect user permissions, since UID's are only used on the system that created them.  It really shouldn't make any difference.  Make sure the spelling and upper and lower case of the username is exactly the same.

---

