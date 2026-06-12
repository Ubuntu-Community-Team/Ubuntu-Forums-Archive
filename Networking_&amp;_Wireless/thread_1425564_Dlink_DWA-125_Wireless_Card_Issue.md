---
title: "Dlink DWA-125 Wireless Card Issue"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by Tansonnhut on 2010-03-09
I recently installed Ubuntu and everything pretty much worked and what didn't I soon fixed however, the Dlink DWA-125 usb wireless card which I use won't work. I have searched in the forums and all the threads related to my problem are either incomplete (i.e. they gave up before solving it) or for advanced/skilled Ubuntu/Linux users.

If anyone has gotten the card to work please tell me how.

---

### Post by chili555 on 2010-03-09
Please open a terminal and do:```
sudo modprobe rt3070sta
iwconfig
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by rufuslucky on 2010-03-09
Can I ask what distro we are talking about so I can follow along?

---

### Post by rufuslucky on 2010-03-09
Here is what I got in karmic. 

balance@balance-desktop:~$ sudo modprobe rt3070sta 
balance@balance-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

balance@balance-desktop:~$ dmesg | grep -e rt2 -e rt3 
[    8.968968] Registered led device: rt2800usb-phy0::radio 
[    8.969000] Registered led device: rt2800usb-phy0::assoc 
[    8.969027] Registered led device: rt2800usb-phy0::quality 
[    8.969720] usbcore: registered new interface driver rt2800usb 
[   12.686221] rt2800usb 1-5:1.0: firmware: requesting rt2870.bin 
[  108.447758] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned. 
[  108.457337] usbcore: registered new interface driver rt2870 
balance@balance-desktop:~$ 

I'm not married to this distro though, so let me know if this would work better on one of the others.

---

### Post by Tansonnhut on 2010-03-09
Here is what I got from the terminal:

tansonnhut@acer:~$ sudo modprobe rt3070sta
[sudo] password for tansonnhut: 
FATAL: Error inserting rt3070sta (/lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
tansonnhut@acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tansonnhut@acer:~$ dmesg | grep -e rt2 -e rt3
[   93.061788] rt3070sta: Unknown symbol usb_alloc_urb
[   93.062064] rt3070sta: Unknown symbol usb_free_urb
[   93.062798] rt3070sta: Unknown symbol usb_register_driver
[   93.063398] rt3070sta: Unknown symbol usb_put_dev
[   93.063619] rt3070sta: Unknown symbol usb_get_dev
[   93.064087] rt3070sta: Unknown symbol usb_submit_urb
[   93.065110] rt3070sta: Unknown symbol usb_control_msg
[   93.065832] rt3070sta: Unknown symbol usb_deregister
[   93.066859] rt3070sta: Unknown symbol usb_kill_urb
[   93.067070] rt3070sta: Unknown symbol usb_buffer_free
[   93.067963] rt3070sta: Unknown symbol usb_buffer_alloc

And I am using Ubuntu 9.10 Karmic, I think that's the name.

Also, in case I have screwed anything up trying other solutions here is one of the solutions I tried which didn't work: [http://ubuntuforums.org/showthread.php?t=1289917](http://ubuntuforums.org/showthread.php?t=1289917)
I'm pretty sure that is why I get an error for sudo modprobe rt3070sta.

Thanks.

---

### Post by chili555 on 2010-03-09
@rufuslucky-

It looks like you have a driver conflict. First, let's see what driver you need. Please post:```
lsusb
lsmod | grep -e rt2 -e rt3
```Maybe a little blacklisting will get you going.

---

### Post by chili555 on 2010-03-09
@Tansonnhut-

It's pretty hard to follow what you did from the other thread. Please post:```
lsusb
dmesg | grep -e rt2 -e rt3
```Did you download and build a .tar.gz file?

For what it's worth, I think a lot of these issues are driver conflicts. Building yet another driver to further conflict does no good, as you see.

---

### Post by Tansonnhut on 2010-03-09
Ok, first I downloaded the RT3070_LinuxSTA_V2.3.0.1_20100208.tar.bz2 and extracted it to RT3070_LinuxSTA_V2.3.0.1_20100208. Then I ran the command sudo su and then make. I then ran make install which brought up no errors and just seemed to work. I then blacklisted the rt2800usb as well as the rt2x00usb. I then moved the old driver files from the /lib/modules/2.6.31-14-generic/kernel/drivers/staging/ and 2.6.31-20-generic. After that I tried to use the sudo modprobe rt3070sta however it returned the error from above.

lsusb:
Bus 002 Device 003: ID 07d1:3c0d D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04ca:002f Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 058f:6363 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c054 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg | grep -e rt2 -e rt3:
[   93.061788] rt3070sta: Unknown symbol usb_alloc_urb
[   93.062064] rt3070sta: Unknown symbol usb_free_urb
[   93.062798] rt3070sta: Unknown symbol usb_register_driver
[   93.063398] rt3070sta: Unknown symbol usb_put_dev
[   93.063619] rt3070sta: Unknown symbol usb_get_dev
[   93.064087] rt3070sta: Unknown symbol usb_submit_urb
[   93.065110] rt3070sta: Unknown symbol usb_control_msg
[   93.065832] rt3070sta: Unknown symbol usb_deregister
[   93.066859] rt3070sta: Unknown symbol usb_kill_urb
[   93.067070] rt3070sta: Unknown symbol usb_buffer_free
[   93.067963] rt3070sta: Unknown symbol usb_buffer_alloc
[  517.875991] rt3070sta: Unknown symbol usb_alloc_urb
[  517.876308] rt3070sta: Unknown symbol usb_free_urb
[  517.877042] rt3070sta: Unknown symbol usb_register_driver
[  517.877644] rt3070sta: Unknown symbol usb_put_dev
[  517.877864] rt3070sta: Unknown symbol usb_get_dev
[  517.878302] rt3070sta: Unknown symbol usb_submit_urb
[  517.879322] rt3070sta: Unknown symbol usb_control_msg
[  517.880062] rt3070sta: Unknown symbol usb_deregister
[  517.881094] rt3070sta: Unknown symbol usb_kill_urb
[  517.881309] rt3070sta: Unknown symbol usb_buffer_free
[  517.882202] rt3070sta: Unknown symbol usb_buffer_alloc
[ 1696.751897] rt3070sta: Unknown symbol usb_alloc_urb
[ 1696.752176] rt3070sta: Unknown symbol usb_free_urb
[ 1696.752948] rt3070sta: Unknown symbol usb_register_driver
[ 1696.753552] rt3070sta: Unknown symbol usb_put_dev
[ 1696.753773] rt3070sta: Unknown symbol usb_get_dev
[ 1696.754213] rt3070sta: Unknown symbol usb_submit_urb
[ 1696.755237] rt3070sta: Unknown symbol usb_control_msg
[ 1696.755961] rt3070sta: Unknown symbol usb_deregister
[ 1696.757003] rt3070sta: Unknown symbol usb_kill_urb
[ 1696.757215] rt3070sta: Unknown symbol usb_buffer_free
[ 1696.758112] rt3070sta: Unknown symbol usb_buffer_alloc

---

### Post by rufuslucky on 2010-03-09
balance@balance-desktop:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 07d1:3c0d D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
balance@balance-desktop:~$ lsmod | grep -e rt2 -e rt3 
rt3070sta             503348  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb 
rt2x00lib              29756  2 rt2800usb,rt2x00usb 
led_class               4096  1 rt2x00lib 
input_polldev           3716  1 rt2x00lib 
mac80211              181236  2 rt2x00usb,rt2x00lib 
cfg80211               93052  2 rt2x00lib,mac80211 
crc_ccitt               1852  1 rt2800usb 
balance@balance-desktop:~$ 


Chili, it looks like tansonnhut and I are going it two separate directions. Would you like me to start a new thread?

---

### Post by chili555 on 2010-03-09
> ID 07d1:3c0d D-Link System Your device is supposed to be supported by rt2800usb.> $ modinfo rt2800usb | grep 3C0D
alias:          usb:v[COLOR="Blue"]07D1[/COLOR]p[COLOR="Blue"]3C0D[/COLOR]d*dc*dsc*dp*ic*isc*ip*Tou might try:```
sudo rmmod -f rt3070sta
sudo modprobe rt2800usb
```Does your wireless come to life?```
iwconfig
```We can do some minor surgery if it works.

---

### Post by chili555 on 2010-03-09
> Chili, it looks like tansonnhut and I are going it two separate directions.Not really. You also have conflicting drivers. If you do:```
modinfo rt3070sta | grep 3C0D
```If your card is supported by the version of rt3070sta you successfully built, then we simply need to blacklist these:> rt3070sta 503348 0
[COLOR="Red"]rt2800usb[/COLOR] 37372 0
[COLOR="Red"]rt2x00usb[/COLOR] 11548 1 rt2800usb
[COLOR="Red"]rt2x00lib[/COLOR] 29756 2 rt2800usb,rt2x00usb
led_class 4096 1 rt2x00lib
input_polldev 3716 1 rt2x00lib
mac80211 181236 2 rt2x00usb,rt2x00lib
cfg80211 93052 2 rt2x00lib,mac80211
crc_ccitt 1852 1 rt2800usb Please post back and we'll see what we need to do.

---

### Post by rufuslucky on 2010-03-09
> **chili555 said:**
> Not really. You also have conflicting drivers. If you do:```
modinfo rt3070sta | grep 3C0D
```If your card is supported by the version of rt3070sta you successfully built, then we simply need to blacklist these:Please post back and we'll see what we need to do.


balance@balance-desktop:~$ modinfo rt3070sta | grep 3C0D 
balance@balance-desktop:~$ 
 
If you want me to blacklist the other drivers you specified I can do so, but I am going to need to know the proper command. blacklist rt2800usb spits back the response(blacklist: command not found) is it a sudo command?

---

### Post by rufuslucky on 2010-03-09
Tangentially, is there a way to turn off the smiles when posting a reply?

---

### Post by Tansonnhut on 2010-03-09
Ok here's what I got after the iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Looks like something happened however I still can't connect to any wireless networks.

To disable smilies there is a checkbox under the reply box.

---

### Post by chili555 on 2010-03-09
> Looks like something happened however I still can't connect to any wireless networks.Before you reboot or even breathe on the computer, please run:```
sudo iwlist wlan0 scan
```Do you see any networks? If not, let's again look at:```
dmesg | grep -e wlan -e rt2 -e rt3
```Does it try to connect when you click the Network Manager icon? Is your ethernet cable detached as you try to connect? Thanks.

---

### Post by Tansonnhut on 2010-03-09
Is says that there are no scan results.

dmesg | grep -e wlan -e rt2 -e rt3
[  163.451499] Registered led device: rt2800usb-phy0::radio
[  163.451537] Registered led device: rt2800usb-phy0::assoc
[  163.451581] Registered led device: rt2800usb-phy0::quality
[  163.458561] usbcore: registered new interface driver rt2800usb
[  163.502621] rt2800usb 2-3:1.0: firmware: requesting rt2870.bin
[  163.743073] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  541.210637] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by chili555 on 2010-03-09
> **rufuslucky said:**
> balance@balance-desktop:~$ modinfo rt3070sta | grep 3C0D 
balance@balance-desktop:~$ 
 
If you want me to blacklist the other drivers you specified I can do so, but I am going to need to know the proper command. blacklist rt2800usb spits back the response(blacklist: command not found) is it a sudo command?It is not supported by your driver. No need to proceed with blacklisting. I am trying to work out a solution for both of you.

---

### Post by Tansonnhut on 2010-03-10
Due to other complications I was forced to reinstall Ubuntu. As of right now I have redone all of the steps and all the results are almost exactly matching rufuslucky's.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsusb
Bus 002 Device 003: ID 07d1:3c0d D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04ca:002f Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6363 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c054 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dmesg | grep -e rt2 -e rt3
[   61.389656] Registered led device: rt2800usb-phy0::radio
[   61.389669] Registered led device: rt2800usb-phy0::assoc
[   61.389681] Registered led device: rt2800usb-phy0::quality
[   61.390293] usbcore: registered new interface driver rt2800usb
[   61.443822] rt2800usb 2-3:1.0: firmware: requesting rt2870.bin
[  300.364311] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[  300.372240] usbcore: registered new interface driver rt2870
[  516.351087] usbcore: deregistering interface driver rt2870

sudo iwlist wlan0 scan
wlan0     No scan results

If I missed anything when running the commands again let me know.

---

### Post by chili555 on 2010-03-10
Please remove the device and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add the following lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit. You may use nano, kate, vim or any text editor if you don't have gedit.

Reinsert the device and check:```
iwconfig
sudo iwlist wlan0 scan
```Any improvement?

We are going to get this device going if I have to buy one myself and wear out my keyboard!!!

---

### Post by Tansonnhut on 2010-03-10
Ok, here are the results:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist wlan0 scan
wlan0     No scan results

I hope it doesn't come to that. (Wearing out of keyboard)

---

### Post by chili555 on 2010-03-10
Please do:```
lsmod | grep -e rt3 -e rt3
```We are tring to find out if it's running on rt2870sta or rt3070sta or whatever. I am wondering if part of the issue is the default, probably wrong, settings in /etc/Wireless/RT3070STA/RT2870STA.dat. You might, as I am going to do, read that file and we'll see what we might amend. We can get some guidance from the README in the folder you used to compile the driver. Of course, this depends on which specific driver your card has grabbed.

---

### Post by rufuslucky on 2010-03-10
Sorry I have been gone, and I am going to be gone all day tomorrow too. I should be around on friday and the weekend if that will work for you. 

Here is what I got. 

balance@balance-desktop:~$ sudo gedit /etc/modprobe.d/blacklist.conf 
balance@balance-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

balance@balance-desktop:~$ sudo iwlist wlan0 scan 
wlan0     Interface doesn't support scanning. 

balance@balance-desktop:~$ lsmod | grep -e rt3 -e rt3 
rt3070sta             503348  0 
balance@balance-desktop:~$ 


At some point should I download RT3070USB (RT307x) and install it per these instructions:

 Re: Help with Dlink USB WiFi!
Drag and drop the file to any convenient place, your Documents folder, for example. Right-click it and select 'Extract Here.' A folder will be created called 2009_1110_RT3070_Linux_STA_v2.1.2.0.

Drop your Ubuntu install CD in the tray. Open a terminal and do:

Code:

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0
gedit os/linux/config.mk

Find the lines: HAS_WPA_SUPPLICANT=n and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

Change both lines to =y

Proofread, save and close gedit.

Code:

sudo su
make

You may get a few warnings, but no errors. If you get errors, stop and post them here.

Code:

make install
gedit /etc/modprobe.d/blacklist.conf

Add two lines:

Code:

blacklist rt2800usb
blacklist rt2x00usb

Proofread, save and close gedit.

Reboot.
Code:

lsmod | grep rt3

Did rt3070sta get loaded automagically?

Code:

iwconfig

Do you see a wireless interface, ra0 perhaps? Can you connect in Network Manager?
__________________


I apologize, I followed the thread with cessna but I didn't do any of the command line because it didn't have a conclusion.

---

### Post by Tansonnhut on 2010-03-10
I tried the command and nothing came back.

---

### Post by chili555 on 2010-03-11
> **Tansonnhut said:**
> I tried the command and nothing came back.Which, exactly?

---

### Post by rufuslucky on 2010-03-11
lsmod | grep -e rt3 -e rt3

provided me with no information either.

---

### Post by chili555 on 2010-03-11
> **rufuslucky said:**
> lsmod | grep -e rt3 -e rt3

provided me with no information either.Wonderful! That means rt3070sta has gone to sleep. Please do:```
sudo modprobe rt3070sta
iwconfig
sudo iwlist wlan0 scan
```What brand and model is this computer?

---

### Post by chili555 on 2010-03-11
I am working on several Realtek issues on this forum, all of which have the same symptoms. The driver grabs the device, an interface is created, wlanx, usually, and the device will not scan for networks and Network Manager will not allow it to connect. Everything looks perfect except it doesn't work.

I have been searching extensively and found this:  [http://ubuntuforums.org/showpost.php?p=8790489&postcount=97](http://ubuntuforums.org/showpost.php?p=8790489&postcount=97)

I was especially interested in this part:> For those that are using laptops with internal wifi cards and trying to use an external usb wifi dongle, on mine the internal must be on i.e. blue light for any external wifi dongle to work.

Once it connects I have to click on network manager and it will show both adapters are connected then click on disconnect for the internal card.And this:> I originally disabled the internal adapter in Windows. This is the major stumbling block that prevents having a wireless connection even though ndiswrapper is on, driver installed and device recognized.This also means that any blacklists for your internal card must be removed.

You two have been selected to be our test pilots! Is your computer a laptop? Please remove all your  blacklists for your internal card, if any, and push that wireless switch to activate your internal card. Now see if your external USB device comes to life. I have my fingers crossed.

---

### Post by rufuslucky on 2010-03-12
Hey Chilli, I think I am going to have to back out of this little experiment, because whatever we have done has ****** up our whole wireless network. My laptop that worked natively with the network, will no longer connect to the internet, and the issues began with I started trying to fix the 9.10 DWA-125 interface issue.

---

### Post by rufuslucky on 2010-03-12
OK, so I am a dueche, What I really needed to do was reset the the router. Any way, I a more than prepared to reinstall ubuntu on the second drive and get back to where we were. Do you want to proceed and see if we can fix this driver issue?

---

### Post by chili555 on 2010-03-12
No worries; all of us have been there before. 

I am not really sure it is necessary to reinstall, but if you feel that there are too many conflicting fixes, please proceed. Do you have a working ethernet connection so you can get the files you need?

I would *love* to get these pesky Realteks working. I am close to buying a DWA-125 myself, just so I can learn how to do it!!

---

### Post by rufuslucky on 2010-03-12
I was really hoping you would say that. I have the rt3070usb driver saved on a thumb drive. I have to go pick up my dear old mum from the airport, but then I will go through what we have done again, and send you a message when I am caught up.

---

### Post by chili555 on 2010-03-12
I am retiring for the evening, but will check in early tomorrow. Before you compile from source, let's first try the built-in rt3070sta, after we get rid of the usual conflicts, if any, rt2800usb, for example.

---

### Post by rufuslucky on 2010-03-13
Chili you asked me a couple of questions:
First the computer I am trying to do this on is a Balance digital technology desktop with an 845GV &#8211; M2 motherboard.  I've never been able to find out who manufactured it, though does seem that it was in a number of older cheaper pentium machines. That being said would you still like me to remove any of the blacklists that I have done? By which I mean

Please remove the device and do:
Code:
sudo gedit /etc/modprobe.d/blacklist.conf
Add the following lines:
Code:
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib


This is what we have done so far. 


balance@balance-desktop:~$ sudo modprobe rt3070sta 
[sudo] password for balance: 
balance@balance-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

balance@balance-desktop:~$ dmesg | grep -e rt2 -e rt3 
[    9.149656] Registered led device: rt2800usb-phy0::radio 
[    9.149687] Registered led device: rt2800usb-phy0::assoc 
[    9.149723] Registered led device: rt2800usb-phy0::quality 
[    9.150379] usbcore: registered new interface driver rt2800usb 
[   12.698906] rt2800usb 1-5:1.0: firmware: requesting rt2870.bin 
[   94.170471] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned. 
[   94.179908] usbcore: registered new interface driver rt2870 

balance@balance-desktop:~$ lsusb 
Bus 001 Device 002: ID 07d1:3c0d D-Link System 
Bus 001 Device 003: ID 054c:0243 Sony Corp. MicroVault Flash Drive 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

balance@balance-desktop:~$ lsmod | grep -e rt2 -e rt3 
rt3070sta             503348  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb 
rt2x00lib              29756  2 rt2800usb,rt2x00usb 
led_class               4096  1 rt2x00lib 
input_polldev           3716  1 rt2x00lib 
mac80211              181236  2 rt2x00usb,rt2x00lib 
cfg80211               93052  2 rt2x00lib,mac80211 
crc_ccitt               1852  1 rt2800usb 

balance@balance-desktop:~$ modinfo rt3070sta | grep 3C0D 

balance@balance-desktop:~$ sudo gedit /etc/modprobe.d/blacklist.conf 

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

balance@balance-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

balance@balance-desktop:~$ sudo iwlist wlan0 scan 
wlan0     No scan results 

balance@balance-desktop:~$ lsmod | grep -e rt3 -e rt3 
rt3070sta             503348  0 

balance@balance-desktop:~$ sudo modprobe rt3070sta 

balance@balance-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

balance@balance-desktop:~$ sudo iwlist wlan0 scan 
wlan0     No scan results 

balance@balance-desktop:~$


That should bring this box up to date. Let me know if you have seen anything that I have missed. I will be online at noon tomorrow. If that doesn't work for you, leave me a time that does. I will be around all day. 

Thanks for your help so far.

---

### Post by chili555 on 2010-03-13
> That being said would you still like me to remove any of the blacklists that I have done? Not in your case. Please leave them. Everything else, as far as I can see, looks fine, except, "No scan results."

What is your time zone? Noon where?

---

### Post by Tansonnhut on 2010-03-13
Sorry, I was gone for a while. Blasted school work. Anyways, when I tried the:
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

Those are the results I got. To answer your other question, this computer is an acer aspire x1301.

---

### Post by rufuslucky on 2010-03-14
Chili and I were able to get mine working, I believe he is going to post the postgame wrap up soon.

---

### Post by chili555 on 2010-03-14
Indeed we did. Remove the device. Blacklist conflicting drivers:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Remove ndiswrapper completely, if you installed it:```
sudo apt-get remove --purge ndiswrapper*
```Uninstall any drivers you compiled from source:```
cd Desktop/2009_RTL3070etc.
```Change to the directory of whatever file you compiled.```
sudo make uninstall
```Caution, this is for those devices with usb.id of [COLOR="Blue"]07d1:3c0d[/COLOR] only! Check with *lsusb*. Create two files:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta"
```Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rt3070sta
```You should then be able to see networks and connect in Network Manager.

If the module doesn't load automatically on boot, please do:```
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta
exit
```You may get an error in *dmesg* about loading RT2870STA.dat. If so, the fix is somewhat system dependent. Post:```
ls /etc/Wireless
```We'll find a quick fix.

For the benefit of the searchers, please post your report.

---

### Post by chili555 on 2010-03-14
My thanks to poohstickz, whose method we adapted.

[http://ubuntuforums.org/showpost.php?p=8927671&postcount=32](http://ubuntuforums.org/showpost.php?p=8927671&postcount=32)

---

### Post by Turbo_2 on 2010-03-17
Hey, I'm new to 9.1 Karmic, and have been following the posts for the last few days. Followed all the steps but I'm still getting error messages for unknown symbols in rt3070sta. Also, ls/etc/Wireless outputs RT2870STA RT3070STA...I'm not sure what this means. Thanks for any help.

---

### Post by chili555 on 2010-03-17
> **Turbo_2 said:**
> Hey, I'm new to 9.1 Karmic, and have been following the posts for the last few days. Followed all the steps but I'm still getting error messages for unknown symbols in rt3070sta. Also, ls/etc/Wireless outputs RT2870STA RT3070STA...I'm not sure what this means. Thanks for any help.Please start a new thread and post:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Tansonnhut on 2010-03-18
Thank you very much, it worked like a charm.

---

### Post by chili555 on 2010-03-18
Great work! I was worried about you when I didn't hear from you for several days. Glad you are all fixed.

---

### Post by ChairsForSquares on 2010-03-20
Hi I've followed all the steps but to no avail... my USB device id is 07d1:3c16

What do I need to do differently? Thanks for your help

---

### Post by chili555 on 2010-03-20
I wonder why you decided to follow all these steps; it clearly says:> Caution, this is for those devices with usb.id of 07d1:3c0d only! Check with lsusb. That's not the device you have. Please start a new thread and post:```
iwconfig
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by Turbo_2 on 2010-03-20
Sorry to butt in... but on a separate note: My network manager sees all the wireless networks in the area, but continues to ask for my WEP password. I've been watching what it does as it is trying to connect and it will gain the proper essid, and an access point, but never give me internet access. Then it disconnects, reconnects and asks for the WEP again. iwconfig and ifconfig show two different encryption key settings and ect/network/interfaces has no ra0 in it.  I could use some help writing ra0 into interfaces file because I'm not aware of proper formatting.

