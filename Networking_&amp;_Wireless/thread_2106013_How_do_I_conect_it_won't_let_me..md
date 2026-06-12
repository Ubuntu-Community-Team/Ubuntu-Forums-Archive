---
title: "How do I conect? it won't let me."
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by tahdas on 2013-01-17
Ok so today I got asus USB n13 . I can see my network, I click, it ask for password. I type in password, it try's to conect, then it pulls up the password thing again I try a different combo. It won't let me conect.
Here is the code I'm getting my password from: 001c26859039
If I type in 1c26859039 it connects my laptop and iPad, but it won't conect my ubuntu desktop.

Is there a way to override password for the Internet?
Thanks
Tahdas
Edit: I tried what  Ahallubuntu said but it was giving me a hard time. Is there anyway I could download something from the Ubuntu software center? I can get a wired connection with much trouble for a short amount of time.
The problem I have isn't with the USB thing and compatibility right? It's something else right?

---

### Post by ahallubuntu on 2013-01-17
It's not a password issue.  It's a driver issue with the built-in driver, which is unreliable.  You need to download/build/install the latest driver from Realtek, the maker of the chipset inside the dongle.  The chipset is called 8188/8192CU. Realtek lists it as "RTL8192CU" on their drivers page.

You can try these instructions.

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

---

### Post by tahdas on 2013-01-17
I'm running 12.10 and that's for 12.04.

Thanks,
Tahdas

---

### Post by ahallubuntu on 2013-01-17
Same problem in 12.10.  Same instructions worked for me to fix it in 12.10.

---

### Post by tahdas on 2013-01-17
Oh come on! The whole reason I bought this thing is because it was supposed to just work!
Now I have to return it and find one that is. Darn it!

Thanks,
Tahdas

---

### Post by ahallubuntu on 2013-01-17
OK, if you think ten minutes of work to download and install a driver is too hard, take back your wireless card and buy another one.

---

### Post by tahdas on 2013-01-17
> **ahallubuntu said:**
> OK, if you think ten minutes of work to download and install a driver is too hard, take back your wireless card and buy another one.

Sorry bad day. I was over estimating. 

Thanks
tahdas

---

### Post by tahdas on 2013-01-18
I tried what you said but it wasn't working. Can someone tell me what the issue is? Am I missing a driver? 
On the cd for the USB thing it has a section that says Linux, how do I install that?

Sorry I'm very confused.

Thanks!

---

### Post by ahallubuntu on 2013-01-18
What isn't working?  You'll have to be more specific if my instructions didn't work.  At what step did you have trouble?

The issue is that Ubuntu 12.04 LTS and 12.10 have a built-in driver for the card's Realtek chipset but the driver is broken.  The best solution I have found is to download, build, install the newest driver from Realtek's website as I describe in my instructions.

The driver on your CD may be too old to work with 12.10 or 12.04 .  That's why I suggest downloading the latest one.  Navigate through Realtek's website and find the driver for RTL8192CU .

I have several dongles with this same chipset, and those exact instructions worked for me.  I get great wireless connections with my USB dongles now, whereas before I could barely connect if at all.

---

### Post by tahdas on 2013-01-18
In vista I clicked on the link in the instructions and searched RTL8192CU I clicked on the correct link, then I downloaded the correct driver thing or whatever its called. The I put it on a USB drive and transferred it into Ubuntu the copyed it to desktop and renamed the file fish, I typed the command and it said the file didn't exist.

Thanks!

---

### Post by ahallubuntu on 2013-01-18
Yeah, it's not a "command," it's a zipped driver.  You have to extract it.

Try re-downloading it without changing the name this time.  The name may help extracting it correctly.

The current name of the correct driver is "RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip" .  That's from November 5, 2012; the name will change in the future when they update the driver.

Copy the downloaded file from Vista from your thumb drive to the Ubuntu computer, say to the Downloads folder in your home directory.

