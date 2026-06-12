---
title: "Video Driver won't compile"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by BDwinsAlt on 2007-03-10
I have an Intel 82865G Graphics Controller.  I am trying to compile these drivers.  When I do I get the errors.  Please help me fix these errors.

Link to driver download: [http://downloadfinder.intel.com/scripts-df-external/T8Clearance.aspx?url=/8203/eng/i915Graphics.tar.gz&agr=Y&ProductID=1044&DwnldID=8203&lang=eng](http://downloadfinder.intel.com/scripts-df-external/T8Clearance.aspx?url=/8203/eng/i915Graphics.tar.gz&agr=Y&ProductID=1044&DwnldID=8203&lang=eng)

Errors:
```

The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```

----------------------------------------------------------------------------------------------------------
dri.log:

```

make -C /lib/modules/2.6.19-custom/build SUBDIRS=/home/brad/Desktop/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-2.6.19'
  CC [M]  /home/brad/Desktop/dripkg/agpgart-2.0/backend.o
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:105: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:106: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:220: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;drm_agp&#8217;
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_add_bridge&#8217;:
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:281: warning: implicit declaration of function &#8216;inter_module_register&#8217;
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:281: error: &#8216;drm_agp&#8217; undeclared (first use in this function)
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_remove_bridge&#8217;:
/home/brad/Desktop/dripkg/agpgart-2.0/backend.c:301: warning: implicit declaration of function &#8216;inter_module_unregister&#8217;
make[2]: *** [/home/brad/Desktop/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/brad/Desktop/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.19'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/brad/Desktop/dripkg/drm'
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.19-custom/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-2.6.19'
rm: cannot remove `/home/brad/Desktop/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-2.6.19'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/brad/Desktop/dripkg/drm'
make: *** [gdg.ko] Error 2


I chmod the files to try and fix it that way as well.  I am running as root.  What's going on?

Please help,
Brad

```

Edit:  I could only find support for Windows drivers.

---

### Post by BDwinsAlt on 2007-03-10
I tried doing it outside of Xorg liek one forum said, I renamed all .o to .ko in drm/Makefile.linux... nada.

Please help :(

---

### Post by TrueJk7 on 2007-03-17
Bump.

Sorry to be a bother bumping an old post but I found no resolution myself either with the same kinda problem installing an intel driver. below I will also post my terminal message and the error

```
The script will now compile the agpgart module and DRM kernel modules
for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

root@D610:/home/jake/Ubuntu/dripkg# 

```

dri.log
```
make -C /lib/modules/2.6.17-11-386/build SUBDIRS=/home/jake/Ubuntu/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-386'
  CC [M]  /home/jake/Ubuntu/dripkg/agpgart-2.0/backend.o
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:281: warning: ‘inter_module_register’ is deprecated (declared at include/linux/module.h:562)
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.c:301: warning: ‘inter_module_unregister’ is deprecated (declared at include/linux/module.h:563)
make[2]: *** [/home/jake/Ubuntu/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/jake/Ubuntu/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-386'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/jake/Ubuntu/dripkg/drm'
make -C /lib/modules/2.6.17-11-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-386'
rm: cannot remove `/home/jake/Ubuntu/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-386'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/jake/Ubuntu/dripkg/drm'
make: *** [gdg.ko] Error 2

```

---