---

### Post by chili555 on 2010-03-20
It is not necessary to use */etc/network/interfaces* if you are using Network Manager. Without further configuration, you should be able to see your network, click connect and supply your WEP key, not password. Please see attached.

---

### Post by Turbo_2 on 2010-03-20
Yeah, I understand that. I misspoke when I said password. I needed to say key. Still not working. For whatever reason it doesn't want to go. I even logged on to the router with my other computer and copied the proper key, then pasted into authentication dialogue box.

---

### Post by chili555 on 2010-03-20
May we please see:```
modinfo rt3070sta | grep module
sudo cat /var/log/syslog | grep -i network
```The last command will produce lots of output if you have tried to connect many times, please don't flood the forum. Just try to see where it tries and fails and post ten or so lines before it does. If you are unsure, you might also use: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

How many characters are in your WEP key?

---

### Post by Turbo_2 on 2010-03-20
sudo modinfo rt3070sta | grep module
filename: /lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt3070/rt3070sta.ko
Mar 20 09:52:45 aren-desktop NetworkManager: <info>  (ra0): supplicant connection state:  disconnected -> scanning
Mar 20 11:15:48 aren-desktop NetworkManager: <info>  (ra0): device state change: 6 -> 9 (reason 7)
Mar 20 11:15:48 aren-desktop NetworkManager: <info>  Activation (ra0) failed for access point (3809Borthwick)
Mar 20 11:15:48 aren-desktop NetworkManager: <info>  Marking connection 'Auto 3809Borthwick' invalid.
Mar 20 11:15:48 aren-desktop NetworkManager: <info>  Activation (ra0) failed.

