---
title: "Interesting wireless problem"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by unactiveaccount on 2010-07-24
[SIZE=3]I run the most updated Linux Mint distro which, according to a few people, is essentially a different looking Ubuntu. I recently got this Ralink USB Hi-Gain wireless N card (RT2870 chipset) and tried to get it to work with this OS. It doesn't work out of the box so I had to visit their website ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2))[/SIZE][SIZE=3] in hope of a linux supported driver. To both my surprise and delight, there actually was! So, along with that I found a post on this forum ([http://ubuntuforums.org/showthread.php?p=8847310](http://ubuntuforums.org/showthread.php?p=8847310)) about it and I followed MamaiaPapaia's long directions at about the middle of the page including the directions in the website link that he disclosed in his post.

I did everything and even installed the driver with no errors. For some reason, Linux recognizes its existence in lsusb but doesn't recognize the device as a wireless device according to iwconfig and ifconfig. Also, I didn't understand the directions that mama wrote:[/SIZE]

[SIZE=3]"[I]Be sure to add a USB_DEVICE line to the array in os/linux/usb_main_dev.c  with the hex id from the adapter (use 'lsusb | grep Hawking' to find  it... 0x0E66,0x0013 IIRC) so the driver will recognize the HWUN3"

[/I][/SIZE][SIZE=3]Also, I haven't used ndiswrapper with the .inf driver file to get this working. First of all, I'm not sure how to even obtain the .inf driver so perhaps someone could enlighten me on that. 

I don't have that much experience with linux. My knowledge extends to about the traversal and alteration of folders and files within the command prompt. I'd really, really, REALLY appreciate if someone could throughly help me out in solving this. Thank you!

**NOTE: The exact link for the Ralink linux driver: [/SIZE][RT2870USB(RT2870/RT2770)]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpBNUwyUnZkMjVzYjJGa05ETTVOalU0TXpVeU5pNWllakk5UFQweU1ERXdYekEzTURsZlVsUXlPRGN3WDB4cGJuVjRYMU5VUVY5Mk1pNDBMakF1TVM1MFlYST1D")
[SIZE=3][I] 
lsusb[/I] 
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 006 Device 002: ID 1241:1603 Belkin 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0644:0200 TEAC Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0e66:0013 Hawking rt2870 [Hawking Hi-Gain Wireless-N]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:cf:c3:04  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fecf:c304/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13953243 (13.9 MB)  TX bytes:1111090 (1.1 MB)
          Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4750 (4.7 KB)  TX bytes:4750 (4.7 KB)

```sudo make (in the linux driver folder)
```

make -C tools
make[1]: Entering directory `/home/alex/Desktop/ralink/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/alex/Desktop/ralink/tools'
/home/alex/Desktop/ralink/tools/bin2h
cp -f os/linux/Makefile.6 /home/alex/Desktop/ralink/os/linux/Makefile
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/alex/Desktop/ralink/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/alex/Desktop/ralink/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/alex/Desktop/ralink/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/alex/Desktop/ralink/os/linux/rt2870sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'

```sudo make install (within the same linux driver folder)
```

make -C /home/alex/Desktop/ralink/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/alex/Desktop/ralink/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/alex/Desktop/ralink/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-21-generic
make[1]: Leaving directory `/home/alex/Desktop/ralink/os/linux'

```[/SIZE]

---

### Post by bkratz on 2010-07-24
> **unactiveaccount said:**
> [SIZE=3]

I did everything and even installed the driver with no errors. For some reason, Linux recognizes its existence in lsusb but doesn't recognize the device as a wireless device according to iwconfig and ifconfig. Also, I didn't understand the directions that mama wrote:[/SIZE]

[SIZE=3]"[I]Be sure to add a USB_DEVICE line to the array in os/linux/usb_main_dev.c  with the hex id from the adapter (use 'lsusb | grep Hawking' to find  it... 0x0E66,0x0013 IIRC) so the driver will recognize the HWUN3"

[/code][/SIZE]

An explanation of that step exists in the link you provided. Copied here for convenience.
```

