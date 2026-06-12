---
title: "Nautilus will not access Samba share"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by s31523 on 2006-06-01
Just upgraded to Dapper from Breezy and I can no longer get to my Samba share that is running on my other Linux (which is running Breezy as of yet) machine.  I am certain this is a Nautilus thing because I can print to the Samba share, it shows up if I do a smbtree, and I can access the share using smbclient, AND I can mount the Samba share.

When I browse the samba shares under Nautilus I see the share but when I click on it I get a dialog box with "The folder contents could not be displayed" with "homes" couldn't be found. Perhaps it has recently been deleted on the bottom of the dialog.

**Can someone who has had success using Nautilus post both client and server smb.conf files?**

What gives?

For now, I plan on putting a script that will mount the share, or do auto mount and make an entry in fstab.  For anyone else out there with the same problem here is my workaround (mounting the share):
1.) Be sure the smbfs package is installed (search for it in synaptic)
2.) open terminal and go to /mnt
3.) sudo mkdir samba
4.) sudo mount -t smbfs -o username=your_user_name //your_server/your_share /mnt/samba/

Uggh.... Everything was going SO well too.  Gotta have one problem I guess.

---

### Post by karthik085 on 2006-06-01
[QUOTE=s31523]Just upgraded to Dapper from Breezy and I can no longer get to my Samba share that is running on my other Linux (which is running Breezy as of yet) machine.  I am certain this is a Nautilus thing because I can print to the Samba share, it shows up if I do a smbtree, and I can access the share using smbclient, AND I can mount the Samba share.

When I browse the samba shares under Nautilus I see the share but when I click on it I get a dialog box with "The folder contents could not be displayed" with "homes" couldn't be found. Perhaps it has recently been deleted on the bottom of the dialog.

What gives?

For now, I plan on putting a script that will mount the share, or do auto mount and make an entry in fstab.  For anyone else out there with the same problem here is my workaround (mounting the share):
1.) Be sure the smbfs package is installed (search for it in synaptic)
2.) open terminal and go to /mnt
3.) sudo mkdir samba
4.) sudo mount -t smbfs -o username=your_user_name //your_server/your_share /mnt/samba/

Uggh.... Everything was going SO well too.  Gotta have one problem I guess.[/QUOTE]
[http://ubuntuforums.org/showpost.php?p=860325&postcount=3](http://ubuntuforums.org/showpost.php?p=860325&postcount=3)

---

### Post by s31523 on 2006-06-02
Yes, I read that post, and every other post related, but nothing describes my situation... I already had password encryption setup in Breezy.  Nothing has changed, and as I said I know Samba is setup and working correctly since I can access the share through smbclient and I can mount the share and use it that way.  Nautilus can see the share, but just won't display the contents.

---

### Post by s31523 on 2006-06-02
I think there is some sort of bug here.  There is a similar report in bugzilla, and I have added a comment.
see Bug #47386, [https://launchpad.net/distros/ubuntu/+source/samba/+bug/47386](https://launchpad.net/distros/ubuntu/+source/samba/+bug/47386)

If anyone can help, please post here and make comments to the bugzilla report.

---

### Post by Uta on 2006-06-02
I have a similar issue with a weird twist. I have 3 computers on the network. An iBook running Dapper, G5 running Mac OS and a Dell running Dapper. The Mac G5 and iBook booting Dapper have 2 way Samba communication, plus both computers can see and access the Samba share on the Dell but the Dell running Dapper can't see any Samba network shares and the samba shares that were previously bookmarked (in Breezy) now give weird error messages like, "smb:/// is not a valid location" and this one, "smb://apg5/myname is not a valid location" which of course it is. Any work arounds? It seems to be a i386 Dapper issue but not a PPC Dapper issue.

---

### Post by s31523 on 2006-06-02
I am running the i686 kernel, if that means anything.

There are a ton of other similar Samba problems describing what you are seeing.  Sounds like others are having problems with network name resolution in Nautilus.  The more I read about problems the more I think it is a Nautilus thing, not Samba.  Try using the IP address of your machine.  Open a Nautilus window and hit Ctrl-L and type smb://198.168.whatever.whatever and see if that gets your share up.  Search the other posts too, people have mentioned this very issue.  Also, try doing smbclient from terminal or mounting to make sure Samba is not horked up.

---

### Post by Uta on 2006-06-02
[QUOTE=s31523] Open a Nautilus window and hit Ctrl-L and type smb://198.168.whatever.whatever and see if that gets your share up.  Also, try doing smbclient from terminal or mounting to make sure Samba is not horked up.[/QUOTE]

I already had tried using smb://198.168.0.x and got the same error message as before but when I used smbclient via the terminal and did, 'smbclient -L ibookg4'
it listed the shares on that machine and repeated for the G5 it also was able to list the shares on that machine. I am not sure of the line command to mount a samba share via the terminal. Can you tell me? thanks.

---

### Post by s31523 on 2006-06-02
See the previous messages in this thread, I described my mount "work around" for this annoying problem. ](*,)