---

### Post by chili555 on 2010-03-20
> Activation (ra0) failed for access point (3809Borthwick)May I assume that is your network?> Marking connection 'Auto 3809Borthwick' invalid.If you right-click Network Manager and select Edit Connections, select Wireless and Wireless Security, are all the entries correct, especially the wireless key and type; probably 40/128-bit Hex? Is Connect Automatically checked?

How many characters are in your WEP key? 10 or 26? Or what?

---

### Post by Turbo_2 on 2010-03-20
Its a 10 place key...I'll edit this post with further detail

---

### Post by chili555 on 2010-03-20
> **Turbo_2 said:**
> Its a 10 place key...I'll edit this post with further detailThat sounds like a correct 40/128-bit Hex key.

---

### Post by artemgab on 2010-03-23
today I bought D-Link DWA-125 and was frustrated until I found this topic.
I've got a usb.id 07d1:3c0d device, the howto in page 4 helped me to bring wifi to life in seconds.
BIG THANKS!!!

---

### Post by Jyl-Byl Pes on 2010-04-04
Hello. Thanks for previous posts.
I am trying to connect my DWA-125 and it sees the network, keeps asking for password but could never connect.

odmin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: 00:19:CB:13:54:E9   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-79 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

odmin@ubuntu:~$ lsmod | grep -e rt2 -e rt3
rt3070sta             503348  1 
odmin@ubuntu:~$ dmesg | grep -e rt2 -e rt3
[   24.765351] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[   24.782711] usbcore: registered new interface driver rt2870
[   24.783898] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.


