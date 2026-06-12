---
title: "How-To: Setup IOCELL's NetDISK NDAS 351UNE"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by gamez on 2013-06-02
Hello,

I tested the following yesterday and today (June 02, 2013) under Kubuntu 12.04 (x86 32 Bit). It should help you set up your NetDISK 351UNE NDAS drive. At the time of writing the [NDAS4LINUX driver]("https://github.com/iocellnetworks/ndas4linux/tree/master/3.8.2") was in version 3.8.2. Please check out the related [documentation]("https://github.com/iocellnetworks/ndas4linux/tree/master/3.8.2/doc").

You may want to create the follwing 2 scripts in your home directory; DO NOT EXECUTE THEM as such, please read the explanations first.

**ndas-start.sh**
```
#!/bin/sh

# More doc here: https://github.com/iocellnetworks/ndas4linux/tree/master/3.8.2/doc

# First part: install git and download github
# sudo apt-get install git-core
# git clone git://github.com/iocellnetworks/ndas4linux.github

# Second part: compile NDAS driver and start is
# cd build_x86_linux/ndas-3.8.2.x86/
# make
# sudo make install
# sudo /etc/init.d/ndas start

# Third part: mount ndas drive
# call this script from /etc/rc.local
cat /proc/ndas/devs
ndasadmin register sssss-sssss-sssss-sssss-wwwww -n NetDisk1         
cat /proc/ndas/devices/NetDisk1/slots
ndasadmin enable -s 1 -o w
ls /dev/ndas-*
mount -t ntfs /dev/ndas-44726619-0p2 /media/NDAS

```

**ndas-stop.sh:**
```
#!/bin/sh
# make a symbolic link to this file in /etc/rc0.d/S32ndas-stop

umount /media/NDAS
ndasadmin disable -s 1
ndasadmin unregister -n NetDisk1

```

Explanations:

1-1) The commented lines (part one and two in the 1st sript) explain how to download the source of the NDAS4LINUX driver modules, and how to compile them. Create a specific installation directory and run the commands from there. You can uncomment the lines, and run the script, but it is probably preferable that you execute the commands one at a time to see if everything works or if you get errors.
Obviously, you need to do these first parts only once for your Ubuntu system, afterwards the ndas module will be loaded on each startup.

1-2) The lower part of **ndas-start.sh** register, enable and mount the NDAS drive to a directory of your choice (/media/NDAS in my case) that you will have to create beforehand. You actually don't really need the **cat** and **ls** commands (you may comment them out later), they just help you to verify that **ndasadmin** does its job. Note that the register command expects 5 (!) quintuplets: 4 for the serial, followed by the write access code (see bottom of the NDAS enclosure). Please enter the code valid for your drive.

1-3) After enabling the slot (which should always be 1) you should check the ndas-* devices in /dev. In my case there were 4 of them, but only the one with an suffix of -0p2 was mountable. The installed disk drive was a Seagate Barracuda ST3000DM001, that I already had GPT-partitioned and NTFS formatted before under Windows 7. I still have to check how to do this under Ubuntu Linux.

1-4) After you have verified that the **ndas-start.sh** correctly enables and mounts your drive, you may want to run the script automatically at each startup by adding a line ```
sh /home/<your-name>/ndas-start.sh
``` to your **/etc/rc.local**.

1-5) After reboot, check at least once the properties of the mount directory (eg. /media/NDAS). If it shows the expected disk size of your NDAS, everything should be working fine.

