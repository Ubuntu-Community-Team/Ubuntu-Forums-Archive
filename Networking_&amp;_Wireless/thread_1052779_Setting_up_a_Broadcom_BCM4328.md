---
title: "Setting up a Broadcom BCM4328"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by mpl34 on 2009-01-28
I am completely new to linux and am having a tough time installing drivers for my broadcom wireless chipset. 

After installing linux I immediately updated and upgraded. I then tired to follow  the tutorial for compiling the broadcom STA driver given [here]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&itemid=61"),

I am using a dell vostro1500, below are the details of my wireless card and the errors i had while following the tutorial.

I would appreciate any advice on what i am doing wrong or what i need to do, if you require any extra information please give the command i need to use.

-------------------------------------------------------------------------------------------------------

2.6.27-7-generic

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Dell Device 000a
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
        Memory at f0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb, wl

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Dell Device 000a
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f9ffc000 (64-bit, non-prefetchable) [size=16K]
        Memory at f0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb, wl

-------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd` clean

make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
michael@michael-laptop:~/hybrid$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/michael/hybrid/built-in.o
  CC [M]  /home/michael/hybrid/src/wl/sys/wl_linux.o
  CC [M]  /home/michael/hybrid/src/wl/sys/wl_iw.o
  CC [M]  /home/michael/hybrid/src/shared/linux_osl.o
/home/michael/hybrid/src/shared/linux_osl.c: In function &#8216;osl_printf&#8217;:
/home/michael/hybrid/src/shared/linux_osl.c:456: warning: format not a string literal and no format arguments
  LD [M]  /home/michael/hybrid/wl.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/michael/hybrid/wl.o
see include/linux/module.h for more information
  CC      /home/michael/hybrid/wl.mod.o
  LD [M]  /home/michael/hybrid/wl.ko
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

--------------------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ sudo modprobe -r b43 ssd ndiswrapper wl

FATAL: Module ssd not found.

--------------------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ sudo modprobe ieee80211_crypt_tkip
michael@michael-laptop:~/hybrid$ sudo insmod wl.ko

insmod: error inserting 'wl.ko': -1 File exists

--------------------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ /etc/init.d/networking restart

 * Reconfiguring network interfaces...ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
rm: cannot remove `/var/run/network/initialized': Permission denied

--------------------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ /etc/rc.d/network restart

bash: /etc/rc.d/network: No such file or directory

---

### Post by kreggz on 2009-01-28
did you try this?

type:

jockey-kde

and it should allow you to automatically install them.

---

### Post by Ayuthia on 2009-01-28
> **mpl34 said:**
> 
michael@michael-laptop:~/hybrid$ sudo modprobe -r b43 ssd ndiswrapper wl

FATAL: Module ssd not found.
ssd should have been ssb.

> 
--------------------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ sudo modprobe ieee80211_crypt_tkip
michael@michael-laptop:~/hybrid$ sudo insmod wl.ko

insmod: error inserting 'wl.ko': -1 File exists

There is already a wl module that is in use at the time.  The modprobe -r command above failed because it could not find ssd.

> 
--------------------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ /etc/init.d/networking restart

 * Reconfiguring network interfaces...ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
