---
title: "can't share (samba) from NTFS drive"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by xenton on 2010-09-15
Hi Everyone, 

I am very new to Ubuntu, I managed to install samba and it's GUI. I tried to share a directory within the pictures folder (at home/mark/pictures/share) just as a test. I had everything set up right, but it was inaccessible from a windows XP machine on my network. After some digging I found the problem lay with the permissions of it's parent folder. I right clicked on the parent folder then clicked properties, then clicked on the permissions tab. I changed the permissions for others and it's working fine.

I'm having the same problem now but with a share on a NTFS drive called storage. I cannot change the permissions for the shared folder or any of it's parents by right clicking. Any changes I make revert immediately back to their previous setting.

Is there any way to change the permissions to allow read access to everyone?

---

### Post by dmizer on 2010-09-16
Is the storage drive a USB external drive? If so, you will have to create a mount pont for the drive in /etc/fstab in order to set the correct local file permissions.

---

### Post by xenton on 2010-09-16
No, it's on a RAID array that consists of 2 internal SATA drives (it's not the same array as my Linux install if that makes a difference).

Thanks for your reply

---

### Post by dmizer on 2010-09-16
I see. Well, please post your /etc/fstab and highlight the section which contains the mount point for your raid array.

---

### Post by xenton on 2010-09-16
Here we are:
 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
 
proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/mapper/nvidia_abjcfaad3    /    ext4    errors=remount-ro    0    1
/dev/mapper/nvidia_abjcfaad2    /media/Seven    ntfs    defaults,nls=utf8,umask=0222    0    0
***[COLOR=orange]/dev/mapper/nvidia_jjeidcec1    /media/Storage    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0[/COLOR]***
/dev/mapper/nvidia_abjcfaad1    /media/XP    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/mapper/nvidia_abjcfaad5    none    swap    sw    0    0
```

---

### Post by xenton on 2010-09-21
Anybody have any ideas?

---

### Post by dmizer on 2010-09-21
Try this instead:
```
/dev/mapper/nvidia_jjeidcec1 /media/Storage ntfs-3g defaults,locale=en_US.utf8 0 0
```

Found here -> [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Note the "Known issues" section.

---

### Post by xenton on 2010-09-23
Right, I used the NTFS Config. GUI to setup my NTFS drives since my last post so my fstab entries are now as in your last post. I booted into windows and changed the permissions to give 'everyone' full access for the folders I'm trying to share.
Back in Lucid I've checked the permissions tab of the properties for the folders and it seems to reflect the changes, it now matches the successful ext 4 share I have working but still no joy.

---

### Post by Morbius1 on 2010-09-23
If your fstab entry matches dmizer's this shouldn't be an issue but just in case post the permissions of the shared directory:
```
ls -dl /media/Storage
```

For the Samba part why not post your smb.conf:
```
testparm -s
```

---

### Post by xenton on 2010-09-23
These shares were added via the samba GUI, I just tried to add them by right clicking and got an error
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-FolderSharing.png[/IMG]
I think I could be onto something here

---

### Post by Morbius1 on 2010-09-23
Ah. You've got two choices. You could make a change to smb.conf to accommodate the fact that root owns the partition or you could take possession of the partition yourself. 

Let's take the second option:
If your fstab entry looks like this:
```
/dev/mapper/nvidia_jjeidcec1 /media/Storage ntfs-3g defaults,locale=en_US.utf8 0 0
```Add one more option - uid=1000 so that it looks like this:
```
 /dev/mapper/nvidia_jjeidcec1 /media/Storage ntfs-3g defaults,uid=1000,locale=en_US.utf8 0 0
