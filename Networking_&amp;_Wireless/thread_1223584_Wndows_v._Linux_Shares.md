---
title: "Wndows v. Linux Shares"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by HDTimeshifter on 2009-07-26
I had an old Windows XP machine with 3 drives which I shared and was basically using as a basement file server to backup my files from my main Ubuntu desktop machine.  I had set it up on my Windows Network and was able to read and write to the shared drives/folders.

Yesterday, I installed Ubuntu 9.04 desktop on this PC, wiping out the Windows OS partition.  Now the 3 drives are Filesystem, Data, and Linux Data.  I'm not sure if the Data and Linux Data drives were converted to Linux filesystems since when I try to share the Data drive or a folder in the Data drive through Nautilus, it told me to install some Windows networking stuff.  So I did that, however, when I try to share it, it gives me an error saying I'm not the owner:
[I]  'net usershare' returned error 255: net usershare add: cannot share path /media/Data/Documents and Settings as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.[/I]

I opened up a terminal and chown to myself (the admininstrator), however still get the same error.  Where is the smb.conf file?  (More than two decades after first learning UNIX and I still haven't figured out the find command - damn complicated syntax and man page!)  I don't really want to allow other users to set up shares - after all I am the owner and administrator.  Now when I try to view this share from my main Ubuntu desktop, first I open Places / Network and see a new Windows Network group in my file browser (WORKGROUP - it used to be part of my MSHOME group - so I assume when I installed the Windows networking stuff for Ubuntu on this PC, it defaulted to the old XP convention, while I had been using the Vista convention).  Then when I click on WORKGROUP, I see this PC (Athlon), but the only share is print$.

If this PC's other 2 drives were not converted to Linux file systems, how do I do that?  How do I share the drives (or at least folders in those drives).  If I convert them to Linux filesystems, will I still be able to share folders in the drives with my Vista laptop (to backup my Vista folder/files) through Samba?

---

### Post by Iowan on 2009-07-26
> **HDTimeshifter said:**
> 
If this PC's other 2 drives were not converted to Linux file systems, how do I do that?  You *might* be able to mount them as NTFS. [Here]("http://ubuntuforums.org/showthread.php?&t=283131") is a How-To that may be helpful.

---

### Post by HDTimeshifter on 2009-07-26
Ok, so the Sharing folders via Nautilus help didn't work.  I was able to get sharing working through the Sharing folders via the Shared Folders application help.

However, in Properties, I changed the network name from WORKGROUP back to MSHOME, but this machine still shows up in WORKGROUP and not MSHOME network?  What the hell???

And I'm still confused why Windows networks (SMB) is the only sharing option.  Is Linux an NFS (UNIX) or SMB (Windows) filesystem?
Edit:  Ok, I guess the drives were converted or linked as ext2 or ext3 filesystem, as one of those was the default installation option, however since we use Samba to for networking in Ubuntu, we have to mount through SMB.

---

### Post by Iowan on 2009-07-26
[Another]("http://ubuntuforums.org/showthread.php?t=1169149") How-To that might be helpful. Files can be shared various ways. NFS and SSH are a couple of other options. [Here]("http://ubuntuforums.org/showthread.php?t=249889") is a basic NFS How-To. 
There is a more involved version [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").
 [SSHFS]("https://help.ubuntu.com/community/SSHFS") is another option.

---

### Post by martinbaselier on 2009-07-26
How to find stuff in the terminal:

method 1:
sudo updatedb
locate smb.conf

method 2:
cd /
find * | grep smb.conf

method 1 is a lot faster though.

---

### Post by HDTimeshifter on 2009-07-26
Got the PC back to the original domain.  I guess the domain settings didn't take effect until I rebooted.

---

