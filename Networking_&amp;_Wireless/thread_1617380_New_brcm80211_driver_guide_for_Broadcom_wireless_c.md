---
title: "New brcm80211 driver guide for Broadcom wireless cards"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by Axx83 on 2010-11-09
**Update 29/04/2011**
The new broadcom driver is included in the 2.6.38 kernel that comes with Ubuntu 11.04 Natty Narwhal
I suggest everyone to just upgrade to the new version.


**Update 07/01/11**
Thanks to user [some-one]("http://ubuntuforums.org/member.php?u=1214853") the problem with git sources has been solved.
At the moment the only commit version that compiles in 10.10 is this one:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz](http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz)
Download the .tar.gz file in your home directory and extract it.
Now INSTEAD of "cd ~/linux-next/drivers/staging/brcm80211" you will do "cd ~/linux-next-a694cb1" and follow the rest of the guide strarting with "nano Makefile".

**START**
This guide has been tested and works on Ubuntu 10.10 Maverick amd64 installed on an Acer Travelmate 8172t with Broadcom **BCM43225** wireless device.

Currently supported chips
=========================
Name      Device ID
BCM4313   0x4727
BCM43224  0x4353
BCM43225  0x4357

This guide is based on this tutorial in the opensuse forum: [Opensuse installation guide]("http://forums.opensuse.org/english/get-help-here/hardware/447485-bcm43224-bcm43225-bcm4313-installation-guide.html") which is based on the README file inside the source code.

Make sure the proprietary broadcom driver is not loaded by the system, open "Additional driver" application in system > administration and disable the driver if it was enabled, restart if necessary.

Open terminal (Applications>Accessories>Terminal) and copy paste these lines one after another.

Install build packages
```
sudo apt-get install build-essential git-core
```


Download the driver and the firmware
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
```

Modify the file to make it work with your kernel
```
cd ~/linux-next/drivers/staging/brcm80211
nano Makefile
```

Add this code at the end
```
KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS)/include -I$(SUBDIRS)/sys -I$(SUBDIRS)/phy

