---
title: "[SOLVED] nvidia and x server file error"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Bucky Ball on 2008-08-31
Hi all. I posted about not being able to run foobilliards and no response. I have continued searching though, and am getting somewhere I think.

When I go System->Administration->Nvidia X Server Settings, tells me this ...

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. I open terminal and get this:
```

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```Repeat previous process (System->Administration->Nvidia X Server Settings), and no change. Went to the file itself to see if I could tweak anything but wouldn't have the foggiest as to what to tweak.

The strange thing is, was all fine last time I used foobilliards (about a month ago) and the Nvidia settings (was using that driver). I have included this list of last 50 things removed in case that helps anyone ... 

```
skulker@HPLappy:~$ cat /var/log/dpkg.log | grep ' \(remove\|purge\) '
2008-08-02 02:05:36 remove libakonadiprivate0 0.82.0-0ubuntu2~hardy1~ppa3 0.82.0-0ubuntu2~hardy1~ppa3
2008-08-10 18:28:05 remove rhythmbox 0.11.5-0ubuntu8 0.11.5-0ubuntu8
2008-08-15 01:48:27 remove viewpdf.app 1:0.2dfsg1-3 1:0.2dfsg1-3
2008-08-15 01:48:27 remove gnustep-back0.12 0.12.0-1 0.12.0-1
2008-08-15 01:48:27 remove gnustep-back0.12-art 0.12.0-1 0.12.0-1
2008-08-15 01:48:27 remove gnustep-gpbs 0.12.0-1 0.12.0-1
2008-08-15 01:48:27 remove gnustep-gui-runtime 0.12.0-3ubuntu1 0.12.0-3ubuntu1
2008-08-15 01:48:28 remove libgnustep-gui0.12 0.12.0-3ubuntu1 0.12.0-3ubuntu1
2008-08-15 01:48:28 remove gnustep-base-runtime 1.14.1-2ubuntu1 1.14.1-2ubuntu1
2008-08-15 01:48:28 remove libgnustep-base1.14 1.14.1-2ubuntu1 1.14.1-2ubuntu1
2008-08-15 01:48:28 remove libobjc2 4.2.3-2ubuntu7 4.2.3-2ubuntu7
2008-08-15 01:48:28 remove libpopplerkit0 0.0.20051227svn-5 0.0.20051227svn-5
2008-08-15 01:48:53 remove etw 3.2+svn125-1 3.2+svn125-1
2008-08-15 01:48:54 remove etw-data 3.2+svn125-1 3.2+svn125-1
2008-08-16 19:40:23 remove abuse 1:0.7.0-6 1:0.7.0-6
2008-08-16 19:40:23 remove abuse-frabs 2.10-7ubuntu2 2.10-7ubuntu2
2008-08-17 04:35:00 remove smbfs 3.0.28a-1ubuntu4.4 3.0.28a-1ubuntu4.4
2008-08-17 04:35:44 remove gsambad 0.1.9-2ubuntu1 0.1.9-2ubuntu1
2008-08-17 04:35:44 remove samba 3.0.28a-1ubuntu4.4 3.0.28a-1ubuntu4.4
2008-08-26 18:30:26 remove wine 1.1.0~winehq0~ubuntu~8.04-1 1.1.0~winehq0~ubuntu~8.04-1
2008-08-30 00:00:22 remove fltk1.1-games 1.1.7-6 1.1.7-6
2008-08-30 00:00:26 remove foobillard 3.0a-3ubuntu1 3.0a-3ubuntu1
2008-08-30 00:00:26 remove libfltk1.1 1.1.7-6 1.1.7-6
2008-08-30 00:06:41 remove csmash 0.6.6-6.3ubuntu1 0.6.6-6.3ubuntu1
2008-08-30 00:06:41 remove csmash-data 0.6.6-6.3ubuntu1 0.6.6-6.3ubuntu1
2008-08-30 00:06:41 remove foobillard 3.0a-3ubuntu1 3.0a-3ubuntu1
2008-08-30 21:33:19 remove gnustep-back-common 0.12.0-1 0.12.0-1
2008-08-30 21:33:21 remove gnustep-gui-common 0.12.0-3ubuntu1 0.12.0-3ubuntu1
2008-08-30 21:33:21 remove gnustep-base-common 1.14.1-2ubuntu1 1.14.1-2ubuntu1
2008-08-30 21:33:21 remove gnustep-common 2.0.2-1 2.0.2-1
2008-08-30 21:33:22 remove libffcall1 1.10+2.41-3 1.10+2.41-3
2008-08-30 21:33:22 remove winbind 3.0.28a-1ubuntu4.4 3.0.28a-1ubuntu4.4
2008-08-31 14:50:52 remove foobillard 3.0a-3ubuntu1 3.0a-3ubuntu1
```


Any ideas?

---

### Post by Bucky Ball on 2008-08-31
And here is how I solved it:

I went to System->Administration->Hardware Drivers and found that the Nvidia driver was installed and ticked but not in use. I unticked it then ticked it again, restarted machine and all is well that ends well.

---

