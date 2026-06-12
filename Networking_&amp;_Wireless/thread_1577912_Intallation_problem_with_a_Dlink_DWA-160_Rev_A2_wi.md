---
title: "Intallation problem with a Dlink DWA-160 Rev A2 wireless adapter"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by Bateleur on 2010-09-19
Hello all,

I just installed Ubuntu 10,04 with kernel 2.6.32-24-Generic and I'm  trying to nstall the adapter. I downloaded the linux driver from D-ling  and folloed the instructions in the readme:


I checked all the prerequisites:

Kernel-source Header

 ls -al /lib/modules/`uname -r`/build
lrwxrwxrwx 1 root root 40 2010-09-12 21:58 /lib/modules/2.6.32-24-generic/build -> /usr/src/linux-headers-2.6.32-24-generic

GNU toolchain
awk
build-essential

Then I issued the following command:

  [SIZE=2]]$ rpm[/SIZE][SIZE=2] -ivh --force-debian  ---nodeps otusdriver-3.2.0-17.i386.rpm[/SIZE]


[SIZE=2]I got the following error:[/SIZE]


[SIZE=2]
[/SIZE]
 Préparation...             ########################################### [100%]
   Otusdriver             ########################################### [100%]
Installation of Otus driver failed in Compile phase
 
exit: 87: Illegal number: -1
attention: %post(otusdriver-3.2.0-17.i386) scriptlet failed, exit status 2

I then trieg the Source code installation method:

  	 	 	 	p { margin-bottom: 0.21cm; }        [SIZE=2]]$ tar zxvf srcOtusLinux_3_2_0_X.tar.gz[/SIZE]
       [SIZE=2]]$ cd srcOtusLinux_3_2_0_X/OAL/Otus/Linux[/SIZE]
       [SIZE=2]]$ make RELEASE=<DIST>  TARGET=<ARCH>[/SIZE]
       [SIZE=2]]$ make RELEASE=<DIST>  TARGET=<ARCH> install[/SIZE]
 

 

  The <DIST> in RELEASE option is used to specify the Linux  distribution that can use different compile rule in different  distribution. There are 4 different <DIST> options.
   
       [SIZE=2]FC_1 [/SIZE][SIZE=2]: [/SIZE][SIZE=2]Fedora Core 1 only[/SIZE]
       [SIZE=2]MDV  [/SIZE][SIZE=2]: [/SIZE][SIZE=2]Mandriva[/SIZE]
       [SIZE=2]RH_9 [/SIZE][SIZE=2]: [/SIZE][SIZE=2]RedHat 9 only[/SIZE]
       [SIZE=2]FC     [/SIZE][SIZE=2]: [/SIZE][SIZE=2]Others[/SIZE]
 The <ARCH> in TARGET is used to specify the CPU type. It could be  either x86 or x86_64 which means 32bit or 64bit platform. There are 2  different <ARCH> options.
    [SIZE=2]x86:  32 Bit x86 platform[/SIZE]
       [SIZE=2]x86_64: 64 bit x86 platform[/SIZE]
 
and got the following:

~/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux$ sudo make RELEASE=FC TARGET=x86
/lib/modules/2.6.32-24-generic/build
/home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux
-I/lib/modules/2.6.32-24-generic/build/include -I/../../../80211Core -I  -I/../../../HalPlus/OTUS_FB50 -fomit-frame-pointer -O2 -Wall  -Wstrict-prototypes -pipe -DAMAC -DGCCK -DOFDM -DTXQ_IN_ISR  -DWLAN_HOSTIF=0 -DZM_USB_STREAM_MODE=1 -DZM_USB_TX_STREAM_MODE=0  -DZM_PCI_DMA_TEST=0 -DZM_LARGEPAYLOAD_TEST=0 -DZM_FW_LOOP_BACK=0  -DZM_LINUX_TPC=1 -DZM_HOSTAPD_SUPPORT -DZM_HALPLUS_LOCK
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.32-24-generic »
  CC [M]  /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/ccmd.o
In file included from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/usbdrv.h:35,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/oal_marc.h:18,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/cprecomp.h:7,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/ccmd.c:13:
/home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/zdcompat.h:82: error: conflicting types for ‘irqreturn_t’
include/linux/irqreturn.h:16: note: previous declaration of ‘irqreturn_t’ was here
In file included from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/usbdrv.h:35,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/oal_marc.h:18,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/cprecomp.h:7,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/ccmd.c:13:
/home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/zdcompat.h:85:1: warning: "IRQ_RETVAL" redefined
In file included from include/linux/interrupt.h:10,
                 from include/linux/netdevice.h:1071,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/oal_dt.h:19,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/cprecomp.h:6,
                 from /home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/ccmd.c:13:
include/linux/irqreturn.h:17:1: warning: this is the location of the previous definition
make[2]: *** [/home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux/../../../80211Core/ccmd.o] Erreur 1
make[1]: *** [_module_/home/phebert/Pilote_DWA_160/srcOtusLinux_3_2_0_17/OAL/Otus/Linux] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.32-24-generic »
make: *** [all] Erreur 2


Since I'm new to Linux... please help me on that !!

Many thanks in advance !!!
 		                   		  		  		  		  		  	   	
	 	
      	 	 		Bateleur 	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=1151537") 	 	 		[Send a private message to Bateleur]("http://ubuntuforums.org/private.php?do=newpm&u=1151537") 	 	 		[Send email to Bateleur]("http://ubuntuforums.org/sendmessage.php?do=mailmember&u=1151537") 	 	 	 		[Find More Posts by Bateleur]("http://ubuntuforums.org/search.php?do=finduser&u=1151537") 	 	 	[Add Bateleur to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=1151537") 	 	 	 
  	                 	 	 		 	           	 		       			 		 				       [CENTER]  
	[/CENTER]

---

