---
title: "Can not write to Samba share from XP"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by loctavius on 2009-12-12
Ok - so my Ubuntu box just sits here and does it's samba thing. I rarely use it except to patch it for security updates that come out, I just access it from the PC workstations to stream music.

However, it won't let me write the share from my XP stations anymore. I used sudo nautalis to go in and set the permissions for myself. (They were all set to root) I even told it to set the permissions on all the enclosed files. Then I re-mapped the samba drive and rebooted, but I still can't write to that drive.

I had previously been able to write to that drive just fine - I think as recently as a couple of months ago.

Any ideas?

---

### Post by loctavius on 2009-12-12
Just FYI - I CAN write to the files directly from the Ubuntu box when logged in as myself, not as root. So I know that the permissions are set correctly - this has to be some sort of issue with the networking side of it I guess. (BTW - I am logging into my XP box with the same username and password as I do my Ubuntu box)

---

### Post by loctavius on 2009-12-12
bump

---

### Post by loctavius on 2009-12-13
I'll try this again.

I can't write to my Samba share from my XP box. I had previously been able to do so. (The last time I did was probably about two months ago)

I went into the Ubuntu box and did sudo nautalius, and I found that all the permissions were set to root. I changed it all back to my username, told it to apply the permissions to the enclosed files, and rebooted. I then went to my XP box, unmapped the drive, rebooted, and remapped the drive. Still nada.

I log onto my XP box with the same username and password combination. I can open the samba share, and I can playe the media files stored on it, but I can not write to it. I get the standard "make sure the disk is not full or write-protected" windows message.

I CAN however write to the files when logged in as myself from the Ubuntu box, so I know I have the permissions set correctly now. Nothing belongs to root anymore.

Any ideas - please? The Ubuntu box rarely has a head on it, so I have to be able to get this resolved so my wife can have her monitor back. Thanks in advance for the help.

---

### Post by dmizer on 2009-12-13
Please post the contents of /etc/samba/smb.conf

---

### Post by loctavius on 2009-12-14
Thanks for the reply. Here is my /etc/samba.conf file:

(blank is the username I use to access this box)

[global]
    ; General server settings
    netbios name = Dooku
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

    usershare owner only = False

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
    path = /home/samba
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = blank
    force group = blank

---

### Post by dmizer on 2009-12-14
The howto you used to create the smb.conf file is really old (circa Dapper), and many things have change about samba since then.

Try this smb.conf:
```
#======================= Global Settings =======================

## Browsing/Identification ###
[global]
netbios name = Dooku
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
dns proxy = no
name resolve order = lmhosts host wins bcast

#### Debugging/Accounting ####
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

####### Authentication #######
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

########## Printing ##########
printing = cups
printcap name = cups

############ Misc ############
usershare allow guests = yes

#======================= Share Definitions =======================

[MyFiles]
path = /home/samba
browseable = yes
read only = no
```


If you still have problems, please post the output of:
```
sudo ls -la /home
```

---

### Post by dmizer on 2009-12-14
> **dmizer said:**
> The howto you used to create the smb.conf file is really old (circa Dapper), and many things have change about samba since then.

Try this smb.conf:
```
#======================= Global Settings =======================

## Browsing/Identification ###
[global]
netbios name = Dooku
workgroup = WORKGROUP
server string = %h server (Samba, Ubuntu)
dns proxy = no
name resolve order = lmhosts host wins bcast

#### Debugging/Accounting ####
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d

####### Authentication #######
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

########## Printing ##########
printing = cups
printcap name = cups

############ Misc ############
usershare allow guests = yes

#======================= Share Definitions =======================

[MyFiles]
path = /home/samba
browseable = yes
read only = no
```

If you still have problems, please post the output of:
```
sudo ls -la /home
```

---

### Post by loctavius on 2009-12-16
No dice. Still won't write. I moved the old smb.conf file to smb.conf.old, made a new smb.conf file, and pasted in the contents of what you had above, the restarted the machine. The specific message I get when I try to write from the XP box or to modify a file from the XP box is is:

Cannot copy <filename>: Access is denied
Make sure the disk is not full or write-protected and that hte file is not currently in use.

There are almost 3.0 GB free on that drive, and the files I'm trying to copy or modify are not in use. I can still write to the drive from the Ubuntu box directly when logged in as my user and of course as root.

And the output of the command you wanted me to run is:

blank@Dooku:~$ sudo ls -la /home
[sudo] password for blank: 
total 32
drwxr-xr-x  5 root     root      4096 2009-07-28 15:21 .
drwxr-xr-x 21 root     root      4096 2009-12-12 12:12 ..
drwx------  2 root     root     16384 2009-07-28 14:02 lost+found
drwxr-xr-x 36 blank blank  4096 2009-12-16 06:41 blank
drwxrwxr-x 11 blank blank  4096 2009-12-14 18:54 samba
blank@Dooku:~$ 

Again, thanks for the help - I do appreciate it.

---

