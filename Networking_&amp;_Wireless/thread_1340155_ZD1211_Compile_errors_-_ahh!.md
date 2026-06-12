---
title: "ZD1211 Compile errors - ahh!"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by sovvy2009 on 2009-11-28
Hello all,

I'm attempting to compile the drivers for my wireless device (chipset: ZD1211) to use it as a wireless AP (master mode), as the ubuntu driver doesnt support this. However, when I attempt to compile the driver, it comes up with this error:

```
root@bts-desktop:~/Desktop/ZD1211LnxDrv_2_16_0_0# make
/lib/modules/2.6.31-15-generic/build
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0
-I/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -Wno-unused -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DPRODUCTION -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DAAAA03_FIX=1 -DZD1211B -DZDCONF_LP_SUPPORT=0
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zdmisc.o src/zd1211.o
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.o
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
In file included from /home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.h:49,
                 from /home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:42:
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zdcompat.h:69: error: conflicting types for &#8216;irqreturn_t&#8217;
include/linux/irqreturn.h:16: note: previous declaration of &#8216;irqreturn_t&#8217; was here
In file included from /home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.h:49,
                 from /home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:42:
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zdcompat.h:72:1: warning: "IRQ_RETVAL" redefined
In file included from include/linux/interrupt.h:10,
                 from include/linux/netdevice.h:1058,
                 from include/net/sock.h:50,
                 from include/linux/tcp.h:177,
                 from /home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:36:
include/linux/irqreturn.h:17:1: warning: this is the location of the previous definition
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:451: warning: initialization from incompatible pointer type
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;write&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;fd&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;buf&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;count&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: warning: return type defaults to &#8216;int&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c: In function &#8216;_syscall3&#8217;:
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:480: error: expected declaration specifiers before &#8216;_syscall3&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:484: error: expected declaration specifiers before &#8216;;&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: parameter &#8216;dot11A_Channel_Amount&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: &#8216;dot11A_Channel&#8217; undeclared (first use in this function)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: (Each undeclared identifier is reported only once
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:485: error: for each function it appears in.)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:491: error: parameter &#8216;OfdmRateTbl&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:493: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:494: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:495: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:496: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:497: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:498: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:498: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:499: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:499: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:500: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:500: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:501: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:501: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:502: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:502: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:504: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:504: warning: (near initialization for &#8216;OfdmRateTbl&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:507: error: parameter &#8216;OfdmRateTbl_11A&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:509: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:509: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:510: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:510: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:511: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:511: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:512: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:512: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:513: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:514: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:515: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:515: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:516: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:516: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:517: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:517: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:518: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:518: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:521: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:521: warning: (near initialization for &#8216;OfdmRateTbl_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:524: error: storage class specified for parameter &#8216;a_ChannelMap&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:524: error: parameter &#8216;a_ChannelMap&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:525: warning: initialization makes pointer from integer without a cast
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:525: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:525: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:525: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:525: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:526: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:526: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:526: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:526: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:527: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:527: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:527: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:527: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:528: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:528: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:528: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:528: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:529: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:529: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:529: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:529: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:530: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:530: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:530: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:530: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:531: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:531: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:531: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:531: warning: (near initialization for &#8216;a_ChannelMap&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:540: error: storage class specified for parameter &#8216;a_InterpolationStruc&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:542: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;a_InterpolationTbl&#8217;
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:566: error: expected declaration specifiers before &#8216;;&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:582: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:596: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:610: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:623: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:633: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:648: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:678: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:711: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:731: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:751: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:790: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:830: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:869: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:879: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:887: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:898: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:917: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:941: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:947: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:953: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:989: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1001: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1017: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1044: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1054: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1078: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1094: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1123: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1137: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1178: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1226: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1253: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1281: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1300: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1384: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1403: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1443: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1482: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1573: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1615: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1720: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1761: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1787: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1811: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1885: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1957: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:1973: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:2015: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:2291: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:2594: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:2699: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:2786: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3023: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3051: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3070: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3116: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3140: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3165: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3263: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3284: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:3606: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4413: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4522: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4539: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4565: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4592: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4754: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4791: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4853: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4879: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4891: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:4979: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5001: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5211: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5216: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5296: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5332: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5352: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5375: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5454: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5493: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5557: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5571: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5661: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5689: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5846: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:5984: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6007: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6018: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6059: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6069: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6079: error: parameter &#8216;channel_frequency&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: initialization makes pointer from integer without a cast
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6080: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6081: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6083: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6083: warning: (near initialization for &#8216;channel_frequency&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6084: error: parameter &#8216;channel_frequency_11A&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6086: warning: initialization makes pointer from integer without a cast
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6086: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6086: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6087: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6087: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6087: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6087: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6088: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6088: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6088: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6088: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6089: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6089: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6089: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6089: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6090: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6090: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6090: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6090: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6091: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6091: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6091: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6091: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6092: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6092: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6092: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6092: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6093: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6093: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6093: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6093: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6094: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6094: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6094: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6094: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6095: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6095: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6095: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6095: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6096: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6096: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6096: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6096: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6097: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6097: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6097: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6097: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6098: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6098: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6098: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6098: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6099: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6099: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6099: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6099: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6100: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6100: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6100: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6100: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6101: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6101: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6101: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6101: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6102: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6102: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6102: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6102: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6103: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6103: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6103: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6103: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6104: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6104: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6104: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6104: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6106: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6106: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6106: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6106: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6107: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6107: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6107: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6107: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6108: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6108: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6108: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6108: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6109: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6109: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6109: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6109: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6110: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6110: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6110: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6110: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6111: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6111: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6111: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6111: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6112: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6112: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6112: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6112: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6113: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6113: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6113: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6113: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6114: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6114: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6114: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6114: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6115: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6115: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6115: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6115: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6116: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6116: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6116: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6116: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6118: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6118: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6118: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6118: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6119: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6119: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6119: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6119: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6120: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6120: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6120: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6120: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6121: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6121: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6121: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6121: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6122: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6122: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6124: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6124: warning: (near initialization for &#8216;channel_frequency_11A&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6134: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6163: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6289: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6333: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6363: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6373: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6408: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6475: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6499: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6540: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6557: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6563: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6684: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6728: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6743: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6758: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6847: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6853: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6865: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6873: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6905: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6913: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6928: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:6949: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7027: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7121: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7146: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7340: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7397: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7433: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:7560: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8467: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8568: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8686: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:8807: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9054: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9147: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9784: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9793: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:9948: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10043: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10048: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10058: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10068: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10078: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10088: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10141: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10167: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10181: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10192: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10197: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10202: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10208: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10226: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10243: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10254: error: parameter &#8216;next&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10257: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10270: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10276: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10287: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10309: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10326: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10366: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10479: error: parameter &#8216;ZDLOGTEN&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10480: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10481: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10482: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10483: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10484: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10485: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10486: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10487: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10488: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10489: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10490: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10491: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10492: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10493: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10494: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10495: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10496: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10497: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10499: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10499: warning: (near initialization for &#8216;ZDLOGTEN&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10503: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10512: error: parameter &#8216;X_Constant&#8217; is initialized
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: initialization makes pointer from integer without a cast
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10513: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10514: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10515: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10517: warning: excess elements in scalar initializer
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10517: warning: (near initialization for &#8216;X_Constant&#8217;)
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10521: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10578: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10644: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10681: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10693: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10746: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10764: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10791: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10818: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10828: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10873: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10883: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10909: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;{&#8217; token
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: old-style parameter declarations in prototyped function definition
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:479: error: parameter name omitted
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:10921: error: expected &#8216;{&#8217; at end of input
make[2]: *** [/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.o] Error 1
make[1]: *** [_module_/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [all] Error 2

```

