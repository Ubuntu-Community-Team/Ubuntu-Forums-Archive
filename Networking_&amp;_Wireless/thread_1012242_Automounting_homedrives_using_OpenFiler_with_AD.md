---
title: "Automounting homedrives using OpenFiler with AD"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by Milenco on 2008-12-15
I've been trying for some days now to connect my Ubuntu 8.04 workstations to my Windows Server 2008 domain. Using the Howto on this forum ([http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)) I was able to successfully join my Ubuntu workstations to the domain.

I'm using OpenFiler as my fileserver, which I also joined to the Win2008 domain, so the same credentials can be used. To automate the homedrive mounting I used the tutorial [http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/SambaAuth](http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/SambaAuth) .

At this point the homedrive mounting is working, as in: When users log on, the homedrive get automatically mapped to /home/DOMAIN/user and the user has read/write access to this folder. Other homedrives in /home/DOMAIN are inaccessible, which is the correct behavior. So far everything goes right.

However, I do encounter a strange problem I can't seem to fix (mostly because of my lack in Linux/Ubuntu skills). Even though the user has read/write access, the system doesn't really seem to know that. For example, when I log in using a domain account for the first time, I get several errors from Gnome stating it cannot write the files necessary to the homedrive. When I check the path however, the files _are_ written to the homedrive. When I log out and in again the error is gone, but only to come back again when the system needs to write another file to the homedrive. When I start Firefox for the first time it needs to write a profile to the homedir. When I give up a name for this profile and I want to apply it, I first get a error that the file cannot be written. When I accept this error and click on the apply button again, it does continue creating the profile (since it happened the first time I tried, only the system disagreed) .

It seems the system incorrectly gets the idea it cannot write files to the homedrive, where in reality it does write them.

I installed lib_pammount with these configuration files:

I added this line to pam_mount.conf.xml (I also removed the dmask=0751 part without success):
```
<volume fstype="smbfs" server="192.168.3.240" path="%(USER)" mountpoint="~" options="dmask=0751,workgroup=SUPERSTAR" />
```

