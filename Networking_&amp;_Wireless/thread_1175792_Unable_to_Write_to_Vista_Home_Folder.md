---
title: "Unable to Write to Vista Home Folder"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by PerfectReign on 2009-06-01
I have a laptop running 9.04 with Gnome. I use the laptop at work (Active Directory) while plugged in and at home (simple home network) while running wireless.

I have SMB loaded and configured to allow me access to Windows printers and files. On my work Vista machine I can open any directory and write to them. There are some which show up in Nautilus as locked folders but I am able to write. 

I connect to my work computer using an smb bookmark: smb://domain\user@10.10.10.10/c$

This gets me all over the computer.

At home I use a similar syntax smb://user@192.168.0.103/c$ 

However, I can write/read all files outside of the given user's documents folder.  What gives?  I can even create folders off the C: drive, whihc I do, then use remote desktop to "move" them into the appropriate location.

---

### Post by PerfectReign on 2009-06-01
Here's an example of what I see. I'm in the folder but unable to create/edit anything...

---

### Post by dmizer on 2009-06-01
Please see the 6th link in my sig.

---

### Post by anonymousturtle3 on 2009-06-02
Try running "sudo nautilus" (w/out quotes) in your terminal and browse to the Vista home folder. When my menu looks like the one in your picture, this usually fixes that (because you are running it as root which has all privileges.) I'm not sure how far root's permissions go onto a network, I guess it is how it is configured. If you don't want to do a command line entry every time you need to write to a file on that network, you can go to:

