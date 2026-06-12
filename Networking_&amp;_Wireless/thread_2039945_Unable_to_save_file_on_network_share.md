---
title: "Unable to save file on network share"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by megamister on 2012-08-09
Maybe somebody can explain this and offer options.

Setup: Kubuntu 12.10 with Samba shares
Desktop: Kubuntu 11.04

With a file browser I can browse the shares open\access. But when I for example open a Document with LibreOffice on the share it opens with a filename like 1234.0.Actualfilename. Then if I try to save it only saves the file as a temp file with the indicated filename, or sometimes it will just use the numerical portion like 1234.0.doc and saves to /var/tmp/kde-cache-username/krun  If I save as the same filename to the local machine I can then xfer it and overwrite it on the share. 

I can create a new file on the share then name it without any issues.

Doing the same thing from Win7 I have no issues. Open the document, edit it, saves fine in the shared folder.

I have read something about the shares need to be mounted, even though they appear mapped in my Places, they aren't really mounted thus not really accessible? Apparently some have solved it with "gigolo" and automount? But that seems like a lot of extra effort for something so simple, or am I asking for too much convenience?

So what are the options for simple ubuntu to ubuntu shared access from a GUI? Using filezilla and FTP to browse and save, or automount options??? 

Setup: Kubuntu 12.10 with Samba shares
Desktop: Kubuntu 11.04

---

### Post by 2F4U on 2012-08-10
I guess the problem is that not every application can work with shares. For example, I never got Amarok to play music over the KDE Samba sharing, while it plays well when the shares are actually mounted.

---

### Post by megamister on 2012-08-10
I use the same Libreoffice in Win7 with no issues.

---

### Post by bab1 on 2012-08-10
> **megamister said:**
> Maybe somebody can explain this and offer options.

Setup: Kubuntu 12.10 with Samba shares
Desktop: Kubuntu 11.04

With a file browser I can browse the shares open\access. But when I for example open a Document with LibreOffice on the share it opens with a filename like 1234.0.Actualfilename. Then if I try to save it only saves the file as a temp file with the indicated filename, or sometimes it will just use the numerical portion like 1234.0.doc and saves to /var/tmp/kde-cache-username/krun  If I save as the same filename to the local machine I can then xfer it and overwrite it on the share. 

I can create a new file on the share then name it without any issues.

Doing the same thing from Win7 I have no issues. Open the document, edit it, saves fine in the shared folder.

I have read something about the shares need to be mounted, even though they appear mapped in my Places, they aren't really mounted thus not really accessible? Apparently some have solved it with "gigolo" and automount? But that seems like a lot of extra effort for something so simple, or am I asking for too much convenience?

So what are the options for simple ubuntu to ubuntu shared access from a GUI? Using filezilla and FTP to browse and save, or automount options??? 

Setup: Kubuntu 12.10 with Samba shares
Desktop: Kubuntu 11.04

I don't use KDE but I believe the problem is in how the share is mounted.  I believe the KDE file manager uses gvfs to mount the share.  This gvfs mount uses an arbitrary set of options.  The option that is not used is **nbrl**.  The description in the man page (man mount.cifs) is this:```
     nobrl
           Do not send byte range lock requests to the server. This is
           necessary for certain applications that break with cifs style
           mandatory byte range locks (and most cifs servers do not yet
           support requesting advisory byte range locks).

```
If you mount the share either by script or using fstab with this option then you should be able to use  LibreOffice directly on the file.  I have this very set up but with Gnome.  LibreOffice and Samba don't really play well together.

---

### Post by SeijiSensei on 2012-08-10
Dump Samba and use NFS if you're trying to share files from a *nix server to a *nix client.  I have no problems with file on NFS-mounted shares and Open/LibreOffice.

Samba is not a solution; it's a kludge to let *nix machines work with Windows clients.  Unless you need to support Windows clients, there's no reason to run Samba.  If you need to support both Windows and *nix, you can share the same directories with both Samba and NFS.

---

### Post by megamister on 2012-08-11
Yes I need support for Win boxes. 
I think I read that modifying Fstab is no longer an option for automounting in this type of case, can't remember the justification. 
 
But I may look into the NFS as an option. 

What is your opinion of NFS vs an FTP client like filezilla for transferring?

---

### Post by SeijiSensei on 2012-08-11
> **megamister said:**
> Yes I need support for Win boxes. I think I read that modifying Fstab is no longer an option for automounting in this type of case, can't remember the justification.

I don't think that's true.  Follow the steps [here](https://wiki.ubuntu.com/MountWindowsSharesPermanently) to mount the share as type "cifs."  

> What is your opinion of NFS vs an FTP client like filezilla for transferring?

I don't see them as especially comparable.  An NFS mount provides continuous access to the share at a mount point just as if the files were on your local drive.  If you're talking about access to the share from outside your network over the Internet, then you want to use a secure protocol like SFTP or SCP.  Alternatively you can use SSH to mount the share as type [sshfs]("https://help.ubuntu.com/community/SSHFS").

---

