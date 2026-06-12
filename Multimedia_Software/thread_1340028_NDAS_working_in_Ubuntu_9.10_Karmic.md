---
title: "NDAS working in Ubuntu 9.10 Karmic"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Cuto on 2009-11-28
Starting from here [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)

Open Terminal and execute:

[FONT=Arial Black][COLOR=DarkSlateBlue]sudo su[/COLOR][/FONT]
[FONT=Arial Black][COLOR=DarkSlateBlue]apt-get install dpkg-dev debhelper gcc bzip2 fakeroot module-assistant libc6-dev build-essential
[/COLOR][/FONT][FONT=Arial Black][COLOR=DarkSlateBlue]apt-get install linux-headers-`uname -r`[/COLOR][/FONT]

Download files from [http://code.ximeta.com/dev/current/linux/ndas-1.1-24.tar.gz](http://code.ximeta.com/dev/current/linux/ndas-1.1-24.tar.gz)
and copy them in home/your user (home/cuto in my case)

Execute in the Terminal
[FONT=Arial Black][COLOR=DarkSlateBlue]tar zxf ndas-1.1-24.tar.gz

cd ndas-1.1-24[/COLOR][/FONT]

Now you have to apply patches from Tickets 839, 1105 and 1110. For that download from:


[http://code.ximeta.com/trac-ndas/attachment/ticket/839/Linux2.6.27.patch?format=raw ]("http://code.ximeta.com/trac-ndas/attachment/ticket/839/Linux2.6.27.patch?format=raw")

[http://code.ximeta.com/trac-ndas/attachment/ticket/839/Linux2.6.28.patch.zip?format=raw ]("http://code.ximeta.com/trac-ndas/attachment/ticket/839/Linux2.6.28.patch.zip?format=raw")
(you have to unzip this file to get the patch)

[http://code.ximeta.com/trac-ndas/attachment/ticket/1105/openSUSE.patch?format=raw ]("http://code.ximeta.com/trac-ndas/attachment/ticket/1105/openSUSE.patch?format=raw")

[http://code.ximeta.com/trac-ndas/attachment/ticket/1110/Linux2.6.31.patch?format=raw ]("http://code.ximeta.com/trac-ndas/attachment/ticket/1110/Linux2.6.31.patch?format=raw")

[http://code.ximeta.com/trac-ndas/attachment/ticket/1110/Linux2.6.31-1.patch?format=raw ]("http://code.ximeta.com/trac-ndas/attachment/ticket/1110/Linux2.6.31-1.patch?format=raw")

As I downloaded them with Firefox I had to copy then into the ndas-1.1-24 folder to apply the patch. I had some root issues and I copied them using the Terminal...

In the Terminal I executed:

[FONT=Arial Black][COLOR=DarkSlateBlue]cp /home/cuto/Downloads/*.patch /home/cuto/ndas-1.1-24
[/COLOR][/FONT]
Remenber that where I put "cuto" you have to put your user or the name of your folder...

Then, with the files in the ndas-1.1-24 folder and being there I executed:

[FONT=Arial Black][COLOR=DarkSlateBlue]patch -p1 <Linux2.6.27.patch
patch -p1 <Linux2.6.28.patch
patch -p0 <openSUSE.patch 
patch -p1 <Linux2.6.31.patch
patch -p1 <Linux2.6.31-1.patch[/COLOR][/FONT]

I downloaded the ndas-core.conf file (options) from here:
[http://code.ximeta.com/trac-ndas/attachment/ticket/1110/ndas-core.conf?format=raw ]("http://code.ximeta.com/trac-ndas/attachment/ticket/1110/ndas-core.conf?format=raw")
and I copied in /etc/modprobe.d using the Terminal:

[FONT=Arial Black][COLOR=DarkSlateBlue]cp /home/cuto/Downloads/ndas-core.conf /etc/modprobe.d[/COLOR][/FONT]

Remember that where I put "cuto" you have to put your user or the name of your folder...

Then I executed in the Terminal:

[FONT=Arial Black][COLOR=DarkSlateBlue]dpkg-buildpackage -rfakeroot
cd ..[/COLOR][/FONT]

[FONT=Arial Black][COLOR=DarkSlateBlue]dpkg -i ndas-modules-src_1.1-24_all.deb
m-a prepare
m-a auto-install ndas [FONT=Arial][COLOR=Black](you have to execute this command every time the kernel was updated...)[/COLOR][/FONT]
sudo dpkg -i ndasadmin_*.deb [/COLOR][/FONT]

... and followed here for the usage... [http://code.ximeta.com/trac-ndas/wiki/Usage](http://code.ximeta.com/trac-ndas/wiki/Usage) 
 
The unit is mounted in write mode and working fine!!! :popcorn:

Hope was useful for you... the key are the 5 patches applied in that order and with the particularity of the openSUSE.patch with the option "p0"...

:P

---

### Post by jaquim on 2009-12-01
Hi Cuto,

Thanks for the instructions on NDAS installation. Can you put here some other links to the files we should download?
Seems that ximeta site is down again....

Thanks.

---

### Post by hl1mnc on 2009-12-05
Hi Cuto,

Thanks for your instruction...

but in my case...

I have an error message after the last step of your instruction.

that is... "[FONT=Arial Black][COLOR=DarkSlateBlue]sudo dpkg -i ndasadmin_*.deb".

[/COLOR][/FONT]and can't proceed any more.

what can i do?

-----------------------------------------------------------------------------

the error message is...

Starting NDAS:FATAL: Error inserting ndas_core (/lib/modules/2.6.31-15-generic-pae/kernel/drivers/block/ndas/ndas_core.ko): Operation not permitted
 failed to load core module
 Report this problem with the following messages at [http://code.ximeta.com/cgi-bin/trac.cgi/newticket](http://code.ximeta.com/cgi-bin/trac.cgi/newticket)
==============================================================================
Linux version 2.6.31-15-generic-pae (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 16:12:10 UTC 2009
-rw-r--r-- 1 root root  47581 2009-12-05 12:59 /lib/modules/2.6.31-15-generic-pae/kernel/drivers/block/ndas/ndas_block.ko
-rw-r--r-- 1 root root 201845 2009-12-05 12:59 /lib/modules/2.6.31-15-generic-pae/kernel/drivers/block/ndas/ndas_core.ko
-rw-r--r-- 1 root root  55608 2009-12-05 12:59 /lib/modules/2.6.31-15-generic-pae/kernel/drivers/block/ndas/ndas_sal.ko
-rw-r--r-- 1 root root  49321 2009-12-05 12:59 /lib/modules/2.6.31-15-generic-pae/kernel/drivers/block/ndas/ndas_scsi.ko

---

### Post by Cuto on 2009-12-05
jaquim, seems to be operational again...  ;-D

---

### Post by Cuto on 2009-12-05
hl1mnc, sorry but I cannot help you... no idea... that worked for me...

---

### Post by cyann.olsimar on 2009-12-05
hi from france (not very good in english) 

i noticed a a little mistake in cuto's post

you should do cp/home/cuto/Downloads/ndas-core.conf /etc/modprobe.d/ 

/ at the end of line was missing

also you may have to modify the file /etc/modprobe.d/ndas-core.conf 
i had to change the line options ndas-core ndas_dev='''wlan0'''

into

options ndas-core ndas_dev=eth0

because my network uses eth0 instaed of wlan0

works fine since
:P:P

---

### Post by stevenjoes on 2009-12-05
I have the same error as hl1mnc, can anyone help. I'm so close to been windows free! this is my last hurdle! :p

---

### Post by Cuto on 2009-12-06
Cyann, en fait, la première fois que j'ai eu success avec NDAS avec ubuntu 8.10 c'était grace au forum d'ubuntu en France...  ;)

Merci de ta correction... :P

In the last days I have updated the kernel to 2.6.31.16... an I executed the command "m-a auto-install ndas" and everything is "fine"... I put "fine" in brakets because I still have some issues:

- I have not succeded yet in mounting the unit in another laptop, an Acer AspireOne... not a lot of time to try... maybe today... Installation was fine... just problems mounting the unit... just one step more for glory... :P
- I can just can mount the ndas unit as read/write ("w" parametter))... when I try as read mode I got an error message...
- If I try to copy big files (movies)... the copy crashes around tranfering 125 Mb... and the ndas unit is over... I have to reformat it again... which is not evident... :mad:. I just copy into the unit using usb... and just read from wireless... paying attention to have everything backed up in an external hard disk...

... and I have a couple of things more to abandon Windows for ever... my two Garmin gps... ):P... trying with Wine... :popcorn:

---

### Post by hl1mnc on 2009-12-08
thank you very much. Cuto and Cyann.

My issue is solved.

Edited "eth0" to "eth1" in option file, and it works perfectly.

The Key was my network environment.

Merci beaucoup, Cyann.

bye the way, I have learned Langue Francais three years in high school.

2 hours a week, "THREE" years for god's sake.

But...now...

Bon jour, J'aime Toi, Merci beaucoup...

That's all I can remember about Francais. :D

oh! one more...

Sophie Marceau!!!![U]

Anyway, Thank you very much.

[/U]from Republic of Korea.

---

### Post by Cuto on 2009-12-08
Nice to see that is working!!!

In my "file" I have a new line to check... and is the size of the cluster I define when formating the NTFS hard disk... when transferring big files with wireless...

My favourite sentence in French is "voulez vous coucher avec moi, ce soir"... jajjaaa... :P

Keep you informed... ;)

---

### Post by jaquim on 2009-12-08
Hi all !

I was just following the steps on Cuto's instructions, but I can't solve this problem:

On terminal I get this warning when trying to register the ndas drive: (followed instrutions on [http://code.ximeta.com/trac-ndas/wiki/Usage](http://code.ximeta.com/trac-ndas/wiki/Usage))

Failed to open /dev/ndas
Check NDAS device file exists, driver module is loaded and started by administration.

Can anyone help me solve this?

Thanks in advance

EDIT: Found what was wrong.... Bad installation of the ndasadmin.deb file. Reinstalled and it's ok now :)

[hl1mnc]("http://ubuntuforums.org/member.php?u=971350"), have you tryed to start all over again? Worked for me.

Cuto, do you have news about the problem copying big files?

Thanks team

---

### Post by hl1mnc on 2009-12-08
:D

The sentence will be my favorite one, from now on.

^^

---

### Post by Cuto on 2009-12-10
hl1mnc, I have not progressed with big files as I had not a lot of time to do some testing... you know... 
 
What I am going to try is to format again the hard disk in NTFS format with higher cluster size (64k)... and I will try again... but apparently there are not a lot of Linux tools for that... and I will try with Windows Disk Partitioner that I have in my Windows XP laptop together with Ubuntu...
 
I will report on results...  ;-D

---

### Post by Cuto on 2009-12-14
As promised, I report on results of my checking...
 
Well, I formated again the external hard drive as NTFS but now with a cluster size of 64k. I did it with one partition utility in Windows. Again I had problems but now it is possible to recover the disk using chkdsk /f... in Windows... I copied big files (up to 1.2 Gb) and also a lot of files (2gb of pictures) and sometimes is working properly... but sometimes not... After some google research I discover that NTFS is "purely" Windows and that to create and maintain such units it is necessary (recommendable) to do it from Windows... and in addition I also discovered that the wireless router configuration can also compromise the transfers...
 
Conclusion... one step forward... but two steps back in abandoning Windows for ever... as in addition, I continue with my other open "files" to update and maintain my Garmin Nuvi 660 and my Garmin Forerunner 405 just using Ubuntu...
 
To be continued... ;)

---

### Post by hellerro on 2010-01-01
Hi, hope somebody can help me. I'm encountering the following problem:

roger@Study:~/ndas-1.1-24$ sudo dpkg-buildpackage -rfakeroot
dpkg-buildpackage: Warnung: verwende ein root-werde-Befehl obwohl bereits root
dpkg-buildpackage: setze CFLAGS auf Standardwert: -g -O2
dpkg-buildpackage: setze CPPFLAGS auf Standardwert: 
dpkg-buildpackage: setze LDFLAGS auf Standardwert: -Wl,-Bsymbolic-functions
dpkg-buildpackage: setze FFLAGS auf Standardwert: -g -O2
dpkg-buildpackage: setze CXXFLAGS auf Standardwert: -g -O2
dpkg-buildpackage: Quellpaket ndas
dpkg-buildpackage: Quellversion 1.1-24
dpkg-buildpackage: Quellen geändert durch Ilgu Hong <ighong@ximeta.com>
dpkg-buildpackage: Host-Architektur i386
 fakeroot debian/rules clean
dh_testdir
#dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Betrete Verzeichnis '/home/roger/ndas-1.1-24'
Makefile:88: *** /usr/src/linux is not a valid kernel path.  Schluss.
make[1]: Verlasse Verzeichnis '/home/roger/ndas-1.1-24'
make: [clean] Fehler 2 (ignoriert)
dh_clean
 dpkg-source -b ndas-1.1-24
dpkg-source: Information: verwende Quellformat »1.0«
dpkg-source: Warnung: Quellverzeichnis »ndas-1.1-24« lautet nicht <Quellpaket>-<UpstreamVersion> »ndas-1.1«
dpkg-source: Information: baue ndas in ndas_1.1-24.tar.gz
dpkg-source: Information: baue ndas in ndas_1.1-24.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here command to compile/build the package.
/usr/bin/make ndas-admin
make[1]: Betrete Verzeichnis '/home/roger/ndas-1.1-24'
Makefile:88: *** /usr/src/linux is not a valid kernel path.  Schluss.
make[1]: Verlasse Verzeichnis '/home/roger/ndas-1.1-24'
make: *** [build-arch-stamp] Fehler 2
dpkg-buildpackage: Fehler: debian/rules build gab Fehler-Exitstatus 2

roger@Study:~/ndas-1.1-24$ cd ..

roger@Study:~$ sudo dpkg -i ndas-modules-src_1.1-24_all.deb
dpkg: Fehler beim Bearbeiten von ndas-modules-src_1.1-24_all.deb (--install):
 Kann auf das Archiv nicht zugreifen: No such file or directory
Fehler traten auf beim Bearbeiten von:
 ndas-modules-src_1.1-24_all.deb


Any ideas what I'm doing wrong? Any help would be appreciated.

Thank you

---

### Post by riteman on 2010-01-01
Cuto

I got a NetDisk for Xmas  and had big trouble installing it under Ubuntu 9.10 until I found your excellent hints. Following them did the job and I now have a 1 TB NetDisk which is reachable from my Linux PC.

Thanks a lot for sharing your experience !

---

### Post by Cuto on 2010-01-04
My pleasure!

;-D

---

### Post by Yow-El on 2010-01-23
This is really a very good and very clear tutorial... Thanks Cuto!:popcorn:

Unfortunately the building of the package failed when i executed:

> [FONT=Arial Black][COLOR=DarkSlateBlue]m-a auto-install ndas[/COLOR][/FONT]

This is the log file the terminal gave me:

> [FONT=Arial Black][COLOR=DarkSlateBlue] &#9474; (/usr/src/modules/ndas/ndas_core.o) is not supported                
 &#9474; make[4]: *** [/usr/src/modules/ndas/ndas_core.o] Fout 1                         
 &#9474; make[3]: *** [_module_/usr/src/modules/ndas] Fout 2                             
 &#9474; make[3]: Map '/usr/src/linux-headers-2.6.31-17-generic' wordt verlaten     
 &#9474; make[2]: *** [/usr/src/modules/ndas/ndas_sal.ko] Fout 2                    
 &#9474; make[2]: Map '/usr/src/modules/ndas' wordt verlaten                        
 &#9474; make[1]: *** [binary-modules] Fout 2                                       
 &#9474; make[1]: Map '/usr/src/modules/ndas' wordt verlaten                        
 &#9474; make: *** [kdist_build] Fout 2 [/COLOR][/FONT]

Perhaps you (or someone else on this forum) knows what this means and knows how to solve this. :)

Thanks!

---

### Post by toppino on 2010-01-31
Finally thanks to this I could see Jude disc in my PC with Ubuntu 9.10, I wanted to know if you have improved file transfers, since it does not work very well ... what's new
Thank you very much

---

### Post by Andrea9 on 2010-02-28
> **Cuto said:**
> 

...


[FONT=Arial Black][COLOR=DarkSlateBlue] m-a auto-install ndas [FONT=Arial][COLOR=Black](you have to execute this command every time the kernel was updated...)

[/COLOR][/FONT][/COLOR][/FONT]

Hi,

I have a problem in this step. kernel 2.6.31-20-generic

> Build of the package ndas-modules-src failed! How do you wish to proceed? 
     VIEW     Examine the build log file
     CONTINUE Skip and continue with the next operation 
     STOP     Stop processing the build commands


LOG:
```
rm -f build-stamp configure-stamp
/usr/bin/make clean
make[1]: ingresso nella directory «/usr/src/modules/ndas»
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin
rm -rf /usr/src/modules/ndas/ndasadmin /usr/src/modules/ndas/admin/ndasadmin.o /usr/src/modules/ndas/ndas_sal.ko /usr/src/modules/ndas/ndas_core.ko /usr/src/modules/ndas/ndas_block.ko /usr/src/modules/ndas/ndas_scsi.ko /usr/src/modules/ndas/ndas_emu.ko /usr/src/modules/ndas/nd.ko sal/debug.o sal/io.o sal/libc.o sal/mem.o sal/net.o sal/sal.o sal/sync.o sal/thread.o sal/time.o block/block24.o block/block26.o block/ctrldev.o block/ops.o block/procfs.o scsi/ctrldev.o scsi/ndas_scsi.o scsi/procfs.o /usr/src/modules/ndas/ndas.o
find . \( -name 'ndas_*.o' -o -name '*.ko' -o -name '.*.cmd' -o -name '.*.d' -o -name '*.mod.c' -o -name '*.mod.o' -o -name '*.symvers' \) -type f -print | xargs rm -f
rm -rf '.tmp_versions'
rm -rf '.kernel.mk'
make[1]: uscita dalla directory «/usr/src/modules/ndas»
dh_clean
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: ingresso nella directory «/usr/src/modules/ndas»
rm -f build-stamp configure-stamp
/usr/bin/make clean
make[2]: ingresso nella directory «/usr/src/modules/ndas»
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin
rm -rf /usr/src/modules/ndas/ndasadmin /usr/src/modules/ndas/admin/ndasadmin.o /usr/src/modules/ndas/ndas_sal.ko /usr/src/modules/ndas/ndas_core.ko /usr/src/modules/ndas/ndas_block.ko /usr/src/modules/ndas/ndas_scsi.ko /usr/src/modules/ndas/ndas_emu.ko /usr/src/modules/ndas/nd.ko sal/debug.o sal/io.o sal/libc.o sal/mem.o sal/net.o sal/sal.o sal/sync.o sal/thread.o sal/time.o block/block24.o block/block26.o block/ctrldev.o block/ops.o block/procfs.o scsi/ctrldev.o scsi/ndas_scsi.o scsi/procfs.o /usr/src/modules/ndas/ndas.o
find . \( -name 'ndas_*.o' -o -name '*.ko' -o -name '.*.cmd' -o -name '.*.d' -o -name '*.mod.c' -o -name '*.mod.o' -o -name '*.symvers' \) -type f -print | xargs rm -f
rm -rf '.tmp_versions'
rm -rf '.kernel.mk'
make[2]: uscita dalla directory «/usr/src/modules/ndas»
dh_clean
dh_clean: cannot read debian/control: Nessun file o directory

make[1]: [kdist_clean] Errore 1 (ignorato)
for templ in /usr/src/modules/ndas/debian/ndas-modules-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.31-20-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.31-20-generic/g ;s/#KVERS#/2.6.31-20-generic/g ; s/_KVERS_/2.6.31-20-generic/g ; s/##KDREV##/2.6.31-20.57/g ; s/#KDREV#/2.6.31-20.57/g ; s/_KDREV_/2.6.31-20.57/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testroot
dh_clean -k
dh_installdirs lib/modules/2.6.31-20-generic/kernel/drivers/block/ndas
# Build the module
/usr/bin/make NDAS_KERNEL_PATH=/usr/src/linux-headers-2.6.31-20-generic NDAS_KERNEL_VERSION=2.6.31-20-generic ndas-kernel
make[2]: ingresso nella directory «/usr/src/modules/ndas»
Invoking make againt the kernel at /usr/src/linux-headers-2.6.31-20-generic
/usr/bin/make -C /usr/src/linux-headers-2.6.31-20-generic \
        SUBDIRS=/usr/src/modules/ndas \
        KBUILD_VERBOSE=1 \
        ndas_root=/usr/src/modules/ndas \
        modules
make[3]: ingresso nella directory «/usr/src/linux-headers-2.6.31-20-generic»
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /usr/src/modules/ndas/.tmp_versions ; rm -f /usr/src/modules/ndas/.tmp_versions/*
/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/ndas
  gcc -Wp,-MD,/usr/src/modules/ndas/block/.block24.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-headers-2.6.31-20-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -DMODULE -DLINUX -I/usr/src/modules/ndas/inc -DDEBUG -D_X86  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(block24)"  -D"KBUILD_MODNAME=KBUILD_STR(ndas_block)"  -c -o /usr/src/modules/ndas/block/.tmp_block24.o /usr/src/modules/ndas/block/block24.c
  gcc -Wp,-MD,/usr/src/modules/ndas/block/.block26.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude  -I/usr/src/linux-headers-2.6.31-20-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -DMODULE -DLINUX -I/usr/src/modules/ndas/inc -DDEBUG -D_X86  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(block26)"  -D"KBUILD_MODNAME=KBUILD_STR(ndas_block)"  -c -o /usr/src/modules/ndas/block/.tmp_block26.o /usr/src/modules/ndas/block/block26.c
/usr/src/modules/ndas/block/block26.c: In function ‘nbio_alloc’:
/usr/src/modules/ndas/block/block26.c:125: warning: unused variable ‘data’
/usr/src/modules/ndas/block/block26.c: In function ‘nblk_request_proc’:
/usr/src/modules/ndas/block/block26.c:485: error: implicit declaration of function ‘blkdev_dequeue_request’
/usr/src/modules/ndas/block/block26.c:494: error: ‘struct request’ has no member named ‘nr_sectors’
make[4]: *** [/usr/src/modules/ndas/block/block26.o] Errore 1
make[3]: *** [_module_/usr/src/modules/ndas] Errore 2
make[3]: uscita dalla directory «/usr/src/linux-headers-2.6.31-20-generic»
make[2]: *** [/usr/src/modules/ndas/ndas_sal.ko] Errore 2
make[2]: uscita dalla directory «/usr/src/modules/ndas»
make[1]: *** [binary-modules] Errore 2
make[1]: uscita dalla directory «/usr/src/modules/ndas»
make: *** [kdist_build] Errore 2
```

Thanks for help,

Andrea

---

### Post by Andrea9 on 2010-02-28
After install kernel-src I'm in the next step...

dpkg -i ndasadmin_1.x-xxx_<arch>.deb 

but


```
(Lettura del database... 163072 file e directory attualmente installati.)
Preparativi per sostituire ndasadmin v.1.1-24 (utilizzando .../ndas/ndasadmin_1.1-24_i386.deb)...
Stopping NDAS: synced umounted synced stopped modules removed
Estrazione del sostituto di ndasadmin...
Configurazione di ndasadmin (1.1-24)...
update-rc.d: warning: /etc/init.d/ndas missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Starting NDAS:FATAL: Error inserting ndas_core (/lib/modules/2.6.31-20-generic/kernel/drivers/block/ndas/ndas_core.ko): Operation not permitted
 failed to load core module
 Report this problem with the following messages at http://code.ximeta.com/cgi-bin/trac.cgi/newticket
==============================================================================
Linux version 2.6.31-20-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010
-rw-r--r-- 1 root root  47581 2010-02-28 12:31 /lib/modules/2.6.31-20-generic/kernel/drivers/block/ndas/ndas_block.ko
-rw-r--r-- 1 root root 201845 2010-02-28 12:31 /lib/modules/2.6.31-20-generic/kernel/drivers/block/ndas/ndas_core.ko
-rw-r--r-- 1 root root  55608 2010-02-28 12:31 /lib/modules/2.6.31-20-generic/kernel/drivers/block/ndas/ndas_sal.ko
-rw-r--r-- 1 root root  49330 2010-02-28 12:31 /lib/modules/2.6.31-20-generic/kernel/drivers/block/ndas/ndas_scsi.ko
gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

Feb 28 12:35:59 NB-A9 kernel: [  143.528133] NET: Unregistered protocol family 29
Feb 28 12:37:01 NB-A9 kernel: [  205.648051] CE: hpet increasing min_delta_ns to 15000 nsec
Feb 28 12:41:15 NB-A9 kernel: [  459.455086] SN|1|sal_net_init|/usr/src/modules/ndas/sal/net.c:467|ing|modprobe,0:2:39.113,3828:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455101] NET: Registered protocol family 29
Feb 28 12:41:15 NB-A9 kernel: [  459.455109] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:429|ing dev=f70f5c00(lo) event=5|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455121] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:429|ing dev=f70f5c00(lo) event=1|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455133] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:439|net change handler is not set|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455143] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:429|ing dev=f6955000(eth0) event=5|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455154] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:429|ing dev=f6955000(eth0) event=1|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455165] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:439|net change handler is not set|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455176] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:429|ing dev=f65e6800(eth2) event=5|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455186] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:429|ing dev=f65e6800(eth2) event=1|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455197] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:439|net change handler is not set|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455208] SN|1|v_notifiee|/usr/src/modules/ndas/sal/net.c:429|ing dev=f69c5400(vboxnet0) event=5|modprobe,0:2:39.113,3752:1
Feb 28 12:41:15 NB-A9 kernel: [  459.455220] SN|1|sal_net_init|/usr/src/modules/ndas/sal/net.c:548|ed|modprobe,0:2:39.113,3828:1
Feb 28 12:41:15 NB-A9 kernel: [  459.485948] 
Feb 28 12:41:15 NB-A9 kernel: [  459.485950] ndas: Initializing NDAS driver version 1.1.24
Feb 28 12:41:15 NB-A9 kernel: [  459.486192] ndas: Setting max request size to 64kbytes
Feb 28 12:41:15 NB-A9 kernel: [  459.486244] ndas: fail to register network interfaces.
Feb 28 12:41:15 NB-A9 kernel: [  459.633176] NET: Unregistered protocol family 29
==============================================================================
invoke-rc.d: initscript ndas, action "start" failed.
dpkg: errore nell'elaborare ndasadmin (--install):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1
Elaborazione dei trigger per ureadahead...
Si sono verificati degli errori nell'elaborazione:
 ndasadmin

```

:(

thanks for help

---

### Post by Andrea9 on 2010-02-28
RESOLVED!!!!! :popcorn:



- I've installed kernel sources

- Reinstalled all

-I've configured ndas-core.conf with my interface (and after copied in /etc/modprobe.d/)


Thanks!!!!

---

### Post by dkall on 2010-03-17
Hi, 
I have also a problem with the NDAS, and would appreciate any help I can get. 

I'm running ubuntu 9.10, X64, and have followed the steps in:

[LIST]
[*][http://code.ximeta.com/trac-ndas/ticket/839](http://code.ximeta.com/trac-ndas/ticket/839)
[*][http://code.ximeta.com/trac-ndas/ticket/1110](http://code.ximeta.com/trac-ndas/ticket/1110)
[*][http://code.ximeta.com/trac-ndas/ticket/1113](http://code.ximeta.com/trac-ndas/ticket/1113)
[/LIST]

I deleted all broken installations by
[INDENT][I]sudo dpkg -r ndasadmin
sudo dpkg -r ndas-modules-`uname -r`
sudo dpkg -r ndas-modules-src
sudo rm /usr/src/ndas*[/I][/INDENT]
and then made a new install by:
[INDENT][I]sudo dpkg -i ndas-modules-src_1.1-24_all.deb
sudo m-a prepare
sudo m-a auto-install ndas
sudo dpkg -i ndasadmin_1.1-24_amd64.deb[/I][/INDENT]
Everything looks fine during installation, but when I try to register my disk, I get this:
*Failed to open /dev/ndas Check NDAS device file exists, driver module is loaded and started by administration tool*

Any ideas?

---

### Post by Cuto on 2010-05-01
I confirm is also working in Ubuntu 10.4

:popcorn:

---

### Post by alecs123 on 2010-06-17
do you know if this setup will work on Ubuntu 10.04 x64?
I need it, tryed with the ndasadmin (but never thought on the 64 bit version until now).
I hope that was the problem but need confirmation that it works on the 64 bit environment
thanks

---

### Post by cuzco_it on 2010-07-26
Hi everybody.

I'm a brand new Linux user.. I've installed Ubuntu 10.4 32bit for the first time 3 days ago. Now I'm trying to understand how to configure all of my hardware... Everything looks easy... Apart from my IOCELL NETDISK!!

I tried to follow your guide... but all download links from ximeta appears to be down.

Any other location I can go to get those files?

Please help me!!! Thanks in advance!!!

---

### Post by BlueColibri on 2011-05-17
I have a problem i can't compile the source code I use Ubuntu 11.04 natty this is the log Output anybody any sugestion's 

To the above the files are found here to Compile it

[http://code.ximeta.com/]("http://code.ximeta.com/")
[http://linux.ximeta.com:8000/trac/ticket/1110]("http://linux.ximeta.com:8000/trac/ticket/1110")
[http://linux.ximeta.com:8000/trac/ticket/839]("http://linux.ximeta.com:8000/trac/ticket/839")
[http://linux.ximeta.com:8000/trac/ticket/1105](http://linux.ximeta.com:8000/trac/ticket/1105)



rm -f build-stamp configure-stamp
/usr/bin/make clean
make[1]: Entering directory `/usr/src/modules/ndas'
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin
rm -rf /usr/src/modules/ndas/ndasadmin /usr/src/modules/ndas/admin/ndasadmin.o /usr/src/modules/ndas/ndas_sal.ko /usr/src/modules/ndas/ndas_core.ko /usr/src/modules/ndas/ndas_block.ko /usr/src/modules/ndas/ndas_scsi.ko /usr/src/modules/ndas/ndas_emu.ko /usr/src/modules/ndas/nd.ko sal/debug.o sal/io.o sal/libc.o sal/mem.o sal/net.o sal/sal.o sal/sync.o sal/thread.o sal/time.o block/block24.o block/block26.o block/ctrldev.o block/ops.o block/procfs.o scsi/ctrldev.o scsi/ndas_scsi.o scsi/procfs.o /usr/src/modules/ndas/ndas.o
find . \( -name 'ndas_*.o' -o -name '*.ko' -o -name '.*.cmd' -o -name '.*.d' -o -name '*.mod.c' -o -name '*.mod.o' -o -name '*.symvers' \) -type f -print | xargs rm -f
rm -rf '.tmp_versions'
rm -rf '.kernel.mk'
make[1]: Leaving directory `/usr/src/modules/ndas'
dh_clean
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/ndas'
rm -f build-stamp configure-stamp
/usr/bin/make clean
make[2]: Entering directory `/usr/src/modules/ndas'
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-kernel
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/conffiles
rm -f /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL/control
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin/CONTROL
rm -fd /usr/src/modules/ndas/ipkg/ndas-admin
rm -rf /usr/src/modules/ndas/ndasadmin /usr/src/modules/ndas/admin/ndasadmin.o /usr/src/modules/ndas/ndas_sal.ko /usr/src/modules/ndas/ndas_core.ko /usr/src/modules/ndas/ndas_block.ko /usr/src/modules/ndas/ndas_scsi.ko /usr/src/modules/ndas/ndas_emu.ko /usr/src/modules/ndas/nd.ko sal/debug.o sal/io.o sal/libc.o sal/mem.o sal/net.o sal/sal.o sal/sync.o sal/thread.o sal/time.o block/block24.o block/block26.o block/ctrldev.o block/ops.o block/procfs.o scsi/ctrldev.o scsi/ndas_scsi.o scsi/procfs.o /usr/src/modules/ndas/ndas.o
find . \( -name 'ndas_*.o' -o -name '*.ko' -o -name '.*.cmd' -o -name '.*.d' -o -name '*.mod.c' -o -name '*.mod.o' -o -name '*.symvers' \) -type f -print | xargs rm -f
rm -rf '.tmp_versions'
rm -rf '.kernel.mk'
make[2]: Leaving directory `/usr/src/modules/ndas'
dh_clean
for templ in /usr/src/modules/ndas/debian/ndas-modules-_KVERS_.postinst /usr/src/modules/ndas/debian/ndas-modules-_KVERS_.postinst.backup /usr/src/modules/ndas/debian/ndas-modules-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.38-9-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.38-9-generic/g ;s/#KVERS#/2.6.38-9-generic/g ; s/_KVERS_/2.6.38-9-generic/g ; s/##KDREV##/2.6.38-9.43/g ; s/#KDREV#/2.6.38-9.43/g ; s/_KDREV_/2.6.38-9.43/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testroot
dh_clean -k
dh_clean: dh_clean -k is deprecated; use dh_prep instead
dh_installdirs lib/modules/2.6.38-9-generic/kernel/drivers/block/ndas
# Build the module
/usr/bin/make NDAS_KERNEL_PATH=/usr/src/linux-headers-2.6.38-9-generic NDAS_KERNEL_VERSION=2.6.38-9-generic ndas-kernel
make[2]: Entering directory `/usr/src/modules/ndas'
Invoking make againt the kernel at /usr/src/linux-headers-2.6.38-9-generic
/usr/bin/make -C /usr/src/linux-headers-2.6.38-9-generic \
		SUBDIRS=/usr/src/modules/ndas \
		KBUILD_VERBOSE=1 \
		ndas_root=/usr/src/modules/ndas \
		modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.38-9-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/src/modules/ndas/.tmp_versions ; rm -f /usr/src/modules/ndas/.tmp_versions/*
/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/ndas
  gcc -Wp,-MD,/usr/src/modules/ndas/block/.block24.o.d  -nostdinc -isystem /usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/include  -I/usr/src/linux-headers-2.6.38-9-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DMODULE -DLINUX -I/usr/src/modules/ndas/inc -DDEBUG -D_X86  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(block24)"  -D"KBUILD_MODNAME=KBUILD_STR(ndas_block)" -c -o /usr/src/modules/ndas/block/.tmp_block24.o /usr/src/modules/ndas/block/block24.c
  if [ "-pg" = "-pg" ]; then if [ /usr/src/modules/ndas/block/block24.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-2.6.38-9-generic/scripts/recordmcount "/usr/src/modules/ndas/block/block24.o"; fi; fi;
  gcc -Wp,-MD,/usr/src/modules/ndas/block/.block26.o.d  -nostdinc -isystem /usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/include  -I/usr/src/linux-headers-2.6.38-9-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DMODULE -DLINUX -I/usr/src/modules/ndas/inc -DDEBUG -D_X86  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(block26)"  -D"KBUILD_MODNAME=KBUILD_STR(ndas_block)" -c -o /usr/src/modules/ndas/block/.tmp_block26.o /usr/src/modules/ndas/block/block26.c
/usr/src/modules/ndas/block/block26.c: In function ‘nblk_request_proc’:
/usr/src/modules/ndas/block/block26.c:480:13: error: implicit declaration of function ‘blkdev_dequeue_request’
/usr/src/modules/ndas/block/block26.c:489:39: error: ‘struct request’ has no member named ‘nr_sectors’
/usr/src/modules/ndas/block/block26.c:499:2: error: implicit declaration of function ‘blk_fs_request’
/usr/src/modules/ndas/block/block26.c: At top level:
/usr/src/modules/ndas/block/block26.c:200:1: warning: ‘_calc_checksum’ defined but not used
/usr/src/modules/ndas/block/block26.c:213:1: warning: ‘_dump_ioreq’ defined but not used
make[4]: *** [/usr/src/modules/ndas/block/block26.o] Error 1
make[3]: *** [_module_/usr/src/modules/ndas] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.38-9-generic'
make[2]: *** [/usr/src/modules/ndas/ndas_sal.ko] Error 2
make[2]: Leaving directory `/usr/src/modules/ndas'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/ndas'
make: *** [kdist_build] Error 2

---

### Post by bcatt on 2011-05-30
This works great for me in Lucid, however there's a few things I'd like to figure out to make usage a bit more convenient:

1. When I start/restart my computer, the disk will show up in my places menu, but programs (banshee in particular...I only have music on the drive atm, so don't actually know if it applies to all applications) can't seem to access it until I have opened the drive with nautilus (I only have to do this once each time I start the computer, not each time I try to access the drive)...anyone know how I can fix this?

2. I dual boot with whinedoze, and after I have booted into whinedoze, the next time I boot into Ubuntu, I have to do "[FONT=Arial Black][COLOR=DarkSlateBlue]m-a auto-install ndas[FONT=Verdana][COLOR=Black]" before the drive will show up in my places menu...can I set this up to happen automatically, or even do it through a custom application launcher on my panel?

Many thanks in advance for any tips :D
[/COLOR][/FONT][/COLOR][/FONT]

---

### Post by bcatt on 2011-05-30
Also, the problem with the links in the original post can be fixed by adding :8000 after the domain part of the address, so
ximeta.com/trac
becomes
ximeta.com:8000/trac

tickets:
[http://linux.ximeta.com:8000/trac/ticket/839](http://linux.ximeta.com:8000/trac/ticket/839) (this has the ndas_1.1-24.tar.gz as well as two patches attached)
[http://linux.ximeta.com:8000/trac/ticket/1105](http://linux.ximeta.com:8000/trac/ticket/1105) (third patch attached)
[http://linux.ximeta.com:8000/trac/ticket/1110](http://linux.ximeta.com:8000/trac/ticket/1110) (last two patches and ndas-core.conf attached)

---

### Post by hobbystas on 2011-06-29
I'm trying to install the ndas software like described here but i'm missing the ndas-core.conf file and the ximeta site is down. I mean really down. The tickets are not accessible at this moment. Is there anyone perhaps who has a copy of it and wouldn't mind to upload it here?

Thanks in advance.

EDIT: Don't bother, the site is back online now, got the file from there.

---

