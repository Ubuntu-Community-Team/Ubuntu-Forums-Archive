---
title: "Trouble with Samba Shares (Ubuntu to Ubuntu)"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by Rubicon421 on 2011-09-05
I'm having problems accessing shares between two machines both running Ubuntu 11.04. I tried most of the suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

and after none of that worked I started trying the "complete removal" option in Synaptic. I thought I reinstalled all Samba components that I had uninstalled, but now I can't open the samba config tool. It shows up in the programs menu and even asks for a password when I click it but thats as far as it goes. It's now doing this on both of the systems. 

So, what I'd like to do is figure out EVERYTHING Samba related to uninstall/delete so that I can start fresh without doing a reinstall of the whole OS. Could someone please give me a list of packages to remove and what config files to delete?

Thanks!

---

### Post by Rubicon421 on 2011-09-05
Well, I figured out that the Samba config GUI wasn't opening because I deleted the smb.conf file and for some reason, reinstalling Samba didn't create a new file. 

A created a blank smb.conf and now Samba config opens again on both machines. It's not saving my shares that I add though and the smb.conf file is still blank.

---

### Post by Morbius1 on 2011-09-05
smb.conf isn't installed from the "samba" package it's installed from the "samba-common" package because it's used by the samba client as well as the samba server.

You have a copy of it already installed ( or should have ) at the following location:
> /usr/share/samba/smb.confJust copy it to the correct location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```And then make the following correction:

Find the line:> encrypt passwords = false[COLOR=#0000ff]*Could also be listed as "no"*[/COLOR]

and change it to:
```
encrypt passwords = true
```Then restart samba:
```
sudo service smbd restart
```

---

### Post by Rubicon421 on 2011-09-05
I restored the copy as you suggested but


```
sudo service smbd restart
```[/QUOTE]

  yields

restart: Unknown instance:

---

### Post by Morbius1 on 2011-09-05
If it's not already started you need to start it:
```
sudo service smbd start
```

Sorry, should have mentioned that.

---

### Post by Rubicon421 on 2011-09-05
I just restarted both machines. I still can't access the shares though. I have one folder shared on each machine, and from either machine trying to access the other's share, I get:

Unable to mount location
Failed to mount windows share

---

### Post by Morbius1 on 2011-09-05
[1] Let's make sure samba itself works by accessing the remote machine by ip address instead of by name:
```
nautilus smb://192.168.0.100
```Change the ip address to match the remote machine.

[2] Disable any firewall that you have on each machine. Note: if you haven't done anything to the firewalls then it should be OK as it is.

[3] Please post the output of the following commands from the machine you are on:
```
smbtree
``````
hostname
```

---

### Post by Rubicon421 on 2011-09-05
Could not display "smb://192.168.0.18/".
Error: Failed to retrieve share list from server
Please select another viewer and try again.

smbtree:
 is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

hostname:
droid

---

### Post by Morbius1 on 2011-09-05
That's not good.

Please post the output of this command:
```
testparm -s
```

---

### Post by Rubicon421 on 2011-09-05
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = TOOL
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
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

---

### Post by Morbius1 on 2011-09-05
Go into synaptic and install or if it's already there reinstall the following packages:
```
samba-common
samba-common-bin
gvfs-fuse
libsmbclient
smbclient
```If you have any Samba4 packages installed remove them.

You stall have "encrypt passwords" set to no so you'll have to change that to yes.

Then restart or start smbd again.

---

### Post by Rubicon421 on 2011-09-05
just finished making the package changes you suggested on both machines... still getting the same error though.

---

### Post by Rubicon421 on 2011-09-05
the results from smbtree are looking better though

TOOL
    \\VAIO-MINT11            vaio-Mint11 server (Samba, Ubuntu)
        \\VAIO-MINT11\IPC$               IPC Service (vaio-Mint11 server (Samba, Ubuntu))
        \\VAIO-MINT11\Print_to_PDF       Print to a PDF File
        \\VAIO-MINT11\print$             Printer Drivers
        \\VAIO-MINT11\yp                 
    \\DROID                  droid server (Samba, Ubuntu)

---

### Post by Morbius1 on 2011-09-05
OK, so what happens when you issue the following command:
```
nautilus smb://vaio-mint11/yp
```

---

### Post by Rubicon421 on 2011-09-05
Could not display "smb://vaio-mint11/yp/".
Error: Failed to mount Windows share
Please select another viewer and try again.

---

### Post by Morbius1 on 2011-09-05
And is this still broke:
```
nautilus smb://192.168.0.18
```

---

### Post by Rubicon421 on 2011-09-05
Yes, it didn't do anything when I tried it as you had it written. But then I retried it with a / at the end, and got the same error.

---

### Post by Rubicon421 on 2011-09-05
I've made so many changes and followed so many forums/guides on fixing this that there's no telling what is set wrong now. I'd really like to just wipe everything samba related and start over.

---

### Post by Morbius1 on 2011-09-05
These packages:

samba-common
samba-common-bin
gvfs-fuse
libsmbclient
smbclient
Plus the package samba itself is all things samba.

If you followed the HowTo you noted above you also did some bugga-bugga stuff with nsswitch and winbind that should be undone to bring you back to the factory fresh state.

---

### Post by Rubicon421 on 2011-09-05
so I should mark all of those for COMPLETE REMOVAL, then reinstall? What about the config files left behind?

---

### Post by Morbius1 on 2011-09-05
You can try that but I wouldn't wory about any config files left behind. The only one left is smb.conf and except for that "encrypt password" line it looks just the way it would right after an OS install.

---

### Post by Rubicon421 on 2011-09-05
when I select libsmbclient for removal it warns that it's going to remove a bunch of other non-samba related packages that I want to keep like VLC and acidrip. Are you sure I need to get rid of that one?

---

### Post by Morbius1 on 2011-09-05
Sorry, forgot about that. I never had to remove all of samba before and I didn't do my homework first. I don't think this strategy of purging all things samba and adding them back is going to work. None of the other packages have anything that can be modified except samba-common.

---

### Post by Rubicon421 on 2011-09-05
could any packages that you haven't mentioned be interfering with Samba? There are a few other packages that I added while I was trying to get this working. Basically, anything that showed up in synaptic when I searched Samba or SMB if it sounded like it might help.

---

### Post by Rubicon421 on 2011-09-05
I performed a complete uninstall/reinstall of all the packages you listed except libsmbclient on both machines. Then I re-enabled the shares in Samba and still get the same error. I have a few less computers showing up on the network right now as well. I think something that I uninstalled must have marked other dependancies for removal with it, but then reinstalling that package didn't add back everything it removed. 

I may just end up doing a restore... on both :(

---

### Post by Morbius1 on 2011-09-05
There is something fundamentally wrong with samba on your machine since worst case samba will always work when you bring it down to the ip address level.

> Basically, anything that showed up in synaptic when I searched Samba or SMB if it sounded like it might helpThat's was a dangerous thing to do. I searched for samba in synaptic and it listed all sorts of things ( winbind, sadms, etc.. ) that have no place in a home LAN. 

It's hard to tell what happened there. You might want to boot into your Mint Install DVD ( do not install ) that has both samba server and samba client already installed and functional from the DVD itself and see if you can access VAIO-MINT11's share. Then you'll know if there's something wrong with your network or something you did to droid that's the problem.

---

### Post by Rubicon421 on 2011-09-05
great idea with the LiveCD test to see if the VAIO share is set up right! I'll give it a shot and let you know.

---

### Post by Rubicon421 on 2011-09-05
still no luck connecting to the VAIO when I booted the DROID machine from a LiveCD. But at least I know the problem is on the VAIO.

---

### Post by spider_0k on 2011-09-05
I have had many issues with SAMBA, I'm sure mostly my doing. However my greatest success was using [Webmin]("http://www.webmin.com/")  , not just for samba NFS too. Additionally if you have more than one machine you can administer those remotely too.

Philip

---

### Post by Rubicon421 on 2011-09-06
> **spider_0k said:**
> I have had many issues with SAMBA, I'm sure mostly my doing. However my greatest success was using [Webmin]("http://www.webmin.com/")  , not just for samba NFS too. Additionally if you have more than one machine you can administer those remotely too.

Philip

Webmin looks interesting. Kind of like a FreeNAS interface for Linux. I would much rather just have Samba working properly first though. It worked fine in earlier versions of Ubuntu.

---

### Post by Rubicon421 on 2011-09-06
As a last ditch effort to solve this problem, I'm going to try to describe it a bit better and see if anyone catches something we may have missed.

System 1 (droid): LinuxMint 11 (2.6.38-10 kernel) Gnome 2.32.1 on Intel Q6600
System 2 (vaio-Mint11): LinuxMint11 (2.6.38-8 kernel) Gnome 2.32.1 on Intel Core2 Duo T7500

Neither machine is behind a firewall. They are on the same router and none of the default network settings have been changed. 

I have enabled shares from both machines via system-config-samba and via the Nautilus context menu sharing option. 

When opening the Network folder in Nautilus from either machine, I can see the other system in two places. The other machine shows up in the root of the Network folder at network:///

-and when I double click the Windows Network folder, then the TOOL workgroup, I see both machines again. 

In either case, double clicking the icon for one of the machines goes to 
smb://droid/   or    smb://vaio-mint11/

I can also navigate to either machine from the other via the IP in Nautilus. In all three cases (from either machine trying to access the other) I am successfully able to open the folder that's one level up from the shares. On the vaio, I have a shared folder called "yp" as well as the print$ that is created automatically. I can open the folder that shows both those icons, but I can't open the individual shares. 

I get the following error when doubleclicking the individual shares or when trying to connect directly via the location bar or command line by typing the path:

Unable to mount location
Failed to mount Windows share

---

### Post by Morbius1 on 2011-09-06
> **Rubicon421 said:**
> still no luck connecting to the VAIO when I booted the DROID machine from a LiveCD. But at least I know the problem is on the VAIO.
Even if you try to connect to VAIO by ip address?
```
 nautilus smb://192.168.0.18
