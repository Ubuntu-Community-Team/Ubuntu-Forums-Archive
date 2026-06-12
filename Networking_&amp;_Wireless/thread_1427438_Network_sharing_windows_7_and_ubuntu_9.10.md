---
title: "Network sharing windows 7 and ubuntu 9.10"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by JAY6390 on 2010-03-11
Hi everyone,

I have a windows 7 network with two computers running on it, and both can see and access each other without any problem. I've also got a laptop with ubuntu 9.10 (Karmic Koala). The problem I'm having is getting the two to see each other (windows and linux that is) and wondering what sort of things I will need installed to get this working correctly. Ideally I want it so that in windows I can see the ubuntu laptop in the same workgroup as my windows machines (and need to enter a user/pass to access the files of a share on the laptop). If I can get this configured I will be happy. I am also wanting to be able to do the reverse and access windows machines via the laptop

I've tried to search for the windows machines on ubuntu by going to Network > Windows Network in the file explorer but it comes up with "Unable to mount location - Failed to retrieve share list from server"

Sorry if this is a noob question. I'm pretty new to the whole linux thing and appreciate any help I can get with this

(I have googled this quite a bit too but to no avail)

Many thanks in advance

Jay Gilford

---

### Post by thenailedone on 2010-03-19
Oh wow... one whole week without as much as a reply... and I have a similar question... can't seem to share files on my win 7 PC with my laptop running Lucid Lynx... so I am not very hopeful of getting an answer now :(

---

### Post by abohsin on 2010-03-19
Ok, 1 week with no reply is not good for our community.
This is what you do:
1. On ubuntu, install samba.
2. From ubuntu, browse Places > Connect to Server.
3. Enter the IP Address/name of your win 7 machine, share name or C$, if you want to access the entire drive, and necessary username/password.
4. Bingo, you are connected to win machine.

For sharing from ubuntu, try the following:
1. right-click any folder you wish to share.
2. Choose sharing options, check Share this folder.
3. Also check, Guest access, then confirm.
4. From windows machine, enter ubuntu address or machine name in file explorer as follows: \\ubuntu_machine\folder.
5. bingo, you are in.

Please tell us if this is useful, we share because we care.

---

### Post by thenailedone on 2010-03-19
Installed SAMBA, but the rest of the steps (first part, connecting to Win machine) did not work...

---

### Post by coffeecat on 2010-03-19
Once you've installed samba and set up a share on your Ubuntu machine, have a look at this link:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Take each point in turn. There's a couple of simple edits of smb.conf and nsswitch.conf to do, winbind to install (if not already installed), and your firewalls to check. That should be about it. It works fine for me.

The good news is that once you've installed samba all this seems to work out of the box in Lucid.

---

### Post by thenailedone on 2010-03-19
> **coffeecat said:**
> Once you've installed samba and set up a share on your Ubuntu machine, have a look at this link:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Take each point in turn. There's a couple of simple edits of smb.conf and nsswitch.conf to do, winbind to install (if not already installed), and your firewalls to check. That should be about it. It works fine for me.
[B]
The good news is that once you've installed samba all this seems to work out of the box in Lucid[/B].

