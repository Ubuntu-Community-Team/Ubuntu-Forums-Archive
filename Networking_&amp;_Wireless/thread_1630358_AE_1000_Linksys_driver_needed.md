---
title: "AE 1000 Linksys driver needed"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by elkingrey on 2010-11-25
Hello,

I have been trying the last several days to find the driver/install instructions for the AE 1000 wireless adapter for Ubuntu 10.10. If anybody can point me in the right direction your help would be greatly appreciated. These are some of my specs. I'm a linux noob so if there are any other specs you'd like me to get I will probably need to be given the command for getting them as way. Thank you.

lsusb gives me

Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]

iwconfig gives me

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MBR-135"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:30:44:06:71:35   
          Bit Rate=54 Mb/s   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:n
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

uname -a gives me

Linux seth-Dimension-8400 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

---

### Post by chili555 on 2010-11-25
It appears that you have a wireless interface, wlan0, and that you are even connected! Am I missing something?

I'd love to see:```
dmesg | grep rt2
lsmod | grep rt2
```

---

### Post by elkingrey on 2010-11-25
dmesg | grep rt2 produced nothing.

lsmod | grep rt2 produced

rt2x00usb               9779  1 rt73usb
rt2x00lib              27275  2 rt73usb,rt2x00usb
led_class               2633  1 rt2x00lib
mac80211              231541  2 rt2x00usb,rt2x00lib
cfg80211              144470  2 rt2x00lib,mac80211

---

### Post by elkingrey on 2010-11-25
Okay, I apologize. I ran the iwconfig while I was connected to the internet through my old wireless adapter. When I ran it just now disconnected from the internet, yet plugged in with my new wireless adapter I got

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2010-11-25
I'm mystified. rt73usb is not correct for your device, however, you have a wireless interface, wlan0 that is apparently connected! Do you have more than one wireless device? Do you have an available ethernet connection so we can download and install files?

---

### Post by elkingrey on 2010-11-25
I've got two wireless adapters. The old one is a Linksys G and the new one is the Linksys N. I've got internet no problem with the Linksys G but if I unplug it I cannot get internet with the linksys N(AE 1000). I can also have them both plugged in at the same time of course, since they're both USB adapters. So I can download whatever I need to while the inoperative linksys AE 1000 is plugged in.

---

### Post by chili555 on 2010-11-25
It's time to get your geek on. This will get a bit difficult, but I will try to explain everything carefully. If in doubt, stop and ask.

With your internet connection going, do:```
sudo apt-get install build-essential linux-headers-generic
```This assumes that, when you run:```
uname -r
```...that you are running a generic kernel. If in doubt, ask.

Next, go here and download 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Detach your Linksys G.

By default, downloads go to a directory called Downloads. Open it and right-click the file and select 'Extract here.' Open the 2010_0915_RT3572_Linux_STA_v2.4.0.2 folder and then navigate to os/linux/config.mk and change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Change them from =n to =y. Proofread, save and close the text editor.

Next, edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. ***DO NOT ***replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.

Now edit common/rtusb_dev_id.c. Add your device as follows:```
/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT2870
	{USB_DEVICE(0x148F,0x2770)}, /* Ralink */
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */
	{USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
	{USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
        [COLOR="Blue"]{USB_DEVICE(0x13B1,0x002F)}, /* Linksys */[/COLOR]
        --- snip ---
```It doesn't matter whether you add your device first, second, twelfth, etc. Proofread, save and close the text editor.

Open a terminal and do:```
make
```Note any errors and post them here. If there are warnings only and no errors, proceed.```
sudo make install
sudo modprobe rt3572sta
iwconfig
```Is your device running?

---

### Post by elkingrey on 2010-11-25
Wow! These are excellent directions. Thank you!

After I put the make command I got the following message

make: *** No targets specified and no makefile found.  Stop.

Should I have made the command 

make 2010_0195_RT3572_Linux_STA_v2.4.0.2

Also, when I extracted the file I extracted them to a new subfolder in Downloads called Extract.

---

### Post by chili555 on 2010-11-25
I might have been a bit vague about that point; I'm sorry. In a terminal, change directories to where the Makefile is located:```
cd Downloads/Extract/2010_0195_RT3572_Linux_STA_v2.4.0.2
```Now list the contents of the directory:```
ls
```You are in the right place if you see the Makefile, like this:> chips             LICENSE ralink-firmware.txt  RT2870STACard.dat         tools
common            Makefile                     RT2870STA.dat
include           os                           sta
iwpriv_usage.txt  README_STA                   sta_ate_iwpriv_usage.txtNow you are ready to do:```
make
```Proceed as I outlined above. Post back if you get stuck.

---

### Post by elkingrey on 2010-11-26
Okay. These were the only errors I found.

CC [M]  /home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtusb_dev_id.o
/home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtusb_dev_id.c:129: error: redefinition of ‘rtusb_dev_id’
/home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtusb_dev_id.c:40: note: previous definition of ‘rtusb_dev_id’ was here
/home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtusb_dev_id.c:136: error: ‘snip’ undeclared here (not in a function)
/home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtusb_dev_id.c:130: error: unterminated #ifdef
/home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtusb_dev_id.c:136: error: expected expression at end of input
make[2]: *** [/home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtusb_dev_id.o] Error 1
make[1]: *** [_module_/home/seth/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2

---

### Post by chili555 on 2010-11-26
I did not intend for you to put in the line 

--- snip ---

I just used that to tell you that I wasn't printing out the entire rtusb_dev_id file. The rest of the file was to continue unchanged. Did you just add the line --- snip --- or did you remove the remainder of the file? If you just added the line, remove it. If you removed  the file after snip, we need to recreate it. Attached is a replacement. Navigate to the common folder. Delete your rtusb_dev_id.c. Drop this file into the common folder, right click it and select 'Extract here.' Then, in a terminal:```
cd Downloads/Extract/2010_0195_RT3572_Linux_STA_v2.4.0.2
make clean
make
sudo make install
```

---

### Post by elkingrey on 2010-11-26
Yes! I am writing this message to you connected with my new wireless adapter! Thank you!

For the record, I had put the code you gave me at the very bottom of the rtusb_dev_id.c file including the snip. I didn't remove any of the other code. Then, I went back and removed the --snip-- then did make clean and make, but the errors persisted. So I downloaded the zip file you gave me and proceeded from there. And now everything works! 

I really appreciate all of the help you gave me. :p

---

### Post by chili555 on 2010-11-26
Awesome! The searchers will learn from your experience. Please mark the thread solved. I believe it's under Thread Tools above.

---

### Post by SoupFlies on 2010-11-27
I would like to note that if your kernel version is less than 2.6.35, that you can entirely skip the step that is involving the edit of the file /include/os/linux_rt.h

(The first time I did this, I was quite tired, and started trying to look in my root for /include/ then it dawned on me, it is in the downloaded files. Hopefully this saves someone some embarrassment:KS.

---

### Post by chili555 on 2010-11-27
Quite correct! Thank you, sir/madam.

---

### Post by jdonbook86 on 2010-12-02
I went through this long process and got the same error. I closed out the terminal window and went back in fresh to the driver file and reran the make command. For some reason, that broke something loose and the install finally completed without the Error 2. Just something to try.

---

### Post by Grizz Granlien on 2010-12-04
Hello I tried what you was posted and nothing worked so I downloaded and replaced the file with the one you gave us in a message and still no go I installed Ubuntu 10.04 and did all my updates and can't get this computer working wireless yet here is what I did after I replaced the file with your file and did this:

grizzs@grizz-laptop:~$ cd '/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2' 
grizzs@grizz-laptop:~/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2$ make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -fr ../../os/linux/Module.markers
rm -fr ../../os/linux/Module.symvers
rm -fr ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
rm -rf os/linux/Makefile
grizzs@grizz-laptop:~/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2$ make
make -C tools
make[1]: Entering directory `/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.32-26-generic/build SUBDIRS=/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-26-generic'
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_md5.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.o
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1364 bytes is larger than 1024 bytes
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1364 bytes is larger than 1024 bytes
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.o
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c:6112: warning: the frame size of 1720 bytes is larger than 1024 bytes
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_wep.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/action.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_data.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_init.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_aes.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_sync.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/eeprom.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_info.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/dfs.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/spectrum.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rt_channel.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_profile.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_asic.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/assoc.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/auth.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.o
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:1764: warning: the frame size of 1308 bytes is larger than 1024 bytes
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:1094: warning: the frame size of 1300 bytes is larger than 1024 bytes
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:764: warning: the frame size of 1268 bytes is larger than 1024 bytes
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:581: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sanity.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.o
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.c:356: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/wpa.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/ags.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/ba_action.o
  CC [M]  /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coherent’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_free_coherent’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-26-generic'
make: *** [LINUX] Error 2
grizzs@grizz-laptop:~/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo make install
[sudo] password for grizzs: 
make -C /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-26-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.32-26-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3572sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/grizzs/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
make: *** [install] Error 2
grizzs@grizz-laptop:~/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2$ 



I would be happy and so would others if all files and etc were put together and simply run a install file that would be nice if Ubuntu would be simple even for new users... Instructions should be given so that a 5 year old could do it and it would be good,,, try to have your kid get it going if they can't then redo your instructions once your kid can do it post instructions please thanks and hope full Ubuntu gets to that point

---

### Post by chili555 on 2010-12-04
> cmm_mac_usb.c:52: error: implicit declaration of function ‘[COLOR="Red"]usb_alloc_coherent[/COLOR]’The change I suggested in post #7:> Next, edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. DO NOT replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.Is probably not required, in your case, because you are using an older kernel, 2.6.32-26-generic. Please undo that change and try again.

When 'make' ends with an error, please stop and ask us how to proceed. Installation will fail.> I would be happy and so would others if all files and etc were put together and simply run a install file that would be nice if Ubuntu would be simple even for new users... Instructions should be given so that a 5 year old could do it and it would be good,,, try to have your kid get it going if they can't then redo your instructions once your kid can do it post instructions please thanks and hope full Ubuntu gets to that point For most of us, it already is. My grandchildren sit down to my wife's Ubuntu install and surf the web, play games, IM and never complain at all.

Unfortunately, a new wireless card generally comes with no drivers for Linux. In this case, we have to compile the one-size-fits-all driver from the manufacturer. That's really not Ubuntu's fault.

Moreover, if you tell me that you can hand your 5-year-old kid a new wireless card and a bundled driver CD and he can install it with no further guidance, then I am astounded.

---

### Post by slavin80 on 2010-12-05
I just want to say THANK YOU! to every one that posted.  After after about a month of trying my wireless adapter is working.
Thanks again

---

### Post by Grizz Granlien on 2010-12-05
> **chili555 said:**
> The change I suggested in post #7:Is probably not required, in your case, because you are using an older kernel, 2.6.32-26-generic. Please undo that change and try again.

When 'make' ends with an error, please stop and ask us how to proceed. Installation will fail.For most of us, it already is. My grandchildren sit down to my wife's Ubuntu install and surf the web, play games, IM and never complain at all.

Unfortunately, a new wireless card generally comes with no drivers for Linux. In this case, we have to compile the one-size-fits-all driver from the manufacturer. That's really not Ubuntu's fault.

Moreover, if you tell me that you can hand your 5-year-old kid a new wireless card and a bundled driver CD and he can install it with no further guidance, then I am astounded.


Ya I renamed that before I posted my last message and no go

---

### Post by chili555 on 2010-12-05
Are we on the same track here? My post above suggests that you ***NOT*** rename it. Is that what you did? Did you change it back?

If I am misunderstanding, please pardon me.

---

### Post by scarystyx on 2010-12-12
I've been having this same problem.  I'm stuck at the Errors.

scarystyx@scarystyx-MS-7250:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ make
make -C tools
make[1]: Entering directory `/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-23-generic-pae/build SUBDIRS=/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
  CC [M]  /home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_coherent’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/scarystyx/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make: *** [LINUX] Error 2

Any help is appreciated.  Thanks.

---

### Post by chili555 on 2010-12-12
> error: implicit declaration of function ‘usb_buffer_coherent’Did you make the change here as mentioned above? You have a later kernel and this change is needed:> Next, edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. DO NOT replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.Please do so and run:```
make clean
make
sudo make install
```Post back any errors.

---

### Post by scarystyx on 2010-12-12
I made those changes to the only instance of it I found in the file, but the end result is still showing up as the same.

---

### Post by chili555 on 2010-12-12
There is one instance *of each*. Did you find and change both? Did you check your spelling, spacing, case, etc. carefully? Can you please attach a copy of the file to your reply? You may need to rename it linux_rt.txt in order to post it here. Do NOT rename it in your 3572 folder.

I just downloaded it, made the change and it made with a few warnings but no error.

---

### Post by scarystyx on 2010-12-12
I believe I followed the instructions carefully, but I am a novice at this so here's all 3 of the files in question.  Hopefully you can point out my mistake.  Thanks for your patience.

---

### Post by chili555 on 2010-12-13
In your linux_rt.h, line 1077 reads:```
#define RTUSB_URB_ALLOC_BUFFER(pUsb_Dev, BufSize, pDma_addr)				usb_buffer_coherent(pUsb_Dev, BufSize, GFP_ATOMIC, pDma_addr)
```Instead, it should read:```
#define RTUSB_URB_ALLOC_BUFFER(pUsb_Dev, BufSize, pDma_addr)				[COLOR="Red"]usb_alloc_coherent[/COLOR](pUsb_Dev, BufSize, GFP_ATOMIC, pDma_addr)
```Line numbers are visible in the lower right corner of gedit. Please change, proofread and save. 

In your linux_rt.h, line 1078 reads:```
#define RTUSB_URB_FREE_BUFFER(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)	usb_buffer_coherent(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)
```It should read:```
#define RTUSB_URB_FREE_BUFFER(pUsb_Dev, BufSize, pTransferBuf, Dma_addr)	[COLOR="Red"]usb_free_coherent[/COLOR](pUsb_Dev, BufSize, pTransferBuf, Dma_addr)
```Please change, proofread and save. 

I will look at the other files in a moment.

---

### Post by chili555 on 2010-12-13
The other two files look perfect. Please proceed:```
make clean
make
sudo make install
sudo modprobe rt3572sta
iwconfig
```Post back any errors; warnings are fine.

---

### Post by scarystyx on 2010-12-13
That was exactly it.  Thanks for the help.

---

### Post by drjimmy52 on 2010-12-13
Hello,
I am also a newbie to the Linux world.  After  reading this thread, I have tried all of the steps outlined.  The file seems to have built correctly, but when I type iwconfig, there is no ra0 device. I am running Ubuntu 10.10 and don't have Internet access on the computer I am trying to configure.

dmesg | grep rt2: [317.415974] usbcore: registered new interface driver rt2870
lsmod | grep rt2: nothing.

Any thoughts?
Thanks.

---

### Post by conbones on 2010-12-22
well i followed the directions to a T and i am getting a fatel error observe...
conbones@conbones-CM5571:~/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2$ ls
chips             LICENSE ralink-firmware.txt  RT2870STACard.dat         tools
common            Makefile                     RT2870STA.dat
include           os                           sta
iwpriv_usage.txt  README_STA                   sta_ate_iwpriv_usage.txt
conbones@conbones-CM5571:~/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2$ make
make -C tools
make[1]: Entering directory `/home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-23-generic-pae/build SUBDIRS=/home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
  CC [M]  /home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/rt3572sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/rt3572sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
conbones@conbones-CM5571:~/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo make install
make -C /home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-23-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.35-23-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-23-generic-pae
make[1]: Leaving directory `/home/conbones/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
conbones@conbones-CM5571:~/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo modprobe rt3572sta
FATAL: Error inserting rt3572sta (/lib/modules/2.6.35-23-generic-pae/kernel/drivers/net/wireless/rt3572sta.ko): Device or resource busy
conbones@conbones-CM5571:~/Downloads/Extract/2010_0915_RT3572_Linux_STA_v2.4.0.2

what is wrong ?

---

### Post by conbones on 2010-12-22
ok i dont know what happend but i shut down my pc and changed boot priority to my windows7 disc to install it in windows got that done and chaged back to my linux disc and the wireless card works now why is that?
Is it because i activated it in windows7 or did i just have to reboot linux?

---

### Post by chili555 on 2010-12-23
> did i just have to reboot linux?Probably. I'm glad it's working. Have fun!

---

### Post by zami on 2010-12-28
Bah - found it!

I'd changed 
usb_buffer_alloc (fresh)
to
usb_buffer_alloc_coherent (bad!)
instead of
usb_alloc_coherent (good!)

And similar whoopsies with usb_buffer_free

So the below is moot now.

THANK you again Chili man for all the effort you put into this!!

-zami



============================


Chili - you are rediculously patient and helpful!!  Hats off to you sir!

Can you help me troubleshoot what I'm doing wrong here?

I beleive I've followed the instructions perfectly, but I'm still receiving errors during "make".

I've attached zips of the three files altered (one re-un-altered).  At this point, I've been staring at it all for so long I suspect I'm overlooking something silly, like a typo.

Thank you so much for all the help so far.

-zami

Info:

laura@Willa:~$ uname -r
2.6.35-24-generic


minor detail:
Instead of 
/include/os/linux_rt.h

I have
/include/os/rt_linux.h


Errors received: (just pasting the bottom quarter or so)
```

/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [LINUX] Error 2
laura@Willa:~/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2$ 

```

> 
The change I suggested in post #7:
Quote:
Next, edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. DO NOT replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.
Is probably not required, in your case, because you are using an older kernel, 2.6.32-26-generic. Please undo that change and try again.

Okay - that's my kernal too, so I tried undoing that change, did a make clean, and ran make again...
```

/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/laura/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [LINUX] Error 2
laura@Willa:~/Desktop/2010_0915_RT3572_Linux_STA_v2.4.0.2$ 

```

EDIT:  Scratch that about "that being my kernal too" - I'll redo those changes, try again, and upload the "changed" linux_rt.h.  (See, I've been looking at it too long - can't read straight!)

---

### Post by facough on 2010-12-28
hi I'm very new too this Linux world but I'm usually pretty good at following instructions but i just cant seem to get it to find the file to make. i copied and pasted 
cd Downloads/Extract/2010_0195_RT3572_Linux_STA_v2.4.0.2
after following everything to a t but it keeps telling me No such file or directory.
any suggestions for what im doin wrong? thanks

found it but getting the same errors as above...

---

### Post by mnibrad on 2010-12-29
Hello,
 
I've searched everywhere, and first I will say this has been the most helpful thread.  After following the instructions, I have successfully installed with no errors.  The adapter shows as wlan0 under lwconfig and doesn't seem to show any errors.  However, in the task bar under Wireless Networks, it says "device not ready (firmware missing).  I'm actually using the WUSB600N version 2, and updated that in the device name as appropriate.  Is this a related issue, or a different issue all together?
 
Brad

---

### Post by chili555 on 2010-12-29
> **mnibrad said:**
> Hello,
 
I've searched everywhere, and first I will say this has been the most helpful thread.  After following the instructions, I have successfully installed with no errors.  The adapter shows as wlan0 under lwconfig and doesn't seem to show any errors.  However, in the task bar under Wireless Networks, it says "device not ready (firmware missing).  I'm actually using the WUSB600N version 2, and updated that in the device name as appropriate.  Is this a related issue, or a different issue all together?
 
BradPlease start a new thread and post:```
lsusb
dmesg | grep -i firm
```Thanks.

---

### Post by Robr0924 on 2011-01-02
I having the same issues, If I could get some guidance on setting up I would be grateful.  Word of warning I'm totally new to all of this, so newb is truly the word for my expertise with Linux 10.10.  Any help is greatly appreciated.  Started another thread on the same issue, but this one is hitting the nail on the head.

Thanks 

Rob

---

### Post by chili555 on 2011-01-03
The process is as follows. Open Applications > Accessories > Terminal and do:```
lsusb
```Make sure you have the exact same device. If not, post the result and we'll amend the process.> ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]Walk the computer over to the router and get a wired ethernet connection. Still in the terminal, do:```
sudo apt-get install build-essential linux-headers-generic
```Download the file for RT3572 here:  [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

You can proceed as outlined here, except for one addition. [http://ubuntuforums.org/showpost.php?p=10163301&postcount=7](http://ubuntuforums.org/showpost.php?p=10163301&postcount=7)


Just before the 'make' step, do:```
cd Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2
```

Post back if you need more guidance. It looks complex, but go slowly and follow each step carefully and post back immediately if anything is unclear.

---

### Post by spitfirejunky on 2011-01-12
> **chili555 said:**
> It's time to get your geek on. This will get a bit difficult, but I will try to explain everything carefully. If in doubt, stop and ask.

With your internet connection going, do:```
sudo apt-get install build-essential linux-headers-generic
```This assumes that, when you run:```
uname -r
```...that you are running a generic kernel. If in doubt, ask.

Next, go here and download 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Detach your Linksys G.

By default, downloads go to a directory called Downloads. Open it and right-click the file and select 'Extract here.' Open the 2010_0915_RT3572_Linux_STA_v2.4.0.2 folder and then navigate to os/linux/config.mk and change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Change them from =n to =y. Proofread, save and close the text editor.

Next, edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. ***DO NOT ***replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.

Now edit common/rtusb_dev_id.c. Add your device as follows:```
/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT2870
    {USB_DEVICE(0x148F,0x2770)}, /* Ralink */
    {USB_DEVICE(0x148F,0x2870)}, /* Ralink */
    {USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
    {USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
        [COLOR=Blue]{USB_DEVICE(0x13B1,0x002F)}, /* Linksys */[/COLOR]
        --- snip ---
```It doesn't matter whether you add your device first, second, twelfth, etc. Proofread, save and close the text editor.

Open a terminal and do:```
make
```Note any errors and post them here. If there are warnings only and no errors, proceed.```
sudo make install
sudo modprobe rt3572sta
iwconfig
```Is your device running?

I wanted to confirm that these directions (down to every last detail) worked for me. Now I don't have to settle for an ndiswrapper driver that freezes hopelessly.

I should add that the correct download link is labeled "RT3572USB" if that wasn't already obvious.

Thank you, chili.

---

### Post by chili555 on 2011-01-12
Thank you for your kind comments. I am glad it's working and I am sure you have helped some searchers.

---

### Post by rodrickhales on 2011-01-13
Thanks for the instructions. I followed the instructions and the wireless networks in my area were detected.  However, when I enter the password for my network it try to connect and keeps asking for it again and again.  I know it is the right one.  Any ideas?

P.S.  I don't know why we have to do all of this just to make it work but whoever is doing the ground work for the instructions, more power to you!

---

### Post by chili555 on 2011-01-13
Either your driver, Network Manager or wpa_supplicant have problems in two areas. I don't know which. First, it can be troublesome to connect to SSIDs with a space, such as "Chili House." If yours has a space, try changing to something else, such as, "ChiliHouse."

Second, many routers have a mixed WPA and WPA2 mode. The intent, I believe, is to be backwards compatible with older hardware that may not be WPA2 capable. If yours is so configured, you will have better luck with WPA ***or*** WPA2; not both.

Finally, have you double-checked the password? Does it work seamlessly in other computers on the network?

---

### Post by djt69@comcast.net on 2011-01-22
Hi - per these instructions:

Next, go here and download 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

There is now a version 2.5 available... any help would be appreciated.  The .h file change, that it turns out I don't have to do because of my kernel level, is now actually in a different folder and has been renamed.  I end up with similar problems during the first make with a few errors in cmm_mac_usb.c.  

uname -a
Linux docker 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux


/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_alloc_coherent’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_free_coherent’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:235: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:242: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:280: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:509: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:568: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:598: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:612: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:630: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/dtkaczyk/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-27-generic'
make: *** [LINUX] Error 2

---

### Post by djt69@comcast.net on 2011-01-22
OK the fix for my issue above is (this may not work for everyone - it depends on your version of ubuntu):


edit ./include/os/rt_linux.h

edit line 1157 to read:

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 32)

this helps it to make my uname information

uname -a
Linux docker 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

all prior instructions should work fine with 2.5...

---

### Post by dreamsforgotten on 2011-02-12
> **djt69@comcast.net said:**
> OK the fix for my issue above is (this may not work for everyone - it depends on your version of ubuntu):


edit ./include/os/rt_linux.h

edit line 1157 to read:

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 32)

this helps it to make my uname information

uname -a
Linux docker 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux

all prior instructions should work fine with 2.5...

Same errors as above with recent ubuntu update.  I'm running 2.6.32-28 generic
Line 1157 doesn't match but I edited the closest field and no dice.  I did make clean and tried a few others, no dice.  Seems I need a hand here so I can go on with making android source.

---

### Post by judderwocky on 2011-02-12
> **dreamsforgotten said:**
> Same errors as above with recent ubuntu update.  I'm running 2.6.32-28 generic
Line 1157 doesn't match but I edited the closest field and no dice.  I did make clean and tried a few others, no dice.  Seems I need a hand here so I can go on with making android source.

I'm running Linux 2.6.35-25-generic 

I tried make using the changes with and without rt_linux.h ... but each time i get the same errors listed as above.

---

### Post by vorinoch on 2011-02-13
I was previously running Lucid installed via the Windows WUBI installer, and the original instructions worked fine until October, when running a batch of updates caused the adapter to not be recognized, and attempting to reinstall the driver gave me the same error with the "make" command as you guys are experiencing.  I've since reinstalled Lucid as a proper dual-boot with the alternate CD (as of today,) and the connection is up and fine once again.  I'm taking the trouble you guys are experiencing as confirmation that I should hold off on blindly running the update manager until a workaround is found?

---

### Post by dreamsforgotten on 2011-02-13
> **vorinoch said:**
> I was previously running Lucid installed via the Windows WUBI installer, and the original instructions worked fine until October, when running a batch of updates caused the adapter to not be recognized, and attempting to reinstall the driver gave me the same error with the "make" command as you guys are experiencing.  I've since reinstalled Lucid as a proper dual-boot with the alternate CD (as of today,) and the connection is up and fine once again.  I'm taking the trouble you guys are experiencing as confirmation that I should hold off on blindly running the update manager until a workaround is found?

Yes you should, I was fine until my latest update ran.  Hopefull we get a work around soon I dont have a wired connection to revert the kernel.

---

### Post by chili555 on 2011-02-13
> Hopefull we get a work around soon I dont have a wired connection to revert the kernel.Can't you access the GRUB menu and boot into the older kernel? You can certainly remove the newer kernel if the older works for you.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)> The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. Grub 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or Grub 2 cannot determine the status of the key, the menu is displayed. Note: The "SHIFT" keystatus check is currently nested within in a conditional statement within /etc/grub.d/30_os-prober and may not work under certain circumstances.

---

### Post by thatguy29 on 2011-02-14
Just wanted to chime in and say thanks to all for posting here.  After a few hours of searching and running into most of the same issues from this thread I've finally got the Linksys Adapter working.  Now on to the next steps in configuring the new OS install.  :p

Thanks all!

---

### Post by vorinoch on 2011-02-19
Can anyone confirm that simply booting off the older kernel (with all other OS updates installed) will allow the AE1000 to function?

---

### Post by joshuaje1 on 2011-02-23
Hey Chili, I hope you are online still, I got the following errors after the "make" command:


```
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ make
make -C tools
make[1]: Entering directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ 

```

PS: 2.4.0.2 was not available for download

---

### Post by chili555 on 2011-02-24
Please open System > Administration > Synaptic and confirm that you have build-essential and linux-headers-generic installed. Next, did you run with:```
cd Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO\ (2)
[COLOR="Red"]sudo su[/COLOR]
make clean
make
make install
modprobe rt3572sta
[COLOR="Red"]exit[/COLOR]
```Thanks.

---

### Post by joshuaje1 on 2011-02-24
**I did, same error for every command except for modprobe; and I had to modify the command as follows "modprobe rt2870sta"**


```
root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/os/linux'
/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO:1: warning: NUL character seen; rest of line ignored
/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO:1: *** missing separator.  Stop.
make[1]: Leaving directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/os/linux'
make: *** [clean] Error 2
root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# make
make -C tools
make[1]: Entering directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2
root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# make install
make -C /home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/os/linux -f Makefile.6 install
/bin/sh: Syntax error: "(" unexpected
make: *** [install] Error 2
root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# modprobe rt3572sta
FATAL: Module rt3572sta not found.
root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# ls
chips    iwpriv_usage.txt             Makefile    RT2870STACard.dat  sta_ate_iwpriv_usage.txt
common   LICENSE ralink-firmware.txt  os          RT2870STA.dat      tools
include  LICENSE ralink-GPL.txt       README_STA  sta
root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# modprobe rt2870sta
root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# 

```

**I also had to modify the line for rtusb_dev_id.c as I'm using the WUSB600Nv2 wireless usb adapter, modifed as follows:**

```
{USB_DEVICE(0x1737,0x0079)}, /* WUSB600Nv2 */
```> **chili555 said:**
> Please open System > Administration > Synaptic and confirm that you have build-essential and linux-headers-generic installed. Next, did you run with:```
cd Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO\ (2)
[COLOR=Red]sudo su[/COLOR]
make clean
make
make install
modprobe rt3572sta
[COLOR=Red]exit[/COLOR]
```Thanks.
[B]
I searched for a while last night to no success in finding a solution that worked for my WUSB600Nv2, so I'm hoping that you can help, you seem like you're a master at this stuff.

Ubuntu 10.10 64bit
2.6.35-25 generic[/B]

---

### Post by chili555 on 2011-02-24
> I had to modify the command as follows "modprobe rt2870sta"
Why?? rt2870sta is *NOT* correct for your device. > root@jsys:/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)# modprobe rt3572sta
FATAL: Module rt3572sta not found.If you get an error at 'make' and an error at 'make install,' then the module has not built correctly. It does no good to trudge on blindly; it won't work.> /bin/sh: Syntax error: word unexpected (expecting ")")
I haven't seen this behavior previously. I fear it's a compatibility issue with 64-bit. I have this exact file on my computer, a 32-bit system, and it compiles with a few warnings, but no errors. You might check the README file and email the developer for help.

---

### Post by joshuaje1 on 2011-02-24
rt2870sta was the only file available, I was just taking a stab in the dark.
 
You think if I use .22 generic instead of .25 there would be a difference?
 
Also, do you have the raltech 2.4.0.2 file?  Maybe that might make a difference?
 
> **chili555 said:**
> Why?? rt2870sta is *NOT* correct for your device. If you get an error at 'make' and an error at 'make install,' then the module has not built correctly. It does no good to trudge on blindly; it won't work.I haven't seen this behavior previously. I fear it's a compatibility issue with 64-bit. I have this exact file on my computer, a 32-bit system, and it compiles with a few warnings, but no errors. You might check the README file and email the developer for help.

---

### Post by chili555 on 2011-02-24
> Also, do you have the raltech 2.4.0.2 file? Nope, sorry. I'm sorry I can't be of more help.> You think if I use .22 generic instead of .25 there would be a difference?Try it and we'll see. Can you interrupt the boot process and select -22 at the GRUB menu and build the module as above?

I still think it's 64-bit related.

---

### Post by joshuaje1 on 2011-02-24
Yeah, I think i'll try selecting .22 this time, and build it per your instructions.  Just because you haven't given me a definitive answer doesn't mean you haven't helped me :)
 
> **chili555 said:**
> Nope, sorry. I'm sorry I can't be of more help.Try it and we'll see. Can you interrupt the boot process and select -22 at the GRUB menu and build the module as above?
 
I still think it's 64-bit related.

---

### Post by natsfan on 2011-03-01
i was wondering is someone could help me out as well! have a similar issue to joshuaje1, i would get the same fatal error at the madprobe stage. so i tried changing mine to 2870 as well, and it partially worked, now i am able to see an interface, but when i try to bring it up it just locks up and i have to ifconfig ra0 down for it to be accessed again... any ideas????

---

### Post by vorinoch on 2011-03-14
Has anyone who ran into that error during the "make" command figured a workaround?  Does simply booting off the old kernel work?  I have no wired connection and am nervous about FUBARing my internet access.

---

### Post by garypat on 2011-03-24
2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2
is no longer posted on site

---

### Post by garypat on 2011-03-24
:( did not work

gary@gary-desktop:~$ cd~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO
bash: cd~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO: No such file or directory
gary@gary-desktop:~$ cd ~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO
[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ ls
2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO  os
chips                                    README_STA
common                                   RT2870STACard.dat
include                                  RT2870STA.dat
iwpriv_usage.txt                         sta
LICENSE ralink-firmware.txt              sta_ate_iwpriv_usage.txt
LICENSE ralink-GPL.txt                   tools
Makefile
[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ make
make -C tools
make[1]: Entering directory `/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic-pae/build SUBDIRS=/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
  CC [M]  /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo make install
[sudo] password for gary: 
make -C /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-28-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.35-28-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-28-generic-pae
make[1]: Leaving directory `/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo modprobe rt3572sta
[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo make install
make -C /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-28-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.35-28-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-28-generic-pae
make[1]: Leaving directory `/home/gary/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo modprobe rt3572sta
[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[email]gary@gary-desktop:~/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$

---

### Post by tylerwatt12 on 2011-03-25
spent a few hours fixing this. the new kernel with ubuntu 10.10 doesnt need the 

>  edit /include/os/linux_rt.h to change the two functions  usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent  and usb_free_coherent, respectively. so you noobs better not use it :P

other than that, i got my drivers working. thanks!
(no reboot required for me) Ubuntu 10.10 x86

---

### Post by ugmoe2000 on 2011-03-27
> **joshuaje1 said:**
> Hey Chili, I hope you are online still, I got the following errors after the "make" command:


```
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ make
make -C tools
make[1]: Entering directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools'
/home/joshua/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)/tools/bin2h
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2
joshua@jsys:~/Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO (2)$ 

```

PS: 2.4.0.2 was not available for download

The problem with the build here is the name of the directory you're trying to run "make" inside of. It looks like in the process of unzipping your 2.5.0.0 drivers you've created the folder with a "()" in the name.... the 'make' program does NOT like this and bitches /w the following output:
'/bin/sh: Syntax error: word unexpected (expecting ")")'

the "()"s have a special meaning to 'make' (or the bash shell really) and shouldn't typically be used in file-names however the auto-extractor that comes pre-loaded /w Ubuntu just creates the directory w/ the "(2)" because it already sees a file by the name it wanted to use.


IN SHORT: Rename the directory to something without the "()"s in the name and assuming you've installed the proper dependencies, the build should complete. 

However the 2.5.0.0 drivers don't really work properly if you're using a 64-bit version of Ubuntu... at least mine didn't and I stumbled upon a forum where people complained of the same. I was able to find a solution that worked for me with my 64-bit linux... you can follow the instructions here if this applies to you bubba911 made an excellent write-up: [http://ubuntuforums.org/showthread.php?p=10609146#post10609146](http://ubuntuforums.org/showthread.php?p=10609146#post10609146)

---

### Post by chili555 on 2011-03-28
> IN SHORT: Rename the directory to something without the "()"s in the name As well as the space that precedes it.

---

### Post by jim206 on 2011-04-15
> **chili555 said:**
> It's time to get your geek on. This will get a bit difficult, but I will try to explain everything carefully. If in doubt, stop and ask.

With your internet connection going, do:```
sudo apt-get install build-essential linux-headers-generic
```This assumes that, when you run:```
uname -r
```...that you are running a generic kernel. If in doubt, ask.

Next, go here and download 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Detach your Linksys G.

By default, downloads go to a directory called Downloads. Open it and right-click the file and select 'Extract here.' Open the 2010_0915_RT3572_Linux_STA_v2.4.0.2 folder and then navigate to os/linux/config.mk and change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Change them from =n to =y. Proofread, save and close the text editor.

Next, edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. ***DO NOT ***replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.

Now edit common/rtusb_dev_id.c. Add your device as follows:```
/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT2870
	{USB_DEVICE(0x148F,0x2770)}, /* Ralink */
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */
	{USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
	{USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
        [COLOR="Blue"]{USB_DEVICE(0x13B1,0x002F)}, /* Linksys */[/COLOR]
        --- snip ---
```It doesn't matter whether you add your device first, second, twelfth, etc. Proofread, save and close the text editor.

Open a terminal and do:```
make
```Note any errors and post them here. If there are warnings only and no errors, proceed.```
sudo make install
sudo modprobe rt3572sta
iwconfig
```Is your device running?
I tried this. worked great.......except for one little detail........would NOT connect......period.
Any pointers?

---

### Post by jetbangdink on 2011-04-26
im having this same problem and i dont have a os/linux/config.mk directory it says it doesnt exist

---

### Post by Edaw 0 on 2011-05-01
> **tylerwatt12 said:**
> spent a few hours fixing this. the new kernel with ubuntu 10.10 doesnt need the 

> edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. 

so you noobs better not use it :P

Thanks, was going crazy here. After figuring out which kernel I have and getting the latest and greatest driver, works like a charm!

Chili555 you rock!

---

### Post by ferchope on 2011-05-01
it works but it only connects after several tries

---

### Post by chili555 on 2011-05-01
> **jetbangdink said:**
> im having this same problem and i dont have a os/linux/config.mk directory it says it doesnt existInside the folder 2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO, isn't there a folder called *os*? Inside *os* isn't there *linux*? Inside *linux*, insn't the a file *config.mk*?

---

### Post by snakebones on 2011-05-04
First thanks chili555 for the great thread. I had a couple issues the files everyone was using weren't on the server it was updated.
I found all except "common/rtusb_dev_id.c". I'm running ubuntu 11.04 and for some reason i don't know if its just me or nautilus but that file wasn't there. Now when I opened "/common" in terminal and did a ls it was there. So if anyone was having the same issue hopefully this helped

---

### Post by chili555 on 2011-05-04
I've tried every trick I know and I can't get it to compile in 11.04. Did you?

---

### Post by gershy on 2011-05-16
I just spent a few hours today getting this to work on 11.04. All of  these steps are a compilation of various guides on the web. Hope this  helps someone!

[SIZE=3]1.)[/SIZE][INDENT]     Type [COLOR=Red]lsusb[/COLOR] in terminal; if using AE1000 you should see a line similar to this:
[/INDENT][INDENT]     ```
Bus 001 Device 002: ID [COLOR=Red]13b1:002f[/COLOR] Linksys AE1000 v1 802.11n [Ralink RT2870]

```[/INDENT][INDENT]     All you need to worry about is this bit:  ```
[COLOR=Red]13b1:002f[/COLOR]
```[SIZE=3]
[/SIZE][/INDENT][SIZE=3]2.)[/SIZE][INDENT] Download the [COLOR=Blue][RT3572USB]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXhMekEwTHpJM0wyUnZkMjVzYjJGa056RXhOamcyTXpRMk9DNWllakk5UFQweU1ERXhYekEwTWpkZlVsUXpOVGN5WDB4cGJuVjRYMU5VUVY5Mk1pNDFMakF1TUM1RVVFOD1D")[/COLOR] drivers
[/INDENT][SIZE=3]3.)[/SIZE][INDENT]Unpack the download
[/INDENT][INDENT]Navigate to:
 [COLOR=Silver]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/common
And open:
[COLOR=Blue]rtusb_dev_id.c[/COLOR]

Scroll down to the 
```
#endif /* RT2870*/
#ifdef RT35xx
```section of code

and add:
```
{USB_DEVICE(0x13b1,0x002f)}, /* Linksys AE1000 */
```Reference: [http://i.imgur.com/GHfRj.png](http://i.imgur.com/GHfRj.png)

[/INDENT][SIZE=3]4.)[/SIZE][INDENT]Navigate to: 
[COLOR=Silver]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/common/os
And open:
[COLOR=Blue]rt_linux.h[/COLOR]
Scroll down to line **1161** and **1162**
Alternatively: ctrl+f and type *usb_buffer*
Change
```
#define RTUSB_URB_ALLOC_BUFFER(_dev, _size, _dma)        [COLOR=SeaGreen]usb_buffer_alloc[/COLOR](_dev, _size, GFP_ATOMIC, _dma)
#define RTUSB_URB_FREE_BUFFER(_dev, _size, _addr, _dma)    [COLOR=SeaGreen]usb_buffer_free[/COLOR](_dev, _size, _addr, _dma)
```to:
```
#define RTUSB_URB_ALLOC_BUFFER(_dev, _size, _dma)        [COLOR=SeaGreen]usb__alloc_coherent[/COLOR](_dev, _size, GFP_ATOMIC, _dma)
#define RTUSB_URB_FREE_BUFFER(_dev, _size, _addr, _dma)    [COLOR=SeaGreen]usb_free_coherent[/COLOR](_dev, _size, _addr, _dma)
```[/INDENT][SIZE=3]5.)[/SIZE][INDENT]Navigate to:
[COLOR=Silver]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux
And open:
[COLOR=Blue]config.mk[/COLOR]
Change lines 14,17,32 to =y instead of =n

[/INDENT][SIZE=3]6.)[/SIZE][INDENT]Open the terminal
Change directory to: 
[COLOR=SlateGray]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
Once in that directory, type:
```
[COLOR=Red]make[/COLOR]
```After it's done type:
```
[COLOR=Red]sudo make install[/COLOR]
```[/INDENT][SIZE=3]7.)[/SIZE][INDENT]After installation type:
```
[COLOR=Red]sudo modprobe rt3572sta[/COLOR]
```After about 10 seconds, you should be prompted to enter your WiFi password.
[/INDENT]

