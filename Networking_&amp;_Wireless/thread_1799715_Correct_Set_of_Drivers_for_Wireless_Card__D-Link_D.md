---
title: "Correct Set of Drivers for Wireless Card : D-Link DWA525"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by blitzit on 2011-07-08
Hi,

I have been using a D-Link DWA525 since the past 2 months.

I initially installed the drivers with the ndiswrapper and it seemed to work well, although the machine would hang abruptly without any apparent reason.

On a colleagues recommendation, I switched to using Ralink Drivers from their site, as was also recommended in this thread : [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

However, after a couple of weeks of smooth running, one fine day, my card stopped detecting any and all networks available (I am using the card on a desktop in my college lab, there are 5 networks available throughout the day).

So, after some searching on the internet, I landed with yet another helpful suggestion / solution, [http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/) which solved my problem like a click.

But then again (yes the story is long) yesterday, my card stopped connecting to any of the networks although it detects all of them. It was unable to authenticate my connection.

After having tried all that I could, I finally decided to reinstall ubuntu (because I thought there might be a conflict between the upgraded kernel and the driver). Alas! The driver still couldn't connect to the networks :(  1 out of 50 times, it gets connected. But an attempt to reconnect and it's gone.

Now again, I tried to search for other drivers and found this well documented table : [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink), which says I must download "RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT2860/RT2760/RT2890/RT2790)" from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2), the fact is there are 2 different drivers:
1) RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)
2) RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592)

Now my question is, is there a standard tried and tested method for this? Also, I am still confused on the correct set of drivers. Any suggestions?

---

### Post by chili555 on 2011-07-08
Let's see exactly where we are. Let's take a look at some diagnostics before we decide how to proceed. Please run and post:```
lsmod | grep -e rt2 -e rt3
lspci -nn | grep 0280
```Thanks.

---

### Post by blitzit on 2011-07-08
Hi,

Thanks for the reply.

This is the output for the commands that you suggested.

```
vijay@307-21:~$ lsmod | grep -e rt2 -e rt3
rt3562sta             915830  0 
vijay@307-21:~$ lspci -nn | grep 0280
07:01.0 Network controller [0280]: RaLink Device [1814:3060]

```

Even while I was typing this, my wi-fi connected to a network and showed signal strength at 95%, on it's own and then got disconnected within 2 minutes.

Anyways, thanks :)

---

### Post by chili555 on 2011-07-08
Your original post asks which driver to download and yet you seem to have it all installed! When you compiled it, did you make this change as mentioned in the README?> ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.What version do you have?```
modinfo rt3562sta
```

---

### Post by blitzit on 2011-07-08
:) Yes, I made that change.

Actually, my post was regarding the confusion in the drivers. I have tried and installed all available drivers that I knew of. It is just that, these details surprise me:
[LIST=1]
[*]rt2860sta as well rt3562sta, both seem to run well. Which one of them is the best suited?
[*]Why did it so happen that all of sudden, in the middle of a Desktop session, my wifi got disconnected from the network and then couldn't connect back again?
[*]Is it a driver problem, or is it a WPA problem? The fact is, I have used wifi with the same WPA settings and back then it worked smooth.
[/LIST]

And I am presently not in my lab at college, I shall get back to you as soon as possible. Sorry for the delay and thanks for the response.

---

### Post by blitzit on 2011-07-09
This is the output for modinfo
```
vijay@307-21:~$ modinfo rt3562sta
filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/rt3562sta.ko
version:        2.4.1.1
srcversion:     0543E8912DF687C279649F2
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-33-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

```

I suspect it could even be just a frequently occuring wifi drop, however, the laptops I use on the same desk, right beside my desktop, seem to connect fine.

---

### Post by chili555 on 2011-07-09
I am not sure I know the precise answer to your questions. It is clear that either driver works but the determination as to which is best can only be determined in your kernel, your hardware, your router, etc. by you. I have seen wacky things that, by all that I understand, should *never* work. I don't fight momentum; if it works, I say great.> Is it a driver problem, or is it a WPA problem? Or a Network Manager problem. There are so many things that enter into the mix that it's hard, at least for me, to pin down the one factor that makes or breaks the connection. Of course, you could take each factor out of the mix and see if the trouble goes away.

