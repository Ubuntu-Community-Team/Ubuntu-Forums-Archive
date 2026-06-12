---
title: "fstab/cifs one problem I can't solve without help:"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by Atokad on 2009-05-22
[SIZE=3]Hey, folks!  
I got through 99% of my "mission" by searching, reading some great tutorials, and lots of trial and error...
but I have one drive still giving me fits, and am ready to ask for some help.
[SIZE=2]
The relevant hardware is:

_**Server**_
Windows Server 2008 (no Active Directory, just using "Workgroup" Mode
[COLOR=Green]Drives are all "working, mounting, reading, & writing fine", so I don't think we need more details.[/COLOR]

_**Studio**_
Windows XP Pro (SP3)
[COLOR=DarkRed]The problem is with getting L: drive to mount/share on the Dell Laptop in Ubuntu[/COLOR]
_The drive is shared, and XP permissions set to:_
Everyone                = Full Control
Studio\My Name = Full Control
Studio\Users       = Full Control
*(Those permissions are probably "overkill", but I'm frustrated.)*

_**Dell Laptop**_
Dual-Booting WinXP-Pro and Ubuntu 9.04 "Jaunty"

_**I'll start off with the (relevant) lines from my fstab:**_

[COLOR=Blue]/dev/sda1            /media/BlyMain    ntfs   defaults 0 0
/dev/sda2            /media/BlyData    ntfs   defaults 0 0[/COLOR]
[COLOR=Green]#     These lines "auto-mount" my Laptop C: & D: drives(NTFS), and work just fine.[/COLOR]
[COLOR=Blue]
//server/e-david        /media/E-David    cifs   credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//server/F-Susan        /media/F-Susan    cifs   credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//server/G-Studio       /media/G-Studio   cifs   credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//server/H-Software     /media/H-Software cifs   credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//server/I-Music        /media/I-Music    cifs   credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//server/J-Video        /media/J-Video    cifs   credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//server/K-Adult        /media/K-Adult    cifs   credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0[/COLOR]
[COLOR=Green]#    These lines "auto-mount" the E: through K: drives (NTFS) on "Server", and work fine as well.[/COLOR]
[COLOR=Blue]
//studio/L-Stuff       /media/L-Stuff         cifs    credentials=/root/.smbcredentials2,iocharset=utf8,gid=1000,uid=1000,n$[/COLOR]
[COLOR=DarkRed]This line is meant to "auto-mount" the L: drive (NTFS) on "Studio"..... It does, in fact, automount.       
[COLOR=Red]The trouble is, I can only see "folders" on the mounted drive, no "files"! [/COLOR][/COLOR]
[U]
/root/.smbcredentials[/U]
username=Administrator
password=MyServerPassword
(yep, there's a "blank line" here, just in case)
*[COLOR=Green]Those are the inputs needed to access shared drives on "Server" [/COLOR]*

_/root/.smbcredentials2_
username=MyWindowsUserName
password=MyWindowsUserPassword
(yep, there's a "blank line" here, just in case)
[I][COLOR=DarkRed]Those are the inputs I THOUGHT were needed to access shared drives on "Studio"

[/COLOR][/I] (I felt I needed this second credentials file for the "separate"login information)

---------------------------

[/SIZE]So, I thought I had everything set up, and I do, with the exception of the Studio L: Drive.
It mounts, I can see all the directory structure... just no files whatsoever!

Everything else works flawlessly (yeah, okay, it took 6 hours of fiddling, lol)... just this one problem is haunting me.
I was thinking it was because of "permissions", either on the "Studio" end, or here in Linux.

The "mount" folder //media/L-Stuff should be fine, and the permissions on the "Windows" end should be right.

So... what did I either overlook, or grossly misconceptualize?

**[COLOR=Green]Thanks in advance for the help, and for all the tutorials and posts I read to get me this far![/COLOR]**[/SIZE]

---

### Post by callan79 on 2009-05-22
> **Atokad said:**
> //studio/L-Stuff       /media/L-Stuff         cifs    credentials=/root/.smbcredentials2,iocharset=utf8,gid=1000,uid=1000,n$



Hello,

I'd suggest, if you haven't done so already, put file_mode=0777 and dir_mode=0777 in the fstab line. Also, just for a trial, try 'nounix' in the fstab line too!

Could you re-post with the full fstab line (you pasted a truncated line)

And, you have a blank line at the end of /etc/fstab, right?

Cheers
Callan

---

### Post by Atokad on 2009-05-23
**Thanks, Callan, for jumping in so soon... I appreciate the help!**

Sorry about the truncation, I didn't realize nano had truncated that "copy".
Unfortunately, the three suggestions you had were already in there (just hiding:D).
[U]
Here's the whole line:[/U]

[COLOR=Blue]//studio/L-Stuff    /media/L-Stuff    cifs    credentials=/root/.smbcredentials2,iocharset=utf8,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0[/COLOR]

So, at least you can now see what we're fussing with!

I inserted the "gid=1000,uid=1000" in there as a long shot (I'm VERY inexperienced with permissions, etc.)... but I've tested it both with and without those lines (the "change ONE thing" philosophy), in no-no, no-yes, yes-no, yes-yes combinations... although I suppose the order of those two commands could be an issue?  Anyway, other than swapping the order I don't think it's those two parameters that's the issue.  So far still the same... I get it mounted, and can see folders, but no files.

I also noticed in testing that I can't see "all the way" into the directory structure.  What I mean is, I know there are files three "levels" of path deep in the directory structure of that drive... but I can only see the folders of the "root" directories, with no "levels" of folders within them.

Sounds silly, I know, but I thought it might give us (you) a hint?

I'm going off to get some shuteye.  Thanks again, and I'll peek tomorrow.

Dave

---

### Post by callan79 on 2009-05-24
> **Atokad said:**
> I also noticed in testing that I can't see "all the way" into the directory structure.  What I mean is, I know there are files three "levels" of path deep in the directory structure of that drive... but I can only see the folders of the "root" directories, with no "levels" of folders within them.

Sounds silly, I know, but I thought it might give us (you) a hint?



Hi Dave,

About all I can think of is that the permissions on the 'server' drive aren't correct.

Perhaps the windows 'drive' has permissions to read/write by everyone, but what about the folders? And what about folders within folders?

I guess what I'm asking is, when you applied the 'everyone' permissions to the drive, did windows also apply those permissions to every file and folder on the disk, including subfolders?

Something else to try - once you've mounted the share, can you CREATE files and folders?

Re the permissions thing, you'll have to ask a windows person about that - for the life of me I can't remember how to do it!

Let us know how you go!

Cheers
Callan

---