---

### Post by judderwocky on 2011-05-20
Thanks for the info, ... Still not working for me,

---

### Post by judderwocky on 2011-05-23
> **judderwocky said:**
> Thanks for the info, ... Still not working for me,
make[1]: Entering directory `/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Modules.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -rf os/linux/Makefile
[EMAIL="myuser@olympus:%7E/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO"]myuser@olympus:~/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/EMAIL]$ make
make -C tools
make[1]: Entering directory `/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.o
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Wrap’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c:1478:6: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c: In function ‘AES_Key_Unwrap’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_aes.c:1573:6: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.o
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.c: In function ‘MlmeResetRalinkCounters’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.c:918:3: warning: cast from pointer to integer of different size
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/mlme.c:918:3: warning: cast from pointer to integer of different size
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/action.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_init.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/dfs.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/spectrum.o
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/spectrum.c: In function ‘PeerMeasureReportAction’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/spectrum.c:1983:3: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_asic.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/auth.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sync.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/connect.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/ags.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ba_action.o
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ba_action.c: In function ‘convert_reordering_packet_to_preAMSDU_or_802_3_packet’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ba_action.c:1578:2: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../sta/dls.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:235:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:242:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:280:11: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:509:12: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:568:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:598:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:612:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:630:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_io.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_data.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.o
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c: In function ‘RT30xx_ChipSwitchChannel’:
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c:614:17: warning: unused variable ‘BbpR109’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c:613:30: warning: unused variable ‘Tx1FinePowerCtrl’
/home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt30xx.c:613:8: warning: unused variable ‘Tx0FinePowerCtrl’
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt28xx.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../chips/rt35xx.o
  CC [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_dev_id.o
  LD [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.ko


don't know if im missing something stupid,,, im really new to this

---

### Post by chili555 on 2011-05-23
> CC [M] /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtusb_dev_id.o
LD [M] /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.o
Building modules, stage 2.
MODPOST 1 modules
LD [M] /home/myuser/ralink/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.koYou have warnings but no errors. Please proceed with:```
sudo make install
sudo modprobe rt3572sta
iwconfig
```Thanks.

---

### Post by judderwocky on 2011-05-23
ok, installed, and when i do i can see lists of networks, but when i click on one it just stalls out.

i checked lsusb and got Bus 001 Device 004: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]

so i blacklisted everything 
/etc/modprobe.d/blacklist.conf

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
blacklist rt2870lib
blacklist rt2870usb

and still it comes up

i checked 

/etc/modules

and didn't have any thing except the defualts, so i added 

rt3572sta  ... still get 2870 on the lsusb

i'm stumped

thanks for helping :)

