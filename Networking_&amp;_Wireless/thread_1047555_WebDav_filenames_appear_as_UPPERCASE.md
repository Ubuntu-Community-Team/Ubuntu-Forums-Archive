---
title: "WebDav filenames appear as UPPERCASE"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by mrmoney on 2009-01-22
Hey,

I am having some issues with a mounted WebDav drive.
I can mount it fine, open and edit files. But the problem is that all the file/directory names appear to me as all UPPERCASE.

For example: the actual path
foo/bar/baz.html
appears to me as FOO/BAR/BAZ.HTML

When I edit the file and save it, it is renamed from foo/bar/baz.html to foo/bar/BAZ.HTML and the server being linux and case-sensitive, it breaks any references to that file being made elsewhere.

I have no idea why this is. Any help is greatly appreciated.
I am using davfs2 mounted as a normal user.

Thanks in advance

---

### Post by albinootje on 2009-01-22
> **mrmoney said:**
>  For example: the actual path
foo/bar/baz.html
appears to me as FOO/BAR/BAZ.HTML


Can you give an example how you mounted it ?

And can you try connecting with "cadaver" the command line webdav client, to see whether that also shows everything in uppercase.
For example :
```

sudo apt-get install cadaver
cadaver https://your_webdav_server:portnumber/your_webdav_directory

```

---

### Post by mrmoney on 2009-01-22
Hey,

thanks for the reply.

I mounted the directory by following the usual davfs procedure.
- installed davfs
- reconfigured to allow non-root users to mount
- selected group and user as davfs for the daemon
- added myself to group davfs
- created a directory in my home directory to mount to
- added the appropriate line in /etc/fstab
   [http://foo.com/dav](http://foo.com/dav) /home/mike/mnt/foo.com davfs user,noauto,rw 0 0
- mounted by running
mount ~/mnt/foo.com
- entered my username and password

Those are what I remember, I am no longer at work, so it might be a little off. I also had to disable file locking in my ~/.davfs/davfs.conf preferences as the remote directory did not support it and was causing other errors when I tried to edit files.

Other than that I dont think I did anything out of the ordinary.

Ill try cadaver tomorrow when I am back at work. Thanks for the suggestion

---

### Post by mrmoney on 2009-01-22
Oh, and one other point, is that this is not over https, it is a regular http address I am hitting

---

### Post by mrmoney on 2009-01-23
> **albinootje said:**
> 
And can you try connecting with "cadaver" the command line webdav client, to see whether that also shows everything in uppercase.


I just installed and tried cadaver, and the paths and filenames are all proper case...

so does that mean my davfs configuration is the screwy part? Or is it something on their end, I am confused

---

### Post by albinootje on 2009-01-23
> **mrmoney said:**
> I just installed and tried cadaver, and the paths and filenames are all proper case...

so does that mean my davfs configuration is the screwy part? Or is it something on their end, I am confused

Okay, it sounds like your davfs configuration needs tweaking, or perhaps you found a bug.
I will try to test with davfs myself later on.

---

### Post by mrmoney on 2009-01-23
thanks,

I tried completely removing davfs and re-installing to see if that helped. Unfortunately, still the same result.

Some more weirdness is this:

The full path for the WebDav directory might be

~/mnt/foo.com/foo/bar/baz/blah/blahblah.html

What I see is something like this

~/mnt/foo.com/foo-slash/bar-slash/BAZ/BLAH/BLAHBLAH.HTML

The two top-most directory names are appended with '-slash' before the rest follow the all uppercase convention.

---