Kirk
August 17, 2009 at 06:25
@quakhu: My guess is that your device is not listed in the driver’s compatable list. Use a “lsusb” command to find out the USB ID of your device. it will be something like 0411,015d. Then check to see if, in the downloaded driver’s include directory, the rt2870sta.h file includes a line that reads USB_DEVICE(0×0411,0x015d), but with your USB codes. If not, add a line after all the others with your info. Then recompile and try inserting again. Now you should see the ra0.

```


He is saying you have to add the device ID to the file rt2870sta.h before you compile it.

---

### Post by KegHead on 2010-07-24
Hi!

contact chili555.

KegHead

---

### Post by unactiveaccount on 2010-07-24
[SIZE=3]> **bkratz said:**
> An explanation of that step exists in the link you provided. Copied here for convenience.
```

Kirk
August 17, 2009 at 06:25
@quakhu: My guess is that your device is not listed in the driver&#8217;s compatable list. Use a &#8220;lsusb&#8221; command to find out the USB ID of your device. it will be something like 0411,015d. Then check to see if, in the downloaded driver&#8217;s include directory, the rt2870sta.h file includes a line that reads USB_DEVICE(0×0411,0x015d), but with your USB codes. If not, add a line after all the others with your info. Then recompile and try inserting again. Now you should see the ra0.

```He is saying you have to add the device ID to the file rt2870sta.h before you compile it.

Thank you bkratz,

Well, I looked at the include directory but there was no rt2870sta.h file, however, there was a "rt2870.h" file in the /include/chip directory. It didn't have any "compatibility list" that I could see but I added the line "USB_DEVICE(0×0e66,0x0013)" at the end anyway... hoping for the best. Also, I created the file "rt2870.h" in the include directory with the only line being "USB_DEVICE(0x0e66, 0x0013)"

To my dismay "sudo make"  output this error: 
```

make -C tools
make[1]: Entering directory `/home/alex/Desktop/ralink/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/alex/Desktop/ralink/tools'
/home/alex/Desktop/ralink/tools/bin2h
cp -f os/linux/Makefile.6 /home/alex/Desktop/ralink/os/linux/Makefile
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/alex/Desktop/ralink/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/alex/Desktop/ralink/os/linux/../../common/crypt_md5.o
In file included from /home/alex/Desktop/ralink/include/rtmp_chip.h:47,
                 from /home/alex/Desktop/ralink/include/rt_config.h:75,
                 from /home/alex/Desktop/ralink/os/linux/../../common/crypt_md5.c:28:
/home/alex/Desktop/ralink/include/chip/rt2870.h:48: error: expected identifier or &#8216;(&#8217; before &#8216;.&#8217; token
/home/alex/Desktop/ralink/include/chip/rt2870.h:48: error: stray &#8216;\303&#8217; in program
/home/alex/Desktop/ralink/include/chip/rt2870.h:48: error: stray &#8216;\227&#8217; in program
In file included from /home/alex/Desktop/ralink/include/rt_config.h:75,
                 from /home/alex/Desktop/ralink/os/linux/../../common/crypt_md5.c:28:
/home/alex/Desktop/ralink/include/rtmp_chip.h:281: warning: data definition has no type or storage class
/home/alex/Desktop/ralink/include/rtmp_chip.h:281: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;MCU_LEDCS_STRUC&#8217;
/home/alex/Desktop/ralink/include/rtmp_chip.h:281: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;PMCU_LEDCS_STRUC&#8217;
In file included from /home/alex/Desktop/ralink/include/rt_config.h:99,
                 from /home/alex/Desktop/ralink/os/linux/../../common/crypt_md5.c:28:
/home/alex/Desktop/ralink/include/rtmp.h:2966: error: expected specifier-qualifier-list before &#8216;MCU_LEDCS_STRUC&#8217;
make[2]: *** [/home/alex/Desktop/ralink/os/linux/../../common/crypt_md5.o] Error 1
make[1]: *** [_module_/home/alex/Desktop/ralink/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [LINUX] Error 2

```[/SIZE]

