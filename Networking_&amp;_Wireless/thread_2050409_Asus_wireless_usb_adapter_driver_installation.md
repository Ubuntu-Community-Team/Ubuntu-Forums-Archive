---
title: "Asus wireless usb adapter driver installation"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by harlie on 2012-08-30
I need help to install the driver for Asus wusb n-13. I downloaded the driver but it says it has to be compiled, I don't know how to do this can someone give me full instruction for compiling in terminal? I sometimes can't tell when a space is needed so please double space where you would normally only single space. using 12.04 now.

thanks harlie

---

### Post by chili555 on 2012-08-30
There are a couple of versions of this device and the two versions have different chipsets. Let's identify which you have. Insert the device and run and post:```
lsusb
```Thanks.

---

### Post by harlie on 2012-08-31
> **chili555 said:**
> There are a couple of versions of this device and the two versions have different chipsets. Let's identify which you have. Insert the device and run and post:```
lsusb
```Thanks.


this is the result of lsusb

Bus 001 Device 004 ID obo5:17ab Asustek computer,Inc.

---

### Post by chili555 on 2012-08-31
Here are some very good instructions: [http://ubuntuforums.org/showpost.php?p=11713923&postcount=2](http://ubuntuforums.org/showpost.php?p=11713923&postcount=2)

---

### Post by harlie on 2012-08-31
> **chili555 said:**
> Here are some very good instructions: [http://ubuntuforums.org/showpost.php?p=11713923&postcount=2](http://ubuntuforums.org/showpost.php?p=11713923&postcount=2)


I will check it out thanks.

---

### Post by harlie on 2012-08-31
> **chili555 said:**
> Here are some very good instructions: [http://ubuntuforums.org/showpost.php?p=11713923&postcount=2](http://ubuntuforums.org/showpost.php?p=11713923&postcount=2)


I will check it out thanks.

---

### Post by harlie on 2012-08-31
> **chili555 said:**
> Here are some very good instructions: [http://ubuntuforums.org/showpost.php?p=11713923&postcount=2](http://ubuntuforums.org/showpost.php?p=11713923&postcount=2)


Strange when I click on this address or enter it manually it takes me to a German portal with German language.???? am I doing something wrong?

---

### Post by chili555 on 2012-08-31
What?? You don't read German fluently?

The most current version of rtl8192cu actually covers your device. Let's see what you have installed and see what we can do:```
modinfo rtl8192cu | grep 17AB
```Do you get output, that is, your device ID from that command? Depending on what you have on your default (not yet updated with 195 updates, I assume) install, tells us what we need to do next.

The German method is slick but we may be able to bypass it.

---

### Post by harlie on 2012-08-31
> **chili555 said:**
> What?? You don't read German fluently?

The most current version of rtl8192cu actually covers your device. Let's see what you have installed and see what we can do:```
modinfo rtl8192cu | grep 17AB
```Do you get output, that is, your device ID from that command? Depending on what you have on your default (not yet updated with 195 updates, I assume) install, tells us what we need to do next.

The German method is slick but we may be able to bypass it.

this gives    alias:   usb v0b05p17ABd*dc*dcs*dp*ic*ics*ip*

---

### Post by harlie on 2012-08-31
> **harlie said:**
> this gives    alias:   usb v0b05p17ABd*dc*dcs*dp*ic*ics*ip*



Would it be murder if I took an Axe  and chopped my pc up in small pieces?

---

### Post by chili555 on 2012-08-31
> alias: usb v[COLOR="Red"]0b05[/COLOR]p[COLOR="Red"]17AB[/COLOR]d*dc*dcs*dp*ic*ics*ip*Good news! Your device is covered. Let's load the driver and see if there are interesting messages:```
sudo modprobe rtl8192cu
dmesg | grep -i rtl
```> Would it be murder if I took an Axe and chopped my pc up in small pieces? Don't give up yet. We will endeavor to persevere.

---

### Post by harlie on 2012-09-01
> **chili555 said:**
> Good news! Your device is covered. Let's load the driver and see if there are interesting messages:```
sudo modprobe rtl8192cu
dmesg | grep -i rtl
```Don't give up yet. We will endeavor to persevere.

sudo modprobe rtl8192cu  returns nothing after asking for sudoers password which I give, Then dmasg | grep -i rtl gives a long string of text ending with[99.442794] [dcaf77787]-rtl-rx-completed+oc1f0[rtlwifi]

I like the sound of endevoring to persevere. sounds like chief Dan George.

---

### Post by chili555 on 2012-09-01
> dmasg | grep -i rtl Please check your work. It's actually:```
dm[COLOR="Red"]e[/COLOR]sg | grep -i rtl 
```I hoped to see the entire text as it hopefully contains some clues as to what's going wrong. If you are having trouble getting it from your Ubuntu machine to the computer from which you are posting, make the output into a text document:```
dmesg | grep -i rtl > harlie.txt
```Find the file harlie.txt in your user directory and transfer it on a USB key or similar.

---

### Post by harlie on 2012-09-01
> **chili555 said:**
> Please check your work. It's actually:```
dm[COLOR=Red]e[/COLOR]sg | grep -i rtl 
```I hoped to see the entire text as it hopefully contains some clues as to what's going wrong. If you are having trouble getting it from your Ubuntu machine to the computer from which you are posting, make the output into a text document:```
dmesg | grep -i rtl > harlie.txt
```Find the file harlie.txt in your user directory and transfer it on a USB key or similar.
 
 Ok lets see if I can cut and paste or something like that.harlie@harlie-DQ175A-ABA-A420N:~$ dmesg | grep -i rtl
[   20.386176] rtl8192cu: MAC address: c8:60:00:d3:7a:15
[   20.386187] rtl8192cu: Board Type 0
[   20.621106] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   20.818904] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.833730] usbcore: registered new interface driver rtl8192cu
[   27.377796] rtl8192cu: MAC auto ON okay!
[   27.411557] rtl8192cu: Tx queue select: 0x05
[   27.412373] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
harlie@harlie-DQ175A-ABA-A420N:~$

---

### Post by harlie on 2012-09-04
Here is the output of    dmesg | grep -i rtl.

harlie@harlie-DQ175A-ABA-A420N:~$ dmesg | grep -i rtl
harlie@harlie-DQ175A-ABA-A420N:~$ dmesg | grep -i rtl
harlie@harlie-DQ175A-ABA-A420N:~$ dmesg | grep -i rtl
harlie@harlie-DQ175A-ABA-A420N:~$ 


Funny that it worked before and not now. Anyway it is posted to your last message as an edit.

Harlie

This version (12.04) has never acted right since the upgrade.

---

### Post by harlie on 2012-09-04
Ok so maybe the device has to be plugged in?????????????

harlie@harlie-DQ175A-ABA-A420N:~$ dmesg | grep -i rtl
[   20.178021] rtl8192cu: MAC address: c8:60:00:d3:7a:15
[   20.178034] rtl8192cu: Board Type 0
[   20.565773] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   20.626669] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   20.627547] usbcore: registered new interface driver rtl8192cu
[   20.697424] rtl8192cu: MAC auto ON okay!
[   20.733931] rtl8192cu: Tx queue select: 0x05
[   20.734563] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
harlie@harlie-DQ175A-ABA-A420N:~$

---

### Post by chili555 on 2012-09-04
> Ok so maybe the device has to be plugged in?????????????It generally helps! So now do you have a wireless interface?```
iwconfig
```My patience with the built-in rtl8192cu is rapidly waning. Unless we get a hopeful result quickly, I am about to suggest radical steps...

I am working on another rtl8192cu case here that's just as dismal.

---

### Post by harlie on 2012-09-04
NO  still no interface will try iwconfig and stick the result here.harlie@harlie-DQ175A-ABA-A420N:~$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

harlie@harlie-DQ175A-ABA-A420N:~$

---

### Post by chili555 on 2012-09-04
Isn't wlan1 your USB? Does it scan?```
sudo iwlist wlan1 scan
rfkill list all
```

---

### Post by harlie on 2012-09-04
harlie@harlie-DQ175A-ABA-A420N:~$ sudo iwlist wlan1 scan rfkill list all
[sudo] password for harlie: 
Invalid scanning option [rfkill]
harlie@harlie-DQ175A-ABA-A420N:~$

---

### Post by chili555 on 2012-09-04
Commands on two lines are two separate commands. Like this:```
sudo iwlist wlan1 scan
```Note the result and copy it into your reply; then:```
rfkill list all
```Note the result and copy it into your reply. Sorry if I wasn't clear.

---

### Post by harlie on 2012-09-04
My mistake also.

harlie@harlie-DQ175A-ABA-A420N:~$ sudo iwlist wlan1 scan
[sudo] password for harlie: 
wlan1     No scan results

harlie@harlie-DQ175A-ABA-A420N:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
harlie@harlie-DQ175A-ABA-A420N:~$

---

### Post by chili555 on 2012-09-04
I've just about concluded that the built-in rtl8192cu is not going to work in my lifetime. We can try two things. The first is:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic [COLOR="Red"]<--or -pae if you are running a PAE kernel[/COLOR]
```Find out about PAE:```
uname -r
```If -pae is mentoned, include it and not if not.

