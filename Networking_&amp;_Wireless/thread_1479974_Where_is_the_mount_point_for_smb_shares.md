---
title: "Where is the mount point for smb shares?"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by HamburgerTS on 2010-05-11
Hello,

sorry if this question has already been answered but i was not able to find it neither in ubuntuforums.org nor via google:

Where are the mount points for smb shares connected via 

"Places -> Connect to Server"?

I assumed them in one of the usual places like

/mnt
or
/media

but these folders are both empty. 

There are a couple of applications which are not capable of accessing my shares because i can't navigate to the right location...

Many thanks for your time!
Martin

---

### Post by Olav on 2010-05-11
> Where are the mount points for smb shares connected via

"Places -> Connect to Server"?
Those locations aren't "mounted" as you would expect. They are accessed as virtual file systems in Nautilus. If you want them mounted you must install the package smbfs and mount them manually, or edit your /etc/fstab.

---

### Post by Morbius1 on 2010-05-11
**/home/your_user_name/.gvfs**

As you can see, it's in a hidden directory so you need to enable Nautilus to see the hidden folder. Why is it in a hidden directory? I personally think it was a practical joke by the developers.

[COLOR=Blue]EDIT:[/COLOR] If your applications can't get to the hidden directory you'll need to create a symbolic link to a "real" directory.

---

### Post by Olav on 2010-05-11
> **Morbius1 said:**
> **/home/your_user_name/.gvfs**

As you can see, it's in a hidden directory so you need to enable Nautilus to see the hidden folder. Why is it in a hidden directory? I personally think it was a practical joke by the developers.
That's why I like to do this manually, keeping control over where things are mounted.

---

### Post by Morbius1 on 2010-05-11
> **Olav said:**
> That's why I like to do this manually, keeping control over where things are mounted.

I personally don't have a religious affiliation with either method. gvfs-mount ( mounting through Nautilus ) is sorta - kinda the client side equivalent of nautilus-share. You can create a share by defining it in smb.conf ( Classic-share ) or you can right click a folder and say "share this thing" ( Nautilus-share ). Each method has it's place.

---

### Post by HamburgerTS on 2010-05-11
> **Morbius1 said:**
> **/home/your_user_name/.gvfs**

Thank you very much! This was exactly the information i needed...

> **Morbius1 said:**
> Why is it in a hidden directory? I personally think it was a practical joke by the developers.

In my opinion its a serious usability bug (in the application i use). Shares mounted by "Connect to server" should be accessible the same way "normal" folders are. OpenOffice for example has no problems to show these folders...

I have the (by far not professional) impression that the application ("unison" in this case but the "MySQL Query Browser" has the same issue) uses a outdated (at least older version) of the "File select" dialog...

> 
[COLOR=Blue]EDIT:[/COLOR] If your applications can't get to the hidden directory you'll need to create a symbolic link to a "real" directory.
Good idea. Works perfect. 

Thank you all for your response. 

Have a nice day
Martin

---

### Post by larsonj on 2010-07-30
> Quote:
 	 	 		 			 				[COLOR=Blue]EDIT:[/COLOR] If your applications can't get to the hidden directory you'll need to create a symbolic link to a "real" directory. 			 		 	 	 
Good idea. Works perfect. 

How does one go about making the symbolic link?  When I choose "make link" from right clicking on my shared folder, I get "Target does not support symbolic links".  

By the way, mounting shared folders to a hidden location is a major usability bug as many programs can't locate the shared folder.

---

### Post by bab1 on 2010-07-30
> **larsonj said:**
> How does one go about making the symbolic link?  When I choose "make link" from right clicking on my shared folder, I get "Target does not support symbolic links".  

You can create the symlink link from the terminal```
ln -s 
``` 

See [**_here_**]("http://unixhelp.ed.ac.uk/CGI/man-cgi?ln").

Symlinks are no longer allowed by default with Samba shares.  You would have to edit the /etc/samba/smb.conf file.  See [**_here _**]("http://ubuntuforums.org/showthread.php?t=1439092").

> 

By the way, mounting shared folders to a hidden location is a major usability bug as many programs can't locate the shared folder.

There are valid reasons for using a hidden mount point (location) for GUI created shares.  I think you will find many apps don't work with SMB shares even if you do know where the shares are.  Not all developers follow the same methods.

---

### Post by Morbius1 on 2010-07-30
To create a symbolic link I use the Terminal:

Let's say I want to create a link from the gvfs mountpoint of a share named "music" on a server named "bob" to say /home/morbius/Music:

```
ln -s /home/morbius/.gvfs/"music on bob" /home/morbius/Music
```> **bab1 said:**
> Symlinks are no longer allowed by default with Samba  shares.  You would have to edit the /etc/samba/smb.conf file. That's only true if the share you're trying to access has a symbolic link embedded in it's directory on the [COLOR=Blue]server[/COLOR]. It is not applicable in this case as this user is trying to create a symbolic link from the mounted share to another location on the same [COLOR=Blue]client[/COLOR] machine.

---

### Post by larsonj on 2010-07-30
Thanks.  Creating a symbolic link from the terminal works fine, and as mentioned by Morbius1, editing the config file was unnecessary.

> **bab1 said:**
> 

There are valid reasons for using a hidden mount point (location) for GUI created shares.  I think you will find many apps don't work with SMB shares even if you do know where the shares are.  Not all developers follow the same methods.

Even if using the hidden mount point is for a valid reason, GUI created shares do not show up in any program that I can find except open office.  Even programs that are loaded with Ubuntu by default such as FSpot photo manager, Mozilla, etc, do not work.   Since creating a link via the GUI also disabled forcing the user to go to the terminal, I consider the GUI broken.

Addtion:
Apparently, this was noted as an issue in 2005 [http://ubuntuforums.org/showthread.php?t=289918](http://ubuntuforums.org/showthread.php?t=289918)

---

### Post by Morbius1 on 2010-07-30
> Even programs that are loaded with Ubuntu by default such as FSpot photo  manager, Mozilla, etc, do not work.   Since creating a link via the GUI  also disabled forcing the user to go to the terminal, I consider the  GUI broken.I'm really not trying to aggravate everyone in this forum but I don't think that's quite right either. Take Mozilla for example. Let's say you want to save this web page to a hidden directory. You'll get a "Save As" dialog box and no hidden directories will be visible. . You need to right click an open spot on the directory listing and select "Show Hidden Files". It really depends on the application.

But overall, I think we as users would have been better served if the gvfs-mount process created a "non hiden" mount point. smb4k did that the last time I used it. It created a mount point at /home/morbius/smb4k.

---

