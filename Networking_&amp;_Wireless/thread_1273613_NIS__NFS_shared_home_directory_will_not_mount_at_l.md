---
title: "NIS:  NFS shared home directory will not mount at login - can't login through NIS"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by thepossiblehuman on 2009-09-23
I'm trying to get NIS logons working with my Ubuntu workstation box.  I installed, NFS, NIS, and AutoFS.  It is definitely binding with the NIS server, and if I log in with a local account, I can mount the share through the mount command.

However when I try to login with an account in NIS, it tells me:

*Your home directory is listed as: '/users/ops/<username>' but it does not appear to exist.  Do you want to log in with the / (root) directory as your home directory.  It is unlikely anything will work unless you use a failsafe session.*

Now <username> is just whatever username I was trying to use, and that's the correct path.  The account owns its own home directory there too.

My auto.master file is configured the same as other working linux boxes on the network (albiet RedHat boxes), and I even tried hacking it to point to a auto.home file that I created which has the mountpoint location.  

I went through the client config instructions here as well: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Nothing changes.  I always get the same error.  Any help at all is appreciated.  banging my head against my desk with this one.

---

### Post by thepossiblehuman on 2009-09-25
Anyone?  This is a fairly simply thing in other distros and I've even tried to match all the files from other boxes with redhat, cent, and suse to no avail.

---

### Post by thepossiblehuman on 2009-09-30
Anybody know any good debian forums?  Perhaps it's debian specific...

---

### Post by 480silverton on 2009-10-09
If you look in your NIS settings where you set NISSERVER and NISCLIENT

Some instructions tell to set the NISMASTER as master when it should be true instead.

NISSERVER=true
NISCLIENT=false

Not:
NISSERVER=master
NISCLIENT=false

---