Reboot and tell us how it's working. If it's not, Plan 2!

---

### Post by harlie on 2012-09-04
Not working but when I click on the wireless icon I now have some new networks shown that were not previously there.

Time for me to quit for tonight, will return to the grind stone tomorrow afternoon.

---

### Post by harlie on 2012-09-05
Ok I am ready for plan 2 (briskly rubbing hands together).

---

### Post by chili555 on 2012-09-05
First we need to blacklist rtl8192cu:```
sudo su
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
modprobe -r rtl8192cu
exit
```Then proceed as here in posts #13 and following: [http://ubuntuforums.org/showthread.php?t=2053044&page=2&highlight=8192cu](http://ubuntuforums.org/showthread.php?t=2053044&page=2&highlight=8192cu)

As always, post back if you get stuck.

---

### Post by harlie on 2012-09-05
Thank you I did the command ok now will go to the site you specify. And again thanks forr your assistance.

Harlie

---

### Post by harlie on 2012-09-06
This is not working for me here is what happens.

harlie@harlie-DQ175A-ABA-A420N:~$ cd Desktop/RTL81
bash: cd: Desktop/RTL81: No such file or directory
harlie@harlie-DQ175A-ABA-A420N:~$ 

Earlier (a few minutes ago) I got it to change directories, then when I did the command

