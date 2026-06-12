---
title: "No wireless network connection now at all"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by slowman_x on 2010-03-05
Hi - I am new to Linux and Ubuntu so I have no idea how to fix or problem solve unfortunately :-(  I installed Ubuntu 9.10 from scratch recently on this laptop and all was good. I connected to my WIFI network no problem. It's WPA PSK encrypted, DHCP enabled. I just set it up in Network Manager and it was all fine. Then after a few days I installed a printer and some packages and updates via synaptics. The network connection started dropping after 20 mins or so. Only a reboot would restore it - auto connects at first, runs fine till it drops then never will reconnect. I posted on here, someone gave me some lines to put in a config file. I tried that. I didn't seem to help much, problem remained. Yesterday I checked for updates and there were a whole bunch so I just installed them all. Now I cannot connect at all. I have deleted and recreated the connection in Network Manager but it doesn't help. It tries to establish a connection but never achieves it. I am connecting to the internet now on the same laptop booted into Windows, so all the hardware is fine.

Can anyone who knows about ubuntu networking help? Do I need to do a complete reinstall? Seems a bit much, but it worked when I initially installed the OS. I want to like Ubuntu, but something as basic as connecting to the internet is pretty vital so reluctantly having to start using Windows again...

---

### Post by chili555 on 2010-03-05
Please open a terminal and do:```
lspci -nn
iwconfig
history | grep black
```Let's see what's (not) happening.

---

### Post by slowman_x on 2010-03-05
Hi - thanks for your reply - here are the results - I did this straight after boot before it tried to connect, then while it was trying, then after it gave up:


STRAIGHT AFTER BOOT (Has not tried to connect yet):

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Acer Incorporated [ALI] Device [1025:9602]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:""  
Mode:Managed  Frequency:2.412 GHz  
Access Point: Not-Associated   
Tx-Power=20 dBm   
Retry  long limit:7   RTS thr off   Fragment thr off
Power Management on     
Link Quality:0  Signal level:0  Noise level:0      
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0     
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

11  history | grep black



THEN I MANUALLY ASKED NETWORK MANAGER TO CONNECT VIA HIDDEN CONNECTION I SET UP:


lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bgn  ESSID:"DHOCM"       
Mode:Managed  Frequency:2.462 GHz  
Access Point: 00:11:50:4F:7C:A3   
Bit Rate=36 Mb/s   Tx-Power=20 dBm   
Retry  long limit:7   RTS thr off   Fragment thr off
Power Management on
Link Quality=18/70  Signal level=-92 dBm  
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

11  history | grep black
14  history | grep black



THEN AFTER IT GAVE UP TRYING TO CONNECT:

lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bgn  
Mode:Managed  Frequency:2.462 GHz  
Access Point: Not-Associated   
Tx-Power=20 dBm   
Retry  long limit:7   
RTS thr off   
Fragment thr off
Power Management on
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
   
11  history | grep black
14  history | grep black
16  history | grep black

---

### Post by chili555 on 2010-03-05
> wlan0 IEEE 802.11bgn ESSID:"DHOCM"
Mode:Managed Frequency:2.462 GHz
Access Point: 00:11:50:4F:7C:A3
Bit Rate=36 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thr off Fragment thr off
Power Management on
Link Quality=18/70 Signal level=-92 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0At this point, it was pretty close. I believe it couldn't hear a response from the router:> Link Quality=[COLOR="Red"]18/70[/COLOR]How far are you from the router? You might try increasing the txpower on your wireless interface:```
sudo iwconfig wlan0 txpower 21
```Increase the number to 22, 23, 24, etc. until it errors. See if it connects better then.

Also, I'd like to know what driver is in use:```
lsmod | grep ath
```Thanks.

---

### Post by Greenwidth on 2010-03-05
Installing the backport modules helps some people using the ath9k driver:
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

---

### Post by slowman_x on 2010-03-06
> **chili555 said:**
> At this point, it was pretty close. I believe it couldn't hear a response from the router:How far are you from the router?

You might try increasing the txpower on your wireless interface:```
sudo iwconfig wlan0 txpower 21
```Increase the number to 22, 23, 24, etc. until it errors. See if it connects better then.

Also, I'd like to know what driver is in use:```
lsmod | grep ath
```Thanks.


Hi, thanks for your thoughts and ideas - to answer:

1. About 3 feet from it - I can see it is scoring low there, but when using Windows the network connection strength is described as good to excellent - everything else is the same. Also of course it has connected in the past (prior to updates) and been perfectly happy. 

I will try the power thing - it makes sense if that is a Ubuntu driver issue setting, but not if it is a native hardware issue... 


2. 
ath9k  258744  0
mac80211  181140  1  ath9k
ath  8060  1 ath9k
led_class  4096  2  ath9k, acer_wmi
cfg80211  93052  3  ath9k, mac80211, ath



Power increase trying to set with 21:

Error for wireless request "Sex Tx Power" (8B26) :
SET failed on device wlan ; No such device.


...

---

### Post by slowman_x on 2010-03-06
> **chili555 said:**
> At this point, it was pretty close. I believe it couldn't hear a response from the router:How far are you from the router? You might try increasing the txpower on your wireless interface:```
sudo iwconfig wlan0 txpower 21
```Increase the number to 22, 23, 24, etc. until it errors. See if it connects better then.

Also, I'd like to know what driver is in use:```
lsmod | grep ath
```Thanks.


Also, when I tell NM to connect to my hidden network and it starts trying, if I look at the available networks it shows my network with 4 bars (full strength) in the list and I can see other people's networks that are broadcasting SSIDs at lower strengths.. But my little connection icon just keeps on going round and round...

If it had never worked at all that would be one thing, but the orginal install of 9.10 went without hitch and I used the network for days with no issue - it's only since updating stuff through synaptic that problems have started to occur. Looking at this forum I see there are many people reporting similar problems...

---

### Post by chili555 on 2010-03-06
I noticed this:> Error for wireless request "Sex Tx Power" (8B26) :
SET failed on device wlan ; No such device.The device is wlan[COLOR="Red"]0[/COLOR]. Please try again.```
sudo iwconfog wlan0 txpower 21
```I also noticed:```
Power Management on
```Power management, in order to conserve battery power on a laptop, is used to manipulate power management scheme parameters and mode. Let's see if that is interfering with our connection ability. Please do:```
sudo iwconfig wlan0 power off
iwconfig
```Is our connection strength and ability to connect improved?

---

### Post by slowman_x on 2010-03-06
Hi - sorry that's just me typoing when posting here - I entered it as you said originally - have just tried again, typing exactly what you've said I get this:

Error for wireless request "Set Tx Power" (8B26) :
  SET failed on device wlan0 ; Invalid argument.

---

### Post by slowman_x on 2010-03-06
RE the power management off and retry I get this:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DHOCM"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:4F:7C:A3   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


So signal is improved - but NM icon still spinning... I can't reach my router...



The thing I did previously on someone else's advice in this forum was the following - he said this:

----------------

Re: Ubuntu 9.10 dropping network connection randomly
I upgraded network-manager from the PPA to see if it would help to stop the disconnects and it's working good 3 days so far without a single one. So it may help.
I got it by adding the karmic PPA from here:
Karmic network-manager PPA

These are bleeding edge with the very latest bug fixes so do so at your own risk!!!
If you want to give it a try you can do it like this:
Open a terminal
Applications > Accessories > Terminal
and follow this:
(when asked for your password in the terminal it wont display what you type, you just type it in and hit Enter)
Code:

gksu gedit /etc/apt/sources.list

Add these 2 lines to the bottom
Quote:
deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
Save and close it then use this to add the key (shouldn't really need sudo in the rest but I included it just in case you take more than 15 minutes to complete it all).
Code:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8

Then update apt
Code:

sudo apt-get update

Install the new network manager
Here you have some choices

If you just want to just update network manager use this first one (this is what I used)
Code:

sudo apt-get upgrade network-manager network-manager-gnome

---------------

I did that. It seemed to improve the amount of time the connection would stay up, although the length of time was variable anyway, so that's not conclusive... It certainly didn't seem to do any harm though... 

It's only since I installed the recent recommended system updates having run Update Manager and saying yes to everything that I have lost the ability to connect completely..

---

### Post by karthick ayyapillai on 2010-03-08
hi
if you are using ubuntu 9.10 version and ath9 dirvers for wifi then you can try to install wicd instead of gnome network manager and check if the wifi is working .
note : plz remove the gnome network manager after installing wicd so that it doesnt conflict .
try this sudo apt-get update
type the sudo password and then type sudo apt-get install wicd you ll be successful in installing it after that
type sudo reboot 
 go to the system and check there will be an option for the wicd or click on network manager you can see a different icon . If you have any doubts need any help with installing wicd then refer to this 
[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

---

### Post by slowman_x on 2010-03-08
Just for the record, having no success with trying to fix this, I have resorted to deleting the entire Linux partition and reinstalling Ubuntu 9.10 from my original ISO. Needless to say I entered my network info once and connected first time without issue (just like I did first time round). So it seems clear that something in the package updates caused a serious problem. 

So normally I would update any OS as a first step but of course if I do that it is likely I will lose my network connection permanently... so what to do?

---