Complete pam_mount.conf.xml (which is just default besides the added lines I stated above):
```

<?xml version="1.0" encoding="utf-8" ?>
<pam_mount>

<!--
NOTE: Special characters like < > and & require escaping them to &lt; &gt;
and &amp; according to the XML standard. Though, you really should not use
them in pathnames.

Do not use comments inside tags like <lsof></lsof> - the case is not
handled by the parser.
-->


<!-- Turn on if you want to debug why some volume cannot be mounted etc.
This can be overriden by user's local configuration. This will also affect
the pmvarrun helper program. To disable, use enable="0" or comment it out
entirely. -->
<debug enable="0" />


<!--
Create mountpoint if it does not exist yet. This is a good thing.

If enabled, and a mountpoint was created by pam_mount, the mountpoint will
be removed again on logout. To disable this behavior, use remove="false".
-->
<mkmountpoint enable="1" remove="true" />


<!-- Loopback device to use to run fsck on loopback filesystems. -->
<fsckloop device="/dev/loop7" />


<!--
Users' local configuration file (if there is none, comment this parameter
out). Will be read as ~/<file>.

Note: you must include either options_allow or options_deny to use this
directive. I recommend also including options_require.

Individual users may define additional volumes to mount if allowed by
pam_mount.conf.xml (usually ~/.pam_mount.conf.xml). The volume keyword is
the only valid keyword in these per-user configuration files. If the
luserconf parameter is set in pam_mount.conf.xml, allowing user-defined
volumes, users may mount and unmount any volumes they specify. The mount
operation is executed under the user account, not with root permissions.

<luserconf name=".pam_mount.conf.xml" />
-->


<!--
These directives determine which options may be specified in a user config
file (luserconf). You must include one of these directives if you have a
luserconf directive. You may not include both directives.

If you have an options_allow directive, then the options listed in that
directive wil be allowed, and all others rejected. If you have an
options_deny directive, then the options listed will be denied, and all
others permitted.

You may use the wildcard '*' to match all options. I recommend not
permitting the suid and dev options.
-->

<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->


<!--
The options listed in this directive are required for all volumes from a
user config file. That is, any volume specified in a user config file that
does not include these options will be ignored.

Note: you must make sure that a required option is permitted (either by
including it in options_allow, or by not including it in options_deny).

I recommend requiring at least nosuid and nodev.

This is ignored completely if the volume is configured to get its options
and mount point from /etc/fstab.
-->
<mntoptions require="nosuid,nodev" />


<!--
Commands to mount/unmount volumes. They can take parameters, as shown.

If you change the -p0 argument for lclmount, you'll need to modify the
source in mount.c (it sends the password to the stdin file descriptor of
the child process - look for STDIN_FILENO).

You can specify either absolute paths, or relative ones, in which case
$PATH will be searched. Since some login programs really behave
antisocial, pam_mount will always set its own $PATH.
-->

<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>

<lsof>lsof %(MNTPT)</lsof>

<fsck>fsck -p %(FSCKTARGET)</fsck>

<losetup>losetup -p0 "%(before=\"-e\" CIPHER)"
    "%(before=\"-k\" KEYBITS)" %(FSCKLOOP) %(VOLUME)</losetup>

<unlosetup>losetup -d %(FSCKLOOP)</unlosetup>

<cifsmount>mount -t cifs //%(SERVER)/%(VOLUME) %(MNTPT) -o
    "user=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</cifsmount>

<davmount>mount -t davfs %(SERVER)/%(VOLUME) %(MNTPT) -o
	"username=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\"
	OPTIONS)"</davmount>

<smbmount>smbmount //%(SERVER)/%(VOLUME) %(MNTPT) -o
    "username=%(USER),uid=%(USERUID),gid=%(USERGID)%(before=\",\" OPTIONS)"</smbmount>

<smbumount>smbumount %(MNTPT)</smbumount>

<ncpmount>ncpmount %(SERVER)/%(USER) %(MNTPT) -o
    "pass-fd=0,volume=%(VOLUME)%(before=\",\" OPTIONS)"</ncpmount>

<ncpumount>ncpumount %(MNTPT)</ncpumount>

<fusemount>mount.fuse %(VOLUME) %(MNTPT) "%(before=\"-o \" OPTIONS)"</fusemount>

<fuseumount>fusermount -u %(MNTPT)</fuseumount>

<truecryptmount>truecrypt %(VOLUME) %(MNTPT)</truecryptmount>

<truecryptumount>truecrypt -d %(MNTPT)</truecryptumount>

<!-- Linux supports lazy unmounting (-l). May be dangerous for encrypted
volumes. May also break loopback mounts because loopback devices are not
freed. Need to unmount mount point (not volume!) to support SMB mounts,
etc. -->
<umount>umount %(MNTPT)</umount>


<!-- On OpenBSD try "/usr/local/bin/mount_ehd" (included in pam_mount
package). -->
<lclmount>mount -p0 -t %(FSTYPE) %(VOLUME) %(MNTPT)
	"%(before=\"-o\" OPTIONS)"</lclmount>

<cryptmount>mount -t crypt "%(before=\"-o \" OPTIONS)"
	%(VOLUME) %(MNTPT)</cryptmount>

<nfsmount>mount %(SERVER):%(VOLUME) %(MNTPT)
	"%(before=\"-o\" OPTIONS)"</nfsmount>

<!-- mntcheck utility for BSDs which lack /etc/mtab -->
<mntcheck>mount</mntcheck>

<pmvarrun>pmvarrun -u %(USER) -o %(OPERATION)</pmvarrun>

<!--
Volumes that will be mounted when user triggers the pam_mount module
(usually at login).

    <volume
        user="*" | pgrp="foo" | sgrp="bar"
        invert="1"
        fstype="auto"
        server="..."
        path="..."
        mountpoint="..."
        options="..."
        fskeycipher="..."
        fskeypath="..."
    />


USER is a user for which a volume rule applies, "*" selects all users.

A volume with PGRP attribute will be mounted when a user has that
particular group as its primary group. A volume with SGRP attribute will
be mounted when the user has the group as either primary or secondary.

USER, PGRP and SGRP are mutually exclusive. If neither is present,
USER="*" is assumed.

INVERT will invert the sense of the USER, PGRP or SGRP selector, thereby
making it possible to specify, e.g. "all users not in group xyz".


FSTYPE can be any filesystem type. If /bin/mount or the kernel does not
support it, you will get an error. You can use the special keyword "auto"
which automatically lets the kernel choose a matching filesystem. Note
that the kernel's auto feature only works with currently loaded
filesystems (listed in /proc/filesystem), so you will have to load the
necessary modules _first_ for them to be recognized with "auto". If this
attribute is not present, "auto" is assumed.

The "cifs", "davfs", "smbfs", "ncpfs", "fuse" and "truecrypt" types
override the identically-named kernel filesystems and use the
helper programs as defined above.


SERVER defines the server from which to source. The exact volume path
depends on the filesystem type. SMB uses //SERVER/VOLUME, NFS uses
SERVER:VOLUME. davfs uses SERVER/VOLUME. The attribute may be absent.


PATH specifies the location of the volume, locally or on the server (if
applies), respectively. This attribute is mandatory.


MOUNTPOINT specifies the destination directory onto which the volume is
mounted. '~' expands to the user's home directory as present in the passwd
database, according to sh semantics. "~name" is not supported. If this
attribute is omitted, the location is read from /etc/fstab, which also
requires PATH to be the device of an fstab entry.


OPTIONS specifies mount options. If omitted, and /etc/fstab is used (see
MOUNTPOINT), then the options are also sourced from fstab.


Note that if the mount command has specified an option, e.g. %(KEYBITS)
and you do not specify a value, a warning is printed in the log. The
warning can usually be ignored, except when the option is mandatory.

SMB mounts require the `smbmount` and `smbumount` programs, NCP `ncpmount`
and `ncpumount`. Both SMB and NCP work in ~/.pam_mount.conf.xml.


General examples:

    <volume user="user" fstype="smbfs" server="krueger" path="public"
        mountpoint="/home/user/krueger" />

    <volume user="user" fstype="ncpfs" server="krueger" path="public"
        mountpoint="/home/user/krueger" options="user=user.context" />

    <volume fstype="smbfs" server="krueger" path="homes"
        mountpoint="/home/%(USER)/remote" options="dmask=0711" />

    <volume fstype="davfs" server="https://dev.computergmbh.de/"
        path="/svn/libHX/trunk" mountpoint="/projects/libHX" />

You can use ~ to use whatever home directory the user has (therefore you
can distribute home directories along more than one location. This is
useful for pam_chroot:

    <volume path="/bin" mountpoint="~/bin" options="bind" />

For FUSE mounts, use something like this:

    <volume fstype="fuse" path="sshfs#%(USER)@fileserver:"
        mountpoint="~" />

    <volume fstype="nfs" server="fileserver" path="/home/%(USER)"
        mountpoint="~" />

Some more examples:

    <volume path="/home/%(USER).img" mountpoint="~" fskeycipher="aes-256-ecb"
        fskeypath="/etc/ehd/%(USER)" />

Windows 2000, which requires a domain specified (does it really? works for
me without -jengelh), example (thanks John Knox):
-->
    <volume fstype="smbfs" server="192.168.3.240" path="%(USER)"
        mountpoint="~" options="workgroup=SUPERSTAR" />




<!--
Linux encrypted home directory examples, using dm_crypt:

crypt mounts require a kernel with CONFIG_BLK_DEV_DM and CONFIG_DM_CRYPT
enabled as well as all the used ciphers (e.g. CONFIG_CRYPTO_AES_586,
CONFIG_CRYPTO_TWOFISH, etc.). crypt mounts must be in the global config
file /etc/security/pam_mount.conf.xml.

Linux encrypted home directory examples, using dm_crypt:

    <volume fstype="crypt" path="/dev/sda2" mountpoint="/home/user"
        options="cipher=aes" fskeycipher="aes-256-ecb"
        fskeypath="/home/user.key" />

cryptoloop mounts require a kernel with CONFIG_BLK_DEV_CRYPTOLOOP enabled.
cryptoloop mounts must be in the global config
/etc/security/pam_mount.conf.xml. Linux encrypted home directory examples,
using cryptoloop:

    <volume path="/dev/hda123" mountpoint="/home/user"
        options="loop,encryption=aes" />

    <volume path="/home/user.img" mountpoint="/home/user"
        options="loop,user,exec,encryption=aes,keybits=256" />

    <volume path="/home/user.img" />

    <volume path="/home/user.img" fskeycipher="aes-256-ecb"
        fskeypath="/home/user4.key" />

The last two examples (^^) need a line like the following in /etc/fstab:

    /home/user4.img /home/user4 xfs user,loop,encryption=aes,keybits=256,noauto 0 0

OpenBSD encrypted home directory example (see also lclmount above):

    <volume path="/home/user.img" mountpoint="/home/user"
        options="svnd0" />

Volatile tmpfs mount with restricted size (thanks to Mike Hommey for this
example):

    <volume user="test" fstype="tmpfs" path="none" mountpoint="/home/test"
        options="size=10M,uid=test,gid=users,mode=0700" />

See http://www.tldp.org/HOWTO/Loopback-Encrypted-Filesystem-HOWTO.html to
learn how to create a encrypted loopback filesystem.

If the volume's password is different than the user's login password, the
following technique may be used (see also README):

{...} are placeholders, insert the proper value there!

1.  Create a file containing the volume's password (FS key). If you are
    using pam_mount to mount an loopback encrypted volume, this password
    should be generated with /dev/urandom.

    Simple example:
    echo {volume password} | openssl enc -aes-256-ecb >/home/user.key
    Encrypt this file using the user's login password as the key.

    Verbose loopback encrypted volume example:
    a.  dd if=/dev/urandom of=/home/user.img bs=1M count={image size in MB}
    b.  dd if=/dev/urandom bs=1c count={keysize/8} | \
        openssl enc -{fs key cipher} >/home/user.key
        Encrypt this file using the user's login password as the key.
    c.  modprobe -q cryptoloop
    d.  openssl enc -d -{fs key cipher} -in /home/user.key | \
        losetup -e aes -k {keysize} -p0 /dev/loop0 /home/user.img
    e.  mkfs -t ext2 /dev/loop0
    f.  losetup -d /dev/loop0

3.  In pam_mount.conf.xml:
        a.  Set the fs key cipher variable to the cipher used
            (ie: aes-256-ecb).
        b.  Set the fs key path variable to the key's path
            (ie: /home/user.key)

4.  If a user changes his login password, regenerate the efsk that was
    created in step 1b.  A script named passwdehd is provided to do this.

If FSKEYCIPHER is empty, then the user's login password is also the
volume's password.
-->

<!--
When pam_mount is not used with "use_first_pass" or "try_first_pass" in
the PAM configuration files (/etc/pam.d/), it will have to ask for a
password. This is also the case if pam_mount is the first auth module
in the block.
-->
<msg-authpw>pam_mount password:</msg-authpw>

<!--
In case the 'session' PAM block does not have the password (e.g. on su
from root to user), it will ask again.
-->
<msg-sessionpw>reenter password for pam_mount:</msg-sessionpw>

</pam_mount>


```