```Can you even ping VAIO by ip address:
```
ping 192.168.0.18
```If the answer is no then I'm beginning to wonder if there's a problem with your router or perhaps an encrypted home directory or something I'm not smart enough to consider yet.

---

### Post by Rubicon421 on 2011-09-06
Ping response was almost instant:
PING 192.168.0.18 (192.168.0.18) 56(84) bytes of data.

So no problem there. Neither side has an encrypted home directory.

BTW, the IP was typed correctly- but the forum saw an 8 next to a ) and decided to turn that into a smiley for me.

---

### Post by Morbius1 on 2011-09-06
Looks like we posted past each other.
> Unable to mount location
Failed to mount Windows shareThat's a different error than before. That error isn't a samba error it's a Linux Permissions error.

What are the ownership and permissions on the VAIO folder represented by the "yp" share? You need to find that out from the VAIO box itself not from droid.

EDIT: The command from VAIO would be:
```
 ls -al /path/to/yp/folder
```

---

### Post by Rubicon421 on 2011-09-06
Owner: Create and Delete
File Access: --

Group: vaio
Folder Access: none
File Access: --

Others:
Folder Access: none
File Access: --

And for some reason I can't change any of these settings with the drop down menus. When I select something different it reverts back to the original value.

---

### Post by Morbius1 on 2011-09-06
Sounds like an ntfs or FAT32 partition to me. 

On VAIO edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - right uner the "workgroup" line:
```
force user = morbius
```[COLOR=Blue]*Change morbius to the login user name you use on VAIO.*[/COLOR]

Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Note: Every time smbd is restarted the network has a fit so wait a few minutes - seriously - like about 5 minutes - for things to settle down before trying to access the yp share from droid.

---

### Post by Rubicon421 on 2011-09-06
Just now saw your edit. I'm on the other machine now but I ran the ls -al command and it listed:


drwx----- 1 vaio vaio

drwx----- 1 vaio vaio

-rw----- 1 vaio vaio [file name]-repeated for all files

---

### Post by Rubicon421 on 2011-09-06
Yes, the yp folder is on an NTFS partition. Does that have something to do with the problem?

Why change the user name to morbius though?

---

### Post by Morbius1 on 2011-09-06
With an NTFS partition that is mounted trough Nautilus it will mount with only you having access. The remote user is not you so when he tries to access the share he will be blocked. "force user" will create a mask that converts the remote user to you so that he can see and access the share.

Given your last posts it looks like the owner is "vaio" so the line in VAIO's smb.conf would be :
```
force user = vaio
```

---

### Post by Rubicon421 on 2011-09-06
I added the line

force user = vaio

and restarted the vaio, then restarted samba and nautilus on droid. Now the vaio doesn't show up in the network folder on the droid machine. So I connected to it via the IP address in the nautilus location bar and got an empty folder

---

### Post by Morbius1 on 2011-09-06
> and restarted the vaio ..... So I connected to it via the IP address in the nautilus location bar and got an empty folder     
Did you mount the ntfs partition on VAIO before you tried to connect to it from Droid? 

If you did and it's still blank then from VIAO post the utput of the following commands please:
```
testparm -s
``````
net usershare info --long
```

---

### Post by Rubicon421 on 2011-09-06
SUCSESS!!!!!

Finally got it. That was it. I needed to re-mount the NTFS partition after I restarted. So your tweak to the smb.conf file is what fixed it, it just didn't work at first because I had to remount.

Thanks for your help man!

---

### Post by Morbius1 on 2011-09-06
Whew ;)

---

### Post by Rubicon421 on 2011-09-06
My sentiments exactly! I don't see a way to add rep points or thank you in the forums. BUT THANK YOU!

---

