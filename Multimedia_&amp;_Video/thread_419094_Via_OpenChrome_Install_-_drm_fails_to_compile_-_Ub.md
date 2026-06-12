---
title: "Via OpenChrome Install - drm fails to compile - Ubuntu 7.04 Fiesty Fawn"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by MayOne.Net on 2007-04-22
I've successfully compiled the OpenChrome driver under 7.04 for my Gateway MX3210 laptop with a VIA VN800 video card using a combination of the debian guide located here (gives a good list of things to install before you can compile):
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Debian](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Debian)

and the Ubutunu OpenChrome Docs located here:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

While this allowed me to increase the resolution, and appears to be working for 2d, when I run "glxinfo | grep render" I get the following error:

X Error of failed request: GLXBadContext
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 5 (X_GLXMakeCurrent)
Serial number of failed request: 19
Current serial number in output stream: 19

So, I attempted to install the custom libdrm and drm kernal modules.  Using the process in the Ubuntu docs libdrm compiled and installed without problem.  However, no luck with DRM. When I tried to make using

"sudo make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via" 

I get the following error

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
CC [M] /home/shad/stuff/drm/linux-core/drm_compat.o
/home/shad/stuff/drm/linux-core/drm_compat.c:190: error: static declaration of ‘vm_insert_pfn’ follows non-static declaration
include/linux/mm.h:1126: error: previous declaration of ‘vm_insert_pfn’ was here
make[2]: *** [/home/shad/stuff/drm/linux-core/drm_compat.o] Error 1
make[1]: *** [_module_/home/shad/stuff/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

While I can live with 2d only, I would prefer 3d. Also if I have to live with 2d, how do I uninstall the libdrm, as it appears to be slowing down my boot & shutdown times.

FYI - was unable to use automake-1.9 as I could only apt-get 1.10. Would this be part of the problem? If so, how do I get 1.9?

Thanks for any help.

---

### Post by hawk684 on 2007-04-25
Same problem here, I'm assuming it's a change in the kernel based on the include.  If I figure anything out I'll report back.

---

### Post by sdavies9574 on 2007-04-27
This is what I did.  It appears to have worked, I get a positive response when I run glxinfo.

Find drm_compat.c in tmp/openchrome/drm/linux-core

```
gedit drm_compat.c
```

Find this (line 188 on mine):

```
static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)
{
	int ret;
	if (!drm_pte_is_clear(vma, addr))
		return -EBUSY;

	ret = io_remap_pfn_range(vma, addr, pfn, PAGE_SIZE, vma->vm_page_prot);
	return ret;
}
```

Change it to this (you are just commenting it out):

```
/*
static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)
{
	int ret;
	if (!drm_pte_is_clear(vma, addr))
		return -EBUSY;

	ret = io_remap_pfn_range(vma, addr, pfn, PAGE_SIZE, vma->vm_page_prot);
	return ret;
}
*/
```

then continue with the instructions as per normal:
```

make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via

sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
```

etc...

---

### Post by hawk684 on 2007-04-29
That worked for me, doesn't seem to be causing any problems.

---

### Post by jimboriach on 2007-04-29
> **MayOne.Net said:**
> I've successfully compiled the OpenChrome driver under 7.04 for my Gateway MX3210 laptop with a VIA VN800 video card using a combination of the debian guide located here (gives a good list of things to install before you can compile):
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Debian](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Debian)

and the Ubutunu OpenChrome Docs located here:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

While this allowed me to increase the resolution, and appears to be working for 2d, when I run "glxinfo | grep render" I get the following error:

X Error of failed request: GLXBadContext
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 5 (X_GLXMakeCurrent)
Serial number of failed request: 19
Current serial number in output stream: 19

So, I attempted to install the custom libdrm and drm kernal modules.  Using the process in the Ubuntu docs libdrm compiled and installed without problem.  However, no luck with DRM. When I tried to make using

"sudo make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via" 