Any ideas on what I should do/what i'm doing wrong?

I'm running Karmic, btw.

---

### Post by nixscripter on 2009-11-28
Did you install the kernel headers package for the correct kernel build? You can install **linux-headers** to get them all if you're not sure.

---

### Post by chili555 on 2009-11-28
> make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'Yes, evidently. How about ***build-essential***?

---

### Post by sovvy2009 on 2009-11-29
> **chili555 said:**
> Yes, evidently. How about ***build-essential***?

Yeah, I've got build-essential installed - I tried installing a 'bunch of things' (though I think those were the linux-headers, looking back on it; I think I had build-essential already installed) that various guides told me to install about the issue that I managed to find, with little success.

---

### Post by nixscripter on 2009-11-29
The line that strikes me is:

```
/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory

```

The fact you have a Makefile suggests that if there was a configure script you ran it, which usually is where config.h comes from.

It also seems like there are conflicting headers; it seems to be shipping with some, as evidenced by errors like:

```

/home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zdcompat.h:72:1: warning: "IRQ_RETVAL" redefined
In file included from include/linux/interrupt.h:10,
                 from include/linux/netdevice.h:1058,
                 from include/net/sock.h:50,
                 from include/linux/tcp.h:177,
                 from /home/ben/Desktop/ZD1211LnxDrv_2_16_0_0/src/zd1205.c:36:
include/linux/irqreturn.h:17:1: warning: this is the location of the previous definition

```

Something isn't right with the build process. Maybe the driver's Makefile is screwed up or something.

---

### Post by chili555 on 2009-11-29
> ZD1211LnxDrv_2_16_0_0How old is this? Is there a newer version? I doubt it is likely to compile properly if it is more than a year old, given the evolution of the kernel.

Please give us a link to where this was downloaded.

Also, please see: [https://bugs.launchpad.net/ubuntu/+source/drbd8/+bug/105552](https://bugs.launchpad.net/ubuntu/+source/drbd8/+bug/105552) especially:> symlinking autoconf.h to config.h in /usr/src/linux/include/linux/ seems to fix the initial problem for me, but then there are more build errors in 0.7.You might try:```
cd /usr/src/linux-headers-2.6.31-15-generic/include/linux/
sudo ln -s autoconf.h config.h
```It may help.

---

