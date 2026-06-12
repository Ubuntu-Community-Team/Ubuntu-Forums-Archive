---
title: "EUB9603 EXT. drivers on website as .rar..."
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by Stray Wolf on 2011-08-03
The link: [http://www.engeniustech.com.sg/node/276](http://www.engeniustech.com.sg/node/276).

So, I converted a friends laptop to Ubuntu and he wants to strengthen his wifi signal through this usb antenna-like device.  The site has linux drivers but since it's not a gdeb that has its own installer I don't know what to do with it.  Help me keep this guy with Ubuntu by taking care of this issue.  I just need to know how to where to  extract this .rar to so the device can use these drivers.

---

### Post by chili555 on 2011-08-03
If you installed the latest version, Natty 11.04, you can stick the device in the slot and, in a terminal, do:```
sudo modprobe r8712u
```You should be all set. If it doesn't go as smoothly as I suspect, post back with the result of:```
uname -r
lsusb
```Thanks.

---

### Post by Stray Wolf on 2011-08-04
@ chili->Thanks for your response.  It's much appreciated.  I must apologize for not being more specific.  The laptop is running Ubuntu 10.04 (LTS).  But your advice should translate.  His antenna is in the mail and I'm glad to have a solution to work with when it arrives.

---

### Post by chili555 on 2011-08-04
Well, I doubt r8712u is on 10.04 LTS. If you try the command and it says the module is not found or doesn't exist, then we'll proceed. Compiling this driver is not trivial, so let's be sure before we proceed. With the device in the USB slot, it ought to load the module automagically. If not, run and post:```
lsusb
```Thanks.

---

### Post by Stray Wolf on 2011-08-04
Awesome.  The man who I'm doing this for said his device should be delivered tomorrow.  You and people like you are why Ubuntu is awesome...just in case you don't hear it enough.

---

### Post by Stray Wolf on 2011-08-05
uname -r output:  2.6.32-33-generic

lsusb output:        Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1740:9603 Senao 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

If the link in my first post goes to the actual linux drivers I'd be glad to use it but I don't know how to install from .rar.  If I have to compile it or anything I'd be glad to repackage it as a .deb package and post it for others.  But this is what I've got so far.  Thanks for the help chili.

---

### Post by chili555 on 2011-08-05
Most of us won't need the .deb. The driver r8712u is included on the latest Ubuntu version and r8192s_usb on earlier versions. This might be your lucky day. Please insert the device and run:```
sudo modprobe r8192s_usb
```Is there any sign of activity from the device? There is sometimes a firmware issue; check with:```
dmesg | grep 819
```Compiling from source is always fun, but I think the Ubuntu developers beat us!

---

### Post by Stray Wolf on 2011-08-05
I did sudo modprobe r8192s_usb.  After pressing enter it just went to a new $ line.  Then I did dmesg:
dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91864 r8192 d22824 u2097152
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u2097152 alloc=1*2097152
[    0.000000] Memory: 2821576k/2881920k available (5412k kernel code, 416k absent, 59928k reserved, 2981k data, 888k init)
[   13.906696] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   13.928839] Linux kernel driver for RTL8192 based WLAN cards
[   14.196875] usbcore: registered new interface driver rtl819xU
[   14.725665] rtl819xU: --->FirmwareDownload92S()
[   14.725674] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.795674] rtl819xU:request firmware fail!
[   14.796697] rtl819xU:Firmware Download Fail!!a
[   14.808175] rtl819xU: --->FirmwareDownload92S()
[   14.808186] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.824315] rtl819xU:request firmware fail!
[   14.824750] rtl819xU:Firmware Download Fail!!a
[   14.824756] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   14.836929] rtl819xU: --->FirmwareDownload92S()
[   14.836939] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.840121] rtl819xU:request firmware fail!
[   14.840765] rtl819xU:Firmware Download Fail!!a
[   14.893232] rtl819xU: --->FirmwareDownload92S()
[   14.893241] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.897999] rtl819xU:request firmware fail!
[   14.898436] rtl819xU:Firmware Download Fail!!a
[   14.898443] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

---

### Post by chili555 on 2011-08-05
See post #15 here: [http://ubuntuforums.org/showthread.php?t=1468429&page=2](http://ubuntuforums.org/showthread.php?t=1468429&page=2)

The fix is the same except that step #3 should read:```
sudo mkdir /lib/firmware/RTL8192SU
```And step #4 should be:```
sudo cp rtl8192swf.bin /lib/firmware/RTL8192SU
```Please proceed and post back if you get stuck.

---

### Post by Stray Wolf on 2011-08-05
So, I downloaded the .rar from the site to my download folder, extracted it there.  Then I moved that folder (EUB9603H series linux driver) to the new folder I made in lib/firmware named RTL8192SU.  I don't see any .bin files in the folder.  Grep prints out the same result as before.  Though, the website says it's the linux drivers.  Should it have a .bin file in it?  So,  [http://www.engeniustech.com.sg/node/276](http://www.engeniustech.com.sg/node/276) - do you think it's legit? It says (on the left of the site) that it's linux drivers...

---

### Post by chili555 on 2011-08-05
Post #15 I linked above has the file you need attached. You don't need the EUB...rar file.> then I moved that folder (EUB9603H series linux driver) to the new folder I made in lib/firmware named RTL8192SU.Please remove the EUB9603H series linux driver from /lib/firmware/RTL8192SU.

---

### Post by Stray Wolf on 2011-08-05
Ok...my fault.  I should use the attached file in that thread.  On it now, I'll let you know how it comes out.

---

### Post by Stray Wolf on 2011-08-05
grep output:[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91864 r8192 d22824 u2097152
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u2097152 alloc=1*2097152
[    0.000000] Memory: 2821576k/2881920k available (5412k kernel code, 416k absent, 59928k reserved, 2981k data, 888k init)
[    0.398198] ACPI: Invalid active0 threshold
[   13.739285] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   13.759661] Linux kernel driver for RTL8192 based WLAN cards
[   13.989271] usbcore: registered new interface driver rtl819xU
[   14.151022] rtl819xU: --->FirmwareDownload92S()
[   14.151033] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.188418] rtl819xU:request firmware fail!
[   14.189483] rtl819xU:Firmware Download Fail!!a
[   14.200405] rtl819xU: --->FirmwareDownload92S()
[   14.200416] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.211033] rtl819xU:request firmware fail!
[   14.211476] rtl819xU:Firmware Download Fail!!a
[   14.211482] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   14.224530] rtl819xU: --->FirmwareDownload92S()
[   14.224540] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.231865] rtl819xU:request firmware fail!
[   14.232571] rtl819xU:Firmware Download Fail!!a
[   14.276668] rtl819xU: --->FirmwareDownload92S()
[   14.276679] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[   14.290143] rtl819xU:request firmware fail!
[   14.290481] rtl819xU:Firmware Download Fail!!a
[   14.290486] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 3338.870073] rtl819xU:=============>wlan driver to be removed
[ 3338.880846] rtl819xU:wlan driver removed
[ 3345.771739] rtl819xU: --->FirmwareDownload92S()
[ 3345.771758] usb 1-3: firmware: requesting RTL8192SU/rtl8192sfw.bin
[ 3345.784345] rtl819xU:signature:8192, version:902b, size:30, imemsize:7408, sram size:9688
[ 3345.784446] rtl819xU:--->FirmwareDownloadCode()
[ 3345.784528] rtl819xU:--->FirmwareCheckReady(): LoadStaus(1),
[ 3345.785508] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(1), rtStatus(0)
[ 3345.785517] rtl819xU:--->FirmwareDownloadCode()
[ 3345.785613] rtl819xU:--->FirmwareCheckReady(): LoadStaus(2),
[ 3345.788891] rtl819xU:-->FirmwareEnableCPU()
[ 3345.790975] rtl819xU:IMEM Ready after CPU has refilled.
[ 3345.790989] rtl819xU:<--FirmwareEnableCPU(): rtStatus(0x0)
[ 3345.790999] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(2), rtStatus(0)
[ 3345.791007] rtl819xU:--->FirmwareDownloadCode()
[ 3345.791023] rtl819xU:--->FirmwareCheckReady(): LoadStaus(3),
[ 3345.791286] rtl819xU:DMEM code download success, CPUStatus(0x3f)
[ 3345.792645] rtl819xU:Polling Load Firmware ready, CPUStatus(ff)
[ 3345.793608] rtl819xU:FirmwareCheckReady(): Current RCR settings(0x157e20e)
[ 3345.794057] rtl819xU:<---FirmwareCheckReady(): LoadFWStatus(3), rtStatus(0)
[ 3345.794065] rtl819xU:Firmware Download Success!!
[ 3357.070997] =====>rtl8192SU_link_change 1
[ 3357.072243] <=====rtl8192SU_link_change 2
[ 3357.113062] rtl819xU:==>SetBWModeCallback8192SUsbWorkItem()  Switch to 20MHz bandwidth
[ 3357.168261] rtl819xU:<==SetBWModeCallback8192SUsbWorkItem()
[ 3357.168301] =====>rtl8192SU_link_change 1
[ 3357.169510] <=====rtl8192SU_link_change 2
[ 3357.172571] rtl819xU:rtl8192_qos_association_resp: network->flags = 2,0
[ 3357.172611] rtl819xU:qos active process with associate response received
[ 3357.172653] =====>rtl8192SU_link_change 1
[ 3357.190376] <=====rtl8192SU_link_change 2
[ 3360.185127] rtl819xU:EnableHWSecurityConfig8192:, hwsec:1, pairwise_key:4, SECR_value:c
[ 3360.185420] rtl819xU:====>to setKey(), dev:ffff8800a00e0000, EntryNo:4, KeyIndex:0, KeyType:4, MacAddr00:30:0d:47:a4:f5
[ 3360.224178] rtl819xU:====>to setKey(), dev:ffff8800a00e0000, EntryNo:1, KeyIndex:1, KeyType:2, MacAddrff:ff:ff:ff:ff:ff
[ 3369.152990] =====>rtl8192SU_link_change 1
[ 3369.156766] <=====rtl8192SU_link_change 2
[ 3370.774919] =====>rtl8192SU_link_change 1
[ 3370.787161] <=====rtl8192SU_link_change 2
[ 3409.153388] =====>rtl8192SU_link_change 1
[ 3409.156814] <=====rtl8192SU_link_change 2

Also, the link light is flashing on the device.  It hasn't before.  Looks like your the man.  Thanks!

---

### Post by chili555 on 2011-08-05
Thanks! Would you please use thread tools at the top and Mark Solved?

---

### Post by Stray Wolf on 2011-08-10
I decided to reopen this thread.  I'd prefer to either compile the official drivers I have linked to in post #1 of this thread, or find drivers less than a year old.  The advice received so far has been helpful but I'd like to get this thing operating optimally.  Thanks in advance.

---

### Post by chili555 on 2011-08-10
If you are running Ubuntu 10.04 LTS, the drivers are only as old as your entire install; that is 1 1/3 years old. Frankly, you have no way that I can find, to determine the age of the driver in the file you downloaded. There is no evidence that a brand new driver will work better on your 1 1/3 year old kernel and gcc version than the driver it came with and a few reasons I can think of that it will not.

If you are determined to find out, please do:```
sudo apt-get install unrar build-essential linux-headers-generic
```Go to your downloads folder and right-click the .rar file and select Extract Here. Right-click the folder that is created and select Rename. Rename it to EUB9603H. Now, back to the terminal:```
cd Downloads/EUB9603H
make
sudo make install
```It builds a driver called 8712s. Remove the driver you have now temporarily:```
sudo rmmod -f r8192s_usb
```And load the new one:```
sudo modprobe 8712s
```If it is operating optimally, I will fall off my chair and we can blacklist r8192s_usb:```
sudo su
echo "blacklist r8192s_usb" >> /etc/modprobe.d/blacklist.conf
exit
```If you run into this little jewel, you will know the supplied driver is inadequate:> /home/chili/Desktop/Forum/StrayWolf/EUB9603H/os_intf/osdep_service.c: In function ‘_rtl_rwlock_init’:
/home/chili/Desktop/Forum/StrayWolf/EUB9603H/os_intf/osdep_service.c:306:2: error: [COLOR="Red"]implicit declaration of function ‘init_MUTEX’[/COLOR]
make[2]: *** [/home/chili/Desktop/Forum/StrayWolf/EUB9603H/os_intf/osdep_service.o] Error 1
make[1]: *** [_module_/home/chili/Desktop/Forum/StrayWolf/EUB9603H] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
[COLOR="Red"]make: *** [modules] Error 2[/COLOR]Good luck.

We can always try the compat-wireless suite.

---

### Post by Stray Wolf on 2011-08-10
I got as far as "sudo make install' and got this: ~/Downloads/EUB9603H$ sudo make install
[sudo] password for mike: 
Makefile:11: /config: No such file or directory
make: *** No rule to make target `/config'.  Stop.

If there is any more info I can give I'd be glad to provide it.

---

### Post by chili555 on 2011-08-10
Notice there isn't a README file to read to tell us what to do. We have to flail about and experiment. That's strike two. (The first is that you can't compile, at least no way I know of, a file with spaces in the name; hence the rename.)

Please try:```
cd Downloads/EUB9603H
```Unless, of course, you are already there.```
make clean
chmod +x config
make
sudo make install
```If that fails, you might also try:```
cd Downloads/EUB9603H
sudo su
make clean
make
make install
exit
```

---

### Post by Stray Wolf on 2011-08-10
> **chili555 said:**
> Notice there isn't a README file to read to tell us what to do. We have to flail about and experiment. That's strike two. (The first is that you can't compile, at least no way I know of, a file with spaces in the name; hence the rename.)

sudo make install[/CODE]If that fails, you might also try:```
cd Downloads/EUB9603H
sudo su
make clean
make
make install
exit
```

Done this so far...this is the only one that didn't get that error.  Here's the output: /home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c: In function ‘_init_recv_priv’:
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:102: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c: In function ‘sta2sta_data_frame’:
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:678: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:678: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:679: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:679: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:680: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:680: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c: In function ‘ap2sta_data_frame’:
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:824: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:824: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:825: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:825: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:826: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:826: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c: In function ‘validate_recv_data_frame’:
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1017: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1017: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1018: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1018: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c: In function ‘validate_recv_frame’:
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1161: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1161: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1162: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl871x_recv.c:1162: warning: cast to pointer from integer of different size
  CC [M]  /home/mike/Downloads/EUB9603H/recv/rtl8712_recv.o
In file included from /home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c:22:
/home/mike/Downloads/EUB9603H/include/osdep_service.h: In function ‘_init_timer’:
/home/mike/Downloads/EUB9603H/include/osdep_service.h:151: warning: cast from pointer to integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/rtl871x_ht.h:25,
                 from /home/mike/Downloads/EUB9603H/include/drv_types.h:67,
                 from /home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c:23:
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_da’:
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_sa’:
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_hdr_bssid’:
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast to pointer from integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/drv_types.h:73,
                 from /home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c:23:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c: In function ‘init_recv_priv’:
/home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c:68: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c:172: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c: In function ‘recvbuf2recvframe_u’:
/home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c:2514: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c: In function ‘recv_tasklet’:
/home/mike/Downloads/EUB9603H/recv/rtl8712_recv.c:2571: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/mike/Downloads/EUB9603H/rf/rtl871x_rf.o
In file included from /home/mike/Downloads/EUB9603H/rf/rtl871x_rf.c:23:
/home/mike/Downloads/EUB9603H/include/osdep_service.h: In function ‘_init_timer’:
/home/mike/Downloads/EUB9603H/include/osdep_service.h:151: warning: cast from pointer to integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/rtl871x_ht.h:25,
                 from /home/mike/Downloads/EUB9603H/include/drv_types.h:67,
                 from /home/mike/Downloads/EUB9603H/rf/rtl871x_rf.c:24:
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_da’:
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_sa’:
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_hdr_bssid’:
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast to pointer from integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/drv_types.h:73,
                 from /home/mike/Downloads/EUB9603H/rf/rtl871x_rf.c:24:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast to pointer from integer of different size
  CC [M]  /home/mike/Downloads/EUB9603H/rf/rtl8712_rf.o
In file included from /home/mike/Downloads/EUB9603H/rf/rtl8712_rf.c:23:
/home/mike/Downloads/EUB9603H/include/osdep_service.h: In function ‘_init_timer’:
/home/mike/Downloads/EUB9603H/include/osdep_service.h:151: warning: cast from pointer to integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/rtl871x_ht.h:25,
                 from /home/mike/Downloads/EUB9603H/include/drv_types.h:67,
                 from /home/mike/Downloads/EUB9603H/rf/rtl8712_rf.c:24:
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_da’:
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_sa’:
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_hdr_bssid’:
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast to pointer from integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/drv_types.h:73,
                 from /home/mike/Downloads/EUB9603H/rf/rtl8712_rf.c:24:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast to pointer from integer of different size
  CC [M]  /home/mike/Downloads/EUB9603H/sta_mgt/rtl871x_sta_mgt.o
In file included from /home/mike/Downloads/EUB9603H/sta_mgt/rtl871x_sta_mgt.c:23:
/home/mike/Downloads/EUB9603H/include/osdep_service.h: In function ‘_init_timer’:
/home/mike/Downloads/EUB9603H/include/osdep_service.h:151: warning: cast from pointer to integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/rtl871x_ht.h:25,
                 from /home/mike/Downloads/EUB9603H/include/drv_types.h:67,
                 from /home/mike/Downloads/EUB9603H/sta_mgt/rtl871x_sta_mgt.c:24:
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_da’:
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_sa’:
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_hdr_bssid’:
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast to pointer from integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/drv_types.h:73,
                 from /home/mike/Downloads/EUB9603H/sta_mgt/rtl871x_sta_mgt.c:24:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/sta_mgt/rtl871x_sta_mgt.c: In function ‘_init_sta_priv’:
/home/mike/Downloads/EUB9603H/sta_mgt/rtl871x_sta_mgt.c:82: warning: cast from pointer to integer of different size
  CC [M]  /home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.o
In file included from /home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:22:
/home/mike/Downloads/EUB9603H/include/osdep_service.h: In function ‘_init_timer’:
/home/mike/Downloads/EUB9603H/include/osdep_service.h:151: warning: cast from pointer to integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/rtl871x_ht.h:25,
                 from /home/mike/Downloads/EUB9603H/include/drv_types.h:67,
                 from /home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:23:
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_da’:
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_sa’:
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_hdr_bssid’:
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast to pointer from integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/drv_types.h:73,
                 from /home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:23:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c: In function ‘_init_xmit_priv’:
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:143: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:206: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:223: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c: In function ‘xmitframe_addmic’:
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:682: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:682: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:682: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c: In function ‘make_wlanhdr’:
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:868: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:868: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:868: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:868: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c: In function ‘xmitframe_coalesce’:
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:1140: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl871x_xmit.c:1144: warning: cast to pointer from integer of different size
  CC [M]  /home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.o
In file included from /home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.c:22:
/home/mike/Downloads/EUB9603H/include/osdep_service.h: In function ‘_init_timer’:
/home/mike/Downloads/EUB9603H/include/osdep_service.h:151: warning: cast from pointer to integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/rtl871x_ht.h:25,
                 from /home/mike/Downloads/EUB9603H/include/drv_types.h:67,
                 from /home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.c:23:
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_da’:
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:350: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:353: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:356: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:359: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_sa’:
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:374: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:377: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:380: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:383: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h: In function ‘get_hdr_bssid’:
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:397: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:400: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/wifi.h:403: warning: cast to pointer from integer of different size
In file included from /home/mike/Downloads/EUB9603H/include/drv_types.h:73,
                 from /home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.c:23:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h: In function ‘rxmem_to_recvframe’:
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/include/rtl871x_recv.h:434: warning: cast to pointer from integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.c: In function ‘dump_xframe’:
/home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.c:1606: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.c:1606: warning: cast from pointer to integer of different size
/home/mike/Downloads/EUB9603H/xmit/rtl8712_xmit.c:1606: warning: cast to pointer from integer of different size
  LD [M]  /home/mike/Downloads/EUB9603H/8712u.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mike/Downloads/EUB9603H/8712u.mod.o
  LD [M]  /home/mike/Downloads/EUB9603H/8712u.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
root@mikes-laptop:/home/mike/Downloads/EUB9603H# make install
install -p -m 644 8712u.ko  /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-33-generic
exit
root@mikes-laptop:/home/mike/Downloads/EUB9603H# exit
exit
Now I just complete the steps above? (sudo rmmod -f r192s_usb  - [FONT=monospace]sudo modprobe 8712s - then blacklist if running properly?[/FONT]

---

### Post by chili555 on 2011-08-10
> Now I just complete the steps above? (sudo rmmod -f r192s_usb - sudo modprobe 8712s - then blacklist if running properly?Yes, please. Shall I seatbelt myself in to my chair?

It did 'make' without error, but that is a great big pile-o-warnings! I am going to do some Googling while you test.

---

### Post by Stray Wolf on 2011-08-11
I'm expecting the gentleman (Mike) to bring his laptop back up here for me to tinker with sometime this afternoon.  Sorry if this ends up waisting your time.  But, if it works, maybe it can help others in the community.

---

### Post by Stray Wolf on 2011-08-11
Alright.  After sudo rmmod -f r8192s_usb it went to a new prompt line where I entered:  sudo modprobe 8712s and I received: FATAL: Module 8712s not found.

---

### Post by chili555 on 2011-08-11
Sorry, my mistake:> root@mikes-laptop:/home/mike/Downloads/EUB9603H# make install
install -p -m 644 [COLOR="Red"]8712**u**[/COLOR].ko /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-33-generic
exitPlease try:> sudo modprobe 8712uThanks.

---

### Post by Stray Wolf on 2011-08-11
Ok.  I did sudo modprobe 8712u.  The result was a new command line.  So, is that it or or are there any tests I should run?

---

### Post by chili555 on 2011-08-11
That means the command was accepted and executed with no errors, warnings, smoke, sparks, etc. Now was a wireless interface created?```
iwconfig
```Do you see networks when you click the Network Manager icon? What does this tell us?```
dmesg | grep 8712
```

---

### Post by Steve53 on 2011-12-27
I need help with this same issue. But I am very new at this and do not know where to start I did download the .rar file but when I tried to open it the archive manager siad it could not open it.  Help

---

### Post by chili555 on 2011-12-28
> **Steve53 said:**
> I need help with this same issue. But I am very new at this and do not know where to start I did download the .rar file but when I tried to open it the archive manager siad it could not open it.  HelpAre you running an older Ubuntu version? Please see post #2 above.

To extract the package, you'll need the package unrar:```
sudo apt-get install unrar
```Then you can right-click the package and select 'Extract Here.'

---

### Post by Steve53 on 2011-12-30
> **chili555 said:**
> Are you running an older Ubuntu version? Please see post #2 above.

To extract the package, you'll need the package unrar:```
sudo apt-get install unrar
```Then you can right-click the package and select 'Extract Here.'

I am running version 11.10. I have placed rtl8192.bin in \\lib\firmware\rtl8192su
Iran modprobe it does see the EnGenius device.

steve@steve-FK785AA-ABA-s3620f:~$ sudo modprobe 8712u
[sudo] password for steve: 
FATAL: Module 8712u not found.
steve@steve-FK785AA-ABA-s3620f:~$ dmesg | grep 8712
[   10.228507] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   10.229840] r8712u: DriverVersion: v7_0.20100831
[   10.229861] r8712u: register rtl8712_netdev_ops to netdev_ops
[   10.229864] r8712u: USB_SPEED_HIGH with 4 endpoints
[   10.230338] r8712u: Boot from EFUSE: Autoload OK
[   10.768099] r8712u: CustomerID = 0x0000
[   10.768105] r8712u: MAC Address from efuse = 00:02:6f:87:31:68
[   10.778506] usbcore: registered new interface driver r8712u
[   10.840093] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   11.605214] r8712u: 1 RCR=0x153f00e
[   11.605960] r8712u: 2 RCR=0x553f00e
steve@steve-FK785AA-ABA-s3620f:~$ ^C
steve@steve-FK785AA-ABA-s3620f:~$ 

I do not see the device in Network connections. The link light is blinking on the device.

---

### Post by chili555 on 2011-12-31
> I have placed rtl8192.bin in \\lib\firmware\rtl8192suIn fact, the driver is looking for it in /lib/firmware/rtlwifi and it found it just fine:> r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"What does this suggest?```
iwconfig
sudo cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Thanks.

---