### Post by dmizer on 2009-12-17
Have you added the XP username/pass to your Ubuntu box? If not, use these commands:
```
sudo useradd -s /bin/true [COLOR="Red"]XP-username[/COLOR]
sudo smbpasswd -L -a [COLOR="Red"]XP-username[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]XP-username[/COLOR]
```
Replace [COLOR="Red"]XP-username[/COLOR] with your actual XP machine's username. When it asks you for the password after the second command, make sure the password matches the actual XP user's password. This IS case sensitive, and may not work if there is a space in the username.

---

### Post by loctavius on 2010-01-06
Finally got around to trying the last suggestion, and again, no dice. (Holidays were hectic) The output was as follows:

username@Dooku: ~$sudo useradd -s /bin/true username
[sudo] password for username:
useradd: user username exists
username@Dooku: ~$sudo smbpasswd -L -a username
New SMB password:
Retype new SMB password:
username@Dooku: ~$ sudo smbpassword -L -e username
Enabled user username.

Still get the same generic message when trying to write from XP - Access is denied - check to see if the disk is full or write protected. Ugh.

Any more ideas?

---

### Post by loctavius on 2010-01-09
Bump. I still need help.

Thought I'd add the following - I'd really rather NOT re-install the OS if I can avoid it. Last time I managed to wipe my disk despite me telling the installer to NOT do it. Not sure how I managed that.

