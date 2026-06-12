---
title: "can't see windows workgroup pcs"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by WildeBeest on 2009-06-14
Jaunty

I can't see any windows pcs in my workgroup.

When I select Places>Network nautilus displays the workgroup name.
Clicking on that shows none of my Windows pcs.

I have it working in Hardy and have Jaunty configured the same as Hardy.

I can ping all the Windows pcs on my network and Jaunty from the windows machines.
The windows pcs can see and access the shares I setup with samba.
I also have a printer connected to Jaunty that's shared and all the windows pcs can print to it.

Anyone have any ideas?

---

### Post by superprash2003 on 2009-06-14
try this [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by WildeBeest on 2009-06-14
The recommended changes to the smb.conf and nsswitch.conf did not work.
The system hung on boot at the start samba daemons.

---

### Post by Iowan on 2009-06-14
Did you run **testparm** to check for errors in */etc/samba/smb.conf*?

---

### Post by WildeBeest on 2009-06-16
I ran testparm and there were no errors.  Just one warning.

WARNING: The "printer admin" option is deprecated

---

### Post by WildeBeest on 2009-07-02
Still have the problem... ](*,)

---

### Post by superprash2003 on 2009-07-02
do you use firestarter? i think the guide clearly mentioned the problem with firestarter..

---

### Post by dmizer on 2009-07-02
Please post your smb.conf file.

---

### Post by WildeBeest on 2009-07-02
```
[global]
    ; General server settings
    netbios name = wes-office-p4
    server string =
    workgroup = HOMENET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = lmhosts hosts wins bcast
;    name resolve order = hosts wins bcast

;    wins support = no

    load printers = yes
    printing = cups
    printcap name = cups

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
;[print$]
;    path = /var/lib/samba/printers
;    browseable = yes
;    guest ok = yes
;    read only = yes
;    write list = root
;    create mask = 0664
;    directory mask = 0775
[print$]
comment = Printer Drivers
path = /etc/samba/drivers
browseable = yes
guest ok = yes
read only = yes
write list = root

;[printers]
;    path = /tmp
;    printable = yes
;    guest ok = yes
;    browseable = no
[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
public = yes
guest ok = yes
writable = no
printable = yes
printer admin = root, wildebeest

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = wildebeest
    ;force group = wildebeest

[ShareDrive]
    path = //media/Share_disk/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = wildebeest
    ;force group = wildebeest

```

---

### Post by WildeBeest on 2009-07-02
> **superprash2003 said:**
> do you use firestarter? i think the guide clearly mentioned the problem with firestarter..

Don't use it, unless it runs automatically.

---

### Post by dmizer on 2009-07-02
Okay, I see several problems, I'll try to address them all.

1) Remove all the printer stuff and share your printer through CUPS instead. That should solve the warning you get on boot.

2) Your "MyFiles" share configuration isn't possible, and even if it was possible, it's dangerous. You need something more like this:
```
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/
```
That way all your sensitive files are not exposed. But I still suggest sticking to a dedicated shared folder rather than sharing your entire home directory.

3) On your ShareDrive configuration, your path has two "//" in it. Remove one.

4) Remove these two options: "announce version = 5.0" and "server string ="

Try that.

---

### Post by WildeBeest on 2009-07-03
2. Your "MyFiles" share configuration isn't possible

It is possible, because my Windoze machines can see and access the share.

I did 1-4 and I still can't see the Windoze machines. I do get the "Windows Network" icon, but when I open it there is nothing there.

When I run Hardy, with the exact same smb.conf, it works just fine.

There must be something Jaunty specific that will resolve this.

---

### Post by dmizer on 2009-07-03
Okay, then take a look at the 6th link in my sig.

---

### Post by WildeBeest on 2009-07-03
I followed your 6th link guide before, no success.
When I add wins to the nsswitch.conf file (as below) the system hangs when starting samba during boot.

 hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]wins[/COLOR] dns mdns4

There is no firewall enabled.
Winbind is installed.

---

### Post by dmizer on 2009-07-03
Are you running DHCP or static IP?

Edit:
Also, try the following smb.conf file. First make a backup of your current working smb.conf with this command
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-backup
```
Then replace what's there with this:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

   workgroup = HOMENET
   netbios name = wes-office-p4
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

   name resolve order = lmhosts host wins bcast

#### Networking ####

    interfaces = lo, eth0
    bind interfaces only = yes

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n*password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Printing ##########

   load printers = yes
   printing = cups
   printcap name = cups

############ Misc ############

   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   usershare allow guests = yes

#======================= Share Definitions =======================

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   admin users = root, wildebeest

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

[ShareDrive]
    path = //media/Share_disk/
    browseable = yes
    read only = no
    guest ok = yes
```

I've removed the [MyFiles] configuration because it's really really dangerous. If the above smb.conf allows you to boot with the winbind daemon enabled, then we'll talk about how to share your home directory properly.

Also, please post the output (if any) of:
```
sudo /etc/init.d/winbind restart
```

---

### Post by WildeBeest on 2009-07-04
DHCP