---

### Post by chili555 on 2010-07-24
> I could see but I added the line "USB_DEVICE(0×0e66,0x0013)" at the end anyway... hoping for the best.Please remove it.```
Also, I created the file "rt2870.h" in the include directory with the only line being "USB_DEVICE(0x0e66, 0x0013)"
```Also remove it. Now please do:```
cd /home/alex/Desktop/ralink
```...or whatever the Ralink driver folder is...```
sudo su
make uninstall
make clean
gedit os/linux/usb_main_dev.c
```Use nano or vim or any other convenient text editor if you don't have gedit. You should see a list of device IDs in the file. At the end of the list, add:```
{USB_DEVICE(0x0E66,0x0013)}, /*Hawking 2870 */
```Proofread carefully, twice, and save and close gedit. Now do:```
make 
make install
modprobe rt2870sta
exit
```Now is it working?

If your Ralink driver file doesn't contain a directory called 'os' or you don't have usb_main_dev.c, please zip the file and post it here so we can examine it.

Please note you will be building this driver module against your current running kernel. When a new kernel or linux-image is included in updates, you will need to make clean, make and make install again from the correct driver directory.

---

### Post by unactiveaccount on 2010-07-24
[SIZE=3]Thank you chili! 

I did all that you said and had no difficulty except adding the USB_DEVICE line in the list of device id's. I looked very closely at the file and found no list of device id's however I did find a large "if/then" sequence that contained what seemed to be several hex numbers of different devices. If I'm right, I'm not exactly sure how to properly add the device id anyway. 

When the guy talked about an array or device id's, I think he literally meant an array lol... Anyway, I've zipped up the file and uploaded it as your directions said so I would very much appreciate further assistance. 
[/SIZE]

---

### Post by chili555 on 2010-07-24
Please follow my suggestions above, *except* do:```
gedit common/rtusb_dev_id.c
```You will see a whole lot of Hawking usb.ids listed and add the line I suggested in there. It will then read:> --- snip ---
{USB_DEVICE(0x15c5,0x0008)}, /* Amit */
	{USB_DEVICE(0x0E66,0x0001)}, /* Hawking */
	{USB_DEVICE(0x0E66,0x0003)}, /* Hawking */
        [COLOR="Blue"]{USB_DEVICE(0x0E66,0x0013)}, /* Hawking */[/COLOR]
	{USB_DEVICE(0x129B,0x1828)}, /* Siemens */
	{USB_DEVICE(0x157E,0x300E)},	/* U-Media */
--- snip ---I have colored the line you are adding but you should not do so in your file. Proofread carefully, save and proceed as above.

Note that the usb.id matches your device:> Bus 001 Device 003: ID [COLOR="Blue"]0e66:0013[/COLOR] Hawking rt2870 [Hawking Hi-Gain Wireless-N]


---

### Post by unactiveaccount on 2010-07-24
[SIZE=3]Thanks again chili,

I did exactly as you instructed (including installing) however both "iwconfig" and "ifconfig" do not yield any results pertaining to the USB (ra0). Ubuntu still doesn't recognize it as a wireless device. 

In one of the links I disclosed the author wrote: 
[/SIZE]```
[SIZE=3]
Last thing is to add this driver to /etc/modules so that it is loaded automatically every time the system is rebooted.[/SIZE]
 
[LIST]
[*][SIZE=3]Open the file with your favorite text editor, for example [GNU Emacs]("http://www.gnu.org/software/emacs/"):
emacs /etc/modules[/SIZE]
[*][SIZE=3]Add the following line:
rt2870sta[/SIZE]   [SIZE=3](others reported that they had only success by adding “alias ra0 rt2870sta“) [/SIZE]
[/LIST]
 [SIZE=3]6.) If you do not want to reboot your machine, you should execute the  following two lines with superuser privileges to load the driver and to  integrate it in your networking configuration:[/SIZE]
 