---

### Post by chili555 on 2011-05-23
> blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
[COLOR="Red"]blacklist rt2870lib
blacklist rt2870usb[/COLOR]The items I highlighted don't exist. These lines do nothing. They probably don't hurt, but to be OCD perfect, you might simply remove them.> still get 2870 on the lsusb
I assume you mean here:> Bus 001 Device 004: ID 13b1:002f Linksys AE1000 v1 802.11n [[COLOR="Red"]**Ralink RT2870**[/COLOR]]That part is a hard-coded identifier; you and I couldn't, through any means I am aware of, change this if we tried. Ralink identifies this as a member of the RT2870 series of chipsets. That, in no way, means with certainty, that rt2870sta is the best driver for the device.> when i do ***i can see lists of networks***, but when i click on one it just stalls out.That suggests that rt3572sta is working but maybe not optimally. Let's do some diagnostics. Please run and post:```
dmesg | grep -e ra0 -e rt3
```Thanks.

---

### Post by judderwocky on 2011-05-23
> **chili555 said:**
> The items I highlighted don't exist. These lines do nothing. They probably don't hurt, but to be OCD perfect, you might simply remove them.I assume you mean here:That part is a hard-coded identifier; you and I couldn't, through any means I am aware of, change this if we tried. Ralink identifies this as a member of the RT2870 series of chipsets. That, in no way, means with certainty, that rt2870sta is the best driver for the device.That suggests that rt3572sta is working but maybe not optimally. Let's do some diagnostics. Please run and post:```
dmesg | grep -e ra0 -e rt3
```Thanks.

