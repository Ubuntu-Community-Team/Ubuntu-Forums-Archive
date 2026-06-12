---
title: "Trying to access NAS files, attempts with Gigolo"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by hans12345 on 2012-10-16
I run several Ubuntu PCs and 1 Lubuntu. One PC is dual-boot with WIN XP.

To bring all my files together I got a simple Zyxel NAS model 310 as a file server. It runs a simple linux and is sold as a NAS for WIN users. The setup prepares Samba for the WIN PC and the whole thing works perfectly for WIN XP.

It sort of works for Ubuntu. Nautilus works fine, but Libre Office, FSLINT and Gnome Commander could not find the NAS files.

So I did my homework. I checked out Mount commands and FSTAB and got cold feet.

I found [http://ubuntuforums.org/showthread.php?t=1592340](http://ubuntuforums.org/showthread.php?t=1592340)

What I wanted was a GUI solution. And then I found Gigolo.

[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Thanks Morbius1 ! :p

Gigolo seems to work fine, well sort off.

Libre Office - this works great!
Gnome Commander finds the NAS but wont do the useful commands like compare dirs - it says operation cannot be performed on non-local files.
FSLINT does not find the NAS at all.
I get no icon for the NAS, which Gigolo says I should, but this is not very important.

1. Can I get Gigolo to do more for me? Maybe I missed something.
2. If I went the hard way with Mount etc, would Gnome Commander and FSLINT be happy?

Help appreciated

---

### Post by hans12345 on 2012-10-18
I should mention that these Ubuntu PCs are running on 12.04

---

### Post by LewisTM on 2012-10-19
There are couple more things you can do to make your NAS more easily accessible:

_1) Bookmark .gvfs_
In Nautilus, reveal hidden files and folders with Ctrl-H. In your home folder, select .gvfs and click Bookmarks->Add bookmark (Ctrl-D). You can edit it with Ctrl-B and give it a meaningful name such as 'Fileservers'. Programs that support Bookmarks in their file selector will be able to use this shortcut to access the NAS directly.
[COLOR="Red"]NOTE: In 12.10, the location of .gvfs has changed. It is now in /run/user/<yourname>/gvfs[/COLOR]

_2) Symlink you NAS_
Even better, navigate inside gvfs. If you are connected to your NAS, you should have it listed inside gvfs; it's a faily long and complicated name. Copy its full location to the clipboard. In a terminal, enter:
```
ln -s </full/path/to/gvfs/smbshare> ~/NAS
```
Now you should have a folder inside your home directory that will lead directly to your NAS contents and which can be accessed by any Linux application.

Cheers!

---

### Post by hans12345 on 2012-10-19
Thanks LewisTM

So far I tried solution 1.

It ( the .gvfs bookmark) works well for fslint. Gnome Commander still complains that it cannot work with network files, but maybe this is a problem with Commander itself.

Tomorrow I'll try solution 2. 

In 
ls -s </full/path/to/gvfs/smbshare> ~/NAS
I imagine I replace 'NAS' by the name I find?

I see a possible problem here, since the directory name I am trying to access has spaces in it : "public on nsa310" 

It could be this (the spaces) is the cause of my problems ?

Thanks anyway, I think I'm nearly there!

---

### Post by LewisTM on 2012-10-19
> Gnome Commander still complains that it cannot work with network files, but maybe this is a problem with Commander itself
I'm not sure but it's possible that softwares can't perform diffs on foreign filesystems.
> I imagine I replace 'NAS' by the name I find?

I see a possible problem here, since the directory name I am trying to access has spaces in it : "public on nsa310" 
You can replace it by any name you want.
For pathnames with spaces, just enclose the whole thing in quotes
```
"/home/you/.gvfs/public on nsa310"
```
I have made a typo. It should be
```
ln -s "/full/path/to/gvfs/smbshare" ~/NAS
```

---

### Post by hans12345 on 2012-10-27
I have not forgotten your help.

It's just that I had a dead PC with a failure on the system disk, so I have been distracted!

---

### Post by hans12345 on 2012-11-02
I finally tried solution 2, using the Symlink. That worked fine too.

Now I have several ways to access my NAS files!

Thanks again LewisTM

---

