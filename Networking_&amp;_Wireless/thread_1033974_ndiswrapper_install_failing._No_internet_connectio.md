---
title: "ndiswrapper install failing. No internet connection."
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by jrockpunk1 on 2009-01-07
So I've just installed wubi, and ubuntu 8.10. I've had it before and used to know a few commands etc, but please talk to me as if you're speaking to a complete newb. Basically, I have a belkin wireless G adapter: F5D7050. There isn't a linux driver so I'll have to use ndiswrapper. Now, I don't have internet connection (obviously), so I downloaded the tar.gz file to my "Documents" folder, and then of course used the mount command so I can see all my windows folders in ubuntu. I extracted the files, and went to the folder (in ubuntu). Now, I do ./configure, and it said something like "no file or directory", but I figure that isn't a problem as there isn't a configure file. Then I do "make" and "make install" and these are the errors:

```

jay@ubuntu:/mnt/windrive/Users/jay/Documents$ cd ndiswrapper-1.53
jay@ubuntu:/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53$ ./configure
bash: ./configure: No such file or directory
jay@ubuntu:/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.o
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver'
make: *** [all] Error 2
jay@ubuntu:/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53$ make install
make -C driver install
make[1]: Entering directory `/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.o
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function ‘iwe_stream_add_event’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function ‘iwe_stream_add_value’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function ‘iwe_stream_add_point’
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53/driver'
make: *** [install] Error 2
jay@ubuntu:/mnt/windrive/Users/jay/Documents/ndiswrapper-1.53$ 

```

Now, I googled and found that it could be my kernel was out of date, even though I've just installed the latest version. I've tried to install the kernel but it says it's up to date. But of course I have no internet connection so it could be wrong. So is there any way/need of installing the kernel without an internet connection? Maybe by downloading a file to the windows partition and then installing it on the ubuntu one. But of course, it would be a bit of a paradox because it might not install the Kernel because it needs the latest Kernel to do so lol. If it's not the Kernel that's the problem then how can I install ndiswrapper without getting those errors?

Please help, I've done hours (literally) of googling to no avail.

jrockpunk1

---

### Post by DaveyR on 2009-01-07
+1

I would like to know how to do this too. Similar problem. Why is this stuff so easy on windows but a nightmare for linux?

---

### Post by jrockpunk1 on 2009-01-07
yeah I know. I suppose it's freeware, and when you know how to do t properly it will be much better than windows. I suppose a lot of it is driver related, and that's the manufacturer's problem for not making a linux driver...

---

### Post by Ayuthia on 2009-01-07
The source is not able to compile in 2.6.27 without a patch.  Here is a link to a patch with some instructions on how to appy it:
[http://gnuwave.org/drupal/node/36](http://gnuwave.org/drupal/node/36)

Hope that helps.

---

### Post by jrockpunk1 on 2009-01-07
Im sorry, but like I said, can you treat me like a noob please?

What exactly do I do with the code in the link?

---

### Post by jrockpunk1 on 2009-01-07
OK I made a new file "something.patch" (cant remember) in the ndiswrapper folder, then cd's to the folder and ran that command, and it said "the command 'patch' was not found". Please help :S

---

### Post by albinootje on 2009-01-07
> **jrockpunk1 said:**
> OK I made a new file "something.patch" (cant remember) in the ndiswrapper folder, then cd's to the folder and ran that command, and it said "the command 'patch' was not found". Please help :S

You need the package patch which provides the tool called patch.
[http://packages.ubuntu.com/intrepid/patch](http://packages.ubuntu.com/intrepid/patch)

---

### Post by albinootje on 2009-01-07
> **jrockpunk1 said:**
> 
Please help, I've done hours (literally) of googling to no avail.


It probably makes much more sense when you download the following packages :
```

ndiswrapper-common
ndiswrapper-utils-1.9
ndisgtk

```
Find them here : [http://packages.ubuntu.com/](http://packages.ubuntu.com/) 
For example : [http://packages.ubuntu.com/ndisgtk](http://packages.ubuntu.com/ndisgtk)

Copy them into your Wubi 8.10 installation, all in one folder.
Then type, after booting Ubuntu, in that folder where you've put those files :
```