sudo su      then password then
./install.sh     it says permission denied

Now I am lost again.

---

### Post by harlie on 2012-09-06
That was an error let me try again to show what I did and the resultharlie@harlie-DQ175A-ABA-A420N:~$ cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/         
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$  sudo su
[sudo] password for harlie: 
root@harlie-DQ175A-ABA-A420N:/home/harlie/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622# ./install.sh
bash: ./install.sh: Permission denied
root@harlie-DQ175A-ABA-A420N:/home/harlie/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622#

When I try to close terminal it says a process is still running and it I close it will be lost.

---

### Post by chili555 on 2012-09-06
> **harlie said:**
> That was an error let me try again to show what I did and the resultharlie@harlie-DQ175A-ABA-A420N:~$ cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/         
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$  sudo su
[sudo] password for harlie: 
root@harlie-DQ175A-ABA-A420N:/home/harlie/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622# ./install.sh
bash: ./install.sh: Permission denied
root@harlie-DQ175A-ABA-A420N:/home/harlie/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622#

When I try to close terminal it says a process is still running and it I close it will be lost.If the terminal is still open, please do:```
chmod +x install.sh
./install.sh
modprobe 8192cu
exit
```Thanks.

---

### Post by harlie on 2012-09-07
> **chili555 said:**
> If the terminal is still open, please do:```
chmod +x install.sh
./install.sh
modprobe 8192cu
exit
```Thanks.
harlie@harlie-DQ175A-ABA-A420N:~$ cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/  sudo su
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ ./install.sh
bash: ./install.sh: Permission denied
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$   chmod +x install.sh
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ ./install .sh
bash: ./install: No such file or directory
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ ./install.sh
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622.tar.gz
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/Makefile
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/Kconfig
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/clean
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622
Authentication requested [root] for make clean:
Password: 
su: Authentication failure
Authentication requested [root] for make driver:
Password: 
su: Authentication failure
##################################################
Compile make driver error: 1
Please check error Mesg
##################################################
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$  modprobe 8192cu
FATAL: Module 8192cu not found.
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$

---