What am I doing wrong?

---

### Post by chili555 on 2010-04-04
Did you compile this from source? Did you amend RT2870STA.dat as instructed in the README?

---

### Post by Jyl-Byl Pes on 2010-04-04
> **chili555 said:**
> Did you compile this from source? Did you amend RT2870STA.dat as instructed in the README?

I tried. But I am not sure everything was done correctly (I am quite ignorant in Linux). 
Is there a way to check?

---

### Post by chili555 on 2010-04-04
Please tell us what kind of encryption you have, WEP, WPA, etc. and post your file here:```
cat /etc/Wireless/RT3070STA/RT2870STA.dat
```Obscure any passwords, of course.

---

### Post by Jyl-Byl Pes on 2010-04-04
> **chili555 said:**
> Please tell us what kind of encryption you have, WEP, WPA, etc. and post your file here:```
cat /etc/Wireless/RT3070STA/RT2870STA.dat
```Obscure any passwords, of course.

I use personal WPA2.

#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=0
SSID=Apple Network ac434b
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2PSK
EncrypType=WEP
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
FtSupport=0
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
PSP_XLINK_MODE=0
WscManufacturer=
WscModelName=
WscDeviceName=
WscModelNumber=
WscSerialNumber=
odmin@ubuntu:~$ ^C
odmin@ubuntu:~$

