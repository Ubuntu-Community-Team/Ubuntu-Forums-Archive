---
title: "Getting the linksys wusb600n to work!"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by mick d on 2010-09-23
**My hair is almost gone now :( lol, hell bent on getting this thing to work. I hope BabyStuey  doesn't mind me posting this, seems to have everyone up and running but me. Can't get past the first step. Anyone else having problems?**
   
 				 				    
 			
					 	
	 	 	 		 		 			 			 				[IMG]http://static.linuxquestions.org/questions/images/icons_lq/icon14.gif[/IMG] 				**WUSB600N v2 Quickstart Guide for Linux** 			
 			 			 		 		  		   		[SIZE=3]A  present for everyone having trouble with the Cisco/Linksys Wireless-N  USB Network Adapter with Dual-Band Version 2 (aka WUSB600N v2)! [/SIZE]

**_NOTE_**: The code for the Ralink driver is currently NOT  64-bit clean, so any success compiling and installing on a 64-bit kernel  (amd64, x86_64, etc.) is pure fluke. If anyone has any luck getting the  adapter to work in a 64-bit environment, please let me know! These  instructions are proven only for 32-bit environments.

**_NOTE_**: These were the steps required to install the driver  on a system running Debian GNU/Linux 2.6.26-2-686, installed from the  5.0.4 (lenny) i386 image available at: [http://www.debian.org/CD/](http://www.debian.org/CD/)

They were revised to be clearer for users running different  distributions, including Ubuntu and Fedora. Others may require minor  tweaks, but should work as well. 

Additional Tests Performed: 

Fedora 12 (2.6.31.5-127.fc12.i686.PAE)
Installed from: Desktop Edition i686 Live CD
[http://download.fedoraproject.org/pu...-i686-Live.iso]("http://download.fedoraproject.org/pub/fedora/linux/releases/12/Live/i686/Fedora-12-i686-Live.iso")
Result: EASY! No added packages were required. Only requires you compile  and install the driver - no additional tweaks necessary. 

Ubuntu 10.04 Lucid Lynx (2.6.32-21-generic)
Installed from: PC (Intel x86) desktop CD image, ubuntu-10.04-desktop-i386.iso
[http://www.ubuntulinux.org/getubuntu/download](http://www.ubuntulinux.org/getubuntu/download)
Result: Pretty easy. No added packages were required. Follow the instructions and it should work.

**_NOTE_**: pico and nano are command-line text editors. If nano  doesn't work in the commands below, try pico. You can always link one  to the other by making a link:  	Code:
 	# ln /usr/bin/nano /usr/bin/pico 
 which will run nano whenever you (accidentally) type pico.

**_NOTE_**: Ubuntu users, please read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for information running commands as the super-user.

**_NOTE_**: Fedora users are able to ignore the prerequisites,  perform Steps 0 through 6, 11 and 12, skipping steps 7 through 10  completely. 


[CENTER][B][SIZE=6][COLOR=Blue]WUSB600N v2 
_Quickstart Guide for Linux_[/COLOR][/SIZE][/B][/CENTER]

**Debian Prerequisites (mostly precautionary): **
- Plug into a wired connection and do a full update with System > Administration > Update Manager.
- Load Synaptic Package Manager 
- You will have have "linux-image-${VERSION}" installed
- ...where ${VERSION} is the output from the command `uname -r`. For example: linux-headers-2.6.26-2-686. 
- Make sure you have "linux-headers-${VERSION}" installed
- Make sure you have "linux-source-${VERSION}" installed
- Install "build-essential" (and also possibly "kernel-package",  "kbuild", "linux-kbuild-${VERSION}", "linux-support-${VERSION}", though I  doubt if these were actually required)


**Step 0.** 
Stop pretending ndiswrapper will work reliably! lol. 
[B]
Step 1.[/B] 
Download the correct chipset driver from Ralink: [INDENT]- [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
- You need RT**3572**USB 2.3.0.0 (12/22/2009) or similar
- **_NOT_** RT2870USB (This is for Version 1 only!)
[/INDENT]**Step 2. **
Unpack the tarball {DATE}_RT3572_LinuxSTA_{VERSION}.tar.bz2 to a  location where you can find it (home folder, Desktop, etc.) All paths  listed below are in reference to the folder you just unpacked, for  example ${BASE} actually refers to the folder:  "/home/username/Desktop/2009_1214_RT3572_LinuxSTA_V2.3.0.0/" (or  similar)

**Step 3.** 
From the command line, run lsusb. You should get some output that looks like this: [INDENT]"ID 1737:0079 Linksys WUSB600N Wireless-N USB Network Adapter with Dual-Band ver. 2"
[/INDENT]**Step 4.** 
- Open the file ${BASE}/common/rtusb_devid.c
- Line 103 shows the device id for WUSB600N Version 1: [INDENT]{USB_DEVICE(0x1737,0x0071)}, /* Linksys WUSB600N */[/INDENT]- We need to tell the driver to work with Version 2. 
- At line 119, add (which should match your output from Step 3):  [INDENT]{USB_DEVICE(0x1737,0x0079)}, /* Linksys WUSB600N v2 */[/INDENT]- Like so: 

 	Code:
 	#ifdef RT35xx 	{USB_DEVICE(0x148F,0x3572)}, /* Ralink 3572 */ 	... 	{USB_DEVICE(0x167B,0x4001)}, /* 3572 */ 	{USB_DEVICE(0x1737,0x0079)}, /* Linksys WUSB600N v2 */ #endif // RT35xx // 	{ }/* Terminating entry */ 
**Step 5. **
As per the ${BASE}/README_STA file's instructions, change the two values in ${BASE}/os/linux/config.mk from =n to =y:
- HAS_WPA_SUPPLICANT=y 
- HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

**Step 6. ** --- **more on this step below in post #13.**
Compile the driver: 
- cd to the driver's home folder ${BASE}[INDENT]
$ cd ${BASE}
$ make[/INDENT]- Deal with any missing package and/or configuration issues that may be displayed. 

- Once the driver compiles correctly, install it as the superuser: [INDENT]$ sudo make install[/INDENT]**OR **[INDENT]$ su 
# make install[/INDENT]**Step 7. **
If you scroll waaaay to the bottom of ${BASE}/README_STA, you'll see  some confusing instructions. What they are trying to say is: 
- As the superuser, open /etc/modules[INDENT]$ sudo nano /etc/modules[/INDENT]**OR** [INDENT]$ su
# nano /etc/modules [/INDENT]- In Ubuntu, add the lines:
	[INDENT]rt3572sta     # Ubuntu only!
alias ra0 rt3572sta[/INDENT]- In Debian, add only the line:
	[INDENT]alias ra0 rt3572sta[/INDENT]**Step 8. **
If you want your driver module to load at startup (and this you do)...
- As the superuser, open /etc/network/interfaces
	[INDENT]$ sudo nano /etc/network/interfaces[/INDENT]**OR**[INDENT]$ su
# nano /etc/network/interfaces[/INDENT]- Update the line that starts with "auto" to include "ra0", for example: 
	[INDENT]auto lo ra0[/INDENT]and add the line: 
	[INDENT]allow-hotplug ra0[/INDENT]- For more information on this step, type the command: 
	[INDENT]man 5 interfaces[/INDENT][B]
Step 9.[/B] 
Blacklist the alternate drivers:
- As the superuser, open /etc/modprobe.d/blacklist or blacklist.conf (whichever you have)[INDENT]$ sudo nano /etc/modprobe.d/blacklist.conf[/INDENT]**OR**[INDENT]$ su 
# nano /etc/modprobe.d/blacklist[/INDENT]- Add the lines: 
 	Code:
 	#default WUSB600 staging drivers blacklist rt2870sta blacklist rt2800usb 
**Step 9 Troubleshooting:**
You may have to also blacklist a selection of additional drivers that  come with your kernel. For example, the default Ubuntu 2.6.32-21-generic  installation may require the following:
 	Code:
 	blacklist rt2860sta blacklist rt2870sta blacklist rt3090sta  blacklist rt2x00usb blacklist rt2500usb blacklist rt2800usb blacklist rt73usb 
If you do a module listing, you can see the kernel object modules attached to your kernel: 
 	Code:
 	modprobe -l 
This is a pretty long list, so let's shorten it to see what we want. One of these should do the trick: 

 	Code:
 	modprobe -l | grep wireless  modprobe -l | grep sta.ko modprobe -l | grep usb.ko 
Look for any drivers that match rtXXXXsta.ko or rtXXXXusb.ko that  are NOT rt3572sta.ko and try blacklisting them as well (minus the .ko  extension). 

[B]
Step 10.[/B] 
Reboot. 

**Step 11.**
Open up your favourite network manager and configure your wireless connection. 

If you're still not getting a connection, repeat Step 3 to ensure your  adapter is present. If it does not show, unplug it and reinsert. lsusb  should now show your adapter and you should be able to connect.

If you're STILL not getting a connection, Consider installing "Wicd", an  alternative network manager. You will need to manually input "ra0" as  your "Wireless interface in the Preferences pane. 

**Step 12.**
Happy surfing, dude(tte)! [IMG]http://static.linuxquestions.org/questions/images/smilies/biggrin.gif[/IMG]
 		 	 		 		 		 		  		 		 		 		 		 		 			 				 				* 					 						Last edited by BabyStuey; 05-01-2010 at 04:38 PM. 					 					 				*

---

### Post by Faith95 on 2010-10-04
On step 3 i only get "linksys"
is that alright? should i continue?

---

### Post by baz.g on 2010-10-07
hi,

many thanks for the intructions, tried them in 10.04 and worked perfectly, now giving 10.10 rc a run and it doesnt want to play :(

i have tried with version 2.3.0.0 of the driver and the latest (2.4.something) they both result in the same error:

```

thegrantfamily@ubuntu:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo makemake -C tools
make[1]: Entering directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_md5.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1664 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_UNWRAP&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:2348: warning: the frame size of 1168 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function &#8216;WscDecryptData&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1408 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c: In function &#8216;WscEncryptData&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1408 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c:895: warning: cast from pointer to integer of different size
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c:895: warning: cast from pointer to integer of different size
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/mlme.c:6112: warning: the frame size of 1728 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_wep.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/action.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_data.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_init.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_aes.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_sync.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/eeprom.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_info.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/dfs.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/spectrum.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/spectrum.c:1977: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rt_channel.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_profile.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_asic.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/assoc.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/auth.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:1764: warning: the frame size of 1456 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:1094: warning: the frame size of 1440 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:764: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c: In function &#8216;MlmeStartReqAction&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sync.c:581: warning: the frame size of 1088 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sanity.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/connect.c:356: warning: the frame size of 1776 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/wpa.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/ags.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_siwencode&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:1484: warning: suggest parentheses around operand of &#8216;!&#8217; or change &#8216;&&#8217; to &#8216;&&&#8217; or &#8216;!&#8217; to &#8216;~&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_iwaplist&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:604: warning: the frame size of 1296 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;rt_ioctl_siwmlme&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:1984: warning: the frame size of 1696 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlMAC&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:5853: warning: the frame size of 1376 bytes is larger than 1024 bytes
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c: In function &#8216;RTMPIoctlE2PROM&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/sta_ioctl.c:6052: warning: the frame size of 1376 bytes is larger than 1024 bytes
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:477: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:479: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/include/asm/string_64.h:58: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:629: warning: assignment makes integer from pointer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function &#8216;update_os_packet_info&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:651: warning: assignment makes integer from pointer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:672: warning: assignment makes integer from pointer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:945: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevDetach&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1694: warning: initialization discards qualifiers from pointer target type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_linux.c:1731: warning: initialization discards qualifiers from pointer target type
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_main_dev.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;MainVirtualIF_close&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../os/linux/rt_main_dev.c:117: warning: unused variable &#8216;Cancelled&#8217;
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/ba_action.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/ba_action.c:1553: warning: assignment makes integer from pointer without a cast
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../sta/dls.o
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocUsbBulkBufStruct&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeUsbBulkBufStruct&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
thegrantfamily@ubuntu:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo makemake -C tools
make[1]: Entering directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools'
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/tools/bin2h
cp -f os/linux/Makefile.6 /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/Makefile
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocUsbBulkBufStruct&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeUsbBulkBufStruct&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:62: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/thegrantfamily/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
thegrantfamily@ubuntu:~/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo modprobe rt3572sta
FATAL: Module rt3572sta not found.

```

any ideas please? :)

---

### Post by ihc100 on 2010-10-08
Try this link:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165)
(Nearly at the end.)

Posting with 10.10 32bit only wusb600N V2 attached. 

Good luck.

---

