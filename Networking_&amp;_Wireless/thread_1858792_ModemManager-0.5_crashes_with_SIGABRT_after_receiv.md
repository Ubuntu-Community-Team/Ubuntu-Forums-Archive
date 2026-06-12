---
title: "ModemManager-0.5 crashes with SIGABRT after receiving sms_send response"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by SatyaKishoreK on 2011-10-13
**ModemManager-0.5 crashes with SIGABRT after receiving sms_send response** 			
 			 			 		   		 		 		Hi All,
Here I am facing small issue while sending SMS using ModemManager-0.5 code.
SMS sent using modem-manager code and SAMSUNG Wave (Modem Number : GT-S8566) as modem, modem-manager crashed with SIGABRT.
logs are as follows:
**************************************************  *********
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>  (ttyACM0): --> 'AT+COPS=3,0;+COPS?<CR>'
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>   (ttyACM0): <-- '<CR><LF>+COPS:  0,0,"AirTel",0<CR><LF><CR><LF>OK<CR><LF>'
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>  (ttyACM0): --> 'AT+CIND?<CR>'
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>   (ttyACM0): <-- '<CR><LF>+CIND:  4,5,1,0,0,0,0,0<CR><LF><CR><LF>OK<CR><LF>'
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>  (ttyACM0): --> 'AT+CIND?<CR>'
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>   (ttyACM0): <-- '<CR><LF>+CIND:  4,5,1,0,0,0,0,0<CR><LF><CR><LF>OK<CR><LF>'
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>  (ttyACM0): --> 'AT+CGREG?<CR>'
Sep 26 11:44:03 kishore-desktop modem-manager[912]: <info>   (ttyACM0): <-- '<CR><LF>+CGREG:  2,0<CR><LF><CR><LF>OK<CR><LF>'
Sep 26 11:44:34 kishore-desktop modem-manager[912]: <info>  (ttyACM0): --> 'AT+CIND?<CR>'
Sep 26 11:44:34 kishore-desktop modem-manager[912]: <info>   (ttyACM0): <-- '<CR><LF>+CIND:  4,5,1,0,0,0,0,0<CR><LF><CR><LF>OK<CR><LF>'
Sep 26 11:44:49 kishore-desktop modem-manager[912]: <info>  (ttyACM0): --> 'AT+CMGF=1<CR>'
Sep 26 11:44:49 kishore-desktop modem-manager[912]: <info>  (ttyACM0): <-- '<CR><LF>OK<CR><LF>'
Sep 26 11:44:49 kishore-desktop modem-manager[912]: <info>   (ttyACM0): --> 'AT+CMGS="9701023336"<CR>haihello\26<CR>'
Sep 26 11:44:49 kishore-desktop modem-manager[912]: <info>   (ttyACM0): <-- '<CR><LF>> <CR><LF>'
Sep 26 11:44:51 kishore-desktop modem-manager[912]: <info>   (ttyACM0): <-- '<CR><LF>+CMGS:  71<CR><LF><CR><LF>OK<CR><LF>'
Sep 26 11:44:51 kishore-desktop modem-manager[912]: out of memory
Sep 26 11:44:51 kishore-desktop NetworkManager[910]: <info> the modem manager disappeared
Sep 26 11:44:51 kishore-desktop NetworkManager[910]: <info> (ttyACM0): now unmanaged
Sep 26 11:44:51 kishore-desktop NetworkManager[910]: <info> (ttyACM0): device state change: 3 -> 1 (reason 36)
Sep 26 11:44:51 kishore-desktop NetworkManager[910]: <info> (ttyACM0): cleaning up...
Sep 26 11:44:51 kishore-desktop NetworkManager[910]: <info> (ttyACM0): taking down device.
Sep 26 11:44:51 kishore-desktop NetworkManager[910]: <info> trying to start the modem manager...
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  ModemManager (version 0.5) starting...
Sep 26 11:44:52 kishore-desktop NetworkManager[910]: <info> modem-manager is now available
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Generic
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Novatel
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin X22X
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Nokia
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Gobi
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Longcheer
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Ericsson MBM
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin ZTE
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Option High-Speed
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin MotoC
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Sierra
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Samsung
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin SimTech
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Huawei
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Linktop
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin AnyData
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Wavecom
Sep 26 11:44:52 kishore-desktop modem-manager[3442]: <info>  Loaded plugin Option
**************************************************  ****
gdb logs :
The modem manager code crashes after calling "dbus_g_method_return" call   which is in function  "async_call_done " of  file  "mm-modem-gsm-sms.c". The gdb logs are as follows:
**************************************************  ************
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Attaching to process 4854
Reading symbols from /usr/local/sbin/modem-manager...done.
Reading symbols from /usr/lib/libgudev-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgudev-1.0.so.0
Reading symbols from /usr/lib/libdbus-glib-1.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-glib-1.so.2
Reading symbols from /lib/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libdbus-1.so.3
Reading symbols from /lib/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
Loaded symbols for /lib/libpthread.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/librt.so.1
Reading symbols from /lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libglib-2.0.so.0
Reading symbols from /lib/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/libc.so.6
Reading symbols from /lib/libudev.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libudev.so.0
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /lib/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/libdl.so.2
Reading symbols from /lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/libpcre.so.3
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-generic.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-generic.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-novatel.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-novatel.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-x22x.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-x22x.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-nokia.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-nokia.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-gobi.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-gobi.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-longcheer.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-longcheer.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-mbm.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-mbm.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-zte.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-zte.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-hso.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-hso.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-moto-c.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-moto-c.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-sierra.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-sierra.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-samsung.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-samsung.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-simtech.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-simtech.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-huawei.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-huawei.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-linktop.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-linktop.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-anydata.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-anydata.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-wavecom.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-wavecom.so
Reading symbols from /usr/local/lib/ModemManager/libmm-plugin-option.so...done.
Loaded symbols for /usr/local/lib/ModemManager/libmm-plugin-option.so
0x00f20832 in ?? () from /lib/ld-linux.so.2
(gdb) b invoke_mm_modem_fn
Breakpoint 1 at 0x8052e06: file mm-callback-info.c, line 25.
(gdb) c
Continuing.
Breakpoint 1, invoke_mm_modem_fn (info=0x95c8850) at mm-callback-info.c:25
warning: Source file is more recent than executable.
25    {
(gdb) vt
Undefined command: "vt".  Try "help".
(gdb) bt
#0  invoke_mm_modem_fn (info=0x95c8850) at mm-callback-info.c:25
#1  0x08052b6b in callback_info_done (user_data=0x95c8850) at mm-callback-info.c:84
#2  0x001d4e44 in ?? () from /lib/libglib-2.0.so.0
#3  0x001d5477 in ?? () from /lib/libglib-2.0.so.0
#4  0x001d58a6 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#5  0x001d9668 in ?? () from /lib/libglib-2.0.so.0
#6  0x001d9ba7 in g_main_loop_run () from /lib/libglib-2.0.so.0
#7  0x080520a6 in main (argc=1, argv=0xbf93df34) at main.c:199
(gdb) s
26        MMModemFn callback = (MMModemFn) info->callback;
(gdb) 
29        if (callback) {
(gdb) 
async_call_done (modem=0x95ce008, error=0x0, user_data=0x95b685:cool: at mm-modem-gsm-sms.c:84
84    {
(gdb) p context
$1 = <value optimized out>
(gdb) p user_data
$2 = (gpointer) 0x95b6858
(gdb) s
87        if (error)
(gdb) p context
$3 = <value optimized out>
(gdb) p user_data
$4 = (gpointer) 0x95b6858
(gdb) s
90            dbus_g_method_return (context);
(gdb) 
91    }
(gdb) 
async_call_done (modem=0x95c8850, error=0x0, user_data=0x95b685:cool: at mm-modem-gsm-sms.c:90
90            dbus_g_method_return (context);
(gdb) 
0x00119c40 in dbus_g_method_return () from /usr/lib/libdbus-glib-1.so.2
(gdb) 
Single stepping until exit from function dbus_g_method_return,
which has no line number information.
Program received signal SIGABRT, Aborted.
0x00f20832 in ?? () from /lib/ld-linux.so.2
(gdb) bt
#0  0x00f20832 in ?? () from /lib/ld-linux.so.2
#1  0x0091d941 in raise () from /lib/libc.so.6
#2  0x00920e42 in abort () from /lib/libc.so.6
#3  0x001e0536 in g_logv () from /lib/libglib-2.0.so.0
#4  0x001e0572 in g_log () from /lib/libglib-2.0.so.0
#5  0x0012367d in ?? () from /usr/lib/libdbus-glib-1.so.2
#6  0x00122125 in ?? () from /usr/lib/libdbus-glib-1.so.2
#7  0x00119ef8 in dbus_g_method_return () from /usr/lib/libdbus-glib-1.so.2
#8  0x08052e26 in invoke_mm_modem_fn (info=0x95c8850) at mm-callback-info.c:29
#9  0x08052b6b in callback_info_done (user_data=0x95c8850) at mm-callback-info.c:84
#10 0x001d4e44 in ?? () from /lib/libglib-2.0.so.0
#11 0x001d5477 in ?? () from /lib/libglib-2.0.so.0
#12 0x001d58a6 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#13 0x001d9668 in ?? () from /lib/libglib-2.0.so.0
#14 0x001d9ba7 in g_main_loop_run () from /lib/libglib-2.0.so.0
#15 0x080520a6 in main (argc=1, argv=0xbf93df34) at main.c:199
(gdb)
**************************************************  **************************************************

   I am using desktop system with Ubuntu-10.10 (32-bit). And ModemManager-0.5 version which is taken from the following site. 
[http://cgit.freedesktop.org/ModemManager/ModemManager/](http://cgit.freedesktop.org/ModemManager/ModemManager/)

Can any one help me regarding this.

Regards,
Satya.

---

