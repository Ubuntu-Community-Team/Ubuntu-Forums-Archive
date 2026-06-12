---
title: "Ndiswrapper won't install"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by maartennoom on 2009-10-31
I installed Kubuntu 9.1 on a standard issue Asus pundit computer. I have a asus v138g wireless card in there. I don't have wired internet.
the command lspci recognized the card and the broadcom chipset, so far so good.
In order to get the wireless working I apparantly need to install the windows driver with Ndiswrapper. 
 
So, I downloaded the ndiswrapper package for the 9.1 ubuntu on another pc.
I checked my kernel version 2.6.31 so that should be fine
I'm not really sure how to check for header files for the kernel but I assumed I had those. 
 
Unwrapped the package, went to the new directory.
I then made a link:
 
*sudo ln -s /usr/src/linux-headers-2.6.31-11 /lib/modules/2.6.31-11-generic/build*
*[sudo] password:*
*ln: creating symbolic link `/lib/modules/2.6.31-11-generic/build/linux-headers-2.6.31-11': File exists*
 
(for generating the output I ran the command again)
 
Then I ran Make:
*~/Downloads/ndiswrapper-1.54$** sudo make*
*make -C driver*
*make[1]: Entering directory `/home/maarten/Downloads/ndiswrapper-1.54/driver'*
*make -C /usr/src/linux-headers-2.6.31-11-generic M=/home/maarten/Downloads/ndiswrapper-1.54/driver*
*make[2]: Entering directory `/usr/src/linux-headers-2.6.31-11-generic'*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/crt_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/crt.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/hal_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/hal.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/ndis_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/ndis.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io.o*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io.c: In function ‘IoConnectInterrupt’:*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io.c:566: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type*
*include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int, void *)’*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/rtl_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/rtl.o*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.o*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.c:1747: error: unknown field ‘poll_controller’ specified in initializer*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.c:1747: warning: initialization from incompatible pointer type*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.c:1747: error: expected ‘}’ before ‘;’ token*
*make[3]: *** [/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.o] Error 1*
*make[2]: *** [_module_/home/maarten/Downloads/ndiswrapper-1.54/driver] Error 2*
*make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-11-generic'*
*make[1]: *** [modules] Error 2*
*make[1]: Leaving directory `/home/maarten/Downloads/ndiswrapper-1.54/driver'*
*make: *** [all] Error 2*
 
Noted the error but didn't what to do with that ran make install:
 
