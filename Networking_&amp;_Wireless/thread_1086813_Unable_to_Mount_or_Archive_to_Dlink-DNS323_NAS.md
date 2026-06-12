---
title: "Unable to Mount or Archive to Dlink-DNS323 NAS"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by california-ken on 2009-03-04
I am an experienced Windows user with modest Linux (Ubuntu) skills.  After 10's of hours of effort, I continue to be unable to archive to a Dlink-DNS323 network storage device.  I have searched numerous web articles and tried a great number of command-line mount commands, fstab entries and archiving via the Nautilus file manager.

**Gnome Tools:**
Using gnome tools, I can mount the Dlink-DNS without any problems.  Clicking on: 
	Places/Computer/Network/Windows Network/House/DLINK-DNS/Volume_2
mounts Volume_2 without errors.  However, when using the Nautilus file manager to archive a file or folder using “Create an Archive” and selecting “volume_2 on dlink-dns” in the dialog box, I get the following error message:  “You don't have the right permissions to create an archive in the destination folder.” In my dlink-DNS323, I have read/write permissions assigned to all users and the Dlink password set equal to my Ubuntu user password.  I don't understand the error message since after “mounting” the Dlink-DNS using Nautilus, I have full read/write access using Nautilus.  It is only the “Create Archive” function that produces the error message.

Is there a way to resolve the permissions issue so that I can archive to the Dlink using Nautilus?

[B]Mount via Command Line or FSTAB:
[/B]
I have tried numerous command-line and fstab entries derived from web searches without success.  A summary of my Ubuntu/network setup is:
	Dlink-DNS IP:  192.168.1.19
	Dlink Drives:  2 sata drives labeled Volume_1 and Volume_2
	Windows Name for the Dlink:  Dlink-DNS
	Ubuntu add-ons:  Samba, smbfs and cifs
	/etc password file:  Yes, /etc/nas.passwd
	Mount Point Defined:  Yes, /mnt/dns-volume_2
	wins” added to /etc/nsswitch,conf:  Yes
	fstab entres:  Several tried;  the last three tried are -
# //192.168.1.19/Volume_2 /mnt/dns-volume_2/ cifs nounix,uid=lovebirds,gid=lovebirds,file_mode=0777,dir_mode=0777 0 0 
# Another try: 
# //192.168.1.19/volume_2    /mnt/dns-volume_2        cifs    credentials=/etc/nas.passwd,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
# Yet another: 
//DLink-DNS/Volume_2    /mnt/dns-volume_2        cifs    credentials=/etc/nas.passwd,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 

When I enter a “sudo mount -a” command, I get no error message or password prompts other than the normal sudo password prompt.  However, when I run a “sudo fdisk -l” the Dlink mount is never is listed.

A side question which may be involved with the mount problem relates to case sensitivity in fstab entries.  I assume that all the key entries are case sensitive.  When using Nautilus, I see various case uses in references to the Dlink DNS.  Examples are volume_2 on dlink-dns, Volume_2 on Dlink-DNS,
DLINK-DNS, etc.  How do I determine the correct spelling for the hostname entry in fstab entry?

I would greatly appreciate help with solving the “archiving to a NAS” problem.

By comparison, connecting to the Dlink in Windows took less than 5 minutes.

Thanks.

Ken

---

### Post by runes on 2009-03-24
Hi Kent, I have the Dlink DNS-323 and here's a how-to manual I created after fighting with it for a week.

I attached a document I created in Openoffice (saved in msword format for the rest of the windows community who want to migrate) for you with an example of how to set it up from start to finish tell me what you think and add comments if you wish.  Please feel free to email me back with your modifications

---

### Post by nestorpistor on 2009-04-18
> **runes said:**
> Hi Kent, I have the Dlink DNS-323 and here's a how-to manual I created after fighting with it for a week.

I attached a document I created in Openoffice (saved in msword format for the rest of the windows community who want to migrate) for you with an example of how to set it up from start to finish tell me what you think and add comments if you wish.  Please feel free to email me back with your modifications

Hi 

Thanks for the instructions.  I follows them to the letter except where changes were necessary.

at the end when I run the mount -a command with sudo i get this...

[FONT="Courier New"]nick@maple:~$ sudo mount -a
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
[/FONT]

any ideas what may be causing this?

Thanks
Nestor.

---

### Post by geoff511 on 2009-05-22
Hi,

Check post [http://ubuntuforums.org/showthread.php?t=1166719](http://ubuntuforums.org/showthread.php?t=1166719)

Will show how to mount DNS-323 folder into Ubuntu.

---

### Post by gammb on 2009-05-24
I've FunPlugged my DLink DNS321 for SSH & NFS.  The SSH let me setup a different user account 1000:1000 and set all exported dirs/files to that (instead of the default 502:702).  This obviated the whole problem of permissions-management on Ubuntu.

---

### Post by wa1d0rf on 2012-05-11
> **runes said:**
> Hi Kent, I have the Dlink DNS-323 and here's a how-to manual I created after fighting with it for a week.

I attached a document I created in Openoffice (saved in msword format for the rest of the windows community who want to migrate) for you with an example of how to set it up from start to finish tell me what you think and add comments if you wish.  Please feel free to email me back with your modifications

I know this post was from years ago, but maybe you or someone else can answer my question.  In the attached documents, there is a reference in a few places to "/root/".  I know that the real "root" folder is simply referenced by "/".  What does this "/root/" reference mean?  Does it mean the users root folder?  Mine is "/home/john" so would I replace "/root/" with "/home/john/"?

---

### Post by bab1 on 2012-05-11
> **wa1d0rf said:**
> I know this post was from years ago, but maybe you or someone else can answer my question.  In the attached documents, there is a reference in a few places to "/root/".  I know that the real "root" folder is simply referenced by "/".  What does this "/root/" reference mean?  Does it mean the users root folder?  Mine is "/home/john" so would I replace "/root/" with "/home/john/"?

First a word of advice.  Don't use out of date information or cures.  The methods and tools change and you can go around in circles with incorrect resources.  This thread is 3 years old and has at least 1 error that I can see.

To answer you question directly: there is root the user and the root of the file system.  The user root has a home directory apart from the other (mortal) users.  This is at /root/.  The root of the entire file Linux system is /.

The instructions specifically state place a .credentials file (or some such)  in the root directory (e.g /root/.smbcredentials).

I advise you start your own thread and post your specific problem so we may best help *you* with *your* problem.

---

### Post by ubudog on 2012-05-11
> **wa1d0rf said:**
> I know this post was from years ago, but maybe you or someone else can answer my question.  In the attached documents, there is a reference in a few places to "/root/".  I know that the real "root" folder is simply referenced by "/".  What does this "/root/" reference mean?  Does it mean the users root folder?  Mine is "/home/john" so would I replace "/root/" with "/home/john/"?

It'd be best to start a new thread, this one is old.

*Thread closed.*

---

