---
title: "mounting NFS/CIFS shares from a Netapp."
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by silverbullet007 on 2013-06-19
Ubuntu 12.04, trying to mount NFS exports from our netapp.  I successfully got the shares to mount via CIFS but ran into a permission issue.  Basically the drive is mapped and I can access with Full Control permissions in a Windows7 P2V VM I created.  But inside Ubuntu using:

//10.1.1.1/MIS /media/MIS cifs username=user,password=pass,iocharset=utf8,sec=ntlm   0    0
or
10.1.1.1:/vol/vol3/MIS /media/MIS NFS auto   0   0

The shares mount, but I either get access denied (via the NFS mount) or I can access but cannot modify data (via CIFS mount).

The account used is the same I successfully use in Windows.. so as far as permissions and rights go I have them.  Can anyone help me get these shares mounted correctly?  I don't have a preference between CIFS or NFS.  I initially went with CIFS after following a guide on integrating Ubuntu with Active Directory, which in my mind should have meant that I would not need to supply a username and password to mount a CIFS share, but I digress.

With regards to NFS, I have created, deleted and re-created multiple times the export for this particular share.  All to no avail.

---

### Post by silverbullet007 on 2013-06-20
No one?

---

### Post by capscrew on 2013-06-20
> **silverbullet007 said:**
> Ubuntu 12.04, trying to mount NFS exports from our netapp.  I successfully got the shares to mount via CIFS but ran into a permission issue.  Basically the drive is mapped and I can access with Full Control permissions in a Windows7 P2V VM I created.  But inside Ubuntu using:

//10.1.1.1/MIS /media/MIS cifs username=user,password=pass,iocharset=utf8,sec=ntlm   0    0

or
10.1.1.1:/vol/vol3/MIS /media/MIS NFS auto   0   0

The shares mount, but I either get access denied (via the NFS mount) or I can access but cannot modify data (via CIFS mount).

The account used is the same I successfully use in Windows.. so as far as permissions and rights go I have them.  Can anyone help me get these shares mounted correctly?  I don't have a preference between CIFS or NFS.  I initially went with CIFS after following a guide on integrating Ubuntu with Active Directory, which in my mind should have meant that I would not need to supply a username and password to mount a CIFS share, but I digress.

With regards to NFS, I have created, deleted and re-created multiple times the export for this particular share.  All to no avail.

What does "NFS exports from our netapp" mean.  If these are mounted using SMB/CIFS then they are not NFS.  They are CIFS.  Windows supports CIFS by default.  Windows does not support NFS without additional software.

What is this "netapp"?

When mounting CIFS you need to set the file and directory ownership as well as the login user.  The login user (username) is for Samba access and the ownership (uid=1000 and gid=<some group ID>) is for Linux permissions.  I put all my Samba users in the group *sambashare*.  

Samba (SMB/CIFS) shares (the CIFS resource) is defined as ```
//COMPUTER_NAME/Share_Name
``` Although your mount seems to work, the correct way to declare the resource is not by //COMPUTER/path/to/directory

---

### Post by silverbullet007 on 2013-06-21
Thanks for replying capscrew.

First things first, a Netapp (should have been capitalized) is a SAN product from a company called Netapp.  I'm sure you've heard of them before ;)

Netapps supports both NFS and CIFS so while I am able to successfully mount the shares using CIFS, I am unable to mount using NFS at all.  NFS is setup correctly on the Netapp as there are 12 other exports that are being used by servers and workstations for the past couple years.  I created this export to be identical to those except for the path to the folders obviously.
I figured I had explained what's going on well enough initially, but let me do it again for you.

I am running Ubuntu 12.04LTS, I also have a Windows 7 virtual machine in VirtualBox.  The VM accesses the same shares I have mounted in Ubuntu using CIFS, so I mention that to relate that the credentials I am using in Ubuntu to mount these shares using CIFS is teh same credentials I'm using in the Windows VM successfully.

My original problem was that while I can mount them using CIFS, I cannot modify..meaning I have Read-Only permissions and not Read/Write like I should.  So after battling that for a couple days I figured since I'm using linux I might as well mount them using NFS.  Which isn't working either, which is why I posted here.

---

### Post by silverbullet007 on 2013-06-21
Oh and I was not using 
//Computer_Name/Path/To/Directory for CIFS.. you might want to re-read it.  I used that for NFS however because I had seen websites showing both.. path/to/dir and //computer/share for NFS mounts.

---

### Post by silverbullet007 on 2013-06-24
I'd really appreciate some help with this.  It's forcing me to use my Windows vm more and more and me not being a very experienced Linux user I cannot figure this out on my own.

---

### Post by SeijiSensei on 2013-06-24
I think one problem is that few of us have experience with a NetApp appliance, so it's hard to know how to troubleshoot your problem.  I could help if you were running NFS or CIFS on another Linux box.

Have you asked around on support forums for NetApp users?  If this device is in a company, perhaps you have some type of support contract?

---