---

### Post by Uta on 2006-06-02
"smbfs: mount_data version 1919251317 is not supported"

This is the error message I got when I tried to mount the samba share via the terminal.

Interms of Samba what does this mean?

---

### Post by s31523 on 2006-06-02
Did you install smbfs in Synaptic?  If So, check out:
[http://lists.samba.org/archive/samba/2001-March/025870.html](http://lists.samba.org/archive/samba/2001-March/025870.html)

---

### Post by Uta on 2006-06-02
Ok, read the post, describes my issue, what's the fix ? Reinstall Samba via Synaptic.
I just upgraded to Dapper yesterday via an iso I had downloaded.

OK,
I installed the missing file and all is well now, I can mount the shares via the terminal but not via Nautilus.
Thanks for your HELP!

---

### Post by s31523 on 2006-06-02
> Ok, read the post, describes my issue, what's the fix ?
I was hoping someone in this joint could tell me that.  I think Nautilus has a bug, see the previous post with link to bug report that is similar to this issue.  For now I will have to live with doing the mount manually.  I will probably put a script on my desktop to do the mount via one click.

---

### Post by s31523 on 2006-06-04
More detailed workaround instructions:
[http://www.ubuntuforums.org/showthread.php?p=1091273#post1091273](http://www.ubuntuforums.org/showthread.php?p=1091273#post1091273)

---

### Post by daengbo on 2006-06-19
If you are having trouble with this, make sure that you take a look at /var/log/samba/* for the error connection. For me, Nautilus is trying to connect to the server as nobody, but the server doesn't allow guests, so it's denied. I have tried manually adding "Connect to Server" setups with the name, but this should be unnecessary as I already had this all set up.

My dhcpd.conf
# DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
        option routers 192.168.0.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 192.168.0.1, 168.126.63.1, 168.126.63.2;
        option netbios-name-servers 192.168.0.1;
        option ip-forwarding off;
        default-lease-time 21600;
        max-lease-time 43200;
    group {
...

My Samba conf
...
        preferred master = Yes
        domain master = Yes
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        hosts allow = 127.0.0.1 192.168.0.0/24
        hosts deny = 0.0.0.0/0
        domain logons = Yes
...
[Clipart]
        comment = Clipart
        path = /home/share/Clipart
        write list = @users
        force group = users
        read only = No
        create mask = 0664
        directory mask = 0775
        guest ok = No

---

### Post by maclaren on 2006-06-27
(This info is posted here in case it helps someone else.)

I too was having this problem: "smb:/// is not a valid location" and I finally found a solution. Yes, I could connect with Konqueror, and I could browse my Windows shares via the command line. Just Nautilus was broken.

In my case the root cause was that I was missing the library libgnomevfs2-extra. Here is its description:

"This package contains extra VFS modules for the GNOME virtual file system. Currently it includes:
 * the bzip2 module;
 * the smb module, to browse Windows shares."

I installed this library and now all is well and I can access my Windows server.

--rick

---

### Post by pt123 on 2006-10-10
Is this bug going to be fixed in Edgy?

---

### Post by NoWhereMan on 2006-10-11
looks like it's not :/
[http://ubuntuforums.org/showthread.php?t=274831](http://ubuntuforums.org/showthread.php?t=274831)
libgnomevfs2-extra is already installed please submit a comment to this bug if you find the provided workaround worked for you

[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/65136](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/65136)

bye

---

### Post by tagra123 on 2007-01-03
How to get nautilus and Windows to see samba share.

This problem occured after install a different router. I wouldn't call this a router problem since windows was able to figure out how to share with ubuntu. It was going the other direction.

Problem:

I would have to manually add 192.168.1.XXX a samba share using connect to server or  nautilus wouldn't be able to resolve or for that matter even see the share.

This guide assumes that you have already installed samba --  if not

please follow this guide --

[http://www.ubuntuforums.org/showpost.php?p=1174825&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1174825&postcount=1)

and then apply the changes below


Fix:
*** if smbusers (below) doesn't exist create it using  sudo touch /etc/samba/smbusers

```
sudo /etc/init.d/samba stop
```

Make backups of the files you are going to change


```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
sudo cp /etc/samba/smbusers /etc/samba/smbusers.bak
sudo cp /etc/hosts /etc/hosts.bak


```


```
sudo gedit /etc/samba.conf
```

Here's an example working smb.conf 

 ```

[global]
    ; General server settings


    smb ports=139
    
#replace myubuntusambaserver with your own server name
    netbios name = myubuntusambaserver
    server string =  %h server (Samba, Ubuntu)
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
   # wins support = yes

    printing = CUPS
    printcap name = CUPS

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


#replace mainsystemusername with your own samba username
# replace path with your own path
[mythwin]
    path = /media/winshares
  public = yes
  writeable = yes
    browseable = yes
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    force user = mainsystemusername
    force group = mainsystemusername




```

save and exit

next

```
sudo gedit /etc/samba/smbusers
```

add the following

```

#replace mainsystemusername with your own samba username
#replace someClientUsername  with a clients username
mainsystemusername="someClientUsername"
mainsystemusername="AnotherClientUsername"
# this lets one account name work for all sambas -- when asked to log in they need to know the username and password   


```


save and exit

if samba is restarted right now it you will bea able to see the shared folder, however when you click on it from nautilus, or windows, it will give a permissions error and / or some other error about not being able to connect.

To fix this do the following

```
sudo gedit /etc/hosts
```

Make it look similar to the example below.  Notice the very last line.

```

127.0.0.1 localhost.localdomain localhost
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
#replace myubuntusambaserver with your own server name
#replace 192.168.1.XXX with your own static ip ( I think you can use 127.0.0.1 for dhcp users)
#If your workgroup is not mshome replace it with whatever it is.

192.168.1.XXX myubuntusambaserver myubuntusambaserver.MSHOME

```


Finally
```
sudo /etc/init.d/samba restart
```

It should work now.


What seems to make it resolve in both windows and ubuntu is the line

in /etc/hosts:

127.0.0.1   hostname.domainname.com   localhost.localdomain   localhost

which we added as a seperate line called

192.168.1.XXX myubuntusambaserver myubuntusambaserver.MSHOME
----------------------------------------------------------------------------------------------
To undo any changes you made

```

sudo cp /etc/samba/smb.conf.bak /etc/samba/smb.conf
sudo cp /etc/samba/smbusers.bak /etc/samba/smbusers
sudo cp /etc/hosts.bak /etc/hosts


```

-------------------------------------------------------------------------------------------------

---

### Post by IamAcoconut on 2007-01-05
I wanted to ask what is mainsystemusername? Just the ordinary user? 
And does 'myubuntusambaserver' name exist anywhere outside these files you tell to edit? I mean I can name it whatever I like, or does it relate to something?
And what's the 'client's username'?

The questions might sound stupid, but if that's not the issue, than I've got no idea.
I did everything as you did, but I still don't see even the server name from my pc.
As I mentioned elsewhere I'm running Samba server on SuSE.

---

### Post by IamAcoconut on 2007-01-13
Any1?

---

### Post by tagra123 on 2007-01-14
#replace mainsystemusername with your own samba username
#replace someClientUsername  with a clients username

so lets say your login name on the machine you are sharing files from is abc123

replace mainsystem username with abc123 in your configuration
l
ets say on the computer you are trying to share files to (the client) username is def456

then

replace someClientUsername with def456


the smbusers file would then look like this

```
#replace mainsystemusername with your own samba username
#replace someClientUsername  with a clients username
abc123="abc123"
abc123="def456"
abc123="ghi789"

# this lets one account name work for all sambas -- when asked to log in they need to know the username and password
```

make sure abc123 has been added as a samba user

---