*maarten@Media-HdK:~/Downloads/ndiswrapper-1.54$** sudo make install*
*make -C driver install*
*make[1]: Entering directory `/home/maarten/Downloads/ndiswrapper-1.54/driver'*
*make -C /usr/src/linux-headers-2.6.31-11-generic M=/home/maarten/Downloads/ndiswrapper-1.54/driver*
*make[2]: Entering directory `/usr/src/linux-headers-2.6.31-11-generic'*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/crt_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/crt.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/hal_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/hal.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/ndis_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/ndis.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel.o*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io.o*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io.c: In function ‘IoConnectInterrupt’:*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/ntoskernel_io.c:566: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type*
*include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int, void *)’*
*MKEXPORT /home/maarten/Downloads/ndiswrapper-1.54/driver/rtl_exports.h*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/rtl.o*
*CC [M] /home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.o*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.c:1747: error: unknown field ‘poll_controller’ specified in initializer*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.c:1747: warning: initialization from incompatible pointer type*
*/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.c:1747: error: expected ‘}’ before ‘;’ token*
*make[3]: *** [/home/maarten/Downloads/ndiswrapper-1.54/driver/wrapndis.o] Error 1*
*make[2]: *** [_module_/home/maarten/Downloads/ndiswrapper-1.54/driver] Error 2*
*make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-11-generic'*
*make[1]: *** [modules] Error 2*
*make[1]: Leaving directory `/home/maarten/Downloads/ndiswrapper-1.54/driver'*
*make: *** [install] Error 2*
 
After this, running the command 'ndiswrapper' doesn't really do anything, it doesn't recognize the program.
So the problem is: what did I do wrong in installing Ndiswrapper?
 
Help.

---

### Post by epk15 on 2009-10-31
Same problem here!!  I had the driver for my netgear wpn111, which I installed via ndiswrapper-1.55 and it worked well with 9.04.  But after upgrading to 9.10 my usb adapter is no longer recognized and it seems that ubuntu doesn't recognize ndiswrapper as a command.  So I used the locate command to locate all files having to do with ndiswrapper and loadndisdriver.  I then deleted these files and tried 
re-installing everything by using the exact same procedure that I used to make the usb adapter work with 9.04.  I did pretty much the same thing that you did and got the same results.  I'm gonna see if there is a newer version of ndiswrapper.  I'll let you know if I can get anything to work.

---

### Post by notbad on 2009-11-01
same thing..9.04 worked like a charm but 9,10 does not install.dont know what to do anymore....

---

### Post by maartennoom on 2009-11-01
As long as you have to struggle this much to get elementary, off the shelf and most of all: common hardware working, Linux will NOT be a success for regular consumers.
 
I really like the idea and would love to get rid of Windows. Linux might look just as fancy, its structure might be better than windows, it might be free and it might have a large community of geeks behind it but it still just doesn't deliver. To bad. :(

---

### Post by notbad on 2009-11-01
i can install ndiswrapper from live cd, but it just dont do anything...
 
i think the best for me would be buying a new and newer wireless adapter

---

### Post by maartennoom on 2009-11-01
And people say windows vista forces people to buy new hardware....

---

### Post by TheLoFiGuy on 2009-11-02
I have the same problem too, it worked just fine in 9.04 but now no luck at all I get the same output and everything

---

### Post by blueidealist on 2009-11-11
exact same problem - sorry, but no answers and very frustrating

---

### Post by dmizer on 2009-11-11
So ... you've tried to install ndiswrapper via synaptic package manager and failed? You will only RARELY need to install ndiswrapper via source code, especially considering that the version in the Karmic repositories is the same as what you can download from the ndis site.

Try running this command:
```
sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by theAmazingP on 2009-11-16
> **maartennoom said:**
> As long as you have to struggle this much to get elementary, off the shelf and most of all: common hardware working, Linux will NOT be a success for regular consumers.
 
I really like the idea and would love to get rid of Windows. Linux might look just as fancy, its structure might be better than windows, it might be free and it might have a large community of geeks behind it but it still just doesn't deliver. To bad. :(

Couldn't agree more...

Same problems here. Karmic Koala, netgear wg111 checked.. However, ndiswrapper won't install through my live cd, neither through the package manager (it says that there are some common scripts missing or sth). So I downloaded some versions which keep hurling errors at me when i'm using apt-get installation. I don't know what to do. I would give you more details, but I'm in a bit of a hurry now.

---

### Post by ArcaVex on 2009-11-16
I can't vouch for karmic, but wg111t works fine on 9.04.

I used the GTK version of ndiswrapper because i had no luck at all with the cli version. Even though the same information was entered.

---

### Post by jamesjpa on 2009-11-16
I too couldn't get ndiswrapper to install using cd or the download commands (such as the one dmizer mentioned) to install from web. 

I had upgraded from 9.04 to 9.10. I just thought maybe the upgrade didn't go through to well so I installed a fresh clean copy but still had the same problem!

Not sure why it wouldn't install but used the gtk one and that worked fine.

To install ndiswrapper (with lan port connected):
```
sudo apt-get install ndisgtk
```

Install the windows driver:
```
sudo ndiswrapper -i /driver_location/inf_file.inf
```

Check driver is installed:
```
ndiswrapper -l
```

Load module:
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```

Add to startup:
```
sudo ndiswrapper -m
```

---

### Post by dank_hippy on 2009-11-16
well. it sucks but its also relieving to know that i'm not the only one with this problem then. i'm new to ubuntu and have started with 9.10. its nice knowing i wasn't just screwing things up because i'm new to it. i got the exact same thing going on.

some help on this would be awesome.

---

### Post by dank_hippy on 2009-11-16
and on that note. ndisgtk wont work either. its fine until the modprobe step:::

luke@ubuntu:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndisgtk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
luke@ubuntu:~$ sudo ndiswrapper -i /ndiswrapper-1.55/driver/WLCOMALL.inf
driver wlcomall is already installed
luke@ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wlcomall : driver installed
    device (049F:0076) present
luke@ubuntu:~$ sudo depmod -a
luke@ubuntu:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
luke@ubuntu:~$

---

