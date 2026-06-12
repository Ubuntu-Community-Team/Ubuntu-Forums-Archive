---
title: "Errors with Compat-Wireless Installation"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by duffingr on 2011-07-11
Hi all,

I am following this guide with Ubuntu 10.10 installed: 

[http://aircrack-ng.org/doku.php?id=compat-wireless&s#compat-wireless](http://aircrack-ng.org/doku.php?id=compat-wireless&s#compat-wireless)

I have gotten to the point where I am using the command "make". When I do this I get some errors. I have followed the guide to the letter at this point. Wondering if anyone can help. I installed the latest gcc, but still a no go. Here is my output:

```

jortgonfreit@FuManchu:~/compat-wireless-2011-07-08$ make
make -C /lib/modules/2.6.35-22-generic/build M=/home/jortgonfreit/compat-wireless-2011-07-08 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.o
/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.c:13: warning: "pr_fmt" redefined
include/linux/kernel.h:381: note: this is the location of the previous definition
/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.c: In function ‘b44_init_one’:
/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.c:2141: error: implicit declaration of function ‘pr_info_once’
make[3]: *** [/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.o] Error 1
make[2]: *** [/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net] Error 2
make[1]: *** [_module_/home/jortgonfreit/compat-wireless-2011-07-08] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2

```Thanks in advance.

---

### Post by chili555 on 2011-07-11
Can you confirm that you have the required build tools installed?```
sudo apt-get install build-essential
```It seems to be stumbling in the process of building the ethernet driver b44. I doubt that is required for aircrack! Did you use the driver-select utility to specify which wireless driver you want? From the README:> Selecting your driver
---------------------

If you know the driver you want you can select it with our
helper script:

./scripts/driver-select

Run that script to see more information. 
Not all drivers are currently enabled via driver-select.I suggest you try:```
./scripts/driver-select restore
./scripts/driver-select <your_needed_driver>
make
```

---

### Post by mosttornbrain on 2011-07-11
> **duffingr said:**
> Hi all,
 
I am following this guide with Ubuntu 10.10 installed: 
 
[http://aircrack-ng.org/doku.php?id=compat-wireless&s#compat-wireless](http://aircrack-ng.org/doku.php?id=compat-wireless&s#compat-wireless)
 
I have gotten to the point where I am using the command "make". When I do this I get some errors. I have followed the guide to the letter at this point. Wondering if anyone can help. I installed the latest gcc, but still a no go. Here is my output:
 
```

jortgonfreit@FuManchu:~/compat-wireless-2011-07-08$ make
make -C /lib/modules/2.6.35-22-generic/build M=/home/jortgonfreit/compat-wireless-2011-07-08 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.o
/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.c:13: warning: "pr_fmt" redefined
include/linux/kernel.h:381: note: this is the location of the previous definition
/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.c: In function ‘b44_init_one’:
/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.c:2141: error: implicit declaration of function ‘pr_info_once’
make[3]: *** [/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net/b44.o] Error 1
make[2]: *** [/home/jortgonfreit/compat-wireless-2011-07-08/drivers/net] Error 2
make[1]: *** [_module_/home/jortgonfreit/compat-wireless-2011-07-08] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2

```Thanks in advance.
 
I coincidentally ran into this same issue with ubuntu 10.10 trying to compile the most recent version of compat-wireless. A simple work-around is to edit b44.c and comment out line 2141. The functionality of other drivers will not be affected.
 
You'll get another error compiling the second driver in the "stable" subdirectory (I don't recall the name off the top of my head). A work-around for that is to just edit the makefile and comment out the line which tries to compile that driver. Assuming you don't actually need support for that driver, everything should then compile successfully.
 
Cheers,
Brian

---

