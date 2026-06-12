---
title: "K3b IO error."
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by bPawn on 2007-01-17
I have the following problem while trying to write audio cds:

K3b output:
```
IO Error. Most likely no space left on harddisk
Removing temporary files
```

and the debug output:

```

System
-----------------------
K3b Version: 1.0rc4

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
TEAC DV-516G F4S6 (/dev/hdb, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]

TEAC DV-W516GB J4S2 (/dev/hda, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

```

df -h prints:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   33G  105G  24% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1             150G  116G   34G  78% /media/WINDOWS
/dev/hdb              4.1G  4.1G     0 100% /media/cdrom1



```
Although I use rc4 the problem also exists at the default k3b of edgy installation. The only difference is the output message "IO Error." (very verbose :evil: )

Gnomebaker seems to work just fine

any ideas?

---

### Post by mervg on 2007-01-19
I had the same problem with Audacity. I followed a suggestion to disable ESD and system sounds in Preferences>Sound where I cleared the 'enable software sound mixing (ESD)'. That resolved the problem.

I run Dapper

---

### Post by bPawn on 2007-01-20
I use KDE... but I don't thing that disabling arts will fix the problem since I don't want to play audio, I want to burn audio. I will check it and if it works I 'll post again.

---

### Post by mndzmyst on 2007-12-09
I had the same issue and solved it by changing my temp folder (settings=>> configure k3b). It was using a non-existing one.

---

### Post by refractal on 2008-03-15
yes, making sure the temp directory is linked to a real folder fixed the problem for me

---

### Post by em3raldxiii on 2008-07-09
One of the more recent updates must have changed the temporary directory for K3B because this problem only recently happened to me.  This thread solved my problem :D

So just to recap for any new Ubuntu users struggling with the same peculiar issue:

If you are getting this error:

"IO Error. Most likely no space left on harddisk."

In K3B, go to Settings > Configure K3b

In the General section, at the top, make sure that the Default Temporary Directory points to a legitimate directory that exists on your harddrive.

2 options here, you can either copy the name of the directory that K3b is already using and using your console to create the directory (where /foo/bar is replaced by your folder):

```
 mkdir /foo/bar 
```

or you could find a folder that already exists on your harddrive (such as /tmp) and put that directory in the appropriate field in K3b.

Cheers! :guitar:

---