sudo dpkg -i ndis*deb

```
If that installs successfully, go here :
-> System -> Administration -> Windows Wireless Drivers

---

### Post by jrockpunk1 on 2009-01-08
thanks for that, it's worked :D

but now I choose the inf file and it says it's an invalid driver. When I try again it says its installed, but under the driver it says "invalid". I read i might need to update ndiswrapper, but I can't can I?

[edit]
and when I do it through the terminal it says:

couldn't open AUTORUN.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by jrockpunk1 on 2009-01-08
sorry for double post but it seems I was using the wrong inf file lol. I had to go to another directory for vista X86 and then use that inf. But now I get this message:

```

FATAL: Could not open '/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory



```

---

### Post by untappedpilot2 on 2009-01-08
Don't use the vista driver .inf file. Try using the xp one or something. Make sure you download the most up to date driver file from the website. It should come with .inf and .sys files. Make sure they're both in the same folder when you point to it from the ndisgtk GUI.

---

### Post by albinootje on 2009-01-08
> **jrockpunk1 said:**
> sorry for double post but it seems I was using the wrong inf file lol. I had to go to another directory for vista X86 and then use that inf. But now I get this message:

```

FATAL: Could not open '/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory



```
Weird that it is not there. 
That module is part of the "generic" 2.6.27-7 kernel:
> 
$ dpkg -S /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko

linux-image-2.6.27-7-generic: /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko


---

### Post by albinootje on 2009-01-08
> **jrockpunk1 said:**
> 
```

FATAL: Could not open '/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory

```

I'll attach mine here. 
> 
$ md5sum /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
aec8d1cc8bc5acb27edce6f833b56f98  /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko

Unzip it, and put it in /lib/modules/2.6.27-7-generic/kernel/ubuntu/

---

### Post by jrockpunk1 on 2009-01-08
OK well I've done that, and now I get the error:

```

Module could not be loaded. Error was:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko): Invalid module format

```

So do I just have like and outdated kernel or something?

---

### Post by jrockpunk1 on 2009-01-08
OK well I've done that, and now I get the error:

```

Module could not be loaded. Error was:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko): Invalid module format

```

So do I just have like and outdated kernel or something?

---

### Post by jrockpunk1 on 2009-01-08
why does it say that albinootje was the last poster, and this isn't on the first page?

---

### Post by jrockpunk1 on 2009-01-08
sorry for triple post, but bump...

also, this is to get this on the front page (why isn't it going there?!)

[edit]
really sorry for the posts. I tried to delete them but there isn't an option to...

---

### Post by albinootje on 2009-01-08
> **jrockpunk1 said:**
> sorry for triple post, but bump...

also, this is to get this on the front page (why isn't it going there?!)

[edit]
really sorry for the posts. I tried to delete them but there isn't an option to...

Are you using 64 bit ?
```

uname -m

```

Did you leave your machine on ?
If so, run :
```

sudo depmod -a

```
And try again.

---

### Post by jrockpunk1 on 2009-01-08
well uname -m shows "x86_64"

and sudo depmod -a does nothing, and the error still comes up.

There are 4 folders with INF files. They are:

vista 32
vista 64
winXP 64
winXP 2K

So the only one so far that's worked the best is winXP2K which still comes up with the error about the .ko file but after, underneat the driver name says "hardware present: yes". All the others say something like "invalid driver".

So basically, it's a problem with the ndiswrapper.ko file.

---

### Post by albinootje on 2009-01-08
> **jrockpunk1 said:**
> well uname -m shows "x86_64"

and sudo depmod -a does nothing, and the error still comes up.


Ah, okay. I'm on 32-bit here.
If /var/cache/apt/archives/linux-image-2.6.27-7-generic doesn't exist anymore (perhaps you did "sudo apt-get clean")

Can you then do the following :
```

sudo apt-get -d install --reinstall linux-image-2.6.27-7-generic

```

And then :
```

file-roller /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb

