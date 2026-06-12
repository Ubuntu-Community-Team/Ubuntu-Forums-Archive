---
title: "Mount FTP, FTP link"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by chloraldo on 2006-06-25
I have two FTP questions:

1. Can I mount an FTP-directory with fstab? How?
2. Can I make a symbolic link to an FTP dir? How?

Thanks!

---

### Post by JackandJohn on 2006-06-25
Yes, please; if anyone has updated information on this, or better; has successfully done it in dapper - please post a howto, or some instructions, and I will work on a howto.

If not; here are some places to start off:


[http://grifi.sourceforge.net/](http://grifi.sourceforge.net/)
[http://wiki.thiesen.org/page/Fuseftp](http://wiki.thiesen.org/page/Fuseftp)

FUSE looks like the best option, since it's a fairly mature way to mount different things as directories (wikipedia and flickr to name a couple)


I, personally, am Extremely interested in something that would connect to an ftp server when I browse the folder, or when I run a command. Then I could edit website files live.
This feature would blow windows out of the water for me.

---

### Post by purfier on 2006-06-27
You said it, I want it:)
So please post a howto on mounting ftp server.

---

### Post by JackandJohn on 2006-07-01
Sure; I can post a howto once I at all figure out how to do it.. Noone has come forward with any table scraps :(

Anyone: If you have gotten this working, post any tips, tricks, links, anything.


Once I can do it, I can make a good howto!

---

### Post by tturrisi on 2006-07-01
If you use Nautilus to connect to an ftp server then from then on it will be listed in Places menu.  You want to mount your own ftp server dirs or remote ftp server?

> I, personally, am Extremely interested in something that would connect to an ftp server when I browse the folder, or when I run a command. Then I could edit website files live.
check out Amaya!
[http://www.w3.org/Amaya](http://www.w3.org/Amaya)

---

### Post by dyssident on 2006-07-16
Ive gotten far enough to realize that there is no good Ubuntu package for FUSEFTP. Im going to need it as part of a larger "super easy home networking" tutorial Im writing, so I will report back when I make some progress.

In the mean time, if you own all the boxes you may want to consider using SSH for sharing. IMHO its superior in all ways to FTP. [Here is a good place to start]("http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/").

---

### Post by JackandJohn on 2006-07-31
> **tturrisi said:**
> If you use Nautilus to connect to an ftp server then from then on it will be listed in Places menu.

That works, but it's not as versatile as I need (cannot do command-line access, or network sharing, or access from apps that do not explicitly support gfs)

> **tturrisi said:**
> You want to mount your own ftp server dirs or remote ftp server?

Remote ftp server(s); basically client webpages for the most part, which is why I would hope to have something I can mount/unmount at will

> **tturrisi said:**
> check out Amaya!
[http://www.w3.org/Amaya](http://www.w3.org/Amaya)

I've never seen that before; it doesn't solve this specific problem, but wow; what a cool app - I'm going to be playing with it now for a few days, thanks :)

---

### Post by splitsch on 2006-08-10
Hello!
I up this thread, because I'd like to be able to mount remote ftp server.
I use Xubuntu, and Thunar, so I can't use nautilus.
And fuseftp doesn't work...

Do you have any clue to do that with xfce or thunar?

Thanks

Splitsch

---

### Post by dyssident on 2006-08-26
> **splitsch said:**
> 
I'd like to be able to mount remote ftp server.


what your looking for is curlftpfs. it is a FUSE extension, so you can mount ftp like any drive. 

ive been using it for a while and it works wonderfully. the only drawback is that its not in the ubuntu package repository for some reason, [but you can get the Debian package here](http://packages.debian.org/testing/utils/curlftpfs) (scroll down to Download curlftpfs they select your platform; select the closes mirror on the following page).

---

### Post by geoffDeGeoffGeoff on 2006-08-29
unfortunately that .deb doesnt install due to many dependency problems/wrong versions on my dapper box.

:confused:

---

### Post by petersjm on 2006-09-03
I've got my ftp site mounted in Nautilus which is perfect for me! Unfortunately, I don't want it appearing as a folder icon on my desktop... Does anyone know how to keep it mounted but not make it appear on my desktop?

---

### Post by dlai on 2006-09-03
it's probably something you can configure in gconf-editor...

---

### Post by pchev on 2006-09-05
Hi,

I just succeed to run fuseftp with Dapper! 
here some info if this can help:

First I install the following packages from Synaptic:
- libfuse2
- libfuse-dev
- fuse-utils (universe)
and fuseiso just to test fuse is really working.
(Perl is also required but you probably already have installed)

Then install the prerequisite Perl modules:
> sudo cpan -i Net::FTP Cache::File Term::ReadKey

Do NOT install the Fuse module from cpan because the last version require Fuse 2.5 and Dapper ship 2.4.

Go to: [http://search.cpan.org/~dpavlin/Fuse/](http://search.cpan.org/~dpavlin/Fuse/) 
and select "Fuse-0.06 22 Jun 2005", download the file and extract. 
Then:
> cd Fuse-0.06
> perl Makefile.PL
> make
> sudo make install

You can now install fuseftp from [http://wiki.thiesen.org/page/Fuseftp](http://wiki.thiesen.org/page/Fuseftp)
I get the version 0.8 : [http://perl.thiesen.org/fuseftp/fuseftp-0.8.tar.gz](http://perl.thiesen.org/fuseftp/fuseftp-0.8.tar.gz)
> cd fuseftp-0.8
> perl Makefile.PL
> make
> sudo make install

That's all for the install!

Next you must add you userid to the "fuse" group and you are ready.

Try for example:
> mkdir ubuntu
> fuseftp ubuntu ftp.ubuntu.com

---

### Post by mobin on 2006-09-11
Great tutorial pchev. Thanks for posting it.

Just one point I found useful. In order to log into ftp accpunts which require verification you can create a .netrc file in your home directory and add the user name and password for the ftp account. This will then be picked up automatically when you mount using the fuseftp command.

Example .netrc file:
[HTML]machine ftp.somemachine.com
        login username
        password yourpassword
[/HTML]



Make sure the permissions on the file are set so only the user can rwx, otherwise you get an error about the permissions.

---

### Post by glennric on 2006-09-14
> **petersjm said:**
> I've got my ftp site mounted in Nautilus which is perfect for me! Unfortunately, I don't want it appearing as a folder icon on my desktop... Does anyone know how to keep it mounted but not make it appear on my desktop?

I would like to find a way to stop this behavior as well.  You can do it with the gconf editor by setting /apps/nautilus/desktop/volumes_visible to false.  However, then your CD and DVD mounts will not show up when disks are inserted. I would like to be able to select which volumes show up, or something.

---

### Post by petersjm on 2006-09-15
> **glennric said:**
> I would like to find a way to stop this behavior as well.  You can do it with the gconf editor by setting /apps/nautilus/desktop/volumes_visible to false.  However, then your CD and DVD mounts will not show up when disks are inserted. I would like to be able to select which volumes show up, or something.

Me, too, Glen. I've turned volumes_visible off, but now I can't see any of my other drives... There must be a way.

---

### Post by glennric on 2006-09-15
> **petersjm said:**
> Me, too, Glen. I've turned volumes_visible off, but now I can't see any of my other drives... There must be a way.

One thing you can do is add the ftp site as a bookmark in Nautilus.  The bookmarks show up in the Places menu, but not on the desktop.  Although, this is not quite the same as mounting the location.

---

### Post by tsiMental on 2006-09-25
> 
Try for example:
> mkdir ubuntu
> fuseftp ubuntu ftp.ubuntu.com
This doesn't work : Get the following message:
fuse: failed to exec fusermount: Permission denied


It worked when I sudoed it. Though, then I could not access the directory.

Anyhow, tnx for the guide.

---

havar@havar-laptop:~$ fuseftp --debug ubuntu ftp.ubuntu.com
fuseftp 0.8 - 2005 (c) by Marcus Thiesen <marcus@thiesen.org>
Successfully logged into ftp.ubuntu.com
fuse: failed to exec fusermount: Permission denied
Segmentation fault

---

### Post by dysmas on 2006-10-19
'ning

righto, have the same problem, ie I need to be able to do access ftp for updating websites & testing code as i develop new sites. Im new to ubuntu and i am determined to do things in "user" mode as much as possible. First choice was to use Quanta's project management features (you store it on your ftp server, it handles the detail) but it is really unstable, and frequently misses out directories when sync'ing with the remote dir. Im sure the Fuse method would work, but after having a good look through the package list i came across "weex", and think it has my problem covered, here is the description text :

> A non-interactive FTP client for updating web pages
Weex is an utility designed to automate the task
 of remotely maintaining a web page or other FTP archive.
With weex, the maintainer of a web site or archive that must
be administered through FTP interaction can largely ignore
that process.
The archive administrator simply creates a local directory
that serves as an exact model for the off-site data.
All modifications and direct interaction is done locally to
this directory structure. When the administrator wishes to
coordinate the data on the remote site with that of the
local model directory, simply executing weex accomplishes
this in the most bandwidth-efficient fashion by only
transferring files that need updating. The program will
create or remove (!) files or directories as necessary to
accurately establish the local model on the remote server.

will be nice to have no lag when changing multiple small files, and i guess it will be best to make a keyboard shortcut to a script that will do the sync & reload the page im working on.

ps- first post

---

### Post by dysmas on 2006-10-19
ok, following up to my last post i have weex setup now and it works like a dream for working on websites. the man file was ++good, basically you have to do the following (substitue the ProfileName, yourhost, ftp-username, ftp-password & localusername/localdir for real values as required)

a) make a local copy of your all of your remote directory struct & files * (that is an important *)

b) install weex

c) make a file in ~/.weex/ called weexrc, along the lines of the following 

```

#My Config
#This is the ftp account profile, its name is in the square brackets
[ProfileName]
HostName = ftp.yourhost.co.uk
LoginName = ftp-username
Password = ftp-password
SrcDir = /home/localusername/localdir
DestDir = /
#ASCIIfile = *.c

#weex requires a [default] section, this is a default default
[default]
AsciiFile = {
*.htm
*.html
*.txt
*.asc
}

IgnoreLocalFile = {
*.bak
*.tmp
*.swp
}
```

d) make sure your local & remote files are both "current"

e) make some changes and run

```
weex -t ProfileName
```

to see what it would do, if you are happy with this you can omit the "-t" and it will apply the changes, how you integrate this depends on your situation.

run :
```
man weex
```

for optional switches & information on multiple profiles (you could create sub-complete-update profiles if you have only updated part of the site etc)

thankyou Yuuki Ninomiya & Chris X Edwards , it is indeed a very helpful program & very helpful manfile.

* if you dont do this & just create an empty dir, on the first sync all your remote (and probably live?) files will be deleted, this would probably be bad.

---

### Post by develcuy on 2006-11-27
Try with curlftpfs

[http://www.getdeb.net/category.php?id=14&release=Dapper](http://www.getdeb.net/category.php?id=14&release=Dapper)

---

### Post by charper_99 on 2007-08-28
Thanks dysmas, that weex program is really awesome!

---

### Post by Viperfang on 2007-11-22
Curlftpfs is easy enough to install...

Its in the universe, you you will have to make sure you enable that source first.

System -> Administration -> Software Sources -> Check the second box down (Gutsy)

The you have to use the synaptic package manager.

System -> Administration -> Synaptic Package Manager

Search for curlftpfs and mark it for installation.

Click Apply - it takes care of all of the dependencies for you.

In your home directory ( Places -> Home Folder ) create a file called ".netrc" (no quotes) you may have to enable hidden files first. ( Ctrl+H ).

then add a section for each password protected FTP like this:

machine <FTP Host>
login <FTP User>
password <FTP Password>

Make sure you replace the obvious!

Add mount points for each of the servers (or as many as you want mounted at any time)

then to mount you use the command:

sudo curlftpfs <Server as in .netrc> <mount point> -o allow_other -o uid=500

Thats all I did, hope it helps!

---

### Post by larytet on 2007-11-30
Re curlftpfs

It works fine when I ls the files on the server, but Nautilus locks out and after that ls does work too - does not exit. I do to resolve the situation, mount again

sudo curlftpfs 192.168.18.107 mnt1/ -o allow_other -o uid=500
ls for mnt1/

ls works

i am trying vi of a text file in the mnt1/ folder - vi locks

---

### Post by larytet on 2007-11-30
This is not for the FTP server, of course, but solved problem in my case - data transfer between two Ubuntu machines

I used sshfs 
sshfs is installed on the client side and ssh server on the server side
command 
sshfs username@192.168.18.107:/home/username  mountpoint/

mounts remote folder /home/username
fusermount -u mountpoint/
will unmount
no sudo is required - this is user space file system

---