the out put was, 

[   38.180030] ra0: no IPv6 routers present
[   87.440195] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!

Thanks :)

---

### Post by chili555 on 2011-05-24
Let's review the process you followed to compile the driver. Which tutorial did you follow? gershy's above?

---

### Post by judderwocky on 2011-05-27
> **chili555 said:**
> Let's review the process you followed to compile the driver. Which tutorial did you follow? gershy's above?

sorry for the delay, I used the above... well actually i've tried all of them... both with 10.10 and 11.04 ... and always gotten about the same result. I get pretty much the same compile errors and then sometimes ill install it anyway, and it never connects. 

There were a few times i managed to get it to spontaneously connect in 10.10 and then it would work for like five minutes, and then the computer would completely freeze up. 

in 11.04 the signal strength always displays as zero... even though it didn't work , in 10.10 it would display as full and the one time it did connect was very fast.

---

### Post by P8TRIOT on 2011-05-28
> **judderwocky said:**
> sorry for the delay, I used the above... well actually i've tried all of them... both with 10.10 and 11.04 ... and always gotten about the same result. I get pretty much the same compile errors and then sometimes ill install it anyway, and it never connects. 

There were a few times i managed to get it to spontaneously connect in 10.10 and then it would work for like five minutes, and then the computer would completely freeze up. 

