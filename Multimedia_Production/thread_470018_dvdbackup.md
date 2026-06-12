---
title: "dvdbackup"
date: 2007-06-10
forum: Multimedia Production
---

### Post by O-pos on 2007-06-10
Hello,

I was interested in command-line DVD backup tool and tried dvdbackup. It works, however it never gives message what it is doing, what file it is copying, how much % and time elapsed/remained etc.. it only gives message when something's wrong, for example "couldn't copy **.. etc).

Can somebody tell me how can I bring it to give me details of what operations it is performing, or tell me good alternative command-line dvd backup tool?

Thanks.

---

### Post by nalmeth on 2007-06-10
```
$ man dvdbackup
...

OPTIONS
       A summary of options is included below.

       -i DEVICE
              where device is your dvd device

       _**-v X   where X is the amount of verbosity**_

       -I     for information abo...
```

---

### Post by pgroudas on 2007-06-15
I've noticed that even verbose mode doesn't give much indication of progress.  An alternative command line utility is vobcopy, but I've had mixed results with it.  You could also use mplayer.

Mplayer dvd://1 -dumpstream -dumpfile file.vob

Where "1" is the title you want and file.vob is the output file.

---

### Post by andrew.46 on 2007-08-16
Hi,

 Saw your comments about dvd ripping:

> **O-pos said:**
> Hello,

I was interested in command-line DVD backup tool and tried dvdbackup. It works, however it never gives message what it is doing, what file it is copying, how much % and time elapsed/remained etc.. it only gives message when something's wrong, for example "couldn't copy **.. etc).

Can somebody tell me how can I bring it to give me details of what operations it is performing, or tell me good alternative command-line dvd backup tool?

Thanks.

Well you could try vobcopy as follows:

```
vobcopy -v -m /media/cdrom0 
```

which gives a pretty verbose process. The -m is a mirror option.

           Andrew

---