I get the following error

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
CC [M] /home/shad/stuff/drm/linux-core/drm_compat.o
/home/shad/stuff/drm/linux-core/drm_compat.c:190: error: static declaration of ‘vm_insert_pfn’ follows non-static declaration
include/linux/mm.h:1126: error: previous declaration of ‘vm_insert_pfn’ was here
make[2]: *** [/home/shad/stuff/drm/linux-core/drm_compat.o] Error 1
make[1]: *** [_module_/home/shad/stuff/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

While I can live with 2d only, I would prefer 3d. Also if I have to live with 2d, how do I uninstall the libdrm, as it appears to be slowing down my boot & shutdown times.

FYI - was unable to use automake-1.9 as I could only apt-get 1.10. Would this be part of the problem? If so, how do I get 1.9?

Thanks for any help.
I did much the same , I deleted the definition"static" which make complained about then everything went ok

---

### Post by kenshin159 on 2007-05-03
Hello all I too have installed Ubuntu Feisty on my Gateway MX3230. When I ran 

```
sudo apt-get build-dep xserver-xorg-video-via
```
 then
```
sudo apt-get install subversion autoconf automake1.9 
```

#

Change into the newly created directory

```
cd openchrome*
```

#

Run autogen.sh with the prefix option so that the driver is being installed in the correct directory

```
./autogen.sh --prefix=/usr
```

#

Compile openChrome

```
make
``` 

**When I run make I get **
```
make: *** No targets specified and no makefile found.  Stop. 
```

#

Install openChrome

```
sudo make install
```
 and I get the same message for this line of command.


Am I doing something wrong? I also want to get 3d to work so that I can run  Beryl on my laptop.


I also cannot > Find drm_compat.c in tmp/openchrome/drm/linux-core there is no openchrome folder in /tmp. Thanks in advance!

---

### Post by MadOrL on 2007-05-05
Hi

I got these message on these commands

> madorl@madorl-desktop:~$ glxgears
0000:   f0000001  00000300  f0000006  00000000
0010:   f000000b  00000000  f000000c  00181f60
0020:   f000000d  00181f60  f000000e  809c009c
0030:   f0000002  00000005  f0000003  00000005
0040:   f0000004  012b012b  f0000000  f0002001
0050:   f000000b  00000000  f0000001  00000300
0060:   f0000006  ffffff00  f000000b  10000000
0070:   f000000c  0018d630  f000000d  0018d630
0080:   f000000e  809c009c  f0000002  00000005
0090:   f0000003  00000005  f0000004  012b012b
00a0:   f0000000  f0002001  f000000b  00000000
00b0:   f210f110  00010000  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
Cancelado (core dumped)
madorl@madorl-desktop:~$ glxinfo | grep render
0000:   f0000001  00000300  f0000006  00000001
0010:   f000000b  00000000  f000000c  00180200
0020:   f000000d  00180200  f000000e  80200020
0030:   f0000002  00000000  f0000003  00000000
0040:   f0000004  00000000  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710


How can i fix this?
When i run wine applications the X crash too..

---

### Post by iclinux on 2007-05-08
hi,all, when compiling drm, I get the follow error, any suggetions? thanks:)

```
iclinux@iclinux:~/Desktop/drm/linux-core$ make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
make -C /lib/modules/2.6.20-15-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/iclinux/Desktop/drm/linux-core/drm_stub.o
/home/iclinux/Desktop/drm/linux-core/drm_stub.c:51: error: size of array &#8216;type name&#8217; is negative
make[2]: *** [/home/iclinux/Desktop/drm/linux-core/drm_stub.o] Error 1
make[1]: *** [_module_/home/iclinux/Desktop/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
iclinux@iclinux:~/Desktop/drm/linux-core$
```

---

### Post by rzimek on 2007-05-09
Hello everyone. I've got the same problem as MadOrL - is there a solution to this problem?

glxinfo | grep render

