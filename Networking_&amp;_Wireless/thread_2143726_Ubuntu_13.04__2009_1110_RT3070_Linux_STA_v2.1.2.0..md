---
title: "Ubuntu 13.04  2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by Techie1996 on 2013-05-09
I recently bought asus - ieee 802.11n usb - wi-fi adapter for my Dell Latitude e6400 running Ubuntu 13.04 Raring Ringtail.

My objective is to upgrade my wireless card, because for some reason my wireless card shuts off after a lot of stress.

I was following these instructions:

[I][B][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]1.)Download the driver from #17 by chili555(2009_1110_RT3070_Linux_STA_v2.1.2.0)[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]2.)Extract it to your Desktop (or anywhere, but I used thatone)[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]Basicallyif you double-click on it the Archive Manager will start and you needto choose where to Extract.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]3.)Go to the folder[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]code:[/SIZE][/FONT][/COLOR][/B][/I]
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]cd/home/redsultan/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0[/SIZE][/FONT][/COLOR]***
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]4.)code:[/SIZE][/FONT][/COLOR]***
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]sudomake[/SIZE][/FONT][/COLOR]***
[I][B][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2](obviouslyit will ask for your sudo/administrator password)[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]5.)code:[/SIZE][/FONT][/COLOR][/B][/I]
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]makeinstall[/SIZE][/FONT][/COLOR]***
[I][B][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]6.)Create two files in the next steps:[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]code:[/SIZE][/FONT][/COLOR][/B][/I]
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]gedit/etc/udev/rules.d/network_drivers.rules[/SIZE][/FONT][/COLOR]***
[I][B][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]thenwhen the text editor opens up[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]copyand paste the followings exactly as it is. case and all, quotes andall:[/SIZE][/FONT][/COLOR][/B][/I]
***[COLOR=#4169e1][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]ACTION=="add",SUBSYSTEM=="usb", ATTR{idVendor}=="0b05",ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qbart3070sta"[/SIZE][/FONT][/COLOR]***
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]saveand close the text editor.[/SIZE][/FONT][/COLOR]***
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]gedit/etc/modprobe.d/network_drivers.conf[/SIZE][/FONT][/COLOR]***
***[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]thecopy and paste as above:[/SIZE][/FONT][/COLOR]***
***[COLOR=#4169e1][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]installrt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS;/bin/echo "0b05 1784" >/sys/bus/usb/drivers/rt2870/new_id[/SIZE][/FONT][/COLOR]***
[I][B][COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]saveand close text editor.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]7.)plug the USB device in (mine wasn't recognized until Irestarted...)[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]8.)exit terminal window[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]9.)restart system[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]10.)configure your wireless[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]11.)enjoy. [/SIZE][/FONT][/COLOR]:grin:

[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]Ihope I didn't miss anything... Good luck.[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntubeta, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]PS:it's worth to mention that I had to fiddle with the router, toobecause for some reason it just didn't let the USB to connect, I ranthe router's connection wizard and that solved my last problem.


[/SIZE][/FONT][/COLOR][/B][/I][COLOR=#000000][FONT=Ubuntubeta]And when I tried ***sudo make******, ***I received this:

[/FONT][/COLOR]tony@tony-Latitude-E6400:~/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0$ sudo make
[sudo] password for tony: 
make -C tools
make[1]: Entering directory `/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/3.8.0-20-generic/build SUBDIRS=/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-20-generic'
  CC [M]  /home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709:2: error: implicit declaration of function ‘init_MUTEX’ [-Werror=implicit-function-declaration]
/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710:2: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type [enabled by default]
In file included from /home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rt_config.h:57:0,
                 from /home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:37:
/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704:13: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
cc1: some warnings being treated as errors
make[2]: *** [/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/tony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-20-generic'
make: *** [LINUX] Error 2

Any help? I don't receive the actual adapter for another 5 days or so, but I wanted to go ahead and install the drivers so that I could just plug and play. 


[COLOR=#000000][FONT=Ubuntubeta]

[/FONT][/COLOR]

---

### Post by chili555 on 2013-05-10
This driver and the process described are far too old for Ubuntu [COLOR="#FF0000"]13[/COLOR].04:> [COLOR="#FF0000"]2009[/COLOR]_1110_RT3070_Linux_STA_v2.1.2.0As a matter of fact, this device should plug and play using the built in driver rt2800usb with no further steps. Please post back if not.

Subscribed.

---

### Post by Techie1996 on 2013-05-15
It works perfectly! No setup just plug and play. I had seen some people had some problems when I went looking around. Speed is twice as fast. I'd recommend this to anyone!

---

