---
title: "Dell Conexant HSF Modem with Intrepid Ibex?"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by warchief_ryan on 2008-12-19
Dell has the drivers for the Conexant HSF Modem for Hardy but not Intrepid yet.  Does anyone know if you can use the Hardy version drivers on Intrepid?

I tried compiling "hsfmodem-7.68.00.09oem", the make install goes fine but hsfconfig ends with "ERROR: Module Build Failed!".


The build log ends with,

/usr/lib/hsfmodem/modules/osservices.c:182: error: field 'semaphore' has incomplete type
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockCreate':
/usr/lib/hsfmodem/modules/osservices.c:194: error: implicit declaration of function 'sema_init'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockLock':
/usr/lib/hsfmodem/modules/osservices.c:221: error: implicit declaration of function 'down_trylock'
/usr/lib/hsfmodem/modules/osservices.c:230: error: implicit declaration of function 'down'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockUnlock':
/usr/lib/hsfmodem/modules/osservices.c:252: error: implicit declaration of function 'up'
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsThreadStop':
/usr/lib/hsfmodem/modules/osservices.c:626: error: implicit declaration of function 'kill_proc'
make[2]: *** [/usr/lib/hsfmodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2

---

### Post by sutupud on 2008-12-20
i had luck with that:

- download the newest driver from linuxant (source version!)
[http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)

- download [http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/hsfmodem-7.60.00.18oem.tar.gz](http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/hsfmodem-7.60.00.18oem.tar.gz)

- unpack both

- replace the /modules/imported directory in the linuxant-version with that from dell

- sudo make install
- sudo hsfconfig

---

### Post by W.Sorting on 2008-12-23
Could you please elaborate on how to get this working?

Thanks!

---

### Post by chiron80 on 2008-12-27
> **sutupud said:**
> i had luck with that:

- download the newest driver from linuxant (source version!)
[http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)

- download [http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/hsfmodem-7.60.00.18oem.tar.gz](http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/hsfmodem-7.60.00.18oem.tar.gz)

- unpack both

- replace the /modules/imported directory in the linuxant-version with that from dell

- sudo make install
- sudo hsfconfig

sutupud,

Can you elaborate? I was able to get both versions (Dell version 7.68 and Linuxant version 7.80), and unpack them both (using the built in Archive Manager), and I see that the "modules/imported" directory is missing from the Linuxant version (at least in my case). However, I think you are missing a few integral steps between your "replace" and your "sudo make install".

In my case, I was using "hsfconfig" to build the kernel module. I installed the Linuxant version and then copied the missing "modules/imported" files from the Dell version directly in to my file system. I then tried running hsfconfig and received the same error message.

```
/usr/lib/hsfmodem/modules/osservices.c:182: error: field 'semaphore' has incomplete type
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockCreate':
/usr/lib/hsfmodem/modules/osservices.c:194: error: implicit declaration of function 'sema_init'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockLock':
/usr/lib/hsfmodem/modules/osservices.c:221: error: implicit declaration of function 'down_trylock'
/usr/lib/hsfmodem/modules/osservices.c:230: error: implicit declaration of function 'down'
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsLockUnlock':
/usr/lib/hsfmodem/modules/osservices.c:252: error: implicit declaration of function 'up'
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsThreadStop':
/usr/lib/hsfmodem/modules/osservices.c:626: error: implicit declaration of function 'kill_proc'
make[2]: *** [/usr/lib/hsfmodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
```


- Ben

---

### Post by 6tangos on 2008-12-27
This might help.

At boot, my Dell Inspiron 6400 was throwing an error when it tried to compile the HSF modem driver. I fixed this by un-installing the old driver, then downloading the new driver which corresponds to my current kernel version.

Here's what I did:

Opened Synaptic - hit "Alt+F2" the type "gksu synaptic"
Searched for HSF modem.
Marked for removal & Apply

Then, visit [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php]("http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php")
Following the instructions on that page I determined my kernel version and downloaded the corresponding HSF driver.
Once this was downloaded I installed it, the new driver compiles with no errors.

Good luck.

---

### Post by warchief_ryan on 2009-01-03
Oops I forgot about this thread, to many projects I guess...

sutupud your method worked great, thanks!

---

### Post by xbesnard on 2009-01-11
Hello and happy new year.

I have an dial up modem with a conexant chipset. For all UBUNTU version, it is really a problem to find a driver. The previous solutions (Dell or others) dont work. The Linuxant driver (free version at 14 kb) works, once install from source or from .deb.

I tried this solution posted in the forum ([http://ubuntuforums.org/showthread.php?t=1015673&highlight=conexant+intrepid](http://ubuntuforums.org/showthread.php?t=1015673&highlight=conexant+intrepid)) but I got compilation errors. 

May be, I miss something in my conf. Below the log of the install for some help.

Thanks a lot. Xavier.


*-------------------------------
root@Pluton:~/Modem/hsfmodem-7.80.02.01full# cat /tmp/hsfconfig-buildlog.txt
(cd /lib/modules/2.6.27-9-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.27-9-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
(cd /lib/modules/2.6.27-9-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.27-9-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.27-9-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.27-9-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.27-9-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
  CC [M]  /usr/lib/hsfmodem/modules/osresour.o
/usr/lib/hsfmodem/modules/osresour.c: In function 'cnxthsf_OsHookInterrupt':
/usr/lib/hsfmodem/modules/osresour.c:131: warning: the address of '__this_module' will always evaluate as 'true'
  CC [M]  /usr/lib/hsfmodem/modules/osstring.o
  CC [M]  /usr/lib/hsfmodem/modules/osmemory.o
  CC [M]  /usr/lib/hsfmodem/modules/osdiag.o
  CC [M]  /usr/lib/hsfmodem/modules/osusb.o
  CC [M]  /usr/lib/hsfmodem/modules/osfloat.o
  CC [M]  /usr/lib/hsfmodem/modules/osdcp.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_pcibasic2.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_pcibasic3.o
In file included from /usr/lib/hsfmodem/modules/mod_pcibasic3.c:29:
/usr/lib/hsfmodem/modules/cnxthwpci_common.c: In function 'cnxthwpci_probe':
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:80: error: 'HW_TYPE_BASIC3' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:80: error: (Each undeclared identifier is reported only once
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:80: error: for each function it appears in.)
make[2]: *** [/usr/lib/hsfmodem/modules/mod_pcibasic3.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2

---

### Post by dafrasaga on 2009-01-12
> **warchief_ryan said:**
> Oops I forgot about this thread, to many projects I guess...

sutupud your method worked great, thanks!


Excuse me to All,
I'm a newbie about Linux but what I can understand is I must pick up all what is under */modules directories of linuxant-version and copy it into */modules directories of Dell-version. OK??

Thanks in advance

---

### Post by Rm Riberra on 2009-01-12
> **warchief_ryan said:**
> Oops I forgot about this thread, to many projects I guess...

sutupud your method worked great, thanks!
I tried it but was not able to replace the /modules/imported directory in the linuxant-version with that from dell...
What is the command line you use?

---

### Post by dafrasaga on 2009-01-12
> **Rm Riberra said:**
> I tried it but was not able to replace the /modules/imported directory in the linuxant-version with that from dell...
What is the command line you use?

Hi Riberra,
I used nautilus after removed modules directory from the linuxant-version, but it didn't work:confused:

I'm trying now to resolve the problem but I don't know....

---

### Post by Rm Riberra on 2009-01-20
> **dafrasaga said:**
> Hi Riberra,
I used nautilus after removed modules directory from the linuxant-version, but it didn't work:confused:

I'm trying now to resolve the problem but I don't know....
Hi dafrasaga,
Well,I think we will have to wait for the Dell newest driver...;)That is really frustrating using the free 14,4 kb linuxant Hsf driver.By chance I have tried Intrepid with Wubi rather than a conventional install.

---

### Post by warchief_ryan on 2009-01-31
I didn't think it was that hard to understand what he said, but here it is command by command, you will have to change some things such as the user name and version of the Linuxant driver you use, 

*NOTE* make sure you grab the "full" drivers from the Linuxant driver download pages.

Unpack the driver tars with,
```
tar -xvf /home/ryan/hsfmodem-7.68.00.09oem.tar.gz
```

and again for the Linuxant driver(hsfmodem-7.80.02.02full.tar.gz in my case),
```
tar -xvf /home/ryan/hsfmodem-7.80.02.02full.tar.gz
``` 

Then remove the modules/imported directory from Linuxant driver,
```
rm -R /home/ryan/hsfmodem-7.80.02.02full/modules/imported
```

Then copy over the modules/imported directory from Dell,
```
cp -R /home/ryan/hsfmodem-7.68.00.09oem/modules/imported /home/ryan/hsfmodem-7.80.02.02full/modules/imported
```

Then change working directory to the Linuxant driver folder,
```
cd /home/ryan/hsfmodem-7.80.02.02full
```

Then install like normal,
```
sudo make install
```
```
sudo hsfconfig
```


Hope that helps, sorry if its to late

---

### Post by Ralph L on 2009-02-01
Under [http://linux.dell.com/files/ubuntu/](http://linux.dell.com/files/ubuntu/) there is a 1.8G file called intrepid that has a very recent date on it.  Is this for installing the hsfmodem under Intrepid or do I stll have to do what is described above?  Did Dell update their install for Intrepid?

Thanks
Ralph

---

### Post by warchief_ryan on 2009-02-01
The process I went through isn't a big deal, its just replacing a folder.

Id rather download two 1.5mb files instead of a 1.8gb image just to get a modem working.

---

### Post by Ralph L on 2009-02-01
I am lost.  I am running Intrepid and want to be able to use my Dell Latitude D610 laptop modem to send and receive faxes.  Although I have a high speed internet connection, I would still like to have the capability for dial up access if I ever need it.  I installed hsfmodem-7.68.00.09 in accordance with your instructions above.  I also installed efax-gtk.  When I try to send a fax, I get the  error messages listed below.  My guess is that I haven't installed or intitialized something correctly, but I don't know what.  Moreover, I am used to having a Gui that I can bring up and use to dial a number--then fax or connect to the internet.  Is there anything like this in Ubuntu or is handled very differently.  I am still a newbie.

Ralph


Socket running on port 9900
efax-0.9a: 23:13:08 Warning: local ID (760-375-3866) has non-standard characters
efax-0.9a: 23:13:08 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:08 opened /dev/ttyS1
efax-0.9a: 23:13:08 failed page /home/ralph/Documents/Iraq Oil/Print to file test.ps.001
efax-0.9a: 23:13:08 Error: fax device write: Input/output error
efax-0.9a: 23:13:10 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:12 Error: fax device write: Input/output error
efax-0.9a: 23:13:14 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:14 sync: dropping DTR
efax-0.9a: 23:13:14 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:14 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:16 Error: fax device write: Input/output error
efax-0.9a: 23:13:18 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:18 Error: fax device write: Input/output error
efax-0.9a: 23:13:18 Error: fax device write: Input/output error
efax-0.9a: 23:13:18 sync: sending escapes
efax-0.9a: 23:13:18 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:18 Error: fax device write: Input/output error
efax-0.9a: 23:13:18 Error: fax device write: Input/output error
efax-0.9a: 23:13:20 Error: fax device write: Input/output error
efax-0.9a: 23:13:22 Error: fax device write: Input/output error
efax-0.9a: 23:13:24 Error: sync: modem not responding
efax-0.9a: 23:13:24 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 23:13:24 finished - unrecoverable error

---

### Post by Rm Riberra on 2009-02-05
> **warchief_ryan said:**
> I didn't think it was that hard to understand what he said, but here it is command by command, you will have to change some things such as the user name and version of the Linuxant driver you use, 

*NOTE* make sure you grab the "full" drivers from the Linuxant driver download pages.

.............

Hope that helps, sorry if its to late

warchief_ryan your detailed explanation solve my problem,
thanks!

---

### Post by W.Sorting on 2009-02-10
I tried the updated instructions quite a few times, but the process still failed when I used hsfconfig. I have a conexant hsf softmodem from U.S. Robotics.

Here's the buildlog:
```
(cd /lib/modules/2.6.27-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.27-7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
(cd /lib/modules/2.6.27-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.27-7-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.27-7-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.27-7-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.27-7-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
  CC [M]  /usr/lib/hsfmodem/modules/osresour.o
/usr/lib/hsfmodem/modules/osresour.c: In function 'cnxthsf_OsHookInterrupt':
/usr/lib/hsfmodem/modules/osresour.c:131: warning: the address of '__this_module' will always evaluate as 'true'
  CC [M]  /usr/lib/hsfmodem/modules/osstring.o
  CC [M]  /usr/lib/hsfmodem/modules/osmemory.o
  CC [M]  /usr/lib/hsfmodem/modules/osdiag.o
  CC [M]  /usr/lib/hsfmodem/modules/osusb.o
  CC [M]  /usr/lib/hsfmodem/modules/osfloat.o
  CC [M]  /usr/lib/hsfmodem/modules/osdcp.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_pcibasic2.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_pcibasic3.o
In file included from /usr/lib/hsfmodem/modules/mod_pcibasic3.c:29:
/usr/lib/hsfmodem/modules/cnxthwpci_common.c: In function 'cnxthwpci_probe':
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:80: error: 'HW_TYPE_BASIC3' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:80: error: (Each undeclared identifier is reported only once
/usr/lib/hsfmodem/modules/cnxthwpci_common.c:80: error: for each function it appears in.)
make[2]: *** [/usr/lib/hsfmodem/modules/mod_pcibasic3.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2
```

I'm getting desperate! Anyone have any suggestions?

Thanks in advance for your time.
W.Sorting

---

### Post by pbartel on 2009-02-12
> **warchief_ryan said:**
> I didn't think it was that hard to understand what he said, but here it is command by command, you will have to change some things such as the user name and version of the Linuxant driver you use, ...


That did the trick for me. Thanks!

---

### Post by spidermc on 2009-02-21
Thanks to warchief_ryan!
I have an HP dv9428 and this method worked well on Interpid Ibex (8.10 amd_64)! 
WoW!

---

### Post by sile16 on 2009-03-05
Worked for me! Thanks!

Intrepid X86_64
Dell D620

---

### Post by mikedash on 2009-03-07
> **sutupud said:**
> i had luck with that:

- download the newest driver from linuxant (source version!)
[http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)

- download [http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/hsfmodem-7.60.00.18oem.tar.gz](http://linux.dell.com/files/ubuntu/gutsy/modem-drivers/hsf/hsfmodem-7.60.00.18oem.tar.gz)

- unpack both

- replace the /modules/imported directory in the linuxant-version with that from dell

- sudo make install
- sudo hsfconfig

YOU ARE A GENIUS SUTUPUD!!!
This worked perfectly!  After 2 days of installing and uninstalling various hsfmodem packages I have a working FAX modem!:D:D

---

### Post by hogat on 2009-03-16
thanks

---

### Post by snakdoc on 2009-04-05
no reason anyone should have to pay for drivers in linux espically when you bought the hardware thanks and hope this works :D

---

### Post by snakdoc on 2009-04-05
sudo hsfconfig gives this 

No pre-built modules for: Ubuntu-8.10 linux-2.6.27-11-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.27-11-generic/build] 

Building modules for kernel 2.6.27-11-generic, using source directory
/lib/modules/2.6.27-11-generic/build. Please wait...

ERROR: Module build failed!

in error log 

driver version 7.80.02.03x86_64full
grep: /lib/modules/2.6.27-11-generic/build/include/linux/device.h: No such file$
(cd /lib/modules/2.6.27-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2$
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: [clean] Error 2 (ignored)
(cd /lib/modules/2.6.27-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2$
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: [clean] Error 2 (ignored)
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_ver$
(cd /lib/modules/2.6.27-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2$
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.


any ideas ?

---

### Post by ishti on 2009-04-10
I successfully installed the driver. It works, many thanks. *But* I have now a problem with sound : seems that the driver overwrite some alsa (for intel HDA) modules and then I have lost in gnome-mixer applet the master control.

@ snakdoc :
You're trying to compile the 64bit version of the driver. But as you have overwritten some modules (as described)  by 32 bits one this will not work ....

---

### Post by snakdoc on 2009-04-10
thanks mate will try to compile again with different ones

---

### Post by snakdoc on 2009-04-11
anyone had luck getting this to work with newer kernels than 2.6.27.* ?

---

### Post by snakdoc on 2009-04-14
while playing with this upgraded to 9.03 and this what i get when i compile and run hsfconfig

driver version 7.60.00.18oem
grep: /lib/modules/2.6.28-11-generic/build/include/linux/device.h: No such file or directory
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "SUBDIRS+=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: [clean] Error 2 (ignored)
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "SUBDIRS+=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS= -DFOUND_OPEN_SUBSTREAM_NOFILE       -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: [clean] Error 2 (ignored)
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "SUBDIRS+=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

---

### Post by chemist109 on 2009-04-15
I installed the HSFmodem drivers using sutupud's method, and they worked, but the sound stopped working.  I tried installing linuxants updated ALSA, but the sound was still broken.  I ended up removing, purging, and re-installing the kernel to get sound working again.  

Did anyone else have my sound problems?  And, if so, did they find a solution?

---

### Post by IvanQ on 2009-04-20
I've updated the [wiki page https://help.ubuntu.com/community/DialupModemHowto/Conexant]("https://help.ubuntu.com/community/DialupModemHowto/Conexant") with an attachment that implements the technique discussed here.

---

### Post by Paul S on 2009-04-25
> **chemist109 said:**
> I installed the HSFmodem drivers using sutupud's method, and they worked, but the sound stopped working.  I tried installing linuxants updated ALSA, but the sound was still broken.  I ended up removing, purging, and re-installing the kernel to get sound working again.  

Did anyone else have my sound problems?  And, if so, did they find a solution?

Yes, but on jaunty not intrepid.

When I tried inserting snd-hda-intel, it failed and complained about symbol errors. I wonder if the /lib/modules/2.6.28-11-generic/modules.symbol file is broken by the alsa-linuxant-driver.  I didn't think of it at the time, but maybe you need to delete and rebuild it.  But, i'm not sure how .. perhaps deleting the kernel completing and then "sudo rm -fr /lib/modules/2.6.28-11-generic" and then reinstall the kernel.

These are some of the things I've tried.  The linuxant alsa driver is the wrong version for jaunty's alsa ( 1.0.19 vs 1.0.18 ).  I found the older ( 1.0.18 ) linuxant alsa deb and tried it but it failed to build.  Then I tried the current 1.0.19.4 and it installed but didn't work with the hsfmodem.  Then I tried uninstalling it and my sound was broken.  Then I tried reinstalling the kernel, but sound still didn't work.  So, I installed the alsa-source package and untarred, patched, and built with module-assistant the alsa modules.  I got the patch from the linuxant alsa driver page for 1.0.18.  Upon rebooting, now sound works.  So, I tried the current hsfmodem with it.  It works, but is speed limited to 14 kbps.  Yes, I did replace the "imported" subdirectory before installing it.  I can't get it to run full speed on jaunty.

hth .. ymmv

---

### Post by parsibox on 2009-04-25
> **Paul S said:**
> Yes, but on jaunty not intrepid.

When I tried inserting snd-hda-intel, it failed and complained about symbol errors. I wonder if the /lib/modules/2.6.28-11-generic/modules.symbol file is broken by the alsa-linuxant-driver.  I didn't think of it at the time, but maybe you need to delete and rebuild it.  But, i'm not sure how .. perhaps deleting the kernel completing and then "sudo rm -fr /lib/modules/2.6.28-11-generic" and then reinstall the kernel.

These are some of the things I've tried.  The linuxant alsa driver is the wrong version for jaunty's alsa ( 1.0.19 vs 1.0.18 ).  I found the older ( 1.0.18 ) linuxant alsa deb and tried it but it failed to build.  Then I tried the current 1.0.19.4 and it installed but didn't work with the hsfmodem.  Then I tried uninstalling it and my sound was broken.  Then I tried reinstalling the kernel, but sound still didn't work.  So, I installed the alsa-source package and untarred, patched, and built with module-assistant the alsa modules.  I got the patch from the linuxant alsa driver page for 1.0.18.  Upon rebooting, now sound works.  So, I tried the current hsfmodem with it.  It works, but is speed limited to 14 kbps.  Yes, I did replace the "imported" subdirectory before installing it.  I can't get it to run full speed on jaunty.

hth .. ymmv

i have conexant modem in dell inspiron 6400 and my kernel is 2.6.28-11-generic 
how can i install my modem???????
i am going to be mad.
my life is ubuntu and now i connect to internet with windows XP.
shet

---

### Post by snakdoc on 2009-04-27
parsibox i believe [http://www.linuxant.com/drivers/hsf/downloads-patches.php](http://www.linuxant.com/drivers/hsf/downloads-patches.php) this should fix your problem

---

### Post by parsibox on 2009-04-28
i will try it
[www.linuxant.com](www.linuxant.com)  release new .deb file for my kernel
it install but can not connect to ISP

---

### Post by W.Sorting on 2009-04-28
Has anyone successfully got this method to work with Ubuntu 9.04 (Jaunty)?  

If anyone was successful with another method, could you please post it?  I would like to get this working as soon as possible ;)

Thanks!
W.Sorting

---

### Post by kazemi on 2009-04-30
Hello everyone,

I just installed Ubuntu 9.04 on my Dell Inspiron 1300 with a Conexant HSF modem. In Ubuntu 8.10, I used to make this modem with compiling a customized driver (according to this link [https://help.ubuntu.com/community/Di...Howto/Conexant]("https://help.ubuntu.com/community/DialupModemHowto/Conexant") ) and everything was working fine.

However, when I try to compile the driver in 9.04, I recieve the following error log:

-----------------------------------------------------------------------------------------------------
driver version 7.68.00.09oem
(cd /usr/src/linux-headers-2.6.28-11-generic && make "CNXT_KERNELSRC=/usr/src/linux-headers-2.6.28-11-generic" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
(cd /usr/src/linux-headers-2.6.28-11-generic && make "CNXT_KERNELSRC=/usr/src/linux-headers-2.6.28-11-generic" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC -DFOUND_TLV -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfosspec.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfserial.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfengine.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfpcibasic2.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfpcibasic3.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfhda.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97ich.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97via.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97ali.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97ati.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfmc97sis.mod /usr/src/linux-headers-2.6.28-11-generic/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /usr/src/linux-headers-2.6.28-11-generic && make "CNXT_KERNELSRC=/usr/src/linux-headers-2.6.28-11-generic" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

----------------------------------------------------------------------------------------------------

I suppose the error is due to wrong "linux-headers-2.6.28-11-generic" path. I have the linux headers installed but not sure about the right path to it ( I used /usr/src/linux-headers-2.6.28-11-generic ).

Can anyone instruct me how to resolve this problem? As I said, the driver compiling for this modem was okay on Ubuntu 8.10 without any problem.

---

### Post by Paul S on 2009-04-30
> **kazemi said:**
> In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1


In terminal, look for string.h as follows:

```
 find /usr/src/linux-headers-2.6.28-11-generic/ -iname '*string.h*'

```

this is what I get back on my jaunty:

/usr/src/linux-headers-2.6.28-11-generic/include/config/netfilter/xt/match/string.h
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h

If it doesn't show up, then reinstall your linux-headers-2.6.28-11-generic and try again.

please report back if you get the modem working as the rest of us are failing on jaunty.

hth

---

### Post by kazemi on 2009-05-01
> **Paul S said:**
> In terminal, look for string.h as follows:

```
 find /usr/src/linux-headers-2.6.28-11-generic/ -iname '*string.h*'

```

this is what I get back on my jaunty:

/usr/src/linux-headers-2.6.28-11-generic/include/config/netfilter/xt/match/string.h
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h

If it doesn't show up, then reinstall your linux-headers-2.6.28-11-generic and try again.

please report back if you get the modem working as the rest of us are failing on jaunty.

hth
To Paul S:

I did your instruction, and i got the output the same as in your last post. Now what does it mean? The "string.h" is out there, but the compiler cannot see it??

By the way, I tried the same procedure with the latest linuxant TAR package ([http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.04full/hsfmodem-7.80.02.04full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.04full/hsfmodem-7.80.02.04full.tar.gz)), but again no results. By the way, I lose my sound every time I uninstall the compiled driver, which is very annoying (I have already installed the ALSA driver from linuxant, but no use).

Any comments to resolve the problem with "string.h"??

---

### Post by kazemi on 2009-05-01
for your information, other things that i tried till now:

1. replacing the /modules/imported directory of the latest linuxant driver (hsfmodem-7.80.02.04full.tar.gz) with that of Dell OEM driver (TAR package). This results in error during compiling with "sudo hsfconfig".

2. So i got the latest ".deb" package for jaunty from linuxant website, extracted it, and obtained the "/usr/lib/hsfmodem/modules/binaries" (which contained "linux-2.6.28-11-generic-SMP" precompiled), then put this in the corresponding directory of "hsfmodem-7.80.02.04full.tar.gz" (that is /modules/binaries). This time during compiling with sudo hsfconfig, it recognized the precompiled modules and used them, however, it results in unregistered limited driver! This work with 14.4kbps now.

I think that if we can find a solution to resolve the mentioned error with "string.h" during compiling, then we can obtain a fully working driver for the modem.

I am quite new to linux file system and programming, so any instruction or help in this regard is appreciated.

---

### Post by Paul S on 2009-05-01
> **kazemi said:**
> By the way, I lose my sound every time I uninstall the compiled driver, which is very annoying (I have already installed the ALSA driver from linuxant, but no use).

Read my note above regarding the mismatch between alsa-driver-linuxant and jaunty.  To get sound working, I had to apply the proper alsa version patch (from linuxant page) to alsa-source, then tar it back up and use module-assistant to create a alsa-modules-2.6.28-11-generic_<>_.deb. Details at end if you need it.

I have found that uninstalling an old version of hsfmodem driver leaves a lot of files in the wrong place.  In particular, it leaves /lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko as /lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko.REPLACEDBYHSFMODEM which leaves sound not working.  I think this may be fixed in the hsfmodem 7.80.02.04 driver, but am not sure.

I wonder if the reason you can't compile is because something has been damaged in your /lib/modules/ or /usr/src/ directories.  If that's the problem, then just reinstalling will not fix it, because a reinstall over writes existing files, but does not delete extra files that may be there.

Maybe you should uninstall hsf and your kernel and clean everything out.  This is what I did to do that:

First make sure you have everything important backed up, in case the worse happens and your system becomes unbootable.

A caution is that once you uninstall your kernel, you cannot do anything that requires any kernel changes (like plug in printer) because the modules will be gone.  So, do this when you're not doing anything else.

1. sudo aptitude purge alsa-driver-linuxant
2. do "sudo make uninstall" from the directory where you untarred you're hsfmodem to uninstall it, or if you installed a debian "sudo aptitude purge hsfmodem"
3. sudo updatedb
4. locate hsf
this will list lingering hsf related directories and files, examples on my system are:
sudo rm -fr /etc/hsfmodem
sudo rm /usr/sbin/rchsf
sudo rm /etc/udev/rules.d/00-hsf.rules
sudo rm /etc/init.d/hsf
sudo rm /etc/modprobe.d/hsf*
sudo rm /etc/rc0.d/K91hsf  /etc/rc1.d/K91hsf  /etc/rc2.d/S09hsf  /etc/rc3.d/S09hsf  /etc/rc4.d/S09hsf  /etc/rc5.d/S09hsf  /etc/rc6.d/K91hsf

note .. be careful to be sure you don't delete something important or you'll end up reinstalling your jaunty.
5. Then uninstall your kernel
sudo aptitude purge linux-image-2.6.28-11-generic linux-restricted-modules-2.6.28-11-generic linux-headers-2.6.28-11-generic linux-headers-2.6.28-11
6.  Then go in and delete any lingering directories and files that may have been left by hsfmodem or alsa-driver-linuxant.
cd /lib/modules
ls -la
sudo rm -fr 2.6.28-11-generic
cd /usr/src
ls -la
sudo rm -fr linux-headers-2.6.28-11-generic linux-headers-2.6.28-11
7. Then reinstall the kernel
sudo aptitude install linux-image-2.6.28-11-generic linux-restricted-modules-2.6.28-11-generic linux-headers-2.6.28-11-generic linux-headers-2.6.28-11
8. reboot
9. Start over with building hsfmodem, using the current 7.80.02.04.  That is the only idea I have as to how to get it to compile.  But, as I said earlier, although it works it is still limited to 14.4 kbps

If it kills your sound, then try my idea of patching alsa-source with the linuxant patch for 1.0.18.

First get the patch in your home directory:
cd ~
wget [http://www.linuxant.com/alsa-driver/alsa-driver-1.0.18-1.patch](http://www.linuxant.com/alsa-driver/alsa-driver-1.0.18-1.patch)

1. sudo aptitude install modules-assistant alsa-source
2. cd /usr/src
3. sudo tar xjvf alsa-driver.tar.bz2
4. cd modules/alsa-driver
5. patch -p1 < ~/alsa-driver-1.0.18-1.patch
6. cd /usr/src
7. sudo tar cjvf alsa-driver.tar.bz2 modules/ 
8. sudo module-assistant auto-build alsa
9. sudo dpkg -i /usr/src/alsa-modules-2.6.28-11-generic*.deb

hth

---

### Post by kazemi on 2009-05-02
I did a clean install of ubuntu 9.04, and tried to compile the newest linuxant driver for HSF modem (replaced by /modules/imported from Dell OEM driver).

The result: I still get the error message with "string.h" during "sudo hsfconfig". Very interesting indeed!

Anybody else managed to compile the driver with the latest linuxant TAR package? (not the pre-compiled DEB package from their website).

maybe this is problem with kernel or the driver itself!!

I gave up testing, will wait until the next kernel version is out and will try compiling again....

---

### Post by Paul S on 2009-05-02
> **kazemi said:**
> I did a clean install of ubuntu 9.04, and tried to compile the newest linuxant driver for HSF modem (replaced by /modules/imported from Dell OEM driver).

The result: I still get the error message with "string.h" during "sudo hsfconfig". Very interesting indeed!

Anybody else managed to compile the driver with the latest linuxant TAR package? (not the pre-compiled DEB package from their website).

maybe this is problem with kernel or the driver itself!!

I gave up testing, will wait until the next kernel version is out and will try compiling again....

Did you remember to "sudo aptitude install build-essential linux-headers-generic" on your fresh install?

As I said before, it compiles on jaunty here, but I don't know what I have installed differently.  Also, are you sure your getting the correct architecture (i386 versus x86_64)

regards,

---

### Post by kazemi on 2009-05-02
clean install, double checked that i have build-essential, linux-headers as necessary, and all other things...

result = the same error message with "string.h"

did u manage to compile the latest linuxant driver (modified by Dell OEM driver) on jaunty? u couldn't get more than 14kbps?

by the way, anybody checked the latest ISO DVD Image from Dell for Jaunty? maybe they have included a working driver for their modem.... I dont have access to high speed internet, so i can't check it...

---

### Post by McMurdo on 2009-05-06
Sounds rather complicated. I hope there is a driver in that .iso or Dell releases a .deb soon.

---

### Post by digitalhead on 2009-05-19
> **kazemi said:**
> by the way, anybody checked the latest ISO DVD Image from Dell for Jaunty? maybe they have included a working driver for their modem.... I dont have access to high speed internet, so i can't check it...

> **McMurdo said:**
> Sounds rather complicated. I hope there is a driver in that .iso or Dell releases a .deb soon.

No, Dell's DVD ISO does not include the driver and I seriously doubt they will release a DEB for it either. It appears as though Dell has decided to only support LTS releases and leaving the rest up to the users. I've been banging my head against the wall for over a week trying to hack this modem driver to get it working and I'm not going to give up. Since I'm using Kubuntu, I've been looking forward to the latest KDE 4.2 for a while, but if I can't get online, it's kind of pointless to worry about upgrading.

As a side question, does anybody know if the DKMS package from Dell will let you upgrade through apt and keep the modem driver working through distribution upgrades? If so, that could be the answer to this problem, but it seems kind of mean and cruel to force dialup users to upgrade to a new release over the Internet. Personally, I haven't seen where DKMS does any real good, even just a kernel upgrade in the same release.

---

### Post by ChamPro on 2009-05-20
> **kazemi said:**
> clean install, double checked that i have build-essential, linux-headers as necessary, and all other things...

result = the same error message with "string.h"

did u manage to compile the latest linuxant driver (modified by Dell OEM driver) on jaunty? u couldn't get more than 14kbps?

by the way, anybody checked the latest ISO DVD Image from Dell for Jaunty? maybe they have included a working driver for their modem.... I dont have access to high speed internet, so i can't check it...

I haven't had any luck with Jaunty either. I get the same string.h error. Here's my sudo hsfconfig log:
```
driver version 7.68.00.09oem
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2
```

I have installed build-essential and doing a find /usr/src/linux-headers-2.6.28-11-generic/ -iname '*string.h*'
```
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/netfilter/xt/match/string.h
```
I'm debating whether to just use the Linuxant free driver since my Dad has old phones lines anyways, or pay the $20 instead of buying a new modem (all 3 of the modems I have are crappy Conexant winmodems).

UPDATE: I tried to install the Linuxant drivers from .debs (the alsa & hsf) and it just maxes the CPU trying to build the module but never finishes. Awesome.

---

### Post by digitalhead on 2009-05-20
I found out earlier today that Dell is definitely not going to be providing Conexant modem drivers for any version of Ubuntu released after 8.04. This leaves a few options... buy the driver from Linuxant for $20 every year, buy an Intel or Lucent external modem (if you're using a laptop), or figure out how to hack future drivers, which will get rather annoying after a few releases. A decent external modem will run anywhere between $20 and $40, which will be about the same cost of renewing a Linuxant license until I replace my laptops. So much for Dell supporting Ubuntu. Personally, I'm still trying to hack the driver. If I get it solved, I will be sure to post it here.

---

### Post by NZJon on 2009-05-20
Hi there digitalhead,

I've installed some "Dell Hybrid" drivers, as per the instructions [here]("https://help.ubuntu.com/community/DialupModemHowto/Conexant"), on my Dell Inspiron 6000.

Using WvDial or gnome-ppp I can get the modem to dial, and connect to, the remote machine. This shows me that the modem can be made to work. (I had to faff around creating a symlink for the .../linux/string.h file in parent dir.) However, as soon as the "handshaking" is completed, the pppd is started, which then exists straight away. I can't figure out (yet) how to fix this. 

I've got a post up [here]("http://ubuntuforums.org/showthread.php?t=1164795") which details my pppd problems. If you have any advice, I certainly love to hear from you.

Cheers,

Jon

---

### Post by Kaulbach on 2009-05-24
I work at a community-based ISP in Toronto. We were donated a large number of Dell GX1 series machines (P2,400Mhz typically).We wished to install some version of Linux, put some inexpensive modems in, and distribute to people without internet access so they could use our dial-up. At that time 6.06 (Dapper) was the platform we chose to work with, and "winmodems" were becoming plentiful and cheap as people began migrating to ADSL, cable, and other faster forms of internet access. After some research it was determined that the Conexant RD01-D270 model would work with the methods described at the following threads:
[http://ubuntuforums.org/showthread.php?t=180632]("http://ubuntuforums.org/showthread.php?t=180632")
 and 
[http://ubuntuforums.org/showthread.php?t=189009]("http://ubuntuforums.org/showthread.php?t=189009")

A custom 6.06 package was built for this. We also ordered a bulk amount of these modems at this time. During this period system updates and other changes to 6.06 and later versions made the custom driver problemmatic (default bash/dash shell, kernel updates, etc) and Dell was also beginning to supply full speed OEM drivers which we were hopeful might work. The results of lspci for instance shows in part:
Subsystem: Dell Device [1028:8d88]

The primary Vendor:Device result is:
Conexant Systems, Inc. Device [14f1:2702] (rev 01)

The chipset reads CX11252-15, and research indicates it is an HSFi

To try and expedite matters we approached Linuxant about a possible bulk licensing fee, but they were not agreeable to this. Dell disclaimed knowledge of this modem and basically we were back to the beginning of trying to work it out ourselves. 8.04 arrived during this period. The Dell 8.04 Conexant drivers seemed to sometimes work, sometimes not. Much frustration ensued. Also Dell is not currently providing drivers for 8.10 and 9.04, possibly we may see one for next LTS of 10.04 (hopefully).

Recently we revived the idea and this is how I got this particular model working under 9.04
(specifically an Xubuntu box but all instructions given here are Desktop-Environment-agnostic and should work equally well with KDE or GNOME )

Firstly, the pre-requisites need to be present:
sudo apt-get update && sudo apt-get install build-essential linux-headers-$(uname -r) debhelper fakeroot

Later, hsfconfig will try to use /usr/src/kernel-headers-$(uname -r) instead of /usr/src/linux-headers-$(uname -r) so we do:
sudo ln -s /usr/src/linux-headers-$(uname -r) /usr/src/kernel-headers-$(uname -r)

Make the directories:
cd ~/
mkdir Dell ; mkdir Linuxant

Start by getting the 8.04 Dell driver and untar it:

cd Dell
wget http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09oem.tar.gz
tar -xvzf hsfmodem-7.68.00.09oem.tar.gz

Same with the most recent Linuxant Debian tarball:
cd ../Linuxant
wget http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.04full/hsfmodem-7.80.02.04full.tar.gz
tar -xvzf hsfmodem-7.80.02.04full.tar.gz

Make a patches dir in the Linuxant one, get and put a patch there:
cd hsfmodem-7.80.02.04full
mkdir patches ; cd patches
wget http://www.linuxant.com/drivers/hsf/full/archive/patches/hsf-7.80.02.04-debian_tree.patch
cd ../

Remove the Linuxant modules/imported directory and replace it with the Dell modules/imported directory: 
rm -rf modules/imported
cp -a ~/Dell/hsfmodem-7.68.00.09oem/modules/imported modules

Taking from Posting #4 at [http://ubuntuforums.org/showthread.php?t=1143904]("http://ubuntuforums.org/showthread.php?t=1143904") fix line 356 of the osservices.h file 
From:
#include <strings.h>
Into:
#include <linux/string.h>
 
For this I did in the current working directory of ~/Linuxant/hsfmodem-7.80.02.04full/ :
nano +356 modules/imported/include/osservices.h
Saved and exited.

To reflect that this is a custom-built driver, I edited lines 12 and 13 in the Dell makeflags.mak file (not an essential step):
nano +12 modules/imported/makeflags.mak
And changed:
IMPORTED_BUILD_TYPE = oem
IMPORTED_CNXTLINUXVERSION = 7.68.00.09oem
Into:
IMPORTED_BUILD_TYPE = custom
IMPORTED_CNXTLINUXVERSION = 7.80.02.04custom
Saved and exited.

At this point hsfconfig needs to be made so that we can apply the patch:
sudo make install 
So after this I did:
sudo hsfconfig --patch patches/hsf-7.80.02.04-debian_tree.patch
Then successfully made clean, rebuilt again:
sudo make clean
sudo make install
And then the recommended:
sudo hsfconfig

When hsfconfig asks "Where is the linux source build directory that matches your running kernel?" I used:
/usr/src/linux-headers-$(uname -r)


THERE WAS A PROBLEM! (and then a solution in my case)
The sudo make install/sudo hsfconfig process had no complaints, and recognised my modem after a reboot, creating the proper /dev/ttySHSF0 and linking /dev/modem to this. All seemed well, but was not.
Testing with: sudo screen /dev/modem       and manually inputting commands showed the modem properly responds to all the things like ATZ and so on, which looked good (f you do this part remember that ctrl-a and then uppercase K will exit the screen session properly).

HOWEVER: Setting ATX1 (ignore dial tone) and then picking up the phone and listening while it is dialling a number from a command like ATDT123456789 shows it is not actually making any touch-tone sounds that would dial anywhere. Eventually it times out with NO CARRIER for instance.

THERE WAS A DIAGNOSIS:
So after much gnashing of teeth, wailing, fruitless experimental AT commands to the modem, etc, I discovered that the default driver being used for this modem was incorrect.
It is an HSFi modem but the best guess of the detection method was to use the driver called hsfpcibasic2smart when in fact it should have been the driver called hsfpcibasic2hsfi ...this turns out to be coded into the file: mod_pcibasic2.c

THERE WAS A SOLUTION:
So in the working directory of ~/Linuxant/hsfmodem-7.80.02.04full 
nano +118 modules/mod_pcibasic2.c
(which in the file is just under a line reading, appropriately "/* the following entries need verification & more testing: */" )
I changed:
        {0x14F1, 0x2702, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2smart")},
into:
        {0x14F1, 0x2702, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2hsfi")},
Saved and exited (please note the 0x14F1 and 0x2702 correspond to Vendor:Device of 14F1:2702 found from lspci -nn ).

I then made clean, rebuilt, ran hsfconfig:
sudo make clean
sudo make install
sudo hsfconfig

Success!

Further notes:
For some reason it wants to load all these modules (result of lsmod|grep hsf):
hsfusbcd2              69312  0
hsfmc97sis             71488  0
hsfmc97ati             70440  0
hsfmc97ali             77112  0
hsfmc97via             72888  0
hsfmc97ich             74812  0
hsfpcibasic3          113032  0
hsfpcibasic2           71216  0
hsfserial              28708  8 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2
hsfengine            1267776  9 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2,hsfserial
hsfosspec             107084  13 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2,hsfserial,hsfengine
hsfsoar               101720  7 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic2

I'll poke into why this happens shortly, it seems only (for me) hsfengine, hsfserial, and hsfpcibasic2 are essential.

---

### Post by chang47 on 2009-05-25
> **ChamPro said:**
> I haven't had any luck with Jaunty either. I get the same string.h error. Here's my sudo hsfconfig log:
```
driver version 7.68.00.09oem
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.28-11-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.28-11-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.28-11-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2
```

I have installed build-essential and doing a find /usr/src/linux-headers-2.6.28-11-generic/ -iname '*string.h*'
```
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h
/usr/src/linux-headers-2.6.28-11-generic/include/config/netfilter/xt/match/string.h
```
I'm debating whether to just use the Linuxant free driver since my Dad has old phones lines anyways, or pay the $20 instead of buying a new modem (all 3 of the modems I have are crappy Conexant winmodems).

UPDATE: I tried to install the Linuxant drivers from .debs (the alsa & hsf) and it just maxes the CPU trying to build the module but never finishes. Awesome.

I had the same problem and after reading a couple of threads including this one I decided to edit /usr/lib/hsfmodem/modules/imported/include/osservices.h and changed "string.h" to "linux/string.h" on line 356. I then redid hsfconf and was able to get the driver working on Jaunty. Tested it out with faxing and it worked.  I just wanted to do fax.

Hope this will work for you.

---

### Post by Orion2000za on 2009-05-26
> **Kaulbach said:**
> I work at a community-based ISP in Toronto. We were donated a large number of Dell GX1 series machines (P2,400Mhz typically).We wished to install some version of Linux, put some inexpensive modems in, and distribute to people without internet access so they could use our dial-up. At that time 6.06 (Dapper) was the platform we chose to work with, and "winmodems" were becoming plentiful and cheap as people began migrating to ADSL, cable, and other faster forms of internet access. After some research it was determined that the Conexant RD01-D270 model would work with the methods described at the following threads:
[http://ubuntuforums.org/showthread.php?t=180632]("http://ubuntuforums.org/showthread.php?t=180632")
 and 
[http://ubuntuforums.org/showthread.php?t=189009]("http://ubuntuforums.org/showthread.php?t=189009")

A custom 6.06 package was built for this. We also ordered a bulk amount of these modems at this time. During this period system updates and other changes to 6.06 and later versions made the custom driver problemmatic (default bash/dash shell, kernel updates, etc) and Dell was also beginning to supply full speed OEM drivers which we were hopeful might work. The results of lspci for instance shows in part:
Subsystem: Dell Device [1028:8d88]

The primary Vendor:Device result is:
Conexant Systems, Inc. Device [14f1:2702] (rev 01)

The chipset reads CX11252-15, and research indicates it is an HSFi

To try and expedite matters we approached Linuxant about a possible bulk licensing fee, but they were not agreeable to this. Dell disclaimed knowledge of this modem and basically we were back to the beginning of trying to work it out ourselves. 8.04 arrived during this period. The Dell 8.04 Conexant drivers seemed to sometimes work, sometimes not. Much frustration ensued. Also Dell is not currently providing drivers for 8.10 and 9.04, possibly we may see one for next LTS of 10.04 (hopefully).

Recently we revived the idea and this is how I got this particular model working under 9.04
(specifically an Xubuntu box but all instructions given here are Desktop-Environment-agnostic and should work equally well with KDE or GNOME )

Firstly, the pre-requisites need to be present:
sudo apt-get update && sudo apt-get install build-essential linux-headers-$(uname -r) debhelper fakeroot

Later, hsfconfig will try to use /usr/src/kernel-headers-$(uname -r) instead of /usr/src/linux-headers-$(uname -r) so we do:
sudo ln -s /usr/src/linux-headers-$(uname -r) /usr/src/kernel-headers-$(uname -r)

Make the directories:
cd ~/
mkdir Dell ; mkdir Linuxant

Start by getting the 8.04 Dell driver and untar it:

cd Dell
wget [http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09oem.tar.gz](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09oem.tar.gz)
tar -xvzf hsfmodem-7.68.00.09oem.tar.gz

Same with the most recent Linuxant Debian tarball:
cd ../Linuxant
wget [http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.04full/hsfmodem-7.80.02.04full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.04full/hsfmodem-7.80.02.04full.tar.gz)
tar -xvzf hsfmodem-7.80.02.04full.tar.gz

Make a patches dir in the Linuxant one, get and put a patch there:
cd hsfmodem-7.80.02.04full
mkdir patches ; cd patches
wget [http://www.linuxant.com/drivers/hsf/full/archive/patches/hsf-7.80.02.04-debian_tree.patch](http://www.linuxant.com/drivers/hsf/full/archive/patches/hsf-7.80.02.04-debian_tree.patch)
cd ../

Remove the Linuxant modules/imported directory and replace it with the Dell modules/imported directory: 
rm -rf modules/imported
cp -a ~/Dell/hsfmodem-7.68.00.09oem/modules/imported modules

Taking from Posting #4 at [http://ubuntuforums.org/showthread.php?t=1143904]("http://ubuntuforums.org/showthread.php?t=1143904") fix line 356 of the osservices.h file 
From:
#include <strings.h>
Into:
#include <linux/string.h>
 
For this I did in the current working directory of ~/Linuxant/hsfmodem-7.80.02.04full/ :
nano +356 modules/imported/include/osservices.h
Saved and exited.

To reflect that this is a custom-built driver, I edited lines 12 and 13 in the Dell makeflags.mak file (not an essential step):
nano +12 modules/imported/makeflags.mak
And changed:
IMPORTED_BUILD_TYPE = oem
IMPORTED_CNXTLINUXVERSION = 7.68.00.09oem
Into:
IMPORTED_BUILD_TYPE = custom
IMPORTED_CNXTLINUXVERSION = 7.80.02.04custom
Saved and exited.

At this point hsfconfig needs to be made so that we can apply the patch:
sudo make install 
So after this I did:
sudo hsfconfig --patch patches/hsf-7.80.02.04-debian_tree.patch
Then successfully made clean, rebuilt again:
sudo make clean
sudo make install
And then the recommended:
sudo hsfconfig

When hsfconfig asks "Where is the linux source build directory that matches your running kernel?" I used:
/usr/src/linux-headers-$(uname -r)


THERE WAS A PROBLEM! (and then a solution in my case)
The sudo make install/sudo hsfconfig process had no complaints, and recognised my modem after a reboot, creating the proper /dev/ttySHSF0 and linking /dev/modem to this. All seemed well, but was not.
Testing with: sudo screen /dev/modem       and manually inputting commands showed the modem properly responds to all the things like ATZ and so on, which looked good (f you do this part remember that ctrl-a and then uppercase K will exit the screen session properly).

HOWEVER: Setting ATX1 (ignore dial tone) and then picking up the phone and listening while it is dialling a number from a command like ATDT123456789 shows it is not actually making any touch-tone sounds that would dial anywhere. Eventually it times out with NO CARRIER for instance.

THERE WAS A DIAGNOSIS:
So after much gnashing of teeth, wailing, fruitless experimental AT commands to the modem, etc, I discovered that the default driver being used for this modem was incorrect.
It is an HSFi modem but the best guess of the detection method was to use the driver called hsfpcibasic2smart when in fact it should have been the driver called hsfpcibasic2hsfi ...this turns out to be coded into the file: mod_pcibasic2.c

THERE WAS A SOLUTION:
So in the working directory of ~/Linuxant/hsfmodem-7.80.02.04full 
nano +118 modules/mod_pcibasic2.c
(which in the file is just under a line reading, appropriately "/* the following entries need verification & more testing: */" )
I changed:
        {0x14F1, 0x2702, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2smart")},
into:
        {0x14F1, 0x2702, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2hsfi")},
Saved and exited (please note the 0x14F1 and 0x2702 correspond to Vendor:Device of 14F1:2702 found from lspci -nn ).

I then made clean, rebuilt, ran hsfconfig:
sudo make clean
sudo make install
sudo hsfconfig

Success!

Further notes:
For some reason it wants to load all these modules (result of lsmod|grep hsf):
hsfusbcd2              69312  0
hsfmc97sis             71488  0
hsfmc97ati             70440  0
hsfmc97ali             77112  0
hsfmc97via             72888  0
hsfmc97ich             74812  0
hsfpcibasic3          113032  0
hsfpcibasic2           71216  0
hsfserial              28708  8 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2
hsfengine            1267776  9 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2,hsfserial
hsfosspec             107084  13 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic3,hsfpcibasic2,hsfserial,hsfengine
hsfsoar               101720  7 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic2

I'll poke into why this happens shortly, it seems only (for me) hsfengine, hsfserial, and hsfpcibasic2 are essential.

I am more than a little bit impressed by your efforts, please keep up the good work! :D

---

### Post by Paul S on 2009-05-26
Kaulbach, thanks, it finally is working here.

I'm running 64 bit jaunty on a dell inspiron laptop.  I have the standard dell conexant.  It requires the alsa-driver-linuxant_1.0.20.0_all.deb to be compiled first, then reboot, then do your instructions (but substitute the x86_64 packages for the i386 versions.)

However, now when I connect, I get a hard freeze that requires a power off / on to recover.  This is nasty.  It happens after varying amounts of time (within a minute, after 5 minutes or after 20 minutes).

I noticed the following messages in /var/log/kern.log just BEFORE the last freeze:

May 26 13:58:38 localhost kernel: [ 3564.705656] general protection fault: 0000 [#1] SMP
May 26 13:58:38 localhost kernel: [ 3564.705666] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/status
May 26 13:58:38 localhost kernel: [ 3564.705671] Dumping ftrace buffer:
May 26 13:58:38 localhost kernel: [ 3564.705675]    (ftrace buffer empty)
May 26 13:58:38 localhost kernel: [ 3564.705678] CPU 0
May 26 13:58:38 localhost kernel: [ 3564.705682] Modules linked in: ppp_deflate zlib_deflate bsd_comp ppp_async crc_ccitt binfmt_misc ppdev bridge stp bnep vboxnetflt vboxdrv input_polldev hsfhda snd_hda_cod
ec_conexant snd_hda_codec_idt snd_hda_intel snd_hda_codec hsfusbcd2 hsfmc97sis hsfmc97ati hsfmc97ali hsfmc97via hsfmc97ich hsfpcibasic3 hsfpcibasic2 hsfserial hsfengine(P) hsfosspec hsfsoar ipt_REJECT ipt_LO
G xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_t
ables lp parport snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event b44 ssb snd_seq mii snd_timer snd_seq_device iTCO_wdt iTCO_vendor_support ie
ee80211_crypt_tkip wl(P) snd soundcore ieee80211_crypt ricoh_mmc sdhci_pci sdhci intel_agp psmouse snd_page_alloc serio_raw video pcspkr nvidia(P) dcdbas output joydev sha256_generic aes_x86_64 aes_gen
May 26 13:58:38 localhost kernel: ric cbc usbhid ohci1394 ieee1394 dm_crypt fbcon tileblit font bitblit softcursor [last unloaded: snd_hda_codec]
May 26 13:58:38 localhost kernel: [ 3564.705716] Pid: 3004, comm: khsfd/modem Tainted: P           2.6.28-11-generic #42-Ubuntu
May 26 13:58:38 localhost kernel: [ 3564.705716] RIP: 0010:[<ffffffffa1084a12>]  [<ffffffffa1084a12>] hsfengine2063_+0x32/0x180 [hsfengine]
May 26 13:58:38 localhost kernel: [ 3564.705716] RSP: 0018:ffff88007ddf7dc0  EFLAGS: 00010086
May 26 13:58:38 localhost kernel: [ 3564.705716] RAX: 0000000000000000 RBX: f000ec62f000e2c3 RCX: 0000000000000004
May 26 13:58:38 localhost kernel: [ 3564.705716] RDX: 0000000000000000 RSI: 0000000000020004 RDI: f000ec62f000e2c3
May 26 13:58:38 localhost kernel: [ 3564.705716] RBP: ffff88007a0bd000 R08: 0000000000000001 R09: 0000000000000000
May 26 13:58:38 localhost kernel: [ 3564.705716] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000020004
May 26 13:58:38 localhost kernel: [ 3564.705716] R13: 0000000000000000 R14: 0000000000000000 R15: ffff88007ddf7e86
May 26 13:58:38 localhost kernel: [ 3564.705716] FS:  00007f20181546f0(0000) GS:ffffffff80aa3000(0000) knlGS:0000000000000000
May 26 13:58:38 localhost kernel: [ 3564.705716] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
May 26 13:58:38 localhost kernel: [ 3564.705716] CR2: 0000000001f3e5d8 CR3: 0000000000201000 CR4: 00000000000006a0
May 26 13:58:38 localhost kernel: [ 3564.705716] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
May 26 13:58:38 localhost kernel: [ 3564.705716] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
May 26 13:58:38 localhost kernel: [ 3564.705716] Process khsfd/modem (pid: 3004, threadinfo ffff88007ddf6000, task ffff88007d1b5980)
May 26 13:58:38 localhost kernel: [ 3564.705716] Stack:
May 26 13:58:38 localhost kernel: [ 3564.705716]  0000000000000001 ffff88007a0bd000 ffff88007a0bd000 0000000000000001
May 26 13:58:38 localhost kernel: [ 3564.705716]  0000000000000001 ffffffffa1088781 0000000000000030 ffff88007a0bd000
May 26 13:58:38 localhost kernel: [ 3564.705716]  ffff88007ddf7e87 0000000000000001 0000000000000001 ffffffffa1087247
May 26 13:58:38 localhost kernel: [ 3564.705716] Call Trace:
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffffa1088781>] ? hsfengine1952_+0x41/0x50 [hsfengine]
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffffa1087247>] ? hsfengine52_+0xa7/0x140 [hsfengine]
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffffa11e3810>] ? cnxt_intr+0x370/0x4dc [hsfserial]
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffff8025c9bb>] ? mod_timer+0x4b/0x60
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffffa1037444>] ? cnxt_thread+0x1b4/0x240 [hsfosspec]
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffff8024a580>] ? default_wake_function+0x0/0x10
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffffa1083610>] ? hsfengine1867_+0x0/0x30 [hsfengine]
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffff80213979>] ? child_rip+0xa/0x11
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffffa1083610>] ? hsfengine1867_+0x0/0x30 [hsfengine]
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffffa1037290>] ? cnxt_thread+0x0/0x240 [hsfosspec]
May 26 13:58:38 localhost kernel: [ 3564.705716]  [<ffffffff8021396f>] ? child_rip+0x0/0x11
May 26 13:58:38 localhost kernel: [ 3564.705716] Code: 24 48 45 31 ed 48 85 ff 48 89 5c 24 30 4c 89 64 24 40 4c 89 74 24 50 48 89 6c 24 38 48 89 fb 41 89 f4 49 89 d6 0f 84 04 01 00 00 <48> 8b 6f 08 48 89 ef e8 12 f9 ff ff ba 01 00 00 00 85 c0 75 20
May 26 13:58:38 localhost kernel: [ 3564.705716] RIP  [<ffffffffa1084a12>] hsfengine2063_+0x32/0x180 [hsfengine]
May 26 13:58:38 localhost kernel: [ 3564.705716]  RSP <ffff88007ddf7dc0>
May 26 13:58:38 localhost kernel: [ 3564.705716] ---[ end trace c1ed297a00f8ae38 ]---
May 26 13:59:47 localhost kernel: [ 3633.248069] 0003601.385: <7>DPCRequest: array is full!
May 26 13:59:51 localhost kernel: [ 3637.831162] 0003605.968: <7>DPCRequest: array is full!
May 26 13:59:56 localhost kernel: [ 3642.408512] 0003610.545: <7>DPCRequest: array is full!
May 26 14:00:02 localhost kernel: [ 3648.458873] 0003616.595: <7>DPCRequest: array is full!
May 26 14:00:05 localhost kernel: [ 3651.456012] CE: hpet increasing min_delta_ns to 15000 nsec
May 26 14:00:08 localhost kernel: [ 3654.484986] 0003622.621: <7>DPCRequest: array is full!
May 26 14:00:13 localhost kernel: [ 3659.068011] 0003627.205: <7>DPCRequest: array is full!

A google reveals this post:  [http://www.linuxant.com/pipermail/hsflinux/2006q3/002047.html](http://www.linuxant.com/pipermail/hsflinux/2006q3/002047.html)   But, the complaint there was disconnect not freeze.

I'll give those init codes a try when I get time.

---

### Post by McMurdo on 2009-06-12
Wow, good work, y'all. Any chance of releasing a .tar or .deb with the proper changes made for 9.04?

---

### Post by Kaulbach on 2009-06-17
> **McMurdo said:**
> Wow, good work, y'all. Any chance of releasing a .tar or .deb with the proper changes made for 9.04?

Unfortunately, the Linuxant license does not allow for this.

---

### Post by McMurdo on 2009-06-19
Hmmm. Not surprising. Dell must have a licensing deal with them. What about a shell script? Would that be possible?

P.S. I think if this keeps I might just buy an USB modem.

---

### Post by JKyleOKC on 2009-06-23
> **Kaulbach said:**
> 
THERE WAS A PROBLEM! ... Setting ATX1 (ignore dial tone) and then picking up the phone and listening while it is dialling a number from a command like ATDT123456789 shows it is not actually making any touch-tone sounds that would dial anywhere. Eventually it times out with NO CARRIER for instance.

THERE WAS A DIAGNOSIS:
So after much gnashing of teeth, wailing, fruitless experimental AT commands to the modem, etc, I discovered that the default driver being used for this modem was incorrect.
It is an HSFi modem but the best guess of the detection method was to use the driver called hsfpcibasic2smart when in fact it should have been the driver called hsfpcibasic2hsfi ...this turns out to be coded into the file: mod_pcibasic2.c

THERE WAS A SOLUTION:
So in the working directory of ~/Linuxant/hsfmodem-7.80.02.04full 
nano +118 modules/mod_pcibasic2.c
(which in the file is just under a line reading, appropriately "/* the following entries need verification & more testing: */" )
I changed:
        {0x14F1, 0x2702, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2smart")},
into:
        {0x14F1, 0x2702, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2hsfi")},
Saved and exited (please note the 0x14F1 and 0x2702 correspond to Vendor:Device of 14F1:2702 found from lspci -nn ).

I then made clean, rebuilt, ran hsfconfig:
sudo make clean
sudo make install
sudo hsfconfig

Success!

This may be the solution to my problem, but the Vendor:Device codes for my unit are different: 14f1:2015. However I have the same symptom: no tones generated, neither the DTMF dial tones nor the fax chirps. Can you elaborate a bit on how you determined which driver to use to get tones generated?

---

### Post by Orion2000za on 2009-06-24
this is a quote from Mario Limoncieollo on the Dell linux mailinglist regarding this matter, I see/hope no harm in passing it on. The really interesting part is at the end where he invites anyone to repackage for later versions than Hardy. Maybe someone can do something with the code in question:

for some time I've been attempting to assemble a better solution for this problem that centers around using DKMS to provide that patched snd-hda-intel kernel module instead.  Unfortunately there were a lot of complications with building a DKMS package like this, including ALSA bugs and DKMS bugs that have been fixed later in the releases for both projects.

So I've got a better solution assembled now that i've uploaded to the dell-team PPA.  Here's what it looks like:

hsfmodem -> repackaed original conexant deb that pre-depends on hsfmodem-base-dkms
hsfmodem-base-dkms -> deb that contains the ALSA 1.0.16 tree with the ubuntu patchset (as of 2.6.24-24) applied and the conexant patchset applied

The way it will work is that provided you've got the headers installed for the 2.6.24 based kernel you intend on booting into, it will build the ALSA tree against those kernel headers prior to the reboot into the new kernel.  There is a header postinstall script that will execute DKMS to do these actions.  During the next reboot, it will take longer than normal because conexant's init script for hsfmodem triggers and links with snd-hda-intel that was rebuilt by DKMS.  The end result should be a functional audio driver and functional modem.

I've tested most of the scenarios I could think of related to the order of package installation, so hopefully this should be a more stable setup.  The one scenario I didn't test is not installing the headers during a package update.  Be sure to install all updates prior to a reboot if you are installing a new kernel.  The headers have to be there, the linux-ubuntu-modules has to be there and all.

Hopefully this works out for you modem folks.  We don't ship internal modems on any systems with an OS later than 8.04, so I wouldn't expect to see this on a newer release than 8.04 (especially considering the amount of work it took to get this solution right).  If someone from the community would like to step up however and use the sources for these packages to develop an 8.10, 9.04, or 9.10 solution you are welcome to do so.  I've posted them at:

[https://code.edge.launchpad.net/~dell-team/dell/hsfmodem-base-hardy](https://code.edge.launchpad.net/~dell-team/dell/hsfmodem-base-hardy)
and
[https://code.edge.launchpad.net/~dell-team/dell/hsfmodem-driver-hardy](https://code.edge.launchpad.net/~dell-team/dell/hsfmodem-driver-hardy)

I'll be glad to sponsor a functional solution for any of those other OSes into the dell-team PPA.

---

### Post by silvagroup on 2009-07-01
WOW !!! I was just wanting to be able to fax from my desktop, should not be such a night mare, even Windows does this.

I found all the drivers for conextant except any for the x64, everything I find is i386. So when I try to install I get wrong acrchitecture.
Don't want to damage my system but can I use dpkg -i --force-architecture hsfmodem_7.60.00.06oem_i386.deb or is that really bad !!!???

I just want to fax from my computer ocassionally without havingto have to install Windows again.

---

### Post by Orion2000za on 2009-07-02
given that is does affect the alsa sound drivers you might get problems. I do not run the x64 myself and am still on Hardy so I don't really know what would happen though.

---

### Post by silvagroup on 2009-07-02
Then it's not worth trying it if it has a possibility of messing up my system.

I installed the Dell drivers on my wife's system (i386) yesterday and it seemed to install alright, not sure because I haven't really checked it out yet to see if the modem works, ran out of day afater spending most of it trying to get my modem working on my x64.

But I will be experimenting with it some today to to see how it works.
Will report back with findings.

I thought I might have a real modem some where but after checking seven modems I have laying around, they were all win modems.

Would ndiswrapper work, because in my searching to get things working on my x64 I saw that there are drivers for windows 64 for these conexant modems?

---

### Post by Kaulbach on 2009-07-13
> **JKyleOKC said:**
> This may be the solution to my problem, but the Vendor:Device codes for my unit are different: 14f1:2015. However I have the same symptom: no tones generated, neither the DTMF dial tones nor the fax chirps. Can you elaborate a bit on how you determined which driver to use to get tones generated?

I had found the datasheet for the CX11252 chipset at the Conexant site, it states the type as "HSFi". So by this I knew that the driver should be the "hsf" one and not the "smart" one. The results of: sudo lshw show which driver a device uses. In this case it showed the modem as using the smart driver. Took some poking around to find where this is decided in the Linuxant code, but was eventually successful.

The site
[http://tldp.org/HOWTO/Conexant+Rockwell-modem-HOWTO/getting-started.html](http://tldp.org/HOWTO/Conexant+Rockwell-modem-HOWTO/getting-started.html)
Shows that your device code also corresponds to an HSF type. If the stanza for your specific vendor:device doesn't exist, you could try adding it.

ADDED:
The stanza of
       {0x14F1, 0x2015, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2")},
is found at line 57 of the mod_pcibasic2.c file

---

### Post by Kaulbach on 2009-07-13
> **Paul S said:**
> Kaulbach, thanks, it finally is working here.

I'm running 64 bit jaunty on a dell inspiron laptop.  I have the standard dell conexant.  It requires the alsa-driver-linuxant_1.0.20.0_all.deb to be compiled first, then reboot, then do your instructions (but substitute the x86_64 packages for the i386 versions.)

However, now when I connect, I get a hard freeze that requires a power off / on to recover.  This is nasty.  It happens after varying amounts of time (within a minute, after 5 minutes or after 20 minutes).

Unfortunately not much help here, I'm working only with the i386 version at the moment. But if you do find some solution/fix please do post back, I'm sure it help a lot of others who read this thread.

---

### Post by Paul S on 2009-07-13
silvagroup > I found all the drivers for conextant except any for the x64, everything I find is i386. So when I try to install I get wrong acrchitecture.

Kaulbach

> Unfortunately not much help here, I'm working only with the i386 version at the moment. But if you do find some solution/fix please do post back, I'm sure it help a lot of others who read this thread.

I gave up and installed an i386 and now the modem is working fine.  In searching the relevent web, I've found other instances of 64 bit freezing over the years with the conexant modem, and  they never get solved.  Most likely, it's not easily fixed.

So, my idea is to give up on 64 bit when using the hsfmodem.

hth

---

### Post by JKyleOKC on 2009-07-13
> **Kaulbach said:**
> I had found the datasheet for the CX11252 chipset at the Conexant site, it states the type as "HSFi". So by this I knew that the driver should be the "hsf" one and not the "smart" one. The results of: sudo lshw show which driver a device uses.

ADDED:
The stanza of
       {0x14F1, 0x2015, PCI_ANY_ID, PCI_ANY_ID, 0, 0, CNXTHWCFG("pcibasic2")},
is found at line 57 of the mod_pcibasic2.c fileThanks much!

I did find the stanza, and tried both the HSFi and Smart variations just in case, but none of them made any difference. The modem also has audio capabilities and that might be why the drivers don't work. I've tried both the Dell drivers, and the free ones, in both cases with and without the audio drivers that Linexant recommends, but nothing seems to make a difference. Looks like I'm going to have to use an external full modem to do fax processing on this system, or simply keep it on Win98SE where the modem works as expected...

---

### Post by silvagroup on 2009-08-05
It's really stupefying that as long as linux x64 OS has been out that there is still nothing for the winmodems in x64 arch.
By the way the dell hsf doesn't work with my wife's 386 after it installed. Just get errors, not posting them because I'm scrapping the whole faxing with Linux thing and staying with the old reliable fax machine, paper is made from a renewable resource after all and it's recyclable. Of course if you do allot of faxing that could be a problem.

---

### Post by slaykristian on 2009-08-06
> **kazemi said:**
> clean install, double checked that i have build-essential, linux-headers as necessary, and all other things...

result = the same error message with "string.h"

did u manage to compile the latest linuxant driver (modified by Dell OEM driver) on jaunty? u couldn't get more than 14kbps?

by the way, anybody checked the latest ISO DVD Image from Dell for Jaunty? maybe they have included a working driver for their modem.... I dont have access to high speed internet, so i can't check it...

Hello!

Kazemi, I think the problem is a conflict with original ALSA driver installed in jaunty by repos or cd...
I had the same problem, with my Dell Inspiron 1520, and I solved it with these method:

- remove hsfmodem package installed in your pc with:

```
sudo apt-get remove hsfmodem
```

- next, remove ALL Alsa modules and drivers with:

```
cat /proc/modules|gawk '/^snd-/{print $1}'|xargs -i rmmod {}
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils alsa
```

- then, you can try to install modem driver with the How-to ([https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)).

Try it... 
I think that before applies the HOW-TO method, is necessary for all cases, to uninstall ALSA drivers/modules presents in your distro, and install the Linuxant alsa driver, specified in the how-to, in a second moment.

I hope that it function also for you... 

Bye from Italy!

---

### Post by Orion2000za on 2009-11-23
Has anyone tried this in Karmic?

---

### Post by Orion2000za on 2009-11-23
to reply my own query:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8225398](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8225398)

---