```
Double-click on the data tar.bz2 file inside that deb file.
Then double-click on the . (dot).
Then navigate until you find this one :
lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
And extract that, and copy it into the right directory, as before.

---

### Post by jrockpunk1 on 2009-01-08
well the file is isn't there (I did in fact do a clean), but I can't reinstall because I would need to connect to the inernet.

---

### Post by albinootje on 2009-01-08
Sorry, forgot you had no internet connection on that Ubuntu box.

$ md5sum ndiswrapper.ko 
57bbf22203c6e93e773d1e5dfedf0863  ndiswrapper.ko

$ file ndiswrapper.ko 
ndiswrapper.ko: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped

Attached as zip file.

---

### Post by albinootje on 2009-01-08
Uploaded the 64 bit version of that kernel module.

---

### Post by jrockpunk1 on 2009-01-09
OK well the file you PMd me worked and Now I've installed the driver, and there were no errors. However, when I go to the network thing under the wireless tab, there isn't a wlan0 like there should be. When I go on windows wireless drivers and click "configure network" it says "network configuration tool is not installed" or something. Anyway, the point is it doesn't say wlan0, but the driver has installed. What can I do to get this to work?

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
> OK well the file you PMd me worked and Now I've installed the driver, and there were no errors. However, when I go to the network thing under the wireless tab, there isn't a wlan0 like there should be. When I go on windows wireless drivers and click "configure network" it says "network configuration tool is not installed" or something. Anyway, the point is it doesn't say wlan0, but the driver has installed. What can I do to get this to work?

Can you try this :
```

sudo ndiswrapper -ma

```

From here :
[http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html](http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html)

```

Now add following line to the file /etc/modprobe.d/ndiswrapper at the end.

alias wlan0 ndiswrapper

Reboot and enjoy using your wireless lan network.

```

Can you show the output of :
```

iwconfig
iwlist scan

```

---

### Post by jrockpunk1 on 2009-01-09
I'll get right on it :)

[edit]
OK bad news.

I did as you said, and now my ndiswrapper file has this in it:
```

alias usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper

alias wlan0 ndiswrapper

```
I then rebooted

the output of iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

The output of iwlist scan:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

The driver has installed because when I tried to install the INF file again it said "driver already installed".

Please help :S

[edit 2]
OK albinootje please help when you get up lol :P. I might hit the sack as well in a bit.

---

### Post by jrockpunk1 on 2009-01-09
nobody know?

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
> 
alias usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias wlan0 ndiswrapper
[/quote]
Can you post the output of this :
```

lspci
lsusb
lshw -C network

