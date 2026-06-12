---
title: "Unable to Windows Network via File Browser"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by XenoWolf on 2010-08-11
If this has already been solved, please just point me to the correct thread.

I am new to Linux and decided on trying out Ubuntu. Love it so far. Running Ubuntu 64-bit 10.04 on a Toshiva Satellite L300. Network browsing worked fine to both my other machines (one running XP, the other Win7). The next day I switched the laptop on, the other two systems don't show automatically in the File Browser under Network like they used to. It now only shows a Windows Network icon which, when I click on it, gives the following error: Unable to mount location, Failed to retrieve share list from server.

Strangely enough, I can access the machines' shared folders perfectly through the terminal using smbclient.

What happened and can someone help me fix it?

---

### Post by Morbius1 on 2010-08-11
That's interesting - works one day and not the next. What happens when you try to access it directly:

From a terminal try both of these:
```
nautilus smb://machine_name
nautilus smb://machine_name/share_name
```You also might see what kind of error messages you get when you issue this command:
```
smbtree
```

---

### Post by Morbius1 on 2010-08-11
I've got to shut down for the day so let me leave you with this temporary workaround if those "nautilus smb://" commands work: Bookmark it.

If they connect or if they can connect by ip address for example:
```
nautilus smb://192.168.0.100
```Then go to Bookmarks > Add Bookmark in Nautilus.

It will show up on the bottom of the left side panel of Nautilus sort of like a "mapped drive" does in Windows.

---

### Post by XenoWolf on 2010-08-12
:DOk, thankyou! That works. I can access the machines.:D

Any way of getting my automatic network discovery back in Nautilus perhaps?

---

### Post by Morbius1 on 2010-08-12
You know there are about 152 reasons for getting "Unable to mount location, Failed to retrieve share list from server". You can induce that error at will just by blocking the samba ports on the server or client firewalls for example. The usual "fixes" focus on the network as the cause but I don't think that this is your problem because it worked perfectly 24 hours earlier. I've noticed some anomalies myself when using Nautilus to browse network shares - I get a blank screen and have to hit the refresh button literally about a dozen times before the remote boxes show up. I'm beginning to think that Nautilus itself is contributing to these errors.

You could, as an experiment, install **gigolo**. It's a network browser + mounter that uses the same exact underlying commands as nautilus but has the advantage of  .. well ... not being Nautilus.

When you bring up gigolo for the first time enable the side panel:
Select the "View" button:
enable: "Toolbar", "Side Panel", and "Status Icon"
Then click on the "Network" tab on the side. It will eventuall show you all the networks workgroups and all the shares within those workgroups. If you can see it in gigolo and not in Nautilus then I suspect Nautilus has some kind of bug.

gigolo is a very impressive ( and misunderstood ) little application that can do some extraordinary things: you can have it launch minimized to the panel at startup, you can have it automount remote shares at login, you can even have it automount a remote share and wait for the remote box to to become available before it mounts - in case the remote box has not booted yet.

Sorry , this was more a rant than an answer

---

### Post by 54Rigger on 2010-08-12
Xeno,  there is a file on your computer that can be found at

/etc/samba/smb.conf

it is a configuration file for the windows networking portion of ubuntu.   please post the contents of that file,  if you want to shorten the post,  you can delete any line that starts with a #

Rig

---

### Post by XenoWolf on 2010-08-12
Thanks for the reply guys.

- Morbius1

I installed Gigolo. Same thing as Nautilus. When I go the network I still cant see any machines with shares or even work*****s for that matter.

- 54Rigger

Ok, I deleted the stuff with the # and maybe some spaces between paragraphs too by accident, but here are the contents:

[global]
;   wins server = w.x.y.z
   dns proxy = no
;   name resolve order = lmhosts host wins bcast
;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon drive = H:
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add ***** script = /usr/sbin/add***** --force-badname %g
;   printing = bsd
;   printcap name = /etc/printcap
;   printing = cups
;   printcap name = cups
;   include = /home/samba/etc/smb.conf.%m
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum *****s = yes
;   winbind enum users = yes
;   usershare max shares = 100
;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin

;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by Morbius1 on 2010-08-12
> **XenoWolf said:**
> :DOk, thankyou! That works. I can access the machines.:D
When you where successful did you access it by name:
```
 nautilus smb://machine_name
```
Or by ip address:
```
 nautilus smb://192.168.0.100
```

---

### Post by XenoWolf on 2010-08-12
When I try to access a machine via computer name in the terminal with nautilus, I get an error:

Could not display "smb://mymachine/".
Error: Failed to retrieve share list from server
Please select another viewer and try again

When I access any one of the two machines by their IP, it works.

---

### Post by capscrew on 2010-08-12
> **Morbius1 said:**
> When you where successful did you access it by name:
```
 nautilus smb://machine_name
```
Or by ip address:
```
 nautilus smb://192.168.0.100
```

This is a name service problem.  You probably have a firewall blocking the Samba ports.

---

### Post by Morbius1 on 2010-08-12
I simply don't understand how all of this worked 48 hrs ago and now it doesn't. You didn't change anything on the network?  - add a new device or change any settings on the Windows machines or the router?

