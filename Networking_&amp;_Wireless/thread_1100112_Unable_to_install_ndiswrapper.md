---
title: "Unable to install ndiswrapper"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by _Zac_ on 2009-03-18
I'm following these set of instructions to get my Wireless card working:
```
If you're running a 32-bit OS, this method is deprecated. I recommend the native linux driver instead.



If you're running a 64-bit OS, use the method below.



Make sure you use the appropriate version of the drivers for your version of Linux. If you're using a 64-bit version of Linux, you must use 64-bit drivers. You can check this using the following command:

Code:



getconf LONG_BIT



I personally recommend using the wicd program for WiFi connectivity. It boasts built-in WPA support and has been successful where other network connection manager programs have failed.



This chipset showed up on my Acer Aspire 5050-3785. The lspci program spit out the following info:

Code:



Atheros Unknown device 001c (rev 01)



It also has been incorrectly labeled as an AR5006X device, in some cases.



Here is a step by step procedure to install the drivers manually (in case you don't want to use the script I wrote, or if it doesn't work properly). Open a terminal and copy/paste the following lines:



1a. Download the ndiswrapper source code and AR5007EG Windows drivers:

Code:



http://wifix.sourceforge.net/software.php?title=ndiswrapper



1b. Download the AR5007EG Windows XP drivers:

For 64-bits of blazing WiFi glory, use this:

Code:



wget http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz



2. Extract the archives:

Code:



tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz



3. Ensure you have your kernel headers and the build essential package.

Code:



sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential



4. Blacklist the ath_pci kernel module (it doesn't support our chipset).

Code:



echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist



5. Compile ndiswrapper:

Code:



pushd ndiswrapper-*/

sudo make uninstall

make

sudo make install

popd



6. Install the Windows drivers (using ndiswrapper):

Code:



pushd */ar5007eg/

sudo ndiswrapper -i net5211.inf

popd



7. Make sure ndiswrapper loads up every time we start Linux:

Code:



sudo modprobe ndiswrapper

echo "ndiswrapper" | sudo tee -a /etc/modules



8. Restart your computer.

Code:



sudo init 6


```
I've followed these instructions exactly and I'm having an error while installing ndiswrapper.

Here's the error message:```
zachary@zachary-laptop:~/ndiswrapper-1.51$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
zachary@zachary-laptop:~/ndiswrapper-1.51$ make
make -C driver
make[1]: Entering directory `/home/zachary/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/zachary/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/zachary/ndiswrapper-1.51/driver/built-in.o
  CC [M]  /home/zachary/ndiswrapper-1.51/driver/crt.o
  CC [M]  /home/zachary/ndiswrapper-1.51/driver/hal.o
  CC [M]  /home/zachary/ndiswrapper-1.51/driver/iw_ndis.o
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c: In function &#8216;ndis_translate_scan&#8217;:
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
make[3]: *** [/home/zachary/ndiswrapper-1.51/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/zachary/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/zachary/ndiswrapper-1.51/driver'
make: *** [all] Error 2
zachary@zachary-laptop:~/ndiswrapper-1.51$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
zachary@zachary-laptop:~/ndiswrapper-1.51$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
zachary@zachary-laptop:~/ndiswrapper-1.51$ make
make -C driver
make[1]: Entering directory `/home/zachary/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/zachary/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/zachary/ndiswrapper-1.51/driver/iw_ndis.o
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c: In function &#8216;ndis_translate_scan&#8217;:
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
make[3]: *** [/home/zachary/ndiswrapper-1.51/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/zachary/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/zachary/ndiswrapper-1.51/driver'
make: *** [all] Error 2
zachary@zachary-laptop:~/ndiswrapper-1.51$ sudo make install
make -C driver install
make[1]: Entering directory `/home/zachary/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/zachary/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/zachary/ndiswrapper-1.51/driver/iw_ndis.o
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c: In function &#8216;ndis_translate_scan&#8217;:
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
make[3]: *** [/home/zachary/ndiswrapper-1.51/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/zachary/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/zachary/ndiswrapper-1.51/driver'
make: *** [install] Error 2
zachary@zachary-laptop:~/ndiswrapper-1.51$ popd
~
zachary@zachary-laptop:~$ pushd */ar5007eg/
~/ar5007eg-64-0.2/ar5007eg ~
zachary@zachary-laptop:~/ar5007eg-64-0.2/ar5007eg$ sudo ndiswrapper -i net5211.inf
sudo: ndiswrapper: command not found
zachary@zachary-laptop:~/ar5007eg-64-0.2/ar5007eg$ popd
~
zachary@zachary-laptop:~$ pushd ndiswrapper-*/
~/ndiswrapper-1.51 ~
zachary@zachary-laptop:~/ndiswrapper-1.51$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
zachary@zachary-laptop:~/ndiswrapper-1.51$ make
make -C driver
make[1]: Entering directory `/home/zachary/ndiswrapper-1.51/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/zachary/ndiswrapper-1.51/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/zachary/ndiswrapper-1.51/driver/iw_ndis.o
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c: In function &#8216;ndis_translate_scan&#8217;:
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1039: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1049: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1055: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1066: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1081: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1095: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1106: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1122: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1133: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1139: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/zachary/ndiswrapper-1.51/driver/iw_ndis.c:1162: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
make[3]: *** [/home/zachary/ndiswrapper-1.51/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/zachary/ndiswrapper-1.51/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/zachary/ndiswrapper-1.51/driver'
make: *** [all] Error 2
```
Does anyone know what's wrong and how I can fix it?

I have Ubuntu 8.10 and I'm running on an HP Pavilion dv7.

---