Then open a terminal in Ubuntu (search for "terminal" in dash).  cd to your Downloads directory, unzip the file, and install it.  Again, instructions are here:

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

---

### Post by tahdas on 2013-01-18
cd (NEWDIRECTORY_CREATED)

I'm not understanding what I'm supposed to put here? Cd something right? How do I find out the something?

Thank you so much!

---

### Post by dpurgert on 2013-01-18
> **tahdas said:**
> cd (NEWDIRECTORY_CREATED)

I'm not understanding what I'm supposed to put here? Cd something right? How do I find out the something?

Thank you so much!


OK, when you unzip the zip file, it will create a new directory, usually following the same naming convention as the zip file.

So, since the zip file is "RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip", after unzipping you will most likely see a new directory called "RTL8192xC_USB_linux_v3.4.4_4749.20121105".  so, you would issue the command:

```

$cd RTL8192xC_USB_linux_v3.4.4_4749.20121105

```

and then continue on.

---

### Post by ahallubuntu on 2013-01-18
> **dpurgert said:**
> 
So, since the zip file is "RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip", after unzipping you will most likely see a new directory called "RTL8192xC_USB_linux_v3.4.4_4749.20121105".  so, you would issue the command:

```

$cd RTL8192xC_USB_linux_v3.4.4_4749.20121105

```

and then continue on.