### Post by chili555 on 2012-09-07
If you properly did 'sudo su' then this:> [COLOR="Red"]harlie[/COLOR]@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622[COLOR="Red"]**$**[/COLOR] ./install.sh...would have become this:> [COLOR="Red"]root[/COLOR]@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622[COLOR="Red"]**#**[/COLOR] ./install.shHere is an example from my machine:> chili@LAPTOP60:~$ sudo su
[sudo] password for chili: 
[COLOR="Red"]root[/COLOR]@LAPTOP60:/home/chili[COLOR="Red"]# [/COLOR]
Please try again.

---

### Post by harlie on 2012-09-07
> **chili555 said:**
> If you properly did 'sudo su' then this:...would have become this:Here is an example from my machine:Please try again.


I will try again.harlie@harlie-DQ175A-ABA-A420N:~$ cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/sudo su
bash: cd: Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/sudo: No such file or directory
harlie@harlie-DQ175A-ABA-A420N:~$ sudo su
[sudo] password for harlie: 
root@harlie-DQ175A-ABA-A420N:/home/harlie# ./install.sh
bash: ./install.sh: No such file or directory
root@harlie-DQ175A-ABA-A420N:/home/harlie# 


  


harlie@harlie-DQ175A-ABA-A420N:~$ cd Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622/ sudo su
harlie@harlie-DQ175A-ABA-A420N:~/Desktop/RTL8188C_8192C_USB_linux_v3.4.3_4369.20120622$ ./install.sh
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622.tar.gz
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_xmit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_query.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/efuse/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/efuse/rtw_efuse.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_recv.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_br_ext.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_eeprom.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_debug.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_p2p.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ieee80211.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_security.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_cmd.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_sta_mgt.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_rf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_pwrctrl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_wlan_util.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mlme_ext.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_io.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_rtl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_mp_ioctl.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_ioctl_set.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/core/rtw_iol.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/wlan0dhcp
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/osdep_service.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/recv_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/os_intfs.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/usb_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/mlme_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/pci_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/sdio_intf.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/rtw_android.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/xmit_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/os_dep/linux/ioctl_cfg80211.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/wlan_bssdef.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/cmd_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mlme_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/wifi.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/farray.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_dm.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_android.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_recv.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/nic_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_dm.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_event.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_qos.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_pwrctrl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_ce_service.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ieee80211.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/recv_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_linux.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_efuse.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_ce.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUTestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ht.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ioctl_cfg80211.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ethernet.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/mp_custom_oid.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_rtl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_linux.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_spec.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mlme.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/hal_init.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ieee80211_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_ce.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CPhyCfg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/swab.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/swabb.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/big_endian.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/little_endian.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/byteorder/generic.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_ops_xp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DETestHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192CEHWImg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_p2p.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_conf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_vendor_req.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_service.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DUHWImg_wowlan.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_query.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_eeprom.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/drv_types_xp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_byteorder.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_xmit.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_version.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl_set.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/h2clbk.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_osintf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192d_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/pci_ops.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_cmd.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_event.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/mlme_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_debug.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/osdep_intf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sta_info.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_iol.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp_phy_regdef.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_rf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/usb_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/autoconf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_security.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/sdio_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_io.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/Hal8192DPhyReg.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_br_ext.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/circ_buf.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/basic_types.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_hal.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/ip.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_led.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/if_ether.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/xmit_osdep.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtl8192c_sreset.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_mp.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/include/rtw_ioctl.h
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/ifcfg-wlan0
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/Makefile
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/Kconfig
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/hal_init.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_cmd.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_phycfg.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_dm.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_mp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rxdesc.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_rf6052.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_led.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_halinit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_recv.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/Hal8192CUHWImg_wowlan.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_ce.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/Hal8192CUHWImg.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_linux.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/rtl8192cu_xmit.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/usb/usb_ops_xp.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_sreset.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/hal/rtl8192c/rtl8192c_hal_init.c
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622/clean
rtl8188C_8192C_usb_linux_v3.4.3_4369.20120622
Authentication requested [root] for make clean:
Password: 
su: Authentication failure
Authentication requested [root] for make driver:
Password: 


This is not working I am definitely giving the correct password but it is not accepted.

Ok I finally got to the bottom where it said setup complete, so I guess I should reboot and try it.?

---

### Post by harlie on 2012-09-07
No luck for a few minutes the light on the device was lit but still would not communicate, then the light on the wusb went out and stays off now. Also the screen asking for the password for wireless pops up every few seconds or minutes. I click to enable the password but no change then it asks for password again.