2-4) The second script does everything in reverse order to unmount, disable and unregister your drive. You can put a link to the script in the directory **/etc/rc0.d/** in order to execute it during shutdown. Without unmounting the drive, my Ubuntu wouldn't reboot. Chose the right prefix for the link (S32 works for me) so that the script is executed before all networking services are stopped.

Let me know how it goes for you.

Cheers, g.

---

### Post by manlug on 2013-08-13
Ubuntu 13.04 x86_64
kernel 3.8.0-27 generic


> sudo apt-get install git
git clone [http://github.com/iocellnetworks/ndas4linux]](http://github.com/iocellnetworks/ndas4linux]) ~/git/ndas

the directory build_... not exist in repository it is create with
>  ~/git/ndas/make linux-rel
or
> ~/git/ndas/make linux64-rel
or
> .. (more options)

> cd ~/git/ndas/3.8.0/build_x86_64_linux/ndas-3.8.0.x86_64/
make
sudo make install
sudo /etc/init.d/ndas start

> sudo ndasadmin register sssss-sssss-sssss-sssss-wwwww -n NetDisk1         

sudo ndasadmin enable -s 1 -o w

[waiting ....] it working .. ubuntu show in the panel for mount 

and thank you, you are solved my problem.

---

### Post by electroken on 2014-07-01
Hello, I have obtained some IOCELL Netdisk NDAS 352UNE which I assume are dual drive versions of the 351UNE. I have found that the software which has been in development by IOCELL has now been put in public domain with hopes that somebody in the linux community will take over from there. I am hoping this can be made into some software package which I will be able to download and have install from the software depository where I seem to get all my other linux programs.
I am not necessarily a noob, but in linux command line I am not comfortable at all. I have used dos commands and in Amiga dos I did pretty well with things, but that was a long time ago and my expertise if severly lacking now. I realize that in linux, like in using Amiga dos, you can type in commands which you will regret the second you hit the return key. I know enough to be dangerous.
I am hoping to find some help to walk me through the install as given in this post, but it is not easy to find.
This sort of thing is what keeps me from turning over entirely to linux mint or ubuntu. I still need to run some windows machines for my comfortable factor to be ok. 
I have the 352UNE devices running under windows 7. If I manage to access the devices directly from my linux machines by installing the software and mounting the disks, does that mean I have to unmount them and cease to use them under windows 7? This would not be a good thing.
My alternate way of accomplishing things might have to be to keep the linux machines seeing the drives in the 352une units via a windows share.
I welcome opinions from some of you experts as to my best course of action.
Running this install via use of the gui would be my preference.
Someday I will be free of microsoft but not so far. Please try to make it easier for me. 
BTw I also use Nerolinux and like it a lot. Seems I was still able to buy a legitimate copy last year.

---

### Post by konzeck on 2015-06-23
Hello, it is 2015 and I left Windows and joined Ubuntu. I am astonished what works and how easy it was.  Even my Filemaker Database runs in Wine!!!  But: There is a last task I cant get to work:  My NDAS from Iocell. The manual I found here doesnt work for me because the URL mentioned here is no longer valid. Looks as if I am stuck in the middle of nowhere. I need a guiding hand to lead me out of here to the shining light of a working NDAS.  Please!  Thx for your efforts to help me.  I already found a folder called ndas4linux-master, containing source-code for several Kernel versions. I use now 3.16.0-41-generic and the last Kernel in that folder  is 3.9.0-rc2. But I am not able to build the program. This is sad.  Donald

---

### Post by electroken on 2015-06-23
158
I just read all the posts and I had missed the ones by manlug and gamez so I will look at those and see if I can do what is required on the command line for mounting and using my ndas(s) and I do have several. I have complications even in using them via win 7 and it seems this will be much more complicated to do for me.
I am not good on the command line so the directions might have me trying to figure out exactly what is required to be written down for each of the drives. I have lived with using windows gui for a long tme now and going to the command line is not easy for me.
I was told on the IOCell site that the source code was available and it seems that konzek has been trying to work with it for various kernals. I am lost as to what he did, but at least someone was trying. I printed out the directions and hopefully I will be able to do something with them. Perhaps my nephew can help with it as he is quite good at linux and windows.
Thanks all for the efforts.

---

### Post by konzeck on 2015-06-23
Hello elektoken,  looks as if we have to do the task on our own. I will post any progress on this. Please do the same. There must be a way. BTW: I use the NDAS on win7 now for more then 5 years and it worked like a charm for me. On Linux I use the NDAS via VirtualBox. This works with no problem. The device is a shared device so I can access it via Linux. But I think it is time to find a native solution on Linux to run such a storage device. Dont you agree?  I wish you success  Donald

---

### Post by electroken on 2015-06-24
Yes I sure do agree with you. I have put the NDAS thing on the back burner for now and will do what you are doing. I have to install on windows of course and I hve several of the boxes I am using so that i can just leave my b ackups and files on my older drives until if they die it is now so far in the future that is wont matter if I lose the programs and files. I would be nice if someone with far more skills than I have could make this as easy to do from a gui on linux as it is on win7. I wont even try this on win8.
It is not simply point and click on win7 either and is somewhat bothesome to enter all the data etc. Its hard to teach an old dog new tricks and that applies to me. Perhaps though that since perhaps more of the ndas boxes are not being produced anymore, (if that is true) that it explains why noone is doing anything to put the install into a gui for guys like me on linux.
My only problem with the sharing thing is that it seems to me I have to have the win7 computer on line and running for me to see them on linux. 
Thanks for the reply and I will make an effort to get the boxes going again.

269

---

### Post by konzeck on 2015-06-24
>>My only problem with the sharing thing is that it seems to me I have to have the win7 computer on line and running for me to see them on linux.   You dont need a 2. PC running to use all your data on the NDAS. Install VirtualBox from Oracle on the Linux PC , its free. Than  install inside the virtual machine your Win7.  Read the way how to do it properly. You find a manual for this if you google (so did I). Make sure you have the extensions for your virtualbox installed. Then install the NDAS software in  virtualbox, mount the drive and set the share correctly. (You need to have a admin user on win7 with name and password and the same user on Linux). When you switch to Linux you see this drive as anetwork drive. Feel free to use it.  Dont forget to put your user into the group of vbusers. Look up the way to do it in terminal. You find it, promissed.

---

### Post by Louis_Baiani on 2016-06-07
Hi, I desperately need soem help with this.  This is the output from make:


carrielou@carrielou-ThinkCentre-M58:~/Desktop/ndas-4.4.0.x86_64$ sudo make
Invoking make against the kernel at /lib/modules/4.4.0-23-generic/build
make -C /lib/modules/4.4.0-23-generic/build \
	SUBDIRS=/home/carrielou/Desktop/ndas-4.4.0.x86_64 \
	KBUILD_VERBOSE=1 \
	ndas_root=/home/carrielou/Desktop/ndas-4.4.0.x86_64 \
	modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-23-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (	\
echo >&2;							\
echo >&2 "  ERROR: Kernel configuration is invalid.";		\
echo >&2 "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
echo >&2 "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
echo >&2 ;							\
/bin/false)
mkdir -p /home/carrielou/Desktop/ndas-4.4.0.x86_64/.tmp_versions ; rm -f /home/carrielou/Desktop/ndas-4.4.0.x86_64/.tmp_versions/*
make -f ./scripts/Makefile.build obj=/home/carrielou/Desktop/ndas-4.4.0.x86_64
  gcc -Wp,-MD,/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/.net.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/5/include  -I./arch/x86/include -Iarch/x86/include/generated/uapi -Iarch/x86/include/generated  -Iinclude -I./arch/x86/include/uapi -Iarch/x86/include/generated/uapi -I./include/uapi -Iinclude/generated/uapi -include ./include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -fno-pie -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -std=gnu89 -fno-pie -no-pie -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -m64 -falign-jumps=1 -falign-loops=1 -mno-80387 -mno-fp-ret-in-387 -mpreferred-stack-boundary=3 -mskip-rax-setup -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -DCONFIG_X86_X32_ABI -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_SSSE3=1 -DCONFIG_AS_CRC32=1 -DCONFIG_AS_AVX=1 -DCONFIG_AS_AVX2=1 -DCONFIG_AS_SHA1_NI=1 -DCONFIG_AS_SHA256_NI=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -fno-delete-null-pointer-checks -O2 --param=allow-store-data-races=0 -Wframe-larger-than=1024 -fstack-protector-strong -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -fno-var-tracking-assignments -pg -mfentry -DCC_USING_FENTRY -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -Werror=implicit-int -Werror=strict-prototypes -Werror=date-time -DCC_HAVE_ASM_GOTO -DMODULE -DLINUX -I/home/carrielou/Desktop/ndas-4.4.0.x86_64/inc -D_X86_64 -DNDAS_DONT_CARE_SCHEDULER  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(net)"  -D"KBUILD_MODNAME=KBUILD_STR(ndas_sal)" -c -o /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/.tmp_net.o /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c
/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c: In function ‘_sock_create’:
/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:366:10: error: too few arguments to function ‘sk_alloc’
     sk = sk_alloc(net, PF_LPX, GFP_ATOMIC, &sal_linux_proto);
          ^
In file included from /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:47:0:
include/net/sock.h:1511:14: note: declared here
 struct sock *sk_alloc(struct net *net, int family, gfp_t priority,
              ^
In file included from /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:55:0:
/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c: In function ‘sal_sock_create’:
/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:73:16: warning: passing argument 1 of ‘sock_create_kern’ makes pointer from integer without a cast [-Wint-conversion]
 #define PF_LPX 29
                ^
/home/carrielou/Desktop/ndas-4.4.0.x86_64/inc/linux_ver.h:196:22: note: in definition of macro ‘SOCK_CREATE’
     sock_create_kern(family, type, protocol, res)
                      ^
/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:1075:23: note: in expansion of macro ‘PF_LPX’
     err = SOCK_CREATE(PF_LPX, type, 0,&sock);
                       ^
In file included from include/linux/skbuff.h:29:0,
                 from include/linux/if_ether.h:23,
                 from include/uapi/linux/ethtool.h:17,
                 from include/linux/ethtool.h:16,
                 from include/linux/netdevice.h:42,
                 from /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:37:
include/linux/net.h:216:5: note: expected ‘struct net *’ but argument is of type ‘int’
 int sock_create_kern(struct net *net, int family, int type, int proto, struct s
     ^
In file included from /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:55:0:
/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:1075:39: warning: passing argument 4 of ‘sock_create_kern’ makes integer from pointer without a cast [-Wint-conversion]
     err = SOCK_CREATE(PF_LPX, type, 0,&sock);
                                       ^
/home/carrielou/Desktop/ndas-4.4.0.x86_64/inc/linux_ver.h:196:46: note: in definition of macro ‘SOCK_CREATE’
     sock_create_kern(family, type, protocol, res)
                                              ^
In file included from include/linux/skbuff.h:29:0,
                 from include/linux/if_ether.h:23,
                 from include/uapi/linux/ethtool.h:17,
                 from include/linux/ethtool.h:16,
                 from include/linux/netdevice.h:42,
                 from /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:37:
include/linux/net.h:216:5: note: expected ‘int’ but argument is of type ‘struct socket **’
 int sock_create_kern(struct net *net, int family, int type, int proto, struct s
     ^
In file included from /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:55:0:
/home/carrielou/Desktop/ndas-4.4.0.x86_64/inc/linux_ver.h:196:5: error: too few arguments to function ‘sock_create_kern’
     sock_create_kern(family, type, protocol, res)
     ^
/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:1075:11: note: in expansion of macro ‘SOCK_CREATE’
     err = SOCK_CREATE(PF_LPX, type, 0,&sock);
           ^
In file included from include/linux/skbuff.h:29:0,
                 from include/linux/if_ether.h:23,
                 from include/uapi/linux/ethtool.h:17,
                 from include/linux/ethtool.h:16,
                 from include/linux/netdevice.h:42,
                 from /home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.c:37:
include/linux/net.h:216:5: note: declared here
 int sock_create_kern(struct net *net, int family, int type, int proto, struct s
     ^
scripts/Makefile.build:258: recipe for target '/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.o' failed
make[2]: *** [/home/carrielou/Desktop/ndas-4.4.0.x86_64/sal/net.o] Error 1
Makefile:1402: recipe for target '_module_/home/carrielou/Desktop/ndas-4.4.0.x86_64' failed
make[1]: *** [_module_/home/carrielou/Desktop/ndas-4.4.0.x86_64] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-23-generic'
Makefile:405: recipe for target '/home/carrielou/Desktop/ndas-4.4.0.x86_64/ndas_sal.ko' failed
make: *** [/home/carrielou/Desktop/ndas-4.4.0.x86_64/ndas_sal.ko] Error 2


Thanks so much!

---

### Post by manlug on 2016-06-16
Hi Louis_Baiani,

visit [https://github.com/iocellnetworks/ndas4linux]("https://github.com/iocellnetworks/ndas4linux").
I think that kernel version is mayor to supported.
It isn't maintained from 4 years.

Bye.

---

