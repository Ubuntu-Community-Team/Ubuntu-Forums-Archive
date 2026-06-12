---
title: "smbclient fails with &quot;SPNEGO login failed: Invalid parameter&quot; from Windows 7"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by markhor2 on 2010-06-04
Hello, guys.

I experience the following issue (it is the same as  [here]("http://www.pubbs.net/201001/samba/53691-samba-windows-7-share-and-smbclient.html")).

I have a Windows 7 PC and a Lucid laptop. My PC has some shared folders (e.g. "Pictures") and password-less access. Let my PC's host name be "NASTYA". Command
```
smbmount //NASTYA/Pictures /media/Share -o guest
```
works fine and I get the contents of that share, browse and view photos.

However, when I try to execute
```
smbclient -L NASTYA -N
```
it fails with "Error returning browse list: NT_STATUS_ACCESS_DENIED" message.

Here is the complete output:
```
smbclient -L NASTYA -N -d4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter client lanman auth = Yes
doing parameter workgroup = workgroup
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
doing parameter security = share
doing parameter guest ok = yes
pm_process() returned Yes
added interface wlan0 ip=fe80::226:5eff:fe2f:e532%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.10 bcast=192.168.0.15 netmask=255.255.255.240
Client started (version 3.4.7).
Connecting to 192.168.0.14 at port 445
 session request ok
Doing spnego session setup (blob length=336)
SPNEGO login failed: Invalid parameter
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]
 session setup ok
 tconx ok

	Sharename       Type      Comment
	---------       ----      -------
NetShareEnum failed
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

```

So you can see here that it drops SPNEGO login. Incorrectly parses the response I guess. That command fails even if execute "-U [PC's user name] -p" and enter the correct password.

Maybe we could fix the problem together?

Links to likely similar discussions:
[http://forums.fedoraforum.org/archive/index.php/t-237359.html]("http://forums.fedoraforum.org/archive/index.php/t-237359.html")
[http://ubuntuforums.org/showthread.php?t=1333542]("http://ubuntuforums.org/showthread.php?t=1333542")

---

### Post by Jeroensum on 2010-06-04
The -N option represses the password prompt, effectivly trying a 'null-session' to the windows box. afaik windows 7 doesn't allow null-sessions anymore due to security problems. Don't confuse this however with published shares.
Without the -N it should try a connection with your current username and ask you for a password, which, when set, should allow you to scan the box.

---

### Post by markhor2 on 2010-06-04
Finally I figured it out, thanks. That is,

smbclient -L NASTYA -U UserTest%passwd

works! UserTest is a new user I created with password passwd. However, my Windows 7 had originally a user in Russian letters, "&#1053;&#1072;&#1089;&#1090;&#1103;", and smbclient refused to work with such user. I am going to investigate this further. Seems like russian user names are not supported by smbclient.

Also, how do you explain that smbmount works without asking any user name or password, using guest mode?

---

### Post by Jeroensum on 2010-06-05
> **markhor2 said:**
> Finally I figured it out, thanks. That is,

smbclient -L NASTYA -U UserTest%passwd

works! UserTest is a new user I created with password passwd. However, my Windows 7 had originally a user in Russian letters, "&#1053;&#1072;&#1089;&#1090;&#1103;", and smbclient refused to work with such user. I am going to investigate this further. Seems like russian user names are not supported by smbclient.

Also, how do you explain that smbmount works without asking any user name or password, using guest mode?

SMB/CIFS only works with unicode characters, no need for investigations there, it's in the specs ;-)

Second question is easily explained aswell, when you used Guest-mode you **did** provide a username: *guest*, that is what guestmode does, check your windows box and you'll find an account acutally named 'guest' which is used for this specific purpose. (again, it's in the specs and works by design) :)
When you setup a null-session there are no usernames/passwords used at all. That's the difference :)

---