You could try to connect with WEP instead of WPA. You could connect with no encryption. You could stop Network Manager and configure manually. You could change quite a few settings in the router, such as WPA vs. WPA2, channel and, in some routers, signal strength.

Does /var/log/syslog have any clues?

---

### Post by blitzit on 2011-07-22
Hi,

It's been a long time since the last activity on this post, and I had given up all hopes on getting the issue solved. Infact, I had even contacted the network support team here at IIT-Delhi (my college) and they weren't able to help me much.

Then today, I thought, I must give it another shot and I started searching again when I landed on this page : [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink) again. [I had landed on it earlier as well, but had skipped a few, (apparently helpful) lines]. The column for DWA-525 asked me to follow the README_STA for a successful installation and I in my merriment had overlooked the same.

So I set out reading the file and went through each and every line. This file exists in the folder which is extracted from the tar file. Some of the lines had to be understood and, although it wasn't mentioned, one or two things had to be substituted in the commands they recommended.

But, all in all, my wi-fi seems to be running fine for the moment :) and I am happy.

I am marking this thread as [SOLVED] and here is a tip to the people installing drivers for their D-Link DWA-525. There's more to be done than what the help offered here [[http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/]](http://steveswinsburg.wordpress.com/2011/03/12/how-to-install-a-d-link-dwa-525-wireless-network-card-in-ubuntu-10-04/]) says. (No offence to the write-up, it's a wonderful start point, but it lacks a few important things.)

If anyone needs help on the matter, please post a message here, I am thinking a tutorial for the same could be helpful.

---

### Post by Wtwine on 2011-08-16
Hi Vijay

I would appreciate a tutorial.