rm: cannot remove `/var/run/network/initialized': Permission denied
That one should have been sudo /etc/init.d/networking restart.  I'll get the documentation updated.

> --------------------------------------------------------------------------------------------------------------------

michael@michael-laptop:~/hybrid$ /etc/rc.d/network restart

bash: /etc/rc.d/network: No such file or directory

This command is for Arch users, not Ubuntu.  The file is not there in Ubuntu.


As kreggz mentioned in the previous post, did you try out the Broadcom STA module from System->Administration->Hardware Drivers?  If I recall correctly the versions are different between the website version and Ubuntu only because Broadcom released a new update recently.

---

### Post by mpl34 on 2009-01-28
Thanks for the quick replies, I have tried to install the STA driver thru System->Administration->Hardware Drivers but when i clickd on the activate button nothing happened, the hardware driver window freezes but otherwise everything else worked fine. I thought this may have meant that it takes awhile to activate but after 20min i thoughout maybe not.

thanx for noting the ssd and sudo mistake i'm at work atm but will give it another shot once i get home

Thanx,

---

### Post by kreggz on 2009-01-28
it can take a while from my experience. last time I walked away from the pc and left it to download.

---

### Post by mpl34 on 2009-01-30
Hey

Still having problems using the hardware drivers manager has been unsuccessful. I am still getting the following errors and unsure of how to fix them.

----------------------------------------------------------------

WARNING: modpost: missing MODULE_LICENSE() in /home/michael/hybrid/wl.o
see include/linux/module.h for more information
CC /home/michael/hybrid/wl.mod.o
LD [M] /home/michael/hybrid/wl.ko

----------------------------------------------------------------

michael@michael-laptop:~/hybrid$ sudo insmod wl.ko

insmod: error inserting 'wl.ko': -1 File exists

---

### Post by Ayuthia on 2009-01-30
> **mpl34 said:**
> Hey

Still having problems using the hardware drivers manager has been unsuccessful. I am still getting the following errors and unsure of how to fix them.

----------------------------------------------------------------

WARNING: modpost: missing MODULE_LICENSE() in /home/michael/hybrid/wl.o
see include/linux/module.h for more information
CC /home/michael/hybrid/wl.mod.o
LD [M] /home/michael/hybrid/wl.ko

----------------------------------------------------------------

michael@michael-laptop:~/hybrid$ sudo insmod wl.ko

insmod: error inserting 'wl.ko': -1 File exists

For the last part, please try:
```
sudo rmmod wl
sudo insmod wl.ko
```

---

### Post by mpl34 on 2009-01-30
Hey I'm getting another problem, I ran both,
        sudo rmmod wl
        sudo insmod wl.ko

but the i was still unable to make a wireless connection sudo i decided to start over from scratch and now im getting the error

root@michael-laptop:~/hybrid# sudo modprobe -r b43 ssb ndiswrapper wl
FATAL: Module ssb is in use.
root@michael-laptop:~/hybrid# sudo rmmod ssb
ERROR: Module ssb is in use by b44

---

### Post by Ayuthia on 2009-01-30
> **mpl34 said:**
> Hey I'm getting another problem, I ran both,
        sudo rmmod wl
        sudo insmod wl.ko

but the i was still unable to make a wireless connection sudo i decided to start over from scratch and now im getting the error

root@michael-laptop:~/hybrid# sudo modprobe -r b43 ssb ndiswrapper wl
FATAL: Module ssb is in use.
root@michael-laptop:~/hybrid# sudo rmmod ssb
ERROR: Module ssb is in use by b44

Ok.  This means that you also have a Broadcom wired ethernet card (b44 module).  So in order to load the wl module:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo insmod wl.ko
sudo modprobe b44
```

---

### Post by mpl34 on 2009-01-30
Got it working!!!! thanx for all the help in the end i had to include b44 in the sudo modprobe command

---

### Post by mpl34 on 2009-01-30
new problem i just restarted and now ive lost my wireless option in the network manager and as far as i can tell my wireless card is not working... whats the problem

---

### Post by Ayuthia on 2009-01-31
> **mpl34 said:**
> new problem i just restarted and now ive lost my wireless option in the network manager and as far as i can tell my wireless card is not working... whats the problem

Since you are using the compiled version, you might be better off adding some commands into /etc/rc.local so that it will work upon reboot.  Edit /etc/rc.local (in sudo mode) and add:
```
modprobe -r b43 b44 ssb ndiswrapper wl
insmod <compiled wl.ko path>/wl.ko
modprobe b44
```

That should fix it.  Hope that helps.

---

### Post by mpl34 on 2009-01-31
i have tried to modify rc.local like suggested but it still did not seem to fix the problem. I tried just typing the following into the konsole after restart but still got nothing,

sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo rmmod wl
sudo insmod wl.ko
sudo /etc/init.d/networking restart

i the end i had to re-compile from the beginning with,

make  -C /lib/modules/`uname -r`/build M=`pwd` clean
make -C /lib/modules/`uname -r`/build M=`pwd`
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo rmmod wl
sudo insmod wl.ko
sudo /etc/init.d/networking restart

and it was working again however i would preferably not like to be continuously doing this every time i restart. i'm not quite sure what that rc.local file does but im assuming it carries out specified commands with booting?

