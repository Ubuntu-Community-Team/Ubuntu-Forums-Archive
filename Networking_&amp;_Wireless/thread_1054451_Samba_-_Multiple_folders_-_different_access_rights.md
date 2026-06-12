---
title: "Samba - Multiple folders - different access rights"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by Alt69 on 2009-01-29
Setup – Ubuntu 7.10 file server, several WinXp desktop,  several WinXp Laptops connection wirelessly.


Hi, this is what I am trying to accomplish.  (I still consider myself a Linux / Samba newbie).

Would like to have three separate folders where different information is stored in each and the users each have varying degrees of access.

Folders:  
  A: public – shared by everyone on the system. Already existing
  B: finance  - new folder
  C: management  - new folder

Users:    userpub – only has full access to the public folder
	  userfin – has full access to public and finance folders
	  usermgt – has full access to  public, finance, and management folders

Groups: finance
         - Members: userfin, usermgt
        management
         - Members: usermgt 

I have only been working on trying to get the finance directory setup, but not to successful.
Steps taken:

1) I have the public folder already created and everyone has access to it.

2) I created the users and groups and assigned the users to the groups. I used the gui interface to accomplish this.

3) I created the finance and management directories at the command line.

4) I changed the directory ownership:
      > sudo chgrp finance finance

5)  > sudo chmod 775 finance

6)  I then edited smb.conf

...

[public]
    path = /home/public
    available = yes
    browsable = yes
    public = yes
    writable = yes
    read only = no
    guest ok = no
    create mask = 0777
    force create mode = 0606
    directory mask = 0755

[finance]
    path = /home/finance
    valid users = @finance
    force group = finance
    read only = no
    guest ok = no
    create mask = 660
    directory mask = 0755


7) saved smb.conf and exit

8 ) created samba user and passwords
   > sudo smbpasswd –a userfin     
   > sudo smbpasswd –a usermgt

9) restart samba
   > sudo restart /etc/init.d/samba restart

10) On my WinXP laptop, I connected to the server. I am able to see all folders and am able to read/write/deleted most items within the public folder. 
Issue: I can’t use userpub to create files in some of the subdirectories under the shared public folder.


As for the finance folder, when I try to open it, I get a second window asking me to enter my user id and password. So of course I test it out with the userpub, expecting no access. Sure enough it works, can’t get access to the folder.


I then try it with userfin, expecting to get full access to the finance folder as userfin is part of the finance group. 
Issue: I keep getting an error message, that it is "not accessible and to contact the network administrator". Well that would be me. :)


Can anyone suggest what I have done wrong and what I need to fix it. I suspect the fix should be the same for the management folder, which I haven’t attempted yet.

Much appreciated.

---

### Post by capscrew on 2009-01-30
I think you should redo the permissions on the shares.  See post #10 and  11 at:
 [**http://ubuntuforums.org/showthread.php?t=1048325&highlight=capscrew**]("http://ubuntuforums.org/showthread.php?t=1048325&highlight=capscrew")

The reference to the sticky bit is important.  It maintains consistency in subdirectories as well as stopping users from deleting other users work.

---

### Post by Alt69 on 2009-01-30
hi, thanks for the reply. Now ,I am not able to test it till the weekend with everything else going on. 

I do have a few questions. The Finance folder that I want all members who are in the Finance group to have full rights to, includes deleting others files. While I understand the risk of having a file deleted accidentaly, I am relying on my backups to assist with restores, rather than having to clean up files no longer needed in the directory by the users. 

What are values for the mask should I then be using and should I still use the sticky bit?

thanks,

---

### Post by capscrew on 2009-01-30
> **Alt69 said:**
> hi, thanks for the reply. Now ,I am not able to test it till the weekend with everything else going on. 

I do have a few questions. The Finance folder that I want all members who are in the Finance group to have full rights to, includes deleting others files. While I understand the risk of having a file deleted accidentaly, I am relying on my backups to assist with restores, rather than having to clean up files no longer needed in the directory by the users. 

What are values for the mask should I then be using and should I still use the sticky bit?

The term mask is not what you want to use.  You are forcing the mode not a DOS mask.  See the man page for smb.conf.

> 

thanks,

I think it will server you best to think of the file modes (0755,  664, etc) as permissions (authorization) to use the files and directories and not as access controls (do you have the right).  

The ability to access the directory is set by your login (valid user or group) and share security.  This is authentication (who are you?).

That being said you do not have to use the sticky bit for either of the above situations.  It just makes housekeeping easier.  If you are not going to use the sticky bit then you can omit the first digit (this system adds a leading 0 to the chmod).

Without seeing the file and directory structure it's only a guess as to the modes (chmod) you should be setting.  My guess is that you are the owner of the root directory (of course it is /home).    I will assume that you are also the owner of:> A: public – shared by everyone on the system. Already existing
B: finance - new folder
C: management - new folder

My initial thought is 0770 for all directories.  This allows you  and your groups to have full rights to the directories and all others to have no rights.  The key to using this correctly is how and who you authenticate to the use the directories.

If you use force group you will make that group the primary group  ( and able to use there rights) for the directory.

A basic setup for finance could look something like this:
```

valid users = +finance   <-- all users in finance group
force group = finance    <-- make group primary

writable = yes          
force create mode = 0775 <-- perms always be set on a file 
force directory mode = 0774 <-- same as above (but for dir)
        


```

---

### Post by Alt69 on 2009-02-02
Hi, I was able to make the change as you suggest "0770 for all directories". That worked as only those members who are part of the appropriate group has access to the folders.

However I did not make the following change.
___
writable = yes          
force create mode = 0775 <-- perms always be set on a file 
force directory mode = 0774 <-- same as above (but for dir)
___

Are there any implications of not use this?

cheers,

---

### Post by capscrew on 2009-02-02
The only implication is that you are using the default permissions set by Samba.  If these permissions work for you that's fine.  I would make some files and directories with file in them.  Check the  permissions and use the mode directives to control the permissions if needed.

**Edit:** You could do this if you wanted:
```
force create mode = 0770 <-- perms always be set on a file 
force directory mode = 0770 <-- same as above (but for dir)
```

---

### Post by Alt69 on 2009-02-02
Some more things to think about. I will play with it some more and see how it fits.

Thanks for all of you help.

cheers

---

