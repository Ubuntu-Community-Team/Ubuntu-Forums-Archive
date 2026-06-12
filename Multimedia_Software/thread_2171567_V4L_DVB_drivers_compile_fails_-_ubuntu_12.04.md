---
title: "V4L DVB drivers compile fails - ubuntu 12.04"
date: 2013-08-31
forum: Multimedia Software
---

### Post by shlomicthailand on 2013-08-31
[COLOR=#000000]Hi guys [/COLOR]

[COLOR=#000000]i'm new here , and have some experience with ubuntu but first time i try to compile something here.[/COLOR]
[COLOR=#000000]i have upgraded my ubuntu from 10.04 -> 12.04 [/COLOR]

[COLOR=#000000]i have a DVB-T dongle i'm trying to compile the V4L for it - according to this guide [/COLOR][http://linuxtv.org/wiki/index.php/Ho...Device_Drivers]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")
[COLOR=#000000]i also installed linux-sources-3.2.0-52[/COLOR]
[COLOR=#000000]but there is a compilel error i'm not able to find answer to [/COLOR]

[COLOR=#000000]here it is [/COLOR]



[COLOR=#000000]CC [M] /home/shlomic/v4l/media_build/v4l/v4l2-clk.o[/COLOR]
[COLOR=#000000]CC [M] /home/shlomic/v4l/media_build/v4l/v4l2-async.o[/COLOR]
[COLOR=#000000]CC [M] /home/shlomic/v4l/media_build/v4l/v4l2-of.o[/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_parse_csi_bus':[/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c:38:4: error: implicit declaration of function 'of_prop_next_u32' [-Werror=implicit-function-declaration][/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c:38:9: warning: assignment makes pointer from integer without a cast [enabled by default][/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_get_next_endpoint':[/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c:176:3: error: implicit declaration of function 'of_get_child_by_name' [-Werror=implicit-function-declaration][/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c:176:8: warning: assignment makes pointer from integer without a cast [enabled by default][/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c:180:8: warning: assignment makes pointer from integer without a cast [enabled by default][/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_get_remote_port_parent':[/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c:238:2: warning: passing argument 1 of 'of_parse_phandle' discards 'const' qualifier from pointer target type [enabled by default][/COLOR]
[COLOR=#000000]include/linux/of.h:230:28: note: expected 'struct device_node *' but argument is of type 'const struct device_node *'[/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c: In function 'v4l2_of_get_remote_port':[/COLOR]
[COLOR=#000000]/home/shlomic/v4l/media_build/v4l/v4l2-of.c:262:2: warning: passing argument 1 of 'of_parse_phandle' discards 'const' qualifier from pointer target type [enabled by default][/COLOR]
[COLOR=#000000]include/linux/of.h:230:28: note: expected 'struct device_node *' but argument is of type 'const struct device_node *'[/COLOR]
[COLOR=#000000]cc1: some warnings being treated as errors[/COLOR]
[COLOR=#000000]make[3]: *** [/home/shlomic/v4l/media_build/v4l/v4l2-of.o] Error 1[/COLOR]
[COLOR=#000000]make[2]: *** [_module_/home/shlomic/v4l/media_build/v4l] Error 2[/COLOR]
[COLOR=#000000]make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic'[/COLOR]
[COLOR=#000000]make[1]: *** [default] Error 2[/COLOR]
[COLOR=#000000]make[1]: Leaving directory `/home/shlomic/v4l/media_build/v4l'[/COLOR]
[COLOR=#000000]make: *** [all] Error 2[/COLOR]
[COLOR=#000000]build failed at ./build line 454.[/COLOR]
[COLOR=#000000]shlomic@shlomic-ubuntu:~/v4l/media_build$

thanks[/COLOR]

---

### Post by Filip_Marinic on 2014-06-11
You should upgrade to a more recent kernel and try to compile again, because the header files in your kernel do not support some of the functions in the driver. 
(e.g. function "of_prop_next_u32" is not declared in "/usr/src/linux-headers-3.2.0-52/include/linux/of.h")

---