Also advice on how to get a bluetooth mouse connected i thought it would be simple by using kdebluetooth4 however when i click on the icon nothing happens i believe my bluetooth is a dell 355 chip or something.

Thanks for the help

---

### Post by kevdog on 2009-01-31
Can you tell me what exactly you put in the rc.local file?

Also just curious for this command:
sudo insmod wl.ko

Will this work if you type:
sudo modprobe wl.ko

I have an idea if the above statement works for a possible workaround.

---

### Post by Ayuthia on 2009-01-31
> **mpl34 said:**
> i have tried to modify rc.local like suggested but it still did not seem to fix the problem. I tried just typing the following into the konsole after restart but still got nothing,

sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo rmmod wl
sudo insmod wl.ko
sudo /etc/init.d/networking restart

i the end i had to re-compile from the beginning with,

make  -C /lib/modules/`uname -r`/build M=`pwd` clean
make -C /lib/modules/`uname -r`/build M=`pwd`
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo rmmod wl
sudo insmod wl.ko
sudo /etc/init.d/networking restart

and it was working again however i would preferably not like to be continuously doing this every time i restart. i'm not quite sure what that rc.local file does but im assuming it carries out specified commands with booting?

Also advice on how to get a bluetooth mouse connected i thought it would be simple by using kdebluetooth4 however when i click on the icon nothing happens i believe my bluetooth is a dell 355 chip or something.

Thanks for the help

The insmod wl.ko is that part that contains the problem.  You need to put the path where the wl.ko exists (insmod /home/user/hybrid.../wl.ko) or else the system will think that it should use the one that Ubuntu supplies.

---

### Post by Ayuthia on 2009-01-31
> **kevdog said:**
> Can you tell me what exactly you put in the rc.local file?

Also just curious for this command:
sudo insmod wl.ko

Will this work if you type:
sudo modprobe wl.ko

I have an idea if the above statement works for a possible workaround.

The insmod is being used instead of the modprobe because modprobe is defaulting to the Ubuntu module in /lib/modules/`uname -r`/volatile.  mpl34 compiled a newer version of the wl module somewhere in /home so we are inserting that module instead of the one in /lib/modules.

The rc.local script is being used instead of moving the wl.ko file into /lib/modules because there have been instances where the system is overwriting the wl.ko with the one that Ubuntu supplies.

---

### Post by mpl34 on 2009-01-31
This is what my rc.local file looks like and still no luck using the wireless after reboot. do i need to include the command to restart my network??

sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo insmod /home/michael/Drivers/hybrid wl.ko
sudo modprobe b44

---

### Post by mpl34 on 2009-01-31
Sorry i released a mistake on my part typing the following after reboot does get my wireless to start probably im gona play round with the rc.local file to make it start correctly after reboot. but im still a bit unsure about the rc.local file does or how it is used. 

sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo insmod wl.ko
sudo /etc/init.d/networking restart

---

### Post by mpl34 on 2009-01-31
great i have got it working!! thanks for the help my rc.local file contains

sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe ieee80211_crypt_tkip
sudo insmod /home/michael/Drivers/hybrid/wl.ko
sudo modprobe b44
sudo /etc/init.d/networking restart

Now im gna battle away with my bluetooth which ive set up a new post specifically for  [here]("http://ubuntuforums.org/showthread.php?p=6654458#post6654458")

---

### Post by kevdog on 2009-02-01
You might want to experiment, however since the rc.local file is run as root, I do not think you need the sudo statements for these commands.

---

### Post by Ayuthia on 2009-02-01
> **kevdog said:**
> You might want to experiment, however since the rc.local file is run as root, I do not think you need the sudo statements for these commands.

I agree with kevdog, the sudo commands are not needed.  The rc.local is just a file that is run when the system starts up.  

Sorry for leaving out the ieee80211_crypt_tkip part.  I have been used to using modprobe instead of insmod and forgot about the dependency.  I am glad that you found it and got it working!

---

### Post by frost100 on 2010-06-20
when i get to the last stage and type insmod wl.ko, i get the error:
Can't read 'wl.ko': No such file or directory.
Any ideas?

---

