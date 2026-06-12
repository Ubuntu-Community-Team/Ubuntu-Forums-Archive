---
title: "64 bit Mythbuntu install reverted to 32 bit?"
date: 2012-11-19
forum: Mythbuntu
---

### Post by alien878 on 2012-11-19
This is odd...  It seems that my 64bit mythbuntu install somehow reverted to a 32 bit install when kernel 3.2.0.25 was installed.  Looking at the apt logs, this happened on June 19th.  I've been running 12.04 since May 5th, so it appears to have happened during a normal SW update.

Any idea how this could have happened?  Can I go back to 64 bit without full re-install?

```
$ dpkg --list | grep linux-image
rc  linux-image-2.6.31-14-generic          2.6.31-14.48                        
               Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-21-generic          2.6.31-21.59                        
               Linux kernel image for version 2.6.31 on x86/x86_64
ii  linux-image-2.6.31-22-generic          2.6.31-22.65                        
               Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.32-25-generic          2.6.32-25.44                        
               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.35-22-generic          2.6.35-22.35                        
               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-32-generic          2.6.35-32.67                        
               Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.38-14-generic          2.6.38-14.58                        
               Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-3.0.0-19-generic           3.0.0-19.33                         
               Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.2.0-24-generic           3.2.0-24.39                         
               Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-25-generic           3.2.0-25.40                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-26-generic           3.2.0-26.41                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic           3.2.0-27.43                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.33.36                         
               Generic Linux kernel image
$ file /usr/bin/file
/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, BuildID[sha1]=0xabca77787115d8fb7fc615cc7f245660248f2625, stripped
$
```

---

### Post by tgm4883 on 2012-11-19
> **alien878 said:**
> This is odd...  It seems that my 64bit mythbuntu install somehow reverted to a 32 bit install when kernel 3.2.0.25 was installed.  Looking at the apt logs, this happened on June 19th.  I've been running 12.04 since May 5th, so it appears to have happened during a normal SW update.

Any idea how this could have happened?  Can I go back to 64 bit without full re-install?

```
$ dpkg --list | grep linux-image
rc  linux-image-2.6.31-14-generic          2.6.31-14.48                        
               Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.31-21-generic          2.6.31-21.59                        
               Linux kernel image for version 2.6.31 on x86/x86_64
ii  linux-image-2.6.31-22-generic          2.6.31-22.65                        
               Linux kernel image for version 2.6.31 on x86/x86_64
rc  linux-image-2.6.32-25-generic          2.6.32-25.44                        
               Linux kernel image for version 2.6.32 on x86/x86_64
rc  linux-image-2.6.35-22-generic          2.6.35-22.35                        
               Linux kernel image for version 2.6.35 on x86/x86_64
rc  linux-image-2.6.35-32-generic          2.6.35-32.67                        
               Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.38-14-generic          2.6.38-14.58                        
               Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-3.0.0-19-generic           3.0.0-19.33                         
               Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.2.0-24-generic           3.2.0-24.39                         
               Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-25-generic           3.2.0-25.40                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-26-generic           3.2.0-26.41                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic           3.2.0-27.43                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic           3.2.0-29.46                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic           3.2.0-31.50                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic           3.2.0-32.51                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic           3.2.0-33.52                         
               Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.33.36                         
               Generic Linux kernel image
$ file /usr/bin/file
/usr/bin/file: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, BuildID[sha1]=0xabca77787115d8fb7fc615cc7f245660248f2625, stripped
$
```

That shouldn't be possible (and even if it was, it should cause far more issues I would think). Please post the output of 

```
uname -a
```

---

### Post by alien878 on 2012-11-19
Yes, I know it shouldn't be possible.  I'm just trying to figure out what happened.

My uname -a:
```
$ uname -a
Linux violet 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012 i686 i686 i386 GNU/Linux
$
```
I dug up my original install disk and the label was "Mythbuntu 9.10 i386".  I'm not sure from the label which version it is.  I was sure I installed 64 bit, but maybe I installed 32 bit?  If so, why do all kernels on my system 3.2.0-24 and earlier show 64 bit?

Everything seems to be working (except for some performance issues the last few weeks), so I'm not panicking.  However, something very strange seems to be going on and I would like to understand it before it does cause problems.

Thanks,

Allen

---

### Post by oldfred on 2012-11-19
Did you perhaps do a "dirty" install or not reformat partition and just over install existing? That would keep old files and install new. I do not know how else that could be done.

---

### Post by alien878 on 2012-11-20
It was a completely new system built from scratch.

What does a uname -a show for 64 bit?  I think I'll try and boot one of those kernels marked 64 bit and check.  Maybe it is just the label is wrong.  It was over 3 years ago I installed it.  Maybe I did chose 32 bit for some reason I have forgotten.

---

### Post by nickrout on 2012-11-21
> **alien878 said:**
> It was a completely new system built from scratch.

What does a uname -a show for 64 bit?  I think I'll try and boot one of those kernels marked 64 bit and check.  Maybe it is just the label is wrong.  It was over 3 years ago I installed it.  Maybe I did chose 32 bit for some reason I have forgotten.```
nick@envy ~ $ uname -a
Linux envy 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```(It's linux mint 13 but has ubuntu 12.04 kernel I think)

---

### Post by alien878 on 2012-11-21
I booted one of the old kernels labelled 64 bit in dpkg and it was a 32 bit image.  It seems the dpkg labels were wrong (or corrupt) and I really have been running 32 bit all along.

A bit of a relief... I was afraid something nasty had happened during one of the updates.

---

