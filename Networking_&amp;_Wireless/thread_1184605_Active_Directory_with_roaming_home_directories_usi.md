---
title: "Active Directory with roaming home directories using Server 2003 R2 and up"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by ntrocks on 2009-06-11
This post will cover using Ubuntu 9.04 and Winbind to join an Active Directory domain served by Windows Server 2003 R2 or higher. I'll also describe a method of providing &#8220;roaming home directories&#8221;, having similar functionality to Windows' Roaming User Profiles. The idea is NOT to mount a remote home directory, but to have a local home and perform automatic synchronization on logon/logoff. I'm using Winbind because Likewise Open simply isn't flexible enough.

Although tested on Ubuntu, most of this will apply to other distros as well.

In the following, the AD domain is called kosmos.local

**[SIZE="6"]Windows configuration[/SIZE]**
I'll only cover the additional components you need for *nix interop. For the general stuff, there's plenty of resources on technet, notably:
[http://technet.microsoft.com/en-us/library/cc779189(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc779189(WS.10).aspx)
[http://technet.microsoft.com/en-us/library/cc757013.aspx](http://technet.microsoft.com/en-us/library/cc757013.aspx)
[http://technet.microsoft.com/en-us/library/cc738803(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc738803(WS.10).aspx)

Open up the Add/Remove Windows Components wizard. First, you need to install Active Directory Services > Identity Management for UNIX. If you want roaming home directories, select everything under Other Network File and Print Services > Microsoft Services for NFS besides Client for NFS, Server for NFS Authentication and User Name Mapping (you could probably use SFU together with rsync instead, but I didn't go there yet).

Then, open up Administrative Tools > Active Directory Users and Computers and assing the needed UNIX Attributes (in the object's properties).
-assign domains, GIDs to the selected groups
-assing domains, UIDs, home directories, primary groups, etc. to the selected users
-assign members to the previously selected groups
-you will also need to assign a NIS domain to each *nix computer that joins the domain.

Note1: These attributes can be edited programmatically, i.e. using LDAP. See also: [http://www.microsoft.com/technet/scriptcenter/scripts/ad/default.mspx?mfr=true](http://www.microsoft.com/technet/scriptcenter/scripts/ad/default.mspx?mfr=true)
[http://blogs.msdn.com/powershell/archive/2006/06/24/645876.aspx](http://blogs.msdn.com/powershell/archive/2006/06/24/645876.aspx)
[http://blogs.msdn.com/powershell/archive/2007/04/12/active-directory-cmdlets.aspx](http://blogs.msdn.com/powershell/archive/2007/04/12/active-directory-cmdlets.aspx)

Note2: I wasn't able to assign an UID of 0 to the Administrator account, winbind didn't like it.

Server for NFS setup (Tools > Microsoft Services for Network File System)

Open the properties of Microsoft Services for NFS. Select &#8220;Use Active Directory Lookup&#8221; and type in the DNS name of the domain.

Open the properties of Server for NFS. Go to the Filename Handling tab, select Translate file names, and use the following mapping:
```

0x00 0x5C : 0xF0 0x5C	; \ 
0x00 0x3A : 0xF0 0x3A	; : 
0x00 0x2A : 0xF0 0x2A	; * 
0x00 0x3F : 0xF0 0x3F	; ? 
0x00 0x22 : 0xF0 0x22	; " 
0x00 0x3C : 0xF0 0x3C	; < 
0x00 0x3E : 0xF0 0x3E	; > 
0x00 0x7C : 0xF0 0x7C	; | 

```
This is the same mapping that is used by SFU and Samba. The U+F0xx characters belong to a user-defined reserved range, so they won't break anything. This mapping allows *nix clients to use characters which are disallowed by Win32 (even if NTFS and the NT kernel handle them just fine. It's a relic from the bad old days of Fail 3.x/9x).

On the same tab, you'll probably want to enable case sensitive lookup and perhaps marking files beginning with a . as hidden.

NTFS is a case-sensitive file system, it's just the Win32 subsystem that's case insensitive. If you insist, you can enable case-sensitivity using the following trick:
```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\kernel]
"obcaseinsensitive"=dword:00000000

```
This way, *nix NFS clients will be able to create files with names differing only in case. Note however, that Win32 applications will generally be able to open only one of those files, unless they call native NT APIs instead of Win32.

Check this out:
[http://blogs.msdn.com/sfu/pages/sharing-folders-over-nfs.aspx](http://blogs.msdn.com/sfu/pages/sharing-folders-over-nfs.aspx)

To summarize, you need to create a client grup by typing:
```
nfsadmin server ServerName creategroup GroupName
```

And adding client computers: 
```
nfsadmin server ServerName addmembers GroupName Computer1 [, Computer2 &#8230; ]
```

We'll need to setup a share for the roaming home directories. Create a directory and share it over nfs. Use the NFS share permissions dialog to add the previously created client group and allow read/write access. The exact permissions are controlled using NTFS permissions. The minimum required permissions are almost like those described here:
[http://technet.microsoft.com/en-us/library/cc757013.aspx](http://technet.microsoft.com/en-us/library/cc757013.aspx)

The &#8220;Domain Users&#8221; group needs the following set of permissions:
Traverse Folder / Execute File
List Folder / Read Data
Read Attributes
Read Extended Attributes
Create Folders / Append Data
Read Permissions
Apply onto:  This folder only

CREATOR OWNER needs Full Controll, subfolders and files only.

(this assumes that you want the users' home directories to be automatically created, and not pre-created).

**[SIZE="6"]Ubuntu 9.04 configuration[/SIZE]**

Personally, I've found most of the online guides outdated, misleading and nearly useless. Here are the steps I've performed to get this working:

**1.Install kerberos**
But before, make sure Ubuntu is using the DNS server provided by Active Directory, either by specifying it manually (in /etc/resolv.conf or the NotworkManager), or by using DHCP. If you're albe to ping your primary domain controller by its fully qualified domain name, the setup should be fine.

Kerberos requires time synchronization between the servers and clients. Go to System > Administration > Time and Date and switch the configuration to &#8220;keep synchronized with blah&#8221;. Enter the address of your primary domain controller as the NTP server. (You might want to read [http://technet.microsoft.com/en-us/library/cc782712(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc782712(WS.10).aspx)).

The /etc/hosts file should have an entry like this:
127.0.0.1       ubuntu-1.kosmos.local ubuntu-1 localhost.localdomain localhost 
The first thing after 127.0.0.1 is the localhost's fully qualified domain name, or FQDN (the computer is called ubuntu-1, as defined in /etc/hostname).

Having done that,  it's time to install and configure the krb5-user package and dependencies.
A bare minimal /etc/krb5.conf will look like this:
```

[logging]
    default = FILE:/var/log/krb5.log

[libdefaults]
    default_realm = KOSMOS.LOCAL

[realms]
    KOSMOS.LOCAL = {
        default_domain = KOSMOS.LOCAL
    }

[domain_realm]
    .kosmos.local = KOSMOS.LOCAL

[appdefaults]
    pam = {
        forwardable = true
    }


```
Yup, that's all. You don't need to specify the kdc addresses if the DNS is properly configured, and MS docs about AD networks segmented with firewalls don't mention anything about a kerberos admin server, so it's probably not even there (or isn't used by AD).
As always, check out man krb5.conf for more info.

Test the configuration by typing kinit UserName. There should be no errors. Cleanup using kdestroy.

**2.Install samba and winbind.**
You want the samba, winbind, smbfs and smbclient packages. You'll want /etc/samba/smb.conf to look something like this:
```

[global]
security = ads
realm = KOSMOS.LOCAL
workgroup = KOSMOS
use kerberos keytab = yes
auth methods = winbind guest sam
local master = no

idmap config KOSMOS : backend  = ad
idmap config KOSMOS : range = 10000-20000
idmap config KOSMOS : schema_mode = rfc2307

winbind nss info = rfc2307

winbind enum users = yes
winbind enum groups = yes
winbind refresh tickets = yes
winbind use default domain = yes

client use spnego = yes
client ntlmv2 auth = yes

encrypt passwords = yes
restrict anonymous = 2

socket options = TCP_NODELAY

```
see man smb.conf and man idmap_ad for explanations.
There's also the new adex idmap backend that's a replacement for ad, but I haven't been able to get it working.

You might want to disable winbind's cache, at least for the time being. It'll help to avoid nasty problems related to using stale information during these early configuration stages. You can do this by adding the line:
WINBINDD_OPTS=-n
somewhere at the beginning of /etc/init.d/winbind

Now set up /etc/nsswitch.conf. Add winbind on the passwd and group lines and make sure dns is the second thing on the hosts line, i.e.:
```

passwd:         compat winbind 
group:          compat winbind 
shadow:         compat 

hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4 
(other stuff follows)

```

After that's done, restart winbind:
```
sudo /etc/init.d/winbind restart
```

You should be ready to join the domain now. Type:
```
sudo net ads join -U Administrator
```
If you get a message about a failed DNS update, this means the /etc/hosts file is not properly set up. The fully qualified domain name must be the first thing after 127.0.0.1.

Test by typing wbifo -u, wbinfo -g, getent passwd, getent group. All these should report Active Directory users and groups.

If you'll restart your system now, you'll probably notice just as I have that winbind stopped working. You can get it back up by restarting it, but this shouldn't be happening and needs to be fixed before we proceed. This means it's time for...

**3.Fixing the service startup order and network configuration.**
As it turns out, winbind and samba are by default started BEFORE networking. This makes them go stupid, and they continue to be stupid even after the network becomes available. Winbind also seems to have problems if the network comes down for some other reason at a later time. This second fact implies that it would be appropriate to add an ifup hook for winbind. To do this, simply put this script at /etc/network/if-up.d/winbind:
```

#!/bin/sh

status="`/etc/init.d/winbind status 2> /dev/null`"
if [ "$status" = ' * winbind is running' ]; then
	/etc/init.d/winbind restart >/dev/null 2>&1
fi

exit 0

```

This is a workable setup, but samba's logs will still be littered with error messages about the initial network-less period. To fix this, networking needs to start first. We can change the service start/stop priorities using System > Administration > Services or (better) BUM (The Boot-Up Manager). 

In Jaunty, the default startup priority for samba and winbind is 20, networking &#8211; 40 and the NetworkManager &#8211; 50. Also of note is gdm, which starts before all of the above with a priority of 14. Taking that into account, we might move samba and winbind to, say, 55. Later, we're also going to need networking and winbind available by the time gdm starts, so let's give gdm an even bigger number, like 80.

Ok, so now we're done, right? No. It turns out that the NotworkManager messes everything up and refuses to start the network interfaces immediately, even if they're set to auto. If using a wired connection, the restart script above will make this setup workable, but it seems that wireless interfaces are enabled only after logon, which is unacceptable. The only Final Solution to the NotworkManager Problem I've found is to purge it from the system. Just get rid of all the network-manager* and libnm-* packages and setup your interfaces using the plain old /etc/network/interfaces file. It might be as simple as adding:
```

auto eth0
iface eth0 inet dhcp

```

More info here: [https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html)

Note that this means that the startup priorities for samba/winbind can be lower, say 45.

**4.PAM based authentication**
This step should be quick. Put the following at /usr/share/pam-configs/winbind:
```

Name: Winbind authentication
Default: yes
Priority: 255
Auth-Type: Primary
Auth:
	[success=end default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE try_first_pass
Auth-Initial:
	[success=end default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE
Account-Type: Primary
Account:
	[success=end new_authtok_reqd=done default=ignore]	pam_winbind.so
Account-Initial:
	[success=end new_authtok_reqd=done default=ignore]	pam_winbind.so
Session-Type: Additional
Session:
	required pam_mkhomedir.so umask=0022 skel=/etc/skel
Session-Initial:
	required pam_mkhomedir.so umask=0022 skel=/etc/skel

```


Just sudo pam-auth-update and make sure winbind is selected. Press OK and test. You should be able to login using the active directory accounts using su and the gdm login screen (thanks to step 3). When logging in, type the user names in lower case (just as they show up in wbinfo -u).

**5.Roaming home directories**
For this, you'll need to install nfs-common, autofs and rsync. You'll also need pam_script:
[http://sourceforge.net/project/showfiles.php?group_id=133192](http://sourceforge.net/project/showfiles.php?group_id=133192)
There's a i386 .deb available under that address.
Oh, you'll also want gcc standing by.

First, set up autofs to mount the nfs share (an alternative is to do a setuid on mount.nfs and use it directly in the scripts below).

```
sudo mkdir /.roamers
```
Edit /etc/auto.master and add:
```
/.roamers /etc/auto.roamers &#8211;timeout=60
```

Create /etc/auto.roamers:
```

kosmos -rw,hard,intr,rsize=8192,wsize=8192 PDC.kosmos.local:/.home

```

(of course, the names are specific to my setup)

sudo /etc/init.d.autofs restart, su to an active directory account and check if the share is available. If you're getting permission errors, most likely the ntfs permissions are set incorrectly.

The problem with scripts ran by pam-script is that they'll be executing with a different EUID depending on the context, but it should always be either 0 or of the user being authenticated. We need the latter. With an EUID of 0 we can change it to whatever we want, but we can't use sudo (sudo uses pam itself, and that would result in some sort of recursive authentication. If we try hard enough, we might end up with infinite recursion here, so it's better to steer clear off that path).

What else can we use? I didn't know of any command that I could use inside a script, so I decided to write this tiny little c program:
```

#include <sys/types.h>
#include <pwd.h>
#include <unistd.h>

int main(int argc, char *argv[])
{
	struct passwd *pwd;

	if(argc < 3 || !(pwd = getpwnam(argv[1])) ||
	   setregid(pwd->pw_gid, pwd->pw_gid) ||
	   setreuid(pwd->pw_uid, pwd->pw_uid))
		return 1;

	execvp(argv[2], argv + 2);

	return 1;
}


```

This program will succeed only if is's running as root or the target user.

While we're at it, we might fix a problem that pam_mkhomedir has &#8211; it requires root privileges during authentication, which aren't always available. We'll solve this with another small program, which makes sure that the user's home directory exists. This program will have the setuid flag set.
```

#include <sys/types.h>
#include <sys/stat.h>
#include <unistd.h>
#include <pwd.h>
#include <ctype.h>
#include <errno.h>
#include <string.h>

int main(int argc, char *argv[])
{	
	struct passwd *pw;
	struct stat s;
	char *home, *p;

	if(argc != 1)
		return 1;

	/* there is no command line args: using the current real UID */
	pw = getpwuid(getuid());

	if(!pw)
		return 1;

	home = pw->pw_dir;
	if(*home == 0)
		return 1; /* no home dir */

	if(stat(home, &s) == 0)
		return 0; /* already exists */

	p = home + 1;
	while(p = strchr(p, '/')) {
		*p = 0;
		if(mkdir(home, 0755) && (errno != EEXIST))
			return 1;
		*p++ = '/';
	}

	if(mkdir(home, 0755) == 0) {
		if(chown(home, pw->pw_uid, pw->pw_gid))
			return 1;
	} else if(errno != EEXIST)
		return 1;	

	return 0;
}

```

These can be built like this:
```

gcc -O2 execas.c -oexecas
gcc -O2 mkhomedir.c --omkhomedir

```

Now it's time for the scripts:
pam_script_ses_open:
```

#!/bin/bash -p

USER_INFO=`wbinfo -i "$PAM_USER" 2> /dev/null`
if [ $? -ne 0 ]; then
	exit 0
fi

home="`echo "$USER_INFO" | cut -d : -f 6`"

cd "`dirname "$0"`"

./execas "$PAM_USER" ./session_open "$home"

```

session_open:
```

#!/bin/bash

mode='u+rwX,g-rwx,o-rwx'
skel=/etc/skel

src="${1/home/.roamers}"
dst="$1"

if [ -d "$src" ]; then
	./mkhomedir
	if [ $? -ne 0 ]; then
		exit $?
	fi

	rsync -rulptogO "$src/" "$dst"
elif [ ! -d "$dst" ]; then
	./mkhomedir
        if [ $? -ne 0 ]; then
                exit $?
        fi
	
	shopt -s dotglob
	cp -a "$skel"/* "$dst"
	chmod -R "$mode" "$dst"
fi

```

pam_script_ses_close:
```

#!/bin/bash -p

USER_INFO=`wbinfo -i "$PAM_USER" 2> /dev/null`
if [ $? -ne 0 ]; then
	exit 0
fi

home="`echo "$USER_INFO" | cut -d : -f 6`"

cd "`dirname "$0"`"

./execas "$PAM_USER" ./session_close "$home"

```

session_close:
```

#!/bin/bash

src="$1"
dst="${1/home/.roamers}"

rsync -rlptogO --delete "$src/" "$dst" 

```

Place the scripts and executables in some convenient place, i.e. /etc/adauth, and don't forget to:
```
sudo chmod u+s /etc/adauth/mkhomedir
```

We have to modify /usr/share/pam-configs/winbind a little bit:
```

Name: Winbind authentication
Default: yes
Priority: 255
Auth-Type: Primary
Auth:
	[success=end default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE try_first_pass
Auth-Initial:
	[success=end default=ignore]	pam_winbind.so krb5_auth krb5_ccache_type=FILE
Account-Type: Primary
Account:
	[success=end new_authtok_reqd=done default=ignore]	pam_winbind.so
Account-Initial:
	[success=end new_authtok_reqd=done default=ignore]	pam_winbind.so
Session-Type: Additional
Session:
	required	pam_script.so dir=/etc/adauth
Session-Initial:
	required	pam_script.so dir=/etc/adauth

```

Update PAM config files using pam-auth-update.
	
That should be most of it, folks.

**Finishing touches:**
You might want to use pam_group to assign all the AD users to a common set of local groups, like cdrom, plugdev, etc.

You might also want to add the &#8220;Domain Admins&#8221; AD group to sudoers. Note that you need to escape the ' ' as '\ ', rename the group to exclude the space, or enable name normalization in smb.conf (by adding winbind normalize names = yes, see man smb.conf)

If you disable the &#8220;use default domain&#8221; option and leave the default separator character '\', you'll need to escape it in the console, i.e. su DOMAIN\\user

---