```Then in a terminal:
```
sudo umount /media/Storage
``````
sudo mount -a
```Then use nautilus to try and share the folder again.

---

### Post by xenton on 2010-09-23
OM actual G!
[IMG]http://209.85.48.8/228/109/upload/p4193510.gif[/IMG]
I have my NTFS shares working from within Ubuntu!

After setting the correct permissions (I just gave full control to everyone, maybe that just everyone needs read permission to read, write permission to write, will look into this further)
Then added then line usershare owner only = false to the global section of smb.conf and restarted the samba service.

Off to bed now will investigate the permissions further tomorrow and will submit another guide.

[Morbius1]("http://ubuntuforums.org/member.php?u=982144") -  was so excited didn't see your reply - thanks. Does ```
uid=1000
``` just make me the owner as opposed to root? and does the line ```
sudo mount -a
``` just remount everything from fstab?

---

### Post by Morbius1 on 2010-09-23
This might not be an issue with you in particular but I try to avoid the usershare owner only fix because it gives every local user on your system the ability to share anything on the system. If you are the only user then it's not an issue.

BTW, that error message is in my opinion one of the best written error messages in all of computerdom. It not only tells you what the problem is it tells you how to fix it. If they all did that there would be no need for a support forum. :P

---

### Post by xenton on 2010-09-23
It's not an issue at the present as I am the only user, but I can see your point and may well change it anyway, modifying the fstab is just as easy and seems more the 'correct method.'

Yeah, that error message was ace, only reason I didn't see it sooner was because adding a share in the samba GUI doesn't generate the error message.

---

### Post by xenton on 2010-09-23
yay!

---

### Post by xenton on 2010-10-02
Right thanks everyone for your help though I'd throw together a HOWTO on this now I've got it working:

Firstly if you haven't already, you need to get your NTFS drives working in Ubuntu. The method outlined below will mount all your drives automatically on startup.

Click on*** Applications > Ubuntu Software Centre*** then type NTFS in the search box, install NTFS-3g and the NTFS Configuration Tool you can see them here in my list of installed software:

[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/one.png?t=1286029432[/IMG]


Now Click*** System > ****Administration> NTFS Configuration Tool*** and check the 'enable write support for internal devices' checkbox
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/2systemadminNTFSConfigToolEnablewritesupport.png?t=1286029941[/IMG]
Ubuntu can only share that which it owns, and at the moment your NTFS drives are owned by root, we need to change this;

Open a terminal and type

```
sudo gedit /etc/fstab