/etc/pam.d/common-auth:
```
auth    required        pam_mount.so
auth    sufficient      pam_winbind.so use_first_pass
auth    required        pam_unix.so nullok_secure use_first_pass
```

/etc/pam.d/common-session
```
session required        pam_mkhomedir.so umask=0022 skel=/etc/skel
session optional        pam_mount.so
```

/etc/krb5.conf
```
[libdefaults]
        default_realm = SUPERSTAR.LOCAL

# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true

# The following libdefaults parameters are only for Heimdal Kerberos.
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true

[realms]
        SUPERSTAR.LOCAL = {
                kdc = SUPERSTAR-SRV01.SUPERSTAR.LOCAL
                admin_server = SUPERSTAR-SRV01.SUPERSTAR.LOCAL
                default_domain = SUPERSTAR.LOCAL
        }
[domain_realm]
        .SUPERSTAR.LOCAL = SUPERSTAR.LOCAL
        SUPERSTAR.LOCAL = SUPERSTAR.LOCAL

[login]
        krb4_convert = true
        krb4_get_tickets = false
```

/etc/samba/smb.conf
```
[global]
        security = ads
        netbios name = Superstar-WKS01
        realm = SuperStar.local
        password server = SuperStar-SRV01.SuperStar.local
        workgroup = SuperStar
        idmap uid = 500-10000000
        idmap gid = 500-10000000
        winbind separator = +
        winbind enum users = no
        winbind enum groups = no
        winbind use default domain = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash
        client use spnego = yes
        domain master = no
```