---

### Post by chili555 on 2010-04-04
> SSID=Apple Network ac434bAn SSID with spaces needs to be in quotes: SSID="Apple Network ac434b"> CountryCode=Should be specified. I don't know where you are, so I can't know what goes here.> AuthMode=WPA2PSK
EncrypType=[COLOR="Red"]WEP[/COLOR]
This can be NONE, WEP, TKIP or AES. If your network is WPA2-PSK as stated in AuthMode, then EncrypType must either be TKIP or AES. Please check in the administration pages of your router.> WPAPSK=This should be: WPAPSK=yoursecretkey.

Substitute your details, of course. Save your changes and try again.

---

### Post by Jyl-Byl Pes on 2010-04-04
> **chili555 said:**
> An SSID with spaces needs to be in quotes: SSID="Apple Network ac434b"Should be specified. I don't know where you are, so I can't know what goes here.This can be NONE, WEP, TKIP or AES. If your network is WPA2-PSK as stated in AuthMode, then EncrypType must either be TKIP or AES. Please check in the administration pages of your router.This should be: WPAPSK=yoursecretkey.

Substitute your details, of course. Save your changes and try again.

Thanks for quick reply, I will try to make changes. As for coutry code - I am in Russia.

---

### Post by chili555 on 2010-04-04
It looks like it's RU. Please check here:  [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

And here:```
man crda
```

---

### Post by Jyl-Byl Pes on 2010-04-04
With all changes the situation progressed to "connection established" in the right upper corner of the screen but web pages are not loading.

I have to give up at least for today - gotta put kids to bed.

Many thanks for your help.

---

### Post by Turbo_2 on 2010-04-08
I realize I've been away for weeks now. Still trying to resolve my linux issues on my extra computer. I was wrong to say that my protection encryption was WEP all along when in reality it is WPA. For whatever reason my linux box will associate and then disconnect only to ask for the password again. I checked the logs with my d-link router and it shows "received deauthentication" ...this doesn't follow for me. I wanted to get this working over weekend but can't find anybody else having the same WPA issues.  Let me know. Thanks.

---

### Post by bfh80 on 2010-04-15
Thanks to all for this thread helped me get up and running like a champ

---

### Post by souzacds on 2010-04-18
thanks everbody.
its worked for my hardware.

the ubuntu 10.04 will come with this hardware supported??

---

### Post by nbhagwat on 2010-04-20
Thanks for all the help. I did everything as advised. Now I see the networks, but can't connect. When I look for RT2870STA.dat, it claims that no such file exists. What did I do wrong?
Thanks.

---

### Post by chili555 on 2010-04-21
See what you have listed in /etc/Wireless. Post it here and we can maybe cheat a bit!

---

### Post by leolca on 2010-05-11
I recomend downloading the vendor driver and using it.

mkdir ~/dwa125
cd ~/dwa125
wget [ftp://dlink:dlink@www.dlinkla.com/pub/drivers/DWA-125/DRIVER_LINUX_DWA-125_STA_v2.1.2.0.tar.gz](ftp://dlink:dlink@www.dlinkla.com/pub/drivers/DWA-125/DRIVER_LINUX_DWA-125_STA_v2.1.2.0.tar.gz)
tar xzvf DRIVER_LINUX_DWA-125_STA_v2.1.2.0.tar.gz
cd 2009_1204_RT3070_Linux_STA_v2.1.2.0

>>> follow the instructions in the readme file <<<

less README.txt
sudo make
sudo make install
sudo bash -c 'echo blacklist rt2800usb >> /etc/modprobe.d/blacklist.conf'
sudo reboot

I hope it will work for you too. ;)

---

### Post by motin on 2010-06-15
Seems to be relevant, I posted how to install a working driver for the device with id 07d1:3c0d on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653)

Cheers

---

