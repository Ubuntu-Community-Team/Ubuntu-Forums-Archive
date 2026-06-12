---
title: "Samba share loading forever.."
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by dgrzalja on 2010-11-22
Hi. Been using XUbuntu 10.10 on my laptop and everything is great.. In my firm i'm trying to connect to Windows share to run a company program by wine, but the share is loading forever..

I successfully connect and see all shared folders, but this particular share has a lot of files (images) in it and i think it's because of that.. Other shares load normal..

I only need to run some software inside that folder, i don't need to see all the contents, like 10000 of images in it!? How can i do that? 

I use Gigolo to connect to the share.. 

Any help is welcome.. Thanks..

---

### Post by VanillaMozilla on 2010-11-22
I have found large directories to be very slow on a slow machine, irrespective of networking.

---

### Post by dgrzalja on 2010-11-22
Well, i have other pc's that are slower that the one with ubuntu, with win xp and they load the share normally..!?

Any suggestions, anyone?

---

### Post by VanillaMozilla on 2010-11-22
I'm telling you they are slow with Ubuntu.  With Linux I think speed is normal.  Talk to Gnome about it or try a different file manager.

---

### Post by SeijiSensei on 2010-11-23
Try mounting the share directly into the Linux directory structure like this:

```
sudo smbmount //server/share /mnt/point [-o options]
```

Options include things like authentication credentials.  As root, create an empty directory in the file system and replace "/mnt/point" above with the path to the directory.  If everything works you can search online for methods to mount the share at boot from /etc/fstab. 

You'll need to install smbfs (sudo apt-get install smbfs) to make this work.  If you have to log into the share with a username and password, using "-o username=foo,password=bar" will work.  You can also place the username and password in a file and use "-o credentials=/path/to/creds" to authenticate.  See "man smbmount" for details. Remember to give the credentials file 400 permissions so only root can see it.  Use 600 permissions only to create or edit the file, then switch to read-only 400 when you're done.

You may need to apply 777 permissions to /mnt/point to enable access from your user account in Linux, or create the appropriate group rights and limit access to that.  On the Windows server, you'll have the permissions granted to the username you log in with.

---

### Post by dgrzalja on 2010-11-23
I don't think you understand what i'm saying.. 

I can mount the share normally. But when i go to the file manager and try to see the files they load forever and never show. I can see other shared folders that dont have that many files in a single folder normally. However, other pc's that are slower than this one and run WinXP can load the folder, so if shitty windows can do it, i bet ubuntu can too. Oh and one other thing, i tryed the same with XUbuntu, GUbuntu, KUbuntu, so it's not a file manager thing...

Any suggestions?

---

### Post by VanillaMozilla on 2010-11-23
That's good that you tried other versions, even though it didn't solve the problem.  I still wonder, however, if the problem is with Samba or some part of the directory service.  I think it could be either.

To eliminate Samba, I would try viewing the directory from the same computer, using XUbuntu. Boot with a live CD if you have to.  Then you'll know for sure where the problem is.

---

### Post by dgrzalja on 2010-11-24
I tryed, but i still can't access the files..

It's like samba is loading it forever, but some limit or something exists for getting the files, and it crosses that limit, so it won't load.. It looks something like that to me..

---

### Post by VanillaMozilla on 2010-12-03
Did you actually try it without Samba, as I suggested in my previous post?

I know Samba can be a pain to set up, but it IS possible that the problem is not Samba in this case.

Oh, never mind.  You CAN'T test without Samba on the same computer, can you?  I don't know.  I'm stymied by Samba myself.  Sorry I can't help.  I'm about to try paying Canonical to solve some of my networking and disk mounting problems.

---

### Post by bab1 on 2010-12-03
> **VanillaMozilla said:**
> Did you actually try it without Samba, as I suggested in my previous post?

I know Samba can be a pain to set up, but it IS possible that the problem is not Samba in this case.

Oh, never mind.  You CAN'T test without Samba on the same computer, can you?  I don't know.  I'm stymied by Samba myself.  Sorry I can't help.  I'm about to try paying Canonical to solve some of my networking and disk mounting problems.

Mounting it without using some of samba routine is not easily  possible when addressing a windows share.  The method **SeijiSensei ** recommended does, however eliminate the GUI file manager.

Wherever you mount the share it should be able to be inspected via normal CLI tools.

One final thought.  Why guess at what is going on?  Install and use Wireshark and IOtop and see what is actually going on.  Guessing is frustrating and ultimately a waste of everyone's time.

---

### Post by VanillaMozilla on 2010-12-05
> **bab1 said:**
> Mounting it without using some of samba routine is not easily  possible when addressing a windows share.  The method **SeijiSensei ** recommended does, however eliminate the GUI file manager.

Wherever you mount the share it should be able to be inspected via normal CLI tools.
?? My experience was exactly the opposite.  No problem with Nautilus, but I never did get access from the command line.  Samba's a big mess for mere mortals, in my opinion.

---