in 11.04 the signal strength always displays as zero... even though it didn't work , in 10.10 it would display as full and the one time it did connect was very fast.

Same here I got everything compiled and working however it never seems  to connect, just keeps scanning and prompting for the authentication,  and I have triple checked the pass. and I know i am using the right one.  BTW I am running this on 10.04. Also everyone who has contributed to  the fix has been extremely helpful, thank you all. Now if we could get  past this last hurdle, it's like we are sooo close but not there yet.

---

### Post by judderwocky on 2011-05-29
> **P8TRIOT said:**
> Same here I got everything compiled and working however it never seems  to connect, just keeps scanning and prompting for the authentication,  and I have triple checked the pass. and I know i am using the right one.  BTW I am running this on 10.04. Also everyone who has contributed to  the fix has been extremely helpful, thank you all. Now if we could get  past this last hurdle, it's like we are sooo close but not there yet.

 I know i got it to connect once, when my Belkin G card was in at the same time, on 10.10.... I pulled the belkin out and it worked for about five minutes... The speed was much faster and the Signal strength showed full for the Linksys card... Then the computer froze, and when I restarted it wouldn't connect, and I couldn't duplicate it. 

In 11.04 I only get one bar of strength. Which I think is weird. Even in 10.10 it still showed full signal strength even though I only got it to connect the one time. I don't know if its significant...

---

### Post by Acrosby on 2011-06-02
Hi all, 
When I do code "make" in the terminal it replies with

ashley@ashley-GA-MA790XT-UD4P:~$ make
make: *** No targets specified and no makefile found.  Stop.

any Ideas?
acrosby

---

### Post by judderwocky on 2011-06-02
> **Acrosby said:**
> Hi all, 
When I do code "make" in the terminal it replies with

ashley@ashley-GA-MA790XT-UD4P:~$ make
make: *** No targets specified and no makefile found.  Stop.

any Ideas?
acrosby

sorry ,its hard to tell what directory you are in... did you cd into the directory? 
you get that error i think if you aren't in the right directory...

---

### Post by Acrosby on 2011-06-02
Im a noob here, how do you cd into the directory?

---

### Post by chili555 on 2011-06-02
> **Acrosby said:**
> Im a noob here, how do you cd into the directory?Where did you download the file that you extracted? Downloads? Your Desktop? In the terminal, you need to change directories (cd) to the directory where the Makefile is located. It's sometning like:```
cd Downloads/2010_1215_RT3572_Linux_STA_v2.5.0.0.DPO
make
sudo make install
etc., etc.
```

---

### Post by Acrosby on 2011-06-02
I am running 10.10, so it goes to places/downloads,,, also I tried this.


ashley@ashley-GA-MA790XT-UD4P:~$ Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
bash: Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO: Permission denied
ashley@ashley-GA-MA790XT-UD4P:~$

---

### Post by chili555 on 2011-06-02
It should be:```
ashley@ashley-GA-MA790XT-UD4P:~$ [COLOR="Red"]**cd**[/COLOR] Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
```I'll be away for about an hour, see you soon.

---

### Post by Acrosby on 2011-06-02
It doesn't see it, what am I doing wrong?? I even tried "cd ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO"

---

### Post by chili555 on 2011-06-02
[RANT]Far be it from me to second guess the great and powerful Ralink developers, but why, oh why, in the name of all that's Linux, would you send out a package compressed to bz2 that contains another package that needs to be de-compressed and it doesn't have a file extension telling the newbies what to do with the durned thing? Why, oh why???[/RANT]

Sorry about that, I've taken a few tranquilizers and had a bit of a rest and I feel better.

The second package with a name ending in DPO is also a compressed package like a zip or rar or something. Since it has no file extension, we can't tell what. Let's do a trick. Right click it and select Rename. Rename it to RT3572. Now right click it and select Extract Here. The folder 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO will magically appear! Now go back to the terminal and do:```
cd Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
```If the terminal now reads like:```
ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
```Then you know you are in the correct directory. Confirm by listing the contents of the directory:```
ls
```If you see, among other things, the Makefile, then you know you're ready to rock!

---

### Post by Acrosby on 2011-06-02
thanks for the tip, but,,,,

ashley@ashley-GA-MA790XT-UD4P:~$ sudo make install
[sudo] password for ashley: 
make: *** No rule to make target `install'.  Stop.
ashley@ashley-GA-MA790XT-UD4P:~$ cd Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
[email]ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ make
make -C tools
make[1]: Entering directory `/home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools'
/home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic-pae/build SUBDIRS=/home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
  CC [M]  /home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/rt3572sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic-pae'
[email]ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo make install
make -C /home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-28-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.35-28-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-28-generic-pae
make[1]: Leaving directory `/home/ashley/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux'
[email]ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo modprobe rt3572sta
[email]ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[email]ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ 





Ive tried reinstalling everything but still no luck. the wireless card works fine on my other os, win7 (I was set me up with a dual boot). I got excited there for a minute when all that installation was happening, any other ideas?
Acrosby

---

### Post by mcellius on 2011-06-03
> **gershy said:**
> I just spent a few hours today getting this to work on 11.04. All of  these steps are a compilation of various guides on the web. Hope this  helps someone!

[SIZE=3]1.)[/SIZE][INDENT]     Type [COLOR=Red]lsusb[/COLOR] in terminal; if using AE1000 you should see a line similar to this:
[/INDENT][INDENT]     ```
Bus 001 Device 002: ID [COLOR=Red]13b1:002f[/COLOR] Linksys AE1000 v1 802.11n [Ralink RT2870]

```[/INDENT][INDENT]     All you need to worry about is this bit:  ```
[COLOR=Red]13b1:002f[/COLOR]
```[SIZE=3]
[/SIZE][/INDENT][SIZE=3]2.)[/SIZE][INDENT] Download the [COLOR=Blue][RT3572USB]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXhMekEwTHpJM0wyUnZkMjVzYjJGa056RXhOamcyTXpRMk9DNWllakk5UFQweU1ERXhYekEwTWpkZlVsUXpOVGN5WDB4cGJuVjRYMU5VUVY5Mk1pNDFMakF1TUM1RVVFOD1D")[/COLOR] drivers
[/INDENT][SIZE=3]3.)[/SIZE][INDENT]Unpack the download
[/INDENT][INDENT]Navigate to:
 [COLOR=Silver]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/common
And open:
[COLOR=Blue]rtusb_dev_id.c[/COLOR]

Scroll down to the 
```
#endif /* RT2870*/
#ifdef RT35xx
```section of code

and add:
```
{USB_DEVICE(0x13b1,0x002f)}, /* Linksys AE1000 */
```Reference: [http://i.imgur.com/GHfRj.png](http://i.imgur.com/GHfRj.png)

[/INDENT][SIZE=3]4.)[/SIZE][INDENT]Navigate to: 
[COLOR=Silver]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/common/os
And open:
[COLOR=Blue]rt_linux.h[/COLOR]
Scroll down to line **1161** and **1162**
Alternatively: ctrl+f and type *usb_buffer*
Change
```
#define RTUSB_URB_ALLOC_BUFFER(_dev, _size, _dma)        [COLOR=SeaGreen]usb_buffer_alloc[/COLOR](_dev, _size, GFP_ATOMIC, _dma)
#define RTUSB_URB_FREE_BUFFER(_dev, _size, _addr, _dma)    [COLOR=SeaGreen]usb_buffer_free[/COLOR](_dev, _size, _addr, _dma)
```to:
```
#define RTUSB_URB_ALLOC_BUFFER(_dev, _size, _dma)        [COLOR=SeaGreen]usb__alloc_coherent[/COLOR](_dev, _size, GFP_ATOMIC, _dma)
#define RTUSB_URB_FREE_BUFFER(_dev, _size, _addr, _dma)    [COLOR=SeaGreen]usb_free_coherent[/COLOR](_dev, _size, _addr, _dma)
```[/INDENT][SIZE=3]5.)[/SIZE][INDENT]Navigate to:
[COLOR=Silver]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux
And open:
[COLOR=Blue]config.mk[/COLOR]
Change lines 14,17,32 to =y instead of =n

[/INDENT][SIZE=3]6.)[/SIZE][INDENT]Open the terminal
Change directory to: 
[COLOR=SlateGray]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
Once in that directory, type:
```
[COLOR=Red]make[/COLOR]
```After it's done type:
```
[COLOR=Red]sudo make install[/COLOR]
```[/INDENT][SIZE=3]7.)[/SIZE][INDENT]After installation type:
```
[COLOR=Red]sudo modprobe rt3572sta[/COLOR]
```After about 10 seconds, you should be prompted to enter your WiFi password.
[/INDENT]

This worked!  Well, I still have to respond to pop-up login requests every few minutes, but otherwise it's fine.  (Yeah, that'll get annoying after awhile, I know.  And actually, now that I've disconnect and re-connected, it isn't doing that anymore.  Woo hoo!)

However, in the RT3572 download, the extraction did not - as someone else reported, too - create a /common/os folder, so I never edited the rt_linux.h file (I'm running Natty with its kernel, and I read in a couple of the posts that it wasn't necessary to edit that file).

If I might make one suggestion: it needs to be stressed that the file to be downloaded from Ralink's site is RT3572USB and NOT RT2870USB, despite the fact that your AE 1000 is identified in lsusb as being a Ralink 2870.  It's easy to miss that, as I did at first, too.

Thanks so much for the tremendous amount of patient and kind work that has been provided here!

---

### Post by chili555 on 2011-06-03
> **Acrosby said:**
> thanks for the tip, but,,,,

/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo modprobe rt3572sta
[email]ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[email]ashley@ashley-GA-MA790XT-UD4P:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ 

Ive tried reinstalling everything but still no luck. the wireless card works fine on my other os, win7 (I was set me up with a dual boot). I got excited there for a minute when all that installation was happening, any other ideas?
AcrosbyLet's have a look at:```
lsusb
sudo modprobe rt3572sta
dmesg | grep -i rt3
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Acrosby on 2011-06-06
It's been over 5 minutes and still waiting for my wi fi input
Thanks 
Ash

---