[http://gnome-look.org/content/show.php/Nautilus+Scripts+Pack?content=90330](http://gnome-look.org/content/show.php/Nautilus+Scripts+Pack?content=90330).

Download the file and untar it, then move the files to your /.gnome2/nautilus-scripts (it's a hidden folder in your home directory; press ctrl-H to see it) and there will be a right-click menu item called "Scripts" and under that there will be a script called "Rootilus" which just opens the current window that you are in in nautilus as root in a new window. It's quite convenient.

I hope that helped.

---

### Post by dmizer on 2009-06-02
> **anonymousturtle3 said:**
> Try running "sudo nautilus" (w/out quotes) in your terminal and browse to the Vista home folder.

Never do this. Running Nautilus as root is an extreme security hazard.

---

### Post by anonymousturtle3 on 2009-06-02
> **dmizer said:**
> Never do this. Running Nautilus as root is an extreme security hazard.

You're probably right since we're talking about a network here.
I hadn't thought about that.
Ubuntu does have good security, however, and I have not had any issues so far with it (probably because I don't run sudo nautilus on a home network).

---

### Post by dmizer on 2009-06-02
> **anonymousturtle3 said:**
> You're probably right since we're talking about a network here.
I hadn't thought about that.
Ubuntu does have good security, however, and I have not had any issues so far with it (probably because I don't run sudo nautilus on a home network).

Yes, aside from the obvious direct root access hole you open up, there's a good chance that a [failed drag/drop](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/50977) could hose the system. To say nothing of the fact that running Nautilus as root only fixes the symptom not the actual problem.

---

### Post by PerfectReign on 2009-06-02
I read through it.

It appears interesting. However...

1. I don't have an issue browsing the smb/cifs shares. I do a connect using the ip address.

2. I am able to conect and browse through other folders on the smb mounts. Also, it works fine on my one vista desktop but not my wife's vista desktop.

3. I don't really want to use fstab since I'm dynamically connecting to these shares. I have one at home - WORKGROUP - one at work - VIMS - one at a remote office - ASSESSOR -and one at my father in law's house - PARKY.  (I hadn't brought up the others yet.)

---

### Post by dmizer on 2009-06-02
Yes, oddly enough ... using the fix I proposed above (not using /etc/fstab) may still fix your problem.

Alternatively, you'll need to look into the Vista share/firewall/UAC configurations.

---

### Post by PerfectReign on 2009-06-03
Okay, did what you said - in both manual mount and fstab.  In both cases, I get a directory mounted at /media/windows.  It is set to the root (C:\) of the vista machine. 

I can make folders or whatever at that level. As soon as I go into c:\users I'm unable to write.

I checked the permissions on the Wintendo box and the user - who's credentials I''m authenticating against - has full control over the folders.

Ideas?

# added 20090603 kai to mount lilly's computer
//xwing/c$    /media/windows        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

.smbcredentials has 

username=lilly
password=<her password>


I even included the blank line after the mount command in fstab.

---

### Post by dmizer on 2009-06-03
Please post the output of the following command:
```
smbtree
```

Edit:
Just found this out.

If your trying to connect to Vista, you will not be able to connect to any UAC protected drive/directory. Because of this, sharing the entire drives will not give you access (unlike it did in XP). Believe me when I say ... this is a very good thing. You don't want your entire system hanging out there for all to see.

Instead, share a single folder that your Vista user has control over. More information here: [http://www.vistax64.com/vista-security/103790-access-denied.html](http://www.vistax64.com/vista-security/103790-access-denied.html)

---

### Post by PerfectReign on 2009-06-03
Thank you for all your help.

Here is the output:

[FONT=Courier New]kai@r2d2:~$ smbtree
Password: 
WORKGROUP
    \\XWING                  
kai@r2d2:~$ 


[FONT=Arial]As for the home folder. The machine has file sharing turned off. I'm connecting using the local username and password so shouldn't (AFAIK) need file sharing. I'm kind of anal about sharing. My home network has a very strong encryption and the wifi does not broadcast the SSID.  I also share nothing from my Wintendo computers. (This is how my work desktops are configured as well.)

Now...

...I just checked again after a reboot. Oddly enough I can do whatever I want - add files/folders/delete in the C:\users directory. I can do the same in c:\users\lilly directory. I just cannot in c:\users\lilly\Documents.

Go figure.
[/FONT][/FONT]

---

### Post by dmizer on 2009-06-03
First of all, see my above edit.

Additionally, this makes a lot of sense to me. Unless you specifically include guest access to personal directories in Vista, Vista will deny access. Even if you log in as Lilly from Ubuntu, you will still be unable to get access to those directories because Ubuntu doesn't have the same permissions levels and settings as Vista does.

Instead, you should keep all the files you wish to share in a publically accessable folder, and make sure it has guest access. I don't have Vista, so the specifics of doing that are beyond me, but I suspect it should be fairly simple.

---

### Post by NTolerance on 2009-08-24
Wait a minute.  Something is up with how Nautilus handles Vista/Win7 shares mounted by GVFS.  See this thread I created a long time ago:

[http://ubuntuforums.org/showthread.php?t=940817](http://ubuntuforums.org/showthread.php?t=940817)

Never did get an answer on that, and I believe that it's still unresolved in Jaunty.  

I've revisited this issue because I've recently moved from Vista to Windows 7.  I have created a file share for the "C:\Users\username" directory on Windows 7.  I am using the "advanced" sharing method which allows you to specify permissions for the share.  In my case I want full read/write access to authenticated users and no access to anyone else.  I find this to be the best file sharing method.  Only I can access my files, and when I do, I have full access.  I'm not a fan of "public" or "guest" methods. 

At any rate, here's where it gets funny.  Once the share is mounted in Nautilus, all "shell" folders have a lock icon above them and you cannot write to them.  All other folders in your Win7 "home" directory are writeable.  

Here are two observations which point to a problem with Nautilus itself:

1.  An authenticated Windows XP system can write to the special Win7 user folders.
2.  GVFS can authenticate and write to the special folders via the command line using this path:  ~/.gvfs

So the shares are writeable and agreeable to even a non-MS platform such as Ubuntu Jaunty.  GVFS is quite happy to write to the folders, but Nautilus gets all uncooperative about it.

#-o

Edit:  Another point of interest:  Nautilus and GVFS only display the default Vista/Win7 shell folders, not any ones that have been renamed by the user.  In my case I have renamed the "Downloads" folder to "Temp".  This is not a true rename; what actually happens is that Vista/Win7 creates a symbolic link from the new name given to the old folder, if that makes sense.

---

### Post by NTolerance on 2009-08-27
So I've done some more testing and now believe this problem to do with GVFS and the way it provides information to a GUI file manager.  Shares mounted via GVFS cannot be fully accessed with Nautilus, Thunar, or PCManFM.  

I say this because I installed Kubuntu in a virtual machine and Dolphin has no trouble writing all the special Vista/Win7 folders.

---

### Post by NTolerance on 2009-10-12
I've done some more testing on this issue and submitted a [bug report](https://bugzilla.gnome.org/show_bug.cgi?id=598206) to GNOME.  

If anyone's morbidly curious, read about my findings and post your thoughts and/or testing results.

---

### Post by dmizer on 2009-10-14
> **NTolerance said:**
> I've done some more testing on this issue and submitted a [bug report](https://bugzilla.gnome.org/show_bug.cgi?id=598206) to GNOME.  

If anyone's morbidly curious, read about my findings and post your thoughts and/or testing results.

This post: [http://ubuntuforums.org/showpost.php?p=8053685&postcount=1083](http://ubuntuforums.org/showpost.php?p=8053685&postcount=1083) may be of interest to you.

---

### Post by NTolerance on 2009-10-14
> **dmizer said:**
> This post: [http://ubuntuforums.org/showpost.php?p=8053685&postcount=1083](http://ubuntuforums.org/showpost.php?p=8053685&postcount=1083) may be of interest to you.

That's great information.  It's definitely the read-only flag that's causing the problem.  attrib -r will fix it on the Ubuntu side, but this nixes the folder view and icon customizations on the Windows side.  :(

I guess my next concern is this:  do I need to revise my bug report?  Does this now indicate a problem with the samba backend or kernel?

---

### Post by dmizer on 2009-10-14
> **NTolerance said:**
> That's great information.  It's definitely the read-only flag that's causing the problem.  attrib -r will fix it on the Ubuntu side, but this nixes the folder view and icon customizations on the Windows side.  :(

I guess my next concern is this:  do I need to revise my bug report?  Does this now indicate a problem with the samba backend or kernel?

If the linked post fixed the problem, then this is not a bug in Samba or in Linux. This is a Windows side issue.

---

### Post by NTolerance on 2009-10-14
> **dmizer said:**
> If the linked post fixed the problem, then this is not a bug in Samba or in Linux. This is a Windows side issue.

Well, I guess I don't consider it a fix if all the default Windows shell folders have the read-only flag set.  Every new user account on every Vista/Win7 PC has about 10 of these folders, all of them inaccessible from Ubuntu.  These folders account for just about any and all types of user data - pictures, music, documents, contacts, etc...  Looking at that fact, Ubuntu cannot write to nearly all Vista/Win7 user data folders.  I might also add that these folders are the default save location for Windows apps.  Changing them involves a headache each time you go to save or open a file in Windows.

If you run the attrib -r command on these folders, you might as well just delete them because you'll lose their intended purpose, which is to show a special icon and display the data with context-specific folder views. 

For example, now your music folder in Vista/Win7 won't show the ID3 tag data.  Instead, it'll just show default file list data.  

Let's look at the text straight from the Microsoft documentation:

> Unlike the Read-only attribute for a file, the Read-only attribute for a folder is typically ignored by Windows, Windows components and accessories, and other programs. For example, you can delete, rename, and change a folder with the Read-only attribute by using Windows Explorer. The Read-only and System attributes is only used by Windows Explorer to determine whether the folder is a special folder, such as a system folder that has its view customized by Windows (for example, My Documents, Favorites, Fonts, Downloaded Program Files), or a folder that you customized by using the Customize tab of the folder's Properties dialog box. As a result, Windows Explorer does not allow you to view or change the Read-only or System attributes of folders.

If Windows apps typically ignore the read-only flag on folders, then Samba should as well, right?

Does this make any sense or should I just withdraw my bug report because this is a "Windows" bug?  I really don't want to fight an uphill battle if this is likely the prevailing opinion.

---

### Post by dmizer on 2009-10-14
> **NTolerance said:**
> Does this make any sense or should I just withdraw my bug report because this is a "Windows" bug?  I really don't want to fight an uphill battle if this is likely the prevailing opinion.

Well, if you're wanting to pursue it, I think you should consider closing your current report and opening a new one. Given this new information, you should be able to make a more specific bug report. I suggest you make a similar argument in your new bug report. Also, this should probably be filed against CIFS rather than Nautilus.

I would hardly suggest calling my opinion on this matter "prevailing" as I'm not even a part of the Ubuntu Samba team, but I suspect that (if it's considered a bug) this will be an upstream bug.

---

### Post by NTolerance on 2009-10-14
> **dmizer said:**
> Well, if you're wanting to pursue it, I think you should consider closing your current report and opening a new one. Given this new information, you should be able to make a more specific bug report. I suggest you make a similar argument in your new bug report. Also, this should probably be filed against CIFS rather than Nautilus.

I would hardly suggest calling my opinion on this matter "prevailing" as I'm not even a part of the Ubuntu Samba team, but I suspect that this will be an upstream bug.

Cool, thanks for the advice.  But I'm still confounded by the fact that the folders are writable via the ~/.gvfs path.  Everything is all well and good right up until Nautilus comes into the picture.  Which is why I filed the bug under Nautilus.  If, in spite of this fact you still think this belongs in the CIFS realm, please let me know and I'll take the bug report there.

---

### Post by dmizer on 2009-10-15
> **NTolerance said:**
> Cool, thanks for the advice.  But I'm still confounded by the fact that the folders are writable via the ~/.gvfs path.  Everything is all well and good right up until Nautilus comes into the picture.  Which is why I filed the bug under Nautilus.  If, in spite of this fact you still think this belongs in the CIFS realm, please let me know and I'll take the bug report there.
No problem at all. I've run into this very issue many times and I'm thrilled that someone's finally found something of a fix for it.

GVFS still depends on CIFS when mounting shares. Also, keep in mind that the link I gave earlier was a fix for a Samba share mounted with CIFS in /etc/fstab where the directory permissions showed dr-xr-xr-x at the CLI level.

---

