---
title: "Realtek Driver Compilation"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by JM Rain on 2011-09-23
Rather than necro an old thread, I'll make my own.  I'm attempting to drive a Realtek driver on my linux kernel.  The following thread describes my situation to the dime: 

[http://ubuntuforums.org/showthread.php?t=1575611](http://ubuntuforums.org/showthread.php?t=1575611)

I've been perusing looking for an answer as to how to get the driver to install, and every working situation involves editing the driver file.  Granted I don't know much about .c files or the compilation thereof, but I did replace "init_MUTEX(pmutex)" with "sema_init(pmutex,1)" in the os_dep/osdep_service.c file using a text editor.  Saved and overwritten.  When I navigate the terminal and run "./install.sh", I get the same compiling error and another program appears to have overwritten my edited osdep_service.c file with the original.  Am I missing something?

---

### Post by chili555 on 2011-09-23
Which of the many files floating around have you downloaded? What kernel version are you running? I'm not sure ./install.sh is the best method in Ubuntu; I'd try, instead:```
cd Desktop/rtl8*   <--or wherever the file exists
sudo su
make clean
make
make install
exit
```

---

### Post by JM Rain on 2011-09-23
I'm using the latest RTL8192CU driver from the Realtek website: 

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

This is an attempt to connect my Alfa AWUS036NHR wireless adapter in Backtrack 5 R1.  My linux kernel is 2.6.39.4 which isn't supported with this particular driver, but nevertheless I should be able to edit the os_dep.c file to make it work.  Thanks for the response, I tried your suggestion with "make install" but still managed to get a "Compile make driver error" message.

---

### Post by chili555 on 2011-09-24
I downloaded the file and on my 2.6.38-11 system, changed the line you referenced. I then did:```
cd Desktop/Forum/JMRain/**RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715**
```Notice I am in the extracted file that contains the Makefile, not the directory containing install.sh. Then I did:```
sudo su
make
```I didn't get any warnings or errors. Please try this method and post back any errors.

---

### Post by JM Rain on 2011-09-24
No luck with that method:

```
root@root:~/Desktop/RTL8192CU_8188CUS_8188CE-
root@root:~/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715# sudo su                                                                                   
root@root:~/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715# make                                                                                      
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.39.4/build M=/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715  modules
make[1]: Entering directory `/usr/src/linux-source-2.6.39.4'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.39.4/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o
In file included from /root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.c:24:
/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/include/osdep_service.h:49:29: error: linux/smp_lock.h: No such file or directory
make[2]: *** [/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/root/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.39.4'
make: *** [modules] Error 2
root@root:~/Desktop/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/rtl8192_8188CU_linux_v3.0.2164.20110715#    
```

I did boot up Backtrack 5 which inherently uses kernel version 2.6.38 and tried this kind of install and it worked like a charm! Granted the Realtek drivers are apparently supported in that kernel version, but I believe I tried the install a week or two ago on Backtrack 5 with no results. Is this a lost cause on the newer kernel?

---

### Post by chili555 on 2011-09-25
> Is this a lost cause on the newer kernel?Maybe not. It's just beyond my knowledge. I'd suggest you Google this:> Module.symvers
           is missing; modules will have no dependencies and modversions.And this:> error: linux/smp_lock.h: No such file or directoryTry to solve each issue and try again. I have compiled a lot of things but never on a custom or vanilla kernel. I'm sorry I could not be of more help.

---