[LIST]
[*][SIZE=3]sudo modprobe rt2870sta[/SIZE]
[*][SIZE=3]sudo /etc/init.d/networking restart[/SIZE]
[/LIST]
 [SIZE=3]Now in my case with Kubuntu the [KNetworkManager]("http://en.opensuse.org/Projects/KNetworkManager") came up and listed me all available WLAN networks. Even without [wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant/") I was able to connect to my [WPA2]("http://en.wikipedia.org/wiki/Wpa2") encrypted network as KNetworkManager seems to have build-in WPA2 support.[/SIZE]

```[SIZE=3]I tried modifying the modules file to have both "rt2870sta" and "alias ra0 rt2870sta"with both not producing results. Any other ideas? [/SIZE]

---

### Post by chili555 on 2010-07-24
Please do and post:```
sudo modprobe rt2870sta
iwconfig
dmesg | grep 2870
```Thanks.

---

### Post by unactiveaccount on 2010-07-24
typing in those commands output this
```

alex@alex-desktop ~/Desktop $ sudo modprobe rt2870sta
alex@alex-desktop ~/Desktop $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

alex@alex-desktop ~/Desktop $ dmesg | grep 2870
[   11.406379] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.413272] usbcore: registered new interface driver rt2870
alex@alex-desktop ~/Desktop $ 

```

---

### Post by chili555 on 2010-07-24
> [   11.406379] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
From the timestamp, it looks like it loaded on boot. Please amend /etc/modules to reflect:```
rt2870sta
```Remove this line:```
alias ra0 rt2870sta
```Reboot and do:```
sudo modprobe rt2870sta
iwconfig
dmesg | grep 2870
modinfo rt2870sta | grep 0013
```Please don't make me resort to Plan B!

---

### Post by unactiveaccount on 2010-07-24
I hope plan B doesn't involve torching my system because it still didn't work! Here's the output:
**NOTE: I added a 'iwconfig' and 'ifconfig' command after what you told me to input just to see if it decided to appear. 
```

alex@alex-desktop ~/Desktop $ sudo modprobe rt2870sta
[sudo] password for alex: 
alex@alex-desktop ~/Desktop $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

alex@alex-desktop ~/Desktop $ dmesg | grep 2870
[   11.526254] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.533160] usbcore: registered new interface driver rt2870
alex@alex-desktop ~/Desktop $ modinfo rt2870sta | grep 0013
alex@alex-desktop ~/Desktop $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

alex@alex-desktop ~/Desktop $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:cf:c3:04  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fecf:c304/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115075 (115.0 KB)  TX bytes:37965 (37.9 KB)
          Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4906 (4.9 KB)  TX bytes:4906 (4.9 KB)