/etc/nsswitch.conf
```
passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

When I do 'ls -alF' on /home/SUPERSTAR on the workstation it outputs this:
```
root@superstar-wks01:/home/SUPERSTAR# ls -alF
total 20
drwxr-xr-x  6 root          domain users 4096 2008-12-15 17:05 ./
drwxr-xr-x  5 root          root         4096 2008-12-13 17:08 ../
drwxr-xr-x  2 administrator domain users 4096 2008-12-15 11:57 administrator/
drwx------ 28 hverbeek      domain users    0 2008-12-15 18:11 hverbeek/
drwxr-xr-x  3 kkarbagenbonk domain users 4096 2008-12-15 16:09 kkarbagenbonk/
drwxr-xr-x  2 stephan       domain users 4096 2008-12-15 17:01 stephan/

```

When I do the same command on the appropriate dir on Openfiler (drive is formatted XFS):
```
[root@SuperStar-NAS01 test]# ls -alF
total 16
drwxrwxrwx   6 root          root           75 Dec 15 17:05 ./
drwxrwxrwx   5 root          root          135 Dec 14 16:06 ../
drwxrwxrwx   8 administrator domain users 4096 Dec 15 17:01 administrator/
drwx------  28 hverbeek      domain users 4096 Dec 15 18:11 hverbeek/
drwx------  22 kkarbagenbonk domain users 4096 Dec 15 16:21 kkarbagenbonk/
drwx------  23 stephan       domain users 4096 Dec 15 17:04 stephan/

```
(I've tried messing around with chmod to see if 777-rights would help (I know, really bad ;)) but that didnt really help either.

Also, this error occurs with all domain users on all workstations (I've got 2 workstations in a test-setup)

I'm convinced I'm pretty close to get this 100% working since the write access does already work, only the system can't really seem to understand that, and I can't understand what I'm missing here. Any help in this would greatly be appreciated!

---

### Post by Milenco on 2009-01-14
I'm still having difficulties with this issue. Does anyone have any suggestions on how I might fix this problem?

---