### Post by Acrosby on 2011-06-06
> **Acrosby said:**
> It's been over 5 minutes and still waiting for my wi fi input
Thanks 
AshAnd the stick is plugged in. Sorry I didn't get back sooner, I was away for the weekend

---

### Post by chili555 on 2011-06-07
Let's have a look at:```
lsusb
```I wonder why this driver doesn't grab your device and start running.

---

### Post by Acrosby on 2011-06-07
ashley@ashley-GA-MA790XT-UD4P:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ashley@ashley-GA-MA790XT-UD4P:~$

What if I entered  or changed the wrong code?

---

### Post by chili555 on 2011-06-07
Now let's see:```
modinfo rt3572sta | grep -e version -e 002F
```Thanks.

---

### Post by Acrosby on 2011-06-07
ashley@ashley-GA-MA790XT-UD4P:~$ modinfo rt3572sta | grep -e version -e 002F
version:        2.5.0.0
srcversion:     D7F6D97B756AC2B0CFC20A9
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
vermagic:       2.6.35-28-generic-pae SMP mod_unload modversions 686 
ashley@ashley-GA-MA790XT-UD4P:~$

---

### Post by chili555 on 2011-06-07
Dr. Chili will now begin exploratory surgery. We are going to create a big text file and zip it and post as an attachment to your reply using the paperclip tool at the top of the reply box. Open a terminal and do:```
sudo modprobe rt3572sta
dmesg > acro.txt
sudo cat /var/log/syslog | tail -n25 >> acro.txt
rfkill list all >> acro.txt
lsmod >> acro.txt
zip acro.zip acro.txt
```You will find the acro.zip file in your user directory. Please attach it to your reply.

---

### Post by Acrosby on 2011-06-08
Doc,

I hope this helps.

Ash

---

### Post by Acrosby on 2011-06-08
I wonder why we can't just download the driver with the changes already made ? It seems to me that I am not the only one who has bought a AE1000

---

### Post by chili555 on 2011-06-08
> **Acrosby said:**
> I wonder why we can't just download the driver with the changes already made ? It seems to me that I am not the only one who has bought a AE1000Not everyone uses Network Manager or Ubuntu. A downloadable source code file needs to be a one size fits Ubuntu, Suse, Slackware, Mint, etc. The instructions in the README aim to allow each of them to customize the file for any distribution across a wide variety of uses.

---

### Post by chili555 on 2011-06-08
> **Acrosby said:**
> Doc,

I hope this helps.

AshWe see that the driver rt3572sta wasn't loaded automatically; it was loaded when you modprobed it. Can you confirm that the device was inserted when you ran all these tests? Let's try another test. Please do:```
sudo su
echo rt3572sta >> /etc/modules
exit
```Make sure the device is inserted. Make sure the ethernet cable is detached. Reboot. Now run:```
dmesg > acro2.txt
cat /etc/network/interfaces >> acro2.txt
sudo cat /var/log/syslog | grep etwork | tail -n25 >> acro2.txt
rfkill list all >> acro2.txt
lsmod >> acro2.txt
zip acro2.zip acro2.txt
```Then hook up the ethernet cable and attach the file to your reply.

---

### Post by Acrosby on 2011-06-08
I think this is the file you mean, let me know if it isn't?
Ash

---

### Post by chili555 on 2011-06-08
So far, so good. You missed the dmesg part. Could I get that one, too?```
dmesg > acro3.txt
zip acro3.zip acro3.txt
```

---

### Post by Acrosby on 2011-06-08
hope this helps
Ash

---

### Post by chili555 on 2011-06-08
> [    3.936040] hub 5-0:1.0: unable to enumerate USB device on port 3I found that in dmesg. The next line is:> [   [COLOR="Red"]15.6[/COLOR]64541] end_request: I/O error, dev fd0, sector 0The second message itself, that there is an error in fd0, a floppy disk device, is not significant. What is significant is that from the USB problem to the resumption of boot activities took 12 seconds, the same as 12 years or so in human terms!!! I wonder if either the wireless device or the USB port is electrically defective. That would go a long way to explain why the device and the driver don't marry, connect and start downloading pictures from grandpa.

Does your Linksys work elsewhere? On another operating system? On another computer?

Please remove the device and reboot. Look for the same message with:```
dmesg | grep enumerate
```If it appears, it will probably be at a different time, say 3.91xxx or 3.97xxx. Reboot with the device in a different USB port and look again. Report your findings here.

You might also look at the Ralink lines in:```
sudo lsusb -vv
```[http://askubuntu.com/questions/7704/unable-to-enumerate-usb-device](http://askubuntu.com/questions/7704/unable-to-enumerate-usb-device)> Update: I found a computer which had the same issues, it was caused by a faulty usb port on the computer and it was confirmed to be the hardware since no matter what software was run on it it caused the same errors. This port caused all sorts of issues since a hp printer was plugged into it which needed firmware and the faulty usb port was corrupting the firmware sent to the printer causing it to start having issues with any machine it was plugged into.

---

### Post by Acrosby on 2011-06-08
I'll boot into win7 and see if it is still working

---

### Post by Acrosby on 2011-06-08
Yes Doctor, 
I tried to fire it up in Windows7 ,basically the same issue. A problem with my ports. I believe my motherboard is still warranted so I will take it into the shop and get them to fix it on windows7 then it should work on my Ubuntu10.10. Thank you for all the time you spent helping me out. It is greatly appreciated. I will post back here when I get the machine back from the shop.
Thank you,
Ash

---

### Post by chili555 on 2011-06-08
Sorry to hear about your hardware issue, but I'm glad to hear I've not lost my mojo. If you need help when the replacement arrives, please post back.

---

### Post by judderwocky on 2011-06-10
this wireless card is not worth the effort. i'm taking it back.

---

### Post by Acrosby on 2011-06-10
Doctor,

A friend has a wireless Airlink 101, so we tried it on this computer. the results were, my computer sees the wireless adapter in Ubuntu10.10, and shows the networks (mine, the neighbors, ETC) but when I try to connect to mine I enter the password and it tries, but doesn't connect. the odd thing is after installing the driver in my Windows 7 OS, it doesn't work at all on the other side?

More perplexed than ever,

Ash

---

### Post by chili555 on 2011-06-10
Is the Airlink the same device or what?```
lsusb
lspci -nn
```

---

### Post by Acrosby on 2011-06-10
ashley@ashley-GA-MA790XT-UD4P:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ashley@ashley-GA-MA790XT-UD4P:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part [1002:5958]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A) [1002:5978]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A) [1002:597a]
00:0a.0 PCI bridge [0604]: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F) [1002:597f]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Cedar PRO [Radeon HD 5450] [1002:68f9]
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
02:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
02:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
04:06.0 Modem [0703]: Motorola SM56 Data Fax Modem [1057:3052] (rev 04)
04:0e.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
ashley@ashley-GA-MA790XT-UD4P:~$ lspci -nn

---

### Post by Acrosby on 2011-06-10
I have the adapter plugged in but also the ethernet wire plugged in right now

---

### Post by chili555 on 2011-06-10
It's a whole other device; it uses the module r8712u. I'd be happy to work on it in a new thread. Give me the link here and I'll hop over after supper.

---

### Post by Acrosby on 2011-06-10
[http://ubuntuforums.org/showthread.php?p=10925844#post10925844](http://ubuntuforums.org/showthread.php?p=10925844#post10925844)

---

### Post by lukemacneil on 2011-06-14
This is one of the finest threads I have ever read on any subject, ever. Very well done. I went through this process today and found that  the driver will drop stack faster than ... anyone who can drop anything drops something.

It's also interesting to note that even though it dumps, it does see the available access points, and try to connect to them.. at that point though, it requires a hard reboot.

---

### Post by tmeehan on 2011-06-19
I agree that this is one of the best threads I've seen in a long time.

For those setting up an AE1000 with Ubuntu 10.04 as of today, I've compiled what worked for me in the attached.  It's a compilation of many threads I reviewed before getting things to work and the many issues I and others encountered.

It was rather lengthy and I was concerned the formatting may not come through on the forum.

I hope this saves someone some time...

Cheers

---

### Post by ramina on 2011-06-21
> **chili555 said:**
> It's time to get your geek on. This will get a bit difficult, but I will try to explain everything carefully. If in doubt, stop and ask.
 
With your internet connection going, do:```
sudo apt-get install build-essential linux-headers-generic
```This assumes that, when you run:```
uname -r
```...that you are running a generic kernel. If in doubt, ask.
 
Next, go here and download 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar.bz2.
 
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
 
Detach your Linksys G.
 
By default, downloads go to a directory called Downloads. Open it and right-click the file and select 'Extract here.' Open the 2010_0915_RT3572_Linux_STA_v2.4.0.2 folder and then navigate to os/linux/config.mk and change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Change them from =n to =y. Proofread, save and close the text editor.
 
Next, edit /include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. ***DO NOT ***replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.
 
Now edit common/rtusb_dev_id.c. Add your device as follows:```
/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT2870
    {USB_DEVICE(0x148F,0x2770)}, /* Ralink */
    {USB_DEVICE(0x148F,0x2870)}, /* Ralink */
    {USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
    {USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
        [COLOR=blue]{USB_DEVICE(0x13B1,0x002F)}, /* Linksys */[/COLOR]
        --- snip ---
```It doesn't matter whether you add your device first, second, twelfth, etc. Proofread, save and close the text editor.
 
Open a terminal and do:```
make
```Note any errors and post them here. If there are warnings only and no errors, proceed.```
sudo make install
sudo modprobe rt3572sta
iwconfig
```Is your device running?
 
 
NO my device still not recognized??? Done everything you said.. pls help. thnx

---

### Post by chili555 on 2011-06-21
> **ramina said:**
> NO my device still not recognized??? Done everything you said.. pls help. thnxLet's see:```
lsusb
modinfo rt3572sta
iwconfig
```Thanks. I'll be here for an hour before my body and mind collapse.

---

### Post by ramina on 2011-06-21
> **chili555 said:**
> Let's see:```
lsusb
modinfo rt3572sta
iwconfig
```Thanks. I'll be here for an hour before my body and mind collapse.
 
 
sorry i just saw your message
 
 
lsusb even lists we have the driver and AE1000 v1 802.11n ralink 2870
 
I ran all of these what am i sopouse to look for?
 
 
iwconfig just shows no wireless extentions or ra0
 
p.s im running 11.04 ubuntu 64 bit machine
 
 
thanks for all your hardwork

---

### Post by chili555 on 2011-06-22
> lsusb even lists we have the driver and AE1000 v1 802.11n ralink 2870

I ran all of these what am i sopouse to look for?


iwconfig just shows no wireless extentions or ra0
The point of all this is just exactly that: *you* don't know what you're looking for; I do. If you post the data, I can probably tell what went wrong. Let's make it easier. Please post the usb.id from lsusb. Is it indeed 13b1:002f? If not, you have a different device or version and maybe this driver is not correct for it.

Next, let's see if the driver associates with the device; that is, if there is an alias in the driver for your usb.id:```
modinfo rt3572sta | grep 002F
```If there is an alias, then you did this change correctly:> Now edit common/rtusb_dev_id.c. Add your device as follows:
Code:

/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT2870
    {USB_DEVICE(0x148F,0x2770)}, /* Ralink */
    {USB_DEVICE(0x148F,0x2870)}, /* Ralink */
    {USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
    {USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
    [COLOR="Red"]{USB_DEVICE(0x13B1,0x002F)}, /* Linksys */[/COLOR]
        --- snip ---

Now, let's see if there is any error or problem when you load the module:```
sudo modprobe rt3572sta
```Any warnings, errors or problems? Are there any error messages here?```
dmesg | grep rt3
```I understand it's difficult to post from a not-connected computer; however, you can always copy and paste from the terminal window and transfer it to a text document and transfer that to a USB key to whatever computer you are answering these posts from.

"What am I sopouse to look for" doesn't help a bit.

---

### Post by ramina on 2011-06-22
> **chili555 said:**
> The point of all this is just exactly that: *you* don't know what you're looking for; I do. If you post the data, I can probably tell what went wrong. Let's make it easier. Please post the usb.id from lsusb. Is it indeed 13b1:002f? If not, you have a different device or version and maybe this driver is not correct for it.
 
Next, let's see if the driver associates with the device; that is, if there is an alias in the driver for your usb.id:```
modinfo rt3572sta | grep 002F
```If there is an alias, then you did this change correctly:Now, let's see if there is any error or problem when you load the module:```
sudo modprobe rt3572sta
```Any warnings, errors or problems? Are there any error messages here?```
dmesg | grep rt3
```I understand it's difficult to post from a not-connected computer; however, you can always copy and paste from the terminal window and transfer it to a text document and transfer that to a USB key to whatever computer you are answering these posts from.
 
"What am I sopouse to look for" doesn't help a bit.
 
 
 
 
Hello, here is what i got after each command you told me to do.
 
 
 
alias        usb:v13b1p002fd*dc*dsc*dp*ic*isc*ip*
 
alias        usb:v07AAp002fd*dc*dsc*dp*ic*isc*ip*
 
 
 
sudo modprobe just asked me for my user password and did nothing
 
 
 
 
dmesg | grep rt3 also did nothing
 
 
 
in lsusb i have 13b1 and 0x002F
 
 
 
thanks doc

---

### Post by MeeMaw on 2011-06-22
I'm sure it would be MUCH MORE useful to chili555 if you would actually post the output of each command by copy & pasting......

(I'm just saying...)

:/

---

### Post by ramina on 2011-06-22
> **MeeMaw said:**
> I'm sure it would be MUCH MORE useful to chili555 if you would actually post the output of each command by copy & pasting......
 
(I'm just saying...)
 
:/
 
 
 
 
 
 
im a linux nooooobbb idk how ):
 
 
sorry doc if i make you mad

---

### Post by chili555 on 2011-06-22
> **ramina said:**
> im a linux nooooobbb idk how ):
 
 
sorry doc if i make you madI'm not mad at all. Please read my previous post:> I understand it's difficult to post from a not-connected computer; however, you can always copy and paste from the terminal window and transfer it to a text document and transfer that to a USB key to whatever computer you are answering these posts from.
Please see attached.

You can also send the terminal output straight to a text document; I bet Meemaw doesn't even know this little trick. We'll do so in the next set of tests:```
lsmod | grep -e rt2 -e rt3 > ramina.txt
dmesg | grep -e rt2 -e rt3 >> ramina.txt
lsusb >> ramina.txt
```In your user directory, you will find a text file called ramina.txt. Insert a USB key in your computer. Borrow one from a friend if needed. Drag and drop the text file to the USB key and post it here, either by copying and pasting or as an attachment to your reply using the paperclip tool at the top of the reply box.

If you have trouble or don't understand, please don't be shy to ask. Meemaw or I will be happy to help.

---

### Post by mcellius on 2011-06-22
> **ramina said:**
> sorry i just saw your message
 
 
lsusb even lists we have the driver and AE1000 v1 802.11n ralink 2870
 
I ran all of these what am i sopouse to look for?
 
 
iwconfig just shows no wireless extentions or ra0
 
p.s im running 11.04 ubuntu 64 bit machine
 
 

I followed the instructions earlier in this thread and got my AE1000 to work just fine, but I was running the 32-bit Ubuntu 11.04.  I later reinstalled Ubuntu 11.04, but used the 64-bit version, and since then the AE1000 hasn't worked.  I followed all of the instructions again, but never had any luck.  (Fortunately, it was a desktop computer that also had an Ethernet connection, so it didn't really matter: as someone new to Linux, I was doing it to learn.)

Could that be it, though?  The AE1000 doesn't work - or the Ralink drivers don't work - with 64-bit Ubuntu 11.04?

---

### Post by chili555 on 2011-06-22
> or the Ralink drivers don't work - with 64-bit Ubuntu 11.04?That's exactly what I think. I believe I've read that if you email Ralink they will send you a 64-bit and latest kernel version. If you do so, post back and we'll figure out how to make it available to others. Be sure to tell them your kernel version:```
uname -r
```

---

### Post by ramina on 2011-06-22
> **chili555 said:**
> That's exactly what I think. I believe I've read that if you email Ralink they will send you a 64-bit and latest kernel version. If you do so, post back and we'll figure out how to make it available to others. Be sure to tell them your kernel version:```
uname -r
```
 
 
 
 
 
ok befor i do that
 
 
doc, thank you SO much for being a huge help to the ubuntu fourms

---

### Post by IMSargon on 2011-06-26
The procedure by Chili555 worked fine for me.

I downloaded 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO.bz2
I'm running 32-bit Ubuntu 11.04
I tried compiling and installing without making the source code changes, but it didn't work. I then tried again with the changes as described by Chili555, and everything worked.

---

### Post by sandman887 on 2011-07-08
Ok. I have edited the .c files, but not the .h file, because I have 2.6.32-32-generic. 

I installed this, but it's not working yet. 

lsmod | grep rt2 produces no output
dmesg | grep rt2 produces no output
lsusb produces this line:
```
Bus 001 Device 004: ID 13b1:002f Linksys 

```

iwconfig says no extensions. 

Any ideas?

Ubuntu 10.04 LTS Lucid Lynx
2.6.32-32-generic

Anything else you need?

---

### Post by chili555 on 2011-07-08
> lsmod | grep rt2 produces no output
dmesg | grep rt2 produces no outputHow about:> lsmod | grep rt3
dmesg | grep rt3
modinfo rt3572sta | grep 002FThanks.

---

### Post by sandman887 on 2011-07-08
None of the first two produce any output. 

Here is what I installed: 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2

Here is the output from modinfo rt3090sta:
```
filename:       /lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt3090/rt3090sta.ko
version:        2.1.0.0
license:        GPL
description:    RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
srcversion:     B604A3D317238CA9B81AC1A
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
staging:        Y
vermagic:       2.6.32-32-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```

I forgot to mention that I even modprobed the module into the kernel, didn't work, so I rebooted just to see if it would work, for some reason, and of course it didn't.

---

### Post by chili555 on 2011-07-08
> Here is what I installed: 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.2_DPO.bz2Then you downloaded and compiled the wrong driver.

[http://ubuntuforums.org/showpost.php?p=10163301&postcount=7](http://ubuntuforums.org/showpost.php?p=10163301&postcount=7)

You need rt3572sta, not rt3090 and not rt3070.

---

### Post by sandman887 on 2011-07-08
Ok, I just downloaded it and edited the correct files, and when I did make (without sudo), this is what I got:
```
/bin/sh: Syntax error: word unexpected (expecting ")")
make: *** [build_tools] Error 2

```

---

### Post by sandman887 on 2011-07-08
I found out what the problem was. The .bz2 file did not extract normally on the command line, so I had to use the gui, which extracted it to a file of the same name, with (2) at the end of the filename. 

Once I moved the original file, and removed the "(2)", I ran
```
sudo make clean
```

and then
```
make
```

This was the erroneous result I got:
```
make[2]: *** [/home/shredder/Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/shredder/Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
make: *** [LINUX] Error 2

```

---

### Post by chili555 on 2011-07-09
That's it? "Error 1?" Is there no further explanation? Can you confirm you have linux-headers (matching your kernel version) installed as well as build-essential?

---

### Post by sandman887 on 2011-07-09
They're already installed, and they're also the current version.

I'm adding this:
```
shredder@technodrome:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for shredder: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

As for the error message, the output is just as I posted.

---

### Post by chili555 on 2011-07-10
> make[2]: *** [/home/shredder/Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/shredder/Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
make: *** [LINUX] Error 2So you typed 'make' and pressed Enter and those few lines are all that came back? Please try again:```
cd Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
make clean
make > make.txt
zip make.zip make.txt
```Attach the file make.zip to your reply using the paperclip tool at the top of the reply box.

I am confident there were lines preceeding these you posted; we need to know what went wrong in order to know what to fix.

---

### Post by sandman887 on 2011-07-10
I don't remember what I did that last time...I was really tired. I may have made a mistake. 

Anyway, I got the rt3572 driver installed. 

```
shredder@technodrome:~$ lsmod | grep rt3
rt3572sta             569273  0 

```

```
shredder@technodrome:~$ dmesg | grep rt3
shredder@technodrome:~$ 

```

I modprobed it into the kernel, however, iwconfig still says no extensions, and when my ethernet cable is unplugged, all it shows when I left click the networking icon on my panel is :
<grayed-out>
Wired connections
disconnected</grayed-out>
VPN connections >

I just typed that so you would know that I know I'm not connected to any network. Normally, if a wireless device is functioning, it will show any wireless networks in the area that it detects. Is it possible this wireless adapter is defective?

---

### Post by chili555 on 2011-07-10
> Is it possible this wireless adapter is defective?It's possible but unlikely in my opinion.

It's very hard to troubleshoot when I get no information in return. This doesn't help, either; I asked:> How about:
Quote:
lsmod | grep rt3
dmesg | grep rt3
modinfo [COLOR="Red"]rt3572sta[/COLOR] | grep 002F Your reply:> Here is the output from modinfo [COLOR="Red"]rt3090sta[/COLOR]:
Code:

filename:       /lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt3090/rt3090sta.ko
version:        2.1.0.0
license:        GPL
description:    RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>I am very sorry I have been unable to help more.

---

### Post by sandman887 on 2011-07-10
At that time, I couldn't execute the command you wanted, because I didn't have the driver installed yet.

Here's the output of the command.
```
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*

```

---

### Post by sandman887 on 2011-07-13
I'm just taking this back. I've decided just to use ethernet. Saves me money.

---

### Post by Elfyy on 2011-07-16
Do you have an update with the 2.5.0? I tried doing your instructions and when I get to the make part and hit ls it just lists DOcuments pictures desktop.... Any help? thanks!

---

### Post by chili555 on 2011-07-16
I'm not sure which of several posters you are addressing; however:> hit ls it just lists DOcuments pictures desktop.... Any help? thanks!Then you are not in the correct directory. Where did you download the file that you extracted? To your desktop? Then preceed 'make' with:```
cd Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
```Now list the files:```
ls
```Is one of the files listed called Makefile? If so, please proceed:```
make
sudo make install
sudo modprobe rt3572sta
```Post back if you get stuck.

---

### Post by ghat on 2011-07-16
hi

I have not had any good luck with the latest (2.5.0.0) drivers on lucid (which is still the current  LTS version.. I am using 2.4.02 as in the initial posts... 

the following file (attached) 

669396  2010_0915_RT3572_Linux_STA_v2.4.0.2-ae1K.tar.bz2 ( ls -l ) 
e836b5b5bc470e94ae6bb0c079f77bcc  2010_0915_RT3572_Linux_STA_v2.4.0.2-ae1K.tar.bz2 (md5sum)

has all the changes needed for it to use with lucid, and the OS's wpa_supplicant, for the Cisco/Linksys AE1000.

Ghat

PS: Just untar the file, cd into it, and then its just
```

make 
sudo make install

(reboot OR)

sudo /etc/init.d/networking stop
sudo rmmod rt3572sta
sudo lsmod | grep  rt # (check if it really removed any old modules)
sudo modprobe rt3572sta
sudo /etc/init.d/networking start

```You will have to do this procedure every time you do a apt-get dist-upgrade and the kernel is replaced by a new one... 
Working for > 1 year now.. on lucid/x86_64

---

### Post by Elfyy on 2011-07-16
Its on desktop And still wont work....

kyle@kyle-CX2620:~$ cd Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO
bash: cd: Desktop/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO: Not a directory
kyle@kyle-CX2620:~$ ls
Bliss.bmp  Documents  examples.desktop  Pictures  Templates
Desktop    Downloads  Music             Public    Videos

---

### Post by Elfyy on 2011-07-16
NOt sure if this matters but just to give you more info, I have the .dpo on my desktop and the .dpo.bz2 on my desktop. Both look like boxes opening....Is this how its supposed to be?

---

### Post by Elfyy on 2011-07-16
Wait! I just dragged all the individual file onto the desktop and make file worked but when I :

kyle@kyle-CX2620:~/Desktop$ sudo modprobe rt3572sta
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.


Still not working....

---

### Post by chili555 on 2011-07-16
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.Let's take care of this first. See what's inside it:```
cat /etc/modprobe.d/blacklist
```We will either add it to blacklist.conf or, if it's no longer valid, remove it entirely. Please run and post:```
lsusb
lsmod | grep rt3
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Can you confirm you did this step?> Now edit common/rtusb_dev_id.c. Add your device as follows:
Code:

/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT2870
	{USB_DEVICE(0x148F,0x2770)}, /* Ralink */
	{USB_DEVICE(0x148F,0x2870)}, /* Ralink */
	{USB_DEVICE(0x07B8,0x2870)}, /* AboCom */
	{USB_DEVICE(0x07B8,0x2770)}, /* AboCom */
        [COLOR="RoyalBlue"]{USB_DEVICE(0x13B1,0x002F)}, /* Linksys */[/COLOR]
        --- snip ---

It doesn't matter whether you add your device first, second, twelfth, etc. Proofread, save and close the text editor.
And how about this?> Open the 2010_0915_RT3572_Linux_STA_v2.4.0.2 folder and then navigate to os/linux/config.mk and change 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Change them from =n to =y. Proofread, save and close the text editor.If not, please do so and we'll need to rebuild the driver.

---

### Post by Elfyy on 2011-07-16
THANK YOU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! ITS WORKS!!!! Your the man!!!!!!!! I just had to restart it again!!!

---

### Post by xnatex21 on 2011-07-19
Thank you. It worked perfectly and was much easier than I thought. 

The only thing worth noting for me was
1)The ralink package has a new date in the file name
2)linux_rt.h is now named rt_linux.h

:)

Pretty easy to figure those out but you never know how literal someone is going to be.

Thanks again!!!!!!

---

### Post by akavir on 2011-07-21
I'm trying to make this work on Linux Mint 11(64-bit).  I have followed this guide, and network connections now sees wireless networks in range.  But when I connect and type my WPA key, it just endlessly tries to connect and eventually crashes my system.  I had this adapter working with a similar guide on Ubuntu 10.10.  Now I'm just frustrated and upset.

---

### Post by ugmoe2000 on 2011-07-22
Write-up of the process available here: [http://confignewton.com/?p=104](http://confignewton.com/?p=104)

---

### Post by akavir on 2011-07-22
@ugmoe2000 THANK YOU SO MUCH!! Your guide worked amazingly. (My only concern is something on your website caused two of my computer to lag, a dual core i5, and an octocore i7!  Might want to investigate.) The only difference between it and the one here is including the old driver.  That was my problem.  To all who have problems with this DO NOT USE THE DRIVER DATED APRIL 2011, the 2.5.0.0 DRIVER!!  IT DOES NOT WORK AND WILL CRASH YOUR DESKTOP!!  Thanks again, this means so much to me!

---

### Post by ugmoe2000 on 2011-07-23
@akavir -- the lagging was caused by the secret scripting rooting your boxes in the background. Now they'll be zombies in my DoS attack against all companies that manufacture boxer-briefs... j/k I'll see if I can reproduce the lag elsewhere, thanks for the tip!

---

### Post by akavir on 2011-07-24
@ugmoe2000 lol that's awesome.  I think I'm going to post the fixed driver on my website, so all people have to do is download the linux header package and make!  I'll probably upload tommorow and post a link here and in the reply on your how-to.  Thanks again!

---

### Post by fu9ar on 2011-07-24
Ubuntu 11.04

linux-headers-2.6.38-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[EMAIL="fu9ar@fubar-mac-****:%7E/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO"]fu9ar@fubar-mac-****:~/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/EMAIL] $ make
make -C tools
make[1]: Entering directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools'
/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools/bin2h
make: /home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO: Command not found
make: *** [build_tools] Error 127
[EMAIL="fu9ar@fubar-mac-****:%7E/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO"]fu9ar@fubar-mac-****:~/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/EMAIL] $