---

### Post by chili555 on 2012-09-07
OK, diagnostics are in order:```
modinfo 8192cu
dmesg | grep 8192
iwconfig
lsmod | grep 8192
```

---

### Post by harlie on 2012-09-07
> **chili555 said:**
> OK, diagnostics are in order:```
modinfo 8192cu
dmesg | grep 8192
iwconfig
lsmod | grep 8192
```
harlie@harlie-DQ175A-ABA-A420N:~$ modinfo 8192cu
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/8192cu.ko
version:        v3.4.3_4369.20120622
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     FC509A1A4CDA0D05860BC6D
alias:          usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0061d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p624Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2103d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp2102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0091d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p1201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3358d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3359d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4856p0091d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp5088d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3357d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4855p0090d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp018Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.2.0-29-generic SMP mod_unload modversions 686 
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:charp
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_force_iol:Force to enable IOL (bool)
parm:           rtw_intel_class_mode:The intel class mode [0: off, 1: on] (uint)
parm:           rtw_mc2u_disable:int
harlie@harlie-DQ175A-ABA-A420N:~$ dmesg | grep 8192
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.171098] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.171118] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[   18.890708] CHIP TYPE: RTL8188C_8192C
[   18.897740] ====> ReadAdapterInfo8192C
[   23.296978] readAdapterInfo_8192CU(): REPLACEMENT = 1
[   23.296982] <==== ReadAdapterInfo8192C in 4400 ms
[   23.304584] usbcore: registered new interface driver rtl8192cu
[   25.457015] rtl8192cu_hal_init in 2096ms
harlie@harlie-DQ175A-ABA-A420N:~$ iwconfig
lo        no wireless extensions.

wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

harlie@harlie-DQ175A-ABA-A420N:~$ lsmod | grep 8192
8192cu                502394  0 
harlie@harlie-DQ175A-ABA-A420N:~$ lsmod | grep 8192[/code][/quote]
8192cu                502394  0 
harlie@harlie-DQ175A-ABA-A420N:~$

---

### Post by chili555 on 2012-09-07
All this looks almost normal. Why is your interface wlan**1**? Is there another internal device we need to blacklist? May I see:```
cat /etc/udev/rules.d/70-persistent-net.rules
```Network Manager will probably have trouble juggling two wireless devices.

---