Unfortunately, Realtek decided to use a different name for the unzipped file!  If you unzip that file, the new directory (with the current zip file - they'll update the name over time) is:

"RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105"  .  So if you downloaded it to your Downloads folder (or copied it there from the thumbdrive), you'd type this in the terminal window:

```
cd ~/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
```

Then you'll be in the directory "RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105" .  Run the install there as directed in the original instructions.  You have to do the blacklisting too to make it work, otherwise you won't disable the old driver.

---

### Post by dpurgert on 2013-01-18
> **ahallubuntu said:**
> Unfortunately, Realtek decided to use a different name for the unzipped file! 
:rolleyes:
OFC, they just _had_ to make it difficult...

---

### Post by ahallubuntu on 2013-01-18
Yeah, it's bad enough that people have to type in a terminal to install this driver!  Easy for me, but some people find it quite intimidating.  Too bad Realtek won't release Debian/Ubuntu packages for this driver - would save lots of people major grief!!!

---

### Post by tahdas on 2013-01-19
```
tahdas@tahdas:~$ unzip RTL8192xC_USB_linux_v3.4.4_4749.20121105 
Archive:  RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip 
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/ 
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/android_reference_codes/ 
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/android_reference_codes/realtek_wifi_SDK_for_android.txt  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/android_reference_codes/realtek_wifi_SDK_for_android_20120618.tar.gz  
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/android_reference_codes_ICS_nl80211/ 
 extracting: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/android_reference_codes_ICS_nl80211/realtek_wifi_SDK_for_android_ICS_20120621.tar.gz  
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/ 
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/HowTo_enable_driver_to_support_WIFI_certification_test.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/HowTo_enable_the_power_saving_functionality.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/HowTo_support_more_VidPids.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/linux_dhcp_server_notes.txt  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/Quick_Start_Guide_for_Bridge.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/Quick_Start_Guide_for_Driver_Compilation_and_Installation.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/Quick_Start_Guide_for_SoftAP.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/Quick_Start_Guide_for_Station_Mode.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/Realtek_Wi-Fi_SDK_for_Android_ICS.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/RTK_Wi-Fi_Direct_Programming_guide.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/RTL8192D_operation_mode.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/SoftAP_Mode_features.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/Wireless_tools_porting_guide.pdf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/document/wpa_cli_with_wpa_supplicant.pdf  
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/ 
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz  
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/hardware_wps_pbc/ 
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/hardware_wps_pbc/Readme.txt  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/hardware_wps_pbc/sample.c  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/install.sh  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/readme.txt  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/ReleaseNotes.pdf  
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/WiFi_Direct_User_Interface/ 
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/WiFi_Direct_User_Interface/Android.mk  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/WiFi_Direct_User_Interface/install.sh  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/WiFi_Direct_User_Interface/p2p_api_test_linux.c  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/WiFi_Direct_User_Interface/p2p_test.h  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/WiFi_Direct_User_Interface/p2p_ui_test_linux.c  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/WiFi_Direct_User_Interface/Start_Guide_P2P_User_Interface_Linux.pdf  
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wireless_tools/ 
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wireless_tools/wireless_tools.30.rtl.tar.gz  
   creating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/ 
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/p2p_hostapd.conf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/rtl_hostapd_2G.conf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/rtl_hostapd_5G.conf  
 extracting: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/wpa_0_6_9.conf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/wpa_0_8.conf  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/wpa_supplicant-0.6.9_wps_patch_20100201_1.zip  
  inflating: RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/wpa_supplicant_hostapd/wpa_supplicant_hostapd-0.8_rtw_20120803.zip  
tahdas@tahdas:~$ cd 
tahdas@tahdas:~$ cd RTL8192xC_USB_linux_v3.4.4_4749.20121105 
bash: cd: RTL8192xC_USB_linux_v3.4.4_4749.20121105: No such file or directory 
tahdas@tahdas:~$ cd RTL8192xC_USB_linux_v3.4.4_4749.20121105 
bash: cd: RTL8192xC_USB_linux_v3.4.4_4749.20121105: No such file or directory 
tahdas@tahdas:~$ cd RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105 
tahdas@tahdas:~/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ chmod 755 ./install.sh 
tahdas@tahdas:~/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo ./install.sh 
[sudo] password for tahdas: 
################################################## 
Realtek Wi-Fi driver Auto installation script 
Novembor, 21 2011 v1.1.0 
################################################## 
Decompress the driver source tar ball: 
	rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105.tar.gz 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/clean 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ht.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_osintf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_event.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_rf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_rf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_sreset.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_hal.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/recv_osdep.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_recv.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_cmd.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/generic.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/little_endian.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swabb.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/swab.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/byteorder/big_endian.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_osintf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyReg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_service.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_osintf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_spec.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_hal.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CPhyCfg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_pwrctrl.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_cmd.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DETestHWImg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_version.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ethernet.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_br_ext.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_qos.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_p2p.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_xmit.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/xmit_osdep.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_ioctl.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_xmit.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_spec.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_hal.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/pci_ops.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CEHWImg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mlme_osdep.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/h2clbk.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_xp.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_vendor_req.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_eeprom.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/farray.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyCfg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ioctl_cfg80211.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_dm.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/if_ether.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_ce.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_security.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_rtl.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg_wowlan.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_led.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_led.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wlan_bssdef.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme_ext.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DPhyReg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/wifi.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192d_recv.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_event.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DEHWImg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192CUHWImg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/nic_spec.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_intf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_ce.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_ops_linux.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/circ_buf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_byteorder.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_xmit.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUHWImg_wowlan.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_set.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_recv.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_dm.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mlme.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/mp_custom_oid.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ip.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_ioctl_query.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/hal_init.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_conf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/Hal8192DUTestHWImg.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_linux.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/autoconf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/osdep_ce_service.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_efuse.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_cmd.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sdio_hal.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_io.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_led.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/ieee80211_ext.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/cmd_osdep.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/sta_info.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_iol.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/usb_ops.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_hal.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_debug.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/drv_types_xp.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtl8192c_rf.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_android.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/basic_types.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/include/rtw_mp_phy_regdef.h 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_eeprom.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.tmp_rtw_wlan_util.o 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp_ioctl.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_rtl.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mp.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/.rtw_wlan_util.o.d 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Makefile 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/ifcfg-wlan0 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/wlan0dhcp 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/pci_intf.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/sdio_intf.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/Kconfig 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/ 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_ce.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_xp.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.c 
rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 
Authentication requested [root] for make clean: 
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~ 
rm .tmp_versions -fr ; rm Module.symvers -fr 
rm -fr Module.markers ; rm -fr modules.order 
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c/usb ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/rtl8192c ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
Authentication requested [root] for make driver: 
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-17-generic/build M=/home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules 
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic' 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.o 
  CC [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.o 
  LD [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.mod.o 
  LD [M]  /home/tahdas/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.ko 
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic' 
################################################## 
Compile make driver ok!! 
################################################## 
Authentication requested [root] for remove driver: 
ERROR: Module 8192cu does not exist in /proc/modules 
Authentication requested [root] for insert driver: 
insmod: error inserting '8192cu.ko': -1 Device or resource busy 
Authentication requested [root] for install driver: 
install -p -m 644 8192cu.ko  /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/ 
/sbin/depmod -a 3.5.0-17-generic 
################################################## 
The Setup Script is completed ! 
################################################## 

Then:
tahdas@tahdas:~$ /etc/modprobe.d/blacklist.conf 
bash: /etc/modprobe.d/blacklist.conf: Permission denied 
tahdas@tahdas:~$ /etc/modprobe.d/blacklist.conf 
bash: /etc/modprobe.d/blacklist.conf: Permission denied 
tahdas@tahdas:~$ blacklist rtl8192cu 
blacklist: command not found 
tahdas@tahdas:~$ 
```

The blacklist thing messed up i think.

Thanks!

---

### Post by ahallubuntu on 2013-01-19
OK, you're almost there.

The Blacklist file is a file you EDIT, not a command.

Try this in a terminal:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

and add these three lines to the bottom of that file:

```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```

and then save the file and quit.



Finally, add the name of the new module to the end of the modules file, so it will automatically load each time you boot up:

```
gksu gedit /etc/modules
```


Add one line with just "8192cu" on it (without the quotes), put a blank line under that, and save the file.

At this point you can reboot or type:

```
sudo modprobe -r rtl8192cu
sudo modprobe 8192cu

```
and try your wireless.

---

### Post by tahdas on 2013-01-19
Heck yes!! Thank you soooooo much! [https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQtwIwAA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAXwGVXD7qEQ&ei=Xxn7UKPYFqnh0gG4hYDIAw&usg=AFQjCNEXilFPIJeux6nKesuwxtqhq_bDdw&sig2=gXlpAxNSHFJfNn8SCJ4nnA&bvm=bv.41248874,d.dmQ](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQtwIwAA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAXwGVXD7qEQ&ei=Xxn7UKPYFqnh0gG4hYDIAw&usg=AFQjCNEXilFPIJeux6nKesuwxtqhq_bDdw&sig2=gXlpAxNSHFJfNn8SCJ4nnA&bvm=bv.41248874,d.dmQ)

---

### Post by tahdas on 2013-01-20
Damn it! It asked to install a up date and now it dosent detect the USB wifi and the USB wifi thing doesn't light up

---

### Post by VictorMature on 2013-01-20
> **tahdas said:**
> Damn it! It asked to install a up date and now it dosent detect the USB wifi and the USB wifi thing doesn't light up

Can you just repeat the steps above?  It probably installed a new linux kernel, and you will have to build the driver for the new kernel

---

### Post by ahallubuntu on 2013-01-20
Make sure you added the module name 8192cu to the end of the file /etc/modules as per instructions, otherwise, the module won't load at each boot.

Otherwise, just build the module again.  Most of the make is already done if you didn't erase the old download directory, just do the install.sh again and it should be very quick.  No need to blacklist again.

---

### Post by tahdas on 2013-02-02
I'm having trouble again! Pease help! The guide isn't working! 
It installed sometype of update and now it's back to where I started. The guide isn't working.

Thanks tahdas

---

