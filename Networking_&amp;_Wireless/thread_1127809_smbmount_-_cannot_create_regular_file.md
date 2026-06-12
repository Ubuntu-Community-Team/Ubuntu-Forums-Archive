---
title: "smbmount - cannot create regular file"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by fermulator on 2009-04-16
Hi there!

Hoping to find someone with a similar problem, or experience with mounting a samba share to the local file system using *smbmount*.

_**Scenario - 2 Desktops, 1 Server**_
 * **myserver**, ubuntu 8.04 server, running samba server
 * **winxp**, windows xp
 * **ubuntu**, ubuntu 8.10

OK.  I'll simplify my situation so it makes sense.  "myserver" has two samba shares, "Downloads" and "Stuff".  Both have sub directories "/foo/bar".

The "bat" folder contains many empty files, we'll call them: A, B, C, and D.

> :myserver
--stuff
----foo
------bar
--downloads
----foo
------bar
--------bat
----------A
----------B
----------C
----------D

_**Task:**_
 * Copy the directory bat (and all it's contents) from smb://myserver/Downloads/foo/bar
 * Paste the directory bat (and all it's contents) to smb://myserver/Stuff/foo/bar

_What Works:_
From both **winxp** and **ubuntu**, if we browse using the "Network", this works without a hitch.  In **winxp**, we can browse to \\myserver and perform the task.  In **ubuntu**, we can browse to smb://myserver and perform the task.

_The Setup and Config_
However, as we all know, browsing through the "network browser" in Linux doesn't achieve maximum performance.  So, the solution for most, mount the server shares to the local file system.  There are two directories with the mounted samba shares:
 * /mnt/myserver/downloads
 * /mnt/myserver/stuff

Here's the fstab entry for such a thing:
```
//myserver/Downloads /mnt/myserver/downloads cifs auto,credentials=/home/fermulator/.smbcredentials,workgroup=WORKGRUOP,gid=fermulator,uid=fermulator,rw,errors=continue       0       6
//myserver/Stuff /mnt/myserver/stuff cifs auto,credentials=/home/fermulator/.smbcredentials,workgroup=WORKGRUOP,gid=fermulator,uid=fermulator,rw,errors=continue       0       6
```

To be brief on the fstab entry, we need gid and uid entries because we're not on a domain, and the numerical values of uid and gid might not match between server and client, the rest is self explanatory and status quo mostly.

So, finally, on to the problem:

_**What Doesn't Work:**_

_Using the GUI_
On the **ubuntu** machine, if we browse using Nautilus to /mnt/myserver, and try to copy and paste, we receive the following error:
> Error while copying "A".
There was an error copying the file into /mnt/myserver/stuff/foo/bar/bat.
Show more details (expanded)
Error opening file '/mnt/myserver/stuff/foo/bar/bat/A': Permission denied.

 * If I choose **Cancel**, the operation is canceled, but the 'bat' directory exists.
 * If I choose **Skip** (or Skip All), the file A is skipped, but then B, C, D are successfully copied!  (weird!)

_Using the Command Line:_
```
cd /mnt/myserver/downloads/foo/bar
cp -Rv bat /mnt/myserver/stuff/foo/bar
```
> cp: cannot create regular file '/mnt/myserver/stuff/foo/bar/bat/A': Permission denied.

Again, same as with Nautilus, the directory bat was created, but this time no files were copied.
Try the command:
```
cp -Rv bat /mnt/myserver/stuff/foo/bar
```
again? ... no problem, the files are copied.

What gives?  It's like when a samba share is mounted, it takes a second for the ACLs from the server to propagate or something? ... anytime we try to copy/paste again, the operation is successful so long as the parent directory was not JUST NOW created, but created "a few seconds ago".

Just for those non-believers, the permissions on the client side are correct!
> drwxrwx---  2 fermulator fermulator 0 2009-04-16 21:41 1969 - 20 20 bat
Even on the server side, if I do a getfacl on the bat directory, or it's parent bar, in either source or destination, the correct ACLs (generated from the default ACLs) have been applied.

We *KNOW* that the permissions are correct anyways since if we retry the task, *THEN* it works ... this seems to be something with 'timing'?...

Any light would be wonderful!

---

### Post by xrat on 2009-05-05
Hi fermulator,
Thanks a lot for this detailed description. I am facing the exact same problem with a Ubuntu 9.04 client trying to copy folders to a Debian Samba 3.2.5.

So, the problem is not just copying from share to share. When I try to copy a local folder to the Samba share nautilus says "Error while copying ..." and "Error opening file '/home/tux/mnt/sambashare/sample.jpg': Permission denied" in the details.

I thought that someone must have had reported this already, but I could not find any bug reports. What's worse I have no idea why it doesn't work :-(

---

### Post by fermulator on 2009-05-05
> **xrat said:**
> Hi fermulator,
Thanks a lot for this detailed description. I am facing the exact same problem with a Ubuntu 9.04 client trying to copy folders to a Debian Samba 3.2.5.

So, the problem is not just copying from share to share. When I try to copy a local folder to the Samba share nautilus says "Error while copying ..." and "Error opening file '/home/tux/mnt/sambashare/sample.jpg': Permission denied" in the details.

I thought that someone must have had reported this already, but I could not find any bug reports. What's worse I have no idea why it doesn't work :-(

Interesting, I just upgraded to Jaunty 9.04 as the ubuntu client, and I SEEM to be able to copy/cut and paste without problems now.  It is a fresh install, so perhaps there was a conflict somewhere?

The server installation has not been updated at all.

---

### Post by xrat on 2009-05-06
That's strange. Anyway, something's broken. And there are plenty of reports of problems with Nautilus, Samba & Co. Just this particular issue I can't find anywhere else.
But I am tired of looking any further. I'll use the .gvfs path for now.

---

### Post by pollamat on 2009-06-23
I have the exact same problem however my server is OpenSuSE 10.3 and the client is Ubuntu Intrepid.    This is the most frustrating issue I have had the misfortune to encounter in a very long time...     I am still with out a fix so Please any one... post with a fix...

---

### Post by dmizer on 2009-06-23
Have a look through some of the troubleshooting remarks at the bottom of my CIFS howto (2nd link in my sig).

If you're mounting via fstab (in Ubuntu) it's critical to make sure that you have the smbfs metapackage installed:
```
sudo aptitude install smbfs
```
While Ubuntu does allow for some samba functionality out of the box, it's not really a complete set of packages, and really only caters to the needs of very simple peer to peer file sharing over GVFS (places > connect to server).

---

### Post by xrat on 2009-06-27
Hi dmizer,
Thanks a lot for having a look at this thread. I am afraid, though, that your troubleshooting chapter does not apply here. As far as I can tell the problem occurs and always occurred even with a proper setup. I still think that a bug is involved (just did not find the time yet to reproduce on a clean installation and properly report it).

May I suggest the following example to reproduce (and hopefully clarify):

What I am going to use
```
tux@client:~$ grep "/home/tux/mnt/myshare" /etc/fstab
//smbserver/myshare  /home/tux/mnt/myshare  cifs  credentials=/root/.smbcred,uid=1000  0  0
tux@client:~$ grep "/home/tux/mnt/myshare" /proc/mounts
//smbserver/myshare /home/tux/mnt/myshare cifs rw,mand,unc=\\smbserver\myshare,username=andreas,uid=1000,posixpaths,acl,rsize=16384,wsize=57344 0 0
tux@client:~$ mkdir testdir
tux@client:~$ touch testdir/somefile
```

First encounter of the problem:

```
tux@client:~$ cp -r testdir /home/tux/mnt/myshare
cp: cannot create regular file `/home/tux/mnt/myshare/testdir/somefile': Permission denied
```

The same command works when issued again (because the first try actually did create the directory, only the file could not be copied):

```
tux@client:~$ cp -r testdir /home/tux/mnt/myshare
```

Let's try again after creating the directory ourselves:

```
tux@client:~$ rm -r /home/tux/mnt/myshare/testdir # just to clean up
tux@client:~$ mkdir /home/tux/mnt/myshare/testdir && cp -r testdir /home/tux/mnt/myshare
cp: cannot create regular file `/home/tux/mnt/myshare/testdir/somefile': Permission denied
tux@client:~$ cp -r testdir /home/tux/mnt/myshare
```

Let's try again and let's see if it is a timing issue (which it is i.a.)

```
tux@client:~$ rm -r /home/tux/mnt/myshare/testdir # clean up again
tux@client:~$ mkdir /home/tux/mnt/myshare/testdir && sleep 1 && cp -r testdir /home/tux/mnt/myshare
tux@client:~$ ls -o /home/tux/mnt/myshare/testdir
total 0
-rw------- 1 tux 0 2009-06-27 19:35 somefile
```


Indeed, it apparently is not just a timing issue since I've just found out that **copying folders does work without problems as root**. As you see I am using "uid=1000" (and always did). Adding "file_mode=0777,..." did not help. Interestingly, "nounix" does not work for me. With "nounix" the mount point is empty.

---

### Post by dmizer on 2009-06-28
I discuss this exact problem under the "Files owned by root" section. You'll need to add the gid (in addition to the uid). Also add the nounix option.

Also, you have some strange options that apply to ext3 rather than CIFS. Having them in your CIFS mount command doesn't hurt anything (because they are simply ignored) but they're not doing anything either.

Try something like this instead.
```
//smbserver/myshare /home/tux/mnt/myshare cifs rw,username=andreas,uid=1000,[COLOR="Red"]gid=1000,nounix[/COLOR],rsize=16384,wsize=57344 0 0
```

See man mount and man mount.cifs for more information.

The problem is that you need to disable unix style permissions handling over CIFS because CIFS can't pass them correctly (remember, this is Windows file sharing, not Linux).

Edit:
It has also [been suggested](http://ubuntuforums.org/showpost.php?p=7530129&postcount=987) to try the "noperm" option as well.

---

### Post by xrat on 2009-06-29
Hi dmizer,
Thanks again for your efforts.

First of all, adding "noperm" works around the timing issues when copying folders. **With "noperm" it works as the user, too.** Thanks for the hint. Nevertheless, IMHO, this just underlines the fact that the actual error is to be found somewhere else.

To clarify and comment your remark: I am not using any ext3 options. Maybe the grep command was confusing. I tried to clear it up by breaking it up into two separate commands. I am using practically what you recommend in your "Files owned by root" section, which, however, from my point of view does not discuss timing problems where writing files works whereas copying folders does not. But never mind.

---

### Post by dmizer on 2009-06-29
> **xrat said:**
> Hi dmizer,
Thanks again for your efforts.

First of all, adding "noperm" works around the timing issues when copying folders. **With "noperm" it works as the user, too.** Thanks for the hint. Nevertheless, IMHO, this just underlines the fact that the actual error is to be found somewhere else.

To clarify and comment your remark: I am not using any ext3 options. Maybe the grep command was confusing. I tried to clear it up by breaking it up into two separate commands. I am using practically what you recommend in your "Files owned by root" section, which, however, from my point of view does not discuss timing problems where writing files works whereas copying folders does not. But never mind.

Yes, that did clear things up. Sorry for the confusion.

This may be how unix permissions are set up locally on the server side of things. A "ls -la" on the shared directory may shed light on what may have been causing this problem. It normally shouldn't matter, but since both server and cient are Unix, it adds a level of complexity for permissions.

---

### Post by xrat on 2009-06-29
> **dmizer said:**
> A "ls -la" on the shared directory may shed light on what may have been causing this problem.

In general, yes, but not in the case described. Here everything is fine. User can create directories and files. It's just that files cannot be created right after creating a directory. However, a few milliseconds later it works.

---

### Post by trinacriax on 2009-07-30
Hi to all,
I've experienced the same problem but the proposed solution does not work for me.

In my /etc/fstab I have this line:
```

//SERVER/SHARE/ /home/MYUSER/MOUNTDIR smbfs credentials=/etc/samba/.credentials,noauto,user,rw,uid=1000,gid=1000,file_mod=0777,dir_mode=0777 0 0

```

I would like to mount the shared folder and work on it as normal user.
```

$ mount MOUNTDIR
$ cd MOUNTDIR
$ ls 
test.txt 
$ cd ~
$ cp test2.txt MOUNTDIR
$ ls MOUNTDIR
test.txt test2.txt
$ cp test2.txt MOUNTDIR
cp: cannot create regular file `blade-2/test2.txt': No such file or directory
$ rm MOUNTDIR/test2.txt

```

It't look like I can write each file only once, no re-write are allowed.
Any suggestions???
I have no idea!
PS In the remote server my user has a different name and uid (1011), in the fstab i wrote the uid of the user that access to the shared folder.

---

### Post by fermulator on 2009-07-30
> **trinacriax said:**
> Hi to all,
I've experienced the same problem but the proposed solution does not work for me.

In my /etc/fstab I have this line:
```

//SERVER/SHARE/ /home/MYUSER/MOUNTDIR smbfs credentials=/etc/samba/.credentials,noauto,user,rw,uid=1000,gid=1000,file_mod=0777,dir_mode=0777 0 0

```

I would like to mount the shared folder and work on it as normal user.
```

$ mount MOUNTDIR
$ cd MOUNTDIR
$ ls 
test.txt 
$ cd ~
$ cp test2.txt MOUNTDIR
$ ls MOUNTDIR
test.txt test2.txt
$ cp test2.txt MOUNTDIR
cp: cannot create regular file `blade-2/test2.txt': No such file or directory
$ rm MOUNTDIR/test2.txt

```

It't look like I can write each file only once, no re-write are allowed.
Any suggestions???
I have no idea!
PS In the remote server my user has a different name and uid (1011), in the fstab i wrote the uid of the user that access to the shared folder.

What happens if you change your fstab entry from:
> //SERVER/SHARE/ /home/MYUSER/MOUNTDIR smbfs credentials=/etc/samba/.credentials,noauto,user,rw,uid=1000,gid=1000,file_mod=0777,dir_mode=0777 0 0
to
> //SERVER/SHARE/ /home/MYUSER/MOUNTDIR smbfs credentials=/etc/samba/.credentials,rw,uid=1000,gid=1000,file_mod=0777,dir_mode=0777 0 0

Just curious if the manual mounting and user allowed mount maybe mucks something up.  To test, you'll have to mount as root.

Also, after you've done that test code that you wrote, can you please place the output of ```
ls -al MOUNTPOINT?
```.  Do it from the CLIENT side, and from the SERVER side.

---

### Post by trinacriax on 2009-07-30
I've changed the mount point as you suggested
```

$ sudo mount MOUNTDIR
$ cp test.txt  MOUNTDIR/
$ cp test.txt  MOUNTDIR/
cp: cannot create regular file `MOUNTDIR/test.txt` No such file or directory

```

now, on the client side
```

$ ls -la 
...
drwx-----x 15 trinacriax trinacriax     0 2009-07-30 14:10 MOUNTDIR
...

and 

$ ls -la MOUNTDIR
drwx-----x 15 trinacriax trinacriax     0 2009-07-30 14:10 .
drwxr-xr-x 53 trinacriax trinacriax  4096 2009-07-30 14:08 ..
-rw-------  1 trinacriax trinacriax 10128 2009-07-30 14:03 .bash_history
-rw-r--r--  1 trinacriax trinacriax   220 2006-12-11 23:28 .bash_logout
-rw-r--r--  1 trinacriax trinacriax   414 2006-12-11 23:28 .bash_profile
-rw-r--r--  1 trinacriax trinacriax  2304 2008-11-12 17:48 .bashrc
-rwx------  1 trinacriax trinacriax   357 2009-07-30 14:10 test.txt
-rw-------  1 trinacriax trinacriax   866 2009-07-06 14:38 .gnuplot_history
-rw-------  1 trinacriax trinacriax   965 2009-07-30 14:03 .lesshst
drwxr-xr-x  2 trinacriax trinacriax     0 2009-06-17 11:24 .mc
drwxrwx---  4 trinacriax trinacriax     0 2009-07-28 15:20 public_html
drwx------  2 trinacriax trinacriax     0 2009-07-29 10:02 .ssh
-rw-------  1 trinacriax trinacriax 11480 2009-07-29 17:04 .viminfo

```

server side

```

$ ls -la
drwx-----x 15 russo users  4096 2009-07-30 14:10 .
drwxr-xr-x 11 root  root   4096 2009-07-16 11:26 ..
-rw-------  1 russo users 10128 2009-07-30 14:03 .bash_history
-rw-r--r--  1 russo users   220 2006-12-11 23:28 .bash_logout
-rw-r--r--  1 russo users   414 2006-12-11 23:28 .bash_profile
-rw-r--r--  1 russo users  2304 2008-11-12 17:48 .bashrc
-rwx------  1 russo users   357 2009-07-30 14:10 test.txt
-rw-------  1 russo users   866 2009-07-06 14:38 .gnuplot_history
-rw-------  1 russo users   965 2009-07-30 14:03 .lesshst
drwxr-xr-x  2 russo users  4096 2009-06-17 11:24 .mc
drwxrwx---  4 russo users  4096 2009-07-28 15:20 public_html
drwx------  2 russo users  4096 2009-07-29 10:02 .ssh
-rw-------  1 russo users 11480 2009-07-29 17:04 .viminfo

```

any idea??

---

### Post by dmizer on 2009-07-30
With CIFS mounts, the user option is reserved for username and password. If you want a regular user to be able to mount and control the share, you'll have to use the "users" option like so:
```
//SERVER/SHARE/ /home/MYUSER/MOUNTDIR smbfs credentials=/etc/samba/.credentials,noauto,[COLOR="Red"]users[/COLOR],rw,uid=1000,gid=1000,file_mod=0777,dir_mode=0777 0 0
```

For more information, see man mount.cifs
```
       user=arg
          specifies the username to connect as. If this is not given, then the
          environment  variable  USER  is  used. This option can also take the
          form "user%password" or  "workgroup/user"  or  "workgroup/user%pass&#8208;
          word" to allow the password and workgroup to be specified as part of
          the username.
```
and man mount
```
              users  Allow  every  user  to mount and unmount the file system.
                     This option implies the options noexec, nosuid, and nodev
                     (unless  overridden  by  subsequent  options,  as  in the
                     option line users,exec,dev,suid).
```

---

### Post by trinacriax on 2009-07-30
Hi dmizer,

I've just tried your hints but without success.
I don't know why, I think I'll switch to sshfs.
thx

---

### Post by xrat on 2009-07-31
trinacriax -- I do not think that you are experiencing the exact same problem (we were talking about copying folders, you have problems copying files).

I guess that you should have a look at how the share is defined on the server's smb.conf.

HTH.

P.S.: sshfs is a very good alternative, anyway.

---

### Post by varanasi on 2009-11-15
Anyone figure this problem out?

I have the same problem (error reported creating a folder but the folder is created and the copy command then works on the second try) with 9.04 clients and a unix server.

---

### Post by varanasi on 2009-11-15
I think this is the bug . . . 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221887)

---

### Post by xrat on 2009-11-17
> **varanasi said:**
> I think this is the bug . . . 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221887)

Many thanks for this pointer. This is the bug report that I have been looking for for a long time.

It describes the same behavior only with "mkdir" instead of "cp".

---