direct rendering: Yes
0000:   f0000001  00000300  f0000006  00000001
0010:   f000000b  00000000  f000000c  00180200
0020:   f000000d  00180200  f000000e  80200020
0030:   f0000002  00000000  f0000003  00000000
0040:   f0000004  00000000  f0000000  f0002001
0050:   f000000b  00000000  f210f110  00010000
0060:   cccccccc  cccccccc  cccccccc  cccccccc
0070:   cccccccc  cccccccc  cccccccc  cccccccc
******************************************
fire_buffer: DRM_VIA_PCICMD returned -22
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX+/3DNow!+/SSE2

and then when I type

sudo echo "drm" >>/etc/modules 
bash: /etc/modules: Permission denied

:(

---

### Post by MadOrL on 2007-05-10
rzimek

I give up to try when i read this msg, I found in google

[http://wiki.openchrome.org/pipermail/openchrome-users/2007-January/002706.html](http://wiki.openchrome.org/pipermail/openchrome-users/2007-January/002706.html)

"You haven't done anything wrong at all.  We have not implemented support
for this chipset in Mesa yet.  As soon as we get spec sheets from VIA we
will tackle this."

I hope they tell us when ok

---

### Post by linunix on 2007-05-11
My video card is via/s3g unichrome, too.
I followed [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) to do.
When I finished the work to fix 2D, I find that when 'glxears' was enter, fps can reach 700. And when 'glxinfo | grep render' was enter, it layout:
direct rendering: Yes
OpenGL renderer string: Mesa DRI UniChrome 20060710 x86/MMX/SSE2
It means the video card work well.
But when I  was doing the work to fix 3D. It layout the same errors as yours.
And when I reboot computer, it failed to boot.
I reinstall ubuntu. This time I just do the 2D's work.
And I think it work well. 
I don't know if I need to fix 3D.

---

### Post by pac-man on 2007-06-18
Well my output after i try to compile the kernel modules is this:

[I]make -C /lib/modules/2.6.20-16-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make: *** /lib/modules/2.6.20-16-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2[/I]

Then I try to go to the  /lib/modules/2.6.20-16-386/ and type "ls -a" and yes, the "build" file or directory doesn't exist!

So, what can I do?

---

### Post by rivera151 on 2007-06-23
> **sdavies9574 said:**
> This is what I did.  It appears to have worked, I get a positive response when I run glxinfo.

Find drm_compat.c in tmp/openchrome/drm/linux-core

```
gedit drm_compat.c
```

Find this (line 188 on mine):

```
static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)
{
	int ret;
	if (!drm_pte_is_clear(vma, addr))
		return -EBUSY;

	ret = io_remap_pfn_range(vma, addr, pfn, PAGE_SIZE, vma->vm_page_prot);
	return ret;
}
```

Change it to this (you are just commenting it out):

```
/*
static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)
{
	int ret;
	if (!drm_pte_is_clear(vma, addr))
		return -EBUSY;

	ret = io_remap_pfn_range(vma, addr, pfn, PAGE_SIZE, vma->vm_page_prot);
	return ret;
}
*/
```

then continue with the instructions as per normal:
```

make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via

sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/
```

etc...

I'm going to suggest a possibly safer solution.  The two lines

```

/home/shad/stuff/drm/linux-core/drm_compat.c:190: error: static declaration of &#8216;vm_insert_pfn&#8217; follows non-static declaration
include/linux/mm.h:1126: error: previous declaration of &#8216;vm_insert_pfn&#8217; was here

```

tell you that you either have to change the declaration in the header file to non-static (a bad idea, since the file is in your include/linux directory) or change the definition of vm_insert_pft (within drm/linux-core/drm_compat.c) from

```

static int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)

```

to

```

int vm_insert_pfn(struct vm_area_struct *vma, unsigned long addr,
		  unsigned long pfn)

```

That saves you the trouble that, if down the road somebody calls the function, yor driver will not fail b/c of undefined procedure.  Cheers!

---

### Post by Seisen on 2007-07-12
> **pac-man said:**
> Well my output after i try to compile the kernel modules is this:

[I]make -C /lib/modules/2.6.20-16-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make: *** /lib/modules/2.6.20-16-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2[/I]

Then I try to go to the  /lib/modules/2.6.20-16-386/ and type "ls -a" and yes, the "build" file or directory doesn't exist!

So, what can I do?

Install the generic kernel and them try it. I had the same problem.

---

### Post by joolean on 2007-10-07
I tried to install the via chrome9 hc igp driver using [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) tutorial. it works fine on 2D. but when I followed the 3D tutorial (I deleted the "static" word on function vm_insert_pfn at file drm_compat.c )

it all went fine until I ran "glxinfo |grep render" the error output was:

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  19
  Current serial number in output stream:  19


anybody experienced the same problem? thanks before...

---

### Post by menotu3169 on 2008-02-14
I know this is kind of an old thread, but hopefully i can still get some help :)

I'm following [this]("https://help.ubuntu.com/community/OpenChrome") thread, trying to get 3D working on my system, and when i try to do this```
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
```

i get an error that says```

cmp: invalid option -- r
cmp: Try 'cmp --help' for more information.
make -C /lib/modules/uname -r/build SUBDIRS='pwd' DRMSRCDIR='pwd' modules
make: invalid option -- /
make: invalid option --u

```

then it lists the usage of the make command and then displays
Make: *** [modules] Error 2

Can anyone help me sort this out?
I'm still not that experienced with Ubuntu, or Linux for that matter, so you may need to explain things a little more thoroughly :(

EDIT:
I edited the drm_compat.c file in the ways suggested in this thread, but it didn't help. I even tried editing the file and restarting my system, but it was still a no-go.

---

### Post by Marcinnn on 2008-04-20
> **menotu3169 said:**
> I know this is kind of an old thread, but hopefully i can still get some help :)

I'm following [this]("https://help.ubuntu.com/community/OpenChrome") thread, trying to get 3D working on my system, and when i try to do this```
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
```

i get an error that says```

cmp: invalid option -- r
cmp: Try 'cmp --help' for more information.
make -C /lib/modules/uname -r/build SUBDIRS='pwd' DRMSRCDIR='pwd' modules
make: invalid option -- /
make: invalid option --u

```

then it lists the usage of the make command and then displays
Make: *** [modules] Error 2

Can anyone help me sort this out?
I'm still not that experienced with Ubuntu, or Linux for that matter, so you may need to explain things a little more thoroughly :(

EDIT:
I edited the drm_compat.c file in the ways suggested in this thread, but it didn't help. I even tried editing the file and restarting my system, but it was still a no-go.


Hej! Giving word "sudo" in front of line (befor make) and remebering that between "LINUXDIR" and "via" r words, slashes etc but no empty spaces - " " - doesn't resolve ur problem? ;-)

---

### Post by Aleksandar_M on 2008-04-23
Plz help...

I edit the file and that pass.. but now I get this message 

```
aleks@ubuntu:~/drm/linux-core$ sudo make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via
make -C /lib/modules/2.6.20-15-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/aleks/drm/linux-core/drm_compat.o
/home/aleks/drm/linux-core/drm_compat.c: In function ‘drm_bo_vm_fault’:
/home/aleks/drm/linux-core/drm_compat.c:220: error: too few arguments to function ‘drm_bo_wait’
make[2]: *** [/home/aleks/drm/linux-core/drm_compat.o] Error 1
make[1]: *** [_module_/home/aleks/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

```

Anybody know?

---

### Post by Marcinnn on 2008-04-24
I don't know what ubuntu does with kernel source code but what i read in makefile is that after "LINUXDIR=/" u should give a path to ur kernel sorce code path. But maybe i can't understand it well. I also read there that 3D on viachrome 9 just doesn't work.

---