```You must add  
uid=1000
to any line that refers to an NTFS drive so my fstab was this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/mapper/nvidia_abjcfaad3    /    ext4    errors=remount-ro    0    1
/dev/mapper/nvidia_abjcfaad2    /media/Seven    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_jjeidcec1    /media/Storage    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad1    /media/XP    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad5    none    swap    sw    0    0
```and becomes this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/mapper/nvidia_abjcfaad3    /    ext4    errors=remount-ro    0    1
/dev/mapper/nvidia_abjcfaad2    /media/Seven    ntfs-3g    defaults,uid=1000,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_jjeidcec1    /media/Storage    ntfs-3g    defaults,uid=1000,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad1    /media/XP    ntfs-3g    defaults,uid=1000,locale=en_GB.utf8    0    0
/dev/mapper/nvidia_abjcfaad5    none    swap    sw    0    0
```click ***File>Save ***then exit gedit.

Ubuntu won't share the files unless it has the correct permissions, and at the time of writing, setting permissions for NTFS volumes wasn't possible from within Ubuntu. So, restart your computer and boot into windows XP. 

You must first disable simple file sharing:

Click ***Start>Control Panel ***if you are in classic view you will see the following screen and simply double click ***folder options***
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/folderoptionsclassicview.jpg?t=1286031444[/IMG]
If you are in the category view you will see this screen:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/folderoptionscatview1.jpg?t=1286031639[/IMG]

Click on ***Appearance and Themes*** to get to this screen:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/folderoptionscatview2.jpg?t=1286031913[/IMG]
Now click on ***Folder Options*** to open the following dialogue box:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/2folderoptionsdialogue.jpg?t=1286037532[/IMG]

Click on the ***view*** tab then scroll down to '***Use simple file sharing (Recommended)***' Click apply.

Now navigate to the folder you want to share from within Ubuntu, ***right click*** on the folder then click on ***properties*** you will see something similar to the image below, in this example I am sharing a folder called complete:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/1folderproperties1.jpg?t=1286037966[/IMG]

We are going to give full control to 'Everyone' [SIZE=1](please note I have only tried giving full control to everyone and this is the only tested working solution I have tried, other combinations of read/write control may work, I have not tried)[/SIZE] in most cases we must create the group 'Everyone'.  Click the Security tab then click Add... you will get a dialogue box similar to this:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/2addeveryone.jpg?t=1286038628[/IMG]
Click in the large box at the bottom and type ***everyone*** then click on ***Check Names*** then click on ***OK ***

---

### Post by xenton on 2010-10-02
this will return you to the previous dialogue:
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/3giveeveryonefullaccess.jpg?t=1286040877[/IMG]
Click on ***Everone*** then click in the check box to allow ***full control*** then click on ***apply***.

You can then click OK and then reboot into Ubuntu

Now open the software centre again and search for samba, install the **'samba'** and '**GUI for managing samba shares and users'**.

Now click ***System>Administration>Samba*** then click [I][B]Preferences>Server Settings...
[/B][/I]You will see something similar to this
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-ServerSettings.png?t=1286041438[/IMG]
Change the Workgroup name to the correct name (as used by the rest of your network) then click*** OK.*** Back at the main Samba GUI as pictured below, click the green + to add a share:
Click ***browse*** and locate the folder we have just changed permissions for in XP then check visible, and optionally check writeable. 
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-CreateSambaShare.png?t=1286041960[/IMG]
Click on the access tab and grant access to 1 or more specific users or allow access to everyone (In which case anyone connected to the network will be able to view, and if you selected writeable, modify your files)
[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-CreateSambaShare-1.png?t=1286042162[/IMG]
Click ***OK*** then exit the Samba GUI. Job done, you may need to restart Samba or reboot.

Working for me from within Lucid sharing to an XP laptop and an Xbox running XBMC.

Massive thanks to [[COLOR=#d40000]**dmizer_[B] [COLOR=Black]and[/COLOR] **_[/B][/COLOR]]("http://ubuntuforums.org/member.php?u=77219")[URL="http://ubuntuforums.org/member.php?u=982144"] Morbius1  [COLOR=Black][/COLOR]
[/URL]

---

### Post by Morbius1 on 2010-10-02
Hope you don't mind some constructive criticism but the second half of the following statement is not correct:
> Ubuntu won't share the files unless it has the correct permissions, and [COLOR=Blue] at the time of writing, setting permissions for NTFS volumes wasn't  possible from within Ubuntu[/COLOR].I can create a line in fstab that looks like this:
> /dev/sda1 /windows/WinXP  ntfs    defaults,nls=utf8,umask=027,gid=46 0       0The umask=027 determines the permissions of the partition and in this case it will allow the owner ( which is root ) full access ( the first "0" ), the group ( which is the gid=46 - representing all local login users) read only access ( the second "2") and no access to everyone else ( the last "7" ). You can also change the ownership using uid and group using gid. 

So while it's true that you cannot use the linux commands of chown or chmod to alter the ownership or permissions of an already mounted NTFS partition, you are in complete control of ownership and permission at time of mount.
> You must add  
uid=1000
to any line that refers to an NTFS drive so my fstab was this:It is true that Nautilus-share ( usershare ) can only share something it owns thus making it necessary to take ownership of the mount point ( the uid = 1000 part ). But your resulting howto has abandoned Nautilus-share in favor of Classic-share ( ***System>Administration>Samba ***)

Two entirely different methods of using Samba to share Folders. You have to be root to share a folder using Classic-shares and are therefore not bound to any ownership restrictions.

---

### Post by xenton on 2010-10-02
I welcome the criticism, I am very new and still learning.

I think I meant to put that it is not possible to change permissions of files and directories on an NTFS volume, poor wording, sorry.

If I allowed full access to the volume using the method you suggeted, would that grant full access to all the files and folders within that volume, completely negating the need to change permissions from within a windows OS?

I had a mixture of usershare and classic shares and neither worked until I changed the permissions (in windows) and added the uid=1000 line in fstab afterwards both worked. I simply prefer the classic share as it lists all the sahres in one windows and I just find it easier to work with.

Thanks very much for you reply and if you could answer the above I would be very grateful.

---

### Post by Morbius1 on 2010-10-02
> If I allowed full access to the volume using the method you suggeted,  would that grant full access to all the files and folders within that  volume, completely negating the need to change permissions from within a  windows OS?
Yes. Unlike the mounting of a linux filesystem all of the files and directories of a mounted Windows filsystem inherit the ownership and permissions of what you specified in fstab. 

[COLOR=Blue] EDIT: Actually you already had it set up that way:[/COLOR]
> /dev/mapper/nvidia_abjcfaad1    /media/XP    ntfs-3g    defaults,locale=en_GB.utf8    0    0I'm not familiar with the /dev/mapper/nvidia... designation but the "defaults" used in that line has an embedded umask=000. So all your files and folder when accessed locally will have permissions for everyone to read and write. How you configured your shares would have determined if the remote user could have accessed them.
> I simply prefer the classic share as it lists all the sahres in one windows and I just find it easier to work with.Classic-shares have much more flexibility and power but can also be much more complex to set up. Depending on the need Nautilus-shares are the easiest to set up and you can always get a listing of what nautilus-shares you have and how they are set up by issuing the following command:
```
net usershare info
```

---

### Post by xenton on 2010-10-03
> **Morbius1 said:**
> Yes. Unlike the mounting of a linux filesystem all of the files and directories of a mounted Windows filsystem inherit the ownership and permissions of what you specified in fstab. 


Well that's fantastic, thank you very much for pointing that out, not having to keep booting into Windows to change permissions is a great relief.

> [COLOR=Blue]EDIT: Actually you already had it set up that way:[/COLOR]
I'm not familiar with the /dev/mapper/nvidia... designation but the "defaults" used in that line has an embedded umask=000. So all your files and folder when accessed locally will have permissions for everyone to read and write. How you configured your shares would have determined if the remote user could have accessed them.

The /dev/mapper/nvidia... designation is just pointinf at a RAID array rather than a physical drive. When I had it set up like this (I believe root was the owner) trying to usershare generated an error:

[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-FolderSharing.png[/IMG]
In was actually you who sugested adding the line uid=1000 which would make the current user the owner solving the problem as editing the smb.conf was less secure.

My classic shares started to work after this as well (though it may of been a permission issue with those, as I changed the folder permissions at the same time).

if the ***default*** option in fstab grants read and write access, could it be that full access is needed?

> Classic-shares have much more flexibility and power but can also be much more complex to set up. Depending on the need Nautilus-shares are the easiest to set up and you can always get a listing of what nautilus-shares you have and how they are set up by issuing the following command:
```
net usershare info
```

I currently have an NTFS drive with no shares on it, so I am going to do a few test shares see exactly what is and isn't needed.

Thanks again for all your help. That Guide will be a lot shorter, shortly :P

---

### Post by Morbius1 on 2010-10-03
> In was actually you who sugested adding the line uid=1000 which would  make the current user the owner solving the problem as editing the  smb.conf was less secure.Right, two different methods of using Samba. 

In classic-shares you are sharing files as root and root has access to everything. 

Nautilus-shares is the gnome implementation of samba "usershares" and by definition it only allows a user to share things he owns. So with usershares you either need to take possession of the folder / mountpoint ( for an NTFS / FAT32 filesystem that means a uid=1000 ) or you need to edit smb.conf to allow usershares to share anything.

---

### Post by xenton on 2010-10-03
> **Morbius1 said:**
> Right, two different methods of using Samba. 

In classic-shares you are sharing files as root and root has access to everything. 

Nautilus-shares is the gnome implementation of samba "usershares" and by definition it only allows a user to share things he owns. So with usershares you either need to take possession of the folder / mountpoint ( for an NTFS / FAT32 filesystem that means a uid=1000 ) or you need to edit smb.conf to allow usershares to share anything.

Right, I've got it now, thanks for being so patient and clear with me :P.

---

### Post by Objekt on 2012-02-07
I know this thread is almost 2 years old and all but...

OMG THANK YOU SO MUCH!

I've been banging my head against Samba/file sharing in general almost since I started using Linux back in 2008.

Only just today, with the help of this thread and and a similar one also in these forums, did I finally get it to work the way I wanted from the beginning!

---

### Post by xenton on 2012-02-09
I'm glad it helped you. I was dual booting and ending up going entirely back to windows. I just couldn't sync to my mobile device, it was a windows mobile device, there were a handful of program's that should of done the job, but I couldn't configure them correctly, and in the end the community which was the main plus to Ubuntu became the reason I left. I just got so much abuse for wanting to try and sync a WinMo device. I have an evil apple device now and it syncs directly with my hotmail account so I might give it another go.

---

### Post by Objekt on 2012-02-12
I hear you.  I took a long Ubuntu hiatus, because I was having some weird hardware and/or software issues that just couldn't be solved (mainly, VLC Media Player would lose audio/video sync inexplicably).

I just set up a home "media server" and I used Linux Mint 12, not Ubuntu.  Ubuntu's lost me because it's now spent several releases flailing about with "new and improved" GUI garbage.  Instead they should be fixing basic OS functions that Windows users take for granted, and which generally work smoothly.  But that's not the way Ubuntu is going.

FWIW, I was able to share NTFS volumes from the new Linux Mint 12 machine in a jiffy, using the method of this thread.

---

