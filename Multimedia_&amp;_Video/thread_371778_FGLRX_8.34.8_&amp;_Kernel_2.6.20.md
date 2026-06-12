---
title: "FGLRX 8.34.8 &amp; Kernel 2.6.20"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by dantum on 2007-02-27
Just managed to install the latest drivers from ATI. 8.34.8 with my custom 2.6.20 kernel on hp nx6125 with express M200 card.

Here is what i did.


Get the patch from:

mkdir 8.34

wget [http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.34.8-for-2.6.20.patch](http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.34.8-for-2.6.20.patch)

*get driver from ati site.*

sh ati-driver-installer-8.34.8-x86.x86_64.run --extract my_folder_name

*go into* " my_folder_name/common/lib/modules/fglrx/build_mod "

patch -p0 < /<patch location>/fglrx-8.34.8-for-2.6.20.patch 

get to back to root of 8.34 folder 

*go into my_folder_name*

*create ubuntu specific files.*

sudo sh ati-installer.sh 8.34.8 --buildpkg Ubuntu/edgy

install the packages 

sudo dpkg -i xorg-driver-fglrx_8.34.8-1*.deb
sudo dpkg -i fglrx-kernel-source_8.34.8-1*.deb
sudo dpkg -i fglrx-control_8.34.8-1*.deb

*remove old junk if present*

sudo rm /usr/src/fglrx-kernel*.deb

Install the kernel module

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

REBOOT.

Hope this helps. From what i heard the next version of ATI drivers is out on 14th of march and will include the 2.6.20 kernel support. So patching won't be needed.

Sorry for my rather basic tutorial and I hope everyone understands it.


Info Sources used:
[http://www.linuxespanol.com/ftopic17881.php](http://www.linuxespanol.com/ftopic17881.php)
[http://ati.cchtml.com/show_bug.cgi?id=566](http://ati.cchtml.com/show_bug.cgi?id=566)
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

