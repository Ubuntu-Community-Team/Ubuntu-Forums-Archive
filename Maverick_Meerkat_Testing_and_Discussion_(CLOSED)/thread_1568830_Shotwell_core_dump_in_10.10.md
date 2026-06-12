---
title: "Shotwell core dump in 10.10"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by locosway on 2010-09-05
I'm not sure if this is because I was trying to use shotwell with photos on a network share, or because of something other.


```
greg@moniker:~$ shotwell
**
ERROR:DirectoryMonitor.vala:509:directory_monitor_real_internal_notify_directory_discovered: assertion failed: (updated)
Aborted (core dumped)
```


Any help would be appreciated!

---

### Post by yorba-jim on 2010-09-10
Hi,

I'm the lead developer of Shotwell at Yorba.  Can you tell me what kind of network share you're using (Windows File Sharing, SFTP, etc.)?  How is your Pictures directory configured?  In Edit -> Preferences, what is your library directory?  Does it point directly to your network share?

Thanks,

-- Jim

---

### Post by locosway on 2010-09-10
I'm using an Iomega NAS. I think perhaps this is related to the gvfsd problems with Maverick right now as I can't browse shares from Nautilus, I have to use Dolphin are mount them manually.

I have my config set to import from:

/home/greg/.gvfs/photos on 192.168.1.140

Edit: Also, how do I go about requesting a feature be added to Shotwell?

---

### Post by yorba-jim on 2010-09-13
Yes, that would be a problem.  We rely on information gleaned from GVFS to identify unique directory paths (to prevent loops due to symbolic links, for example).  If you can't browse in Nautilus, that indicates a larger problem to me.

If you wish to file a bug report, please go to our Trac system at [http://trac.yorba.org](http://trac.yorba.org).  You'll need to register to file a bug or feature request.

-- Jim

---

