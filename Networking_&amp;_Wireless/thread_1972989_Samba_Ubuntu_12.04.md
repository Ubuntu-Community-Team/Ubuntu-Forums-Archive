---
title: "Samba Ubuntu 12.04"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by xingular on 2012-05-04
Hello,

in a fresh installation of Ubuntu, always I open the Software Center and I install all the packets with the result "samba".
I reboot and inmediately I can access to the shared folders of the other computers of the home network.
But in 12.04... no. I can not see the Windows computers from Nautilus.

Problem? How can I solve this? Any start point? I don't have much knowledge of networks in Linux...

Many thanks!

---

### Post by lukeiamyourfather on 2012-05-04
The "Ubuntu Software Centre" is more of an "app" like store than a package manager because it doesn't show you all available packages, like those related to Samba. The Samba packages you're looking for are still in the repositories and can be installed with apt(-get), aptitude, Synaptic, or whatever other package manager you want to use.

---

### Post by Morbius1 on 2012-05-04
> in a fresh installation of Ubuntu, always I open the Software Center and I install all the packets with the result "samba".
I reboot and inmediately I can access to the shared folders of the other computers of the home network.
There's a couple of interesting points about that statement:

*** There's 2 parts to Samba: The server part and the client part. Ubuntu ships with the client part already installed so you shouldn't have to install anything to see the remote shares.

*** If you literally installed everything labeled "samba" then you installed Samba4 ( experimental ) and Samba3. One conflicts with the other so I'm not sure what you have.

---