### Post by motin on 2010-06-15
Seems to be relevant, I posted how to install a working driver for the device with id 07d1:3c0d on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653)

There are many threads about this issue, but I couldnt find a complete solution anywhere. Hope this helps!

Cheers

---

### Post by kamalarora2kin on 2010-07-02
thanks chili for your efforts. i made  my dlink usb 125 working in just 5 minutes.

actually 5 days. well what happened actually i did not remove my device before blacklisting and making new files. and today i realised it and give it another try.

for all who have problem with dlink dwa 125, follow page no. 4 of this thread. even beginners can do this.

cheers

---

### Post by kamalarora2kin on 2010-07-03
I am back again with a little sad face. as i explained in the above post that device started working but when rebooted the computer it did not work. I disconnected and reconnected the device but no luck. now i dont know what to do. 

i followed your post #37 on page 4 of this thread. the last few codes which you asked in case module doesn't load automatically on boot; here are the results

```
administrator@ubuntu:~$ sudo su
[sudo] password for administrator: 
'root@ubuntu:/home/administrator# [COLOR="Navy"]echo rt3070sta >> /etc/modules[/COLOR]
root@ubuntu:/home/administrator# [COLOR="Navy"]modprobe rt3070sta[/COLOR]
FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta
root@ubuntu:/home/administrator# [COLOR="Navy"]exit[/COLOR]
exit
administrator@ubuntu:~$ [COLOR="Navy"]exit[/COLOR]
```

```
[COLOR="Navy"]ls /etc/wireless[/COLOR]

ls: cannot access /etc/wireless: No such file or directory

```

please help.

---

### Post by flash63 on 2010-07-03
Hello,
remove ndiswrapper completely und use rt2870sta. Tutorial here:

[http://ubuntuforums.org/showthread.php?p=9512177#post9512177](http://ubuntuforums.org/showthread.php?p=9512177#post9512177)

---

### Post by kamalarora2kin on 2010-07-03
thanks flash63

it solved my problem. 

good news chili555,

i got it working as i folowed the above link by flash63.

it can help anyone. i just changed my device id to "3c0d" .... that clicked.


thanks again

---

### Post by kamalarora2kin on 2010-07-04
i installed ubuntu 10.04 on a fresh partition
i ran these commands in shell which solved my WIRELESS adapter problem
```
sudo modprobe -rf ndiswrapper

echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07D1 3C0d" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe rt2870sta

dmesg | egrep 'rt28|usb|Phy'

sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9

sudo gedit /etc/udev/rules.d/10-wlan.rules
```

and added this long line in the editor and saved
> # UDEV-Rule for D-Link DWA-125 ID 07D1:3C0d
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c0d", RUN+="/sbin/modprobe rt2870sta"

rebooted pc

thats it. i did not even need to blacklist any old drivers.

good luck and thanks to all

**[COLOR="Red"]CREDIT goes to "flash63"[/COLOR]**

---

### Post by flash63 on 2010-07-04
> thats it. i did not even need to blacklist any old drivers.
Finally you must block rt2800usb at least!
```
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by Mr. Matt on 2010-07-11
Help, I have followed the steps on page 4 and in other threads but I cannot get this device working.  It is reporting networks available but I cannot connect to any of them.

Any ideas on where to start?  I have device 07d1:3c0d

This is the result of iwconfig except like I mentioned, it keeps trying to connect.

> ra0       Ralink STA  ESSID:"matt"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:39:49:53:C8   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level:-53 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When following the above commands and running:

> sudo modprobe rt2870sta

I get

> FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-23-generic/updates/staging/rt2870sta.ko): Device or resource busy

---

### Post by spacegravity4me on 2010-08-21
> **chili555 said:**
> Indeed we did. Remove the device. Blacklist conflicting drivers:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Remove ndiswrapper completely, if you installed it:```
sudo apt-get remove --purge ndiswrapper*
```Uninstall any drivers you compiled from source:```
cd Desktop/2009_RTL3070etc.
```Change to the directory of whatever file you compiled.```
sudo make uninstall
```Caution, this is for those devices with usb.id of [COLOR="Blue"]07d1:3c0d[/COLOR] only! Check with *lsusb*. Create two files:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta"
```Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rt3070sta
```You should then be able to see networks and connect in Network Manager.

If the module doesn't load automatically on boot, please do:```
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta
exit
```You may get an error in *dmesg* about loading RT2870STA.dat. If so, the fix is somewhat system dependent. Post:```
ls /etc/Wireless
```We'll find a quick fix.

For the benefit of the searchers, please post your report.

I got to the part where you plug it in and nothing happened. So I typed sudo modprobe rt3070sta and I got 
FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta

Really need some help. ty.

---

### Post by prasopsuk on 2010-08-25
to spacegravity4me
Thank alot. my dwa-125 working now after i had tring to get up for a few weeks.
Your post make my wireless wake up now.
thank you.

---

### Post by rastar101 on 2010-09-11
> you might have to do:```
sudo modprobe rt3070sta
```You should then be able to see networks and connect in Network Manager.

If the module doesn't load automatically on boot, please do:```
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta
exit
```You may get an error in *dmesg* about loading  RT2870STA.dat. If so, the fix is somewhat system dependent.  Post:```
ls /etc/Wireless
```We'll find a quick fix.

For the benefit of the searchers, please post your report.

hi,
i did what you said and when i run "sudo modprobe rt3070sta" ,i just faced by this error :

"
FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta
"
any idea what should i do to have my dwa-125 running?
tnx a lot!

---

### Post by ario on 2010-10-02
I did all steps about 40 times! I have DWA-125 and (You may have guessed it before) have the error message:
```
FATAL: Error inserting rt3070sta (/lib/modules/2.6
net/wireless/rt3070sta.ko): Unknown symbol in modu
dmesg)
sh: cannot create /sys/bus/usb/drivers/rt2870/new_
FATAL: Error running install command for rt3070sta

