---
title: "Mount Different NAS Shares For Different Users"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by varanasi on 2009-11-09
How can I mount different server shares for each individual user?

There is a new server on our network that has individual home directories for each user.  For example, bob's credentials mount /home/bob, mary's credentials mount /home/mary.  I cannot figure out the best way to automatically mount the correct home directory.  

I don't think I can use fstab.  Since fstab is read before the user logs in, I can't use fstab to pass just the right user's credentials the way I can to the common, shared directories.

I thought about 1) [individual shell scripts]("http://ubuntuforums.org/showthread.php?t=1186877") executed when each user logs in, but I suspect there must be a better way; 2) bookmarking each user's share and entering their credentials.  But the bookmarked shares don't show up in file browser dialogs.

---

### Post by fargle on 2009-11-10
Try the PAM_Mount module:

[http://pam-mount.sourceforge.net/](http://pam-mount.sourceforge.net/)

You can install it in Ubuntu with the libpam-mount package.  I use it to mount my encrypted home directory, but you can use it for network shares as well.  It uses a configuration file in /etc/security called pam_mount.conf.xml, which has examples.

You used to have to muck about in /etc/pam.d to get it working, but I don't believe I had to do that on Karmic, so win there!

---

### Post by varanasi on 2009-11-12
Thanks!  Looks like just the thing.  I'll give it a try.

---

### Post by varanasi on 2009-11-23
I cannot seem to get pam-mount working in Karmic (not that I tried with earlier versions!)

Would you mind posting the relevant parts of your pam_mount.conf.xml?  

I can't seem to find a tutorial that works for me.  I've tried the info from the project page, the man page, [MountWindowsShares]("https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount%20password%20protected%20network%20folders%20without%20credentials%20file%20using%20libpam_mount"), [this one]("http://ubuntuforums.org/showthread.php?t=810247"), and [one from Novell]("http://www.novell.com/coolsolutions/feature/15354.html").  Perhaps configuring pam-mount has changed since these were written.


After a couple hours, all I have accomplished is to temporarily arrange things so gdm wouldn't authenticate my login!

---

### Post by varanasi on 2009-12-15
If some kind soul could explain how to do this, I'd be very grateful.  (And judging from the number of threads and posts asking about how to do this, so would many others.)

I have spent a few more hours "mucking" around with pam with no luck.  The [ubuntu wiki page]("https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount%20password%20protected%20network%20folders%20without%20credentials%20file%20using%20libpam_mount") more or less throws up its hands.  The [ubuntu man page]("http://manpages.ubuntu.com/manpages/karmic/en/man8/pam_mount.8.html") is generic (and slightly outdated.) When I work through the man page, I end up unable to login.

Mainly, the man page says to add  pam_mount.so to the session and auth sections of a pam config file.  Ubuntu's install of libpam-mount appears to take care of this by adding the lines to common-auth and common-session.  

I changed /etc/security/pam_mount.conf.xml to allow user files (I removed the comments (<!-- and -->) from the section called <luserconf name=".pam_mount.conf.xml" />), added a directory to use as a mount point (~/test_mount), and created a local .pam_mount.conf.xml.  I checked to make sure that my login password on the NAS and my desktops were the same.  Here's what's currently in my .pam_mount.conf.xml:

> <?xml version="1.0" encoding="utf-8" ?>

<pam_mount>

    <volume user="varanasi" fstype="cifs" server="nest" path="home" mountpoint="~/test_mount" />

</pam_mount>

I have tried many variations of the substantive line with no luck.

---

### Post by varanasi on 2010-05-06
Please?

---