### Post by harlie on 2012-09-08
> **chili555 said:**
> All this looks almost normal. Why is your interface wlan**1**? Is there another internal device we need to blacklist? May I see:```
cat /etc/udev/rules.d/70-persistent-net.rules
```Network Manager will probably have trouble juggling two wireless devices.
harlie@harlie-DQ175A-ABA-A420N:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1106:0x3065 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0e:a6:78:60:b6", 

ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x13b1:0x003a (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="20:aa:4b:62:13:1b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0b05:0x17ab (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="c8:60:00:d3:7a:15", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x0b05:0x17ab (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:4c:81:92:b7", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
harlie@harlie-DQ175A-ABA-A420N:~$

I see several wireless networks listed when I open the wireless configuration window and I can not remopve them. They have a lock symbol beside them.

---

### Post by chili555 on 2012-09-08
> I see several wireless networks listed when I open the wireless configuration window and I can not remove them. They have a lock symbol beside them.Why do you want to remove them?? They have a lock indicating they are protected with encryption. The little lock is saying, roughly, 'if you have a key, I will let you in.' That's perfectly normal.

It looks like you have tried three (!!) different USB wireless devices. We have no internal device fighting us. What does this tell us?```
nm-tool
```

---

### Post by harlie on 2012-09-08
> **chili555 said:**
> Why do you want to remove them?? They have a lock indicating they are protected with encryption. The little lock is saying, roughly, 'if you have a key, I will let you in.' That's perfectly normal.

It looks like you have tried three (!!) different USB wireless devices. We have no internal device fighting us. What does this tell us?```
nm-tool
```
harlie@harlie-DQ175A-ABA-A420N:~$ ```
nm-tool
```[/quote]
bash: ```
nm-tool
```[/quote]: No such file or directory
harlie@harlie-DQ175A-ABA-A420N:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        00:0E:A6:78:60:B6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.10.10.138
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.10.1

    DNS:             192.168.1.254
    DNS:             10.10.10.1


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        C8:60:00:D3:7A:15

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WirelessHomeNetwork: Infra, 2C:B0:5D:34:E7:B3, Freq 2437 MHz, Rate 44 Mb/s, Strength 46 WPA2
    NETGEAR-Guest:   Infra, CA:3D:C7:A7:EF:E1, Freq 2422 MHz, Rate 16 Mb/s, Strength 10
    harlie:          Infra, 20:AA:4B:38:74:85, Freq 2437 MHz, Rate 16 Mb/s, Strength 100 WPA2


harlie@harlie-DQ175A-ABA-A420N:~$ 


I thought you were indicating that there may be too many networks??   Any way I had a Linksys wusb device that I could not make work so I returned it and bought the Asus. Those are the only wireless devices ever connected to this pc.

Correction, there was once a wireless mouse connected which was removed when I got my new computer.

I have no idea why the thing is called wlan1 I guess that is what ubuntu likes????

Harlie

---

### Post by harlie on 2012-09-13
I still need help if you are willing to try to solve this. Thanks.

Harlie

---

### Post by chili555 on 2012-09-14
> - Device: wlan1 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8192cu
State: disconnected
Default: no
HW Address: C8:60:003:7A:15

Capabilities:

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
WirelessHomeNetwork: Infra, 2C:B0:5D:34:E7:B3, Freq 2437 MHz, Rate 44 Mb/s, Strength 46 WPA2
NETGEAR-Guest: Infra, CA:3D:C7:A7:EF:E1, Freq 2422 MHz, Rate 16 Mb/s, Strength 10
[COLOR="Red"]harlie: Infra, 20:AA:4B:38:74:85, Freq 2437 MHz, Rate 16 Mb/s, Strength 100 WPA2[/COLOR]
So you've compiled a driver, you see networks when you click the Network Manager icon and it sees yours. What happens then? Are you asked for your WPA2 password? Have you double- and triple-checked your password?

---

### Post by harlie on 2012-09-14
I will check these items and let you know what I see. Will be back shortly. 

Harlie

---

### Post by harlie on 2012-09-14
Ok here is what I see: in system settings/ network I see the wired network which works ok, there is no wireless net shown. At top of desktop clicking Edit connections shows:
Wireless networks
 harlie never used
wireless connection 1 never used
Netgear-guest   never used 
show password gives harlie1947

Wusb no longer lights up when the pc is started or anytime while pc is on.

lsusb does not show the device now.

---

### Post by chili555 on 2012-09-14
> lsusb does not show the device now.Without more information, I'd suspect the device or the USB bus may be defective. I wonder if there is anything significant here:```
sudo lsusb -v
```

---

### Post by harlie on 2012-09-14
bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength              11
  bDescriptorType      41
  nNbrPorts             8
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00 0x00
  PortPwrCtrlMask    0xff 0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0503 highspeed power enable connect
   Port 7: 0000.0100 power
   Port 8: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.02
  iManufacturer           3 Linux 3.2.0-30-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0303 lowspeed power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.02
  iManufacturer           3 Linux 3.2.0-30-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.02
  iManufacturer           3 Linux 3.2.0-30-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0001
  Self Powered

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            3.02
  iManufacturer           3 Linux 3.2.0-30-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:10.3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0300 lowspeed power
Device Status:     0x0001
  Self Powered

Bus 001 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0b05 ASUSTek Computer, Inc.
  idProduct          0x17ab 
  bcdDevice            2.00
  iManufacturer           1 Realtek
  iProduct                2 802.11n WLAN Adapter
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 002: ID 0461:4d0f Primax Electronics, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0461 Primax Electronics, Ltd
  idProduct          0x4d0f 
  bcdDevice            2.00
  iManufacturer           0 
  iProduct                2 USB Optical Mouse
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      71
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x9360 8-in-1 Media Card Reader
  bcdDevice            1.00
  iManufacturer           1  
  iProduct                2 USB Reader
  iSerial                 3 9206051
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)
harlie@harlie-DQ175A-ABA-A420N:~$

Wusb device lights in my other pc.

---

### Post by harlie on 2012-09-14
More and more I suspect a bad copy of upgrade from 11.10 to 12.04.  There are a few other things that act weird since the upgrade which was done via Internet . The  DVD would not work due to some error concerning a blacklisted file. I assume that was in 11.10. So what do you think of me trying again to upgrade via DVD? maybe if I specify a separate partition it might work? 

Harlie

---

### Post by harlie on 2012-09-17
Well now lsusb is showing the device but it still does not light on this computer. I have not done anything yet since the last post to, you where I asked if you thought it might be a good idea to reinstall 12.04.

Looking back I see the device was shown by  the commands I simply overlooked it. Sorry if this led us down the wrong path.   I do humbly apologize. 
Harlie

---

### Post by chili555 on 2012-09-18
> More and more I suspect a bad copy of upgrade from 11.10 to 12.04. There are a few other things that act weird since the upgrade which was done via Internet . The DVD would not work due to some error concerning a blacklisted file. I assume that was in 11.10. So what do you think of me trying again to upgrade via DVD? maybe if I specify a separate partition it might work?
I suggest you upgrade via the DVD. I am a big fan of a separate /home partition. That allows upgrades and even fresh installs without disturbing my valuable cat pictures, mp3s, etc.

You can also run the DVD live first to see how the wireless works. Frankly, rtl8192cu is a bit tricky.

---

### Post by harlie on 2012-09-18
Thank you, I will do this and see if it helps with the wireless and also some other problems I have  with pc since the upgrade. It worked perfectly with 11.10 but not with 12.04. I did not have the wusb when I had 11.10 installed.

Thanks for all your time I do appreciate your help and learned a good bit while working with you.

Harlie

---

### Post by harlie on 2012-09-24
Hi chilli555;
I am back to haunt you again. I reloaded 11.10,  (totally  impossible to reinstall 12.04 by any means). so I followed your instructions up to the compiling of the new driver. This was a success and the device lights and blinks on and off, I see the icon at the top of the page emitting but still no connection to wireless net. Also it still repeatedly prompts for the password. I am sure of the password so don't know what is next. Do you have time??

harlieharlie@harlie-DQ175A-ABA-A420N:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

harlie@harlie-DQ175A-ABA-A420N:~$ 
harlie@harlie-DQ175A-ABA-A420N:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:78:60:b6  
          inet addr:10.10.10.140  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe78:60b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14357374 (14.3 MB)  TX bytes:2608693 (2.6 MB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr c8:60:00:d3:7a:15  
          inet6 addr: fe80::ca60:ff:fed3:7a15/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:53 overruns:0 frame:0
          TX packets:46 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2934 (2.9 KB)  TX bytes:11239 (11.2 KB)

harlie@harlie-DQ175A-ABA-A420N:~$

---

### Post by harlie on 2012-09-28
For anyone who might be following this thread, I now know this is a problem with my computer and not specifically a Linux problem. I was able to try the device on another machine with ubuntu 12.04 and it worked   "out of the box" the one remaining problem on that machine is that the device repeatedly asks for the password even though I am certain I give it the correct one. However I saw a post on line about how to fix this, it was on an Asus site. still not solved the problem on the original machine yet. But still hopefull.

Harlie

Well the latest is, the device now works perfectly. The only thing I have done since above was to enter the command         sudo lshw  -c  network  then the device immediately started to work.
How long it will continue to work I don't know yet but after a couple of shut downs and restarts it still works. I guess for now I call this solved.

---

### Post by harlie on 2012-10-05
I just used the directions from chilli 555 after upgrading to 12.04 and the instruction works beautifully thanks again to  "The Doc". I started with the blacklisting then proceeded from there,  and in a few minutes I had beautiful success! chilli 555 is a miracle worker.

---

### Post by chili555 on 2012-10-05
Thank you for your kind words. I'm glad it's working.

---

### Post by harlie on 2012-10-08
> **chili555 said:**
> Thank you for your kind words. I'm glad it's working.

You are very welcome, thanks so much, my wife was getting fed up with me.
harlie

---

### Post by harlie on 2012-10-15
:mad:  Well here I am again, the device has worked perfectly until I installed updates Sunday eve.
Then it quit working completely, so if I do the sudo modprobe rtl8192cu and then dmesg | grep -i rtl  the device starts to work but showing a weak signal, and each time I shut off and restart the pc I have to enter the command again. I don't know whether to recompile or what, recall we have blacklisted one driver all ready. Will recompiling over write the apparently broken driver or create another?

Also I need a way to protect the driver from future updates once it is working properly again. Can you advise me on both issues?

Thanks 
Harlie

---

### Post by chili555 on 2012-10-15
> I don't know whether to recompile or what,Yes, recompile 8192cu.

Whenever a newer kernel version is installed by Update Manager, you need to rebuild the driver for the new kernel.

---

### Post by harlie on 2012-10-16
Ok thanks.   And can the driver not be protected from future updates?

Harlie

---

### Post by chili555 on 2012-10-16
> **harlie said:**
> Ok thanks.   And can the driver not be protected from future updates?

HarlieIt can with *dkms*, about which I am unfamiliar. Here is a starting place: [http://ubuntuforums.org/showthread.php?t=1964197](http://ubuntuforums.org/showthread.php?t=1964197)

See post #5.

---

### Post by harlie on 2012-10-16
Thanks for the help. I am slow but I am old. Where did you learn all this?  I keep looking for a manual with this kind of info but none I can find has anything about this type of trouble shooting. Even the Ubuntu Help site does not go there.

Harlie

---

### Post by chili555 on 2012-10-16
I am, no doubt, older. Hint: I have been retired since 1998 and I have a great-grandson!

I learned all this in eleven years in various Linux distros, trying and failing, re-installing and keeping many notes. My 'Forum' folder is a nice compact 3.1 GB! I decided a few years ago to specialize in one thing, networking and wireless, rather than be barely competent in many things. I enjoy learning more every day. I especially enjoy when a new product comes out and I get to figure out a driver using an existing close driver, awkwardness and duct-tape. Here, for example: [http://ubuntuforums.org/showpost.php?p=12206393&postcount=4](http://ubuntuforums.org/showpost.php?p=12206393&postcount=4)

---

### Post by harlie on 2012-10-17
I retired in 1995 so who is older? Hint I retired early. I am new to Linux and I love it even though I don't know that much about it. I got really tired of MS Windows still have it on the other pc for doing   Turbo Tax, wish I could run Turbo Tax in Linux, Well you can't have it all I guess.

Take care, hope I don't have to bother you again, but don't count on it :)

Harlie

---

### Post by harlie on 2012-12-03
Well here I am again, I had to revert to 11.10 and tried to follow your instructions to install the driver fot the ASUS wusb. However the kernel for my current install is a different one thus has a different driver so your instructions don't exactly match now.
I think I got rid of the installed driver (pretty sure of it)but from there on I can't make any progress. Mostly due to the fact I don't know how to correctly modify your instructions. Now I don't know what state the computer is in. Will you help me again with this? I don't really want to go back to 12.04 at this time because it is so flakey on this machine.

      Strange it works so well on the newer machine.

Harlie:confused:

I have a great grand daughter born past April.

---

### Post by chili555 on 2012-12-03
You need to do the step on post #26: [http://ubuntuforums.org/showpost.php?p=12220262&postcount=26](http://ubuntuforums.org/showpost.php?p=12220262&postcount=26)

Then do the steps here: [http://ubuntuforums.org/showpost.php?p=12219425&postcount=13](http://ubuntuforums.org/showpost.php?p=12219425&postcount=13)

You can skip the ndiswrapper step since I doubt you installed it. 

I'll be around to help for several more hours and then again tomorrow, so reply if you get stuck.> I have a great grand daughter born past April. Congratulations! They are fun, aren't they?

---

### Post by harlie on 2012-12-05
> **chili555 said:**
> You need to do the step on post #26: [http://ubuntuforums.org/showpost.php?p=12220262&postcount=26](http://ubuntuforums.org/showpost.php?p=12220262&postcount=26)

Then do the steps here: [http://ubuntuforums.org/showpost.php?p=12219425&postcount=13](http://ubuntuforums.org/showpost.php?p=12219425&postcount=13)

You can skip the ndiswrapper step since I doubt you installed it. 

I'll be around to help for several more hours and then again tomorrow, so reply if you get stuck.Congratulations! They are fun, aren't they?


Thanks, I will work on it this evening.        Yes fun but mine lives in Florida.

Harlie

---

### Post by harlie on 2012-12-06
Thank you again it is working again.   You are so much help.

ps I will be 66 in January.

Thanks
 Harlie

---