```
Any suggestions?

---

### Post by chili555 on 2010-10-02
> Any suggestions?Yes.

[http://ubuntuforums.org/showpost.php?p=9917564&postcount=90](http://ubuntuforums.org/showpost.php?p=9917564&postcount=90)

---

### Post by lzebra on 2010-10-05
Hello all

I did the instructions at [ ]("http://ubuntuforums.org/showpost.php?p=8966294&postcount=37")[D-Link setup post]("http://ubuntuforums.org/showpost.php?p=8966294&postcount=37") and have my adapter working. Thanks Chili555 - you're AWESOME! A couple of minor annoyances though:
- if I reboot it is lost. I have to unplug my usb wireless, type 
sudo modprobe rt2870sta
and then plug it back in. Any way to make it stick through the boot process? I am guessing that this has to do with Linux understanding which version (some variation of modprobe, module) but don't know how to make it work through boot process.

- every day or two the network gets real slow and I have to unplug and plug it back in.

I am grateful for any suggestions. Thank you.!

Laughing Zebra :confused:

---

### Post by ario on 2010-10-14
> **lzebra said:**
> Hello all

I did the instructions at [ ]("http://ubuntuforums.org/showpost.php?p=8966294&postcount=37")[D-Link setup post]("http://ubuntuforums.org/showpost.php?p=8966294&postcount=37") and have my adapter working. Thanks Chili555 - you're AWESOME! A couple of minor annoyances though:
- if I reboot it is lost. I have to unplug my usb wireless, type 
sudo modprobe rt2870sta
and then plug it back in. Any way to make it stick through the boot process? I am guessing that this has to do with Linux understanding which version (some variation of modprobe, module) but don't know how to make it work through boot process.

- every day or two the network gets real slow and I have to unplug and plug it back in.

I am grateful for any suggestions. Thank you.!

Laughing Zebra :confused:
Dear Laughing Zebra,
Did you make a wireless connection with DWA-125 using those instructions mentioned by Chili and in **Ad-Hoc WPA2 encryption mode**???
Thanks.

---

### Post by EmreSevinc on 2010-10-17
Hello,

I'm trying to connect to my wireless connection using my D-Link DWA-125   (N 150) Wireless USB Adapter. So far I was able to download, compile  and  install the driver provided by RALINK. The current situation is:

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```I assume that I'm using the correct driver, right?:

```
$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I'm trying to up the ra0 interface and then do a scan, but I cannot see any networks:

```
$ sudo ifconfig ra0 up

$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:11:2f:e9:81:08  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fee9:8108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5241984 (5.2 MB)  TX bytes:886749 (886.7 KB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ra0       Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet6 addr: fe80::f27d:68ff:fe14:19b0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:858032 (858.0 KB)

ra0:avahi Link encap:Ethernet  HWaddr f0:7d:68:14:19:b0  
          inet addr:169.254.6.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

``````

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results
```I also tried to "down" the eth0, again   no list scan result. I even tried from the Network Manager to connect to   a hidden network (even though it is not hidden, e.g. I can see my   network when I click on the Network Manager applet running on another   laptop, it lists my network among available networks and I can easily   connect) but without success. The point is this: I cannot see any  wireless networks when I click on the NM applet, I only see Wired  Network Auto eth0  and then Wireless networks disconnected and no list  of networks :sad:

Here's some probably relevant output from $ sudo cat /var/log/syslog | grep -i network:

```

Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'ssid' value 'emretanya'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'scan_ssid' value '1'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: added 'psk' value '<omitted>'
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:   nm_setting_802_1x_get_pkcs11_engine_path: assertion   `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]:   nm_setting_802_1x_get_pkcs11_module_path: assertion   `NM_IS_SETTING_802_1X (setting)' failed
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> Config: set interface ap_scan to 2
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  disconnected -> scanning
Oct 17 01:50:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  associating -> disconnected
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  disconnected -> scanning
Oct 17 01:51:14 yusuf-desktop NetworkManager[1694]: <info> (ra0): supplicant connection state:  scanning -> associating
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): association took too long.
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 5 -> 6 (reason 0)
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0/wireless): asking for new secrets
Oct 17 01:51:15 yusuf-desktop NetworkManager[1694]: <info> (ra0):   supplicant connection state:  associating -> disconnected
Oct 17 01:51:30 yusuf-desktop NetworkManager[1694]: <warn> (ra0): link timed out.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> (ra0): device state change: 6 -> 9 (reason 7)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn> Activation (ra0) failed for access point (emretanya)
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <info> Marking connection 'emretanya' invalid.
Oct 17 01:51:57 yusuf-desktop NetworkManager[1694]: <warn>   Activation (ra0) failed.
```Am I missing something, or doing   something wrong?

I'm using Ubuntu 10.10 with latest updates and:

```
$ uname -a
Linux yusuf-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

```Also the led light on my adapter is flashing constantly (I take   this as a sign that is somehow active because before I installed the   driver correctly it was not flashing).

I also copied RT2870STA.dat to /etc/Wireless/RT2870STA/ and did not change it, so it is as below:
```

