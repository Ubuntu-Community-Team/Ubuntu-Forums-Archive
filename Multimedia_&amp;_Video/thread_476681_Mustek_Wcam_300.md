---
title: "Mustek Wcam 300"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by kashey_be on 2007-06-17
Hello dear Ubuntu users,

Was anyone capable of activating a NW802 based webcam with linux?
I was trying to follow the guide here:
[[COLOR="RoyalBlue"]http://nw802.sourceforge.net/faq.html[/COLOR]]("http://nw802.sourceforge.net/faq.html")
However all I get is errors of this sort:

###############################
gcc -O3 -D__KERNEL__ -DMODULE -Wall -DMODVERSIONS -funroll-loops -frerun-cse-after-loop -funroll-all-loops -fomit-frame-pointer -nostdinc -I /usr/src/linux/include -I `dirname \`gcc -print-libgcc-file-name\``/include/ -include /usr/src/linux/include/linux/modversions.h -c -o usbvideo.o usbvideo.c
cc1: error: /usr/src/linux/include/linux/modversions.h: No such file or directory
In file included from /usr/src/linux/include/linux/kernel.h:11,
                 from usbvideo.c:17:
/usr/src/linux/include/linux/linkage.h:4:25: error: asm/linkage.h: No such file or directory
In file included from /usr/src/linux/include/linux/posix_types.h:47,
                 from /usr/src/linux/include/linux/types.h:14,
                 from /usr/src/linux/include/linux/kernel.h:13,
                 from usbvideo.c:17:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/asm/posix_types.h:13:22: error: features.h: No such file or directory
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/asm/posix_types.h:14:35: error: no include path in which to search for asm/posix_types.h
In file included from /usr/src/linux/include/linux/kernel.h:13,
                 from usbvideo.c:17:
/usr/src/linux/include/linux/types.h:15:23: error: asm/types.h: No such file or directory
In file included from /usr/src/linux/include/linux/kernel.h:13,
                 from usbvideo.c:17:
/usr/src/linux/include/linux/types.h:19: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;__kernel_dev_t&#8217;
/usr/src/linux/include/linux/types.h:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;dev_t&#8217;
/usr/src/linux/include/linux/types.h:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ino_t&#8217;
/usr/src/linux/include/linux/types.h:24: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;mode_t&#8217;
/usr/src/linux/include/linux/types.h:25: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;nlink_t&#8217;
/usr/src/linux/include/linux/types.h:26: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;off_t&#8217;
/usr/src/linux/include/linux/types.h:27: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;pid_t&#8217;
/usr/src/linux/include/linux/types.h:28: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;daddr_t&#8217;
/usr/src/linux/include/linux/types.h:30: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;suseconds_t&#8217;
/usr/src/linux/include/linux/types.h:31: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;timer_t&#8217;
/usr/src/linux/include/linux/types.h:32: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;clockid_t&#8217;
/usr/src/linux/include/linux/types.h:38: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;uid_t&#8217;
/usr/src/linux/include/linux/types.h:39: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;gid_t&#8217;
/usr/src/linux/include/linux/types.h:40: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;uid16_t&#8217;
/usr/src/linux/include/linux/types.h:41: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;gid16_t&#8217;
/usr/src/linux/include/linux/types.h:58: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;loff_t&#8217;
/usr/src/linux/include/linux/types.h:67: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;size_t&#8217;
/usr/src/linux/include/linux/types.h:72: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ssize_t&#8217;
/usr/src/linux/include/linux/types.h:77: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ptrdiff_t&#8217;
/usr/src/linux/include/linux/types.h:82: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;time_t&#8217;
/usr/src/linux/include/linux/types.h:87: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;clock_t&#8217;
/usr/src/linux/include/linux/types.h:92: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;caddr_t&#8217;
/usr/src/linux/include/linux/types.h:110: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u_int8_t&#8217;
/usr/src/linux/include/linux/types.h:111: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;int8_t&#8217;
/usr/src/linux/include/linux/types.h:112: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u_int16_t&#8217;
/usr/src/linux/include/linux/types.h:113: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;int16_t&#8217;
/usr/src/linux/include/linux/types.h:114: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u_int32_t&#8217;
/usr/src/linux/include/linux/types.h:115: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;int32_t&#8217;
/usr/src/linux/include/linux/types.h:119: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;uint8_t&#8217;
/usr/src/linux/include/linux/types.h:120: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;uint16_t&#8217;
/usr/src/linux/include/linux/types.h:121: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;uint32_t&#8217;
###############################

and it goes on like this until it just sends exit code 1.

I installed linux-sources, untarred the file in /usr/src and put up a symbolic link /usr/src/linux that points to sourced directory.

Would appreciate any sort help,
Thanks in advance.

---

### Post by merwizard on 2007-06-17
Just a quick answer

I've got a Mustek Wcamm 300A and it uses the gspca module (and works fine). ([http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)) Also, as a general rule, Ubuntu makes use of a nifty program called "module-assistant" which automates the process of compiling and installing modules (get it with synaptic).
In your case, you should download and install at least the kernel-headers package, if not the kernel-sources packages.

I am not sure if "module-assistant" will solve all your dependecies, so, at least go for the "kernel headers" package

---

