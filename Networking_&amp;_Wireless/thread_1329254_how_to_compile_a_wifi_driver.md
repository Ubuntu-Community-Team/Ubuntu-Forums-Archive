---
title: "how to compile a wifi driver"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by topsykretts on 2009-11-17
ok..it seems no one has an answer to my last post bout the 8192se realtek driver([http://ubuntuforums.org/showthread.php?p=8327377#post8327377)..no](http://ubuntuforums.org/showthread.php?p=8327377#post8327377)..no) prob haha...now can anyone help me compile the native realtek 8192se driver?i think thats my only hope..im kind of a newbie here so of anyone can help guide me through compiling it would be greatly appreciated..here is the link..thanks in advance and i hope i can get more replies this time..haha:  [http://launchpadlibrarian.net/339279...12.2009.tar.gz]("http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz")

---

### Post by chili555 on 2009-11-17
I worked on this for quite a while and finally, *finally* got it to make and install. Perhaps some of the steps I will outline are redundant, but that's what worked for me.

DISCLAIMER: I do not use the Realtek 8192SE, so I cannot tell if this drives the device properly; these steps merely build the module you linked.

All the steps in 'Code' blocks are terminal commands. Please enter each individually. This assumes you have internet access on the computer on which the module is to be compiled and installed.

```
sudo apt-get install build-essential linux-source-2.6.31 *linux-headers-generic*
cd /usr/src
sudo tar -xvjf linux-source-2.6.31.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.31 /usr/src/linux
cd ~
mkdir Realtek
cd Realtek
wget http://launchpadlibrarian.net/33927923/rtl8192se_linux_2.6.0010.1012.2009.tar.gz
tar -xvzf rtl8192se_linux_2.6.0010.1012.2009.tar.gz
cd rtl8192se_linux_2.6.0010.1012.2009
make
sudo su   
make install
```I have assumed you are running kernel 2.6.31-xx. Find out with:```
uname -r
```It will be something like this:> 2.6.31-14-genericThe source you need is the first part only, in this case, 2.6.31. If your running kernel is different, customize these commands to match. 

Some of these steps will take a few moments and spit out many lines of text. Please be patient. Please stop and post back with a question if you see the dreaded 'Error.' Next do:```
modprobe r8192se_pci
iwconfig
```Do you now have a wireless interface, wlan0, perhaps? Can you click the Network Manager and connect?

EDIT: Added additional required packages.

---

### Post by topsykretts on 2009-11-17
hey chili555...thanks so much...i followed it down to the t and it worked...after i put in the modprobe commant the little wheel turned and i was connected to my wifi here at home..so i thought everything was fine..enjoyed a little wifi experience i havent had the chance to enjoy for a few days now..then i shut it down..when i log back it..it not there any more...no wireless interface again..what could have gone wrong?

---

### Post by Dude-PWB- on 2009-11-17
from terminal cd back to the installed directory

then 

sudo ./wlan0up

---

### Post by topsykretts on 2009-11-17
ok so i put in 

sudo su
-then
modprobe r9182se_pci

in the terminal..and i get a wifi signal again..so im thinking i have to do this every time i log back on..is there a way to make this automatic on startup?

---

### Post by topsykretts on 2009-11-17
> **Dude-PWB- said:**
> from terminal cd back to the installed directory

then 

sudo ./wlan0up


hey man..so i go
cd realtek
cd rtl8192se_linux_2.6.0010.1012.2009
sudo ./wlan0up

and i get this error "insmod: error inserting 'r8192se_pci.ko': -1 File exists"

---

### Post by Dude-PWB- on 2009-11-17
> **topsykretts said:**
> hey man..so i go
cd realtek
cd rtl8192se_linux_2.6.0010.1012.2009
sudo ./wlan0up

and i get this error "insmod: error inserting 'r8192se_pci.ko': -1 File exists"


Hmm, weird, that's what I had to do with my 8192e after every reboot after I compiled and installed the drivers.

Installed wicd instead and removed network manager, going to see if that works better next time.

However, your error, that i don't get, gives me something else to look for and muck around with. :)

---

### Post by topsykretts on 2009-11-17
> **Dude-PWB- said:**
> Hmm, weird, that's what I had to do with my 8192e after every reboot after I compiled and installed the drivers.

Installed wicd instead and removed network manager, going to see if that works better next time.

However, your error, that i don't get, gives me something else to look for and muck around with. :)

so u have to type in a command every reboot to get your wifi to work?

---

### Post by Dude-PWB- on 2009-11-17
> **topsykretts said:**
> so u have to type in a command every reboot to get your wifi to work?

Yes. On a laptop with a live usb install (for testing and wrecking things till I get it all right:D).

Like I say, trying some other things now to see if I can get it to start on it's own. Not the most experienced user, but I'm not giving up!

---

### Post by topsykretts on 2009-11-17
> **Dude-PWB- said:**
> Yes. On a laptop with a live usb install (for testing and wrecking things till I get it all right:D).

Like I say, trying some other things now to see if I can get it to start on it's own. Not the most experienced user, but I'm not giving up!

alright cool!!post a reply if you get anything ok??thanks so much guys!!i really appreciate the help

---

### Post by Dude-PWB- on 2009-11-17
Found this in the readme file for the driver.

> 3. Load driver module to kernel and start up nic.
      ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok..

---

### Post by topsykretts on 2009-11-18
> **Dude-PWB- said:**
> Found this in the readme file for the driver.

oh wow...i didnt see that on the read me file..so i tried it.. ./wlan0up.. ./wlan0down .. ./wlan0up again

then i restarted my computer..no wireless interface again..i entered the following code:

 marc@marc-laptop:~$ sudo su
root@marc-laptop:/home/marc# cd Realtek
root@marc-laptop:/home/marc/Realtek# cd rtl8192se_linux_2.6.0010.1012.2009
root@marc-laptop:/home/marc/Realtek/rtl8192se_linux_2.6.0010.1012.2009# sudo ./wlan0up
root@marc-laptop:/home/marc/Realtek/rtl8192se_linux_2.6.0010.1012.2009# 

and i got my wireless interface back...at this point im so desperate to get the wifi working on this thing that i dont mind if i have to input the above code everytime a turn my laptop on!haha..but incase you or anyone can help me to get this thing to work at start up and make my life easier it would be very much appreciated..thanks so much guys

---

### Post by chili555 on 2009-11-18
Please see my PM. If that doesn't work, we can automate the above easily.

---

### Post by topsykretts on 2009-11-18
got the wifi to work on start up..thanks so much to chili555 and dude-PWB-..much appreciated guys!!

---

### Post by chili555 on 2009-11-18
For the benefit of the searchers, he added r8192se_pci to /etc/modules. Also, whenever a new kernel, also known as linux-image is installed, the r8192se_pci module will need to be rebuilt against the new kernel as outlined in post #2, preceded with an additional command, as follows:```
--- snip ---
cd rtl8192se_linux_2.6.0010.1012.2009
[COLOR="Red"]make clean[/COLOR]
make
sudo su   
make install
```Also, to make this all a bit less cumbersome, I suggest right-clicking the *rtl8192se_linux_2.6.0010.1012.2009* folder and renaming it to something reasonable, such as Realtek. Afterwards, your commands will be, simply:```
--- snip ---
cd Realtek
[COLOR="Red"]make clean[/COLOR]
make
sudo su   
make install
```Thanks for the kind comments. Have fun and go after those updates!

---

### Post by Dude-PWB- on 2009-11-18
Although the PM must be nice, but can you post the commands to get the wireless to work on startup so that the rest of us that are having issues can make it work as well?

---

### Post by chili555 on 2009-11-18
> **Dude-PWB- said:**
> Although the PM must be nice, but can you post the commands to get the wireless to work on startup so that the rest of us that are having issues can make it work as well?> For the benefit of the searchers, he added r8192se_pci to /etc/modulesPlease open a terminal and do:```
sudo gedit /etc/modules
```Add a single line:```
r8192se_pci
```Proofread, save, close gedit and enjoy.

---

### Post by Dude-PWB- on 2009-11-18
Thanks chili555!

I just figured it out and was about to come back here and post it when I saw your reply.

Hope this will help everyone else as well.

---

### Post by northd_tech on 2009-11-25
I've been having some trouble using the above to build a 64-bit module for a Toshiba Satellite P505D with a Realtek 8192E wireless interface.

I've had absolutely ZERO luck using 64 bit Windoze drivers under ndiswrapper, so I thought I'd try chili555's method pointed out at post #2 above.

After successfully building the [32 bit- whoops ;) ] modules, I noticed my mistake and did not install them.  I was also able to successfully build the 64-bit modules using this tarball file:

[FONT=Franklin Gothic Medium][COLOR=Blue]**rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz**[/COLOR][/FONT]

This was the result of "make" with the 64-bit tarball: > 
 Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192se_pci.mod.o
  LD [M]  /home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/r8192se_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'I could not get "make install" to run the first time (using "sudo make install" "sudo su, make install" or "sudo make install" from a root terminal).  I very recently installed some new kernel packages, and got different results the 2nd time (and this laptop currently wants a requested restart after installing a bunch of header files).  In the interests of documentation, I'm posting the results that I got from the earlier "sudo make install" (actually run as root):

> make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: Entering directory `/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make -C /lib/modules/2.6.31-15-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make: *** [install] Error 2After using the Synaptics Package Manager to install some kernel and wireless packages, I tried running "make" (a 2nd successful time), but this time it looks like "sudo make install" took hold.

Here are those results > 
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: Entering directory `/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make -C /lib/modules/2.6.31-15-generic/build M=/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
install -p -m 644 r8192se_pci.ko /lib/modules/2.6.31-15-generic/kernel/drivers/net/wireless/
depmod -a
make[1]: Leaving directory `/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'I've since installed a bunch of header packages that were not requested (and depmod hasn't been throwing any errors the whole time that I noticed).  I also installed the backport modules and a "server" kernel that the backports requested.

I'll advise with what I find out after the restart (if the new kernel(s) restart...)

EDIT:  This Bug page:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126)

And this page (in German, has an 8192E tarball source) about the Realtek 8192E (not SE, and I'm not convinced they are compatible under 64 bit yet) are worth keeping handy links to:

[http://forum.ubuntuusers.de/topic/samsung-n510-und-ubuntu/3/#post-2247165](http://forum.ubuntuusers.de/topic/samsung-n510-und-ubuntu/3/#post-2247165)

Also, if you don't mind using 32-bit ubuntu, the 32-bit Windows drivers work great with this laptop and the Realtek 8192E WiFi under Jaunty Jackalope 9.04- FWIW.

---

### Post by siamect on 2009-11-26
Yes!!! 
This was the problem. It is not a SE! it is an 8192E in my wife's Samsung N120,
UNR Karmic Koala

Thanks for this link
[http://forum.ubuntuusers.de/topic/sa.../#post-2247165]("http://forum.ubuntuusers.de/topic/samsung-n510-und-ubuntu/3/#post-2247165")


Just uncompress the 
[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)

get the latest snapshot:[INDENT][http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192e;hb=aa021baa3295fa6e3f367d80f8955dd5176656eb](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192e;hb=aa021baa3295fa6e3f367d80f8955dd5176656eb)
[/INDENT]uncompress and and copy the files over the previous one.


cd to wherever the files are

sudo su
./install.sh


That's what made it work for me. UNR Karmic Koala


Thanks all for this!
Martin

---

### Post by SevinK on 2009-12-02
Hello,

Sorry if this is a bit late.

I just want to begin off by saying how glad I am to see a working solution for the Realtek 8172 driver. I currently own a ThinkPad x200 so this is a relief. However, after downloading the rtl source (32-bit) and following the steps that chili555 outlined in the original post, I am getting this error:

irving@phoenix:~/Desktop/Realtek/rtl8192se_linux_2.6.0010.1012.2009$ make
make: *** /lib/modules/2.6.31-15-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2


Can anyone help me out here? I tried a make clean and I still receive that. Thanks!

---

### Post by chili555 on 2009-12-02
Did you observe my comments about the kernel version? Please let us see:```
uname -r
ls /usr/src
```Thanks.

---

### Post by SevinK on 2009-12-02
irving@phoenix:~$ uname -r
2.6.31-15-generic
irving@phoenix:~$ ls /usr/src
linux  linux-source-2.6.31  linux-source-2.6.31.tar.bz2  vboxdrv-3.0.8  vboxnetadp-3.0.8  vboxnetflt-3.0.8

---

### Post by chili555 on 2009-12-02
Please do:```
sudo apt-get install linux-headers-generic build-essential
```Then try again.

---

### Post by SevinK on 2009-12-02
Alright, make worked but sudo make install is throwing the error the guy on the 2nd page got. I'm not exactly sure what packages I need.

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: Entering directory `/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make -C /lib/modules/2.6.31-15-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make: *** [install] Error 2 			 		

Here is my sudo lspci -v

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device e020
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 2000 [size=256]
    Memory at f2500000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88
    Kernel driver in use: rtl819xSE



So I believe I have the correct rtl8192se package..

---

### Post by howdoesitmatter on 2009-12-02
Even I installed the 8192Se by mistake. How do I remove it. Please help.

---

### Post by howdoesitmatter on 2009-12-02
My wireless worked. Thanks to everyone on this thread. I used 8192 driver for 8172. It worked.

---

### Post by chili555 on 2009-12-02
SevinK --

Here:> However, after downloading the rtl source (32-bit)you refer to 32-bit, but here:> make[1]: Entering directory `/home/xxx/Desktop/rtl8192se_linux_2.6.0010.1020.2009_[COLOR="Red"]64bit[/COLOR]/HAL/rtl8192'indicates you are trying to build 64-bit. Which is your system? Please post:```
uname -a
```

---

### Post by SevinK on 2009-12-02
Hmm, that's weird.

Linux phoenix 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux


I could have swore I downloaded the 32-bit version.

EDIT: After redownloading the 32-bit tarball and running sudo make install, I still get the same error w/o the 64-bit namespace.

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: Entering directory `/home/iruan/Desktop/Realtek/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192'
make -C /lib/modules/2.6.31-15-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/iruan/Desktop/Realtek/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192'

---

### Post by chili555 on 2009-12-02
```
sudo make install
```> make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.I get this error, too, when I do 'sudo make install.' However, the instructions, very intentionally, say:```
sudo su
make install
```Please post back for the benefit of the searchers.

---

### Post by SevinK on 2009-12-03
Oh wow, can't believe it worked because of that. Any reason why the sudo prepend does not work?

---

### Post by rachael4u on 2009-12-03
> **Dude-PWB- said:**
> from terminal cd back to the installed directory

then 

sudo ./wlan0up

hw sss rite.. u can use this method.

---

### Post by chili555 on 2009-12-03
> **SevinK said:**
> Oh wow, can't believe it worked because of that. Any reason why the sudo prepend does not work?I don't know. I read about it  googling for 8192SE in a bug report, if I remember correctly. That's part of why I worked on it for a long time; working stuff like this out.

May I assume your wireless is working now?

---

### Post by SevinK on 2009-12-03
For the most part, yes, it is working. I had to add it to /etc/modules like you stated but sometimes it has trouble initially connecting to an AP. Do I need to run the wpasupplicant tool if I needed to connect to a WPA/WPA2 AP?

---

### Post by chili555 on 2009-12-03
I don't know. I am not yet versed in WPA. You may wish to start a new thread and describe your symptoms.

---

### Post by northd_tech on 2009-12-03
> **siamect said:**
> Yes!!! 
This was the problem. It is not a SE! it is an 8192E in my wife's Samsung N120,
UNR Karmic Koala

Thanks for this link
[http://forum.ubuntuusers.de/topic/sa.../#post-2247165]("http://forum.ubuntuusers.de/topic/samsung-n510-und-ubuntu/3/#post-2247165")


Just uncompress the 
[http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)

get the latest snapshot:[INDENT][http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192e;hb=aa021baa3295fa6e3f367d80f8955dd5176656eb](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=tree;f=drivers/staging/rtl8192e;hb=aa021baa3295fa6e3f367d80f8955dd5176656eb)
[/INDENT]uncompress and and copy the files over the previous one.

cd to wherever the files are

sudo su
./install.sh

That's what made it work for me. UNR Karmic Koala

Thanks all for this!
Martin
Hi Martin.  All my changes caused a kernel panic issue that I just fixed on this laptop (but I've been out of town this week too).

It looks to me like the Realtek 8192E does indeed require different sourcecode (although either module seems to compile for me).  Under 64-bit Koala 9.10, 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux, here are my install shell results:

>   LD [M]  /home/xxxx/Desktop/rtl819Xe/r8192_pci.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 5 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/xxxx/Desktop/rtl819Xe/r8192_pci.mod.o
  LD [M]  /home/xxxx/Desktop/rtl819Xe/r8192_pci.ko
make: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
Copying firmware...
Installing module and rebuilding dependencies...
Loading module...
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper.fubar, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
..ready
Now I can see a wireless interface under Network Manager, but the wireless choice is greyed out and says "disconnected" under "Wireless Networks."  One can see that the kernel module that I compiled is called[SIZE=4]** r8192_pci.ko**[/SIZE] for the 8192E Realtek PCI wireless interface.

If I run iwconfig, I see this:

> rtl819Xe# iwconfig
lo        no wireless extensions.

wlan0     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

virbr0    no wireless extensions.
It looks like I've still got some /etc/modules configuration issues (or else I'm still seeing 64-bit trouble with the sourcecode and snapshot from the German page above).

Here are the lines/comments that I added to the /etc/modules file:

> # ndiswrapper # for Windoze Wifi drivers
# r8192se_pci for Realtek 8192SE (make sure to match either 32- or 64-bit 
# versions
# r8192_pci # for Realtek 8192E (NOT SE!!!) module
r8192_pci
Also "lsmod" command gives me this now:

> ...
amd64_edac_mod         26688  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
i2c_piix4              11728  0 
edac_core              48876  1 amd64_edac_mod
shpchp                 37756  0 
dm_crypt               14888  0 
r8192_pci             265672  0 
lp                     11908  0 
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
... 

---

### Post by rajeeja on 2009-12-05
Thanks chili555.

Keep it up. Like it - "Ubuntu Addict and Loving it"

---

### Post by SevinK on 2009-12-05
Howcome I get this mesage when I do this:

sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8192se_pci does not exist in /proc/modules


I thought you load the module in /etc/modules, so why would it look for it in /proc/modules?

This is my kernel version: 2.6.31-16-generic
And this is my /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
r8192se_pci


The reason why I'm asking is because sometimes if the module doesn't get loaded onto the kernel correctly, I have to manually type sudo ./wlan0down then sudo ./wlan0up and it *usually* works. Now I can't because it's looking in /proc/modules.

---

### Post by chili555 on 2009-12-05
> I thought you load the module in /etc/modules, so why would it look for it in /proc/modules?/proc/modules is simply a listing the system uses to know what modules are currently loaded.

---

### Post by ac7ss on 2009-12-17
Thank you for this thread.

I was trying to get my RT73 wireless working, apparently there is a module now in the system (9.10). (Maybe not, I did try compiling it, but there were errors on the install.) But it is there now.

I was not able to get the wireless to show up without a 
```
sudo modprobe rt73usb
```

Happiness, it would work after that. 
Sadness, I did not want to have to do that every time.

I stumbled on this thread, and did the following:
```
sudo su
echo rt73usb >> /etc/modules
```(Very important to use the double redirect, as it will append instead of overwrite the file)
and it now works!!!
Thank you all.

---

### Post by Bornabe on 2010-02-24
Toshiba Qosmio x505-Q870 (Win7 / Linux Dual-Boot)
-Ubuntu v9.10 (2.6.31-19-generic) All current updates.
-Realtek RTL8191SE

lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     802.11bgn  ESSID:"Fletcher Coin Laundry"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:17:9A:2D:67:2E   
          Bit Rate=300 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=86/100  Signal level=-54 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It's showing my Wireless Card now, thank you so much, and oddly enough it works fine at home with my Verizon FiOS Router and it's WEP protection... but... always a but, right?  It does not work, after successfully 'Connecting' to my Unsecure Connection at work on a D-Link Router which is fine with all other Laptops and Win7 on my Laptop (Dual-Boot) just fine.

It connects, seems to start to connect to a web page, or download a file in Ubuntu Software Center, then immediately loses it's connection... but never says it's disconnected.

---

### Post by jdayrutherord on 2010-03-06
I have a Toshiba 135 laptop with atheros for wired eth0 and the realtek
for wifi. Karmic picks up the wired interface ok but no wifi.
so I installed the driver following your instructions. Seemed to work like a charm, 
and I connected to my wireless.

However, I noticed that if I left the system for a while, I would come back and both
the wired and wireless were dead. And also a usb external drive began to have problems, would not mount or would mount but be unuseable.

I ran make uninstall, and things are back to normal for (minus wifi).

Anyone have any ideas on this one?
I tried this twice following fresh karmic installs. So probably not a fluke.

---

### Post by NeverSage on 2010-03-09
Hi, first post here.  My wifi issue has been driving me crazy for days and am hoping the good people here might be able to help me out.  I'm a Linux newbie, so please be gentle.  

My card has the Realtek rtl8192su usb chipset.  First I tried using ndiswrapper which worked except I had to do it every time I restarted the computer.  I figured if I had to spend a lot of time getting it to work correctly I might as well do it natively in Linux.  I emailed Realtek and got the newest driver (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202.tar.gz).  After much trial and error and reading many forums I got it to work using chili555's directions on the first page.  The problem is it didn't keep after the reboot.  I'm assuming this has something to do with the module.  I don't see it in /etc/modules folder but honestly I'm not sure if I'm supposed to.  I'd like to add it into /etc/modules through gedit like topsykretts but of course I wouldn't be able to add the line r8192se_pci since I'm using a different chipset.  I don't know where to find the information on what to use, though.  

Another issue:
> **Dude-PWB- said:**
> from terminal cd back to the installed directory

then 

sudo ./wlan0up

When I do this ./wlan0up just says "No such file or directory".

If I didn't provide enough info, I'm sorry.  Please let me know what other information you need.  I'd like to add that on the computer I'm having these issues with I'm not technically running Ubuntu... It's Linux Mint.  To my understanding there should be no difference when it comes to these drivers though.

Thanks for any help you can give me.

---

### Post by chili555 on 2010-03-09
> **NeverSage said:**
> Hi, first post here.  My wifi issue has been driving me crazy for days and am hoping the good people here might be able to help me out.  I'm a Linux newbie, so please be gentle.  

My card has the Realtek rtl8192su usb chipset.  First I tried using ndiswrapper which worked except I had to do it every time I restarted the computer.  I figured if I had to spend a lot of time getting it to work correctly I might as well do it natively in Linux.  I emailed Realtek and got the newest driver (rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100202.tar.gz).  After much trial and error and reading many forums I got it to work using chili555's directions on the first page.  The problem is it didn't keep after the reboot.  I'm assuming this has something to do with the module.  I don't see it in /etc/modules folder but honestly I'm not sure if I'm supposed to.  I'd like to add it into /etc/modules through gedit like topsykretts but of course I wouldn't be able to add the line r8192se_pci since I'm using a different chipset.  I don't know where to find the information on what to use, though.  

Another issue:


When I do this ./wlan0up just says "No such file or directory".

If I didn't provide enough info, I'm sorry.  Please let me know what other information you need.  I'd like to add that on the computer I'm having these issues with I'm not technically running Ubuntu... It's Linux Mint.  To my understanding there should be no difference when it comes to these drivers though.

Thanks for any help you can give me.Dr. Chili is here to help. Please start a new thread.

---

### Post by NeverSage on 2010-03-09
Will do!

---

### Post by rclowery on 2010-03-23
I also have a Toshiba T135 with Realtek Wirless 8192_se on Ubuntu
9.10 64-bit. 

I tried Chili's detailed instructions but I haven't been able to get the
wireless card to detect any networks even though Ubuntu says the
driver is installed and active.

I am unable to use the command sudo ./wlan0up without Ubuntu
telling me that their has been a system crash and the kernel is
unstable.

When I first started working on this problem I had to install a bunch of
packages using a USB flashdrive in order to get build-essentials so
I could build-headers. I also had to download a copy of the source-code.

I'm thinking that I'll need to reinstall Ubuntu and start over again just in case
I've introduced critical errors into the system. I may also need to try connecting
to the Internet through the Ethernet port in order to make some of this easier.

Does anyone have any ideas about what I may be doing wrong or what I should try next?

Thank you,

RC

---

### Post by chili555 on 2010-03-23
I wonder if this is a 64-bit vs. 32-bit driver problem. Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/comments/28](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126/comments/28)

I suggest a sudo make uninstall in your current folder and then download and install the version listed. Do your troubles go away?

---

### Post by rclowery on 2010-03-23
Do I use the sudo make uninstall in the folder the driver is currently stored in?

Also, should I remove the script from etc/modules?

---

### Post by chili555 on 2010-03-23
> Do I use the sudo make uninstall in the folder the driver is currently stored in?Yes.> Also, should I remove the script from etc/modules? Not yet. Hopefully, we will use it to load our shiny new 64-bit driver. Hopefully, you meant [COLOR="Red"]/[/COLOR]etc/modules.

As you compile, please stop and post any errors. Warnings are OK.

---

### Post by rclowery on 2010-03-23
Chili,

OK, I retried it with the 64-bit driver and I'm still not able to see any networks. The driver seems to install, but during the process of installation I get a lot of warning messages.

I'm attaching a text file of my terminal log from the point where things seem to go bad. 

Thanks again for all of your help. 

RC

---

### Post by chili555 on 2010-03-23
Hey, that's not so bad! I've seen worse. Let's try a few steps:```
cd ~/Realtek/rtl8192se_64
cp wlan0up wlan4up
sudo gedit wlan4up
```Change this line:```
#ifconfig wlan0 up
```To this:```
#ifconfig wlan4 up
```Proofread, save and close gedit.```
sudo ./wlan4up
```Now can you click the Network manager icon and connect? Any errors?

---

### Post by rclowery on 2010-03-23
OK, the plot thickens:

I tried what you suggested but it seems that the wlan# keeps changing. 

Also when I used the ./wlan4up command an icon appeared in the upper right hand corner telling me a major kernel error had occurred. 

I've included the log file again so you can see whats happening.

I appreciate your continued support.

---

### Post by chili555 on 2010-03-23
That doesn't tell us enough information we can use. Please try again and after the kernel error appears, please run:```
sudo tail -n25 /var/log/syslog
```Attach a text file as you have before. Let's try to solve the kernel error problem first and hope that wireless gets fixed as well.

This driver ought to work or not work; not cause kernel problems.

---

### Post by rclowery on 2010-03-23
OK, so I did the whole thing over again from scratch starting with the instructions in your original post at the beginning of this thread.

I didn't get the kernel error this time, but the wireless connection still doesn't work.

I'm going to attach a text file again. Hopefully it will have some helpful information.

---

### Post by chili555 on 2010-03-23
How much memory do you have in your machine? 4GB? Is it a Toshiba?

I saw this: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1955168.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1955168.html)

Perhaps you can do sudo make uninstall and the edit the Makefile and simply remove every instance of  -DENABLE_LPS. After saving your changes, run the compile process again and let's see if the kernel issues are solved.

---

### Post by rclowery on 2010-03-23
Hi Chili,

Yes my laptop is a Toshiba T-135 S1310 with 4gb of RAM and a 64-bit processor.

Could you explain to me what you mean by "edit the Makefile?" I'm not familiar with this process. 

Also, there is a newer version of the driver available on Realtek's website, but it doesn't specify whether or not is is 64 bit. I've tried it and it hasn't worked any better than the version we've been using in our dialogue, but I thought I'd make you aware of it just in case it gives you any new ideas.

Thanks again for your dedication. 

RC

---

### Post by chili555 on 2010-03-23
```
cd ~/Realtek/rtl8192se_64
gedit Makefile
```Scan every line and look for -DENABLE_LPS. Remove it in every instance you can see. Proofread, save and close gedit.```
make clean 
make
sudo make install
rmmod -f r8192se_pci
modprobe r8192se_pci
```Any kernel errors? Any connections?

---

### Post by rclowery on 2010-03-23
Chili,

I tried to remove instances of -DENIABLE_LPS in the Makefile, but there weren't any to begin with. 

Was I supposed to uninstall and reinstall the driver first before trying this? Your last post did not specify.

RC

---

### Post by chili555 on 2010-03-23
> Was I supposed to uninstall and reinstall the driver first before trying this? Your last post did not specify.No. No need to continue with the other steps. More tomorrow.

---

### Post by rclowery on 2010-03-24
Thanks Chili,

I feel like we are caught in an endless knot here, so hopefully we can figure out a way to untie ourselves by working together. I know other people with this issue would find it beneficial as well, especially those with brand-new Toshiba T-135 laptops that don't want to run Windows.

I've considered that a possible plan B would be to replace the Realtek card with a Mini-PCI card with known Ubuntu compatibility. Hopefully this won't be necessary, but I'm keeping it in mind just in case.

RC

---

### Post by chili555 on 2010-03-24
This interested me: [http://ubuntuforums.org/showthread.php?t=1239342&page=3](http://ubuntuforums.org/showthread.php?t=1239342&page=3)> And the fix was to add the following to grub.

One more tip, your problem will dissapear completely if boot your system with "mem=4G iommu=off". Of course, your system will have only ~3.3GB of RAM instead of 8G.And this: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1841651.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1841651.html)> hm_shurt >> I used mem=4G iommu=off kernel parameters instead and now I've only 
have 3Gb recognized (instead of 4Gb) but most important, everything works like a charm ! No more kernel panic. Here is how you add this as a boot parameter: [http://ubuntuforums.org/showpost.php?p=8990468&postcount=4](http://ubuntuforums.org/showpost.php?p=8990468&postcount=4)

Just substitute your parameters *mem=4G iommu=off* for the parameters mentioned in my post. Do not forget to do the last step:```
sudo update-grub
```Reboot and let's see if the kernel is happy when you modprobe r8192se_pci.

---

### Post by rclowery on 2010-03-24
Chili,

OK, I did as you instructed, but I experienced a kernel crash when I used the modprobe command. I'll attach a text file again so you can see.

RC

---

### Post by chili555 on 2010-03-24
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

See post #162; your output exactly.

Please see post #196. It looks like it was the Makefile in HAL/rtl8192 that has the -DENABLE_LPS lines that need removal!!!

Can you do, from the folder where you installed the driver:```
sudo su
make uninstall
make clean
gedit HAL/rtl8192/Makefile
```Remove all and every instance of -DENABLE_LPS. Proofread, save and close gedit.```
make
make install
modprobe r8192se_pci
exit
```Any improvement?

---

### Post by rclowery on 2010-03-24
No, no improvement. I didn't get any kernel errors this time, but the device still doesn't see any networks.

---

### Post by chili555 on 2010-03-24
Is it wlan0 now or wlan178? Does the ./wlan0up command, from the installation folder, produce any errors or warnings?

---

### Post by rclowery on 2010-03-24
It was wlan9 last time I tried. When I try wlan0up it tells me that it can't insert 8192_pci.ko, or something to that effect.

---

### Post by chili555 on 2010-03-24
If you try to unload it first:```
sudo rmmod -f r8192se_pci
sudo ./wlan0up
```What happens then?

---

### Post by rclowery on 2010-03-24
Its really weird. It tells me that there is no such file as r8192se_pci, but I seem to remember it being installed.

---

### Post by chili555 on 2010-03-24
Go back to the install folder and do it all over:```
sudo make clean
sudo make 
sudo make install
sudo ./wlan0up
```

---

### Post by rclowery on 2010-03-24
Chili,

No dice again. I'm wondering if the driver is just very poor quality and thats why it won't work.

I'm including a text file again. Maybe there will be something useful there. 

Is there any reason to think that 10.4 might support this particular chipset?

RC

---

### Post by chili555 on 2010-03-24
> wlan10    802.11bgn  Nickname:"rtl8191SEVA2"

          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   

          Retry:on   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0Please do:```
cd ~/Realtek/rtl8192se
sudo iwconfig wlan10 rate auto
sudo iwconfig wlan10 power on
sudo ./wlan0up
```Now do you see networks?> I'm wondering if the driver is just very poor quality and thats why it won't work.Or the card.

I don't know if it's supported in Lucid; it's worth Googling.

---

### Post by rclowery on 2010-03-25
Ugh, that didn't work either.

Chili, I appreciate your tireless efforts on my behalf, but I'm beginning to think that even if we get this thing to work it isn't going to be reliable. From what I've read of other people who have managed to make a connection, the connection is unstable, slow, and frustrating. 

Perhaps it would simply be better if I swapped the WLAN card out for one with known Ubuntu support. I'm not sure if you work on the hardware side of things, but if you could make a recommendation that would be great. I'm not intimidated by installing the card itself, but I'd like to get a better idea of what Ubuntu users think is the best model.

---

### Post by chili555 on 2010-03-25
> I'm not sure if you work on the hardware side of things,Work? What is that? You might check here:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by rclowery on 2010-03-26
Chili,

I think we are getting close to a solution.

I just downloaded and installed the Ubuntu 10.04 Lucid Lynx Beta and I am finally able 
to see networks! Apparently the driver for the Realtek 819x series has been added to the kernel in this version. 

The only trouble is that I still have difficulty negotiating the connection. The signal strength seems to be low and although I can see the network, once I enter my password information it will not go any further without timing out. 

Do you have any suggestions?

RC

---

### Post by chili555 on 2010-03-26
Let's take a look at:```
iwconfig
```Thanks.

---

### Post by rclowery on 2010-03-26
Sure.

  	 	 	 	 	> cameron@cameron-laptop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     802.11bg  ESSID:"TELFAIR"  Nickname:"rtl8191SEVA2"  
           Mode:Managed  Frequency=2.457 GHz  Access Point: 00:1E:2A:74:BD:FA    
           Bit Rate=54 Mb/s    
           Retry:on   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 pan0      no wireless extensions.  


Thank you again for your efforts.

---

### Post by rclowery on 2010-03-26
The smiley faces were not my choice. I'm not sure why they are there, but they seem to indicate an O.

---

### Post by chili555 on 2010-03-26
You can check the box below, when you post, to disable smileys.

Your *iwconfig* looks pretty normal. I don't see a reading for tx-power, but that may not be an issue. Nontheless, you might try:```
sudo iwconfig wlan0 txpower 7
```If it doesn't error out, try increasing it to 8, 9, 10 etc. until it won't go further. Does that help?

---

### Post by rclowery on 2010-03-27
Chili,

I'm getting a "SET Failed, operation not permitted" reply when I try to boost the power.

I still think the problem here is that the driver is craptacular, even though its now loaded into the kernel and finally working. 

I'm wondering what can be done about this.

RC

---

### Post by chili555 on 2010-03-27
> I'm wondering what can be done about this.I am sure there is a place on Launchpad to report a bug. [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

I don't know if it's the card or the driver. They seem to be touchy to get going. I also wonder if there is some weird interaction between the way the driver starts up the card and Network Manager. It is baffling because everything seems just right, except it just doesn't work.

I am sorry I could not have been more help.

---

### Post by rclowery on 2010-03-27
Chili,

You've been a lot of help actually. It isn't your fault this doesn't work as well as it should. 

Is there any reason to think that installing WICD would be an improvement over NetworkManager?

RC

---

### Post by chili555 on 2010-03-27
It sure is worth a try. I have a computer using Wicd and feel it's a bit faster than NM, but both, as well as manual configuration work just fine for me.

---

### Post by rclowery on 2010-04-01
Chili,

I finally broke down and bought and external USB wifi adapter until this issue is addressed. This card worked under Windows, so I am assuming it is a driver issue since so many people have had difficulties with it. Hopefully the final version of Lucid Lynx will remedy the problem.

Cameron

---

### Post by chili555 on 2010-04-01
I hope so, too. I have been trying Lucid beta and like it so far, but I don't have your device, so I have no idea if it works as expected.

How is your new USB wireless doing?

---

### Post by rclowery on 2010-04-02
Chili,

The USB Wifi adapter is fine for now (its a Netgear Wireless-G.) Its a little bit ungainly, and doesn't always work after the computer wakes up from sleep. If I unplug it and wait a moment and then reinsert it into the USB port, this seems to reload the driver. 

It seems that wireless is an issue on almost all distributions of Linux, but this really says more about manufacturer support for Linux than it does about Linux itself. The Linux community is at a distinct disadvantage, since it seems many drivers are written by volunteers after the hardware has been released. And then, even if their is native Linux support, the problem of substandard manufacturer drivers becomes an issue, as in my case. 

By the way, I'm curious as to how you have the time to dedicate to helping poor unfortunate souls like myself? Its a great service you provide to the Ubuntu community, and I want to commend you for it.

RC

---

### Post by chili555 on 2010-04-02
> the problem of substandard manufacturer drivers becomes an issue, as in my case. Even if the manufacturer wants to do a good job for the Linux customers, they have a challenge. There are customers running kernels from 2.6.28 to 2.6.32. There are various versions of gcc. There are various distributions; Ubuntu, Debian, Suse, Fedora, Gentoo, etc. Then there are the distributions that are based on one of these, Backtrack, Mint, etc. What a nightmare!> By the way, I'm curious as to how you have the time to dedicate to helping poor unfortunate souls like myself? I retired early and this is sort of one of my hobbies. When I want some satisfaction seeing those great words, "Thanks, chili, it's working now," I answer a few posts. I really quite enjoy it. It keeps the brain working. As long and hard as I have been doing this, I learn something new every day.

Thank you for your kind comments.

---

### Post by yungballla6 on 2011-08-08
Hello all, 

This thread helped me before when trying to set up a stable wifi connection on my lappy with a realtek driver. I followed and everything was good. 

A few days ago i decided to do a clean install of 11.04 (which i was running when i followed this thread the first time). After the install i noticed that my wifi was acting up and i realized i had to install the realtek driver again, like i did the first time. I followed the thread again the exact same as i did the first time when it worked for me, now when i boot up i get stuck after the grub menu, it goes to a black screen and i cannot get off of it. i reinstalled ubuntu 11.04 and everything was fine, then i compiled the realtk driver again and the same thing happened. i dont know whats the problem. If anyone can help i would gladly appreciate it. 
Thank you

louie

---

### Post by yungballla6 on 2011-08-09
please!

---

### Post by yungballla6 on 2011-08-10
Pleaseee

---

### Post by quicky2g on 2012-10-08
I have an [Acer Veriton Nettop]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883103629")  running Debain 6.0.6 with a Realtek RTL8192DE wireless card. I  downloaded the Unix/Linux driver from the Realtek website but compiling  the module from source kept failing. The README file mentioned using [compat-wireless]("http://linuxwireless.org/en/users/Download/stable/").  The versions of compat-wireless seemed to be organized based on kernel  versions. Debian is currently running 2.6.32-5. I tried compat-wireless  v2.6 but it didn't work.  After extracting the tar.bz2 file and going  through the README file, there's a command showing the wireless cards it  supports:
```
./scripts/driver-select
```v2.6 didn't have the right driver available. I downloaded v3.5 and it did:
```

Supported 802.11 drivers:
        ath5k
        ath9k
        ath9k_ap
        ath9k_htc
        carl9170
        ath6kl
        b43
        zd1211rw
        rt2x00
        wl1251
        wl12xx
        brcmsmac
        brcmfmac

Supported Ethernet drivers:
        atl1
        atl2
        atl1e
        atl1c
        alx

Supported group drivers:
        atheros <  ath5k ath9k carl9170 zd1211rw ath6kl >
        ath <  ath5k ath9k carl9170 ath6kl >
        brcm80211 <  brcmsmac brcmfmac >
        intel <  iwlwifi, iwlegacy >
        rtl818x <  rtl8180 rtl8187 >
        rtlwifi <  rtl8192ce >
        ti <  wl1251 wl12xx (SPI and SDIO)>

Supported group drivers: Bluetooth & Ethernet:
        atlxx <  atl1 atl2 atl1e alx>
        bt <  Linux bluetooth drivers >

```gcc, kernel headers, and all the other usual software for compiling packages should be installed. I compiled the driver  successfully using the instructions in the README file. Pay attention to  output after the scripts finish installing the kernel modules. There  are a few extra commands needed to load the drivers into the kernel and  reboot, but I can't remember what they are. I'm using the rtlwifi driver  with no problems. Hope this helps!

---

