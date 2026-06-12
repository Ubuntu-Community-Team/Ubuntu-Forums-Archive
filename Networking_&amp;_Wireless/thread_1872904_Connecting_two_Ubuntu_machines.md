---
title: "Connecting two Ubuntu machines"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by asus701user on 2011-10-31
I have just installed 11.10 on a spare machine.

I have managed via fstab to mount two shares that are on a NAS drive (via CIFS).

However I cannot get Ubuntu to see or connect to another Ubuntu (10.04 I think).

Both are wired to the same router. Both can use the Internet.

(I have tried to install Samba but I cannot see how to configure and it does not run when I try to use it from the 'Launcher'.)

Surely there must be an easy way for two Ubuntu machines to connect. This machine can ping the other one but cannot see it via Browse Network.

btw my Windows machine can see the target Ubuntu machine just by clicking on Network.

Regards

---

### Post by Paddy Landau on 2011-10-31
Unfortunately, Samba is not intuitive to use.

When you say that Windows can see your Ubuntu machine, can it actually write files to it? I'm going to proceed here with the assumption that you still need to set up the shared folders on both of your Ubuntu machines.

First, ensure that you have the right programs.

[LIST=1]
[*]Open Ubuntu Software Manager (or Synaptic Package Manager if you prefer).
[*]Search for [FONT=Fixedsys]nautilus-share[/FONT]. If it is not  installed, then install it. You may need to log out and in again (you don't need to reboot).
[/LIST]
Second, create your shares (do this on both your Ubuntu machines):

[LIST=1]
[*]Create a shared folder (if you have not done so already). On my machines, I have created a folder called [FONT=Fixedsys]/public[/FONT]. The easy way is to issue the following command (in terminal):```
sudo mkdir /public
```
[*]Give full read-write permissions to everyone on that folder. The easy way is to issue the command:```
sudo chmod a+rwx /public
```
[/LIST]
 Third, ensure that your computers all have different names.

[LIST]
[*]Windows:
[LIST]
[*]Go to Network and Sharing Centre and see your Windows computer name there. Change it if you want (you will need to reboot).
[*]While you are there, check your workgroup name. Change it if you want (you will need to reboot).
[/LIST]
 
[*]Ubuntu:
[LIST]
[*]Look at the file [FONT=Fixedsys]/etc/hostname[/FONT] to see your computer's name. If it is the same as another computer, change it. Issue the following command (either from terminal or from Alt-F2):```
gksudo gedit /etc/hostname
```Note: The name is case-sensitive.
[*]If you change the name, you must also do so in the file [FONT=Fixedsys]/etc/hosts[/FONT] (obviously use exactly the same name as in [FONT=Fixedsys]/etc/hostname[/FONT]), and reboot.```
gksudo gedit /etc/hosts
```Be very careful to change *only *the computer name and nothing else in [FONT=Fixedsys]/etc/hosts[/FONT].
[/LIST]
 
[/LIST]
Fourth, set up Samba (do this on both Ubuntu machines). The easy way is to take my [FONT=Fixedsys]smb.conf.txt[/FONT] (I have attached it), and edit the file:

[LIST=1]
[*]On line 2, change [FONT=Fixedsys]WORKGROUP[/FONT] to whatever your workgroup (on Windows) is.
[*]On line 30, change [FONT=Fixedsys]YourComputerName[/FONT] to your computer's name.
[*]On line 31, change [FONT=Fixedsys]/public[/FONT] to the path of your computer's shared folder (unless you chose to use [FONT=Fixedsys]/public[/FONT]).
[/LIST]
Fifth (and finally) tell Samba about the changes (do this on both Ubuntu machines):

[LIST=1]
[*]Back up the file [FONT=Fixedsys]/etc/samba/smb.conf[/FONT] (just in case).
[*]Take your changed [FONT=Fixedsys]smb.comf.txt[/FONT] and save it as [FONT=Fixedsys]/etc/samba/smb.conf[/FONT] (without the [FONT=Fixedsys].txt[/FONT]).
[*]Reboot.
[/LIST]

---

### Post by asus701user on 2011-11-02
Thank you very much for taking the time to help me.

I have set things up as follows:

Checked nautilus-share is installed on both machines
Made directory /public on both machines with rwx perms
Checked machine names - one is alan-ubuntu and the other is eeepc
Edited the /etc/samba/smb.conf file on each machine:
------------------
alan-ubuntu machine:
------------------
[global]
    workgroup = WORKGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[public]
    comment = alan-ubuntu
    path = /public
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes
------------------------
eeepc:
------------------------
Exactly the same except

comment = eeepc

-------------------------
Rebooted but it does not seem to work. If I 'Browse Network' I get the error Failed to retrieve share list from server.

If I put files in /public on one machine, I cannot see them from the other machine. I can't see what I might have done wrong.

Each machine can ping the other. There is no Windows machine on the network; it is just these two Ubuntu PCs on the router. Both can use the internet.

Most grateful for any ideas. I had thought there might be a wiki or faq that would cover this but not found one.

Thanks

---

### Post by Paddy Landau on 2011-11-02
> **asus701user said:**
> There is no Windows machine on the network; it is just these two Ubuntu PCs on the router.
That's confusing; your first post said that your Windows machine could see our Ubuntu machine!

* By the way, when you post text output (e.g. smb.conf) or code here, please enclose it with "code" marks (either highlight the text and press the **#** button in the toolbar, or put **[noparse]```
[/noparse]** before the code and** [noparse]
```[/noparse] **after it). This makes it hugely easier to read.*

Samba, unfortunately, is still a bit error-prone. Can you confirm that one machine is 11.10 and the other 10.04? If you aren't sure, use System Monitor > System.

The only thing I can think of is that your firewall is preventing access. This could be at the router level (unlikely) or in your computers (unlikely if you have not changed the firewall).

If you have changed the firewall, please check it before proceeding.

First: check you are a member of sambashare. On **both** machines:

[LIST]
[*]Open Users and Groups > Manage Groups > scroll down to sambashare > Properties. Check that your user name is ticked.
[/LIST]
 
Second: let's check your IP numbers.

[LIST]
[*]Click your network icon and select Connection Information.
[*]Look at the IP Address and the Default Route.
[*]The Default Route should be the same set of four numbers on both machines.
[*]The first three numbers of the IP Address on both machines should be be the same as those on the Default Router, but the fourth number must be different (e.g. Default Route 192.168.0.**1**, IP Address on alan-ubuntu 192.168.0.**3**, IP Address on eeepc 192.168.0.**4**).
[/LIST]
 
Third: check your hosts files. On **both** machines:

[LIST]
[*]Open [FONT=Fixedsys]/etc/hosts[/FONT]. *Ignore* any blank lines and comment lines (lines beginning with **#**).
[LIST=1]
[*]The first two lines should read either:
```
127.0.0.1    localhost
127.0.1.1    alan-ubuntu
```or:
```
127.0.0.1    localhost
127.0.1.1    eeepc
```
[*]The only other lines should be to do with IPv6, i.e. numbers with :: in them.
[*]If [FONT=Fixedsys]/etc/hosts[/FONT] is not as described, let me know what is there so we can fix it.
[/LIST]
 
[/LIST]

Fourth: let's check the firewall. Now, I am not clever with firewalls, so this is my "easy peasy" check. If you know firewalls, go ahead and check them your way.

[LIST]
[*]Install [gufw]("apt:gufw") if not already done.
[*]Start gufw (Firewall Configuration).
[*]Press Unlock (otherwise the display is inaccurate).
[*]Is it enabled?
[LIST]
[*]If not, your firewall is turned off, so that's not the problem.
[*]If it is enabled, what values does it have in Incoming, Outgoing and Rules?
[/LIST]
 
[/LIST]
Let us know the results.

---

### Post by asus701user on 2011-11-02
I'll check your suggestions tomorrow but for now:

I do have a windows 7 machine sitting next to the Ubuntu 11.10 machine but I have (temporarily) only one screen to share between them, so the windows machine is not on while I check this. When it is on it can readily see the eeepc (which is actually running 10.10 now I check). I enables sharing on the /home/documents folder in the eeepc and windows sees it without trouble.

However, I have noticed this thread (not sure how to cite it):

**11.10 - smb.conf not used? **

but it suggest that smb.conf has moved in 11.10. I can't believe or understand that but it might be a clue.

I'll check the firewall; there is one in the router but would that stop the machines pinging each other and also it doesn't stop windows.

I'll investigate further tomorrow.

Thanks

---

### Post by SilvaRizla on 2011-11-02
I found that simply sharing a folder solved this problem on 11.04 for myself, some extra packages were installed and it worked fine

---

### Post by asus701user on 2011-11-03
Here are some further details:

**Machine 1:**

Name        eeePC

System Ubuntu 10.10
File system ext4

User is a member of sambashare. Also enabled to share files with the local network.


IP address  192.168.0.196
Broadcast address 192.168.0.255
Default route  192.168.0.1


```

more /etc/hosts
192.168.0.196    eeepc    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    eeepc    localhost6.localdomain6    localhost6
127.0.1.1    eeepc

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```I have installed gufw. Enabled is not ticked. Incoming and outgoing are greyed out.

**Machine 2**

Name     alan-ubuntu

System  Ubuntu 11.10
File system  ext4

Can't find Users and Groups in 11.10 Unity! So I give up.


IP address  192.168.0.199
Broadcast address 192.168.0.255
Default route  192.168.0.1

```

more /etc/hosts
127.0.0.1    localhost
127.0.1.1    alan-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```I have installed gufw. Status is OFF. Incoming and outgoing are greyed out.


If it is true that 11.10 puts samba share info in a different folder to 10.10 then it could be tricky. It is possible that both machines need to be on 11.10 to get this very basic things to work but that would be unbelievable.


Many thanks

---

### Post by Paddy Landau on 2011-11-03
[LIST]
[*]Your IP addresses look absolutely fine.
[/LIST]

[LIST]
[*] Your /etc/hosts on eeepc has an unusual 192.168.0.196 line in it. Please remove it (or comment it out), reboot, and see if it makes any difference whatsoever from either machine.
[/LIST]

[LIST]
[*] > **asus701user said:**
> I have installed gufw. Enabled is not ticked. Incoming and outgoing are greyed out.
...
I have installed gufw. Status is OFF. Incoming and outgoing are greyed out.
You *must* first press Unlock and enter your password. The screen is inaccurate until you do so, because otherwise gufw cannot read the IP tables (the firewall rules).

Remember that gufw is not a firewall; it simply allows you to change the rules of the firewall (a.k.a IP tables), which is built in to Linux.
[/LIST]

[LIST]
[*] > **asus701user said:**
> Can't find Users and Groups in 11.10 Unity! So I give up.
Open your dash and find *Users and Groups*. If it is not there, open Ubuntu Software Centre and install gnome-system-tools.

EDIT: You can see a user's group membership from the terminal with the following command.```
groups *user*
```
[/LIST]

[LIST]
[*] > **asus701user said:**
>  It is possible that both machines need to be on 11.10 to get this very basic things to work but that would be unbelievable.
It certainly would! No, the problem lies with Samba itself, not with the version of Ubuntu. Although Samba has improved dramatically in the past three years that I've been using Linux, it still has a way to go; not far, but it needs to get there.
[/LIST]

---

### Post by asus701user on 2011-11-04
Thanks for the suggestions. 

I have taken out the first line of hosts file on eeePC which now is:

```

more /etc/hosts 
127.0.0.1    localhost.localdomain    localhost 
::1    eeepc    localhost6.localdomain6    localhost6 
127.0.1.1    eeepc  

# The following lines are desirable for IPv6 capable hosts 
::1     localhost ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts

```I have installed gnome-system-tools and checked the sambashares for alan.

Both machines are the same:
```

groups alan
alan : alan adm dialout cdrom plugdev lpadmin admin sambashare

```With the Firewall, on the 10.10 machine running sudo gufw gives the gui but there is no Unlock icon. Running as root I can change it to on or off and it is off. On the 11.10 machine there is an unlock and doing that I can see that it is off.

On both machines there is a directory /public which I have set for sharing with everyone (read/write and guest). I already had a /home/alan/Documents directory set in the same way on both machines. When I look at /public I see just the files on the local machine.

Presumably I should be able to navigate to those folders and use them as if they were on this machine. (Isn't it confusing if they are the same paths?)

Ideally I don't want to 'share' the directory. Just be able to look at it (i.e. mount it). I have been able to do that with some NAS shares via fstab (having given up on autofs). I suppose given time I could put something in fstab but that does not automount and I thought surely this is easy with both machines being Ubuntu. In theory, enabling sharing on a directory should be all that is needed.

If I go via Browse Network I get Windows Network (why when there may not be one?) and then the message Failed to retrieve share list from server.

There must be something else wrong on my machines or something basic I haven't done.

Regards

---

### Post by Paddy Landau on 2011-11-06
> **asus701user said:**
> I have taken out the first line of hosts file on eeePC which now is...
For some reason, you now have the ::1 line twice. Unless you are using IPv6, I would recommend deleting the first occurrence so that [FONT=Fixedsys]/etc/samba/smb.conf[/FONT] looks [post=11413193]as I first suggested[/post].

> **asus701user said:**
> Presumably I should be able to navigate to those folders and use them as if they were on this machine. (Isn't it confusing if they are the same paths?)
No. The path [FONT=Fixedsys]/public[/FONT] is the folder [FONT=Fixedsys]public[/FONT] on your root drive. To access the other machine's drive, it would look like this (from Nautilus):
```
smb://eeepc/public/
```> **asus701user said:**
> Ideally I don't want to 'share' the directory. Just be able to look at it (i.e. mount it).
Then you *are* sharing it. You can make it read-only in two ways, and I would suggest doing both ways for security.

[LIST=1]
[*]```
chmod go-w /public
```
[*]In the [FONT=Fixedsys][public][/FONT] section of [FONT=Fixedsys]/etc/samba/smb.conf[/FONT], change "[FONT=Fixedsys]read only = No[/FONT]" to "[FONT=Fixedsys]read only = Yes[/FONT]".
[/LIST]

> **asus701user said:**
> If I go via Browse Network I get Windows Network (why when there may not be one?)...
As Windows networking is the de facto standard with desktops, Linux has to conform to Windows instead of to an agreed international standard. Samba is the way to implement Windows networking on Linux. That's why you see Windows Network.

Try making those small changes and try again.

---

### Post by asus701user on 2011-11-07
I did remove the line:
192.168.0.196    eeepc    # Added by NetworkManager

and now I have removed the line 
::1    eeepc    localhost6.localdomain6    localhost6

in the first section of /etc/hosts on eeePC. I didn't notice that you said that.

So here is the file when edited:
```

127.0.0.1    localhost
127.0.1.1    eeepc

# The following lines are desirable for IPv6 capable hosts
::1     eeepc   localhost6.localdomain6 localhost6
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```BUT when I restart it goes back to:

```

192.168.0.196    eeepc    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    eeepc    localhost6.localdomain6    localhost6
127.0.1.1    eeepc

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```On the other machine it stays as:
```
more /etc/hosts
127.0.0.1    localhost
127.0.1.1    alan-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```If in Nautilus I try Go Location
```

smb://eeepc/public

```I get a long wait and then the error Failed to mount Windows share. Please select another viewer and try again. I have got two folders on each machine and in Nautilus they are all set in Sharing Options as shared and with r/w and guest access. However, the ones set up in Nautilus don't show up in smb.conf, but hopefully that is not a problem.

Many thanks

---

### Post by Paddy Landau on 2011-11-07
> **asus701user said:**
> However, the ones set up in Nautilus don't  show up in smb.conf, but hopefully that is not a problem.
It will be a problem. If Samba doesn't know about them, it will not present them to the network. You need to add them both to the [public] section.

Unfortunately, I do not know how to add two different paths to [public], so for now please back up smb.conf, choose *one* folder to keep, and "un-share" the other folder.

You will need to double-check smb.conf after that, because Nautilus might have changed it.

> **asus701user said:**
> I did remove the line:
192.168.0.196    eeepc    # Added by NetworkManager
...
BUT when I restart it goes back to: ...
How odd. I have Googled a bit, and it seems to be because you have IPv6 enabled on that specific machine. I'm not sure of this, though. Please:

[LIST]
[*]Disable IPv6 (press the network manager icon in your panel > Edit Connections > (find your connection, wired, wireless, or perhaps both) > Edit > IPv6 Settngs > Method > Ignore.
[*]Remove one of the ::1 lines (it doesn't matter which one) from smb.conf again.
[*]Reboot.
[/LIST]
 Cross fingers that it solves the problem.

Now...

If you still do not get a connection, edit smb.conf (on *both* machines):

[LIST]
[*]Find the [global] section (at the top of the file).
[*]Anywhere inside that section, add the following two lines:```
name resolve order = bcast host lmhosts wins
os level = 33
```
[*]Reboot both machines.
[/LIST]
If it still doesn't work, change the order of the items in "name resolve order" line on *both* machines to:
```
name resolve order = hosts lmhosts wins bcast
```Post back with your results.

---

### Post by asus701user on 2011-11-07
I have done those things.

I have 'unshared' all folders on both machines except the one in root (public).

Checked on network on both machines. On the 10.10 one IPv6 was already ignored in both wired and wireless. On 11.10 it was automatic and I have changed it to ignored.

I have checked the relevant files on both machines and here they are:

eeepc

/etc/hostname
```

eeepc

```/etc/hosts
```

192.168.0.196    eeepc    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    eeepc    localhost6.localdomain6    localhost6
127.0.1.1    eeepc

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```It keeps going back to the above however I edit it.

/etc/samba/smb.conf
```

[global]
    workgroup = WORKGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    usershare owner only = false

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[public]
    comment = eeepc
    path = /public
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes

```Here is fstab as well
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f9199afa-44a8-490f-a35b-a985ec0d2386 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7aa3daba-e186-4598-8c3e-6a1cedf4af43 none            swap    sw              0       0
UUID=4e9703c5-87ea-48e2-b081-ad66560578d7   /home  ext4  nodev,nosuid    0    2
//192.168.0.198/Music /home/alan/NASmounts/Music cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0
//192.168.0.198/Networkdrive /home/alan/NASmounts/Networkdrive cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0

```On the alan-ubuntu machine:
/etc/hostname
```

alan-ubuntu

```/etc/hosts
```

127.0.0.1    localhost
127.0.1.1    alan-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```/etc/samba/smb.conf
```

[global]
    workgroup = WORKGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    usershare owner only = false

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[public]
    comment = alan-ubuntu
    path = /public
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes

```fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=11b066ac-c990-478b-b1d4-a8154b3bfe9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=57a50aef-84f4-4789-848f-7695d5ffecec none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.0.198/Music /home/alan/NASmounts/Music cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0
//192.168.0.198/Networkdrive /home/alan/NASmounts/Networkdrive cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0

```I have edited smb.conf on both machines and added the name resolve.

The first name resolve order did result in both machines seeing ALL the shares on my NAS. (although I have put only two of them into the fstab). Browse network also showed Windows network. Clicking on any of them gave the error Failed to retrieve share list from server. Each time the response took about 30 seconds or so.

With the second  resolve order. It did not show the NAS shares but just Windows network and same error message. Again the usual slow response.

There is something odd about the hosts file on eeepc being overwritten at logon. Or maybe it is something in the router, although  the machines can ping each other all right.

---

### Post by capscrew on 2011-11-07
> **asus701user said:**
> ...
```

[[COLOR="Red"]**public**[/COLOR]] [COLOR="Red"]<--- This is the share name (SMB-resource)[/COLOR]
    comment = eeepc
    path = /public
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes

```...

I have edited smb.conf on both machines and added the name resolve.
I think you have most of this correct, but there are some simple items that are causing you pain.

The SMB/CIFS naming convention is: //NETBIOS_NAME/SMB-resource/.  By this I mean that a share is defined by something like this //EEEPC/public.  Breaking this down we have a NETBIOS NAME that can be derived from the hostname and a SMB resource that is defined by the share name you gave it See the comment in [COLOR="Red"]red [/COLOR]above.

The problem is you have not provided a method for the Samba server (on either eeepc or alan-ubuntu) to either convert the hostname to a NETBIOS NAME or explicitly defined the NETBIOS NAME in the smb.conf file.
> 
The first name resolve order did result in both machines seeing ALL the shares on my NAS. (although I have put only two of them into the fstab). Browse network also showed Windows network.
The resolve order is part of what you have to do.  This sets the mode in which the Samba server announces itself on the network.

There are 4 modes (methods)```

host = use host or DNS name to ***[COLOR="Red"]convert[/COLOR]*** to NETBIOS NAME
lmhosts = use lmhosts names to ***[COLOR="Red"]convert[/COLOR]*** to NETBIOS NAME
wins = use a WINS server *[COLOR="Purple"]supplied[/COLOR]* NETBIOS NAME
bcast = use a [COLOR="Blue"]*defined*[/COLOR] NETBIOS NAME to broadcast to the network

```

The Windows hosts use the last method (bcast) and so should you.  When this is set up you do not need to mount anything via fstab.
> 
Clicking on any of them gave the error Failed to retrieve share list from server. Each time the response took about 30 seconds or so.This is because your 2 Ubuntu hosts can't provide a NETBIOS NAME at this time. > 

With the second  resolve order. It did not show the NAS shares but just Windows network and same error message. Again the usual slow response.
This is even worse as the /etc/host files are not correct.  If you use DHCP and the IP addresses change you will never be able to use the /etc/hosts file with SAMBA. > 

There is something odd about the hosts file on eeepc being overwritten at logon. Or maybe it is something in the router, although  the machines can ping each other all right.
The etc/hosts file is being overwritten by Network Manager.   If you are using immutable IP addresess (unchanging) the you could stop Network Manager from overwriting the /etc/hosts file, but there is an easier way to accomplish your goals.

First provide the NETBIOS NAME thereby eliminating the reliance on the /etc/hosts file.  Add this to your /etc/samba/smb.conf file in the [global] section```
netbios name = <hostname>
[COLOR="Red"]# use either eeepc or alan-ubuntu for <hostname>[/COLOR]
```
Then add this to the [global] section of the /etc/samba/smb.conf file```
name resolve order = bcast 
```

There is no need for the other modes as broadcast will work and the others don't anyway.

Now I suggest that you re-name the share on one of the hosts so you can tell them apart.  On the host eeepc rename the share to something like [e-public].  now you will be able to tell on share from the other.

In my setup I have my shares *under */smb.  This way I can have shares that are private for some and public for others.  I looks something like this ```

/smb <-- The root of the /smb file system
/smb/backup <-- Admins only here
/smb/public <-- Everyone is allowed
```

One last thing > [Is it true] smb.conf has moved in 11.10. I can't believe or understand that...the smb.conf file has not moved, but usershares (created by the users GUI) are defined at ```
/var/lib/samba/usershares
``` 

I hope this provides the answers you need.

---

### Post by Paddy Landau on 2011-11-08
@capscrew: Thank you so much for giving all that explanation and clarification. I have noted it in my documentation.

From your explanation, I do not understand how it is that my Samba does work (I have Windows 7, Ubuntu 11.04, Lubuntu 11.04 and Ubuntu 10.04 successfully communicating on my network), as I do not use [FONT=Fixedsys]netbios name[/FONT] at all.

I also do not use [FONT=Fixedsys]name resolve order[/FONT] or [FONT=Fixedsys]os level[/FONT]; I presume the defaults give the right results. I had recommended them as they had solved the problems I used to have in 10.04.

Regarding renaming the public shares so that they can be told apart, I have not had any problem with that as they all come under the respective computer names.

Could it be that after following your suggestions, asus701user can remove the [FONT=Fixedsys]name resolve order[/FONT] and [FONT=Fixedsys]os level[/FONT] lines?

Let's hope that your suggestions help asus701user, who has struggled so much.

---

### Post by capscrew on 2011-11-08
> **Paddy Landau said:**
> @capscrew: Thank you so much for giving all that explanation and clarification. I have noted it in my documentation.

From your explanation, I do not understand how it is that my Samba does work (I have Windows 7, Ubuntu 11.04, Lubuntu 11.04 and Ubuntu 10.04 successfully communicating on my network), as I do not use [FONT=Fixedsys]netbios name[/FONT] at all.
Samba has two daemons.  These are smbd and nmbd.  In a network that uses DNS (hosts) for ***local LAN name services ***the  nmbd daemon converts the hostname to a NETBIOS name.  The SMB suite of protocols  use NETBIOS to create the Master Browse List.  If you are capable of browsing the network for shares then you are using NETBIOS to do it.  Many times folks give up and don't fully configure Samba.  They resort to using IP address directly to map shares via either bookmarking them in Nautilus or via an entry in fstab.> 

I also do not use [FONT=Fixedsys]name resolve order[/FONT] or [FONT=Fixedsys]os level[/FONT]; I presume the defaults give the right results. I had recommended them as they had solved the problems I used to have in 10.04.
Yes there is a default for *name resolve order*.  You can see this with ```
testparm -v | grep resolve
```  The os level settings force Samba to win the Master Browser election all the time.  This may or may not be appropriate.

The command *testparm -v*shows all the settings that are not in the smb.conf file (the defaults).> 
Regarding renaming the public shares so that they can be told apart, I have not had any problem with that as they all come under the respective computer names.
I wanted the the OP to realize that the [public] name has no relation to the /public name (we are speaking of names not roles).  The term //eeepc/public may not be recognized as //server_name/share_name by the novice user.  Also, it can be confusing if in the future you want to create a share with restricted access in a filesystem that is /public.  > 
Could it be that after following your suggestions, asus701user can remove the [FONT=Fixedsys]name resolve order[/FONT] and [FONT=Fixedsys]os level[/FONT] lines?
The OP does not need the *os level *directive, but the name resolve order is needed due to the OP's lack of local name services.

Ultimately this problem exists because of the methods used by Ubuntu and the assumptions of the Samba packager (dev).  These are: a) There will be some sort of local DNS (hosts) name resolution or b) That the end user will know how to remedy the lack of thereof.  Unfortunately, many times this is not true.> 
Let's hope that your suggestions help asus701user, who has struggled so much.
Yes indeed.

---

### Post by Paddy Landau on 2011-11-08
@capscrew: Thank you again for taking your time to explain these issues. I understand some of them but not all.

> **capscrew said:**
> Many times folks give up and don't fully configure Samba.
I'm guessing that I was just lucky, then. For the new Ubuntu installations, I merely set the computer name in [FONT=Fixedsys]/etc/hostname[/FONT] and [FONT=Fixedsys]/etc/hosts[/FONT], and copied the [FONT=Fixedsys]smb.conf[/FONT] files that [post=11413193]I attached in post #2[/post] and modified the workgroup and comment; and in Windows I enabled file sharing and set the computer name. Networking between all computers "just worked".

> **capscrew said:**
> ... testparm -v
My testparm reports:
```
name resolve order = lmhosts wins host bcast
os level = 20
```> **capscrew said:**
> I wanted the the OP to realize that the [public] name has no relation to the /public name (we are speaking of names not roles).
Ah, I understand now. It taught me something, too!

> **capscrew said:**
> The OP does not need the *os level *directive, but the name resolve order is needed due to the OP's lack of local name services.
This is something I do not understand. Is this to do with the DNS name resolution? What specifically manages this "local name services" -- or, more practically, how do you turn it on and off? (Mine is obviously on.)

---

### Post by capscrew on 2011-11-08
> **Paddy Landau said:**
> @capscrew: Thank you again for taking your time to explain these issues. I understand some of them but not all.


I'm guessing that I was just lucky, then. For the new Ubuntu installations, [COLOR="DarkGreen"]I merely set the computer name in [FONT=Fixedsys]/etc/hostname[/FONT] and [FONT=Fixedsys]/etc/hosts[/FONT][/COLOR], and copied the [FONT=Fixedsys]smb.conf[/FONT] files that [post=11413193]I attached in post #2[/post] and modified the workgroup and comment; and in Windows I enabled file sharing and set the computer name. Networking between all computers "just worked".
Lucky, I think not.  Unknowing, maybe.  :D    I jest.  Think about what you have done.  You did provide name resolution!  It didn't *"just work" *.  You made it work by providing the hostname and using static IP addressing.

Many times the user just installs Ubuntu and then Samba without understanding the need for infrastructure.  What kind of mess do they really have?  If the host is the only host on the network (as the majority are) then the system works fine.  The host is preconfigured to ask for an IP address via DHCP and the router provides IP address to the host.

On a Debian host (the only Linux I can comment about) there is a workaround for applications that need to see the hosts name (e.g. hostname).  This requirement is covered like so```
127.0.0.1 localhost <-- normal loopback naming
127.0.1.1 ubuntu-hostname [COLOR="Red"]<-- The Debian work around[/COLOR]
```
This is the only way of providing a hostname to IP mapping in a dynamic DHCP environment.  It's not technically correct, but it will work for a single machine.  In short: It does not provide a hostname to Ethernet interface mapping. 

Samba on the other hand needs the correct hostname mapping to the real interface.  This is what I was talking about before.

One other complication should be mentioned.  The SMB/CIFS protocol uses NETBIOS NAMES and that works a little differently.  At the heart of it is the notion that IP addresses would be dynamic (DHCP) and as such you could not count on any particular host having a particular IP address.  So the idea was to create a system where you mapped the COMPUTER NAME to the IP address rather than the other way around.

This was achieved by DEC, IBM and finally by Microsoft with the NETBIOS naming convention.  All Windows shares use this convention to this day.  It has been it has been ported to NETBIOS over TCP (NBT), but it still works the same.

A simple description of how it works is: The host announces its name to the network (bcast) and the IP address is noted.  At this point the host can be contacted via its name as it is mapped to the IP address.

Why this long explanation?  Well, Samba has to operate the same way.  If you are using DNS then Samba has to accommodate that and convert the DNS name to a NETBIOS NAME so that Windows hosts will understand.  In addition the Master Browse List (MBL) is constructed using the NETBIOS NAME convention.  The Master Browser (the host with the MBL) can be either a Samba host or a Windows host so they have to inter-operate. 

Samba achieves this interoperability of naming conventions with the daemon (process) *nmbd *.  As I said before it will either convert a hostname to NETBIOS NAME or user the NETBIOIS NAME provided in the smb.conf file.

An advantage to explicitly declaring the NETBIOS NAME is that you can use dynamic IP addressing (DHCP).  I have come to appreciate this with the pervasiveness of Network-Manager on most Linux Desktop hosts.  In the end this is how Windows does it.  It's called a [**_[COLOR="DarkSlateGray"]B-node[/COLOR]_**]("https://www.google.com/search?q=b-node&btnG=Go!") (broadcast)> 


My testparm reports:
```
name resolve order = lmhosts wins host bcast
os level = 20
```
Ah, I understand now. It taught me something, too!
You can see what happens when the names are resolved with this ```
smbtree -d3
```
This will show the search for the name  in the order configured (lmhosts wins host bcast).  In your case it will be successful with the *host *directive.> 
This is something I do not understand. Is this to do with the DNS name resolution? What specifically manages this "local name services" -- or, more practically, how do you turn it on and off? (Mine is obviously on.)
The /etc/hosts file is a DNS primitive.  DNS was created by extending the hostname ideas.  Linux searches the /etc/hosts file before it searches DNS for name resolution internally.  You are controlling the local nameservices by configuring all the hosts /etc/hosts files and the fact that you have static IP addressing.  Samba does the conversion with the data you provided.

FYI -- the DNS naming convention is: *[COLOR="Blue"]hostname[/COLOR]*.domain_name.top_level_domain.  If I have a host named *oak* in a domain named *trees* in the *.com* (tld) then the DNS name (FQDN) is *[COLOR="Blue"]oak[/COLOR].trees.com*.  On that host the command hostname should return the name [COLOR="Blue"]oak[/COLOR].

---

### Post by Paddy Landau on 2011-11-09
@capscrew: Wow, I have learned much. Thank you.

> **capscrew said:**
> You made it work by providing the hostname and using static IP addressing. ... An advantage to explicitly declaring the NETBIOS NAME is that you can use dynamic IP addressing (DHCP).
How did you know I used static IP addressing? BTW, in my case, the IP address is decided by the router, which I have instructed according to the MAC address. The computer uses whatever IP address the router assigns.

Anyway, does that mean I should add *netbios name* to smb.conf (a) for consistency and standards, and (b) should I stop using static IP addressing?

I also presume that the *netbios name* should be the same as that in /etc/hostname and /etc/hosts, or am I mistaken? I notice that the netbios name is case-insensitive, whereas /etc/hostname and /etc/hosts are case-sensitive.

To all my Ubuntu and Lubuntu machines, I have added:
```
netbios name = *computername*
```> **capscrew said:**
> You can see what happens when the names are resolved with this ```
smbtree -d3
```
That was instructive. I was using the default name resolve order, but now on all my Ubuntu and Lubuntu machines I have set it to
```
name resolve order = bcast lmhosts wins host
```Unless I am misreading it, this resolves quicker (with fewer attempts) than before. I have tested all my network connections and they still work.

The only thing that doesn't work is creating, modifying or deleting files on Windows from Ubuntu, but I suspect that is to do with Windows permissions and not Ubuntu. Fortunately, this is not a problem for me.

> **capscrew said:**
> FYI -- the DNS naming convention is: *[COLOR=Blue]hostname[/COLOR]*.domain_name.top_level_domain.  If I have a host named *oak* in a domain named *trees* in the *.com* (tld) then the DNS name (FQDN) is *[COLOR=Blue]oak[/COLOR].trees.com*.  On that host the command hostname should return the name [COLOR=Blue]oak[/COLOR].
That is not relevant with a workgroup instead of a domain, is it?

---

### Post by asus701user on 2011-11-09
Thank you both for your help. I thought I had done what you suggested but I am still having problems.

Here are the relevant files on alan-ubuntu

```
/etc/hosts
127.0.0.1    localhost
127.0.1.1    alan-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

``````
/etc/hostname
alan-ubuntu

``````
/etc/samba/smb.conf
[global]
    workgroup = WORKGROUP
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* 
%n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    usershare owner only = false
    netbios name = alan-ubuntu
    #use either eeepc or alan-ubuntu
    name resolve order = bcast

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[public]
    comment = alan-ubuntu
    path = /home/alan/main-public/
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes

```The files on the other machine, eeepc, are the same except for the name of the computer and the path of the shared directory.

I notice that Network Manager is still changing the hosts file and inserting the extra lines, but hopefully that is not what is causing the problem. I have taken out the OS Level in smb.conf because I deduce from capscrew that it might not be needed.

I am not sure in smb.conf what goes in [public]. Does this have to be the same name as the shared directory or is it just an identifier that shows up in Browse Network? I have tried both [public] and main-public but that doesn't make any difference.

Each machine now shos all shares on the NAS and Windows Network, but opening any of them gives Failed to retrieve share list from server.

Apologies if I have not understood what you have said or omitted anything; it is at the limits of what I understand with Linux.

---

### Post by capscrew on 2011-11-09
> **asus701user said:**
> Thank you both for your help. I thought I had done what you suggested but I am still having problems.

Here are the relevant files on alan-ubuntu

```
/etc/hosts
127.0.0.1    localhost
127.0.1.1    alan-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

``````
/etc/hostname
alan-ubuntu

```
We don't need to modify the /etc/hosts file so this is fine. > 


```
/etc/samba/smb.conf
[global]
...
    netbios name = alan-ubuntu
    #use either eeepc or alan-ubuntu
    name resolve order = bcast

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[public]
    comment = alan-ubuntu
    path = /home/alan/main-public/
    read only = No
    create mask = 0666
    directory mask = 0777
    guest ok = Yes

```
This looks good.> 

The files on the other machine, eeepc, are the same except for the name of the computer and the path of the shared directory.
Good.> 

I notice that Network Manager is still changing the hosts file and inserting the extra lines, but hopefully that is not what is causing the problem. 
Correct.  You  are not using the /etc/hosts file as you have explicitly declared the NETBIOS NAME.> 

I have taken out the OS Level in smb.conf because I deduce from capscrew that it might not be needed.
Yes this is correct.> 

I am not sure in smb.conf what goes in [public]. Does this have to be the same name as the shared directory or is it just an identifier that shows up in Browse Network? 
The [public] is the share name and it is what shows up when you browse.> 
I have tried both [public] and main-public but that doesn't make any difference.
This is because the browse list is not populated yet.  At this point it is not important.  

I see **the path is not pointing to /public**.  Did you do that on purpose?

Post the output of ```
pgrep -l mbd
```
Sometimes the nmbd daemon doesn't start.  I want to know that it has started correctly.

> Each machine now shos all shares on the NAS and Windows Network, but opening any of them gives Failed to retrieve share list from server.

Apologies if I have not understood what you have said or omitted anything; it is at the limits of what I understand with Linux.

At this point you have done everything correctly except the path to the directory you are sharing.  Do you have a directory at /public.  Do not add one if you haven't done so already.  I'd like you to do that differently.

---

### Post by capscrew on 2011-11-09
> **Paddy Landau said:**
> @capscrew: Wow, I have learned much. Thank you.

How did you know I used static IP addressing? BTW, in my case, the IP address is decided by the router, which I have instructed according to the MAC address. The computer uses whatever IP address the router assigns.
You can't use a static mapping of IP address to hostname when you have IP addresses changing.  You had to have had an immutable IP address. > 

Anyway, does that mean I should add *netbios name* to smb.conf (a) for consistency and standards, and (b) should I stop using static IP addressing?
Not at all.  These are different ways to achieve the same thing.  If you have static IP addressing you *may *use either method.  If you have dynamic IP addressing (via DHCP) then you *** must *** declare the NETBIOS NAME in the smb.conf file. > 

I also presume that the *netbios name* should be the same as that in /etc/hostname and /etc/hosts, or am I mistaken?
It would be confusing otherwise.> 
 I notice that the netbios name is case-insensitive, whereas /etc/hostname and /etc/hosts are case-sensitive.
Windows OS is case insensitive while Linux is case sensitive.  > 
To all my Ubuntu and Lubuntu machines, I have added:
```
netbios name = *computername*
```
That was instructive. I was using the default name resolve order, but now on all my Ubuntu and Lubuntu machines I have set it to
```
name resolve order = bcast lmhosts wins host
```Unless I am misreading it, this resolves quicker (with fewer attempts) than before. I have tested all my network connections and they still work.
I don't know that you accomplished anything meaningful here.  You have however strayed form th default settings of Samba as it is installed in Ubuntu.  You have to remember that when diagnosing future problems.> 
The only thing that doesn't work is creating, modifying or deleting files on Windows from Ubuntu, but I suspect that is to do with Windows permissions and not Ubuntu. Fortunately, this is not a problem for me.
Indeed, this is an entirely different aspect.  Samba has some limited capabilities in this area.  I rely on the underlying Linux file system permissions. > 
---
[QUOTE]FYI -- the DNS naming convention is: hostname.domain_name.top_level_domain. If I have a host named oak in a domain named trees in the .com (tld) then the DNS name (FQDN) is oak.trees.com. On that host the command hostname should return the name oak.
That is not relevant with a workgroup instead of a domain, is it?[/QUOTE]
It was to point out how a hostname is an part of the DNS structure.

---

### Post by asus701user on 2011-11-09
Here is the output you asked for:

```
alan@alan-ubuntu:~$ pgrep -l mbd
713 smbd
788 smbd
1396 nmbd
```and

```
alan@eeepc:~$ pgrep -l mbd
796 smbd
852 smbd
1569 nmbd
```Now something wonderful has happened. On alan-ubuntu, Browse Network shows Windows Network quickly. Then that shows icon for Workgroup and then for alan-ubuntu, eeepc and storage-6B3A which is the NAS. eeepc shows e-public which is the directory I was trying to share, and also print$ and public. As I click each of those it gets put on the desktop.

I don't think I have done anything on alan-ubuntu this session except pgrep -l mbd and I am sure I restarted last time when it didn't work - this time though it was a cold boot.

It now works from the eeepc as well. The only difference is that Network Browse shows alan-ubuntu, eeepc and storage-6B3A as well as Windows Network. Then Windows Network leads to Workgroup and then to the same three shares. I don't know why they are 'duplicated' like that.

I did deliberately change the shared directories from /public to eeepc/home/alan/e-public and alan-ubuntu/home/alan/main-public so that I could distinguish them and also keep things in my $HOME rather than at root.

Once you browse to the shared directory it gets 'mounted' like the folders I have been mounting via fstab.

Is it possible to share directories now in Nautilus via Properties Sharing or will I have to edit smb.conf for each folder?

Also /public comes up for each machine which must be the /public in root even though it is not 'shared' in Nautilus.

So netbios name in smb.conf is the key to it - will try to make a note of that for the future.

Very many thanks to both of you for solving this for me.

---

### Post by capscrew on 2011-11-09
> Now something wonderful has happened.

What happened was the Master Browse List was populated.  This can take a few minutes to happen (up to 15 minutes).  If your happy, I'm happy.  Let us know if you have other questions.

---

### Post by capscrew on 2011-11-09
> Is it possible to share directories now in Nautilus via Properties Sharing or will I have to edit smb.conf for each folder?
I'm sorry.  I missed this question before.

Yes you should be able to share directories via Nautilus.  The shares will be defined in a different place.  You can see then at ```
[COLOR="DarkSlateGray"]/var/lib/samba/usershares[/COLOR]
```

In addition you should not have to have any shares mounted via fstab.

I hope this answers all your questions for now.  If it has then you should mark this thread "solved"  

-Capscrew

---

### Post by asus701user on 2011-11-09
That has done it wonderfully. Thank you for your help.

---

### Post by Paddy Landau on 2011-11-09
And I add my thanks again to capscrew, from whom I have learned a lot in this thread. :cool:

---

