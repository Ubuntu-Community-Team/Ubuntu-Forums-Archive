---
title: "Please Help, Installing Wireless driver using terminal"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by RedeyeAce on 2009-02-07
Heya folks,

Searched through the sticky and my particular card isnt lited, just changed title to reflect card and chipset, but hasnt changed in main site.

SparkLAN WUBZ-103 (lsusb:Fiberline WL-430U), Ubuntu8.1

*edit:  uname -mr 2.6.27-11-generic i686

Changed directory for install location in makedriver file to this and it still doesnt work* 


Thought id be able to do this on my own but im stuck. I am a complete linux noob, however did used to do dos back in the day and thankfully some of the commands are the same.

Im trying to install a wireless usb device on a friends laptop which is using Ubuntu 8.1

here is the location for the driver: [http://www.sparklan.com/download.php?support_id=24&ranload=1234039418](http://www.sparklan.com/download.php?support_id=24&ranload=1234039418)

------------------------------------------------------------------------
The package contains drivers for ZD1211 and ZD1211B. If you doesn’t have specified request, both of them will be installed. 
Under the extracted directory, there is a Makefile in it. Because our driver can support for kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify the Makefile according to the path of “kernel source tree” and the version of the kernel in your system. In the Makefile, you may see the following statements, 
# if the kernel is 2.6.x, turn on this 
#KERN_26=y 
#KERNEL_SOURCE=/usr/src/linux-2.6.7 
# if the kernel is 2.4.x, turn on this 
KERN_24=y 
KERNEL_SOURCE=/usr/src/linux-2.4.20-8 
If you want to build the kernel under the kernel of 2.4.x, one has to let the variable KERN_24=y and comment the KERN_26=y like that as the example above and modify the variable KERNEL_SOURCE to the path which you install the kernel source. After doing these things, one just need to type the “make”, and the driver module will be generated and installed. 
-------------------------------------------------------------------------

So i looked around in usr/src and saw it says 2.6.27, so it to the following KERNEL_SOURCE=/usr/src/linux-headers-2.6.27-7

Then i run the make command by using terminal and navigating to the directory of the uncompressed drivers using cd command

I hit make and get a few errors, which I dont get, looks like theres files missing that its rying to alter, so im wondering whether im using the correct directory.

--------------------------------------------------------------------------
john@john-laptop:~/Documents/Downloads/Drivers/Sparklan$ make
make: *** No targets specified and no makefile found. Stop.
john@john-laptop:~/Documents/Downloads/Drivers/Sparklan$ cd Uncompresed
john@john-laptop:~/Documents/Downloads/Drivers/Sparklan/Uncompresed$ make
make both
make[1]: Entering directory `/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed'
make ZD1211REV_B=0
make[2]: Entering directory `/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed'
/lib/modules/2.6.27-11-generic/build
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed
-I/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.o
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:42:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.h:663: warning: ‘__packed__’ attribute ignored
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:238: warning: function declaration isn’t a prototype
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:239: warning: function declaration isn’t a prototype
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:304: warning: useless storage class specifier in empty declaration
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:432: error: expected declaration specifiers or ‘...’ before ‘write’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:432: error: expected declaration specifiers or ‘...’ before ‘fd’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:432: error: expected declaration specifiers or ‘...’ before ‘buf’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:432: error: expected declaration specifiers or ‘...’ before ‘count’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:433: warning: type defaults to ‘int’ in declaration of ‘_syscall3’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:433: error: expected ‘,’ or ‘;’ before ‘_syscall3’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_house_keeping’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:1229: warning: unused variable ‘tmpvalue’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_config’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:2099: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘U32’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_rx_isr’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:3661: error: ‘struct sk_buff’ has no member named ‘mac’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_xmit_frame’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:4427: warning: suggest parentheses around && within ||
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_watchdog’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:5061: warning: unused variable ‘ssidLenToDump’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:5060: warning: unused variable ‘cbTemp’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_ioctl_setiwencode’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:5381: warning: unused variable ‘bReconnect’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205wext_siwscan’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6128: warning: unused variable ‘ul_mac_ps_state’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6127: warning: unused variable ‘i’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_translate_scan’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6234: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6234: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6234: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6234: error: too few arguments to function ‘iwe_stream_add_event’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6244: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6244: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6244: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6244: error: too few arguments to function ‘iwe_stream_add_point’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6255: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6255: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6255: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6255: error: too few arguments to function ‘iwe_stream_add_event’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6263: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6263: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6263: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6263: error: too few arguments to function ‘iwe_stream_add_event’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6277: warning: unknown conversion type character ‘,’ in format
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6277: warning: spurious trailing ‘%’ in format
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6279: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6279: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6279: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6279: error: too few arguments to function ‘iwe_stream_add_point’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6290: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6290: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6290: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6290: error: too few arguments to function ‘iwe_stream_add_point’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6307: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6307: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6307: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6307: error: too few arguments to function ‘iwe_stream_add_value’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6315: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6315: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6315: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6315: error: too few arguments to function ‘iwe_stream_add_value’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6331: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6331: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6331: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6331: error: too few arguments to function ‘iwe_stream_add_point’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6349: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6349: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6349: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6349: error: too few arguments to function ‘iwe_stream_add_point’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_list_bss’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6415: warning: spurious trailing ‘%’ in format
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_ioctl’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:6682: error: implicit declaration of function ‘verify_area’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_load_card_setting’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:7395: error: implicit declaration of function ‘open’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:7412: error: implicit declaration of function ‘read’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:7416: error: implicit declaration of function ‘close’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:7422: warning: suggest parentheses around assignment used as truth value
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_save_card_setting’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:7568: error: implicit declaration of function ‘write’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zdcb_rx_ind’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:8235: error: implicit declaration of function ‘eth_copy_and_sum’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zdcb_AssocRequest’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:8602: error: implicit declaration of function ‘HashSearch’
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:8602: warning: assignment makes pointer from integer without a cast
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘zd1205_set_zd_cbs’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:8658: warning: assignment from incompatible pointer type
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c: In function ‘CalculateQuality’:
/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.c:8858: warning: ISO C90 forbids mixed declarations and code
make[4]: *** [/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed/src/zd1205.o] Error 1
make[3]: *** [_module_/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/home/john/Documents/Downloads/Drivers/Sparklan/Uncompresed'
make: *** [all] Error 2
john@john-laptop:~/Documents/Downloads/Drivers/Sparklan/Uncompresed$ 
-------------------------------------------------------------------------

Does anybody make an executable file that just works? or is this something to be aware of?

Is it that the answer is easy and i just have to remember what to do in the future for this machine?

Thanks guys,  Not sure if ive committed a forum fopar by copy and pasting all that in, just wanted to ensure i was providing all relevant info.  My apolgies if it is.

Thanks in hope of your help!!

---