```
And what is the name of the Windows driver file again please ?

---

### Post by jrockpunk1 on 2009-01-09
OK I'll do that. What do you mean the name of the driver file? The file with the INF in?

---

### Post by jrockpunk1 on 2009-01-09
OK, that's it, I'm giving up with bloody ubuntu.

I got it so that there was an option for wireless when I right clicked the icon, so I decided to open mozilla firefox. And what do ya know, it crashed and I had to restart. When I restarted it took me to the logon page, and when I logged on nothing happened, it was just a brown screen. I restarted X windows, and went through the recovery process. And still I can't log on. There is no way I'm reinstalling and going through all this again.

So thanks for helping me, but it looks like I'm saying goodbye to the crappy world of Ubuntu.

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
> OK, that's it, I'm giving up with bloody ubuntu.

I got it so that there was an option for wireless when I right clicked the icon, so I decided to open mozilla firefox. And what do ya know, it crashed and I had to restart. When I restarted it took me to the logon page, and when I logged on nothing happened, it was just a brown screen. I restarted X windows, and went through the recovery process. And still I can't log on. There is no way I'm reinstalling and going through all this again.

So thanks for helping me, but it looks like I'm saying goodbye to the crappy world of Ubuntu.

Sorry to hear this :(

Good luck elsewhere.

---

### Post by jrockpunk1 on 2009-01-09
Well, if anyone can find a solution to my problem without reinstalling, then that would be great, but googling has showed others have just had to reinstall for such problems. So if anyone can think of a fix, then great, if not, I'm sorry but I'm not going to be here any more.

Thanks again VERY much for all your help :)

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
> Well, if anyone can find a solution to my problem without reinstalling, then that would be great, but googling has showed others have just had to reinstall for such problems. So if anyone can think of a fix, then great, if not, I'm sorry but I'm not going to be here any more.

I think you have become a little impatient.
I hope that you do realise that still a lot of hardware vendors (computers and computer-parts including wifi-cards) are not willing to support Linux in any way or maybe just a tiny little bit.

To give you one sad example, some years ago I bought a SMC pci based wifi-card, which worked in Ubuntu 5.x
I was happy about that, and told others. One friend of mine went to a shop and bought the same type SMC wifi card, only to find out later that SMC had changed the chipset on the card itself.. a chipset which was not supported (yet) by Linux then.
Needless to say that the box came with a cdrom with ... only MS-Windows drivers.

The fact that you can load Windows wireless drivers thanks to the Ndiswrapper project is unheard of. Image loading Linux drivers in MS-Windows..

You didn't tell us which chipset you card has (lspci, lshw -C network), and it is still possible that you need to load another Windows driver (.inf).

I would also like to tell you that my own experience with Ndiswrapper is very limited.

> 
Thanks again VERY much for all your help :)

No problem, although I'd rather had this problem solved.

---

### Post by jrockpunk1 on 2009-01-09
Thanks, and I can't do that command now lol. All I know is it's a belkin wireless G USB adapter, and it's part# is F5D7050, version 5000.

Like I said, I think I nearly got it working, but then it crashed. So if anyone knows how I can fix this problem (not logging on) please say, as I would REALLY like to use ubuntu again, but like you said - I don't have the patience to do all this again.

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
> Thanks, and I can't do that command now lol. All I know is it's a belkin wireless G USB adapter, and it's part# is F5D7050, version 5000.

Like I said, I think I nearly got it working, but then it crashed. So if anyone knows how I can fix this problem (not logging on) please say, as I would REALLY like to use ubuntu again, but like you said - I don't have the patience to do all this again.

I think it's a good idea to start a new thread for this new problem, with a proper title.
I tend to read threads depending on their title, and I'm probably not the only one.

---

### Post by jrockpunk1 on 2009-01-09
Yes I have, I think it's a problem with GNOME. So here it is:

[http://ubuntuforums.org/showthread.php?t=1035468](http://ubuntuforums.org/showthread.php?t=1035468)

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
> Yes I have, I think it's a problem with GNOME. So here it is:

[http://ubuntuforums.org/showthread.php?t=1035468](http://ubuntuforums.org/showthread.php?t=1035468)

Good that you fixed it!

Can you now please post the output of the following :
```

lspci
lsusb
lshw -C network

```

That will make it easier to find the chipset of your wifi card, which can make it easier to find the right driver.

---

### Post by jrockpunk1 on 2009-01-09
```

lspci:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
05:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)





lsusb:

Bus 002 Device 002: ID 050d:705e Belkin Components 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0d8c:0201 C-Media Electronics, Inc. CM6501
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




lshw -C network:

  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:f8:bd:df:6f:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

Something tells me this isn't good :S

All that I know is that the driver has installed and in windows wireless drivers it says "hardware present: yes".

Thanks again for helping so much, and I'm sorry I snapped before.

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
> 
lsusb:
Bus 002 Device 002: ID 050d:705e Belkin Components 


Thanks!

Interesting, glance this through a little bit later on please :
[http://ubuntuforums.org/showthread.php?t=665847](http://ubuntuforums.org/showthread.php?t=665847)
[http://forums.fedoraforum.org/showthread.php?t=208470](http://forums.fedoraforum.org/showthread.php?t=208470)
[http://wiki.debian.org/rtl818x](http://wiki.debian.org/rtl818x)

We'll continue tomorrow.

---

### Post by jrockpunk1 on 2009-01-10
yeah well that first one and the link to the driver is actually what I looked at before trying ndiswrapper, but the instructions aren't very noob friendly, so I don't know how to install it.

---

### Post by albinootje on 2009-01-10
> **jrockpunk1 said:**
> yeah well that first one and the link to the driver is actually what I looked at before trying ndiswrapper, but the instructions aren't very noob friendly, so I don't know how to install it.

Agreed.
Can you post the output of this, please :
```

modprobe -l | grep rtl

```

---