I successfully followed the instructions provided by [http://steveswinsburg.wordpress.com](http://steveswinsburg.wordpress.com) to get my card working the first time.  However, it stopped working again, probably due to kernel upgrade.  Now I can't get it to work again by repeating these steps that worked before.

I tried reading the README_STA_pci file as you suggest, but most of it goes right over my head (e.g. the makefile instructions).

Thanks
Wayne

---

### Post by chili555 on 2011-08-16
These instructions are written for Ubuntu 11.04. It is required to install build-essential and linux-headers generic. 

```
sudo apt-get install build-essential linux-headers-generic

```
Drag and drop the file to your desktop. Right-click and select Extract Here, if not already extracted. Open the file os > linux > config.mk with a text editor and change:

```
# Support Wpa_Supplicant 
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger 
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```
To:

```
# Support Wpa_Supplicant 
HAS_WPA_SUPPLICANT=y 

# Support Native WpaSupplicant for Network Maganger 
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

Proofread carefully, save and close the text editor. Now, in a terminal, do:```
cd Desktop/2011
```Press Tab and the remainder of the folder name will fill in automatically. Press Enter. Now do:

```
sudo su
make
make install
modprobe rt3562sta
exit
```

Your device should now be working. Whenever a new kernel version or linux-image is installed by Update Manager *you must recompile*:

```
sudo su
make clean
make
make install
modprobe rt3562sta
exit
```Post back if you need additional guidance.

---

### Post by Wtwine on 2011-08-18
Thanks Chilli555

I was sure that the "make clean" in your instructions was the step I had been missing when having to recompile after kernel upgrade, but alas, it still does not work.  The card "sees" the available networks but can't connect.  I know it's not Network Manager that's the problem because I am connected to wireless now using an Edimax usb wireless card.

Here is what I have done:
1. Followed all your instructions (with the "make clean" step)
2. Blacklisted  rt2800pci in /etc/modprobe.d/blacklist.conf (after first installation)
3. Rebooted


Here is some output that might be useful in finding the problem:
```

~$ lsmod | grep -e rt2 -e rt3
rt3562sta            1047386  1 

:~$ modinfo rt3562sta
filename:       /lib/modules/2.6.35-30-generic/kernel/drivers/net/wireless/rt3562sta.ko
version:        2.4.1.1
srcversion:     4D386FD1EDC7B95F07E2F57
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35-30-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
```Thanks

---

### Post by chili555 on 2011-08-18
Please detach the USB wireless device, reboot, try to connect and then do:```
sudo cat /var/log/syslog | grep -e rt3 -e etwork | tail -n25
```Post the result here so we can see what's going on under the hood.

---

### Post by Wtwine on 2011-08-18
OK

Here you go:

```
~$ sudo cat /var/log/syslog | grep -e rt3 -e etwork | tail -n25
[sudo] password for *****: 
Aug 18 16:28:00 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 18 16:28:00 TWINE-DESKTOP kernel: [  150.613160] ===>Set_NetworkType_Proc::(INFRA)
Aug 18 16:28:00 TWINE-DESKTOP kernel: [  150.613162] Set_NetworkType_Proc::(NetworkType=1)
Aug 18 16:28:10 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 18 16:28:10 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 18 16:28:12 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 18 16:28:12 TWINE-DESKTOP kernel: [  162.514391] ===>Set_NetworkType_Proc::(INFRA)
Aug 18 16:28:12 TWINE-DESKTOP kernel: [  162.514393] Set_NetworkType_Proc::(NetworkType=1)
Aug 18 16:28:17 TWINE-DESKTOP NetworkManager[1035]: <warn> (ra0): link timed out.
Aug 18 16:28:22 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 18 16:28:22 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 18 16:28:24 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug 18 16:28:24 TWINE-DESKTOP kernel: [  174.362903] ===>Set_NetworkType_Proc::(INFRA)
Aug 18 16:28:24 TWINE-DESKTOP kernel: [  174.362909] Set_NetworkType_Proc::(NetworkType=1)
Aug 18 16:28:34 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  associating -> disconnected
Aug 18 16:28:34 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug 18 16:28:35 TWINE-DESKTOP NetworkManager[1035]: <warn> Activation (ra0/wireless): association took too long, failing activation.
Aug 18 16:28:35 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): device state change: 5 -> 9 (reason 11)
Aug 18 16:28:35 TWINE-DESKTOP NetworkManager[1035]: <warn> Activation (ra0) failed for access point (witshs)
Aug 18 16:28:35 TWINE-DESKTOP NetworkManager[1035]: <info> Marking connection 'Auto witshs' invalid.
Aug 18 16:28:35 TWINE-DESKTOP NetworkManager[1035]: <warn> Activation (ra0) failed.
Aug 18 16:28:35 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): device state change: 9 -> 3 (reason 0)
Aug 18 16:28:35 TWINE-DESKTOP NetworkManager[1035]: <info> (ra0): deactivating device (reason: 0).
Aug 18 16:28:35 TWINE-DESKTOP kernel: [  185.295968] ===>Set_NetworkType_Proc::(INFRA)
Aug 18 16:28:35 TWINE-DESKTOP kernel: [  185.295973] Set_NetworkType_Proc::(NetworkType=1)

```

---

### Post by chili555 on 2011-08-18
May I have a look at *dmesg*?```
dmesg > wtwine.txt
zip wtwine.zip wtwine.txt
```In your user directory, you will find a file called wtwine.zip. Please attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by Wtwine on 2011-08-18
File attached

Thanks

---

### Post by chili555 on 2011-08-18
That's a very busy dmesg you have there! The driver is struggling and, as you know, not having much success. I have in my hand my personal copy of the C/C++ Programmers Bible. Place you right hand on it and raise your left hand and swear that you have the same device:> $ lspci -nn | grep 0280
07:01.0 Network controller [0280]: [COLOR="Red"]RaLink Device [1814:3060][/COLOR]Also, that you carefully and correctly did this step:> Open the file os > linux > config.mk with a text editor and change:
```
# Support Wpa_Supplicant 
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger 
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```
To:
```
# Support Wpa_Supplicant 
HAS_WPA_SUPPLICANT=y 

# Support Native WpaSupplicant for Network Maganger 
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

Proofread carefully, save and close the text editor. Now, in a terminal, do:Do you promise?

---

### Post by Wtwine on 2011-08-19
I promise! May Bill Gates call me his buddy if I'm lying! 

Just to be sure,  I did it all over again.  This time I copied the lines that need to be changed in the config file and pasted them in a search to make sure I found the right lines to change them.

The only other thing I can think of is this: In one of my many previous searches to sort this, I came across a suggestion that the file RT2860STA.dat should be copied from the driver folder and pasted in the folder under etc/wireless, which I did.  Could that have had any influence?

---

