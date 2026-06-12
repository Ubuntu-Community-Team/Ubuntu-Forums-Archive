---
title: "GnomeBaker || mkisofs: Directories too deep"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by altonbr on 2006-10-30
I'm trying to backup sections of my /home partition manually using GnomeBaker (0.6.0-0ubuntu2 (Edgy)).

Apparently, it can't burn the DVD because I have too many embedded directories. It only allows 6 and I'm sure I have some going up to 12 or so. See attached image (screenshot) for details.

A gentlemen had a similar problem and posted it at the GnomeBaker forum but got no reply. ([http://gnomebaker.sourceforge.net/forum/viewtopic.php?t=924]("http://gnomebaker.sourceforge.net/forum/viewtopic.php?t=924"))


Here is the output of my terminal when running "gnomebaker":
```
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(gnomebaker:684): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

** (gnomebaker:684): WARNING **: gbcommon_close_temp_file - Temporary file descriptor [/tmp/GnomeBaker-root/gnomebaker-VJ3KIT] could not be closed

** (gnomebaker:684): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:684): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:684): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:684): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

```


I was hoping someone could shed some light into this situation, because if I can't backup folders that are more then 6 directories deep, what can I do? Install K3B I guess.. but that's ALOT of extra packages.

Thanks guys.

---

### Post by daveisadork on 2006-10-30
The directory depth is a limitation of the ISO filesystem, not gnomebaker itself. So, I doubt burning the CD with k3b will work either. The easiest solution I can think of is to make a big tarball out of everything you want to save and then burn that

---

### Post by altonbr on 2006-10-30
Yeah, that reply makes sense, although the solution would be tedious when crunching all the data together... but I'll give it a try if worse comes to worse.

The only thing is, I haven't changed that directory path (for "my_pcvs") for about 4 backups now. It seems to have done this all of a sudden... but if what you say is true, I'm not sure how any of them would have worked.

The attached image (screenshot) is of me opening "backup-2.06.09.06". You can see that the directories are at LEAST 8 deep. THAT's why I'm confused.

I forget what I used to do that backup... it might have been a program in Windows.. but I doubt it.

---

### Post by altonbr on 2006-10-30
So my problem is, I need to do backups that have more then 6 embedded directories. Anyone know a work around?

---

### Post by altonbr on 2006-10-31
Bump. Any ideas?

---

### Post by altonbr on 2006-11-02
Sorry guys, I REALLY hate bumping, but I REALLY need to backup all my files and I'm stuck. What can I do? :-k

---

### Post by merlos on 2006-11-12
A small contribute to this post.

I had the same problem while trying to burn my preference directory with GnomeBaker; I confirm that deep burning level is an ISO fs limitation 
[http://en.wikipedia.org/wiki/ISO_9660#Levels_and_restrictions](http://en.wikipedia.org/wiki/ISO_9660#Levels_and_restrictions)
[http://en.wikipedia.org/wiki/Rock_Ridge](http://en.wikipedia.org/wiki/Rock_Ridge)
but with mkisofs you can force this behavior and skip this limit with -D option

How can we do the same think with GnomeBaker? I think we can't do this with graph interface, but...

I launched gnomeBaker inside a terminal with debugging messages
```
gnomebaker --trace-on
```
I created a new project, added directories and then tried to burn a new DVD; finally I received the usual error message
```
mkisofs: Directories too deep for 'giovanni/Desktop/Downloads/VMware/vmware-server-distrib/lib/modules/source' (7) max is 6.
:-( write failed: Input/output error
```

Come back to shell, and after many debug lines at the end you can see the spawned process (growisofs)

```
growisofs -Z /dev/hdc -speed=4 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -gui -V "GnomeBaker data disk" -A GnomeBaker -p Giovanni -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-giovanni/gnomebaker-5U3RIT (null) 
exec_spawn_process - spawed process with pid [8525]
```

While gnomebaker is open (don't close, otherwise tmp file with files list will delete) launch the same command with -D option
```
growisofs **-D** -Z /dev/hdc -speed=4 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -gui -V "GnomeBaker data disk" -A GnomeBaker -p Giovanni -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-giovanni/gnomebaker-5U3RIT
```

Now I have my data DVD
:D 

Hope this help

Bye

---

### Post by ptmurphy on 2006-11-12
Funny thing is that with the last version of Gnomebaker I used to always burn without any problems.  Now with the new version it checks this 6-level directory thing!

---

### Post by altonbr on 2006-11-13
Hmm, thanks merlos, I'll give that suggestion a try.

But does anyone know of a program that doesn't have the same problem as GnomeBaker, or where to get an older version that will allow more than six directories? Thanks.

---

### Post by daver2u on 2006-11-15
BUMP

This is a problem as I cannot burn the dvd even when I use the command line I will paste the output:

[0x809c598] [exec_working_dir_setup_func] [exec.c] [205]
Executing 'mkisofs -gui -V GnomeBaker data disk -A GnomeBaker -iso-level 3 -l -r -hide-rr-moved -graft-points --path-list /tmp/GnomeBaker-dave/gnomebaker-FENOIT | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
mkisofs: Directories too deep for 'bin/acadfeui/Extra Samples/Models/Slot Machine/Cabinet/Bill Validator/Cash Can' (7) max is 6.
:-( write failed: Input/output error

And when I try:
growisofs **-D** -Z /dev/hdc -speed=4 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -gui -V GnomeBaker data disk -A GnomeBaker -iso-level 3 -l -r -hide-rr-moved -graft-points --path-list /tmp/GnomeBaker-dave/gnomebaker-FENOIT

I get:
Executing 'mkisofs -D -gui -V GnomeBaker data disk -A GnomeBaker -iso-level 3 -l -r -hide-rr-moved -graft-points --path-list /tmp/GnomeBaker-dave/gnomebaker-FENOIT | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node - 'data'.
:-( write failed: Input/output error

any ideas?

---

### Post by merlos on 2006-11-16
> **daver2u said:**
> 
And when I try:
growisofs **-D** -Z /dev/hdc -speed=4 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -gui -V GnomeBaker data disk -A GnomeBaker -iso-level 3 -l -r -hide-rr-moved -graft-points --path-list /tmp/GnomeBaker-dave/gnomebaker-FENOIT

I get:
Executing 'mkisofs -D -gui -V GnomeBaker data disk -A GnomeBaker -iso-level 3 -l -r -hide-rr-moved -graft-points --path-list /tmp/GnomeBaker-dave/gnomebaker-FENOIT | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node - 'data'.
:-( write failed: Input/output error

any ideas?

I think you must try 

```
growisofs **-D** -Z /dev/hdc -speed=4 -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -gui -V **'GnomeBaker data disk'** -A GnomeBaker -iso-level 3 -l -r -hide-rr-moved -graft-points --path-list /tmp/GnomeBaker-dave/gnomebaker-FENOIT

```

with "GnomeBaker data disk" quoted, otherwise the command fails.

Merlos

---

### Post by altonbr on 2006-11-18
This is sort of ridiculous. I decided I need to dual-boot now with Windows, so I need to format my HD and install XP then Ubuntu afterwards... but I need to backup my data partition just in case.

Can ANYONE help?

---

### Post by altonbr on 2006-11-18
Hey merlos,

I just used a CD burning program called Brasero and it didn't seem to complain about the directories. Maybe give it a try?

---

### Post by altonbr on 2006-12-12
Anyone else experiencing this?

---

### Post by db9s on 2007-01-03
i did the same, looks like its working

---

### Post by Gustavo Narea on 2007-03-02
> **daveisadork said:**
> The directory depth is a limitation of the ISO filesystem, not gnomebaker itself. So, I doubt burning the CD with k3b will work either. The easiest solution I can think of is to make a big tarball out of everything you want to save and then burn that

Actually, this doesn't happen if you use K3B. Give it a try.

---

### Post by Meurglys on 2007-10-02
Or simply use the built-in CD/DVD Creator in Nautilus to burn data DVDs and GnomeBaker for everything else, like ISOs.

---

### Post by supremedalek on 2008-03-28
Resurrecting this old thread, I tried to use the built-in CD/DVD Creator in Nautilus to burn the contents of a XP-formatted hard drive and ended up having the same issue.  In fact, right now I still have no good way to backup those files to a dvd under Linux in general, ubuntu specifically. I may try under osx, but I would rather not.

---

### Post by triniton on 2008-03-31
use -iso-level=4 instead of iso-level=3

---

### Post by narcisgarcia on 2008-05-29
If K3B doesn't start to record with the error message "Could not determine size of resulting image file" and in the debug details the mkisofs/genisoimage tool is saying something like "genisoimage: Directories too deep for 'a/b/c/d/e/f/g/h' (7) max is 6.", you need to disable deep directory relocation:

Go to Settings menu in K3B, Configure K3B option, Programs section, User Parameters tab, edit the "mkisofs" line and add the text "-D".

Note: This violates ISO9660

---