The problem is netbios name resolution - converting a machine name to a ip address. One way around this is basically to create a lookup table that matches an ip address to the machine name. The file already exits at /etc/hosts and you would specify the ip address followed by the corresponding machine name. Something like this:
> 127.0.0.1    localhost
127.0.1.1    morbius
[COLOR=Blue]192.168.0.100 winxp
192.168.0.101 win7[/COLOR]
#88.191.101.8 packages.medibuntu.org

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhostsThere's four problems with this:
(1) You're really not browsing the network anymore. Nautilus will only see those machines that are in the hosts file.

(2) Not going to work unless all of the other machines have fixed ip addresses.

(3) All new machines will have to also have a fixed ip address and be added to the hosts file.

(4) Functionally, you really have that already with your bookmarks - open nautilus, click on the bookmark, and you see that machines shares.

But it should fix the "not showing up under Network in Nautilus" problem.

[COLOR=Blue]EDIT: Forgive me capscrew for stepping on your post.[/COLOR]

---

### Post by XenoWolf on 2010-08-12
On my Ubuntu system or both of the Windows systems?

Now that you have mentioned firewall, I did install firestarter around the time this problem started. Strange enough, when I disable the firewall with firestarter, it still won't work. Do you think perhaps the install of firestarter might have had a significant change to the system?

---

### Post by capscrew on 2010-08-12
> **Morbius1 said:**
> I simply don't understand how all of this worked 48 hrs ago and now it doesn't. You didn't change anything on the network?  - add a new device or change any settings on the Windows machines or the router?

The problem is netbios name resolution - converting a machine name to a ip address. One way around this is basically to create a lookup table that matches an ip address to the machine name.
Actually the nmbd daemon converts the hostname to a netbios name and then matches it.  Hostnames are not netbios names.> 
The file already exits at /etc/hosts and you would specify the ip address followed by the corresponding machine name. Something like this:
There's four problems with this:
(1) You're really not browsing the network anymore. Nautilus will only see those machines that are in the hosts file.

(2) Not going to work unless all of the other machines have fixed ip addresses.

(3) All new machines will have to also have a fixed ip address and be added to the hosts file.

(4) Functionally, you really have that already with your bookmarks - open nautilus, click on the bookmark, and you see that machines shares.

But it should fix the "not showing up under Network in Nautilus" problem.

[COLOR=Blue]EDIT: Forgive me capscrew for stepping on your post.[/COLOR]

No problem. We can overcome the dynamic hostname to IP mapping by using a DNS server that uses dynamic mapping.  DNSmasq is great or this.  But in all fairness a WINS server will also work, but  ONLY FOR NETBIOS NAME resolution (.e.g. for SMB file sharing only).

---

### Post by Morbius1 on 2010-08-12
Ah, firestarter. Ignore my last post and follow capscrew.

---

### Post by capscrew on 2010-08-12
> **XenoWolf said:**
> On my Ubuntu system or both of the Windows systems?

Now that you have mentioned firewall, I did install firestarter around the time this problem started. Strange enough, when I disable the firewall with firestarter, it still won't work. Do you think perhaps the install of firestarter might have had a significant change to the system?

It takes a few minutes for the "browse list" to be created.  Be patient.

---

### Post by Morbius1 on 2010-08-12
This comment is based on anecdotal evidence only but I have helped three people with a problem similar to yours and it was only resolved when firestarter was uninstalled. Disabling firestarter was not enough.

I never investigated it to determine what the problem was or how a disabled firewall configuration app could be the source of the problem but once it was gone everything returned to normal.

---

### Post by XenoWolf on 2010-08-12
Ok, no matter how long I wait, it still does not crate the list. But, please excuse me for asking this, I am new to Linux, but is there a link I can follow or a post explaining to me step by step how to do the WINS server thing or DNSmasq you talked about, Capscrew?

---

### Post by XenoWolf on 2010-08-12
- Morbuis1

Ok, I presume then that firestarter is the problem. I can connect to the machines the way you showed me, so I guess it is not that much of a problem if I want firestarter and have to make favourites for the connections. At least I now know how. Thanks. :)

- Capscrew

If what you mentioned earlier will work, can you please still post the link or the steps I have to take?

Thanks for the help so far guys. I really appreciate it.

---

### Post by capscrew on 2010-08-12
> **XenoWolf said:**
> Ok, no matter how long I wait, it still does not crate the list. But, please excuse me for asking this, I am new to Linux, but is there a link I can follow or a post explaining to me step by step how to do the WINS server thing or DNSmasq you talked about, Capscrew?

The SMB protocols are not trivial.  It is complicated and Samba is only part of the deal.  The best newbie howto is [**_Samba by Example_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  This will take you from basic to complex.  

I don't really know how to "insert' one piece of knowledge (i.e Wins server) without you having the supporting  knowledge.  No throwing everything against the wall and seeing what sticks.  ;-)

---

### Post by XenoWolf on 2010-08-13
Ok, thanks! :)

Thanks for all the help guys!

---