#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
AutoRoaming=0
RoamThreshold=70
APSDCapable=0
APSDAC=0;0;0;0
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=0
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
CarrierDetect=0
AntDiversity=0
BeaconLostTime=4
PSP_XLINK_MODE=0
```

---

### Post by chili555 on 2010-10-17
First of all, Network Manager is designed to *not allow* a wireless connection if you have wired; you do.> eth0      Link encap:Ethernet  HWaddr 00:11:2f:e9:81:08  
          inet addr:[COLOR="Red"]192.168.1.12[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0Detach the ethernet cable, reboot and try the tests again.

Second, I think I'd try amending your RT2870STA.dat to specify your details here:> #The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
[COLOR="Red"]SSID=[/COLOR]11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
[COLOR="Red"]AuthMode=[/COLOR]OPEN
[COLOR="Red"]EncrypType=[/COLOR]NONE
[COLOR="Red"]WPAPSK=[/COLOR]
Finally, if both changes produce no better result, I'd abandon the compiled driver and do the procedure here, substituting your usb.id 07d1:3c16 and rt2870sta for rt3070sta in every instance.

[http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37](http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37)

Post back and let me know if you need further guidance.

---

### Post by ario on 2010-10-17
Here is a HOW-TO to make it work in Ad-Hoc mode, WEP connection and all using command line. Because this HOW-TO is specially for Sever Edition. But may also work on desktops:
[http://ubuntuforums.org/showthread.php?p=9987771#post9987771](http://ubuntuforums.org/showthread.php?p=9987771#post9987771)
Here is another I created for doing it in Desktop version:
[http://ubuntuforums.org/showpost.php?p=9919355&postcount=11](http://ubuntuforums.org/showpost.php?p=9919355&postcount=11)
By the way, I never succeeded creating a WPA encrypted connection in Ad-Hoc mode using this dangle. Just WEP mode worked for me.

---

### Post by jdieter on 2010-11-24
after HOURS found leolca post! got the driver and all working AOK!
yey!

> **leolca said:**
> I recomend downloading the vendor driver and using it.

mkdir ~/dwa125
cd ~/dwa125
wget [ftp://dlink:dlink@www.dlinkla.com/pub/drivers/DWA-125/DRIVER_LINUX_DWA-125_STA_v2.1.2.0.tar.gz](ftp://dlink:dlink@www.dlinkla.com/pub/drivers/DWA-125/DRIVER_LINUX_DWA-125_STA_v2.1.2.0.tar.gz)
tar xzvf DRIVER_LINUX_DWA-125_STA_v2.1.2.0.tar.gz
cd 2009_1204_RT3070_Linux_STA_v2.1.2.0

>>> follow the instructions in the readme file <<<

less README.txt
sudo make
sudo make install
sudo bash -c 'echo blacklist rt2800usb >> /etc/modprobe.d/blacklist.conf'
sudo reboot

I hope it will work for you too. ;)

---

### Post by fisbike on 2011-04-12
> **chili555 said:**
> Indeed we did. Remove the device. Blacklist conflicting drivers:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Remove ndiswrapper completely, if you installed it:```
sudo apt-get remove --purge ndiswrapper*
```Uninstall any drivers you compiled from source:```
cd Desktop/2009_RTL3070etc.
```Change to the directory of whatever file you compiled.```
sudo make uninstall
```Caution, this is for those devices with usb.id of [COLOR=Blue]07d1:3c0d[/COLOR] only! Check with *lsusb*. Create two files:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c0d", RUN+="/sbin/modprobe -qba rt3070sta"
```Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 3c0d" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rt3070sta
```You should then be able to see networks and connect in Network Manager.

If the module doesn't load automatically on boot, please do:```
sudo su
echo rt3070sta >> /etc/modules
modprobe rt3070sta
exit
```You may get an error in *dmesg* about loading RT2870STA.dat. If so, the fix is somewhat system dependent. Post:```
ls /etc/Wireless
```We'll find a quick fix.

For the benefit of the searchers, please post your report.

Thanks chili555, works like a charm.........
Was pulling hairs for the past week after bot this until came across this thread.

---

### Post by JoZ3 on 2011-04-30
Hi, I update to 11.04 from 10.10, the Wifi in the 11.04 is very very slow... any know what happend, i dont install nothing because the new SO have include the drivers (I think)

---

### Post by sacredrelic on 2011-06-20
Hi, i just started using this wireless USB Stick, since i had trouble with my ethernet..

i am using 11.04 Natty 32bit version of ubuntu.

after combining methods that mentioned in various threads.. (mostly done by chili) i got the fastest connection when using this Wireless Stick, is by blacklisting the rt2800usb, rt2800lib, rt2x00usb and rt2x00lib.

BUT, one unresolved issue.. 
my wireless get on and off repetitiously, i don't know where it go wrong..

---

### Post by chili555 on 2011-06-20
Let's see, in a terminal:```
lsusb | grep rt2
dmesg | grep -e rt2 -e wlan
```Thanks.

---

### Post by sacredrelic on 2011-06-20
poche@kanotsu:~$ lsusb | grep rt2
produces nothing

poche@kanotsu:~$ dmesg | grep -e rt2 -e wlan
[   17.851511] Registered led device: rt2800usb-phy0::radio
[   17.851535] Registered led device: rt2800usb-phy0::assoc
[   17.851556] Registered led device: rt2800usb-phy0::quality
[   17.860047] usbcore: registered new interface driver rt2800usb
[   17.891680] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   17.896925] usbcore: registered new interface driver rt2870
[   29.052250] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   60.336080] wlan0: authenticate with 00:18:39:39:23:c8 (try 1)
[   60.348099] wlan0: authenticated
[   60.540080] wlan0: associate with 00:18:39:39:23:c8 (try 1)
[   60.544222] wlan0: RX AssocResp from 00:18:39:39:23:c8 (capab=0x71 status=0 aid=3)
[   60.544227] wlan0: associated
[   60.868294] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


anw, i just remove all the blacklist from previous post
but when i remove the blacklist.. i cant go online even when my home wireless is detected and connected

edit
i try to add the blacklist again, and the result of demsg and lsusb are
poche@kanotsu:~$ lsusb | grep rt2
produces nothing

poche@kanotsu:~$ dmesg | grep -e rt2 -e wlan
[   16.751093] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   16.769154] usbcore: registered new interface driver rt2870
[   54.925007] <==== rt28xx_init, Status=0
[   91.245071] <==== rt28xx_init, Status=0
i can connect to network now, but the Wireless going on and off again.. 

and FYI, i'm using rt2870.bin not natty default, but the 8kB version that i got from launchpad at [https://bugs.launchpad.net/ubuntu/natty/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/natty/+source/linux-firmware/+bug/762987)

---

### Post by chili555 on 2011-06-20
Does it disconnect with the 4K firmware? Have you tried it the other way; that is, with rt2870sta blacklisted and rt2800usb un-blacklisted? Is your network WPA2 or the mixed WPA and WPA2 mode? Have you tried another channel on the router, 1, 2 or 11?

---

### Post by sacredrelic on 2011-06-20
> **chili555 said:**
> Does it disconnect with the 4K firmware? 
yes..
> **chili555 said:**
> Have you tried it the other way; that is, with rt2870sta blacklisted and rt2800usb un-blacklisted?
yes, but when i disabled the rt2870sta the wireless keep trying to connect to my network, take quite long time to finally connect, and my network is in WPA. trying in un secured mode.. report later..
> **chili555 said:**
> Have you tried another channel on the router, 1, 2 or 11?
no, i always set it in 11

edit
tried using the rt2800usb
the connection is stable, without connect-disconnecting problem, but the downside of this rt2800usb is the packet loss..
i tried to ping my gateway (my router), more than 30% packet loss.. and ping time above 1000ms.. that is crazy..

the rt2870sta is having small ping time, but it has connect-disconnecting problem.. haven't try the rt2870sta with unsecured mode.. more of that later..

2nd edit
i think the problem with rt2870sta lies in handling secured wireless..
for now i remove the security in the router and try to see the stability..
have been running for half an hour now, using rt2870sta without any connect-disconnect problem

3rd edit
have been running for all night now..
the rt2870sta is good, i mean getting this less than 5ms ping to my router..
the downside is, cant use the secured wireless, and for certain frequency.. the connection is paused for a second or two.. but were not disconnected.. just pause.. the downloading process is halted, ping requested is lost, torrent is stalled, but after a second, it all came back together.. otherwise.. it is all good.. thanks chili..

---

### Post by EduBaires on 2012-09-23
Thanks to post #37 from @chili555 I can now use d-link 125 on Ubuntu 10.04, dual with WXP, Pentium4.

I am a newbie who only knows how to pulse Ctrl-Alt-T for reaching the terminal, and how to copy and paste. I followed exactly the procedure in post #37 and IT WORKED! (The second time, the first I hadn't seen the magic words at the beginning: "Remove the device")

Thanks, Chili!

---