:confused: help?

---

### Post by chili555 on 2011-07-24
> **fu9ar said:**
> Ubuntu 11.04

linux-headers-2.6.38-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[EMAIL="fu9ar@fubar-mac-****:%7E/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO"]fu9ar@fubar-mac-****:~/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/EMAIL] $ make
make -C tools
make[1]: Entering directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools'
/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools/bin2h
make: /home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO: Command not found
make: *** [build_tools] Error 127
[EMAIL="fu9ar@fubar-mac-****:%7E/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO"]fu9ar@fubar-mac-****:~/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/EMAIL] $

:confused: help?Have you installed *build-essential*?

---

### Post by fu9ar on 2011-07-24
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[email]fu9ar@fubar-mac-****:~/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email] $ 

:???: yes

---

### Post by chili555 on 2011-07-24
Please try:```
sudo su
make clean
make
make install
modprobe rt3572sta
exit
```Post back any errors; warnings are OK.

---

### Post by fu9ar on 2011-07-24
```
fu9ar@fubar-mac-****:~/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO $ sudo su
root@fubar-mac-****:/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO # make clean
cp -f os/linux/Makefile.clean os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /os/linux'
Makefile:1: /home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO: No such file or directory
Makefile:1: /os/linux/config.mk: No such file or directory
make[1]: *** No rule to make target `/os/linux/config.mk'.  Stop.
make[1]: Leaving directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /os/linux'
make: *** [clean] Error 2
root@fubar-mac-****:/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO # make
make -C tools
make[1]: Entering directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools'
/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /tools/bin2h
make: /home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO: Command not found
make: *** [build_tools] Error 127
root@fubar-mac-****:/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO # make install
make -C /home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO /os/linux -f Makefile.6 install
make: *** /home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO: No such file or directory.  Stop.
make: *** [install] Error 2
root@fubar-mac-****:/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO # modprobe rt3572sta
FATAL: Module rt3572sta not found.
root@fubar-mac-****:/home/fu9ar/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO # 


