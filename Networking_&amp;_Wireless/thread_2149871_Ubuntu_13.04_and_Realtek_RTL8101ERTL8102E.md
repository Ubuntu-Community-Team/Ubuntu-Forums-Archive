---
title: "Ubuntu 13.04 and Realtek RTL8101E/RTL8102E"
date: 2013-05-30
forum: Networking &amp; Wireless
---

### Post by vamsiampolu on 2013-05-30
Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

Steps I followed:

    sudo gedit  /etc/modprobe.d/blacklist.conf

    Add line:

    Code:

    blacklist r8169

    Save and close, then run:

    Code:

    sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.022.00.tar.bz2 && cd r8101-1.022.00 && sudo sh autorun.sh

    After completion of this command, reboot and you're good to go!

    Happy days 

Attached Files Attached Files

    File Type: bz2 r8101-1.022.00.tar.bz2 (41.5 KB, 366 views)

What I ended up getting:

sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.022.00.tar.bz2 && cd r8101-1.022.00 && sudo sh autorun.sh

update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
r8101-1.022.00/
r8101-1.022.00/src/
r8101-1.022.00/src/r8101.h
r8101-1.022.00/src/r8101_n.c
r8101-1.022.00/src/rtl_eeprom.c
r8101-1.022.00/src/rtltool.c
r8101-1.022.00/src/rtltool.h
r8101-1.022.00/src/rtl_eeprom.h
r8101-1.022.00/src/Makefile_linux24x
r8101-1.022.00/src/rtl_ethtool.h
r8101-1.022.00/src/Makefile
r8101-1.022.00/readme
r8101-1.022.00/autorun.sh
r8101-1.022.00/Makefile

Check old driver and unload it.
Build the module and install
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5396:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_init_board&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5799:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_init_one&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5926:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_remove_one&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7851:12: error: &#8216;rtl8101_init_one&#8217; undeclared here (not in a function)
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7852:2: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7852:25: error: &#8216;rtl8101_remove_one&#8217; undeclared here (not in a function)
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7488:12: warning: &#8216;rtl8101_poll&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:869:1: warning: &#8216;rtl8101_xmii_reset_pending&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:885:1: warning: &#8216;rtl8101_xmii_link_ok&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:894:1: warning: &#8216;rtl8101_xmii_reset_enable&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1117:1: warning: &#8216;rtl8101_link_option&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1239:1: warning: &#8216;rtl8101_set_speed_xmii&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1565:1: warning: &#8216;rtl8101_gset_xmii&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1776:27: warning: &#8216;rtl8101_ethtool_ops&#8217; defined but not used [-Wunused-variable]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1811:13: warning: &#8216;rtl8101_get_mac_version&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1879:1: warning: &#8216;rtl8101_print_mac_version&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:4584:1: warning: &#8216;rtl8101_release_board&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5729:1: warning: &#8216;rtl8101_check_eeprom&#8217; defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[3]: *** [/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/vamsi/Downloads/r8101-1.022.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2

Rebooted the system...still no internet connection.
What d I do now?

---

### Post by vamsiampolu on 2013-05-30
I'm running Ubuntu 13.04
Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

    sudo gedit  /etc/modprobe.d/blacklist.conf

    Add line:

    Code:

    blacklist r8169

    Save and close, then run:

    Code:

    sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.022.00.tar.bz2 && cd r8101-1.022.00 && sudo sh autorun.sh

    After completion of this command, reboot and you're good to go!

    Happy days 

Attached Files Attached Files

    File Type: bz2 r8101-1.022.00.tar.bz2 (41.5 KB, 366 views)

sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.022.00.tar.bz2 && cd r8101-1.022.00 && sudo sh autorun.sh
[sudo] password for vamsi: 
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
r8101-1.022.00/
r8101-1.022.00/src/
r8101-1.022.00/src/r8101.h
r8101-1.022.00/src/r8101_n.c
r8101-1.022.00/src/rtl_eeprom.c
r8101-1.022.00/src/rtltool.c
r8101-1.022.00/src/rtltool.h
r8101-1.022.00/src/rtl_eeprom.h
r8101-1.022.00/src/Makefile_linux24x
r8101-1.022.00/src/rtl_ethtool.h
r8101-1.022.00/src/Makefile
r8101-1.022.00/readme
r8101-1.022.00/autorun.sh
r8101-1.022.00/Makefile

Check old driver and unload it.
Build the module and install
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5396:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_init_board&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5799:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_init_one&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5926:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_remove_one&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7851:12: error: &#8216;rtl8101_init_one&#8217; undeclared here (not in a function)
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7852:2: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7852:25: error: &#8216;rtl8101_remove_one&#8217; undeclared here (not in a function)
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7488:12: warning: &#8216;rtl8101_poll&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:869:1: warning: &#8216;rtl8101_xmii_reset_pending&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:885:1: warning: &#8216;rtl8101_xmii_link_ok&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:894:1: warning: &#8216;rtl8101_xmii_reset_enable&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1117:1: warning: &#8216;rtl8101_link_option&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1239:1: warning: &#8216;rtl8101_set_speed_xmii&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1565:1: warning: &#8216;rtl8101_gset_xmii&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1776:27: warning: &#8216;rtl8101_ethtool_ops&#8217; defined but not used [-Wunused-variable]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1811:13: warning: &#8216;rtl8101_get_mac_version&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1879:1: warning: &#8216;rtl8101_print_mac_version&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:4584:1: warning: &#8216;rtl8101_release_board&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5729:1: warning: &#8216;rtl8101_check_eeprom&#8217; defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[3]: *** [/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/vamsi/Downloads/r8101-1.022.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2

Restarted...no internet connection.
What do I do now?

---

### Post by coffeecat on 2013-05-30
@vamsiampolu, I've moved your posts into their own thread and given it a suitable title. The thread you posted to was for 12.04

---

### Post by vamsiampolu on 2013-05-30
@coffeecat,thank you...

I also tried running the  r8101-1.023.00,i get permission denied messages

---

### Post by mrwiggum on 2013-06-04
I'm having the same problem this worked in 12.04 but not in 13.04.

---

### Post by mrwiggum on 2013-06-04
I wonder if this is actually a difference in GCC from 4.6 to 4.7 I'm going to take a look at the offending lines of code tonight.

---

### Post by mrwiggum on 2013-06-04
OK I was wrong doesn't seem to have anything to do with gcc versions.  Now I think this has to do with __devinit, __devexit and __devexit_p.  I'm not sure what these do but I'm pretty sure from my early research they were removed in kernel 3.8.  Removing them from the r8101_n.c file seems to allow the driver to compile and load I didn't have time to test to see if it worked.  I'll have to look into what these defines did to make sure removing them won't create stability problems for the driver.

---

### Post by mrwiggum on 2013-06-05
Ok so yeah It looks like this has to do with removing the CONFIG_HOTPLUG option from the 3.8 kernel.
([https://patchwork.kernel.org/patch/1404661/](https://patchwork.kernel.org/patch/1404661/))
Since __devinit, __devexit, and __devexit_p are defined as nothing when CONFIG_HOTPLUG is y (the default option) ([http://www.spinics.net/lists/newbies/msg29197.html](http://www.spinics.net/lists/newbies/msg29197.html))
removing them should yield the same result. So to fix this issue just edit the r8101_n.c file and remove these macros then run the autorun.sh file and it should work correctly. It seems like this may cause the driver to take more memory (but not that much) under certain circumstances but it shouldn't affect it's functionality.  I don't do alot of driver or kernel development so if someone else comes across this and wants to correct me please feel free.

---

