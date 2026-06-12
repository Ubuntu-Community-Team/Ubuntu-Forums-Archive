---
title: "help me installation DAP-1160"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by nkv1 on 2012-03-19
Hello all,
I am running Ubuntu 11.10.
I have downloaded software and drivers from [http://www.dlink.co.uk/]("http://www.dlink.co.uk/cs/Satellite?c=Product_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319181026&p=1197318962293&packedargs=QuickLinksParentID%3D1197318962293%26locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper")for my wireless router dap-1160
Seem i need to build from source code i have never done it before.C
read me file look like this
```
	RTL8186 LINUX Application Source Package - v1.3
		-----------------------------------------------
		
Package List
============
	1. Directory 'linux-2.4.18' - contain linux kernel 2.4.18 object modules
	   for RTL8186 SoC. It includes the object code and library adopted in 
	   RTL8186 turn-key solution for Access Point and Gateway package. it
	   also includes the makefile to allow you to put your own  application 
	   image and link with kerenl object modules to be a new system image.
	
	2. Directory 'AP' - contain the all application sources and makefile to
    	   build the application image for RTL8186. It includes:
	   - bridge configure utility (brctl)
	   - busybox shell
	   - dnrd for DNS relay
	   - GoAhead web server
	   - iptables to configure netfilter
	   - udhcp for DHCP server/client
 	   - PPPoE daemon and configure utility
	   - uClibc for shared C library
	   - script files to initialize the system
	   - Utility to access flash configuration parameters
	   - PPTP client daemon 
	   - Binary files for IAPP, 802.1x Authenticator, uPNP and 
	     auto-discovery daemon.
	   - tools to make an application image for Access Point (with versions
	     of 16M/2M,8M/2M and 8M/1M SDRAM/Flash) or Gateway  package
	   
 
Install & Build
===============
	1. Install the toolchain:
		(1). copy lexra-nnop-v5.tar.gz to /usr/local/gcc333 and decompress it.
			~#cd /usr/local
			~#mkdir gcc333
			~#cd  gcc333
			~#cp /your source code folder.../lexra-nnop-v5.tar.gz ./.
			~#tar -zxvf lexra-nnop-v5.tar.gz
	2. Building the image.
		(1). Copy the dap-1160_src.tar.gz into any directory you prefered and decompress it 
		     use following commands.
			~#tar -zxvf dap-1160_src.tar.gz
		(2). Into the root directory(named as "dap-1160_src") of dap-1160 source code,
		     and run following commands.
			~#source build.env
			~#cd AP
			~#make clean
			~#make ap
		(3). After make successfully, you will get the image file "web_firm_total_image.bin"
		     in "dap-1160_src/build/release" directory.
	3. Update the new firmware by web interface provide by device.
	4. Congratulations! You got your specific image now.

```

1. i have done with no problem
2. (1) no problem
2. (2) command make clean  gives this with errprs

```
nikola@nikola-MS-7376:~/dap-1160_src$ source build.env 
nikola@nikola-MS-7376:~/dap-1160_src$ cd AP
nikola@nikola-MS-7376:~/dap-1160_src/AP$ make clean 
make[1]: Entering directory `/home/nikola/dap-1160_src/AP/bridge-utils'
make -C brctl clean
make[2]: Entering directory `/home/nikola/dap-1160_src/AP/bridge-utils/brctl'
rm -f *.o
rm -f brctl
rm -f brctld
rm -f core
make[2]: Leaving directory `/home/nikola/dap-1160_src/AP/bridge-utils/brctl'
make -C libbridge clean
make[2]: Entering directory `/home/nikola/dap-1160_src/AP/bridge-utils/libbridge'
rcsclean *
/bin/sh: rcsclean: not found
make[2]: *** [clean] Error 127
make[2]: Leaving directory `/home/nikola/dap-1160_src/AP/bridge-utils/libbridge'
make[1]: *** [clean] Error 2
make[1]: Leaving directory `/home/nikola/dap-1160_src/AP/bridge-utils'
make: *** [clean] Error 2
nikola@nikola-MS-7376:~/dap-1160_src/AP$ make ap
make[1]: Entering directory `/home/nikola/dap-1160_src/AP'
make[2]: Entering directory `/home/nikola/dap-1160_src/AP/bridge-utils'
make -C libbridge 
make[3]: Entering directory `/home/nikola/dap-1160_src/AP/bridge-utils/libbridge'
mips-uclibc-gcc -Wall    -c libbridge_compat.c
mips-uclibc-gcc -Wall    -c libbridge_devif.c
mips-uclibc-gcc -Wall    -c libbridge_if.c
mips-uclibc-gcc -Wall    -c libbridge_init.c
mips-uclibc-gcc -Wall    -c libbridge_misc.c
ar rcs libbridge.a libbridge_compat.o libbridge_devif.o libbridge_if.o libbridge_init.o libbridge_misc.o
ranlib libbridge.a
make[3]: Leaving directory `/home/nikola/dap-1160_src/AP/bridge-utils/libbridge'
make -C brctl 
make[3]: Entering directory `/home/nikola/dap-1160_src/AP/bridge-utils/brctl'
mips-uclibc-gcc -s -I../libbridge -Wall -c -g  -o brctl.o brctl.c
mips-uclibc-gcc -s -I../libbridge -Wall -c -g  -o brctl_cmd.o brctl_cmd.c
mips-uclibc-gcc -s -I../libbridge -Wall -c -g  -o brctl_disp.o brctl_disp.c
mips-uclibc-gcc -s -Wall -g  -o brctl brctl.o brctl_cmd.o brctl_disp.o ../libbridge/libbridge.a
mips-uclibc-gcc -s -I../libbridge -Wall -c -g  -o brctld.o brctld.c
mips-uclibc-gcc -s -Wall -g  -o brctld brctld.o brctl_cmd.o brctl_disp.o ../libbridge/libbridge.a
make[3]: Leaving directory `/home/nikola/dap-1160_src/AP/bridge-utils/brctl'
make -C misc
make[3]: Entering directory `/home/nikola/dap-1160_src/AP/bridge-utils/misc'
gcc -Wall -g  -o bidi bidi.c
make[3]: Leaving directory `/home/nikola/dap-1160_src/AP/bridge-utils/misc'
make[2]: Leaving directory `/home/nikola/dap-1160_src/AP/bridge-utils'
make[2]: Entering directory `/home/nikola/dap-1160_src/AP/busybox-1.00-pre8'
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o applets/applets.o applets/applets.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o applets/busybox.o applets/busybox.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o applets/usage.o applets/usage.c
mips-uclibc-ar -ro applets/applets.a ./applets/applets.o ./applets/busybox.o ./applets/usage.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/bunzip2.o archival/bunzip2.c
archival/bunzip2.c: In function `bunzip2_main':
archival/bunzip2.c:36: warning: `save_name' might be used uninitialized in this function
mips-uclibc-ar -ro archival/archival.a ./archival/bunzip2.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/data_skip.o archival/libunarchive/data_skip.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/data_extract_all.o archival/libunarchive/data_extract_all.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/data_extract_to_stdout.o archival/libunarchive/data_extract_to_stdout.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/data_extract_to_buffer.o archival/libunarchive/data_extract_to_buffer.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/filter_accept_all.o archival/libunarchive/filter_accept_all.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/filter_accept_list.o archival/libunarchive/filter_accept_list.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/filter_accept_reject_list.o archival/libunarchive/filter_accept_reject_list.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/header_skip.o archival/libunarchive/header_skip.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/header_list.o archival/libunarchive/header_list.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/header_verbose_list.o archival/libunarchive/header_verbose_list.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/archive_xread_all.o archival/libunarchive/archive_xread_all.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/archive_xread_all_eof.o archival/libunarchive/archive_xread_all_eof.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/seek_by_char.o archival/libunarchive/seek_by_char.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/seek_by_jump.o archival/libunarchive/seek_by_jump.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/data_align.o archival/libunarchive/data_align.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/find_list_entry.o archival/libunarchive/find_list_entry.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/open_transformer.o archival/libunarchive/open_transformer.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/init_handle.o archival/libunarchive/init_handle.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o archival/libunarchive/decompress_bunzip2.o archival/libunarchive/decompress_bunzip2.c
archival/libunarchive/decompress_bunzip2.c: In function `get_next_block':
archival/libunarchive/decompress_bunzip2.c:137: warning: `hufGroup' might be used uninitialized in this function
archival/libunarchive/decompress_bunzip2.c:138: warning: `base' might be used uninitialized in this function
archival/libunarchive/decompress_bunzip2.c:138: warning: `limit' might be used uninitialized in this function
mips-uclibc-ar -ro archival/libunarchive/libunarchive.a ./archival/libunarchive/data_skip.o ./archival/libunarchive/data_extract_all.o ./archival/libunarchive/data_extract_to_stdout.o ./archival/libunarchive/data_extract_to_buffer.o ./archival/libunarchive/filter_accept_all.o ./archival/libunarchive/filter_accept_list.o ./archival/libunarchive/filter_accept_reject_list.o ./archival/libunarchive/header_skip.o ./archival/libunarchive/header_list.o ./archival/libunarchive/header_verbose_list.o ./archival/libunarchive/archive_xread_all.o ./archival/libunarchive/archive_xread_all_eof.o ./archival/libunarchive/seek_by_char.o ./archival/libunarchive/seek_by_jump.o ./archival/libunarchive/data_align.o ./archival/libunarchive/find_list_entry.o ./archival/libunarchive/open_transformer.o ./archival/libunarchive/init_handle.o ./archival/libunarchive/decompress_bunzip2.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/cat.o coreutils/cat.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/cp.o coreutils/cp.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/cut.o coreutils/cut.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/echo.o coreutils/echo.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/expr.o coreutils/expr.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/false.o coreutils/false.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/head.o coreutils/head.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/mkdir.o coreutils/mkdir.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/rm.o coreutils/rm.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/sleep.o coreutils/sleep.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/tail.o coreutils/tail.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/test.o coreutils/test.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/true.o coreutils/true.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/wc.o coreutils/wc.c
mips-uclibc-ar -ro coreutils/coreutils.a ./coreutils/cat.o ./coreutils/cp.o ./coreutils/cut.o ./coreutils/echo.o ./coreutils/expr.o ./coreutils/false.o ./coreutils/head.o ./coreutils/mkdir.o ./coreutils/rm.o ./coreutils/sleep.o ./coreutils/tail.o ./coreutils/test.o ./coreutils/true.o ./coreutils/wc.o
mips-uclibc-ar -ro console-tools/console-tools.a 
mips-uclibc-ar -ro debianutils/debianutils.a 
mips-uclibc-ar -ro editors/editors.a 
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o findutils/grep.o findutils/grep.c
mips-uclibc-ar -ro findutils/findutils.a ./findutils/grep.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o init/init.o init/init.c
init/init.c:175: warning: shadowing built-in function `log'
init/init.c:183: warning: function declaration isn't a prototype
init/init.c:295: warning: function declaration isn't a prototype
init/init.c:316: warning: function declaration isn't a prototype
init/init.c:591: warning: function declaration isn't a prototype
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o init/reboot.o init/reboot.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o init/init_shared.o init/init_shared.c
mips-uclibc-ar -ro init/init.a ./init/init.o ./init/reboot.o ./init/init_shared.o
mips-uclibc-ar -ro miscutils/miscutils.a 
mips-uclibc-ar -ro modutils/modutils.a 
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o networking/ifconfig.o networking/ifconfig.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o networking/route.o networking/route.c
mips-uclibc-ar -ro networking/networking.a ./networking/ifconfig.o ./networking/route.o
mips-uclibc-ar -ro networking/libiproute/libiproute.a 
mips-uclibc-ar -ro networking/udhcp/udhcp.a 
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o procps/kill.o procps/kill.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o procps/ps.o procps/ps.c
mips-uclibc-ar -ro procps/procps.a ./procps/kill.o ./procps/ps.o
mips-uclibc-ar -ro loginutils/loginutils.a 
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o shell/msh.o shell/msh.c
shell/msh.c:55:1: warning: "NOFILE" redefined
In file included from include/busybox.h:116,
                 from shell/msh.c:44:
/usr/local/gcc333/lexra-nnop-v5/mips-linux-uclibc/sys-include/sys/param.h:39:1: warning: this is the location of the previous definition
shell/msh.c:397: warning: function declaration isn't a prototype
shell/msh.c:432: warning: function declaration isn't a prototype
shell/msh.c:449: warning: function declaration isn't a prototype
shell/msh.c:512: warning: function declaration isn't a prototype
shell/msh.c:520: warning: function declaration isn't a prototype
shell/msh.c:538: warning: function declaration isn't a prototype
shell/msh.c:598: warning: function declaration isn't a prototype
shell/msh.c: In function `msh_main':
shell/msh.c:701: warning: function declaration isn't a prototype
shell/msh.c: In function `forkexec':
shell/msh.c:2477: warning: function declaration isn't a prototype
shell/msh.c: In function `run':
shell/msh.c:2900: warning: function declaration isn't a prototype
shell/msh.c: In function `rdexp':
shell/msh.c:3329: warning: function declaration isn't a prototype
shell/msh.c: At top level:
shell/msh.c:3440: warning: function declaration isn't a prototype
shell/msh.c: In function `pushio':
shell/msh.c:4283: warning: function declaration isn't a prototype
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o shell/cmdedit.o shell/cmdedit.c
mips-uclibc-ar -ro shell/shell.a ./shell/msh.o ./shell/cmdedit.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o sysklogd/klogd.o sysklogd/klogd.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o sysklogd/syslogd.o sysklogd/syslogd.c
mips-uclibc-ar -ro sysklogd/sysklogd.a ./sysklogd/klogd.o ./sysklogd/syslogd.o
mips-uclibc-ar -ro util-linux/util-linux.a 
mips-uclibc-ar -ro libpwdgrp/libpwdgrp.a 
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/libcoreutils/cp_mv_stat.o coreutils/libcoreutils/cp_mv_stat.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/libcoreutils/getopt_mk_fifo_nod.o coreutils/libcoreutils/getopt_mk_fifo_nod.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o coreutils/libcoreutils/xgetoptfile_sort_uniq.o coreutils/libcoreutils/xgetoptfile_sort_uniq.c
mips-uclibc-ar -ro coreutils/libcoreutils/libcoreutils.a ./coreutils/libcoreutils/cp_mv_stat.o ./coreutils/libcoreutils/getopt_mk_fifo_nod.o ./coreutils/libcoreutils/xgetoptfile_sort_uniq.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/bb_asprintf.o libbb/bb_asprintf.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/ask_confirmation.o libbb/ask_confirmation.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/change_identity.o libbb/change_identity.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/chomp.o libbb/chomp.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/compare_string_array.o libbb/compare_string_array.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/concat_path_file.o libbb/concat_path_file.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/copy_file.o libbb/copy_file.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/copyfd.o libbb/copyfd.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/correct_password.o libbb/correct_password.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/create_icmp_socket.o libbb/create_icmp_socket.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/create_icmp6_socket.o libbb/create_icmp6_socket.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/device_open.o libbb/device_open.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/dump.o libbb/dump.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/error_msg.o libbb/error_msg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/error_msg_and_die.o libbb/error_msg_and_die.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/find_mount_point.o libbb/find_mount_point.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/find_pid_by_name.o libbb/find_pid_by_name.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/find_root_device.o libbb/find_root_device.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/fgets_str.o libbb/fgets_str.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/full_read.o libbb/full_read.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/full_write.o libbb/full_write.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/get_last_path_component.o libbb/get_last_path_component.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/get_line_from_file.o libbb/get_line_from_file.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/get_ug_id.o libbb/get_ug_id.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/get_terminal_width_height.o libbb/get_terminal_width_height.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/hash_fd.o libbb/hash_fd.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/herror_msg.o libbb/herror_msg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/herror_msg_and_die.o libbb/herror_msg_and_die.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/human_readable.o libbb/human_readable.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/inet_common.o libbb/inet_common.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/inode_hash.o libbb/inode_hash.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/interface.o libbb/interface.c
libbb/interface.c:1710:2: warning: #warning devel code
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/isdirectory.o libbb/isdirectory.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/kernel_version.o libbb/kernel_version.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/last_char_is.o libbb/last_char_is.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/llist_add_to.o libbb/llist_add_to.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/login.o libbb/login.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/loop.o libbb/loop.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/make_directory.o libbb/make_directory.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/mode_string.o libbb/mode_string.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/module_syscalls.o libbb/module_syscalls.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/mtab.o libbb/mtab.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/mtab_file.o libbb/mtab_file.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/my_getgrgid.o libbb/my_getgrgid.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/my_getgrnam.o libbb/my_getgrnam.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/my_getpwnam.o libbb/my_getpwnam.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/my_getpwnamegid.o libbb/my_getpwnamegid.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/my_getpwuid.o libbb/my_getpwuid.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/obscure.o libbb/obscure.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/parse_mode.o libbb/parse_mode.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/parse_number.o libbb/parse_number.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/perror_msg.o libbb/perror_msg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/perror_msg_and_die.o libbb/perror_msg_and_die.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/print_file.o libbb/print_file.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/get_console.o libbb/get_console.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/process_escape_sequence.o libbb/process_escape_sequence.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/procps.o libbb/procps.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/pwd2spwd.o libbb/pwd2spwd.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/pw_encrypt.o libbb/pw_encrypt.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/qmodule.o libbb/qmodule.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/read_package_field.o libbb/read_package_field.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/recursive_action.o libbb/recursive_action.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/remove_file.o libbb/remove_file.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/restricted_shell.o libbb/restricted_shell.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/run_parts.o libbb/run_parts.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/run_shell.o libbb/run_shell.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/safe_read.o libbb/safe_read.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/safe_write.o libbb/safe_write.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/safe_strncpy.o libbb/safe_strncpy.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/setup_environment.o libbb/setup_environment.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/simplify_path.o libbb/simplify_path.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/syscalls.o libbb/syscalls.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/syslog_msg_with_name.o libbb/syslog_msg_with_name.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/trim.o libbb/trim.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/u_signal_names.o libbb/u_signal_names.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/vdprintf.o libbb/vdprintf.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/verror_msg.o libbb/verror_msg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/vherror_msg.o libbb/vherror_msg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/vperror_msg.o libbb/vperror_msg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/wfopen.o libbb/wfopen.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/xconnect.o libbb/xconnect.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/xgetcwd.o libbb/xgetcwd.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/xgethostbyname.o libbb/xgethostbyname.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/xgethostbyname2.o libbb/xgethostbyname2.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/xreadlink.o libbb/xreadlink.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/xregcomp.o libbb/xregcomp.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/xgetlarg.o libbb/xgetlarg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/fclose_nonstdin.o libbb/fclose_nonstdin.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/fflush_stdout_and_exit.o libbb/fflush_stdout_and_exit.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/getopt_ulflags.o libbb/getopt_ulflags.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/default_error_retval.o libbb/default_error_retval.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/wfopen_input.o libbb/wfopen_input.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/speed_table.o libbb/speed_table.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/perror_nomsg_and_die.o libbb/perror_nomsg_and_die.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/perror_nomsg.o libbb/perror_nomsg.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/skip_whitespace.o libbb/skip_whitespace.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/warn_ignoring_args.o libbb/warn_ignoring_args.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/concat_subpath_file.o libbb/concat_subpath_file.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -c -o libbb/vfork_daemon_rexec.o libbb/vfork_daemon_rexec.c
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_full_version -c libbb/messages.c -o libbb/full_version.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_memory_exhausted -c libbb/messages.c -o libbb/memory_exhausted.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_invalid_date -c libbb/messages.c -o libbb/invalid_date.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_io_error -c libbb/messages.c -o libbb/io_error.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_write_error -c libbb/messages.c -o libbb/write_error.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_name_longer_than_foo -c libbb/messages.c -o libbb/name_longer_than_foo.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_unknown -c libbb/messages.c -o libbb/unknown.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_can_not_create_raw_socket -c libbb/messages.c -o libbb/can_not_create_raw_socket.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_perm_denied_are_you_root -c libbb/messages.c -o libbb/perm_denied_are_you_root.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_shadow_file -c libbb/messages.c -o libbb/shadow_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_passwd_file -c libbb/messages.c -o libbb/passwd_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_group_file -c libbb/messages.c -o libbb/group_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_gshadow_file -c libbb/messages.c -o libbb/gshadow_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_nologin_file -c libbb/messages.c -o libbb/nologin_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_securetty_file -c libbb/messages.c -o libbb/securetty_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_motd_file -c libbb/messages.c -o libbb/motd_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_msg_standard_input -c libbb/messages.c -o libbb/msg_standard_input.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_msg_standard_output -c libbb/messages.c -o libbb/msg_standard_output.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_shell_file -c libbb/messages.c -o libbb/shell_file.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xmalloc -c libbb/xfuncs.c -o libbb/xmalloc.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xrealloc -c libbb/xfuncs.c -o libbb/xrealloc.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xcalloc -c libbb/xfuncs.c -o libbb/xcalloc.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xstrdup -c libbb/xfuncs.c -o libbb/xstrdup.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xstrndup -c libbb/xfuncs.c -o libbb/xstrndup.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xfopen -c libbb/xfuncs.c -o libbb/xfopen.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xopen -c libbb/xfuncs.c -o libbb/xopen.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xread -c libbb/xfuncs.c -o libbb/xread.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xread_all -c libbb/xfuncs.c -o libbb/xread_all.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xread_char -c libbb/xfuncs.c -o libbb/xread_char.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xferror -c libbb/xfuncs.c -o libbb/xferror.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xferror_stdout -c libbb/xfuncs.c -o libbb/xferror_stdout.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xfflush_stdout -c libbb/xfuncs.c -o libbb/xfflush_stdout.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_strlen -c libbb/xfuncs.c -o libbb/strlen.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_bb_vfprintf -c libbb/printf.c -o libbb/bb_vfprintf.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_bb_vprintf -c libbb/printf.c -o libbb/bb_vprintf.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_bb_fprintf -c libbb/printf.c -o libbb/bb_fprintf.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_bb_printf -c libbb/printf.c -o libbb/bb_printf.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xgetularg_bnd_sfx -c libbb/xgetularg.c -o libbb/xgetularg_bnd_sfx.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xgetlarg_bnd_sfx -c libbb/xgetularg.c -o libbb/xgetlarg_bnd_sfx.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_getlarg10_sfx -c libbb/xgetularg.c -o libbb/getlarg10_sfx.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xgetularg_bnd -c libbb/xgetularg.c -o libbb/xgetularg_bnd.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xgetularg10_bnd -c libbb/xgetularg.c -o libbb/xgetularg10_bnd.o
mips-uclibc-gcc -I./include -Wall -Wstrict-prototypes -Wshadow -Os -fomit-frame-pointer -D_GNU_SOURCE -DNDEBUG     -DL_xgetularg10 -c libbb/xgetularg.c -o libbb/xgetularg10.o
mips-uclibc-ar -ro libbb/libbb.a ./libbb/bb_asprintf.o ./libbb/ask_confirmation.o ./libbb/change_identity.o ./libbb/chomp.o ./libbb/compare_string_array.o ./libbb/concat_path_file.o ./libbb/copy_file.o ./libbb/copyfd.o ./libbb/correct_password.o ./libbb/create_icmp_socket.o ./libbb/create_icmp6_socket.o ./libbb/device_open.o ./libbb/dump.o ./libbb/error_msg.o ./libbb/error_msg_and_die.o ./libbb/find_mount_point.o ./libbb/find_pid_by_name.o ./libbb/find_root_device.o ./libbb/fgets_str.o ./libbb/full_read.o ./libbb/full_write.o ./libbb/get_last_path_component.o ./libbb/get_line_from_file.o ./libbb/get_ug_id.o ./libbb/get_terminal_width_height.o ./libbb/hash_fd.o ./libbb/herror_msg.o ./libbb/herror_msg_and_die.o ./libbb/human_readable.o ./libbb/inet_common.o ./libbb/inode_hash.o ./libbb/interface.o ./libbb/isdirectory.o ./libbb/kernel_version.o ./libbb/last_char_is.o ./libbb/llist_add_to.o ./libbb/login.o ./libbb/loop.o ./libbb/make_directory.o ./libbb/mode_string.o ./libbb/module_syscalls.o ./libbb/mtab.o ./libbb/mtab_file.o ./libbb/my_getgrgid.o ./libbb/my_getgrnam.o ./libbb/my_getpwnam.o ./libbb/my_getpwnamegid.o ./libbb/my_getpwuid.o ./libbb/obscure.o ./libbb/parse_mode.o ./libbb/parse_number.o ./libbb/perror_msg.o ./libbb/perror_msg_and_die.o ./libbb/print_file.o ./libbb/get_console.o ./libbb/process_escape_sequence.o ./libbb/procps.o ./libbb/pwd2spwd.o ./libbb/pw_encrypt.o ./libbb/qmodule.o ./libbb/read_package_field.o ./libbb/recursive_action.o ./libbb/remove_file.o ./libbb/restricted_shell.o ./libbb/run_parts.o ./libbb/run_shell.o ./libbb/safe_read.o ./libbb/safe_write.o ./libbb/safe_strncpy.o ./libbb/setup_environment.o ./libbb/simplify_path.o ./libbb/syscalls.o ./libbb/syslog_msg_with_name.o ./libbb/trim.o ./libbb/u_signal_names.o ./libbb/vdprintf.o ./libbb/verror_msg.o ./libbb/vherror_msg.o ./libbb/vperror_msg.o ./libbb/wfopen.o ./libbb/xconnect.o ./libbb/xgetcwd.o ./libbb/xgethostbyname.o ./libbb/xgethostbyname2.o ./libbb/xreadlink.o ./libbb/xregcomp.o ./libbb/xgetlarg.o ./libbb/get_terminal_width_height.o ./libbb/fclose_nonstdin.o ./libbb/fflush_stdout_and_exit.o ./libbb/getopt_ulflags.o ./libbb/default_error_retval.o ./libbb/wfopen_input.o ./libbb/speed_table.o ./libbb/perror_nomsg_and_die.o ./libbb/perror_nomsg.o ./libbb/skip_whitespace.o ./libbb/warn_ignoring_args.o ./libbb/concat_subpath_file.o ./libbb/vfork_daemon_rexec.o ./libbb/full_version.o ./libbb/memory_exhausted.o ./libbb/invalid_date.o ./libbb/io_error.o ./libbb/write_error.o ./libbb/name_longer_than_foo.o ./libbb/unknown.o ./libbb/can_not_create_raw_socket.o ./libbb/perm_denied_are_you_root.o ./libbb/shadow_file.o ./libbb/passwd_file.o ./libbb/group_file.o ./libbb/gshadow_file.o ./libbb/nologin_file.o ./libbb/securetty_file.o ./libbb/motd_file.o ./libbb/msg_standard_input.o ./libbb/msg_standard_output.o ./libbb/shell_file.o ./libbb/xmalloc.o ./libbb/xrealloc.o ./libbb/xcalloc.o ./libbb/xstrdup.o ./libbb/xstrndup.o ./libbb/xfopen.o ./libbb/xopen.o ./libbb/xread.o ./libbb/xread_all.o ./libbb/xread_char.o ./libbb/xferror.o ./libbb/xferror_stdout.o ./libbb/xfflush_stdout.o ./libbb/strlen.o \
		./libbb/bb_vfprintf.o ./libbb/bb_vprintf.o ./libbb/bb_fprintf.o ./libbb/bb_printf.o ./libbb/xgetularg_bnd_sfx.o ./libbb/xgetlarg_bnd_sfx.o ./libbb/getlarg10_sfx.o ./libbb/xgetularg_bnd.o ./libbb/xgetularg10_bnd.o ./libbb/xgetularg10.o 
mips-uclibc-gcc -s -Wl,-warn-common -o busybox -Wl,--start-group ./applets/applets.a ./archival/archival.a ./archival/libunarchive/libunarchive.a ./coreutils/coreutils.a ./console-tools/console-tools.a ./debianutils/debianutils.a ./editors/editors.a ./findutils/findutils.a ./init/init.a ./miscutils/miscutils.a ./modutils/modutils.a ./networking/networking.a ./networking/libiproute/libiproute.a ./networking/udhcp/udhcp.a ./procps/procps.a ./loginutils/loginutils.a ./shell/shell.a ./sysklogd/sysklogd.a ./util-linux/util-linux.a ./libpwdgrp/libpwdgrp.a ./coreutils/libcoreutils/libcoreutils.a ./libbb/libbb.a  -Wl,--end-group
mips-uclibc-strip --remove-section=.note --remove-section=.comment busybox
/bin/sh applets/busybox.mkll include/config.h >busybox.links
( cat docs/busybox_header.pod; \
	    docs/autodocifier.pl include/usage.h; \
	    cat docs/busybox_footer.pod ) > docs/busybox.pod

BusyBox Documentation

mkdir -p docs
pod2text docs/busybox.pod > docs/BusyBox.txt
mkdir -p docs
pod2man --center=BusyBox --release="version 1.00-pre8" \
		docs/busybox.pod > docs/BusyBox.1
pod2html --noindex docs/busybox.pod > \
	    docs/busybox.net/BusyBox.html
mkdir -p docs
/bin/sh applets/install.sh "./_install"
  ./_install/bin/cat -> busybox
  ./_install/bin/cp -> busybox
  ./_install/bin/echo -> busybox
  ./_install/bin/false -> busybox
  ./_install/bin/grep -> busybox
  ./_install/bin/kill -> busybox
  ./_install/bin/mkdir -> busybox
  ./_install/bin/msh -> busybox
  ./_install/bin/ps -> busybox
  ./_install/bin/rm -> busybox
  ./_install/bin/sh -> busybox
  ./_install/bin/sleep -> busybox
  ./_install/bin/true -> busybox
  ./_install/sbin/ifconfig -> ../bin/busybox
  ./_install/sbin/init -> ../bin/busybox
  ./_install/sbin/klogd -> ../bin/busybox
  ./_install/sbin/reboot -> ../bin/busybox
  ./_install/sbin/route -> ../bin/busybox
  ./_install/sbin/syslogd -> ../bin/busybox
  ./_install/usr/bin/[ -> ../../bin/busybox
  ./_install/usr/bin/bunzip2 -> ../../bin/busybox
  ./_install/usr/bin/bzcat -> ../../bin/busybox
  ./_install/usr/bin/cut -> ../../bin/busybox
  ./_install/usr/bin/expr -> ../../bin/busybox
  ./_install/usr/bin/head -> ../../bin/busybox
  ./_install/usr/bin/killall -> ../../bin/busybox
  ./_install/usr/bin/tail -> ../../bin/busybox
  ./_install/usr/bin/test -> ../../bin/busybox
  ./_install/usr/bin/wc -> ../../bin/busybox
make[2]: Leaving directory `/home/nikola/dap-1160_src/AP/busybox-1.00-pre8'
make[2]: Entering directory `/home/nikola/dap-1160_src/AP/udhcp-0.9.9-pre'
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer dhcpd.c
In file included from dhcpd.h:10,
                 from dhcpd.c:43:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer arpping.c
In file included from dhcpd.h:10,
                 from arpping.c:21:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer files.c
In file included from dhcpd.h:10,
                 from files.c:16:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer leases.c
In file included from dhcpd.h:10,
                 from leases.c:13:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer serverpacket.c
In file included from dhcpd.h:10,
                 from serverpacket.c:30:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer dhcpc.c
In file included from dhcpd.h:10,
                 from dhcpc.c:39:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
dhcpc.c: In function `perform_renew':
dhcpc.c:137: warning: deprecated use of label at end of compound statement
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer clientpacket.c
In file included from dhcpd.h:10,
                 from clientpacket.c:44:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer script.c
In file included from dhcpd.h:10,
                 from script.c:34:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer options.c
In file included from dhcpd.h:10,
                 from options.c:11:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
options.c: In function `add_simple_option':
options.c:160: warning: dereferencing type-punned pointer will break strict-aliasing rules
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer socket.c
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer packet.c
In file included from dhcpd.h:10,
                 from packet.c:19:
version.h:4:1: warning: "VERSION" redefined
<command line>:5:1: warning: this is the location of the previous definition
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer pidfile.c
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer frontend.c
mips-uclibc-gcc  dhcpd.o arpping.o files.o leases.o serverpacket.o dhcpc.o clientpacket.o script.o options.o socket.o packet.o pidfile.o frontend.o -o udhcpd
mips-uclibc-gcc -c -DCOMBINED_BINARY -W -Wall -Wstrict-prototypes -DVERSION='"0.9.8"' -Os -fomit-frame-pointer dumpleases.c
mips-uclibc-gcc  dumpleases.o -o dumpleases
mips-uclibc-strip --remove-section=.note --remove-section=.comment udhcpd  dumpleases
make[2]: Leaving directory `/home/nikola/dap-1160_src/AP/udhcp-0.9.9-pre'
make[2]: Entering directory `/home/nikola/dap-1160_src/AP/wireless_tools.25'
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -c iwlib.c
iwlib.c: In function `iw_dbm2mwatt':
iwlib.c:756: warning: unused parameter `in'
iwlib.c:757: warning: control reaches end of non-void function
iwlib.c: In function `iw_mwatt2dbm':
iwlib.c:766: warning: unused parameter `in'
iwlib.c:767: warning: control reaches end of non-void function
iwlib.c: In function `iw_print_pm_mode':
iwlib.c:1092: warning: deprecated use of label at end of compound statement
rm -f libiw.a
ar cru libiw.a iwlib.o
ranlib libiw.a
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -fPIC -c -o iwlib.so iwlib.c
iwlib.c: In function `iw_dbm2mwatt':
iwlib.c:756: warning: unused parameter `in'
iwlib.c:757: warning: control reaches end of non-void function
iwlib.c: In function `iw_mwatt2dbm':
iwlib.c:766: warning: unused parameter `in'
iwlib.c:767: warning: control reaches end of non-void function
iwlib.c: In function `iw_print_pm_mode':
iwlib.c:1092: warning: deprecated use of label at end of compound statement
mips-uclibc-gcc -shared -o libiw.so.25 -Wl,-soname,libiw.so.25 -lc iwlib.so
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -c iwconfig.c
iwconfig.c: In function `set_info':
iwconfig.c:1213: warning: dereferencing type-punned pointer will break strict-aliasing rules
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y   -o iwconfig iwconfig.o libiw.a 
mips-linux-strip iwconfig
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -c iwlist.c
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y   -o iwlist iwlist.o libiw.a 
mips-linux-strip iwlist
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -c iwpriv.c
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y   -o iwpriv iwpriv.o libiw.a 
mips-linux-strip iwpriv
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -c iwspy.c
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y   -o iwspy iwspy.o libiw.a 
mips-linux-strip iwspy
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -c iwgetid.c
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y   -o iwgetid iwgetid.o 
mips-linux-strip iwgetid
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y  -c iwevent.c
iwevent.c:28:1: warning: "MSG_DONTWAIT" redefined
In file included from /usr/local/gcc333/lexra-nnop-v5/mips-linux-uclibc/sys-include/netinet/in.h:212,
                 from /usr/local/gcc333/lexra-nnop-v5/mips-linux-uclibc/sys-include/netdb.h:28,
                 from iwlib.h:30,
                 from iwevent.c:20:
/usr/local/gcc333/lexra-nnop-v5/mips-linux-uclibc/sys-include/bits/socket.h:191:1: warning: this is the location of the previous definition
mips-uclibc-gcc -O2 -W -Wall -Wstrict-prototypes    -DWE_NOLIBM=y   -o iwevent iwevent.o libiw.a 
mips-linux-strip iwevent
make[2]: Leaving directory `/home/nikola/dap-1160_src/AP/wireless_tools.25'
make[1]: Leaving directory `/home/nikola/dap-1160_src/AP'
mknod: `/home/nikola/dap-1160_src/AP/rootfs/dev/ttyS0': Operation not permitted
mknod: `/home/nikola/dap-1160_src/AP/rootfs/dev/console': Operation not permitted
mknod: `/home/nikola/dap-1160_src/AP/rootfs/dev/null': Operation not permitted
mknod: `/home/nikola/dap-1160_src/AP/rootfs/dev/mtd': Operation not permitted
mknod: `/home/nikola/dap-1160_src/AP/rootfs/dev/wl_chr0': Operation not permitted
mknod: `/home/nikola/dap-1160_src/AP/rootfs/dev/wl_chr1': Operation not permitted
cp: omitting directory `./udhcp-0.9.9-pre/mips-scripts/CVS'
============Create Ramdisk=====================
==>Making ramdisk size 2500 KBytes
dd: opening `/dev/ram': Permission denied
mke2fs 1.41.14 (22-Dec-2010)
Could not stat /dev/ram --- No such file or directory

The device apparently does not exist; did you specify it correctly?
make: *** [ap] Error 1
nikola@nikola-MS-7376:~/dap-1160_src/AP$
```
After this file dap-1160_src/build/release does not exist, i do not know if i did something wrong?
Cant access web confirguration interface at 192.168.0.50?

---

### Post by nkv1 on 2012-04-28
That is great you ask the world and nobody can give an answer.
If my wireless router dap-1160 is incompatible with ubuntu 10.10
What wireless router do you suggest?

---