```

---

### Post by chili555 on 2011-07-24
> Makefile:1: /os/linux/[COLOR="Red"]config.mk[/COLOR]: No such file or directoryWhat?? Did you remove it instead of amending it? Do you still have the tar.bz2? Can you ditch the folder you have now and start over?

---

### Post by fu9ar on 2011-07-24
yeah it's still there ./os/linux/config.mk

I changed the WPA_SUPPLICANT settings by hand, there is a root owned Makefile in the ./os/linux directory for some reason...

```
# Declare the contents of the .PHONY variable as phony.  We keep that
# information in a variable so we can use it in if_changed and friends.
.PHONY: $(PHONY)

```

wha? :confused:

---

### Post by fu9ar on 2011-07-24
I never got a .tar.bz2

The archive was packaged as a DPO.bz2, but the graphical archive manager was able to deal with it without any hassle.

I'd rather not start over, that would be counterproductive. I've been banging my head against this wall for about a week and a half now with no more success...

---

### Post by chili555 on 2011-07-24
I just built it on my system, also 2.6.38-10 in three minutes from a cold start. I guess that *is* counter-productive.

I don't know why the Makefile won't find and use what is right there in front of you. I believe your file is somehow corrupted and I have given you my suggestion.> # Declare the contents of the .PHONY variable as phony.  We keep that
# information in a variable so we can use it in if_changed and friends.
.PHONY: $(PHONY)I have none.

---

### Post by fu9ar on 2011-07-24
Alright, I'll see what I can do from a cold start. #-o

---

### Post by fu9ar on 2011-07-24
Compiling now, I didn't edit the header file properly.  Thanks for the help chili555.

---

### Post by fu9ar on 2011-07-24
Posting from the Wi-Fi.

Thanks again for the help.

---

### Post by chili555 on 2011-07-24
Awesome! Glad to hear you're all set!

---

### Post by akavir on 2011-07-25
I've got the solution to the AE 1000 driver that allows you to cut this install guide in half, and not scare newbies from editing driver files.  I've made the necessary changes to the driver and uploaded it with instructions on my website at [http://i2productions.com/lir/?p=228](http://i2productions.com/lir/?p=228) Bear in mind I've only posted the most basic easy to use guide, but the troubleshooting on this thread can still prove extremely helpful if you run into issues.  The first person to try it, please post here or in the comments on my blog to let me know if it worked for you.  I've tested it myself with no issues.

---

### Post by PaLmeTTo_X on 2011-08-18
> **akavir said:**
> I've got the solution to the AE 1000 driver that allows you to cut this install guide in half, and not scare newbies from editing driver files.  I've made the necessary changes to the driver and uploaded it with instructions on my website at [http://i2productions.com/lir/?p=228](http://i2productions.com/lir/?p=228) Bear in mind I've only posted the most basic easy to use guide, but the troubleshooting on this thread can still prove extremely helpful if you run into issues.  The first person to try it, please post here or in the comments on my blog to let me know if it worked for you.  I've tested it myself with no issues.

Worked like a charm :) thx

---

### Post by mcellius on 2011-08-30
akavir,

I used what you posted on your website and it worked on my 64-bit Ubuntu, which I had not been able to get working before.  I had to reboot twice (weird) but after that everything worked just fine.  Otherwise it was quick and easy.

Thanks!

---

### Post by PowerportTech on 2012-01-05
The old site has um expired and is gone. 
I made the changes to the files again and put them up on my web site that is not going anywhere.
[http://powerport.webs.com/linuxubuntu.htm](http://powerport.webs.com/linuxubuntu.htm)
It has instructions on how to install and the password to open the zip

---

### Post by crosstie69 on 2012-01-22
Thank you all very much. I have been trying to run ubuntu from a cd to try it out for 2 days now and could not get my usb wireless dongle to work. I have been rebooting into windows and back into ubuntu over and over reading all these different instructions to no avail. Finally got to this last part and like magic, it is working.
It was a piece of cake.

Thanks again,

Tyler

---

### Post by LoserDude27 on 2012-01-27
Sorry to revive an old thread, but I'd like to jump in here and say thanks to chili and everyone who helped out!

I FINALLY got my AE1000 to work on 11.10 64-bit.  I never had any trouble installing the driver, but I kept getting asked the password in order to connect over and over and over and... over....

Eventually (no changes to anything - just kept pressing connect whenever the Network box came up), it worked.

This is really strange to me, but I guess persistence won in the end.

EDIT: Well, it looks like I'm still out of luck.  After about an hour, my wireless disconnected on its own and now it's back to asking me repeatedly for authentication.  Does anyone have any ideas for how to fix this??

---