### Post by xingular on 2012-05-04
At this time, all the packages "Samba" installed from Software Center are uninstalled (from Software Center too); and I can not "see" the other computers :(

---

### Post by xingular on 2012-05-09
That's the result of: /etc/samba/smb.conf

[global]
 netbios name = Samba24
 server string = Samba file and print server
 workgroup = workgroup
 security = user
 hosts allow = 127. 192.168.0.
 interfaces = 127.0.0.1/8 192.168.0.0/24
 bind interfaces only = yes
 remote announce = 192.168.0.255
 remote browse sync = 192.168.0.255
 printcap name = cups
 ; load printers = yes
 cups options = raw
 ; printing = cups
 ; guest account = nobody
 log file = /var/log/samba/samba.log
 max log size = 1000
 ; null passwords = no
 username level = 6
 password level = 6
 ; encrypt passwords = yes
 unix password sync = yes
 socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
 local master = no
 domain master = no
 ; preferred master = no
 ; domain logons = no
 os level = 33
 logon drive = m:
 logon home = \\%L\homes\%u
 logon path = \\%L\profiles\%u
 logon script = %G.bat
 ; time server = no
 name resolve order = wins lmhosts bcast
 ; wins support = no
 ; wins proxy = no
 dns proxy = no
 ; preserve case = yes
 ; short preserve case = yes
 client use spnego = no
 client signing = no
 client schannel = no
 ; server signing = no
 server schannel = no
 ; nt pipe support = yes
 ; nt status support = yes
 allow trusted domains = no
 obey pam restrictions = yes
 enable spoolss = yes
 ; client plaintext auth = no
 ; disable netbios = no
 follow symlinks = no
 update encrypted = yes
 ; pam password change = no
 passwd chat timeout = 120
 ; hostname lookups = no
 username map = /etc/samba/smbusers
 ; passdb backend = tdbsam
 passwd program = /usr/bin/passwd '%u'
 passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
 add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
 add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
 add group script = /usr/sbin/groupadd '%g'
 delete user script = /usr/sbin/userdel '%u'
 delete user from group script = /usr/sbin/userdel '%u' '%g'
 delete group script = /usr/sbin/groupdel '%g'
 add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
 machine password timeout = 120
 idmap uid = 16777216-33554431
 idmap gid = 16777216-33554431
 template shell = /dev/null
 winbind use default domain = yes
 winbind separator = @
 winbind cache time = 360
 winbind trusted domains only = yes
 winbind nested groups = no
 winbind nss info = no
 ; winbind refresh tickets = no
 ; winbind offline logon = no
 ; guest ok = no

[homes]
 comment = Home Directories
 path = /home
 valid users = %U
 read only = no
 ; available = yes
 ; browseable = yes
 ; guest ok = no
 ; printable = no
 locking = no
 strict locking = no

[netlogon]
 comment = Network Logon Service
 path = /var/lib/samba/netlogon
 read only = no
 ; available = yes
 ; browseable = yes
 ; guest ok = no
 ; printable = no
 locking = no
 strict locking = no

[profiles]
 comment = User Profiles
 path = /var/lib/samba/profiles
 read only = no
 ; available = yes
 ; browseable = yes
 ; guest ok = no
 ; printable = no
 create mode = 0600
 directory mask = 0700
 locking = no
 strict locking = no

[printers]
 comment = All Printers
 path = /var/spool/samba
 ; browseable = yes
 ; writable = no
 ; guest ok = no
 printable = yes
 locking = no
 strict locking = no

[pdf-documents]
 path = /var/lib/samba/pdf-documents
 comment = Converted PDF Documents
 admin users = %U
 ; available = yes
 ; browseable = yes
 writeable = yes
 guest ok = yes
 locking = no
 strict locking = no

[pdf-printer]
 path = /tmp
 comment = PDF Printer Service
 printable = yes
 guest ok = yes
 use client driver = yes
 printing = bsd
 print command = /usr/bin/gadmin-samba-pdf %s %u
 lpq command =
 lprm command =


Any idea?

---

### Post by Morbius1 on 2012-05-10
>  Any idea?     **Yes, don't ever use gadmin-samba again for as long as you live.**

smb.conf is used by the Samba server but also the Samba client so my recommendation is to start over again with a coherent smb.conf:

(1) Make sure the following file exists: /usr/share/samba/smb.conf

(2) Make another backup of your current smb.conf
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD
```(3) Start with a fresh one:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```(4) Correct one mistake in the new one: Find the line:
> encrypt passwords = falseand change it to:
> encrypt passwords = trueAnd add one more line to the [global] section - right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```(5) Restart samba
```
sudo service nmbd restart
sudo service smbd restart

```After you've done all that post the output of the following command:
```
smbtree
```

---

### Post by xingular on 2012-05-10
> After you've done all that post the output of the following command:
Code:
smbtree


It ask me for password, I entered password and nothing happends :P
But now I can acces to a folder called Workgroup and inside are the shared folders of this computer


Could be the name "WORKGROUP"? How can I know the name of the windows net?
I tryed "HOME" but nothing happends.

Thanks!

---

### Post by Morbius1 on 2012-05-11
Run the following command and see if you can access the shares on your Windows machine:
```
nautilus smb://192.168.0.100
```
[COLOR=Blue]*Changing 192.18.0.100 to the ip address of the Windows machine*[/COLOR].

If you cannot then disable the Windows firewall and try it again.

---

### Post by xingular on 2012-05-11
> **Morbius1 said:**
> Run the following command and see if you can access the shares on your Windows machine:
```
nautilus smb://192.168.0.100
```
[COLOR=Blue]*Changing 192.18.0.100 to the ip address of the Windows machine*[/COLOR].

If you cannot then disable the Windows firewall and try it again.

Yes! It works! But when I restart the PC it is not memorized and I have to do it again.

---

### Post by Morbius1 on 2012-05-12
> **xingular said:**
> Yes! It works! But when I restart the PC it is not memorized and I have to do it again.
2 options:

[1] Bookmark it

Run the command again:
```
nautilus smb://192.168.0.100
```
Then bookmark it: Bookmarks > Add bookmark

[2] Gigolo
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Gigolo will automount the remote shares when you log into your Ubuntu box.

---

### Post by waffler57 on 2012-07-01
> **Morbius1 said:**
> **Yes, don't ever use gadmin-samba again for as long as you live.**

smb.conf is used by the Samba server but also the Samba client so my recommendation is to start over again with a coherent smb.conf:

(1) Make sure the following file exists: /usr/share/samba/smb.conf

(2) Make another backup of your current smb.conf
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD
```(3) Start with a fresh one:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```(4) Correct one mistake in the new one: Find the line:
and change it to:
And add one more line to the [global] section - right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```(5) Restart samba
```
sudo service nmbd restart
sudo service smbd restart

```After you've done all that post the output of the following command:
```
smbtree
```

You rock! I've been plonking around for two weeks now trying (unsuccessfully) to network my wife's Windows PC to my Ubuntu -  and now two minutes after finding this thread we're back together again! ;)

---