Or not :( running the Lynx as I type and no luck after installing SAMBA...

---

### Post by coffeecat on 2010-03-19
> **thenailedone said:**
> Or not :( running the Lynx as I type and no luck after installing SAMBA...

I found in earlier versions of Ubuntu that it helped to create a folder for sharing in home, right-click on it to select 'sharing options', and set up a share. This installed samba for you. Whether it did some other configuration of smb.conf, I'm not sure. Perhaps you should set up a share on your Ubuntu machine.

Anyway. Just booted into Vista on my laptop and created a new shared folder. Within a couple of minutes I was able to access this from Places > Network and copy files to and from. And I haven't needed to go through the points listed in that link. Apart from setting up samba by creating a shared folder in Lucid, it's all as out of the box.

Last point. Firewall issues are the number 1 stumbling block in share problems. Check your Windows 7 firewall settings. And, have you enabled gufw/ufw in Lucid? That will block samba shares.

---

### Post by ricojonah on 2010-03-27
> **abohsin said:**
> Ok, 1 week with no reply is not good for our community.
This is what you do:
1. On ubuntu, install samba.
2. From ubuntu, browse Places > Connect to Server.
3. Enter the IP Address/name of your win 7 machine, share name or C$, if you want to access the entire drive, and necessary username/password.
4. Bingo, you are connected to win machine.

For sharing from ubuntu, try the following:
1. right-click any folder you wish to share.
2. Choose sharing options, check Share this folder.
3. Also check, Guest access, then confirm.
4. From windows machine, enter ubuntu address or machine name in file explorer as follows: \\ubuntu_machine\folder.
5. bingo, you are in.

Please tell us if this is useful, we share because we care.

Thank you! Your proposed solution worked for me.  After following your instructions, I was able to connect to my Windows 7 shares from my Ubuntu 9.10 system through the following methods:
[LIST]
[*]Using Places -> Connect to Server  (Successful using IP address AND hostname)
[*]Using the address bar on nautilus by typing smb://x.x.x.x (using the IP address) AND smb://host-name


[/LIST]

---

### Post by Tom.Molyn on 2010-03-27
> **JAY6390 said:**
> Hi everyone,

**I have a windows 7 network with two computers running on it, and both can see and access each other without any problem. I've also got a laptop with ubuntu 9.10 (Karmic Koala). The problem I'm having is getting the two to see each other (windows and linux that is) and wondering what sort of things I will need installed to get this working correctly. Ideally I want it so that in windows I can see the ubuntu laptop in the same workgroup as my windows machines (and need to enter a user/pass to access the files of a share on the laptop). If I can get this configured I will be happy. I am also wanting to be able to do the reverse and access windows machines via the laptop**

I've tried to search for the windows machines on ubuntu by going to Network > Windows Network in the file explorer but it comes up with "Unable to mount location - Failed to retrieve share list from server"

Sorry if this is a noob question. I'm pretty new to the whole linux thing and appreciate any help I can get with this

(I have googled this quite a bit too but to no avail)

Many thanks in advance

Jay Gilford


Ok this might help

There is a setting in windows 7 that only allows wndows 7 and vista to connect remotly

Try these steps
**1. **go to my computer and click on system propertys(on the top tabs)
**2. **Click on Remote settings on the left.(you should be in the remote tab in system propertys)
**3. **Click on Advance(under Remote Assistance)
**4. **uncheck[B] "Create invitations that can only be used from computers using windows vista or later"
5.  [/B]Test

Also there is a setting below the remote assistance called remote desktop witch may apply.
mine is set for the center box that is noted with a (**Less Secure**) and i can access my computer using Ubuntu Netbook Remix just fine.

---

### Post by karlatsaic on 2010-10-05
> **abohsin said:**
> Ok, 1 week with no reply is not good for our community.
This is what you do:
1. On ubuntu, install samba.
2. From ubuntu, browse Places > Connect to Server.
3. Enter the IP Address/name of your win 7 machine, share name or C$, if you want to access the entire drive, and necessary username/password.
4. Bingo, you are connected to win machine.
...

I'm running lucid/netbook remix and wanted a connection to an Iomega 1 TB StorCenter wireless NAS device, which is set up to share with my windows machines. All I had to do was enter the IP address, nothing else, and bingo is right! Thank you :guitar: I can also, under Netook Remix > Files and Folders, drill down to Network > Windows Network > Workgroup > Share > Folder)

---

### Post by karlatsaic on 2010-10-05
And one more comment, applicable to my lucid/netbook-remix setup. After I have clicked on a share to mount it, visible in the files and folders gui, if I wish to reference the share from the command line or a script, it is in ~/.gvfs/shareName

---

