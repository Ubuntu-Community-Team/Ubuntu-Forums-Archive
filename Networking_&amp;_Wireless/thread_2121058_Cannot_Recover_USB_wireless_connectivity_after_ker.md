---
title: "Cannot Recover USB wireless connectivity after kernel update"
date: 2013-02-28
forum: Networking &amp; Wireless
---

### Post by Kariotaki on 2013-02-28
[COLOR=#333333]Hello,[/COLOR]

[COLOR=#333333]I'm a newbie to Linux and I am having issues with my wireless USB network adapter (Mini USB 2.0 / 1.1 Wireless WiFi N LAN Adapter IEEE 802.11n 802.11g 802.11b - 943MiUSBMiF320). I am running Ubuntu 12.04[/COLOR]

[COLOR=#333333]There was initially an issue with the driver.[/COLOR]

[COLOR=#333333]I managed to find a script that will compile and install the correct driver.[/COLOR]

[COLOR=#333333]I saved it as mwdinstall.sh and originally ran it using sudo bash mwdinstall.sh. I was told that it needs to be reinstalled after any kernel upgrade.[/COLOR]

[COLOR=#333333]The kernel has now updated, but for some reason I cannot perform the command. [/COLOR]
[COLOR=#333333]When I tried, I was told to rename the same file cat mwdinstall.sh.[/COLOR]

[COLOR=#333333]If I click on the icon (Gnome Desktop), I get an option that allows me to run in the terminal. It works, however I must run it each time I restart or I lose connectivity. This was not the case when I first got it to work. [/COLOR]

[COLOR=#333333]I am guessing this is do to the fact that I cannot run the 'sudo bash' command in the terminal. I try running it with cd [name of directory]. sudo bash mwdinstall.sh.  It runs but will not register and I must repeat the process on each reboot. 

Can anyone please advise[/COLOR]

---

### Post by sully101 on 2013-03-02
I surpose your working from this [http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux]("http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux")

to help track things down could you post the output of

```
uname -a
```

and ```
ls -l
``` in the directory where you have unpacked the downloaded "driver"

If you have the origonal zip file it may pay to extract it again into a new directory. :)

---

### Post by Kariotaki on 2013-03-02
Hi! Thanks for responding.
You are 100% correct about the link. 

Here is output of the directory with the original "driver," as soon as I turned on the pc and did not have wireless connectivity:

xristaras@xristaras-linux:~$ '/home/xristaras/MostUpdatedRealTekDriver' 
bash: /home/xristaras/MostUpdatedRealTekDriver: Is a directory
xristaras@xristaras-linux:~$ cd '/home/xristaras/MostUpdatedRealTekDriver' 
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver$ uname -a
Linux xristaras-linux 3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686 athlon i386 GNU/Linux
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver$ ls -l
total 4
drwxrwxr-x 10 xristaras xristaras 4096 Feb 23 15:22 RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver$

---

### Post by sully101 on 2013-03-03
OK you should already have build essential installed, if your not sure you can do a ```
sudo apt-get install build-essential
``` this will install all the stuff you need to build the module. If its already installed it wont harm to run it again.

Next change directory to the extracted package ```
cd /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
```

Check that we have all the files we need in that directory ```
ls-lha
```

You should see install.sh and it should be [COLOR="#008000"]green[/COLOR], if not then make it executable ```
chmod +x ./install.sh
```

Your > mwdinstall.sh should also be in the same directory and it should be [COLOR="#008000"]green[/COLOR] too. If you have renamed it then it will be easier to rename it back to what it was to make life easier on the next kernel update :)

You may have to ```
chmod +x ./mwdinstall.sh
```

almost there do a ```
ls -lha
``` to check the > mwdinstall.sh and > install.sh are executable

if all is good then ```
sudo bash mwdinstall.sh
```

As a side note you seem to be confused about the > cat command you can read about it here [http://www.cyberciti.biz/faq/howto-use-cat-command-in-unix-linux-shell-script/]("http://www.cyberciti.biz/faq/howto-use-cat-command-in-unix-linux-shell-script/")

On the next kernel update you should be able to just do ```
sudo bash /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/mwdinstall.sh
```

---

### Post by Kariotaki on 2013-03-03
Thanks for the response.
Am I doing something wrong?
> xristaras@xristaras-linux:~$ cd /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ ls-lha
ls-lha: command not found
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$

---

### Post by sully101 on 2013-03-03
there should be a space between ls and -lha
"ls" means list the files in the directory and the "-lha" means that "ls" will output in an [l]ong[h]umanly readable format [a]ll the files even hidden ones.
Good luck try again :)

---

### Post by Kariotaki on 2013-03-03
Sorry, got it now. I followed the directions. The script runs, however, I must repeat the process each time I reboot. The computer does not "remember" and I do not have connectivity following a reboot/shutdown. Could it be that the new kernel is messing up the script? Here is what I get:

> xristaras@xristaras-linux:~$ cd '/home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105' 
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo bash mwdinstall.sh
[sudo] password for xristaras: 


This script (mwdinstall.sh) is to
    Install a Solwise NET-WL-UMD-606N mini wireless dongle on Ubuntu 12.04 or 12.10
Before use please list it (cat mwdinstall.sh) and read the commented (#...) lines.
Have you done so and are now in the directory with the driver package etc.? (y/n): y
Thank you


The script is provided in the hope that it will be helpful, but no liability for any consequenses of use can be accepted. You have been warned. Feel free to adapt and/or share it but please do not make any charge to others for it.


Do you understand and accept the above? (y/n): y
You agreed


For information: the running kernel is version 3.2.0-38
The real work now starts. It will take a while.
When asked to select the card, enter the digit 1
Do you want to continue? (y/n): y
You agreed


We will now blacklist a problematic driver that the OS tries to use
This will not take immediate effect - needs e.g. a reboot


We will now disable it by name change as it sometimes seems to pop up again!
mv: cannot stat `/lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko': No such file or directory


About to start the main install process. Reply with 1 when asked which chipset is being used.
The process takes a while and may display a warning message or two before completing.
These are probably only warnings which the script deals with.
If more drastic fail see the notes in this script.


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
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-38-generic-pae/build M=/home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-38-generic-pae'
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_cmd.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_security.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_debug.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_io.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_query.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ioctl_set.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_ieee80211.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_mlme_ext.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_wlan_util.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_pwrctrl.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_rf.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_recv.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_sta_mgt.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_xmit.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_p2p.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_br_ext.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/rtw_iol.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/core/efuse/rtw_efuse.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/hal_init.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_hal_init.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_phycfg.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rf6052.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_dm.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_rxdesc.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_cmd.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_mp.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_ops_linux.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/usb_halinit.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_led.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_xmit.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/rtl8192cu_recv.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/rtl8192c_sreset.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/hal/rtl8192c/usb/Hal8192CUHWImg.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/osdep_service.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/os_intfs.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/usb_intf.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_linux.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/xmit_linux.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/mlme_linux.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/recv_linux.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/os_dep/linux/rtw_android.o
  LD [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.mod.o
  LD [M]  /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/8192cu.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-38-generic-pae'
##################################################
Compile make driver ok!!
##################################################
Authentication requested [root] for remove driver:
ERROR: Module 8192cu does not exist in /proc/modules
Authentication requested [root] for insert driver:
Authentication requested [root] for install driver:
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/
/sbin/depmod -a 3.2.0-38-generic-pae
##################################################
The Setup Script is completed !
##################################################


Above should end with an encouraging message. If so ignore any
warning messages. Plug in the dongle if necessary and try it.
Be patient waiting for the initial connection.
If it fails try rebooting.
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ 


---

### Post by sully101 on 2013-03-03
That all looks pretty good. It seems from what you describe that the module is not getting loaded at boot and by the output of the script the old one isnt getting loaded either.

some info that may point us in the right direction can be gathered from the following commands with the usb device in.

list the currently loaded modules
```
lsmod
``` 
list the files that control which modules wont be loaded at boot
```
ls -lha /etc/modprobe.d
```
list usb devices connected to the system 
```
lsusb
``` 
list the directory where the new driver should be.
```
ls -lha /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu
```

---

### Post by Kariotaki on 2013-03-04
Thanks for the reply. Here is the output.
> xristaras@xristaras-linux:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
vesafb                 13516  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
nvidia              10257747  50 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12905  0 
joydev                 17393  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
nv_tco                 13399  0 
rfcomm                 38139  0 
i2c_nforce2            12906  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
forcedeth              58096  0 
sata_nv                23360  2 
pata_amd               13750  1 

Next
> xristaras@xristaras-linux:~$ ls -lha /etc/modprobe.d
total 80K
drwxr-xr-x   2 root root 4.0K Feb  9 19:41 .
drwxr-xr-x 136 root root  12K Mar  4 19:48 ..
-rw-r--r--   1 root root  160 Dec 27 20:48 alsa-base
-rw-r--r--   1 root root 2.5K Feb 15  2012 alsa-base.conf
-rw-r--r--   1 root root 2.6K Dec 28 01:20 alsa-base.conf.save
-rw-r--r--   1 root root  167 Dec 28 01:07 alsa-base.save
-rw-r--r--   1 root root  325 Mar 18  2011 blacklist-ath_pci.conf
-rw-r--r--   1 root root 1.6K Mar 18  2011 blacklist.conf
-rw-r--r--   1 root root  210 Mar 18  2011 blacklist-firewire.conf
-rw-r--r--   1 root root  661 Nov 20  2011 blacklist-framebuffer.conf
-rw-r--r--   1 root root  156 Feb 15  2012 blacklist-modem.conf
lrwxrwxrwx   1 root root   41 Dec 29 18:20 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root  583 Mar 18  2011 blacklist-rare-network.conf
-rw-r--r--   1 root root   20 Mar  3 22:45 blacklist-rtl8192.conf
-rw-r--r--   1 root root 1.1K Mar 18  2011 blacklist-watchdog.conf
-rw-r--r--   1 root root  127 Apr 22  2012 dkms.conf
-rw-r--r--   1 root root  165 Jan 29 08:57 nvidia-current-updates_hybrid.conf
lrwxrwxrwx   1 root root   47 Feb  9 19:41 nvidia-graphics-drivers.conf -> /etc/alternatives/i386-linux-gnu_nvidia_modconf
-rw-r--r--   1 root root  160 Dec 27 20:48 options
-rw-r--r--   1 root root   30 May 18  2012 vmwgfx-fbdev.conf

Now the USB
> xristaras@xristaras-linux:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305



Finally, it doesn't seem to recognize the driver. Here is what I am getting:
> xristaras@xristaras-linux:~$ ls -lha /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu
ls: cannot access /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu: No such file or directory





---

### Post by sully101 on 2013-03-04
Sorry my bad you should have "/lib/modules/3.2.0-38-generic[COLOR="#FF0000"]-pae[/COLOR]/kernel/drivers/net/wireless/rtlwifi/rtl8192cu"

The new driver should be in "/lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/" well thats where I think the script put it? named "8192cu.ko"

If you do a ```
sudo modprobe 8192cu
``` you should be working.

---

### Post by Bucky Ball on 2013-03-04
*Thread moved to **Networking & Wireless***

---

### Post by sully101 on 2013-03-04
Ok "3.2.0-38-generic-pae" is the clue here that "mwdinstall.sh" is not playing nice with the pae modules directory structure. Rather than try and fix "mwdinstall.sh" we should just install it the normal way and check the old one is blacklisted

So here are the commands to do that

```
cd /home/xristaras/MostUpdatedRealTekDriver
sudo chown -R xristaras:xristaras RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
cd RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
make clean
make
sudo make install
sudo depmod -a

```

Finally check that /etc/modprobe.d/blacklist-rtl8192.conf has a line in it that says "blacklist rtl8192cu" so that the old module isnt loaded, it should also have a new line at the end of it. To edit it from the terminal type ```
sudo gedit /etc/modprobe.d/blacklist-rtl8192.conf
```.

All going well reboot!

---

### Post by Kariotaki on 2013-03-05
Here is what I got from sudo modprobe 8192cu

> suxristaras@xristaras-linux:~$ sudo modprobe 8192cu
[sudo] password for xristaras: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '^X'
xristaras@xristaras-linux:~$ 


---

### Post by Kariotaki on 2013-03-05
Now I am proceeding with the next step.

> xristaras@xristaras-linux:~$ cd /home/xristaras/MostUpdatedRealTekDriver
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver$ sudo chown -R xristaras:xristaras RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
[sudo] password for xristaras: 
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver$ cd RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ make clean
make: *** No rule to make target `clean'.  Stop.
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ make
make: *** No targets specified and no makefile found.  Stop.
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo make install
make: `install' is up to date.
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo depmod -a
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ sudo gedit /etc/modprobe.d/blacklist-rtl8192.conf


xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ 
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105$ 


---

### Post by Kariotaki on 2013-03-05
Hello again,

Still the same problem on the reboot. Does not connect automatically and I have to re-run the mwdinstall.sh script on reboot.
Am I doing something wrong?

---

### Post by sully101 on 2013-03-05
well it looks like something else is up.

these lines
"WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '^X'"
indicate that those foles have been edited and lines in them are being ignored, but that may or may not be our problem or part of it. It would pay to have a look at them and see what they contain. Copy and paste the contents in your reply then we can see whats going on with them. 

the line "make clean" failed probably because there was no makefile in the directory. My bad again I think youll have to "cd" into the directory where the makefile is. Mine is in ...
"/home/$USER/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105"
so yours should be in "/home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105/" hopefully?

```
cd /home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105
```

then ...
```
make clean
make
sudo make install
sudo depmod -a
```

to check that the old module is blacklisted ```
grep 8192 /etc/modprobe.d/*
``` you should see a line with blacklist rtl8192cu

---

### Post by sully101 on 2013-03-05
You shouldnt have to re-run the old mwdinstall.sh script, you should be able to just do a ```
sudo modprobe 8192cu
``` to check which modules are loaded use the "lsmod" command which will scroll down your terminal so to check for just the modules we are working on ```
lsmod | grep 8192
``` When the output from that command is rtl8192cu you will have the old module loaded. We dont want that. When the ouput is 8192cu thats the new one.

---

### Post by Kariotaki on 2013-03-06
Hi,
I tried to locate the driver directory. It is locked and would not let me "cd" into it. I found the driver folder in .tar format so I extracted to the same directory. That is why it ends in (2). Still doesn't look like it took. I still need to run the script to access wifi on each reboot. Here is my output: In the grep command, 8192cu is listed in red. 

> xristaras@xristaras-linux:~$ cd '/home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)' 
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ make clean
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
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-38-generic-pae/build M=/home/xristaras/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)  modules
/bin/sh: 1: Syntax error: "(" unexpected
make: *** [modules] Error 2
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ sudo make install
[sudo] password for xristaras: 
install -p -m 644 8192cu.ko  /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `8192cu.ko': No such file or directory
make: *** [install] Error 1
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ sudo depmod -a
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ grep 8192 /etc/modprobe.d/*
/etc/modprobe.d/blacklist-rtl8192.conf:blacklist rtl8192cu
/etc/modprobe.d/blacklist-rtl8192.conf~:blacklist rtl8192cu
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ sudo modprobe 8192cu
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '^X'
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ lsmod | grep 8192
8192cu                502561  0 
xristaras@xristaras-linux:~/MostUpdatedRealTekDriver/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 (2)$ 


---

### Post by sully101 on 2013-03-06
1/ Both scripts gain root privelages before they make the driver which is why you are having trouble cd'ing into the directorys, They shouldnt! because they dont need to but thats the way the person wrote them. To fix that a simple ```
sudo chown -R $USER:$USER /path/to/whatever/directory
``` will change all the files back to being owned by 'you' and in your 'group'. change "$USER" to your user name. such as ```
sudo chown -R xristaras:xristaras /home/xristaras/MostUpdatedRealTekDriver/
```But youll have to do that after you execute either of those scripts

2/ The next bawk was the line "/bin/sh: 1: Syntax error: "(" unexpected" I presume that was because of a space in the directory name when it got the (2) appended

3/ make install failed because ther was nothing made to install.

4/ The line "lsmod | grep 8192" returned 8192cu 502561 0 that shows us that the module is loaded

I would suggest doing things in this order
remove wireless stick
reboot
open a terminal and do ```
lsmod | grep 8192
```
see if any modules are loaded
open another terminal and do ```
tail -f | dmesg
``` to see what happens next leave it open while we do the next step
plug your usb stick in while watching the dmesg terminal, wait for 1 or 2 minuites just to make sure
Go back to the first terminal and do another ```
lsmod | grep 8192
``` and see if the correct module is loaded. Post the results back here

---

### Post by Kariotaki on 2013-03-07
Hi,

Removed stick and rebooted. 
the grep command showed nothing. The first line was before inserting the wireless stick and the next two in step 3, after reinserting.
> xristaras@xristaras-linux:~$ lsmod | grep 8192
xristaras@xristaras-linux:~$ lsmod | grep 8192
xristaras@xristaras-linux:~$ lsmod | grep 8192
xristaras@xristaras-linux:~$ 


In step two I tried the dmesg command. Here is the output. The terminal did not do anything after I plugged in usb stick. 

> [    0.162626] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.162714] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.162801] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.162889] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.162977] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.163065] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.163152] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.163333] vgaarb: device added: PCI:0000:00:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.163345] vgaarb: loaded
[    0.163347] vgaarb: bridge control possible 0000:00:05.0
[    0.163526] i2c-core: driver [aat2870] using legacy suspend method
tail: warning: following standard input indefinitely is ineffective
[    0.163528] i2c-core: driver [aat2870] using legacy resume method
[    0.163631] SCSI subsystem initialized
[    0.163701] libata version 3.00 loaded.
[    0.163771] usbcore: registered new interface driver usbfs
[    0.163789] usbcore: registered new interface driver hub
[    0.163820] usbcore: registered new device driver usb
[    0.163944] PCI: Using ACPI for IRQ routing
[    0.165721] PCI: pci_cache_line_size set to 64 bytes
[    0.165807] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.165811] reserve RAM buffer: 000000007bef0000 - 000000007bffffff 
[    0.165962] NetLabel: Initializing
[    0.165964] NetLabel:  domain hash size = 128
[    0.165966] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.165980] NetLabel:  unlabeled traffic allowed by default
[    0.175427] AppArmor: AppArmor Filesystem Enabled
[    0.175470] pnp: PnP ACPI init
[    0.175493] ACPI: bus type pnp registered
[    0.176218] pnp 00:00: [bus 00-03]
[    0.176221] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.176225] pnp 00:00: [io  0x0000-0x03af window]
[    0.176228] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.176231] pnp 00:00: [io  0x1000-0xffff window]
[    0.176234] pnp 00:00: [io  0x03b0-0x03df window]
[    0.176237] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.176240] pnp 00:00: [mem 0x80000000-0xefffffff window]
[    0.176243] pnp 00:00: [mem 0xf4000000-0xfe02ffff window]
[    0.176327] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.176410] pnp 00:01: [io  0x4000-0x407f]
[    0.176413] pnp 00:01: [io  0x4080-0x40ff]
[    0.176416] pnp 00:01: [io  0x4400-0x447f]
[    0.176418] pnp 00:01: [io  0x4480-0x44ff]
[    0.176421] pnp 00:01: [io  0x4800-0x487f]
[    0.176424] pnp 00:01: [io  0x4880-0x48ff]
[    0.176427] pnp 00:01: [mem 0x7c000000-0x7fffffff]
[    0.176429] pnp 00:01: [io  0x2000-0x207f]
[    0.176432] pnp 00:01: [io  0x2080-0x20ff]
[    0.176510] system 00:01: [io  0x4000-0x407f] has been reserved
[    0.176514] system 00:01: [io  0x4080-0x40ff] has been reserved
[    0.176518] system 00:01: [io  0x4400-0x447f] has been reserved
[    0.176521] system 00:01: [io  0x4480-0x44ff] has been reserved
[    0.176525] system 00:01: [io  0x4800-0x487f] has been reserved
[    0.176528] system 00:01: [io  0x4880-0x48ff] has been reserved
[    0.176532] system 00:01: [io  0x2000-0x207f] has been reserved
[    0.176535] system 00:01: [io  0x2080-0x20ff] has been reserved
[    0.176539] system 00:01: [mem 0x7c000000-0x7fffffff] has been reserved
[    0.176544] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.177285] pnp 00:02: [io  0x0010-0x001f]
[    0.177288] pnp 00:02: [io  0x0022-0x003f]
[    0.177290] pnp 00:02: [io  0x0044-0x005f]
[    0.177293] pnp 00:02: [io  0x0062-0x0063]
[    0.177296] pnp 00:02: [io  0x0065-0x006f]
[    0.177298] pnp 00:02: [io  0x0074-0x007f]
[    0.177301] pnp 00:02: [io  0x0091-0x0093]
[    0.177303] pnp 00:02: [io  0x00a2-0x00bf]
[    0.177306] pnp 00:02: [io  0x00e0-0x00ef]
[    0.177309] pnp 00:02: [io  0x04d0-0x04d1]
[    0.177311] pnp 00:02: [io  0x0800-0x087f]
[    0.177400] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.177404] system 00:02: [io  0x0800-0x087f] has been reserved
[    0.177408] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.177422] pnp 00:03: [dma 4]
[    0.177424] pnp 00:03: [io  0x0000-0x000f]
[    0.177427] pnp 00:03: [io  0x0080-0x0090]
[    0.177430] pnp 00:03: [io  0x0094-0x009f]
[    0.177433] pnp 00:03: [io  0x00c0-0x00df]
[    0.177492] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.177504] pnp 00:04: [io  0x0070-0x0073]
[    0.177520] pnp 00:04: [irq 8]
[    0.177577] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.177588] pnp 00:05: [io  0x0061]
[    0.177646] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.177657] pnp 00:06: [io  0x00f0-0x00ff]
[    0.177670] pnp 00:06: [irq 13]
[    0.177727] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.177984] pnp 00:07: [io  0x0060]
[    0.177987] pnp 00:07: [io  0x0064]
[    0.177997] pnp 00:07: [irq 1]
[    0.178058] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.178093] pnp 00:08: [mem 0xf0000000-0xf3ffffff]
[    0.178175] system 00:08: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.178180] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.178311] pnp 00:09: [mem 0x000f0000-0x000f3fff]
[    0.178314] pnp 00:09: [mem 0x000f4000-0x000f7fff]
[    0.178316] pnp 00:09: [mem 0x000f8000-0x000fbfff]
[    0.178319] pnp 00:09: [mem 0x000fc000-0x000fffff]
[    0.178322] pnp 00:09: [mem 0x7bef0000-0x7befffff]
[    0.178325] pnp 00:09: [mem 0xffff0000-0xffffffff]
[    0.178328] pnp 00:09: [mem 0x00000000-0x0009ffff]
[    0.178331] pnp 00:09: [mem 0x00100000-0x7beeffff]
[    0.178334] pnp 00:09: [mem 0x7bf00000-0x7fefffff]
[    0.178337] pnp 00:09: [mem 0xfec00000-0xfec00fff]
[    0.178339] pnp 00:09: [mem 0xfee00000-0xfeefffff]
[    0.178342] pnp 00:09: [mem 0xfefff000-0xfeffffff]
[    0.178345] pnp 00:09: [mem 0xfff80000-0xfff80fff]
[    0.178348] pnp 00:09: [mem 0xfff90000-0xfffbffff]
[    0.178351] pnp 00:09: [mem 0xfffed000-0xfffeffff]
[    0.178442] system 00:09: [mem 0x000f0000-0x000f3fff] could not be reserved
[    0.178446] system 00:09: [mem 0x000f4000-0x000f7fff] could not be reserved
[    0.178449] system 00:09: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.178453] system 00:09: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.178457] system 00:09: [mem 0x7bef0000-0x7befffff] could not be reserved
[    0.178461] system 00:09: [mem 0xffff0000-0xffffffff] has been reserved
[    0.178465] system 00:09: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.178468] system 00:09: [mem 0x00100000-0x7beeffff] could not be reserved
[    0.178472] system 00:09: [mem 0x7bf00000-0x7fefffff] could not be reserved
[    0.178476] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.178480] system 00:09: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.178484] system 00:09: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.178488] system 00:09: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.178492] system 00:09: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.178495] system 00:09: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.178499] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.178514] pnp: PnP ACPI: found 10 devices
[    0.178516] ACPI: ACPI bus type pnp unregistered
[    0.178520] PnPBIOS: Disabled by ACPI PNP
[    0.215492] Switching to clocksource acpi_pm
[    0.215526] PCI: max bus depth: 1 pci_try_num: 2
[    0.215558] pci 0000:00:05.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.215563] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.215567] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    0.215571] pci 0000:00:02.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.215575] pci 0000:00:02.0:   bridge window [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.215580] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.215583] pci 0000:00:04.0:   bridge window [io  0x9000-0x9fff]
[    0.215587] pci 0000:00:04.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.215592] pci 0000:00:04.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.215597] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.215600] pci 0000:00:10.0:   bridge window [io  0xa000-0xafff]
[    0.215605] pci 0000:00:10.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.215610] pci 0000:00:10.0:   bridge window [mem 0xfdc00000-0xfdcfffff pref]
[    0.215623] pci 0000:00:02.0: setting latency timer to 64
[    0.215628] pci 0000:00:04.0: setting latency timer to 64
[    0.215634] pci 0000:00:10.0: setting latency timer to 64
[    0.215639] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.215642] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.215645] pci_bus 0000:00: resource 6 [mem 0x80000000-0xf3ffffff]
[    0.215649] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xfcffffffff]
[    0.215652] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.215656] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.215659] pci_bus 0000:01: resource 2 [mem 0xfdb00000-0xfdbfffff 64bit pref]
[    0.215663] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.215666] pci_bus 0000:02: resource 1 [mem 0xfda00000-0xfdafffff]
[    0.215670] pci_bus 0000:02: resource 2 [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.215673] pci_bus 0000:03: resource 0 [io  0xa000-0xafff]
[    0.215676] pci_bus 0000:03: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.215680] pci_bus 0000:03: resource 2 [mem 0xfdc00000-0xfdcfffff pref]
[    0.215683] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.215686] pci_bus 0000:03: resource 5 [mem 0x000a0000-0x000bffff]
[    0.215690] pci_bus 0000:03: resource 6 [mem 0x80000000-0xf3ffffff]
[    0.215693] pci_bus 0000:03: resource 7 [mem 0xf4000000-0xfcffffffff]
[    0.215751] NET: Registered protocol family 2
[    0.215830] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.215830] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.215830] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.215830] TCP: Hash tables configured (established 131072 bind 65536)
[    0.215830] TCP reno registered
[    0.215830] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.215830] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.215830] NET: Registered protocol family 1
[    0.215830] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.215830] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.215830] pci 0000:00:05.0: Boot video device
[    0.215830] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.215830] pci 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    0.288033] pci 0000:00:0b.0: PCI INT A disabled
[    0.288195] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.288209] pci 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.304033] pci 0000:00:0b.1: PCI INT B disabled
[    0.304089] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.304097] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    0.304156] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.304164] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    0.304224] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.304231] pci 0000:00:10.0: Enabling HT MSI Mapping
[    0.304294] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.304303] pci 0000:00:10.1: Enabling HT MSI Mapping
[    0.304322] PCI: CLS 32 bytes, default 64
[    0.304727] audit: initializing netlink socket (disabled)
[    0.304740] type=2000 audit(1362704817.300:1): initialized
[    0.333852] Trying to unpack rootfs image as initramfs...
[    0.368923] highmem bounce pool size: 64 pages
[    0.368931] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.374731] VFS: Disk quotas dquot_6.5.2
[    0.374820] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.380313] fuse init (API version 7.17)
[    0.380457] msgmni has been set to 1687
[    0.392361] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.392419] io scheduler noop registered
[    0.392422] io scheduler deadline registered
[    0.392431] io scheduler cfq registered (default)
[    0.392596] pcieport 0000:00:02.0: setting latency timer to 64
[    0.392628] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.392680] pcieport 0000:00:04.0: setting latency timer to 64
[    0.392702] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    0.392785] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.392821] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.393015] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.393022] ACPI: Power Button [PWRB]
[    0.393099] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.393103] ACPI: Power Button [PWRF]
[    0.393172] ACPI: Fan [FAN] (on)
[    0.397314] thermal LNXTHERM:00: registered as thermal_zone0
[    0.397317] ACPI: Thermal Zone [THRM] (40 C)
[    0.397378] ERST: Table is not found!
[    0.397380] GHES: HEST is not enabled!
[    0.400327] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.401587] isapnp: Scanning for PnP cards...
[    0.407508] Linux agpgart interface v0.103
[    0.456819] brd: module loaded
[    0.457801] loop: module loaded
[    0.458168] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.458417] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[    0.458441] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    0.458461] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.458470] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.458652] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[    0.458667] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    0.458686] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.458695] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.459246] Fixed MDIO Bus: probed
[    0.459277] tun: Universal TUN/TAP device driver, 1.6
[    0.459279] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.464240] PPP generic driver version 2.4.2
[    0.464394] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.464428] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.464453] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.464457] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.464504] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.464533] ehci_hcd 0000:00:0b.1: debug port 1
[    0.464542] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    0.464573] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfe02e000
[    0.476058] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.476285] hub 1-0:1.0: USB hub found
[    0.476291] hub 1-0:1.0: 8 ports detected
[    0.476400] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.476428] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    0.476451] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.476455] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.476516] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.476555] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xfe02f000
[    0.568329] hub 2-0:1.0: USB hub found
[    0.568338] hub 2-0:1.0: 8 ports detected
[    0.568448] uhci_hcd: USB Universal Host Controller Interface driver
[    0.568532] usbcore: registered new interface driver libusual
[    0.568586] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.568588] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.569408] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.569544] mousedev: PS/2 mouse device common for all mice
[    0.569705] rtc_cmos 00:04: RTC can wake from S4
[    0.569837] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.569871] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.569949] device-mapper: uevent: version 1.0.3
[    0.570041] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.570087] EISA: Probing bus 0 at eisa.0
[    0.570091] EISA: Cannot allocate resource for mainboard
[    0.570094] Cannot allocate resource for EISA slot 1
[    0.570097] Cannot allocate resource for EISA slot 2
[    0.570100] Cannot allocate resource for EISA slot 3
[    0.570102] Cannot allocate resource for EISA slot 4
[    0.570105] Cannot allocate resource for EISA slot 5
[    0.570108] Cannot allocate resource for EISA slot 6
[    0.570110] Cannot allocate resource for EISA slot 7
[    0.570113] Cannot allocate resource for EISA slot 8
[    0.570115] EISA: Detected 0 cards.
[    0.570128] cpufreq-nforce2: No nForce2 chipset.
[    0.570131] cpuidle: using governor ladder
[    0.570133] cpuidle: using governor menu
[    0.570136] EFI Variables Facility v0.08 2004-May-17
[    0.570408] TCP cubic registered
[    0.570575] NET: Registered protocol family 10
[    0.571169] NET: Registered protocol family 17
[    0.571174] Registering the dns_resolver key type
[    0.571198] Using IPI No-Shortcut mode
[    0.571327] PM: Hibernation image not present or could not be loaded.
[    0.571343] registered taskstats version 1
[    0.710773] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.959860] isapnp: No Plug & Play device found
[    1.119521] Freeing initrd memory: 13836k freed
[    1.139775]   Magic number: 5:747:103
[    1.139895] rtc_cmos 00:04: setting system clock to 2013-03-08 01:06:58 UTC (1362704818)
[    1.139901] powernow-k8: Found 1 AMD Sempron(tm) Processor 3400+ (1 cpu cores) (version 2.20.00)
[    1.139937] powernow-k8: fid 0xa (1800 MHz), vid 0x6
[    1.139940] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.140060] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.140063] EDD information not available.
[    1.140270] Freeing unused kernel memory: 740k freed
[    1.140831] Write protecting the kernel text: 5828k
[    1.140849] Write protecting the kernel read-only data: 2380k
[    1.140852] NX-protecting the kernel data: 4412k
[    1.169144] udevd[81]: starting version 175
[    1.208063] usb 2-1: new full-speed USB device number 2 using ohci_hcd
[    1.434800] pata_amd 0000:00:0d.0: version 0.4.1
[    1.434859] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.469049] scsi0 : pata_amd
[    1.472150] scsi1 : pata_amd
[    1.472696] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    1.472700] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    1.472866] sata_nv 0000:00:0e.0: version 3.5
[    1.472881] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    1.472885] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.472943] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.476659] scsi2 : sata_nv
[    1.479918] scsi3 : sata_nv
[    1.480171] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 21
[    1.480176] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 21
[    1.480248] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    1.480253] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.480313] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.483503] scsi4 : sata_nv
[    1.486220] scsi5 : sata_nv
[    1.486410] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 20
[    1.486415] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 20
[    1.486502] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.486711] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.486719] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.486725] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.644363] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input3
[    1.644629] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-1/input0
[    1.652339] ata1.00: ATAPI: HL-DT-ST RW/DVD GCC-4482B, 1.06, max UDMA/33
[    1.652351] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    1.654889] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.1/input/input4
[    1.655420] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:0b.0-1/input1
[    1.655650] usbcore: registered new interface driver usbhid
[    1.655654] usbhid: USB HID core driver
[    1.684261] ata1.00: configured for UDMA/33
[    1.685328] scsi 0:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4482B 1.06 PQ: 0 ANSI: 5
[    1.686253] sr0: scsi3-mmc drive: 15x/15x writer cd/rw xa/form2 cdda tray
[    1.686257] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.686419] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.686586] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.800036] ata5: SATA link down (SStatus 0 SControl 310)
[    1.948040] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.956193] ata3.00: ATA-7: ST3120213AS, 3.AHH, max UDMA/100
[    1.956198] ata3.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.972187] ata3.00: configured for UDMA/100
[    1.972328] scsi 2:0:0:0: Direct-Access     ATA      ST3120213AS      3.AH PQ: 0 ANSI: 5
[    1.973596] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.973654] sd 2:0:0:0: [sda] Write Protect is off
[    1.973658] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.973683] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.973930] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.008846] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:18:f3:4c:1f:67
[    2.008852] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    2.010634]  sda: sda1 sda2 < sda5 >
[    2.011053] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.284039] ata4: SATA link down (SStatus 0 SControl 310)
[    2.485254] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.596037] ata6: SATA link down (SStatus 0 SControl 310)
[   17.467611] Adding 2027516k swap on /dev/sda5.  Priority:-1 extents:1 across:2027516k 
[   17.481617] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.525621] udevd[433]: starting version 175
[   17.592875] lp: driver loaded but no devices found
[   17.629548] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.099695] Bluetooth: Core ver 2.16
[   18.100581] NET: Registered protocol family 31
[   18.100586] Bluetooth: HCI device and connection manager initialized
[   18.100591] Bluetooth: HCI socket layer initialized
[   18.100594] Bluetooth: L2CAP socket layer initialized
[   18.100607] Bluetooth: SCO socket layer initialized
[   18.103896] ppdev: user-space parallel port driver
[   18.133251] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.133257] Bluetooth: BNEP filters: protocol multicast
[   18.239740] Bluetooth: RFCOMM TTY layer initialized
[   18.239749] Bluetooth: RFCOMM socket layer initialized
[   18.239752] Bluetooth: RFCOMM ver 1.11
[   18.285604] type=1400 audit(1362704835.641:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=653 comm="apparmor_parser"
[   18.296354] type=1400 audit(1362704835.653:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=653 comm="apparmor_parser"
[   18.556124] ACPI: resource nForce2_smbus [io  0x4c00-0x4c3f] conflicts with ACPI region SM00 [io 0x4c00-0x4c05]
[   18.556130] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.564082] i2c i2c-0: nForce2 SMBus adapter at 0x4c40
[   18.574943] NV_TCO: NV TCO WatchDog Timer Driver v0.01
[   18.578300] NV_TCO: Watchdog reboot not detected.
[   18.580336] NV_TCO: initialized (0x4440). heartbeat=30 sec (nowayout=0)
[   18.674894] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   18.715913] type=1400 audit(1362704836.069:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=697 comm="apparmor_parser"
[   18.727387] type=1400 audit(1362704836.081:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=697 comm="apparmor_parser"
[   18.727720] type=1400 audit(1362704836.081:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=697 comm="apparmor_parser"
[   18.851245] nvidia: module license 'NVIDIA' taints kernel.
[   18.851251] Disabling lock debugging due to kernel taint
[   19.726043] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   19.726074] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   19.726084] nvidia 0000:00:05.0: setting latency timer to 64
[   19.726090] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.749956] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.64  Tue Oct 30 11:09:29 PDT 2012
[   20.038006] init: failsafe main process (783) killed by TERM signal
[   20.151881] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   20.151890] snd_hda_intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   20.151952] snd_hda_intel 0000:00:10.1: irq 42 for MSI/MSI-X
[   20.151979] snd_hda_intel 0000:00:10.1: setting latency timer to 64
[   20.434396] forcedeth 0000:00:14.0: eth0: no link during initialization
[   20.439856] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.442878] type=1400 audit(1362704837.797:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=898 comm="apparmor_parser"
[   20.446698] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.459074] type=1400 audit(1362704837.813:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=902 comm="apparmor_parser"
[   20.462362] type=1400 audit(1362704837.817:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=902 comm="apparmor_parser"
[   20.462699] type=1400 audit(1362704837.817:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=902 comm="apparmor_parser"
[   20.481231] type=1400 audit(1362704837.837:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=903 comm="apparmor_parser"
[   20.715342] init: alsa-restore main process (946) terminated with status 19
[   20.860453] hda_codec: ALC888: BIOS auto-probing.
[   20.860461] hda_codec: ALC888: SKU not ready 0x411111f0
[   21.852319] input: HDA NVidia Line as /devices/pci0000:00/0000:00:10.1/sound/card0/input5
[   21.852622] input: HDA NVidia Line as /devices/pci0000:00/0000:00:10.1/sound/card0/input6
[   21.852870] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:10.1/sound/card0/input7
[   21.853109] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:10.1/sound/card0/input8
[   21.853349] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:10.1/sound/card0/input9
[   21.853605] input: HDA NVidia Line-Out as /devices/pci0000:00/0000:00:10.1/sound/card0/input10
[   22.173757] init: plymouth-upstart-bridge main process (605) killed by TERM signal
[   22.367741] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   22.367746] vesafb: scrolling: redraw
[   22.367751] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   22.368743] vesafb: framebuffer at 0xe0000000, mapped to 0xf8900000, using 5120k, total 5120k
[   22.369050] Console: switching to colour frame buffer device 160x64
[   22.369100] fb0: VESA VGA frame buffer device
[   22.428501] init: plymouth-splash main process (1202) terminated with status 1
[   22.478098] init: lightdm main process (1209) killed by TERM signal
[   23.816688] NVRM: Your system is not currently configured to drive a VGA console
[   23.816696] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   23.816700] NVRM: requires the use of a text-mode VGA console. Use of other console
[   23.816703] NVRM: drivers including, but not limited to, vesafb, may result in
[   23.816706] NVRM: corruption and stability problems, and is not supported.
[   45.080664] ISO 9660 Extensions: Microsoft Joliet Level 1
[   45.091611] ISOFS: changing to secondary root


---

### Post by sully101 on 2013-03-08
To force the module to load on boot do the following.

```
sudo su
echo 8192cu >> /etc/modules
```

reboot.

---

### Post by Kariotaki on 2013-03-08
No luck. 
I tried the command and waited for quite a while. The terminal did not "do anything" and just went to the next line. I assumed the process was finished as I saw no activity. Every time I tried to close terminal, I was given a message that if I exited I would terminate the operation. I waited for several minutes but kept getting the same message: 'There is still a process running in this terminal. Closing the terminal will kill it.' Finally rebooted. 
On reboot, still not connectivity. Had to manually run script again. 

Here is the output of the process that I retried upon reboot:
> xristaras@xristaras-linux:~$ sudo modprobe 8192cu
[sudo] password for xristaras: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '^X'
FATAL: Error inserting 8192cu (/lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko): Invalid argument
xristaras@xristaras-linux:~$ lsmdo | grep 8192
No command 'lsmdo' found, did you mean:
 Command 'lsmod' from package 'module-init-tools' (main)
lsmdo: command not found
xristaras@xristaras-linux:~$ lsmod | grep 8192
xristaras@xristaras-linux:~$ sudo su
root@xristaras-linux:/home/xristaras# echo 8192cu >> /etc/modules
root@xristaras-linux:/home/xristaras# sudo echo 8192cu >> /etc/modules
root@xristaras-linux:/home/xristaras# 


---

### Post by sully101 on 2013-03-08
Could you confirm that you have two 8192 modules on your system

/lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko
/lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko

The outpot of ```
modinfo /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko
``` and ```
modinfo /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko
``` should tell us which is which.

You can use the insmod command to explicitley load each one, You may find one works and the other doesnt.```
sudo insmod /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko
``` or ```
sudo insmod /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko
```

I dont know where /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko came from, any ideas?

---

### Post by Kariotaki on 2013-03-08
Hi,

Here is the output of the first two codes you asked for:
> xristaras@xristaras-linux:~$ modinfo /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko
Command 'modinfo' is available in '/sbin/modinfo'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
modinfo: command not found
xristaras@xristaras-linux:~$ modinfo /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko
Command 'modinfo' is available in '/sbin/modinfo'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
modinfo: command not found
xristaras@xristaras-linux:~$ 

Now the next two codes: 
> xristaras@xristaras-linux:~$ sudo insmod /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko
[sudo] password for xristaras: 
insmod: error inserting '/lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko': -1 Invalid parameters
xristaras@xristaras-linux:~$ sudo insmod /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko
insmod: error inserting '/lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko': -1 File exists
xristaras@xristaras-linux:~$ sudo insmod /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko
insmod: error inserting '/lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/8192cu.ko': -1 File exists
xristaras@xristaras-linux:~$


As far as [COLOR=#000000]/lib/modules[/COLOR][COLOR=#000000]/lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko[/COLOR][COLOR=#000000]/3.2.0-38-generic-pae/updates/dkms/8192cu.ko,  if I go on my file system directory, there are two files listed in the dkms folder. 8192cu.ko and nvidia_current_updates.ko
I had added this additional driver because my video card was not being recognized and the screen kept freezing. But the wireless still worked properly if I am not mistaken. It was only after the new kernel was added that connectivity at startup became an issue.[/COLOR]

---

### Post by sully101 on 2013-03-09
what files do you have in /usr/src? could you post the output of the following. ```
ls -lha /usr/src
ls -lha /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless
ls -lha /lib/modules/3.2.0-38-generic-pae/updates/dkms
```As a guess I would say you have the worng module in "/lib/modules/3.2.0-38-generic-pae/updates/dkms" and as a very ugly hack to get you going you could just rename it to something else such as ```
sudo mv /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu[COLOR="#FF0000"].ko[/COLOR] /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.wasako
``` You should then be able to load the other module with ```
sudo modprobe 8192cu
```The we will know if at least that one works.

---

### Post by Kariotaki on 2013-03-09
Here is the output of the first three commands: 
> xristaras@xristaras-linux:~$ ls -lha /usr/src
total 64K
drwxr-xr-x 16 root      root      4.0K Feb 21 20:02 .
drwxr-xr-x 11 root      root      4.0K Feb  9 19:41 ..
drwxr-xr-x 24 root      root      4.0K Aug 17  2012 linux-headers-3.2.0-29
drwxr-xr-x  7 root      root      4.0K Aug 17  2012 linux-headers-3.2.0-29-generic-pae
drwxr-xr-x 24 root      root      4.0K Dec 21 20:12 linux-headers-3.2.0-35
drwxr-xr-x  7 root      root      4.0K Dec 22 23:02 linux-headers-3.2.0-35-generic-pae
drwxr-xr-x 24 root      root      4.0K Jan 17 23:03 linux-headers-3.2.0-36
drwxr-xr-x  7 root      root      4.0K Jan 17 23:03 linux-headers-3.2.0-36-generic-pae
drwxr-xr-x 24 root      root      4.0K Feb  1 18:13 linux-headers-3.2.0-37
drwxr-xr-x  7 root      root      4.0K Feb  9 19:36 linux-headers-3.2.0-37-generic
drwxr-xr-x  7 root      root      4.0K Feb  1 18:13 linux-headers-3.2.0-37-generic-pae
drwxr-xr-x 24 root      root      4.0K Feb 23 00:48 linux-headers-3.2.0-38
drwxr-xr-x  7 root      root      4.0K Feb 23 00:48 linux-headers-3.2.0-38-generic
drwxr-xr-x  7 root      root      4.0K Feb 23 00:48 linux-headers-3.2.0-38-generic-pae
drwxr-xr-x  3 root      root      4.0K Feb  9 19:41 nvidia-current-updates-304.64
drwxrwxrwx  3 xristaras xristaras 4.0K Feb  9  2012 rtl8192cu-3.3.23192
xristaras@xristaras-linux:~$ ls -lha /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless
total 1.2M
drwxr-xr-x 23 root root 4.0K Mar  9 01:12 .
drwxr-xr-x 24 root root 4.0K Feb 23 00:48 ..
-rw-r--r--  1 root root 581K Mar  9 01:12 8192cu.ko
-rw-r--r--  1 root root  37K Feb 19 08:46 adm8211.ko
-rw-r--r--  1 root root 6.2K Feb 19 08:46 airo_cs.ko
-rw-r--r--  1 root root  96K Feb 19 08:46 airo.ko
-rw-r--r--  1 root root  53K Feb 19 08:46 at76c50x-usb.ko
drwxr-xr-x  6 root root 4.0K Feb 23 00:48 ath
-rw-r--r--  1 root root 9.6K Feb 19 08:46 atmel_cs.ko
-rw-r--r--  1 root root  47K Feb 19 08:46 atmel.ko
-rw-r--r--  1 root root 4.4K Feb 19 08:46 atmel_pci.ko
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 b43
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 b43legacy
drwxr-xr-x  5 root root 4.0K Feb 21 20:02 brcm80211
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 hostap
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 ipw2x00
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 iwlegacy
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 iwlwifi
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 iwmc3200wifi
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 libertas
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 libertas_tf
-rw-r--r--  1 root root  37K Feb 19 08:46 mac80211_hwsim.ko
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 mwifiex
-rw-r--r--  1 root root  61K Feb 19 08:46 mwl8k.ko
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 orinoco
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 p54
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 prism54
-rw-r--r--  1 root root  34K Feb 19 08:46 ray_cs.ko
-rw-r--r--  1 root root  40K Feb 19 08:46 rndis_wlan.ko
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 rt2x00
drwxr-xr-x  4 root root 4.0K Feb 21 20:02 rtl818x
drwxr-xr-x  7 root root 4.0K Feb 23 00:48 rtlwifi
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 wl1251
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 wl12xx
-rw-r--r--  1 root root  27K Feb 19 08:46 wl3501_cs.ko
-rw-r--r--  1 root root  28K Feb 19 08:46 zd1201.ko
drwxr-xr-x  2 root root 4.0K Feb 23 00:48 zd1211rw
xristaras@xristaras-linux:~$ ls -lha /lib/modules/3.2.0-38-generic-pae/updates/dkms
total 12M
drwxr-xr-x 2 root root 4.0K Feb 21 20:05 .
drwxr-xr-x 3 root root 4.0K Feb 21 20:04 ..
-rw-r--r-- 1 root root 564K Feb 21 20:05 8192cu.ko
-rw-r--r-- 1 root root  12M Feb 21 20:04 nvidia_current_updates.ko
xristaras@xristaras-linux:~$ 

I don't think the hack worked. Is it because we did not add the suffix .ko at the end of 8192cu?: 
> xristaras@xristaras-linux:~$ sudo mv /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.wasako
[sudo] password for xristaras: 
mv: cannot stat `/lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu': No such file or directory
xristaras@xristaras-linux:~$ 


---

### Post by sully101 on 2013-03-09
yes thats why
sorry my bad again

should be 

sudo mv /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.[COLOR="#FF0000"]ko[/COLOR] /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.wasako

---

### Post by sully101 on 2013-03-09
From ls -lha /usr/src

"drwxrwxrwx 3 xristaras xristaras 4.0K Feb 9 2012 rtl8192cu-3.3.23192"

Tells us that its owned by you ( read not root ) It could be part of a "package" the module version seems to be "3.3.23192" and the new one is "3.4.3_4369" If it was installed as part of a package the correct way would to be to remove the package, as it will rebuild every kernel upgrade and generally get in the way every time. You can check if it is part of a package by doing ```
dpkg -S rtl8192cu-3.3.23192
``` After a little investigation it probably came from here [http://ubuntuforums.org/showthread.php?t=2066809&p=12279876#post12279876]("http://ubuntuforums.org/showthread.php?t=2066809&p=12279876#post12279876"), If so then its not part of a package and we can just remove it when we get things working with the new module.

---

### Post by Kariotaki on 2013-03-09
The mod probe still didn't take:
> xristaras@xristaras-linux:~$ sudo mv /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.wasako
[sudo] password for xristaras: 
xristaras@xristaras-linux:~$ sudo modprobe 8192cu
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '^X'
xristaras@xristaras-linux:~$ 


Here is the result of the "package" inquiry: 
> xristaras@xristaras-linux:~$ dpkg -S rtl8192cu-3.3.23192
dpkg-query: no path found matching pattern *rtl8192cu-3.3.23192*.
xristaras@xristaras-linux:~$ 


---

### Post by Kariotaki on 2013-03-09
[ATTACH=CONFIG]239979[/ATTACH]
Maybe this screenshot of the folder will help....

---

### Post by sully101 on 2013-03-09
I'm more interested in the "drivers/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105" directory. that is where your new module has meen made. It should be installed in /lib/modules/3.2.0-38-generic-pae/kernel/drivers/net/wireless/

Could you confirm for me that after a ```
sudo modprobe 8192cu
``` the module is still not loaded by doing a ```
lsmod | grep 8192
```

---

### Post by Kariotaki on 2013-03-09
The module appears to load and is in red.
> xristaras@xristaras-linux:~$ sudo modprobe 8192cu
[sudo] password for xristaras: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '^X'
xristaras@xristaras-linux:~$ lsmod | grep 8192
8192cu                502561  0 
xristaras@xristaras-linux:~$ 


---

### Post by sully101 on 2013-03-09
So now when you reboot is the module loaded automatically? ie
Reboot ...
open terminal and do "lsmod | grep 8192", if that command returns nothing do a "sudo modprobe 8192cu" to load the module. Does it work ?

---

### Post by Kariotaki on 2013-03-09
No luck. This seems to be the culprit: '/lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko'
Here is the output:

> xristaras@xristaras-linux:~$ sudo modprobe 8192cu
[sudo] password for xristaras: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/alsa-base.save line 7: ignoring bad line starting with '^X'
FATAL: Could not read '/lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko': No such file or directory
xristaras@xristaras-linux:~$ lsmod | grep 8192
xristaras@xristaras-linux:~$ 


I don't even know what a .ko file is. When I googled it, I found this article. Does it apply to what we are discussing? 
[http://forums.opensuse.org/english/get-technical-help-here/hardware/479471-how-do-i-load-my-ko-module-boot-automatically.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/479471-how-do-i-load-my-ko-module-boot-automatically.html)

---

### Post by sully101 on 2013-03-09
So we need to remove the old one from ( found in /usr/src/ ) dkms just for the running kernel

```
sudo dkms remove 8192cu -v [COLOR="#FF0000"]3.1.2590[/COLOR] -k $(uname -r)
``` where the highlighted number in red matches the PACKAGE VERSION= line in /usr/src/rtl8192cu-3.3.23192/dpkg.conf

The version can be found by ```
cat /usr/src/rtl8192cu-3.3.23192/dpkg.conf | grep PACKAGE_VERSION
```

NB dkms is probably going to remove the one found in /lib/modules/3.2.0-38-generic/updates/

---

### Post by sully101 on 2013-03-09
Yes .ko files are the actual modules :) The problem you have is youve actually got three of them 

1. dkms is building the one in /usr/src every time you do a kernel upgrade 8192cu.ko
2. There is a default one in the kernel rtl8192cu.ko
3. There is a new one you have been building with the /home/......./drivers/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 also called 8192cu.ko

We have to tell the system to ignore all the others before we can get the one you want to load. When ubuntu boots it loads the one built from /usr/src/path to whatever/ unfortunately that one aint working. We need to either get dkms to make the new module when you install a new kernel, or just make the new one and install it for this kernel. The former is probably the best option, the latter the easiest.

---

### Post by sully101 on 2013-03-09
Yes .ko files are the actual modules :) The problem you have is youve actually got three of them 

1. dkms is building the one in /usr/src every time you do a kernel upgrade 8192cu.ko
2. There is a default one in the kernel rtl8192cu.ko
3. There is a new one you have been building with the /home/......./drivers/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105 also called 8192cu.ko

We have to tell the system to ignore all the others before we can get the one you want to load. When ubuntu boots it loads the one built from /usr/src/path to whatever/ unfortunately that one aint working. We need to either get dkms to make the new module when you install a new kernel, or just make the new one and install it for this kernel. The former is probably the best option, the latter the easiest.

NB refering to the points above
1. we moved the module out of the way with "sudo mv /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.ko /lib/modules/3.2.0-38-generic-pae/updates/dkms/8192cu.wasako" but the system still wants to load it

2. we told the system not to ever load rtl8192cu.ko "/etc/modprobe.d/blacklist-rtl8192.conf" should contain a line "blacklist rtl8192cu"

We need to get to a point where the system doesnt load the "dkms" one or "default" one and just loads the one youve built.

The sudo "dkms remove 8192cu -v 3.1.2590 -k $(uname -r)" tells it to stop building the module from /usr/src/rtl8192cu-3.3.23192/ and remove it

---

### Post by Kariotaki on 2013-03-09
Here is the output. It looks like it didn't do anything. 

> xristaras@xristaras-linux:~$ cat /usr/src/rtl8192cu-3.3.23192/dpkg.conf | grep PACKAGE_VERSION
cat: /usr/src/rtl8192cu-3.3.23192/dpkg.conf: No such file or directory
xristaras@xristaras-linux:~$ 
xristaras@xristaras-linux:~$ cat /usr/src/rtl8192cu-3.3.23192/dpkg.conf | grep PACKAGE_VERSION
cat: /usr/src/rtl8192cu-3.3.23192/dpkg.conf: No such file or directory
xristaras@xristaras-linux:~$ sudo dkms remove 8192cu -v 3.3.23192 -k $(uname -r)[sudo] password for xristaras: 
Error! There are no instances of module: 8192cu
3.3.23192 located in the DKMS tree.




---

### Post by sully101 on 2013-03-09
it might be in a different directiry have a look in ypur /usr/src directory it could be named something else

---

### Post by Kariotaki on 2013-03-09
It doesn't seem to be in the directory 3.1.2590 either

> xristaras@xristaras-linux:~$ sudo  dkms remove 8192cu -v 3.1.2590 -k $(uname -r)[sudo] password for xristaras: 
Error! There are no instances of module: 8192cu
3.1.2590 located in the DKMS tree.
xristaras@xristaras-linux:~$ 


The only other folder in the /usr/src directory that has a dkms.conf folder is here: /usr/src/nvidia-current-updates-304.64

---

### Post by Kariotaki on 2013-03-09
[ATTACH=CONFIG]239990[/ATTACH]
The is where I see reference to the driver.

---

### Post by sully101 on 2013-03-09
Could you post the output of ```
ls -lha /var/lib/dkms
``` dkms should have made a copy there when the old one was installed

---

### Post by Kariotaki on 2013-03-09
Here is the output: 

> xristaras@xristaras-linux:~$ ls -lha /var/lib/dkms
total 20K
drwxr-xr-x  4 root root 4.0K Feb  9 19:41 .
drwxr-xr-x 64 root root 4.0K Feb 27 18:53 ..
-rw-r--r--  1 root root    6 Jul  8  2008 dkms_dbversion
drwxr-xr-x  3 root root 4.0K Feb 21 20:07 nvidia-current-updates
drwxr-xr-x  3 root root 4.0K Feb 21 20:07 rtl8192cu
xristaras@xristaras-linux:~$ 


---

### Post by sully101 on 2013-03-09
OK getting closer :)
```
dkms status
``` should show the version number

So the module name being built by dkms is rtl8192cu.. So our command would be "sudo dkms remove rtl8192cu -v 3.1.2590 -k $(uname -r)" hopefully

---

### Post by Kariotaki on 2013-03-09
Most likely a root issue, eh?

> xristaras@xristaras-linux:~$ dkms status
Command 'dkms' is available in '/usr/sbin/dkms'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
dkms: command not found
xristaras@xristaras-linux:~$ 

Should I execute the command?
[COLOR=#000000]sudo dkms remove rtl8192cu -v 3.1.2590 -k $(uname -r)[/COLOR]

---

### Post by sully101 on 2013-03-10
yes give it a go

---

### Post by Kariotaki on 2013-03-10
No cigar...

> xristaras@xristaras-linux:~$ sudo dkms remove rtl8192cu -v 3.1.2590 -k $(uname -r)
[sudo] password for xristaras: 
Error! There are no instances of module: rtl8192cu
3.1.2590 located in the DKMS tree.


---

### Post by sully101 on 2013-03-10
try "sudo dkms status"

---

### Post by Kariotaki on 2013-03-10
Here is the output: 
> xristaras@xristaras-linux:~$ sudo dkms status
nvidia-current-updates, 304.64, 3.2.0-37-generic-pae, i686: installed
nvidia-current-updates, 304.64, 3.2.0-38-generic, i686: installed
nvidia-current-updates, 304.64, 3.2.0-38-generic-pae, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-35-generic-pae, i686: installed (WARNING! Diff between built and installed module!)
rtl8192cu, 3.3.23192, 3.2.0-36-generic-pae, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-37-generic, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-37-generic-pae, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-38-generic, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-38-generic-pae, i686: installed (WARNING! Diff between built and installed module!)
xristaras@xristaras-linux:~$ 


---

### Post by sully101 on 2013-03-10
"sudo dkms remove rtl8192cu -v 3.3.23192 -k 3.2.0-38-generic" and "sudo dkms remove rtl8192cu -v 3.3.23192 -k 3.2.0-38-generic-pae" then do the sudo dkms status again and we should have got rid of the last two lines.

---

### Post by Kariotaki on 2013-03-10
I found these instructions in the documents folder. Are they at all useful:

[SIZE=2]To placeour driver into kernel tree and build with kernel, for example, underthe folder &#8220;drivers/net/wireless/&#8221;, you can do as followings:[/SIZE]



[LIST=1]	
[*][SIZE=2]Copy	our driver into drivers/net/wireless/ and rename it as rtl8192cu,	for example.[/SIZE]

[*][SIZE=2]Add	[COLOR=#ff0000]obj-$(CONFIG_RTL8192CU)  += rtl8192cu/[/COLOR]	into drivers/net/wireless/Makefile:[/SIZE]

[*][SIZE=2]Add	[COLOR=#ff0000]source	"drivers/net/wireless/rtl8192cu/Kconfig"[/COLOR] into	drivers/net/wireless/Kconfig[/SIZE]

[*][SIZE=2]Config	kernel, for example, with &#8220;make menuconfig&#8221; command  to select y	or m for our driver[/SIZE]

[*][SIZE=2]Build	kernel with &#8220;make&#8221; command[/SIZE]
[/LIST]

---

### Post by Kariotaki on 2013-03-10
Okay. Followed the commands you gave. Here is the output:

> xristaras@xristaras-linux:~$ sudo dkms status
nvidia-current-updates, 304.64, 3.2.0-37-generic-pae, i686: installed
nvidia-current-updates, 304.64, 3.2.0-38-generic, i686: installed
nvidia-current-updates, 304.64, 3.2.0-38-generic-pae, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-35-generic-pae, i686: installed (WARNING! Diff between built and installed module!)
rtl8192cu, 3.3.23192, 3.2.0-36-generic-pae, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-37-generic, i686: installed
rtl8192cu, 3.3.23192, 3.2.0-37-generic-pae, i686: installed
xristaras@xristaras-linux:~$

---

### Post by sully101 on 2013-03-10
We can now go back to post [#33]("http://ubuntuforums.org/showthread.php?t=2121058&p=12550055#post12550055")
> So now when you reboot is the module loaded automatically? ie
Reboot ...
open terminal and do "lsmod | grep 8192", if that command returns nothing do a "sudo modprobe 8192cu" to load the module. Does it work ? 

---

### Post by sully101 on 2013-03-10
RE: post [#51]("http://ubuntuforums.org/showthread.php?t=2121058&p=12550471#post12550471")This seems to be refering to building the module into the kernel source something quite different

---

### Post by Kariotaki on 2013-03-10
You did it! Thank you so much! As soon as I rebooted, the wireless stick loaded automatically and the connection was automatic. 

One last question....

Just so I know in the future, each time there is a kernel update, what must I do to ensure that the device will work?

---

### Post by sully101 on 2013-03-10
Good to hear :D I might go have a beer tonight. Re: future kernel updates I would 

[LIST=1]
[*]First check that the new module included in the new kernel doesnot infact work by commenting out or removing the line in the /etc/modprobe.d/blacklist-rtl8192.conf. eg "rtl8192cu" to "#rtl8192cu", this will let it load the default included module. Then comment out or remove the line in /etc/modules that relates to your module eg. change the line "8192cu" to "#8192cu" so it wont try to load the module you built for the old kernel at boot ( it shouldnt be able to find it anyway until you rebuild it ) reboot in to your shiny new kernel and give it a try.
[*]Consider installing a backport package if you havn't already. [https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports") probably something like ```
sudo apt-get install linux-backports-modules-cw-generic
``` NB. you may have to enable the repository in Software Centre > Edit > Software sources >Updates > Unsupported updates (precise proposed) It might have a new module for your hardware it might not. I havnt looked into it.
[*]Have a google search sometimes some nice person has a ppa (personal package archive) that you can just add to your sources list and then install their package
[*]If all else fails rebuild from the driver you downloaded mwdinstall.sh ( now dkms is out of the way it shouldnt interfere anymore )
[/LIST]

Apparently marking a thread as solved is broken there is a workaround here [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by Kariotaki on 2013-03-11
Thanks again!
So as long as I put the # before the rtl it should work.
Is there a code to comment out lines, or do I go on to text editor?

---

### Post by sully101 on 2013-03-11
The "#" is code for comment in these particular files. Not all configuration files are formatted the same, some use "//" or "/*" but the ones you will want to edit are. FYI To read the manual from the terminal type man in front of it ie ```
man modules
``` so when you put a # in front of the line the whole line will be ignored. *Hint press q to quit from reading a man page*

There is a code for everything :) but you should probably use a text editor such as nano. ```
man nano
``` You could start reading here [https://help.ubuntu.com/community/Nano]("https://help.ubuntu.com/community/Nano") and here [https://help.ubuntu.com/community]("https://help.ubuntu.com/community"). 

NB* There are some important points in the online documentation for nano*
NB* You have to be "root" to edit the files above eg* ```
sudo nano -w /etc/modules
```

---