### Post by chili555 on 2011-08-19
Let's have a look:```
ls /etc/Wireless/RT2860STA
cat /etc/Wireless/RT2860STA/RT2860STA.dat
```Usually, if Network Manager is allowed to manage the connection, the .dat file will be skipped. I do, however, see a lot of activity in the logs that suggest it's being read and relied upon.> I came across a suggestion that the file RT2860STA.dat should be copied from the driver folder and pasted in the folder under etc/wireless, which I did.Generally, 'make install' does all that for us automatically.

---

### Post by Wtwine on 2011-08-19
```
:~$ ls /etc/Wireless/RT2860STA
RT2860STA.dat
P:~$ cat /etc/Wireless/RT2860STA/RT2860STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=portthru
NetworkType=Infra
WirelessMode=9
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
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
HT_DisallowTKIP=1
HT_STBC=0
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
RadioOn=1

```

---

### Post by Wtwine on 2011-08-26
Hi Chilli555

Does the output you requested (see previous post) yield any insights?

W

---

### Post by praseodym on 2011-08-26
Are your country code settings ok?

```
sudo apt-get install --reinstall iw
sudo iw reg set SA
```
If "SA" is for South Africa

---

### Post by Wtwine on 2011-08-26
Thanks Praseodym

I tried what you suggested (using ZA South Africa code), but country code stays empty after reboot and I still can't connect.

Ho hummmmmm

---

### Post by praseodym on 2011-08-26
Edit the file according to this examples (even if the page ist flagged "outdated"):

[https://wiki.archlinux.org/index.php/Rt2870#Initial_Configuration](https://wiki.archlinux.org/index.php/Rt2870#Initial_Configuration)

You need to change the following lines to your country's settings (here for Germany):

```

CountryRegion=1
CountryRegionABand=1
CountryCode=DE
WirelessMode=5

```

---

### Post by Wtwine on 2011-08-29
Thanks

I updated the file to 

```
CountryRegion=1
CountryRegionABand=1
CountryCode=ZA
ChannelGeography=1
SSID=portthru
NetworkType=Infra
WirelessMode=9


```

The settings stick but I still can't connect (I did reboot) :(

---

### Post by rg50 on 2011-11-03
WiFi Problems  I am running 2 computers. Both with ASUS P5G41T-M LX motherboards. One is used for daily operation, the other is used to test upgrades. When it becomes functional, the roles exchange. Both multi boot using several hard disks, current Ubuntu version, grandfather version and Windows.   Getting the WiFi to run stably has been a problem. I have used 4 PCI cards : D-Link DWA-510, DWL-520, DWA-525 and Netgear WG311v3. All work with Meerkat and Natty on both these machines. The WPA-510, the oldest and slowest, is the only one to work with Ocelot.  The trouble starts with the Ocelot install CD (3.0.0-10). If update is run immediately, all work. If “Try Ubuntu” is run then “Update” is started from there, the last 3 all fail. Sometimes the wireless card is detected by Network Manager and the icon, top right, is a small screen and keyboard, with the message “...SSID name.. Connection established”, otherwise it is a blank segment of a circle.  . The Keyring Login request is never made. In previous versions of Ubuntu this is requested before the connection is made. If connection is forced the icon is animated (segment with moving arcs). The security key is requested repeatedly at about 1 min. interval, but no connection is made. Updating to 3.0.0-11 & 12 has made no change.  When the DWA-520 card connects the Keyring Login request occurs after a long delay after the connection is made even though “Keyring Access” appears at the top left end of the menu bar. The “Keyring Login request” appears immediately if “evolution” is opened.   After Ocelot is loaded and the system is rebooted, using ndiswrapper with WG311v3 connection is made and works normally. If the machine is shut down and rebooted the network manager does not see the card and an abbreviated menu shows when clicking on the icon (blank segment). Using ndiswrapper to remove and reinstall the windows driver, network manager again sees the card and wifi works normally again. i.e The settings are lost on shutdown.  All suggestions from the community pages (Wicd, B43 drivers etc.) have been tried with no significant change. lspci correctly lists the card being tested with the expected driver.  I have been unable to edit the headers to change os-> linux &#8594; config.mk settings as discussed in D-Link's README-STA for DWA-525 and UBUNTU Forums ….... Networking & Wireless.

---