I also checked my lmhosts file and found a small typo - I don't know if it was affecting it or not, but it wasn't the cause because I fixed it and still no dice. (The Samba machine name was not capitalized in the lmhosts file on my XP machine, so I couldn't ping it by name when I capitalized it in the command line. I fixed it and rebooted, but still no dice.)

I need to get this Samba back into write status ASAP. Besides serving as my music server for the house, it also serves as my primary backup for my PC, with my external hard drives being secondary. I haven't been able to sync my files in a couple of months now.

Sorry - one other thing - if someone can tell me how to get telnet access enabled from my XP machine to my Ubuntu machine over the local LAN, I'd be thrilled. My monitor died, so I'm having to move monitors to and from my wife's computer to try the suggestions people are giving me.

---

### Post by dmizer on 2010-01-09
> **loctavius said:**
> Bump. I still need help.

Thought I'd add the following - I'd really rather NOT re-install the OS if I can avoid it. Last time I managed to wipe my disk despite me telling the installer to NOT do it. Not sure how I managed that.

I also checked my lmhosts file and found a small typo - I don't know if it was affecting it or not, but it wasn't the cause because I fixed it and still no dice. (The Samba machine name was not capitalized in the lmhosts file on my XP machine, so I couldn't ping it by name when I capitalized it in the command line. I fixed it and rebooted, but still no dice.)

I need to get this Samba back into write status ASAP. Besides serving as my music server for the house, it also serves as my primary backup for my PC, with my external hard drives being secondary. I haven't been able to sync my files in a couple of months now.

Sorry - one other thing - if someone can tell me how to get telnet access enabled from my XP machine to my Ubuntu machine over the local LAN, I'd be thrilled. My monitor died, so I'm having to move monitors to and from my wife's computer to try the suggestions people are giving me.

For CLI access, use ssh. To install ssh:
```
sudo apt-get install openssh-server
```

Then you will need to get putty for Windows: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

For your smb problem, add "security = user" to the Authentication section like so:
```
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
[COLOR="Red"]security = user[/COLOR]
```
Reboot or restart samba to make the change.

Do you have a local firewall running on the Ubuntu server? If you are not sure, please post the output of:
```
sudo iptables -L
```

---

### Post by loctavius on 2010-01-09
First, thanks for the help with the telnet - it worked perfectly. :)

Second, I don't think I have a firewall installed - I know I didn't put one on there on purpose, so unless the update program did it, I don't have one. Here is the output you asked for: 

user@Dooku: /etc/samba$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source        destination

Chain FORWARD (policy ACCEPT)
target    prot opt source        destination

Chain OUTPUT (policy ACCEPT)
target    prot opt source        destination

Lastly, still no dice with the addition of the "security = user" line. After I added the line and saved the smb.conf file, I not only restarted both machines, but I un-mapped and re-mapped the drive from My Computer to make sure I had a fresh connection and all the changes took effect.

What now? (By the way, I find it incredibly bizarre that I could write to this drive from the XP machines in my house as recently as two months ago and that I haven't changed anything at all - at least, not on purpose)

---

### Post by loctavius on 2010-01-11
Bump.

---

### Post by dmizer on 2010-01-11
Try this:
```
sudo chmod -R 777 /home/samba
```

---

### Post by loctavius on 2010-01-16
Bump.

Unless someone has another idea, I think it may be time to uninstall and reinstall Samba. Can someone point me towards a guide to do that that doesn't involve me wiping the system? Thanks in advance.

---

### Post by CharlesA on 2010-01-16
The only thing you would need to do to uninstall samba would be to run "sudo apt-get purge samba"

Then reinstall it with sudo apt-get install samba

Then try to add the shares.

EDIT: There was an update to samba a few weeks ago I believe. I had to re-add the shares to my smb.conf.

---

### Post by MarkC502 on 2010-01-16
I have had similar issues with samba running on 9.10  after updating and found that the only way a windows PC could access with read/write was to set the share to be available to "everyone" with read write and then it works, but with no security from another LAN user. However you would still be protected from Internet users with a Router as it won't allow port 139 Etc traffic through from the internet unless you set it up to do that ( bad idea ). Several reinstalls of samba had zero positive effect and the problem still was present.

PM me if you ever figure out a better way :-)

---

### Post by CharlesA on 2010-01-16
You should check the folder permissions on the samba share.

---

### Post by loctavius on 2010-01-16
That was suggested in an earlier post, so I did:

sudo chmod -R 777 /home/samba

which did not solve the problem. This is why I'm getting frustrated with the whole thing. I've set all the permissions, changed the password, un-mapped and re-mapped the drive, rebooted a million times, etc, and still no write access, when it was working a couple of months ago.

This is why I came to you guys hoping for an answer - everything I've done SHOULD have fixed it by now but hasn't. Any last ideas before I nuke Samba and start over?

---

### Post by CharlesA on 2010-01-16
I don't see any allowed users listed.

Here's what one entry from smb.conf looks like for me:

```

[Charles]
        comment = Charles' Folder
        invalid users = clone,htpc
        create mode = 660
        path = /array/charles
        write list = charles
        directory mode = 770

```

EDIT: I used Webmin to set up my samba shares and haven't had any problems with them. Maybe give that a shot before totally reinstalling Samba?

---

### Post by loctavius on 2010-01-16
Problem solved!!!!!!!! Yay for me! Now, can someone tell me why? My samba.conf file is posted earlier in this thread if you care to look it over and help me figure this out.

If I map the samba share from my XP machine using \\Dooku\samba, it will let me read and execute, but not write.

However, if I map it as \\Dooku\MyFiles, it lets me read, execute and write. So what gives? Why do I have to map it to "MyFiles" in order for it to work?

I got the idea to try it when looking over my samba.conf file just now, and saw that name under the "Share Definitions" header in the conf file, and I re-mapped it using that, and presto, instant write access.

Regardless, I'm happy it works. I am curious as to why I have to map it like that to make it work when I did the chmod -777 on the directory - it should have worked without mapping it to "MyFiles". 

Thanks for the help guys - I never would have thought of this had you not been prodding me to try different things. I knew it was some stupid little thing all along.

PS: I'd bet that if I added "Samba" as a share definition in the samba.conf file and then mapped my XP drive to that, I'd have write access that way as well. Yes?

---

### Post by dmizer on 2010-01-17
> **loctavius said:**
> Problem solved!!!!!!!! Yay for me! Now, can someone tell me why? My samba.conf file is posted earlier in this thread if you care to look it over and help me figure this out.

If I map the samba share from my XP machine using \\Dooku\samba, it will let me read and execute, but not write.

However, if I map it as \\Dooku\MyFiles, it lets me read, execute and write. So what gives? Why do I have to map it to "MyFiles" in order for it to work?

I got the idea to try it when looking over my samba.conf file just now, and saw that name under the "Share Definitions" header in the conf file, and I re-mapped it using that, and presto, instant write access.

Regardless, I'm happy it works. I am curious as to why I have to map it like that to make it work when I did the chmod -777 on the directory - it should have worked without mapping it to "MyFiles". 

Thanks for the help guys - I never would have thought of this had you not been prodding me to try different things. I knew it was some stupid little thing all along.

PS: I'd bet that if I added "Samba" as a share definition in the samba.conf file and then mapped my XP drive to that, I'd have write access that way as well. Yes?

In samba terms:
\\hostname\sharename

Where "hostname" = the name of the server. This is defined in smb.conf under the option "netbios name = Dooku"
Where "sharename" = the name given to the share on the server. This is defined in smb.conf at the very top of the share stanza in brackets "[]" like so:
```
[MyFiles]
```

So, if you wanted to mount as \\Dooku\samba, all you have to do is change [MyFiles] to [samba] in your smb.conf file.

Frankly, I don't understand why you could see the share at all when mapping it with \\Dooku\samba.

---

### Post by loctavius on 2010-01-19
Not only could I see it from both XP machines in the house, but I could execute from it on both machines in the house. I could also browse to it in Network Neighborhood. Now that I understand better how the samba.conf file works, I'm perplexed too.

Regardless, I thank everyone again for helping - your ideas on how to fix it got me to looking at things, and I probably wouldn't have thought to try this otherwise. So I'm happy.

PS: This is actually good news. I've been worried about my wife accidentally deleting something. So I'll map hers to the \samba share, and mine to the \MyFiles, then I don't have to sweat it at all.

---

### Post by Bilal Haddad on 2010-01-19
hi, am trying to share my external hard disk on my network by using the Ubuntu Operating system. can i someone help me please ?

---