```Do you think I should just reinstall the whole OS but with Ubuntu this time? I hope Linux Mint isn't too far out from what Ubuntu is since, from what I understand, they're pretty much the same. Again, thanks a bunch for your time and effort chili. It's very much appreciated!

---

### Post by chili555 on 2010-07-24
```
alex@alex-desktop ~/Desktop $ modinfo rt2870sta | grep 0013
alex@alex-desktop ~/Desktop $
```Ouch! That means the amendment of the rtusb_dev_id.c file didn't take. Can you please look at the file and make sure your changes were saved? Please confirm that, after you did that change, you ran:```
sudo su
make uninstall
make clean
make 
make install
modprobe rt2870sta
exit
```If not, please do so.> I hope plan B doesn't involve torching my system Nope, not yet. We haven't had to torch one in a couple of weeks now. The smell of kerosene has just about all faded out now. (Yes, I live in a county where you can buy kerosene at the corner store, in case you hadn't paid tha 'lectrik.)> Do you think I should just reinstall the whole OS but with Ubuntu this time?Nope, I have a laptop with Mint and I like it, too.

---

### Post by unactiveaccount on 2010-07-24
Damn, it still didn't work! I followed all your instructions carefully, including the amendments that had to be performed to the rtusb_dev_id.c file. I opened it back up to make sure I actually saved it and--bam!--it was actually still there. I saved it again anyway, uninstalled/reinstalled then modprobed it. Still nothing... I have no idea why the modinfo , apparently, relayed back with no changes. Why won't this just work!? 

so unless you've got something else up your sleeve, what's plan B Mr. Bond? 

Again, thank you : )

---

### Post by David006 on 2010-07-24
@chili555

Also figuring out issues with Ubuntu 10.04 (Lucid) and D-Link DWA-125 (N 150) / rt3070/rt2879.

I've got this to work, but know the method is slightly wrong.  This is only FYI (or to help others), as I can live with my method.

====
---------------------------------------
D-Link DWA-125 ('WIRELESS [N] 150 USB ADAPTER')

[http://ubuntuforums.org/showthread.php?t=1434630](http://ubuntuforums.org/showthread.php?t=1434630)
[http://ubuntuforums.org/showthread.php?p=9512177#post9512177](http://ubuntuforums.org/showthread.php?p=9512177#post9512177)

[http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37](http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37)
[http://www.uluga.ubuntuforums.org/showthread.php?t=1425564&page=8](http://www.uluga.ubuntuforums.org/showthread.php?t=1425564&page=8)

[http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved-3.html](http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved-3.html)

----

(device connected)

  lsusb
--output
  :
Bus 0nn Device 0nn: ID 07d1:3c0d D-Link System 
--

  iwconfig
--output
lo        no wireless extensions.

eth1      no wireless extensions.
--

-----------------------------
## block conflicting driver(s)

  sudo gedit /etc/modprobe.d/blacklist.conf
--append
# D-Link DWA-125 (USB ID 07d1:3c0d)
blacklist rt2800usb
--

-----------------------------
## Add identifier, to start driver

  sudo gedit /etc/udev/rules.d/network_drivers.rules
--add
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta"
--

-----------------------------
## Add alias for 'rt2870'

  sudo gedit /etc/modprobe.d/network_drivers.conf
--add
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id
--

-----------------------------
## start (manually)

??  sudo modprobe rt3070sta
  (can't find rt3070sta)

  sudo modprobe rt2870sta

  dmesg | grep -e rt2 -e rt3
--output
[   12.494224] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   12.525748] usbcore: registered new interface driver rt2870
--

-----------------------------
## auto start (and after boot or restart)

  sudo gedit /etc/udev/rules.d/10-wlan.rules
--add
# UDEV-Rule for D-Link DWA-125 ID 07d1:3c0d
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c0d", RUN+="/sbin/modprobe rt2870sta"
--

  sudo service udev reload

(OR restart)


  iwconfig
--output
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-81 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
--

(now able to use Network Connections (GUI) )

-----------------------------------------------------------
====

---

### Post by chili555 on 2010-07-25
> **unactiveaccount said:**
> Damn, it still didn't work! I followed all your instructions carefully, including the amendments that had to be performed to the rtusb_dev_id.c file. I opened it back up to make sure I actually saved it and--bam!--it was actually still there. I saved it again anyway, uninstalled/reinstalled then modprobed it. Still nothing... I have no idea why the modinfo , apparently, relayed back with no changes. Why won't this just work!? 

so unless you've got something else up your sleeve, what's plan B Mr. Bond? 

Again, thank you : )Please remove the device from the USB slot. Next, we are going to uninstall the driver you downloaded:```
cd /home/alex/Desktop/ralink
sudo su
make uninstall
exit

```Now, we are going to create two files. ```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```As before, use nano or vim or any convenient text editor. Add a single line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0e66", ATTR{idProduct}=="0013", RUN+="/sbin/modprobe -qba rt2870sta"
```Proofread carefully, save and close gedit. Now, do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add a single line:```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0e66 0013" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread carefully, save and close gedit. Now reinsert the device. Does it work now? If not, post:```
dmesg | grep 2870
```

---

### Post by unactiveaccount on 2010-07-25
YES!!!!! It worked after that!!! You're the man chili. Thanks a whole lot! 

This was a great learning experience and I'm sure I wont be the last to benefit from this. SWEET.

---

### Post by chili555 on 2010-07-25
Glad it's working! Have fun with Mint.

---