sudo /etc/init.d/winbind restart
 * Stopping the Winbind daemon winbind                                   [ OK ] 
 * Starting the Winbind daemon winbind                                   [ OK ]

I restarted samba and still does not work

---

### Post by dmizer on 2009-07-04
What do you mean by "it still doesn't work?" Are you at least able to boot without having your machine hang at this point?

Please post the output of:
```
smbtree
```

Also, does testparm complete without error now?

---

### Post by WildeBeest on 2009-07-04
Boot does not hang.

```
smbtree
Password: 
HOMENET
    \\WES-OFFICE-P4          wes-office-p4 server (Samba, Ubuntu)
cli_start_connection: failed to connect to WES-OFFICE-P4<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
    \\TOMS-LAPTOP            
    \\DOE-OFFICE-P4          Office P4 III
        \\DOE-OFFICE-P4\C$                 Default share
        \\DOE-OFFICE-P4\ADMIN$             Remote Admin
        \\DOE-OFFICE-P4\Doe                
        \\DOE-OFFICE-P4\C                  
        \\DOE-OFFICE-P4\print$             Printer Drivers
        \\DOE-OFFICE-P4\IPC$               Remote IPC

```

testparm

```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[ShareDrive]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = HOMENET
    server string = %h server (Samba, Ubuntu)
    interfaces = lo, eth0
    bind interfaces only = Yes
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n*password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = lmhosts host wins bcast
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    admin users = root, wildebeest
    create mask = 0700
    guest ok = Yes
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    guest ok = Yes

[ShareDrive]
    path = //media/Share_disk/
    read only = No
    guest ok = Yes

```

---

### Post by dmizer on 2009-07-04
Well, at least we have your boot problem fixed.

I want to try one small change as a temporary test. This will not be permanent, but I think I know what the problem is now. Try commenting out the "security = user" option, restart samba, and try browsing your shares again.

---

### Post by WildeBeest on 2009-07-05
Still can't browse any shares.

---

### Post by dmizer on 2009-07-05
What is the output of smbtree now (with the change in place)?

---

### Post by WildeBeest on 2009-07-05
smbtree

```
HOMERNET
    \\WES-OFFICE-P4          wes-office-p4 server (Samba, Ubuntu)
cli_start_connection: failed to connect to WES-OFFICE-P4<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
    \\TOMS-LAPTOP            
    \\DOE-OFFICE-P4          Office P4 III
        \\DOE-OFFICE-P4\C$                 Default share
        \\DOE-OFFICE-P4\ADMIN$             Remote Admin
        \\DOE-OFFICE-P4\Doe                
        \\DOE-OFFICE-P4\C                  
        \\DOE-OFFICE-P4\print$             Printer Drivers
        \\DOE-OFFICE-P4\IPC$               Remote IPC

```

---

### Post by WildeBeest on 2009-07-05
I rebooted and "smbtree" ran without any output.

---

### Post by dmizer on 2009-07-05
Well, I've personally run into this problem before. You're getting this error:
```
cli_start_connection: failed to connect to WES-OFFICE-P4<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
```
But since the share is set up for guest access, you shouldn't getting that error. Something's still set up strange in smb.conf, but I'm not sure what.

---

### Post by WildeBeest on 2009-07-21
Ttt

---

### Post by dmizer on 2009-07-22
Check all of your Windows computers to make sure that "File and printer sharing for Microsoft networks" is installed and enabled.

---

### Post by WildeBeest on 2009-07-22
They are. It works under Hardy.

What's different with Samba and networking between Jaunty and Hardy?

---

### Post by dmizer on 2009-07-22
> **WildeBeest said:**
> They are. It works under Hardy.

What's different with Samba and networking between Jaunty and Hardy?

Not much is different with Samba, particularly now that the most recent updates have been backported.

The biggest difference in networking (and something that may or may not cause your problem), is 100% dependence on network-manager for network configuration.

As far as I can see, your Jaunty box is configured correctly for network browsing. If you want to try something else, you can install gnome-network-admin and uninstall network-manager. Then configure your network under System > Administration > network

Otherwise, even though this works in Hardy, the problem is still likely to be on the Windows side.

---

### Post by audiomick on 2009-07-28
Hallo.
Don't have much time right now, I'm going on Holidays tomorrow for ten days, but would like to throw this in the pot.
I have the same/similar problem.
Using Ubuntu Studio 8.04 and 8.10 the Linux box found and could access the SMB shares on my Network area storage and my Vista laptop via "Network" in Nautilis
Since the update to Ubuntu Studio 9.04 it can't anymore.
It can:
find them using Firefox smb://ip address, also the ftp: on the NAS box
after doing this, but I think not before
find them using "connect to server" in Nautilis, access the NAS (embedded some kind of Linux) smb shares, but not those on the Vista machine, although a password is requested and supplied.
I'll look back in after my holidays
Michael
PS: this thread
[http://ubuntuforums.org/showthread.php?t=1082148&highlight=windows+share](http://ubuntuforums.org/showthread.php?t=1082148&highlight=windows+share)
seems to be dealing with the same topic

---