default:
	echo $(PWD)
	$(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules
```
CTRL+X to exit and save


Compile the driver
```
make
```
If it exit with and error then check the UPDATE section at the top.


Copy it in the proper dir
```
sudo cp brcm80211.ko /lib/modules/`uname -r`/
```


Download and copy the device's firmware
```
sudo mkdir /lib/firmware/brcm
cd ~/linux-firmware
sudo cp brcm/bcm43xx* /lib/firmware/brcm
cd /lib/firmware/brcm
sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fw
sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw
```


Load the driver module
```
sudo modprobe mac80211
sudo insmod /lib/modules/`uname -r`/brcm80211.ko

```
At this point the wireless should work correctly in network-manager


Load dependencies
```
sudo depmod -a
```


Add the module to the startup
```
sudo nano /etc/modules
```
Add this lines at the end
```
brcm80211
```
CTRL+X to exit and save


Fix the problem with suspending
```
sudo nano /usr/lib/pm-utils/defaults
```
add after #SUSPEND_MODULES=""
```
SUSPEND_MODULES="brcm80211"
```
CTRL+X to exit and save

---

### Post by Axx83 on 2010-11-11
I need feedback guys...

---

### Post by sigiczek on 2010-11-11
My system is Ubuntu 10.10, Wireless card is BRCM4313, hardware is HP Mini 5103

Just installed the driver according to your description and everything works just as described.

I'm so relieved the BRCM 4313 finally works up to expectations, It was pain to work with the proprietary driver.

You've really made my day.:guitar:

---

### Post by sigiczek on 2010-11-11
Well after playing with it for a while, I've found a strange behavior. The speed of WiFi noticably drops, when the notebook goes on battery. 

It's a powersaving feature, that is quite annoying. The easy workaround is to set:

```
sudo iwconfig eth1 power off 
# presuming that eth1 is your wireless network device
```

which disables the power management feature of your card. Can be handy, when transfering larger files...

---

### Post by Axx83 on 2010-11-11
I am pretty sure power management in this version of the driver is not working, card is always on full power and the sudden drops you register are actually bugs, in fact if I run iwconfig whwn on battery it says power management is off.

Can you check just running
```
sudo iwconfig
```
when on battery with no other tweaks and post the results?

---

### Post by someonestolemyname on 2010-11-12
I got it working, and it has some nice advantages. It's a good bit faster when it works, and treats the network a lot better.

However, it seems to stop working after a minute when I'm connected to an N network. On G it is stable (more or less), but on N I need to reconnect often.

No guarantees that it isn't the network, my school has a screwed up network, but it never seemed to have stability issues with the proprietary driver.

How can I update it to follow new progress? Is there any?

p.s. I have the BCM43224 chip.

---

### Post by sigiczek on 2010-11-12
> **Axx83 said:**
> 
Can you check just running
```
sudo iwconfig
```when on battery with no other tweaks and post the results?

When on battery:
```
~$ sudo iwconfig

eth1      IEEE 802.11  ESSID:"7Patro.42"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1X:CX:6X:1X:DX   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-38 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid csudo iwconfigrypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ sudo iwconfig eth1 power off

~$ sudo iwconfig

eth1      IEEE 802.11  ESSID:"7Patro.42"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:C6:62:1B:D7   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=5/5  Signal level=-38 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```On AC Power, the power management is always off.

I've observed problems with 802.11b - just mere ping took several seconds and the troughtput was tragic, but it can be the AP at where I've checked it. With power management off, the throughtput is great, when it's set to the "All packets received", the ping drops to 200..300ms from the usual 2..5 ms...

My card is BRCM4313, my machine is HP Mini 5103. I'm so annoyed by the instability, that i've already considered swapping the card for some other, but the card is of custom size :(.

---

### Post by Axx83 on 2010-11-12
@someonestolemyname:
On my notebook the proprietary driver did not work AT ALL, connections were all dropped even before getting actually connected, with this driver not all is perfect but it's a development driver, still not stable so it's ok to have some issues. As far as updates go I don't know where to check...

@sigiczek:
Weird, on my computer if I run iwconfig and try to set power management it says it's not allowed...

---

### Post by ShouriChatterjee on 2010-11-13
I have the broadcom bcm4313 chipset.

I had problems with the proprietary wl driver. It would take a long time and not realize that the network it was trying to connect to does not exist etc.

brcm80211 compilation according to the instructions had glitches.
I had to do the following to "ccflags-y" in the Makefile:
```

ccflags-y :=                    \
    -DBCMDBG                \
    -DWLC_HIGH                \
    -DSTA                    \
    -DWME                    \
    -DWL11N                    \
    -DDBAND                    \
    -DBCMDMA32                \
    -DBCMNVRAMR                \
    -Idrivers/staging/brcm80211/sys        \
    -Idrivers/staging/brcm80211/phy        \
    -Idrivers/staging/brcm80211/util    \
    -Idrivers/staging/brcm80211/include    \
    -I/opt/kernel/linux-next/drivers/staging/brcm80211/include    \
    -I/opt/kernel/linux-next/drivers/staging/brcm80211/sys    \
    -I/opt/kernel/linux-next/drivers/staging/brcm80211/phy

```Compilation worked after that.

I did not put in the module name in the /etc/modules file - it works fine.

On the System->Administration -> Additional Drivers tab, I uninstalled all other drivers. Surprisingly it recognises brcm80211!

Wireless network is very fast now.

---

### Post by Jehosephat Q. Turnipseed on 2010-11-14
Tried it - it worked much faster than the Broadcom STA wl driver, but it was pretty unstable - only worked for a few minutes at a time.  Going to try ndiswrapper for now.

By the way /usr/lib/pm-utils/defaults undid my edits by itself.

---

### Post by Axx83 on 2010-11-14
> **Jehosephat Q. Turnipseed said:**
> Tried it - it worked much faster than the Broadcom STA wl driver, but it was pretty unstable - only worked for a few minutes at a time.  Going to try ndiswrapper for now.

By the way /usr/lib/pm-utils/defaults undid my edits by itself.

curious... on my system it's really stable so far, are you on lucid or maverick? 32 or 64 ?

---

### Post by Chitown on 2010-11-19
I now have Monitor mode and Injection working on my system. Ive been looking for a suitable drive to support these functions and here it is, Thanks a Million my friend!!

Hardware specs:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)

Module                  Size  Used by
brcm80211             674102  0 
mac80211              231541  1 brcm80211
cfg80211              144470  2 brcm80211,mac80211

---

### Post by hamidk on 2010-11-21
Thanks for the work.
BCM4313 ,as stated above, is working for me too. Both RFMON and Injection seems working, but the injection seems pretty alpha-quality ! Low rates and low success for injected packets, even for close AP. 

Anybody else having the same problem on injection?

my test bed: Ubuntu 10.10   2.6.35-22  64bit.

---

### Post by Jehosephat Q. Turnipseed on 2010-11-22
Axx83, I'm running kubuntu 10.10 with the 2.6.34-020634-generic kernel (to prevent a problem with system freezes on battery power), on a quad-core Intel studio 1558.  Ndiswrapper was a bust.  I'm back on the latest wl driver, which doesn't seem to want to get me to 802.11n speeds despite my n hardware.

---

### Post by Jehosephat Q. Turnipseed on 2010-11-22
Oh, by the way, 64-bit version.

---

### Post by Jehosephat Q. Turnipseed on 2010-11-22
The linux wireless wiki says that this driver is unstable for my card (43224) unless I restrict the kernel to one cpu.  I'll wait for a bit, I guess.

---

### Post by Axx83 on 2010-11-22
the linux wireless wiki is outdated, on my 43225 the driver is very stable

---

### Post by Jehosephat Q. Turnipseed on 2010-11-30
I know the kernel team has been making changes to the brcm80211 driver, so maybe I'll try the latest version.  The Broadcom STA proprietary driver (wl.ko) has been extremely slow (never connects over 53 MBits/sec, and often drops to 14 or even 2 MBits/sec, despite being 10 feet away from my router in the same room).

---

### Post by Jehosephat Q. Turnipseed on 2010-11-30
OK, installed the brcm80211 driver per the instructions - still somewhat unstable but maybe better?  According to the readme, it's still unstable with the 43224 chip and multicore processors (my situation).  Had a kernel panic in wlc_phy_n.c on line 19709 on one bootup.  Where's a good place to feed this info to the devs?

---

### Post by Axx83 on 2010-12-01
> **Jehosephat Q. Turnipseed said:**
> OK, installed the brcm80211 driver per the instructions - still somewhat unstable but maybe better?  According to the readme, it's still unstable with the 43224 chip and multicore processors (my situation).

Maybe that's the problem, I have 43225 and had no kernel panic, no connection drops, only a few sporadic issues with suspension and back, the networkmanager's list on networks was empty and only removing and inserting back the module did the trick.

> **Jehosephat Q. Turnipseed said:**
> Had a kernel panic in wlc_phy_n.c on line 19709 on one bootup.  Where's a good place to feed this info to the devs?

I wrote the developers about this and this was their answer:

We do not currently have a list specific to the brcm80211 driver. Patches and discussion are posted to [email]devel@linuxdriverproject.org[/email] and
[email]linux-wireless@vger.kernel.org[/email].
See [http://driverdev.linuxdriverproject.org/mailman/listinfo/devel](http://driverdev.linuxdriverproject.org/mailman/listinfo/devel)
and [http://linuxwireless.org/en/developers/MailingLists#About_the_Linux_wireless_mailing_list](http://linuxwireless.org/en/developers/MailingLists#About_the_Linux_wireless_mailing_list)
for information on these two lists.

---

### Post by Jehosephat Q. Turnipseed on 2010-12-01
Hmmmm...back to the wl (Broadcom STA) driver, which now seems faster as long as I am on ac and not battery power.  Kubutu's network manager reports very slow speeds, which are directly contradicted by online bandwidth tests, at least when I am on ac power.

---

### Post by Lupius on 2010-12-02
Can anyone point me to a git tutorial that will teach me how to get only the driver files I need and see when they were last updated? It really doesn't make sense that we have to clone the entire git repository every single time for just a few files.

---

### Post by alan2796 on 2010-12-02
Having some trouble never compiled a driver/kernel before and im getting some errors any help would be appriciated. 


```
alan@amg-laptop:~/linux-next/drivers/staging/brcm80211$ sudo make
echo 

make -C /lib/modules/2.6.32-26-generic/build SUBDIRS=/home/alan/linux-next/drivers/staging/brcm80211 CONFIG_BRCM80211_PCI=y V=1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-26-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/alan/linux-next/drivers/staging/brcm80211/.tmp_versions ; rm -f /home/alan/linux-next/drivers/staging/brcm80211/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/alan/linux-next/drivers/staging/brcm80211
  gcc -Wp,-MD,/home/alan/linux-next/drivers/staging/brcm80211/sys/.wl_mac80211.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-26-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -DBCMDBG -DWLC_HIGH -DSTA -DWME -DWL11N -DDBAND -DBCMDMA32 -DBCMNVRAMR -Idrivers/staging/brcm80211/sys -Idrivers/staging/brcm80211/phy -Idrivers/staging/brcm80211/util -Idrivers/staging/brcm80211/include -DWLC_LOW -I/home/alan/linux-next/drivers/staging/brcm80211/include -I/home/alan/linux-next/drivers/staging/brcm80211/sys -I/home/alan/linux-next/drivers/staging/brcm80211/phy  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(wl_mac80211)"  -D"KBUILD_MODNAME=KBUILD_STR(brcm80211)"  -c -o /home/alan/linux-next/drivers/staging/brcm80211/sys/.tmp_wl_mac80211.o /home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c: In function &#8216;wl_ops_config&#8217;:
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:296: error: &#8216;IEEE80211_CONF_CHANGE_MONITOR&#8217; undeclared (first use in this function)
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:296: error: (Each undeclared identifier is reported only once
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:296: error: for each function it appears in.)
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c: In function &#8216;wl_ampdu_action&#8217;:
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:591: warning: passing argument 1 of &#8216;ieee80211_start_tx_ba_cb_irqsafe&#8217; from incompatible pointer type
include/net/mac80211.h:2027: note: expected &#8216;struct ieee80211_hw *&#8217; but argument is of type &#8216;struct ieee80211_vif *&#8217;
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:595: warning: passing argument 1 of &#8216;ieee80211_stop_tx_ba_cb_irqsafe&#8217; from incompatible pointer type
include/net/mac80211.h:2068: note: expected &#8216;struct ieee80211_hw *&#8217; but argument is of type &#8216;struct ieee80211_vif *&#8217;
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c: At top level:
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:614: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:615: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:628: error: unknown field &#8216;sta_add&#8217; specified in initializer
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:628: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:629: error: unknown field &#8216;sta_remove&#8217; specified in initializer
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:629: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:630: warning: initialization from incompatible pointer type
make[2]: *** [/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.o] Error 1
make[1]: *** [_module_/home/alan/linux-next/drivers/staging/brcm80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-26-generic'
make: *** [default] Error 2


```

---

### Post by jimbrooking on 2010-12-04
Thank you for this.:KS You have saved my brand new ASUS eeePC 1013PED, running Ubuntu 10.10 (BCM4313 chipset) from a watery death in the toilet.

A question from a noob, if you don't mind: Will these mods survive an automatic Ubuntu update? If not, any shortcuts to restoring them after an update?

Thanks again. I am enjoying bonding with the new toy on a Real Operating System, as distinct from Windoze 7 for Dummies (Starter Ed.).

---

### Post by Axx83 on 2010-12-04
UNfortunately the modules are lost every time there is a KERNEL update to a higher kernel version, the kernel is the underlying operative system.

Just check the updates, don't make it automatic, and if there's a linux kernel new update just know that you'll have to redo the module procedure.

That's until the new ubuntu comes out which will have the driver from the start!!!

---

### Post by jimbrooking on 2010-12-04
Thought as much, but ever-hopeful.

I really appreciate your work, as I've been struggling with this wireless problem for a couple of days, and following your procedure everything worked perfectly the first time (with both the Flash Drive try-me version and the installed version).

I did test speeds both on battery and plugged in, and also ran on my desktop, which is hard-wired through the wireless router. All were comparable.

Thanks again.

Jim

---

### Post by alan2796 on 2010-12-04
I have managed to get it compiled and installed properly I think,

it's in additional drivers it is selected instead of the proprietary one, however it does not seem to work on my machine

lshw
> *-network UNCLAIMED
                description: Network controller
                product: BCM43225 802.11b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:d4600000-d4603fff


---

### Post by Axx83 on 2010-12-04
weird, are you sure the binary drivers are not being loaded?

---

### Post by lonniehenry on 2010-12-04
Just used it in a new HP g72t 4171us using a broadcom 4313 that the extra drivers didn't always work.  Connection was a hit and miss affair.  Now it connects immediately and solidly.  

Question about updating when we get a new kernal. Would we be able to make the process work if we started from the "sudo cp brcm80211.ko /lib/modules/`uname -r`/" step and then follow it to the end?

---

### Post by burukuru on 2010-12-04
> **alan2796 said:**
> Having some trouble never compiled a driver/kernel before and im getting some errors any help would be appriciated. 


```
alan@amg-laptop:~/linux-next/drivers/staging/brcm80211$ sudo make
echo 

make -C /lib/modules/2.6.32-26-generic/build SUBDIRS=/home/alan/linux-next/drivers/staging/brcm80211 CONFIG_BRCM80211_PCI=y V=1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-26-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/alan/linux-next/drivers/staging/brcm80211/.tmp_versions ; rm -f /home/alan/linux-next/drivers/staging/brcm80211/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/alan/linux-next/drivers/staging/brcm80211
  gcc -Wp,-MD,/home/alan/linux-next/drivers/staging/brcm80211/sys/.wl_mac80211.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.3/include  -Iinclude  -I/usr/src/linux-headers-2.6.32-26-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -DBCMDBG -DWLC_HIGH -DSTA -DWME -DWL11N -DDBAND -DBCMDMA32 -DBCMNVRAMR -Idrivers/staging/brcm80211/sys -Idrivers/staging/brcm80211/phy -Idrivers/staging/brcm80211/util -Idrivers/staging/brcm80211/include -DWLC_LOW -I/home/alan/linux-next/drivers/staging/brcm80211/include -I/home/alan/linux-next/drivers/staging/brcm80211/sys -I/home/alan/linux-next/drivers/staging/brcm80211/phy  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(wl_mac80211)"  -D"KBUILD_MODNAME=KBUILD_STR(brcm80211)"  -c -o /home/alan/linux-next/drivers/staging/brcm80211/sys/.tmp_wl_mac80211.o /home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c: In function ‘wl_ops_config’:
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:296: error: ‘IEEE80211_CONF_CHANGE_MONITOR’ undeclared (first use in this function)
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:296: error: (Each undeclared identifier is reported only once
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:296: error: for each function it appears in.)
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c: In function ‘wl_ampdu_action’:
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:591: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2027: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:595: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2068: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c: At top level:
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:614: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:615: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:628: error: unknown field ‘sta_add’ specified in initializer
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:628: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:629: error: unknown field ‘sta_remove’ specified in initializer
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:629: warning: initialization from incompatible pointer type
/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.c:630: warning: initialization from incompatible pointer type
make[2]: *** [/home/alan/linux-next/drivers/staging/brcm80211/sys/wl_mac80211.o] Error 1
make[1]: *** [_module_/home/alan/linux-next/drivers/staging/brcm80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-26-generic'
make: *** [default] Error 2


```

Having the exact same problem as alan2796.

Running bcm4313 on an eeepc 1015pem

I have a feeling I'm missing some includes but am not too sure. Anyone has ideas?

---

### Post by alan2796 on 2010-12-05
> **burukuru said:**
> Having the exact same problem as alan2796.

Running bcm4313 on an eeepc 1015pem

I have a feeling I'm missing some includes but am not too sure. Anyone has ideas?

I Solved this by upgrading to Ubuntu 10.10 I was on  LTS

I Possibly did not need to do that might of worked if I had just downloaded the 2.6.35-23-generic kernel ?

However after that unless I did something wrong it didn't work for me. both drivers are in Additional Drivers lsmod shows the brcm80211 as loaded and i removed the Broadcom STA Driver and enabled the brcm80211 but no power light on the wireless card and dosent appear in iwconfig

---

### Post by alejov on 2010-12-06
I dont know put on disble the driver, help me please, the option in spanish is delete the driver... im scared.


Sorry for my english im from Colombia. :p

---

### Post by Axx83 on 2010-12-07
> **alejov said:**
> I dont know put on disble the driver, help me please, the option in spanish is delete the driver... im scared.


Sorry for my english im from Colombia. :p

Are you talking about the program that permits you to choose the driver for the card ? It's called additional drivers, or something like that in spanish. In that case, just press that disable/delete button

---

### Post by alan2796 on 2010-12-08
Just thought id give a update managed to get it working finally don't ask me how though !

had a few issues with the speed but as far as I know, card went into monitor mode, and connected fine no issues with dropping out or anything.

Also installed no problem onto a Backtrack 4 RC2 Persistent USB and seemed to be going into Monitor mode and worked ok.

if theres any more info I can give just ask.

---

### Post by alejov on 2010-12-08
[LEFT]Hi guys, can i install build packages  and download the Drivers (steps 1 and 2) with the proprietary broadcom driver  enabled and after disable it and restart ... i only have wifi conection not lan... 

Step 1. 
Install build packages
[/LEFT]
```
sudo apt-get install build-essential git-core
```Step 2. 

Download the driver
     Code:
 ```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git 
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
```Thanks and sorry for my english :)

---

### Post by hinogi on 2010-12-09
I followed the instructions and it worked, the first time. After a upgrade it stopped working. I followed the instructions again but no change. Somehow it worked later that day again with no reason. Today after no updates and just a reboot it stopped working again. The driver always shows as active in the Additional Drivers tab but I really get an on and off with mostly off experience and I don't know how to diagnose where the problem is and how to fix it.

---

### Post by alan2796 on 2010-12-09
> **alejov said:**
> [LEFT]Hi guys, can i install build packages  and download the Drivers (steps 1 and 2) with the proprietary broadcom driver  enabled and after disable it and restart ... i only have wifi conection not lan... 

Step 1. 
Install build packages
[/LEFT]
```
sudo apt-get install build-essential git-core
```Step 2. 

Download the driver
     Code:
 ```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git 
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
```Thanks and sorry for my english :)

Yes Download everything you would need a Internet connection for first then disable the Broadcom STA Build and install your new Driver 

I would think you only need the STA Driver to be disabled when it comes to installing the modules ? 

```

sudo modprobe mac80211
sudo insmod /lib/modules/`uname -r`/brcm80211.ko

```

```

sudo depmod -a

```

---

### Post by Xirev on 2010-12-09
I followed the instructions in the first post and got WiFi working and was able to connect. However, the speed was almost half that of the STA driver, which already itself provides about half the speed I get on Windows 7 using the same laptop.

Also, the WiFi LED light on the laptop was turned off even though the WiFi was working, and when I tried to toggle WiFi using Fn+F3 the laptop hanged and I had to hard reboot.

I have the bcm43225 card on an Acer TimelineX 4820T, using Ubuntu 10.10.

Thanks for all your work Axx83, we really appreciate it.

---

### Post by alejov on 2010-12-09
Hi i follow all instructions and the new driver work finally, but after restart i cant get load ubuntu 10.10 i select it in grub and get black screen, ubuntu dont load im writing from the other os Windows 7... 

:cry:

 some body help me?

Thanks everybody!

---

### Post by hamidk on 2010-12-14
I've upgraded to new git revision of brcm80211 but the BIG problem about the driver seem not eliminated yet :

While driver works fine for usual tasks, and even is possible to inject packets (it`s required to use latest compat-wireless & patch it though) with acceptable rates, the problem with current driver is that driver does NOT process/receive any data packet while working in RFMON. Beacon traffic are received but no data packet is handled. 

Is it lack of RFMON implementation in current revisions, or a bug on my environment?(which I highly doubt, since others confirmed same problem)

---

### Post by Lupius on 2010-12-15
The inability to capture data packets is a known issue.

By the way, how did you get the compat-wireless to work with this driver for injection? So far I was only able to apply the channel -1 patch.

---

### Post by pol90 on 2010-12-17
> **alejov said:**
> Hi i follow all instructions and the new driver  work finally, but after restart i cant get load ubuntu 10.10 i select it  in grub and get black screen, ubuntu dont load im writing from the  other os Windows 7... 


Same thing happening to me right now. Any solution to this?

EDIT: It seems to be only happening when I boot with the wifi button turned off. If I boot into Windows and turn it on, then it boots correctly. Also, if I press the button at any time, system freezes. 
I can get the monitor mode working and also fixed the channel -1 thing, but no luck with injection...

---

### Post by topbayder on 2010-12-20
sorry, but how can you download all those packets when you have to disable the drivers that make the internet work.

hardwired it works fine but no wifi on my 4313. if i turn off the driver the hardwire doesnt work. 

any ideas?

---

### Post by juanfpina on 2010-12-20
I'm having a problem trying to compile this, first time, followed the directions. I have an id of 14e4:4727
> echo /home/juan/linux-next/drivers/staging/brcm80211
/home/juan/linux-next/drivers/staging/brcm80211
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/juan/linux-next/drivers/staging/brcm80211 CONFIG_BRCM80211_PCI=y V=1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/juan/linux-next/drivers/staging/brcm80211/.tmp_versions ; rm -f /home/juan/linux-next/drivers/staging/brcm80211/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/juan/linux-next/drivers/staging/brcm80211
  gcc -Wp,-MD,/home/juan/linux-next/drivers/staging/brcm80211/sys/.wlc_channel.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.4.5/include  -I/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DBCMDBG -DWLC_HIGH -DSTA -DWME -DWL11N -DDBAND -DBCMDMA32 -DBCMNVRAMR -Idrivers/staging/brcm80211/sys -Idrivers/staging/brcm80211/phy -Idrivers/staging/brcm80211/util -Idrivers/staging/brcm80211/include -DWLC_LOW -I/home/juan/linux-next/drivers/staging/brcm80211/include -I/home/juan/linux-next/drivers/staging/brcm80211/sys -I/home/juan/linux-next/drivers/staging/brcm80211/phy  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(wlc_channel)"  -D"KBUILD_MODNAME=KBUILD_STR(brcm80211)"  -c -o /home/juan/linux-next/drivers/staging/brcm80211/sys/.tmp_wlc_channel.o /home/juan/linux-next/drivers/staging/brcm80211/sys/wlc_channel.c
/home/juan/linux-next/drivers/staging/brcm80211/sys/wlc_channel.c: In function &#8216;wlc_channel_mgr_attach&#8217;:
/home/juan/linux-next/drivers/staging/brcm80211/sys/wlc_channel.c:632: error: implicit declaration of function &#8216;no_printk&#8217;
make[2]: *** [/home/juan/linux-next/drivers/staging/brcm80211/sys/wlc_channel.o] Error 1
make[1]: *** [_module_/home/juan/linux-next/drivers/staging/brcm80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [default] Error 2


---

### Post by aleksz on 2010-12-21
the gits are taking hours to download. is that normal???

---

### Post by raulelinformatico on 2010-12-21
Hello all. I'm facing the same problem that juanfpina is facing. I have an EeePC 1015PD. I installed 10.04 and everything worked fine but touchpad.  I upgraded then to Ubuntu 10.10 and now wifi is driving me crazy. If I install sta everything works fine until I reboot. After that it turns veeeeery slow and finally stops working at all. I wanted to try with this driver for mac but.... I can't compile it. waaaaa... ](*,)


Pleeeeeeease, someone help me!!!

Thanks a million

---

### Post by Axx83 on 2010-12-22
> **juanfpina said:**
> I'm having a problem trying to compile this, first time, followed the directions. I have an id of 14e4:4727

Unfortunately I seem to have the same problem with the latest linux git and latest ubuntu kernel

---

### Post by topbayder on 2010-12-22
sorry that last post wasn't very clear. I cant follow the "how to" because i cant download anything as my internet doesn't work at all. 

the internet works hardwired using the standard driver, but the "how to" tells me to uninstall the driver before starting the "how to" but then i cant download anything because i dont have the internet?

how is everyone else doing it?

---

### Post by juanfpina on 2010-12-22
> **topbayder said:**
> sorry that last post wasn't very clear. I cant follow the "how to" because i cant download anything as my internet doesn't work at all. 

the internet works hardwired using the standard driver, but the "how to" tells me to uninstall the driver before starting the "how to" but then i cant download anything because i dont have the internet?

how is everyone else doing it?
What do you mean hardwired? You just have to uninstall the wireless driver, and you can download the gits first then do the rest after you uninstall the drivers and reboot.

---

### Post by juanfpina on 2010-12-22
> **Axx83 said:**
> Unfortunately I seem to have the same problem with the latest linux git and latest ubuntu kernel

So I redid this, instead of using git on the first link I used the link provided here [http://wireless.kernel.org/en/users/Drivers/brcm80211](http://wireless.kernel.org/en/users/Drivers/brcm80211) and I was able to compile it. It's all working for me now I just need to check if it's able to go into monitor mode.

Edit:
After trying to work with aircrack, it gets stuck at -1, I tried applying the patch but now whenever I start it in monitor mode my laptop seems to crash and turn right off. Other than that it is working well.

---

### Post by raulelinformatico on 2010-12-24
:D Juanfpina, you are my hero. I used that other source that you recommended and it worked!! I was able to compile and complete the tutorial made by Axx83. Thank you both so much. I was seariously going crazy with this and now it works, not perfectly but well enought.


Thank you, thank you, thank you...!!

---

### Post by Axx83 on 2010-12-24
I added the 2 other servers you guys mentioned, at the moment only the second git one compiles and works for me

---

### Post by sheph on 2010-12-26
> **juanfpina said:**
> I'm having a problem trying to compile this, first time, followed the directions. I have an id of 14e4:4727

I got this too initially.  I compiled bleeding edge driver from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)
and while it compiled successfully it locks up faithfully everytime I use it.

---

### Post by Vaun on 2010-12-27
Not sure if this is proper, but was relatively easy to get working in Natty 11.04 64 bit.

```
wget http://ftp.us.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-brcm80211_0.27_all.deb

```

```
sudo dpkg -i firmware-brcm80211_0.27_all.deb 
```

```
sudo modprobe brcm80211
```

Reload from suspend:

```
cd /etc/pm/config.d/
```

```
sudo echo "SUSPEND_MODULES=\"brcm80211\"" > suspend-modules
```

I disabled the Broadcom STA via jockey and rebooted. The brcm80211 loaded with no issues.

It is much faster than the closed wl driver as I was only getting a quarter of my available download bandwidth of 24 Mbps.  It also connects to a network faster, approximately two seconds, on reboot and resume from suspend.

Still testing, but so far so good.

---

### Post by giowck on 2010-12-28
Thank you for this guide!

Now my BCM4313 is woking on the HP mini... With the Broadcom STA drivers from the drivers manager, the speed was terribly slow!

But now, it works perfectly! BTW only the alternative git address works for me, no make errors now...

The steps I did:

1. Install
```
sudo apt-get install build-essential git-core
```

2. Download the firmware
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
```

3. Download driver module sources (this is the only address where make compiles without errors)
```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging-2.6.git
```

4. Follow the original Guide:
> 
Modify the file to make it work with your kernel
Code:
cd ~/linux-next/drivers/staging/brcm80211
nano Makefile
Add this code at the end
Code:
KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS)/include -I$(SUBDIRS)/sys -I$(SUBDIRS)/phy

default:
	echo $(PWD)
	$(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules
CTRL+X to exit and save


Compile the driver
Code:
make

Copy it in the proper dir
Code:
sudo cp brcm80211.ko /lib/modules/`uname -r`/

Download and copy the device's firmware
Code:
sudo mkdir /lib/firmware/brcm
cd ~/linux-firmware
sudo cp brcm/bcm43xx* /lib/firmware/brcm
cd /lib/firmware/brcm
sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fw
sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw

Load the driver module
Code:
sudo modprobe mac80211
sudo insmod /lib/modules/`uname -r`/brcm80211.ko
At this point the wireless should work correctly in network-manager


Load dependencies
Code:
sudo depmod -a

Add the module to the startup
Code:
sudo nano /etc/modules
Add this lines at the end
Code:
mac80211
brcm80211
CTRL+X to exit and save


Fix the problem with suspending
Code:
sudo nano /usr/lib/pm-utils/defaults
add after #SUSPEND_MODULES=""
Code:
SUSPEND_MODULES="brcm80211"
CTRL+X to exit and save



reboot and it works :D

---

### Post by sheph on 2010-12-31
I got it working under Backtrack 4 r2 following the instructions from giowck and Axx83.  However, I had to do a couple of other things:

DO NOT ADD brcm80211 or mac80211 to /etc/modules.  That's what was causing my system to lock up.

Next, wl needs to be added to the blacklist, or it will attempt to use it each time the system is started.  To do that issue the following command:
<code>
sudo nano /etc/modprobe.d/blacklist
</code>

Add these two lines at the top:

<code>
# Kill default wl driver and its sidekick
blacklist wl
blacklist lib80211
</code>
CTRL+X to exit and save

Also, the file to implement the suspend fix is different, it's located at...
/etc/pm/config.d/00sleep_module

---

### Post by juanfpina on 2011-01-01
> **sheph said:**
> I got it working under Backtrack 4 r2 following the instructions from giowck and Axx83.  However, I had to do a couple of other things:

DO NOT ADD brcm80211 or mac80211 to /etc/modules.  That's what was causing my system to lock up.

Next, wl needs to be added to the blacklist, or it will attempt to use it each time the system is started.  To do that issue the following command:
<code>
sudo nano /etc/modprobe.d/blacklist
</code>

Add these two lines at the top:

<code>
# Kill default wl driver and its sidekick
blacklist wl
blacklist lib80211
</code>
CTRL+X to exit and save

Also, the file to implement the suspend fix is different, it's located at...
/etc/pm/config.d/00sleep_module
What card do you have? What functions are possible? Is anything not working?

---

### Post by DieseL1988 on 2011-01-05
I got the driver working on a Lenovo S10-3s which has a bcm4313.

It ran really well, alot faster than the STA driver. However, it locked up the OS upon resume. I've uninstalled and gone back to the STA driver for now as It's at least stable.

The wireless driver is now really the only issue with running Ubuntu on a Lenovo S10-3s. It would be excellent to see this driver in the next release, hopefully it'll clear up the suspend/resume issues - the STA driver stops working upon resume.

---

### Post by Axx83 on 2011-01-05
I still have problems with 2 of the code sources available. Only the 3rd address compiles correctly but I fear it's an old version of the driver.

---

### Post by some-one on 2011-01-06
Instead of cloning all the entire repository I browse it in [http://git.kernel.org]("http://git.kernel.org"), and you can download a specific version of the driver.

Here is the history of the driver:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=f4528696d803749892eac27422a6fd7748cffee1]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=f4528696d803749892eac27422a6fd7748cffee1")

The last commit was "2010-12-16 Joe Perches staging: brcm80211: Fix WL_<type> logging macros", that is the version with problems, but the version "2010-12-16 Joe Perches staging: brcm80211: Convert ETHER_TYPE_802_1X to ETH_P_PAE" compiles.
If you click in the link tree of that version and then in snapshot you can download that specific commit of the driver.
link:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz")

Sorry, but my English is terrible

---

### Post by Axx83 on 2011-01-07
> **some-one said:**
> Instead of cloning all the entire repository I browse it in [http://git.kernel.org]("http://git.kernel.org"), and you can download a specific version of the driver.

Here is the history of the driver:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=f4528696d803749892eac27422a6fd7748cffee1]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=f4528696d803749892eac27422a6fd7748cffee1")

The last commit was "2010-12-16 Joe Perches staging: brcm80211: Fix WL_<type> logging macros", that is the version with problems, but the version "2010-12-16 Joe Perches staging: brcm80211: Convert ETHER_TYPE_802_1X to ETH_P_PAE" compiles.
If you click in the link tree of that version and then in snapshot you can download that specific commit of the driver.
link:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz")

Sorry, but my English is terrible

You're a genius!!! I'm updating the guide right now :-)

---

### Post by mrkrinkle2 on 2011-01-09
I have followed all the instructions on my HP Mini without error however my wireless is now disabled?

Ubuntu 11.04
2.6.35-24-generic

**lspci -vvnn | grep 14e4**
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
[B]
lshw -C network[/B]
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:f3:a3:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:52000000-52003fff

**lsmod**
Module                  Size  Used by
parport_pc             26058  0
ppdev                   5556  0
snd_hda_codec_idt      54887  1
binfmt_misc             6599  1
snd_hda_intel          22107  2
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
i915                  294989  3
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
joydev                  8767  0
brcm80211             674442  0
snd_seq_midi            4588  0
snd_rawmidi            17783  1 snd_seq_midi
lib80211_crypt_tkip     7736  0
mac80211              231541  1 brcm80211
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
wl                   2637607  0
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168092  3 i915,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0
hp_wmi                  5223  0
intel_agp              26694  2 i915
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               43098  1 uvcvideo
cfg80211              144470  2 brcm80211,mac80211
i2c_algo_bit            5168  1 i915
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0
video                  18712  1 i915
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lib80211                5058  2 lib80211_crypt_tkip,wl
serio_raw               4022  0
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2
libahci                21664  1 ahci
r8169                  36489  0
mii                     4425  1 r8169

**modinfo brcm80211**
filename:       /lib/modules/2.6.35-24-generic/brcm80211.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     370CDCBC47C65D9E86B1F33
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,cfg80211
vermagic:       2.6.35-24-generic SMP mod_unload modversions 686 
parm:           msglevel:int
parm:           phymsglevel:int
will@will-HP-Mini-110-3100:~$

---

### Post by tew11 on 2011-01-09
I have the same problem on my Dell E6410. I managed to:
1) compile brcm80211.ko,
2) depmod -a
3) modprobe brcm80211
4) copy firmware into /lib/firmware/brcm
5) iwconfig showed wlan0

However, couldnt detect any wireless network in both managed or monitor mode. When I use broadcom STA driver I can at least use it in managed mode.

Any suggestion? Thanks.

---

### Post by Axx83 on 2011-01-09
Try
```
sudo rfkill unblock all
```
and see if it works

---

### Post by moikop on 2011-01-09
Works perfectly on 4313. It's faster than the wl driver.
But does this enables monitor mode?
I've read that it doesn't. But I tried and it seems to be working..

---

### Post by yehia2amer on 2011-01-09
Can i rebrand a broadcom 43224AG (14E4,4353) card using the new brcm80211 driver

with a method like this (it use b43 driver), but it is not working for me, i think my card is not supported

```
# Install packages that are required and Install b43 driver and firmware, when asked if you'd like to fetch and extract firmware - say YES
sudo apt-get update
sudo apt-get install build-essential curl git-core b43-fwcutter
sudo modprobe b43

# Get, compile, and install the latest ssb-sprom tool
git clone git://git.bu3sch.de/b43-tools.git
cd b43-tools/ssb_sprom
make
sudo cp ssb-sprom /usr/sbin/
sudo chmod 755 /usr/sbin/ssb-sprom
sudo chown root:root /usr/sbin/ssb-sprom



3. Update the sprom - Open up a terminal window and execute the following commands:


SSB_SPROM=$(find /sys/devices -name ssb_sprom)
echo $SSB_SPROM
cd ~
sudo cat $SSB_SPROM > ssb_sprom_copy
ssb-sprom -i ssb_sprom_copy -P
ssb-sprom -i ssb_sprom_copy --subv <NEW VENDOR ID> --subp <NEW PRODUCT ID> -o new_ssb_sprom_copy
ssb-sprom -i new_ssb_sprom_copy -P
echo $SSB_SPROM
sudo cp new_ssb_sprom_copy $SSB_SPROM


```

Thanks

---

### Post by mrkrinkle2 on 2011-01-10
> **Axx83 said:**
> Try
```
sudo rfkill unblock all
```and see if it works

I tried the above with no apparent change.

**rfkill list** provides the following;

0: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

This suggests that it is 'hard blocked' but an rfkill unblock doesn't seem to help?

---

### Post by PatchesTheCaveman on 2011-01-10
A hard block usually means your wireless switch is turned off.  Try and flip it.  It might be a physical switch, a discrete button, or a Fn key combination.

If that doesn't work you'll need to provide us with the diagnostic information requested by this post for us to be able to troubleshoot your issue:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by mrkrinkle2 on 2011-01-10
> **PatchesTheCaveman said:**
> A hard block usually means your wireless switch is turned off.  Try and flip it.  It might be a physical switch, a discrete button, or a Fn key combination.

If that doesn't work you'll need to provide us with the diagnostic information requested by this post for us to be able to troubleshoot your issue:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)


THANK YOU!  :D

Thanks to **PatchesTheCaveman**, **Axx83** and **giowck** I finally got my wireless working on my HP Mini.

For reference, the setup I have is;

HP Mini
Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
Ubuntu 11.4
2.6.35-24-generic

I followed giowck's guide (which just expands on Axx83's original guide) and PatchesTheCaveman kindly alerted me to the Fn F12 key combination which enables / disables the wireless on a HP Mini for those that  don't know ;-) 

Happy now...

Below is network info now it's working;

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:197  Noise level:161
          Rx invalid nwid:0  invalid crypt:4  invalid misc:0

**rfkill list**
0: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by yehia2amer on 2011-01-10
can anyone answer me Please, i want to rebrand my Broadcom card using this card can I

even with a link or a hint to begin with

thanks

---

### Post by PALKOVNIK on 2011-01-11
hi
i've builded the module and it has started
but, iwlist and network-manager show the network list, however i can't connect to any network
bcm4313, Asus eeepc 1015PEM, ubuntu 10.10 i386
uname -a
Linux PALKOVNIK-Eee 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

---

### Post by PALKOVNIK on 2011-01-12
mmm, i've got a question
does this driver work in ad-hoc mode??

---

### Post by Azmir on 2011-01-12
Hi guys,

Im using Ubuntu 10.10 Maverick 64bit installed on Dell Vostro 3700 with Broadcom BCM43224 wireless device.

When i execute "make" i hit error as you seen below.

I did follow both Axx83 and giowck guide. And yet both guide hit same error.

Anybody can tell me where it gone wrong ?
I really appreciate it. Thanks.


```

/home/azmir/linux-next-a694cb1/linux-next/drivers/staging/brcm80211/sys/wlc_channel.c: In function ‘wlc_channel_mgr_attach’:
/home/azmir/linux-next-a694cb1/linux-next/drivers/staging/brcm80211/sys/wlc_channel.c:632: error: implicit declaration of function ‘no_printk’
make[2]: *** [/home/azmir/linux-next-a694cb1/linux-next/drivers/staging/brcm80211/sys/wlc_channel.o] Error 1
make[1]: *** [_module_/home/azmir/linux-next-a694cb1/linux-next/drivers/staging/brcm80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [default] Error 2
azmir@Azmir-UBUNTU:~/linux-next-a694cb1/linux-next/drivers/staging/brcm80211$

```

---

### Post by Axx83 on 2011-01-13
In the first post you should read the UPDATE section that says that you should use that specific link and not the normal git repository for the moment because of an unknown error in the latest version

---

### Post by Azmir on 2011-01-13
@Axx83
Are you saying this link

```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging-2.6.git

```

or

```

http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz

```

---

### Post by Axx83 on 2011-01-13
> **Azmir said:**
> @Axx83
Are you saying this link

```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging-2.6.git

```

or

```

http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz

```

I think the second one, anyway if you go on the first page there's the link. You just extract in the home folder or anywhere you like and follow the guide substituting for this folder and not the standard one.

I'm still not changing the original guide because the main procedure is better for future updates.

---

### Post by Azmir on 2011-01-13
Ok guys,
I successfully manage to compile. :D 

Step 1 :- 
Download the file below, extract it and rename it to brcm80211.
```

http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=a694cb1016824f478da2dcef9658f902aefe3b14;sf=tgz

```

Step 2 :- Download this file
```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git

```

Step 3 :- Download this file and rename the folder to linux-next
```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging-2.6.git

```

Step 4 :- 
```

Make sure the proprietary broadcom driver is not loaded by the system, open "Additional driver" application in system > administration and disable the driver if it was enabled, restart if necessary.

```

Step 5 :-
```

Open Terminal, go to correct address (it should be ~/linux-next-a694cb1) and run..
sudo apt-get install build-essential git-core

```

Step 6 :- 
```

cd ~/linux-next/drivers/staging/
i delete folder brcm80211 and replace with the one i downloaded in step 1

```

Step 7 :-
```

cd ~/linux-next/drivers/staging/brcm80211
nano Makefile

```


Step 8 :-
```

KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS)/include -I$(SUBDIRS)/sys -I$(SUBDIRS)/phy

default:
	echo $(PWD)
	$(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules

```

Step 9 :-
```

make

```


Compilation success. :D
Expert out there, if my steps is wrong, please tell and guide me. This is first time i use linux. :D

---

### Post by Azmir on 2011-01-14
My wireless now running driver brcm80211. But i hit annoying problem.

I only can use after second reboot. 1st time boot, my laptop hang. 2nd time , GRUB screen show up and i can login back.

Anyone facing same problem with me ?

---

### Post by Axx83 on 2011-01-14
I modified the guide to simplify things

---

### Post by Micronaut on 2011-01-15
works on Dell XPS M1530 running Linux Mint 10.  

Thanks for posting the guide.

---

### Post by krvermeulen on 2011-01-17
Thanks for the guide, all's working fine. My laptop hung a few times after installing the driver, making me switch it off and on with the power button. It seems to be doing fine now. 

If I read one of the posts correctly, the installed drivers are all being deleted by doing a kernel update. Is that correct? 

Thanks again for helping this Ubuntu n00b =).

---

### Post by krvermeulen on 2011-01-17
EDIT: Double post.

---

### Post by moikop on 2011-01-18
Has anyone tried this on Ubuntu 10.04?
I'm trying to install it but it won't compile. ? tried with both download links and it still don't :/
Thanks in advance :D

---

### Post by dreamaker.jorge on 2011-01-20
I can't


dream@dream-AO533:~$ sudo apt-get install build-essential git-core
[sudo] password for dream: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
git-core ya está en su versión más reciente.
Los siguientes paquetes se instalaron automáticamente y no son necesarios:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic dkms
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 18 no actualizados.
1 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Configurando firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error al procesar firmware-b43-lpphy-installer (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
Se encontraron errores al procesar:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
what is the problem? thanks

---

### Post by some-one on 2011-01-21
Hi dreamaker.jorge, your problem is that you need to uninstall the packets b43, b43legacy, firmware-b43-lpphy-installer,

```
Configurando firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
```

It says that your card is not supported, I think you have the card BRCM 4313 (for  the PCI id).
Go to Synaptic and uninstall that packets and then try with the guide of the first page of this thread.

---

### Post by some-one on 2011-01-21
There are new commits but they still not compile. The problem is in this commit
***staging: brcm80211: Fix WL_<type> logging macros***
In it the developers added the functions ***printk*** and ***no_printk***, but they forgot to implement them.
I made a little scrip to correct the code, it only erases that functions from the code.

When you go to the directory  ~/linux-next/drivers/staging/brcm80211
You need to do this:

create the scrip
```
nano script.sh
```

Add:
```
#!/bin/bash

for file in ./brcmfmac/*
do
	sed -e 's/no_printk(.*)//' -i ${file}
	sed -e 's/printk(.*)//' -i ${file}
done

for file in ./sys/*
do
	sed -e 's/no_printk(.*)//' -i ${file}
	sed -e 's/printk(.*)//' -i ${file}
done
```

Save and exit

execute
```
sudo chmod 777 script.sh
```

execute
```
./script.sh
```

and then compile the driver

Hope this help someone. And again sorry for my poor English

---

### Post by mauricio.dev on 2011-01-23
Hey, thanks for the how-to! I've sucessfully compiled (using the updated linux-next) on ubuntu 10.10 Dell Vostro 3500.
Now the latency is regular and on 1.3ms inside the lan as expected. Before the fix it often got to 200ms.
Now I just wish ubuntu devs used this driver instead.
Thanks a lot!

---

### Post by jmpratt on 2011-01-24
I did everything per the guide, but when I tried
"sudo insmod /lib/modules/`uname -r`/brcm80211.ko"
I got an error saying there was an invalid parameter.  I continued on with the rest of the steps.  Now, when I try to login, the screen goes black and keeps repeating the last two seconds of the login music.  Any ideas?

I have Ubuntu 10.10 on a Dell Studio XPS 1640 w/ a Broadcomm 43224 wifi card.

---

### Post by jmpratt on 2011-01-24
In reference to the previous post, I was having problems with my wifi before I tried this guide.  I could not get the wl module to load.  I don't know if that means anything.

---

### Post by Freyr92 on 2011-01-26
@jmpratt

I had that error, but I found that the notebook has a button to turn off the wl (and bluetoth) than to boot the system automatically shuts down, turned it on and ready #-o :oops:

---

### Post by jmpratt on 2011-01-29
Ok, I got the driver to compile and load.  It worked for a few minutes, then my computer locked up with a black screen.  Now I don't have the option to enable wireless in the Network Manager any more.  I can turn the wifi on and off, but Ubuntu doesn't seem to recognize it.  I get:

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:26:b9:1f:a9:b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v2.17 latency=0 multicast=yes
       resources: irq:49 memory:fc000000-fc00ffff

Any hints?

---

### Post by jmpratt on 2011-01-29
Got it working!  For some reason the Broadcomm 43224 wouldn't respond in Windows or Ubuntu.  I pulled it out, rebooted, shutdown, reinstalled the card, rebooted, and everything worked!  Thanks for all the help.

Dell Studio XPS 1640 w/ Broadcomm 43224

---

### Post by prubyholl on 2011-01-29
I have successfully compiled and using the brcm80211 on dell vostro 3500 running ubuntu 10.10AMd64

I had the usual first time boot hang but it looks stable now

my only problem is with these log lines in kernel/messages logs

08 phat kernel: [ 2681.629290] Short CCK
Jan 29 16:38:08 phat kernel: [ 2681.683154] Short CCK
Jan 29 16:38:08 phat kernel: [ 2681.731278] Short CCK
Jan 29 16:38:08 phat kernel: [ 2681.780978] Short CCK
Jan 29 16:38:08 phat kernel: [ 2681.830844] Short CCK
Jan 29 16:38:08 phat kernel: [ 2681.876783] Short CCK


 24.520837] wl0: wlc_d11hdrs_mac80211: AC_BE txop exceeded phylen 214/256 dur 2218/1504
Jan 29 17:32:52 phat kernel: [   24.569903] wl0: wlc_d11hdrs_mac80211: AC_BE txop exceeded phylen 201/256 dur 2114/1504


seems to be filling up and increasing the size of my log files. I did some google search and found a bug to do with the brcm80211 driver but I want to know if any one experiences same.

could it be my BIOS needing upgrade? as pls help

thanks

---

### Post by I_Am_Einstein on 2011-01-31
hi everyone,

cannot confirm this worked, but:

If you get the ERROR 2 and other errors when you do "make", it is because

You Must Add The Code At The End, (NOT at the beginning!)
[also I suggest to use gedit instead of nano!] =)

---

### Post by shiman6 on 2011-02-01
I did everything according to instruction, but the computer still isnt associating the driver with the card. The module initializes fine, no errors reported, but it still doesnt associate with the NIC
lspci -v output:
```


02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Hewlett-Packard Company Device 145c
	Flags: fast devsel, IRQ 17
	Memory at 90100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: wl, brcm80211

```
it doesnt show up on rfkill list, 
and lshw -C network outputs this:
```


*-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:90100000-90103fff

```
Any help? I uninstalled and blacklisted b43, b43legacy, the proprietary drivers, and wl.

Almost forgot, running ubuntu 10.10 on an HP g56, single core amd x64 processor, 2gb ram.

---

### Post by ibfelzmann on 2011-02-05
Is this working on 10.04 LTS?
I tried both cloning de repository and also downloading just de right snapshot, and god the same error:

```

/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c: In function ‘wl_ops_config’:
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:296: error: ‘IEEE80211_CONF_CHANGE_MONITOR’ undeclared (first use in this function)
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:296: error: (Each undeclared identifier is reported only once
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:296: error: for each function it appears in.)
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c: In function ‘wl_ampdu_action’:
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:591: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2027: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:595: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2068: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c: At top level:
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:614: warning: initialization from incompatible pointer type
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:615: warning: initialization from incompatible pointer type
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:628: error: unknown field ‘sta_add’ specified in initializer
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:628: warning: initialization from incompatible pointer type
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:629: error: unknown field ‘sta_remove’ specified in initializer
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:629: warning: initialization from incompatible pointer type
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:630: warning: initialization from incompatible pointer type
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c: In function ‘wl_check_firmwares’:
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:1817: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘size_t’
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:1817: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘long unsigned int’
/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.c:1822: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘size_t’
make[2]: ** [/home/ibfelzmann/linux-next-a694cb1/sys/wl_mac80211.o] Erro 1
make[1]: ** [_module_/home/ibfelzmann/linux-next-a694cb1] Erro 2
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.32-28-generic'
make: ** [default] Erro 2

```[I_Am_Einstein]("http://ubuntuforums.org/member.php?u=1233447") said "*If you get the ERROR 2 and other errors when you do "make", it is because You Must Add The Code At The End, (NOT at the beginning!)*". For sure, I am adding it at the end of the file.

```
12:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4353] (rev 01)
    Subsystem: Dell Device [1028:000e]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at fbd00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: eth1
       version: 01
       serial: 5c:ac:4c:97:2e:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:fbd00000-fbd03fff

```The card is working with wl driver, but the connection is very slow and unstable...

---

### Post by juanfpina on 2011-02-06
The Makefile seems to have changed in the newer version, it won't compile with the old edits.

---

### Post by goldeneyexs on 2011-02-11
I'm running BCM43224 (macbookpro 6,2) and I've been having random system crashes after updating the driver as described in this guide.

I found this patch, [https://patchwork.kernel.org/patch/504981/](https://patchwork.kernel.org/patch/504981/) which may or may not be my problem.  As the problem is random, I won't know for a few days but figured I would share in case others were having problems.

EDIT-1:
Here's a fixed makefile though, I have verified it makes a *.ko, but I have not yet tried the module: REMOVED (see below)

You will also need to open brcmsmac/wl_dbg.h and change the code near the top like below
//#define WL_NONE(fmt, args...) no_printk(fmt, ##args)
#define WL_NONE(...)

NOTE: Above is a quick and dirty hack, probably a better idea to actually add the right no_printk include, but I'm getting redefinition errors.

EDIT-2:
I have verified module works on my machine, for at least my chipset

EDIT-3:
See post #101 for simpler, and fixed directions [http://ubuntuforums.org/showpost.php?p=10451875&postcount=101](http://ubuntuforums.org/showpost.php?p=10451875&postcount=101)

---

### Post by Axx83 on 2011-02-11
> **juanfpina said:**
> The Makefile seems to have changed in the newer version, it won't compile with the old edits.

I've seen that as well, I really don't know how to solve the problem

---

### Post by ibfelzmann on 2011-02-12
goldeneyesx:
You makefile is just a blank text :S
Is the driver working in your system without any crash?
I could use it under Debian Squeeze (the driver is included by default...), just installing the firmware from Squeeze non-free repository. But it caused many crashes on my system. That patch should work, I think, but I don't know how to aply it (may I edit the source code, maybe?).
Anyway, I downloaded the Broadcom STA driver (wl) directly from Broadcom website. It is a little more up-to-date (sorry for my English :P) than the one I was using in Lucid, but seems to be much more stable...

---

### Post by goldeneyexs on 2011-02-12
Attached you will find a patch that I can only promise will cleanly apply to 7d5fc5c4d03.

Save the file to your home then run the following commands:

```

#from ~/linux-next if you followed OP
git apply --check ~/brcm80211.txt
#IF NO ERROR CONTINUE
git apply ~/brcm80211.txt
cd drivers/staging/brcm80211
make

```

If the patch does not apply cleanly try (these steps are for the future after this post and the patch becomes stale), then try above again.
```

git reset --hard
git checkout 7d5fc5c4d03

```

---

### Post by goldeneyexs on 2011-02-12
> **ibfelzmann said:**
> goldeneyesx:
You makefile is just a blank text :S
Is the driver working in your system without any crash?
I could use it under Debian Squeeze (the driver is included by default...), just installing the firmware from Squeeze non-free repository. But it caused many crashes on my system. That patch should work, I think, but I don't know how to aply it (may I edit the source code, maybe?).
Anyway, I downloaded the Broadcom STA driver (wl) directly from Broadcom website. It is a little more up-to-date (sorry for my English :P) than the one I was using in Lucid, but seems to be much more stable...

Sorry about the blank makefile...copy/paste error I guess.  I have yet to have a crash running the new patch.  I will not say it's fixed all issues until I use it for a few days, as the problem could take up to 6 hours before it would crash.

I had an issue with the STA driver and wpa2 enterprise disconnects, which may or may not have been caused by network manager, which I have since removed trying to troubleshoot the crashes.

If you follow my new directions above, you will get the patch I mentioned.

---

### Post by mybloo on 2011-02-12
my bcm4313 doesn't capture any packet with airodump, I read somethind about wireshark and b43 drivers but I haven't understand very well...

---

### Post by naveedahmadkhan on 2011-02-12
> **burukuru said:**
> Having the exact same problem as alan2796.

Running bcm4313 on an eeepc 1015pem

I have a feeling I'm missing some includes but am not too sure. Anyone has ideas?


I am also having same problem, Plz help us

---

### Post by some-one on 2011-02-12
> **Axx83 said:**
> I've seen that as well, I really don't know how to solve the problem

The driver now is divided in two, brcm full mac and brcm soft mac. The first one doesn't compile, but the second one does.

For compile you have to download the driver from this link:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=52bac5bcaca7fa5372e02a74cf08e6e7f4d1e202;sf=tgz]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=52bac5bcaca7fa5372e02a74cf08e6e7f4d1e202;sf=tgz")

You always can download the latest version browsing the git:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=HEAD")

Uncompress the file and then go to this folder:
```
cd linux-next-52bac5b/brcmsmac/
```

There is a Makefile in that folder, you have to add this lines:
```
KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS) -I$(SUBDIRS)/../include -I$(SUBDIRS)/../util -I$(SUBDIRS)/phy

default:
	echo $(PWD)
	$(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules
```

And then you have to erase some function calls to "no_printk", I don't know what are they for, but there are just for debugging (for the driver developers), you have to execute this command

```
sed -e 's/no_printk(.*)//' -i wl_dbg.h
```

Without that command the driver doesn't compile.

Then execute make and if there is no problem the driver compiles. One more thing, now the output file is named brcmsmac.ko

you can renamed it
```
mv brcmsmac.ko brcm80211.ko
```

And then do the things from the guide.

---

### Post by mybloo on 2011-02-13
brcm80211 is not getting data packets... I have bcm4313

---

### Post by juanfpina on 2011-02-13
> **mybloo said:**
> brcm80211 is not getting data packets... I have bcm4313

Was it able to do this before? From my knowledge it wasn't able to before but I may be wrong.

---

### Post by mybloo on 2011-02-13
> **juanfpina said:**
> Was it able to do this before? From my knowledge it wasn't able to before but I may be wrong.
itwas not able... I read something about wireshark but I don't understand...

---

### Post by ubuntuforums on 2011-02-19
Installing wireless via Additional Drivers worked yesterday, but today I reinstalled Ubuntu and Jockey Backend kept crashing.

I followed your guide under Ubuntu 10.10 x64 for my BCM43224. Thank you for the easy step by step guide, it worked perfectly. With the generic driver from Additional Drivers my ping was always fluctuating, speedtest.net alone showed it jumping up and down every second. With the driver from your guide it is now stable and oddly enough I'm hitting speeds slightly faster than in Windows 7.

Thanks again. :)

---

### Post by Lupius on 2011-02-19
This driver shows up in the driver list as "Broadcom 802.11n", but it will only work with my router in bgn mode. If I set my router to "n only mode", the connection would drop, and it would repeatedly ask for my password. Is this something that can be easily fixed?

---

### Post by foxjazz on 2011-02-19
I had problems at:
cd ~/linux-next/drivers/staging/brcm80211

no such file or directory exists.

Yes, new to linux ubuntu.

can you write a script program that will do this update auto?

---

### Post by ubuntuforums on 2011-02-20
> **foxjazz said:**
> I had problems at:
cd ~/linux-next/drivers/staging/brcm80211

no such file or directory exists.

Yes, new to linux ubuntu.

can you write a script program that will do this update auto?
Make sure you're in your home folder when running "git clone git://...linux-next.git" and "git clone git://...linux-firmware.git". Otherwise /linux-next and /linux-fireware will not be created in your home directory where they're suppose to be. (in the terminal the ~ indicates your home directory)

Also did you read the note at the top of the guide, it may be useful: > **Axx83]At the moment the only commit version that compiles in 10.10 is this one:
[url]http://git.kernel.org/?p=linux/kerne...efe3b14 said:**
> 
Download the .tar.gz file in your home directory and extract it.
Now INSTEAD of "cd ~/linux-next/drivers/staging/brcm80211" you will do "cd ~/linux-next-a694cb1" and follow the rest of the guide strarting with "nano Makefile".

---

### Post by foxjazz on 2011-02-22
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /home/foxjazz/linux-next/drivers/staging/brcm80211/.tmp_versions ; rm -f /home/foxjazz/linux-next/drivers/staging/brcm80211/.tmp_version

---

### Post by Axx83 on 2011-02-23
> **some-one said:**
> The driver now is divided in two, brcm full mac and brcm soft mac. The first one doesn't compile, but the second one does.

For compile you have to download the driver from this link:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=52bac5bcaca7fa5372e02a74cf08e6e7f4d1e202;sf=tgz]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=snapshot;h=52bac5bcaca7fa5372e02a74cf08e6e7f4d1e202;sf=tgz")

You always can download the latest version browsing the git:
[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=history;f=drivers/staging/brcm80211;h=a3d70642687a4d8c4a1b0c21a5be0845a7bc0156;hb=HEAD")

Uncompress the file and then go to this folder:
```
cd linux-next-52bac5b/brcmsmac/
```

There is a Makefile in that folder, you have to add this lines:
```
KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS) -I$(SUBDIRS)/../include -I$(SUBDIRS)/../util -I$(SUBDIRS)/phy

default:
	echo $(PWD)
	$(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules
```

And then you have to erase some function calls to "no_printk", I don't know what are they for, but there are just for debugging (for the driver developers), you have to execute this command

```
sed -e 's/no_printk(.*)//' -i wl_dbg.h
```

Without that command the driver doesn't compile.

Then execute make and if there is no problem the driver compiles. One more thing, now the output file is named brcmsmac.ko

you can renamed it
```
mv brcmsmac.ko brcm80211.ko
```

And then do the things from the guide.

I tried your guide and this is so far the only driver, newer than the one still on my guide that compiles and install correctly.

Unfortunately as I can see neither the speed nor stability has gotten any better, I think there's no need to update the guide right now

---

### Post by ramakrishna.hcu.mtech on 2011-02-24
sir;

 Internet connection is not detecting in the ubuntu on dell inspiron laptop, but internet is perfectly coming in other os i.e . windows xp. till today also internet came in ubuntu but due to installation of some package alsa driver for sound one file is modified i guess. so can u please help me 

while installing i modified the resulted file

sudo nano /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=dell-m6 is added in the resulted file
 

and asked to save , i saved 

after rebooting the system. internet is not coming in ubuntu, fortunately sound through headphone problem is solved.

please help me as soon as possible

---

### Post by some-one on 2011-02-24
> **Axx83 said:**
> I tried your guide and this is so far the only driver, newer than the one still on my guide that compiles and install correctly.

Unfortunately as I can see neither the speed nor stability has gotten any better, I think there's no need to update the guide right now

Yes, the latest commits are just code cleanup, there is nothing new.

---

### Post by febelus on 2011-02-26
hi all, i've installed it on my macbook air 11" with broadcom bcm43224. After installation my network manager recognize wifi card and scan for all ap on the zone, but when i try to connect to my ap (wpa password) doesn't connect and request me the password.

---

### Post by bradmurmz on 2011-02-26
> **febelus said:**
> hi all, i've installed it on my macbook air 11" with broadcom bcm43224. After installation my network manager recognize wifi card and scan for all ap on the zone, but when i try to connect to my ap (wpa password) doesn't connect and request me the password.


The driver seems to be working great on my macbook air 11"

Actually seems to be more stable and faster than the proprietary wl driver!

I actually updated my kernel to 2.6.37 if this helps at all?

---

### Post by bradmurmz on 2011-02-26
Found a much better solution to this!!

Just update your kernel to 2.6.37 like this ::
[http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/) 


Then just install this nice firmware dpkg ::
[http://packages.debian.org/unstable/kernel/firmware-brcm80211](http://packages.debian.org/unstable/kernel/firmware-brcm80211)


UPDATE ::
Maybe its not as stable as I would have hoped. :(  Who do I got to donate to in order to get some movement on this driver? I really need it to be stable if I want to use linux on my macbook air primarily for work.

---

### Post by bradmurmz on 2011-02-27
According to this [https://bugs.archlinux.org/task/22714](https://bugs.archlinux.org/task/22714)

the bugs have been worked out in the new version of the driver inside 2.6.38-rc5+

I have to say that after the update to this kernel things are MUCH more stable however I was still able to reproduce the bug by threading a lot of http requests at once... 

If anyone trys this, please let me know how it worked for you and what firmware your using?

Thanks!

---

### Post by abettik on 2011-02-28
Hi guys,

thanks for this thread, hope it will help but yet, I'm still stuck to

```
sudo insmod /lib/modules/`uname -r`/brcm80211.ko
insmod: error inserting '/lib/modules/2.6.35-25-generic/brcm80211.ko': -1 Invalid parameters
```

any ideas ?
thanks

my config is the following

```
ubuntu 10.10

uname -r 
2.6.35-25-generic

 lspci -nn | grep -i net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
```

I followed the step in the first step, including the update of 07/01/01

make step is ok

modeprobe is almost ok

```
sudo modprobe mac80211
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

```

but insmod failed as said on the top

(sorry for the eventual wrong tag, I'm a newbie on forums)

---

### Post by Axx83 on 2011-02-28
put here the list of the files you find in the brcm80211 directory AFTER you have completed make command

---

### Post by abettik on 2011-03-01
Here are the list of the main folder and subfolders

l```
s -ltrh
total 1,6M
-rw-r--r-- 1 julie julie 1,6K 2011-02-28 20:33 TODO
-rw-r--r-- 1 julie julie 3,0K 2011-02-28 20:33 README
-rw-r--r-- 1 julie julie  996 2011-02-28 20:33 Kconfig
drwxr-xr-x 3 julie julie 4,0K 2011-02-28 20:33 include
drwxr-xr-x 2 julie julie 4,0K 2011-02-28 20:33 brcmfmac
-rw-r--r-- 1 julie julie 2,2K 2011-02-28 20:55 Makefile
drwxr-xr-x 2 julie julie 4,0K 2011-02-28 20:56 phy
drwxr-xr-x 2 julie julie 4,0K 2011-02-28 20:57 sys
drwxr-xr-x 3 julie julie 4,0K 2011-02-28 20:57 util
-rw-r--r-- 1 julie julie 768K 2011-02-28 20:57 brcm80211.o
-rw-r--r-- 1 julie julie   42 2011-02-28 20:57 modules.order
-rw-r--r-- 1 julie julie    0 2011-02-28 20:57 Module.symvers
-rw-r--r-- 1 julie julie 3,7K 2011-02-28 20:57 brcm80211.mod.c
-rw-r--r-- 1 julie julie 7,2K 2011-02-28 20:57 brcm80211.mod.o
-rw-r--r-- 1 julie julie 775K 2011-02-28 20:57 brcm80211.ko

ls -lhtr phy/
total 1,9M
-rw-r--r-- 1 julie julie 1,7K 2011-02-28 20:33 wlc_phytbl_n.h
-rw-r--r-- 1 julie julie 132K 2011-02-28 20:33 wlc_phytbl_n.c
-rw-r--r-- 1 julie julie 2,1K 2011-02-28 20:33 wlc_phytbl_lcn.h
-rw-r--r-- 1 julie julie  45K 2011-02-28 20:33 wlc_phytbl_lcn.c
-rw-r--r-- 1 julie julie 5,7K 2011-02-28 20:33 wlc_phyreg_n.h
-rw-r--r-- 1 julie julie  74K 2011-02-28 20:33 wlc_phy_radio.h
-rw-r--r-- 1 julie julie 929K 2011-02-28 20:33 wlc_phy_n.c
-rw-r--r-- 1 julie julie 3,2K 2011-02-28 20:33 wlc_phy_lcn.h
-rw-r--r-- 1 julie julie 131K 2011-02-28 20:33 wlc_phy_lcn.c
-rw-r--r-- 1 julie julie  33K 2011-02-28 20:33 wlc_phy_int.h
-rw-r--r-- 1 julie julie 8,5K 2011-02-28 20:33 wlc_phy_hal.h
-rw-r--r-- 1 julie julie  77K 2011-02-28 20:33 wlc_phy_cmn.c
-rw-r--r-- 1 julie julie 1,1K 2011-02-28 20:33 phy_version.h
-rw-r--r-- 1 julie julie  35K 2011-02-28 20:56 wlc_phy_cmn.o
-rw-r--r-- 1 julie julie  53K 2011-02-28 20:56 wlc_phy_lcn.o
-rw-r--r-- 1 julie julie 300K 2011-02-28 20:56 wlc_phy_n.o
-rw-r--r-- 1 julie julie  14K 2011-02-28 20:56 wlc_phytbl_lcn.o
-rw-r--r-- 1 julie julie  41K 2011-02-28 20:56 wlc_phytbl_n.o


julie@julie-1215N:~/brcm80211$ ls -lhtr sys/
total 992K
-rw-r--r-- 1 julie julie 3,2K 2011-02-28 20:33 wl_ucode_loader.c
-rw-r--r-- 1 julie julie 1,8K 2011-02-28 20:33 wl_ucode.h
-rw-r--r-- 1 julie julie 3,8K 2011-02-28 20:33 wl_mac80211.h
-rw-r--r-- 1 julie julie  45K 2011-02-28 20:33 wl_mac80211.c
-rw-r--r-- 1 julie julie 2,7K 2011-02-28 20:33 wl_export.h
-rw-r--r-- 1 julie julie 3,4K 2011-02-28 20:33 wl_dbg.h
-rw-r--r-- 1 julie julie 1,1K 2011-02-28 20:33 wlc_types.h
-rw-r--r-- 1 julie julie 2,0K 2011-02-28 20:33 wlc_stf.h
-rw-r--r-- 1 julie julie  18K 2011-02-28 20:33 wlc_stf.c
-rw-r--r-- 1 julie julie 3,4K 2011-02-28 20:33 wlc_scb.h
-rw-r--r-- 1 julie julie 8,2K 2011-02-28 20:33 wlc_rate.h
-rw-r--r-- 1 julie julie  17K 2011-02-28 20:33 wlc_rate.c
-rw-r--r-- 1 julie julie  25K 2011-02-28 20:33 wlc_pub.h
-rw-r--r-- 1 julie julie 5,1K 2011-02-28 20:33 wlc_phy_shim.h
-rw-r--r-- 1 julie julie 6,2K 2011-02-28 20:33 wlc_phy_shim.c
-rw-r--r-- 1 julie julie  40K 2011-02-28 20:33 wlc_mac80211.h
-rw-r--r-- 1 julie julie 221K 2011-02-28 20:33 wlc_mac80211.c
-rw-r--r-- 1 julie julie 5,5K 2011-02-28 20:33 wlc_key.h
-rw-r--r-- 1 julie julie 2,2K 2011-02-28 20:33 wlc_event.h
-rw-r--r-- 1 julie julie 4,6K 2011-02-28 20:33 wlc_event.c
-rw-r--r-- 1 julie julie 6,3K 2011-02-28 20:33 wlc_channel.h
-rw-r--r-- 1 julie julie  46K 2011-02-28 20:33 wlc_channel.c
-rw-r--r-- 1 julie julie 9,8K 2011-02-28 20:33 wlc_cfg.h
-rw-r--r-- 1 julie julie 5,9K 2011-02-28 20:33 wlc_bsscfg.h
-rw-r--r-- 1 julie julie  11K 2011-02-28 20:33 wlc_bmac.h
-rw-r--r-- 1 julie julie 113K 2011-02-28 20:33 wlc_bmac.c
-rw-r--r-- 1 julie julie 1,4K 2011-02-28 20:33 wlc_antsel.h
-rw-r--r-- 1 julie julie  10K 2011-02-28 20:33 wlc_antsel.c
-rw-r--r-- 1 julie julie 1,7K 2011-02-28 20:33 wlc_ampdu.h
-rw-r--r-- 1 julie julie  39K 2011-02-28 20:33 wlc_ampdu.c
-rw-r--r-- 1 julie julie 1,2K 2011-02-28 20:33 wlc_alloc.h
-rw-r--r-- 1 julie julie 8,2K 2011-02-28 20:33 wlc_alloc.c
-rw-r--r-- 1 julie julie 1,2K 2011-02-28 20:33 d11ucode_ext.h
-rw-r--r-- 1 julie julie 3,6K 2011-02-28 20:56 wlc_alloc.o
-rw-r--r-- 1 julie julie 3,7K 2011-02-28 20:56 wlc_antsel.o
-rw-r--r-- 1 julie julie  14K 2011-02-28 20:56 wlc_channel.o
-rw-r--r-- 1 julie julie 4,1K 2011-02-28 20:56 wlc_event.o
-rw-r--r-- 1 julie julie  93K 2011-02-28 20:56 wlc_mac80211.o
-rw-r--r-- 1 julie julie 5,3K 2011-02-28 20:56 wlc_rate.o
-rw-r--r-- 1 julie julie 7,4K 2011-02-28 20:56 wlc_stf.o
-rw-r--r-- 1 julie julie  25K 2011-02-28 20:56 wl_mac80211.o
-rw-r--r-- 1 julie julie  16K 2011-02-28 20:56 wlc_ampdu.o
-rw-r--r-- 1 julie julie  48K 2011-02-28 20:57 wlc_bmac.o
-rw-r--r-- 1 julie julie 5,4K 2011-02-28 20:57 wlc_phy_shim.o
-rw-r--r-- 1 julie julie 2,5K 2011-02-28 20:57 wl_ucode_loader.o


julie@julie-1215N:~/brcm80211$ ls -lhtr util/
total 576K
-rw-r--r-- 1 julie julie 1,4K 2011-02-28 20:33 siutils_priv.h
-rw-r--r-- 1 julie julie  48K 2011-02-28 20:33 siutils.c
-rw-r--r-- 1 julie julie  15K 2011-02-28 20:33 sbutils.c
-rw-r--r-- 1 julie julie  19K 2011-02-28 20:33 qmath.c
-rw-r--r-- 1 julie julie  22K 2011-02-28 20:33 nicpci.c
-rw-r--r-- 1 julie julie 5,2K 2011-02-28 20:33 linux_osl.c
-rw-r--r-- 1 julie julie  75K 2011-02-28 20:33 hndpmu.c
-rw-r--r-- 1 julie julie  71K 2011-02-28 20:33 hnddma.c
-rw-r--r-- 1 julie julie 6,1K 2011-02-28 20:33 bcmwifi.c
-rw-r--r-- 1 julie julie  27K 2011-02-28 20:33 bcmutils.c
-rw-r--r-- 1 julie julie  51K 2011-02-28 20:33 bcmsrom.c
-rw-r--r-- 1 julie julie  22K 2011-02-28 20:33 bcmotp.c
-rw-r--r-- 1 julie julie  17K 2011-02-28 20:33 aiutils.c
-rw-r--r-- 1 julie julie  19K 2011-02-28 20:56 siutils.o
-rw-r--r-- 1 julie julie 6,9K 2011-02-28 20:56 aiutils.o
-rw-r--r-- 1 julie julie 8,1K 2011-02-28 20:56 bcmotp.o
-rw-r--r-- 1 julie julie  35K 2011-02-28 20:56 bcmsrom.o
-rw-r--r-- 1 julie julie  12K 2011-02-28 20:56 bcmutils.o
-rw-r--r-- 1 julie julie 1,7K 2011-02-28 20:56 bcmwifi.o
-rw-r--r-- 1 julie julie  25K 2011-02-28 20:56 hndpmu.o
-rw-r--r-- 1 julie julie 4,8K 2011-02-28 20:56 linux_osl.o
-rw-r--r-- 1 julie julie  26K 2011-02-28 20:57 hnddma.o
-rw-r--r-- 1 julie julie 7,8K 2011-02-28 20:57 nicpci.o
drwxr-xr-x 2 julie julie 4,0K 2011-02-28 20:57 nvram
-rw-r--r-- 1 julie julie 5,3K 2011-02-28 20:57 qmath.o

```

---

### Post by börly molitor on 2011-03-01
Hi,

i hope anyone could help me.
I Add this code at the end of the makefile:

KDIR := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS)/include -I$(SUBDIRS)/sys -I$(SUBDIRS)/phy

default:
echo $(PWD)
$(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modu



If i compile the driver (make) i get a message see below, but the 'brcm80211.ko' file is missing???.

oot@bt:~/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211# make
echo /root/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211
/root/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211
make -C /lib/modules/2.6.35.8/build SUBDIRS=/root/linux-next-2d57aa7/linux-next-
2d57aa7/drivers/staging/brcm80211 CONFIG_BRCM80211_PCI=y V=1 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.35.8'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || ( \
echo; \
echo " ERROR: Kernel configuration is invalid."; \
echo " include/generated/autoconf.h or include/config/auto.conf are missing.";\
echo " Run 'make oldconfig && make prepare' on kernel src to fix it."; \
echo; \
/bin/false)
mkdir -p /root/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211/. tmp_versions ; rm -f /root/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging /brcm80211/.tmp_versions/*

WARNING: Symbol version dump /usr/src/linux-source-2.6.35.8/Module.symvers
is missing; modules will have no dependencies and modversions.

make -f scripts/Makefile.build obj=/root/linux-next-2d57aa7/linux-next-2d57aa7/d rivers/staging/brcm80211
(cat /dev/null; ) > /root/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/ brcm80211/modules.order
make -f /usr/src/linux-source-2.6.35.8/scripts/Makefile.modpost
scripts/mod/modpost -i /usr/src/linux-source-2.6.35.8/Module.symvers -I /roo t/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211/Module.symvers -o /root/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211/Modul e.symvers -S -w -s
make[1]: Leaving directory `/usr/src/linux-source-2.6.35.8'


root@bt:~/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211# ls -l
total 44
drwxrwxr-x 2 root root 4096 2011-02-23 22:08 brcmfmac
drwxrwxr-x 3 root root 4096 2011-02-23 22:08 brcmsmac
drwxrwxr-x 3 root root 4096 2011-02-23 22:08 include
-rw-rw-r-- 1 root root 1005 2011-02-23 22:08 Kconfig
-rw-rw-r-- 1 root root 1233 2011-02-26 22:39 Makefile
-rw-rw-r-- 1 root root 1252 2011-02-26 22:29 Makefile~
-rw-r--r-- 1 root root 810 2011-02-26 22:15 Makefile.patch
-rw-r--r-- 1 root root 0 2011-02-26 22:42 modules.order
-rw-r--r-- 1 root root 0 2011-02-26 22:00 Module.symvers
-rw-rw-r-- 1 root root 3008 2011-02-23 22:08 README
-rw-rw-r-- 1 root root 1629 2011-02-23 22:08 TODO
drwxrwxr-x 3 root root 4096 2011-02-23 22:08 util
root@bt:~/linux-next-2d57aa7/linux-next-2d57aa7/drivers/staging/brcm80211#


thanks
boerly

---

### Post by Joker5bb on 2011-03-17
the latest staging driver does not build brcm80211.ko

BCM43224 chipset needs the brcmsmac driver 

```
joker@joker-M15x:~$ modinfo brcmsmac
filename:       /lib/modules/2.6.35-27-generic/updates/drivers/staging/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     5D850F4300261D9555349E4
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,cfg80211
vermagic:       2.6.35-27-generic SMP mod_unload modversions
```

```
joker@joker-M15x:~$ iw list
Wiphy phy0
	Band 1:
		Capabilities: 0x4070
			HT20
			Static SM Power Save
			RX Greenfield
			RX HT20 SGI
			RX HT40 SGI
			No RX STBC
			Max AMSDU length: 3839 bytes
			No DSSS/CCK HT40
			40 MHz Intolerant
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 8 usec (0x06)
		HT TX/RX MCS rate indexes supported: 0-15
		Frequencies:
			* 2412 MHz [1] (19.0 dBm)
			* 2417 MHz [2] (19.0 dBm)
			* 2422 MHz [3] (19.0 dBm)
			* 2427 MHz [4] (19.0 dBm)
			* 2432 MHz [5] (19.0 dBm)
			* 2437 MHz [6] (19.0 dBm)
			* 2442 MHz [7] (19.0 dBm)
			* 2447 MHz [8] (19.0 dBm)
			* 2452 MHz [9] (19.0 dBm)
			* 2457 MHz [10] (19.0 dBm)
			* 2462 MHz [11] (19.0 dBm)
			* 2467 MHz [12] (disabled)
			* 2472 MHz [13] (disabled)
			* 2484 MHz [14] (disabled)
		Bitrates (non-HT):
			* 1.0 Mbps
			* 2.0 Mbps (short preamble supported)
			* 5.5 Mbps (short preamble supported)
			* 11.0 Mbps (short preamble supported)
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	Band 2:
		Capabilities: 0x4070
			HT20
			Static SM Power Save
			RX Greenfield
			RX HT20 SGI
			RX HT40 SGI
			No RX STBC
			Max AMSDU length: 3839 bytes
			No DSSS/CCK HT40
			40 MHz Intolerant
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 8 usec (0x06)
		HT TX/RX MCS rate indexes supported: 0-15
		Frequencies:
			* 5180 MHz [36] (17.0 dBm)
			* 5200 MHz [40] (17.0 dBm)
			* 5220 MHz [44] (17.0 dBm)
			* 5240 MHz [48] (17.0 dBm)
			* 5260 MHz [52] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5280 MHz [56] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5300 MHz [60] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5320 MHz [64] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5500 MHz [100] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5520 MHz [104] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5540 MHz [108] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5560 MHz [112] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5580 MHz [116] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5600 MHz [120] (disabled)
			* 5620 MHz [124] (disabled)
			* 5640 MHz [128] (disabled)
			* 5660 MHz [132] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5680 MHz [136] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5700 MHz [140] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5745 MHz [149] (21.0 dBm)
			* 5765 MHz [153] (21.0 dBm)
			* 5785 MHz [157] (21.0 dBm)
			* 5805 MHz [161] (21.0 dBm)
			* 5825 MHz [165] (21.0 dBm)
		Bitrates (non-HT):
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
	max # scan SSIDs: 4
	max scan IEs length: 2257 bytes
	Coverage class: 0 (up to 0m)
	Available Antennas: TX 0 RX 0
	Supported interface modes:
		 * managed
		 * monitor
	Supported commands:
		 * new_interface
		 * set_interface
		 * new_key
		 * new_beacon
		 * new_station
		 * new_mpath
		 * set_mesh_params
		 * set_bss
		 * authenticate
		 * associate
		 * deauthenticate
		 * disassociate
		 * join_ibss
		 * join_mesh
		 * remain_on_channel
		 * set_tx_bitrate_mask
		 * action
		 * frame_wait_cancel
		 * set_wiphy_netns
		 * set_channel
		 * set_wds_peer
		 * connect
		 * disconnect
	Supported TX frame types:
		 * IBSS: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
		 * managed: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
		 * AP: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
		 * AP/VLAN: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
		 * mesh point: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
		 * P2P-client: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
		 * P2P-GO: 0x0000 0x0010 0x0020 0x0030 0x0040 0x0050 0x0060 0x0070 0x0080 0x0090 0x00a0 0x00b0 0x00c0 0x00d0 0x00e0 0x00f0
	Supported RX frame types:
		 * IBSS: 0x00d0
		 * managed: 0x0040 0x00d0
		 * AP: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
		 * AP/VLAN: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0
		 * mesh point: 0x00d0
		 * P2P-client: 0x0040 0x00d0
		 * P2P-GO: 0x0000 0x0020 0x0040 0x00a0 0x00b0 0x00c0 0x00d0

```

---

### Post by alan-souza on 2011-04-15
This driver does not support ad-hoc mode? For when taking place in this way get an error saying it is not supported!

---

### Post by shiman6 on 2011-04-15
it seems the standard wl driver supports ad-hoc networks. And it seems to be doing fine on my system. no bad network connections, no slow network connections. Sadly my wifi card was shipped without a bluetooth chip. (BCM4313)

Edit to add: i found sometimes the wifi chip doesnt work after waking up from sleep mode, (windows and ubuntu) but when you restart the driver, it works again. Either disable then re-enable for windows users, or sudo rmmod wl then sudo modprobe wl, or whatever driver you use, for ubuntu.

---

### Post by alan-souza on 2011-04-15
The connection speed of this driver is exceeding the owner! The problem is that he is not supporting ad-hoc mode!

---

### Post by Robby123 on 2011-04-18
Hello Guys,

i have a problem with this guide and i hope someone can help me.

everytime when i run the insmod command my screen become completly black or white and the system dont react any more....

my system is ubuntu 10.10

you need more information about my system?

---

### Post by RocaHe on 2011-04-19
Driver BUG?!
 
My netbook is ASUS EeePC 1015PW with BCM4313 wireless card.
the OS  is Ubuntu10.10.
 
Brcm80211 Driver is working all right.
 
When running Aircrack-ng(1.1),Monitor mode can be activated an Injection is Working.
 
BUT,the netcard can only recognise the packets(or DATA) send or received by itself.
While other PCs are working via my wireless router,the netcard does find the router's ESSID and can receive the bacons,but data is always stay at 0.Also,the aircrack cannot find other wifi clients except itself.
 
 
SO,I just wordering whether it is a driver bug?

---

### Post by mohegan on 2011-04-19
How can I do with Natty ?  Any idea ?
The brcm80211 module is include in linux 2.6.38 but I want test the last version.

---

### Post by pikamoku on 2011-04-20
I've just installed latest Natty Beta and cant make work neither **brcm80211** nor official **sta** driver (on Lenovo b560, BCM4313 )

but doing:

```
sudo apt-get install b43-fwcutter 
```

made my day :D   

infrastucture works fine but ad-hoc mode doesnt work at least on the only one network I've tested. At least I can now connect to internet.


I'll wait untill official Natty release to test again brcm80211.
any idea would be wellcome. thanks

---

### Post by ephk on 2011-04-20
It seems there's a lot of people who can receive beacons but are unable to get any data packets. I did some research but i cant find anything. Im completely clueless, i dont know whether it's caused by the driver itself or some other configuration, or even the airodump application.

Im using a bcm4313, and i've followed this guide and then downloaded, patched and installed the compat-wireless.

Does anyone have more information regarding this problem?

---

### Post by meesha on 2011-04-22
Under Natty 11.04 :

                 1.Install the Non-free Broadcom STA Driver via 'Additional Software'

2.To check if my suggested solution will work for you, try to run the following command in terminal
```
sudo modprobe -r acer-wmi
```after that you should be able to connect to wireless lan (should work  for acer travelmate & lenovo ideapad with broadcom wireless adapters  )
 
3.If that worked out for you, the following procedure will resolve  the issue permanently with not working wireless/wlan broadcom adapters:
```
sudo gedit /etc/modprobe.d/blacklist.conf
``` in the blacklist.conf file add at the end this:
 blacklist acer-wmi
 
4.Reboot to check and you're done.


see also [https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/730972](https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/730972)

---

### Post by t0nj0uR5 on 2011-04-27
Updated firmware for [BCM4313, BCM43224, and BCM43225 chips]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commitdiff;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09"). Stability fix for packet injection. Give your feedback if it fully works. Thank you.

[http://git.kernel.org/?p=linux/kerne...74b29d2051dd09]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09")

---

### Post by t0nj0uR5 on 2011-04-27
Updated firmware for [BCM4313, BCM43224, and BCM43225 chips]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commitdiff;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09"). Stability fix for packet injection. Give your feedback if it fully works. Thank you.

[http://git.kernel.org/?p=linux/kerne...74b29d2051dd09]("http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09")

---

### Post by divyanshu308 on 2011-04-28
tried first but then it stuck so i force quitted it.
then tried again didnt work.
now it worked but then stopped in between and gave an error.


divyanshu@Inspiron-N5010:~$ sudo apt-get install build-essential git-core
[sudo] password for divyanshu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev git libalgorithm-diff-perl libalgorithm-merge-perl liberror-perl
Suggested packages:
  debian-keyring git-doc git-arch git-cvs git-svn git-email git-daemon-run
  git-gui gitk gitweb
The following NEW packages will be installed:
  build-essential dpkg-dev git git-core libalgorithm-diff-perl
  libalgorithm-merge-perl liberror-perl
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7,193kB of archives.
After this operation, 14.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package dpkg-dev.
(Reading database ... 162594 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.15.8.4ubuntu3.1_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5_amd64.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package git.
Unpacking git (from .../git_1%3a1.7.1-1.1ubuntu0.1_amd64.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.7.1-1.1ubuntu0.1_all.deb) ...
Selecting previously deselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-1_all.deb) ...
Selecting previously deselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-1_all.deb) ...
Processing triggers for man-db ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libdpkg-perl (1.15.8.4ubuntu3.1) ...
Setting up dpkg-dev (1.15.8.4ubuntu3.1) ...
Setting up build-essential (11.5) ...
Setting up liberror-perl (0.17-1) ...
Setting up git (1:1.7.1-1.1ubuntu0.1) ...
Setting up git-core (1:1.7.1-1.1ubuntu0.1) ...
Setting up libalgorithm-diff-perl (1.19.02-1) ...
Setting up libalgorithm-merge-perl (0.08-1) ...
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
divyanshu@Inspiron-N5010:~$ 
:confused:

---

### Post by Axx83 on 2011-04-29
new update

---

### Post by exo6 on 2011-05-25
When I got to the second line (cd ~/linux-firmware), it told me that no such file or directory exists .

sudo mkdir /lib/firmware/brcm
cd ~/linux-firmware
sudo cp brcm/bcm43xx* /lib/firmware/brcm
cd /lib/firmware/brcm
sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fw
sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw

By the way, I was following the original post with the "step-by-step" instructions .

---

### Post by exzR on 2011-05-31
hi! i have ubuntu 10.04 lts and cant upgrade distro because i use backbox...i have followed the tutorial but when i try to load

insmod /lib/firmware/'uname -r'/brcm80211 it says 

insmod: error inserting /lib/firmware/'uname -r'/brcm80211.ko; -1 File exist

and iwconfig says

no wireless extensions....


ps: modprobe mac80211 and brcm80211 work with out errors..

pps: with wl driver works but i need a driver that works with aircrack..

---

### Post by Joker5bb on 2011-05-31
I am using the new firmware with 2.6.39 kernel and I get no data in monitor mode. 
On my ubuntu 11.04 machine it will show no APs if the device interface is down, also crashes when I bring up the interface up

---

### Post by thewump on 2011-06-03
I've been using this driver for about 6 weeks.  Initially I was getting total system freezes frequently, but with latest firmware this is down to about once / day.

Is there any logging I can set to help debug this and report it back?

Thanks

K

---

### Post by Bob.Sponge on 2011-06-08
> **foxjazz said:**
> test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/foxjazz/linux-next/drivers/staging/brcm80211/.tmp_versions ; rm -f /home/foxjazz/linux-next/drivers/staging/brcm80211/.tmp_version

To my understanding this is not an error.
This is the comparison phrase.
Ignore it as long as the .ko file is generated.

---

### Post by Bob.Sponge on 2011-06-08
> **RocaHe said:**
> Driver BUG?!
 
My netbook is ASUS EeePC 1015PW with BCM4313 wireless card.
the OS  is Ubuntu10.10.
 
Brcm80211 Driver is working all right.
 
When running Aircrack-ng(1.1),Monitor mode can be activated an Injection is Working.
 
BUT,the netcard can only recognise the packets(or DATA) send or received by itself.
While other PCs are working via my wireless router,the netcard does find the router's ESSID and can receive the bacons,but data is always stay at 0.Also,the aircrack cannot find other wifi clients except itself.
 
 
SO,I just wordering whether it is a driver bug?

I think we have a similar issue:
My airodump-ng shows no networks at all.
If I create one using airbase-ng then it shows.

I have Broadcom BCM4313 [14e4:4727] (rev 01).

---

### Post by wyt168 on 2011-06-21
> **Axx83 said:**
> 
```
cd ~/linux-next/drivers/staging/brcm80211
nano Makefile
```Add this code at the end
```
KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS)/include -I$(SUBDIRS)/sys -I$(SUBDIRS)/phy

default:
    echo $(PWD)
    $(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules
```CTRL+X to exit and save

Compile the driver
```
make
```

I followed the instructions step by step, and modified the Makefile, as follows:
```
wyt168@ubuntu:~/linux-next/drivers/staging/brcm80211$ cat Makefile 
#
# Makefile fragment for Broadcom 802.11n Networking Device Driver
...
# common flags
subdir-ccflags-y                    := -DBCMDMA32
subdir-ccflags-$(CONFIG_BRCMDBG)    += -DBCMDBG -DBCMDBG_ASSERT

obj-$(CONFIG_BRCMUTIL)    += brcmutil/
obj-$(CONFIG_BRCMFMAC)    += brcmfmac/
obj-$(CONFIG_BRCMSMAC)    += brcmsmac/

# WYT110621:
# Added to build Broadcom wireless driver
KDIR    := /lib/modules/$(shell uname -r)/build
ccflags-y += -I$(SUBDIRS)/include -I$(SUBDIRS)/sys -I$(SUBDIRS)/phy

default:
    echo $(PWD)
    $(MAKE) -C $(KDIR) SUBDIRS=$(shell pwd) CONFIG_BRCM80211_PCI=y V=1 modules
# WYT110621_END

```However after running "make", nothing was built:
```
wyt168@ubuntu:~/linux-next/drivers/staging/brcm80211$ make
echo /home/wyt168/linux-next/drivers/staging/brcm80211
/home/wyt168/linux-next/drivers/staging/brcm80211
make -C /lib/modules/2.6.32-32-generic/build SUBDIRS=/home/wyt168/linux-next/drivers/staging/brcm80211 CONFIG_BRCM80211_PCI=y V=1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";    \
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;                                \
    /bin/false)
mkdir -p /home/wyt168/linux-next/drivers/staging/brcm80211/.tmp_versions ; rm -f /home/wyt168/linux-next/drivers/staging/brcm80211/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/wyt168/linux-next/drivers/staging/brcm80211
(cat /dev/null; ) > /home/wyt168/linux-next/drivers/staging/brcm80211/modules.order
make -f /usr/src/linux-headers-2.6.32-32-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-32-generic/Module.symvers -I /home/wyt168/linux-next/drivers/staging/brcm80211/Module.symvers  -o /home/wyt168/linux-next/drivers/staging/brcm80211/Module.symvers -S -w  -s
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'

wyt168@ubuntu:~/linux-next/drivers/staging/brcm80211$ ls
brcmfmac  brcmutil  Kconfig   modules.order   README
brcmsmac  include   Makefile  Module.symvers  TODO
```Anything I missed here?!

---

### Post by 0x00dec0de on 2011-06-24
[FONT=Arial][SIZE=3][COLOR=Red]It does not work, do not do so.

[/COLOR][/SIZE][/FONT] Dear Sirs,
I met a problem when using a BCM4313.
And looking for a solution. I several times caught this thread.
But after several attempts to adjust the efficiency of office equipment, I came across a kernel panic.
And so a solution was found with the release of kernel 3.0.0
Further, as I did.

Systems:
```

root@undefined:~# lspci |grep Network
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
root@undefined:~# uname -a
Linux undefined 2.6.32-5-amd64 #1 SMP Fri Jun 24 21:14:57 EEST 2011 x86_64 GNU/Linux

```Action:
```

apt-get install -y dpkg-dev devscripts build-essential git fakeroot kernel-package linux-headers-$(uname -r) 
cd /usr/src/[COLOR=#000000][FONT=Times New Roman][FONT=arial]
[FONT=Verdana][SIZE=2]# But you can see that I did not use the kernel which appeared.
# But you can not take a git repository.[/SIZE][/FONT]
[/FONT][/FONT][/COLOR] git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
ln -s linux-next linux
cd linux
cat /boot/config-$(uname -r) > .config
make oldconfig
make-kpkg --append-to-version "-tux" --revision "3.0.0" --us --uc --initrd kernel_image
dpkg -i ../linux-image-3.0.0-rc4-tux-next-20110624_3.0.0_amd64.deb
reboot

```Result:
```

root@undefined:~# lsmod  | grep brcm
brcmsmac              506199  0 
mac80211              172840  1 brcmsmac
brcmutil                5488  1 brcmsmac
cfg80211              124398  2 brcmsmac,mac80211

root@undefined:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```Good luck.

---

### Post by docblue on 2011-07-11
> **0x00dec0de said:**
> [FONT=Arial][SIZE=3][COLOR=Red]It does not work, do not do so.

[/COLOR][/SIZE][/FONT] Dear Sirs,
I met a problem when using a BCM4313.
And looking for a solution. I several times caught this thread.
But after several attempts to adjust the efficiency of office equipment, I came across a kernel panic.
And so a solution was found with the release of kernel 3.0.0
Further, as I did.

Systems:
```

root@undefined:~# lspci |grep Network
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
root@undefined:~# uname -a
Linux undefined 2.6.32-5-amd64 #1 SMP Fri Jun 24 21:14:57 EEST 2011 x86_64 GNU/Linux

```Action:
```

apt-get install -y dpkg-dev devscripts build-essential git fakeroot kernel-package linux-headers-$(uname -r) 
cd /usr/src/[COLOR=#000000][FONT=Times New Roman][FONT=arial]
[FONT=Verdana][SIZE=2]# But you can see that I did not use the kernel which appeared.
# But you can not take a git repository.[/SIZE][/FONT]
[/FONT][/FONT][/COLOR] git clone git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git
ln -s linux-next linux
cd linux
cat /boot/config-$(uname -r) > .config
make oldconfig
make-kpkg --append-to-version "-tux" --revision "3.0.0" --us --uc --initrd kernel_image
dpkg -i ../linux-image-3.0.0-rc4-tux-next-20110624_3.0.0_amd64.deb
reboot

```Result:
```

root@undefined:~# lsmod  | grep brcm
brcmsmac              506199  0 
mac80211              172840  1 brcmsmac
brcmutil                5488  1 brcmsmac
cfg80211              124398  2 brcmsmac,mac80211

root@undefined:~# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```Good luck.

THANK YOU! :) Works for me.
My laptop is an Dell Inspiron n4030 with BCM 4313.
=)

---

### Post by MisterOink on 2011-07-13
Hi all, I just got a new acer netbook today and was trying to figure out how to get the my bcm 4313 card to work better. I read the whole thread, and still haven't been able to find out how to add the kernel version into the makefile.

I typed uname and found my linux kernel is 2.6.35.8

What do I do from here? This is a whole new language for me?

---

### Post by x0x0x0h on 2011-07-16
> **ephk said:**
> It seems there's a lot of people who can receive beacons but are unable to get any data packets.

 Im using a bcm43225 on backtrack 5, and i have the same problem

---

### Post by File_ on 2011-07-27
Same problem here.
I can put my bcm4313 in monitor mode on Natty but I'm also getting no data.
Has anyone found a solution?

---

### Post by geekuillaume on 2011-07-27
Hi everyone !
I use BRCM80211 with Backtrack 5 and, like the others said, no data received... :(
I know it's not a priority for devs but it really be cool to add this function to the next release.
Thanks !

---

### Post by Mcjohnnson on 2011-07-27
I blacklisted it in favour of STA-driver. Couldn't get my WLAN work properly. I am waiting for UBuntu 11.10 and Kernel 3.0.

Everything is fine. But is was real hard to find a sollution. Wrote a [howto]("http://dickmcjohnnson.blogspot.com/2011/07/wifi-wlan-on-acer-travelmate-timeline-x.html").
Acer_wmi was giving me trouble, too.

---

### Post by marcio_mi on 2011-07-27
do you know if these drivers (both the free and proprietory one) support power management? 

this is my iwconfig output

```
wlan0     IEEE 802.11bgn  ESSID:"FASTWEB-1-55ls2qcCoLIk"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 64:87:D7:B9:98:38   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:100   Missed beacon:0

```

but if I try to set the power management on, it doesn't allow me

```
miccoli@netbook-N230:~$ iwconfig wlan0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not permitted.
miccoli@netbook-N230:~$ sudo iwconfig wlan0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

```

this happens both with the propriatory and free driver. Any idea?

---

### Post by .:astroboy:. on 2011-07-29
so we still don't have any solution on how to use bcm4313 chip set for cracking......

---

### Post by shiman6 on 2011-08-01
> **.:astroboy:. said:**
> so we still don't have any solution on how to use bcm4313 chip set for cracking......

funny thing, i have that same chipset on my laptop and the brcm80211 module worked out of the box. it works with aircrack-ng perfectly. It works better than the wl module most of the time in performance and response time.

---

### Post by geekuillaume on 2011-08-03
> **shiman6 said:**
> funny thing, i have that same chipset on my laptop and the brcm80211 module worked out of the box. it works with aircrack-ng perfectly. It works better than the wl module most of the time in performance and response time.

Which linux distro do you use ???

---

### Post by dbdexter on 2011-09-08
Hello everybody.
I have a eeepc 1215n with a bcm4313 card. I found a script that automatically patches the brcmsmac driver, and on ubuntu 11.04 works fine (no more -1 fixed channel, injection test passed), BUT when I try to inject, it just sends packets, and lost packets goes up until injection stops. Here's the script:

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-08-27.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-08-27.tar.bz2)
tar -jxf compat-wireless-2011-08-27.tar.bz2
cd compat-wireless-2011-08-27
wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
#Uncomment the line below to automatically reboot after the script ran.
#sudo reboot

let me know if works
):P
P.S. it's a bit slow when updating grub, just wait.

---

### Post by shadowlyx on 2011-09-23
Hi all,

Let me start by saying that the solution below applies to Lenovo laptops  that have hw switch with dual function - enable WLAN & BT. Please  also make sure you follow all the required steps in order to have the  proper wlan card driver installed.

I had the same wireless problem with bcm4313 and I spent days trying to fix it with no luck. Until last night.
This fix is for Lenovo laptops that have the hardware switch with dual function - enable/disable both wireless and bluetooth.

Before trying to make the linux driver work, you need turn the switch on  and the you MUST boot into windows (I know how it sound but it's not a  joke and I'm not advertising for the MS guys) and use the FN + F5  combination to open the software control and make sure that BOTH  wireless and bluetooth are "On". If at least one of them is OFF, the it  will never work in linux. The downside is for those that cannot  dual-boot because they only use Linux and don't have a Win OS installed.

You can easily check that in the linux terminal using "rfkill list all".  If the ideapad hw-swith is in the list and hard block is on then you  have the problem I mentioned above. It will not matter if you have the  correct driver installed or not. Just using "rfkill unblock all" will  unblock only the soft block, not the hard version.

For me it was a nightmare until I discovered this setting.
Long story short:
- make sure the hw switch is on
- boot into windows and use FN + F5 to enable WLAN & BT
- boot your linux OS, install the driver (if it's not already there) and  use "rfkill list all"; if your driver is correctly installed everything  should be OK
- make sure you defined a wireless connection in Network Manager
Now it should work.

I hope this will also help others like me that spent hours and days  trying to understand why to correct driver is working but wireless  network cannot be enabled.

Have a nice day.                &nbsp;):P

---

### Post by Dr.Aequitas on 2011-10-10
guys, i've read all the pages, all the instructions..
i have a very simple and important problem here..
none of the given kernel.org links are working.. so i am not able to download or clone -whatever you name it- anything to start with..
i did download kernel 3.1rc4, extract it on my desktop, browsed into linuxbla-bla/drivers/staging/brcm80211/
i made the change in the Makefile, run the make command, but all i got is this..
```
xxx@xxx-1015PEM:/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211$ make
echo /usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211
/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211
make -C /lib/modules/3.0.4-030004-generic/build SUBDIRS=/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211 CONFIG_BRCM80211_PCI=y V=1 modules
make[1]:`/usr/src/linux-headers-3.0.4-030004-generic' dizinine giriliyor
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (	\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/.tmp_versions ; rm -f /usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211
make -f scripts/Makefile.build obj=/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac
make[3]: *** Hedef `/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac/wl_cfg80211.o' i derlemek için  hiçbir kural yok, `/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac/brcmfmac.o' taraf&#305;ndan gereksinim duyuluyor. Durdu.
make[2]: *** [/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac] Hata 2
make[1]: *** [_module_/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211] Hata 2
make[1]: `/usr/src/linux-headers-3.0.4-030004-generic' dizininden ç&#305;k&#305;l&#305;yor
make: *** [default] Hata 2
xxx@xxx-1015PEM:/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211$
```
so i need some help over here..
if anyone using eeepc 1015PEM/PED/PE.. can share the brcm80211.ko file with me, it would be appreciated so much..
if noone using eeepc then anyone with a BCM4313 can share it too..
i'm stuck, and can not do anything..

---

### Post by Axx83 on 2011-10-10
The latest linux kernel ALREADY contains the brcm80211 driver and it works well. If you are running Ubuntu 11.04 then it's already functioning, if you are running previous version you could try updating the kernel with the kernel ppa, try googleing it

---

### Post by Dr.Aequitas on 2011-10-10
guys, i've read all the pages, all the instructions..
i have a very simple and important problem here..
none of the given kernel.org links are working.. so i am not able to download or clone -whatever you name it- anything to start with..
i did download kernel 3.1rc4, extract it on my desktop, browsed into linuxbla-bla/drivers/staging/brcm80211/
i made the change in the Makefile, run the make command, but all i got is this..
```
xxx@xxx-1015PEM:/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211$ make
echo /usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211
/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211
make -C /lib/modules/3.0.4-030004-generic/build SUBDIRS=/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211 CONFIG_BRCM80211_PCI=y V=1 modules
make[1]:`/usr/src/linux-headers-3.0.4-030004-generic' dizinine giriliyor
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (	\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/.tmp_versions ; rm -f /usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211
make -f scripts/Makefile.build obj=/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac
make[3]: *** Hedef `/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac/wl_cfg80211.o' i derlemek için  hiçbir kural yok, `/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac/brcmfmac.o' taraf&#305;ndan gereksinim duyuluyor. Durdu.
make[2]: *** [/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211/brcmfmac] Hata 2
make[1]: *** [_module_/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211] Hata 2
make[1]: `/usr/src/linux-headers-3.0.4-030004-generic' dizininden ç&#305;k&#305;l&#305;yor
make: *** [default] Hata 2
xxx@xxx-1015PEM:/usr/src/linux-headers-3.0.4-030004/drivers/staging/brcm80211$
```
so i need some help over here..
if anyone using eeepc 1015PEM/PED/PE.. can share the brcm80211.ko file with me, it would be appreciated so much..
if noone using eeepc then anyone with a BCM4313 can share it too..
i'm stuck, and can not do anything..

---

### Post by Dr.Aequitas on 2011-10-10
> **dbdexter said:**
> Hello everybody.
I have a eeepc 1215n with a bcm4313 card. I found a script that automatically patches the brcmsmac driver, and on ubuntu 11.04 works fine (no more -1 fixed channel, injection test passed), BUT when I try to inject, it just sends packets, and lost packets goes up until injection stops. Here's the script:

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-08-27.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-08-27.tar.bz2)
tar -jxf compat-wireless-2011-08-27.tar.bz2
cd compat-wireless-2011-08-27
wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
#Uncomment the line below to automatically reboot after the script ran.
#sudo reboot

let me know if works
):P
P.S. it's a bit slow when updating grub, just wait.

i did all the steps without any problem..
but i can not insert brcm80211 module.. it says:
```
xxx@xxx-1015PEM:~$ sudo modprobe brcm80211 
[sudo] password for xxx: 
FATAL: Could not read '/lib/modules/2.6.35-30-generic/brcm80211.ko': No such file or directory
xxx@xxx-1015PEM:~$
```

some info:
```
jockey-text -l
kmod:wl - Broadcom STA wireless driver (Sahipli, Etkisizle&#351;tirildi, Kullan&#305;mda de&#287;il) [auto-install]
kmod:bcma - Broadcom's specific AMBA driver (Özgür, Etkinle&#351;tirildi, Kullan&#305;mda)
kmod:brcmsmac - Broadcom 802.11n wireless LAN driver. (Özgür, Etkinle&#351;tirildi, Kullan&#305;mda)
```
```
iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

bnep0     no wireless extensions.
```
there's no eth1 which is the wireless interface..

---

### Post by File_ on 2011-10-10
> **Axx83 said:**
> The latest linux kernel ALREADY contains the brcm80211 driver and it works well. If you are running Ubuntu 11.04 then it's already functioning, if you are running previous version you could try updating the kernel with the kernel ppa, try googleing it
 
It is true that cards using brcm80211 drivers work properly with Ubuntu 11.04 but when you put card in monitor mode you don't recieve data. Or is it just me?

---

### Post by www.rzr.online.fr on 2011-10-13
what about support in oneric ?
-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

### Post by Lupius on 2011-10-16
> **File_ said:**
> It is true that cards using brcm80211 drivers work properly with Ubuntu 11.04 but when you put card in monitor mode you don't recieve data. Or is it just me?

The driver developers plan to start working on monitor mode support after the driver is in main line - which happened two days ago. I've been waiting for almost a year now. Few more months to go!

---

### Post by chaemil on 2011-11-15
will this work in oneiric?

---

### Post by san2244 on 2012-01-17
My laptop is Lenovo Ideapad Z570. I have newly installed Ubuntu 10.04 and the current kernel i have updated to 2.6.38. this is the first time i am using Linux. i am a beginner.The problem i face is that it does not show the wireless device at all in the network option. So from Broadcomm i downloaded the driver and installed it by following commands

# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz
#make
#modprobe lib80211
#insmod wl.ko

Then  the wireless was showing and it worked.But when i restart then it doesn't show again. and if i do the following commands it comes but only until next reboot.
#modprobe lib80211
#insmod wl.ko

Is there a way to solve my problem ???

---

### Post by beatmag on 2012-01-17
> **File_ said:**
> It is true that cards using brcm80211 drivers work properly with Ubuntu 11.04 but when you put card in monitor mode you don't recieve data. Or is it just me?

I've been trying the latest compat_wireless drivers , the bleeding does compile on 2.6 or 3.0 kernels (but complains of missing BCMA symbols or something, on loading). however the stable 3.2 and stable 2.6 compat_wireless does compile and work.

Even monitor mode works. However just the same as you.
When I monitor. Beacons come up, but Data never comes up for the Access Points.

I remember seeing clients being monitored and packets being monitored from clients, however still no Data comes up from Access Points.

Any fix for this yet?

I have also tried the latest Broadcoms STA drivers which has monitor mode, but it was very very unstable and flaky. I couldnt lock on a channel for monitoring and it kept crashing the whole system. But I was able to capture Data from Access Points!!!!!!!!!!!!!!

I've read some people who managed to capture Data in monitor mode........ how did you guys do it??????

---

### Post by ts3 on 2012-01-17
> **san2244 said:**
> My laptop is Lenovo Ideapad Z570. I have newly installed Ubuntu 10.04 and the current kernel i have updated to 2.6.38. this is the first time i am using Linux. i am a beginner.The problem i face is that it does not show the wireless device at all in the network option. So from Broadcomm i downloaded the driver and installed it by following commands

# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz
#make
#modprobe lib80211
#insmod wl.ko

Then  the wireless was showing and it worked.But when i restart then it doesn't show again. and if i do the following commands it comes but only until next reboot.
#modprobe lib80211
#insmod wl.ko

Is there a way to solve my problem ???

The instructions on the Broadcom website explain how to load permanently (pasted below):

[FONT="Courier New"]3: Setup to always load at boot time.

The procedure to make a module load at boot time varies from distro to
distro.  Consult the docs for your specific distro to see how.  The 
following seems to work for my setup on Fedora and Ubuntu.  Check your 
docs to see the procedure for your distro.

Follow these steps to have the driver load as part of the boot process:

# load driver as described above
# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless 
# depmod -a[/FONT]

The complete set of instructions are in the readme.txt file here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

[FONT="Courier New"]'uname -r'[/FONT] stands for your particular kernel version:
Use [FONT="Courier New"]uname -r[/FONT] to get the kernel version, note down carefully then use it in the above 'copy' ([FONT="Courier New"]cp[/FONT]) command.  You'll need to use sudo for [FONT="Courier New"]copy[/FONT] and [FONT="Courier New"]depmod[/FONT].

Cheers :)

---

### Post by abhijeet.1308 on 2012-01-20
i try to follow your instruction but i stuck in MakeFile

i get following error:[http://pastebin.com/WdxBwhrD](http://pastebin.com/WdxBwhrD)
  
if possible please help? 

i try to install this driver from 1 month please help
 i using kernel version 2.6.39.4 with kde 4

---

### Post by vishal1121 on 2013-04-27
heyy bro..
i've same BCM4313 card.. and i did it as u told..it's all hw nd soft ok but i dont know how to install the drivers for it..i m windows user and turned into ubuntu now..so m fresher in this os..can u tell me how to install its drivers nd yehhh dude u spend hours nd i spend 15-17 days nd finally found ur post nd it's very usefull for me..but plz help me to download the drivers..

---

### Post by Back Tracker on 2013-07-16
Sir,

i am totally New to Ubuntu OS... i followed each steps in post i really cant compile the driver.... Plz Plz help me with this and tell me a solution for this....

Millions Thanxs in advance...

---

### Post by pikamoku on 2013-07-17
what card do you have mate?

4313 work fine (on my lenovo b560) with wl driver from **software center** (official repositories). I didnt manually "compile" it

---

