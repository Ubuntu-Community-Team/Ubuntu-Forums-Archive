---
title: "ASUS USB-N13 Wireless Receiver Issues"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by ipolanikonane on 2011-10-12
I'm having issues getting my ASUS USB-N13 wireless receiver to work.  I searched the Networking & Wireless Forum for answers.  I found a post ( [http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2](http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2)) and tried following it, but had no success.  Can anyone help me with this frustrating problem?  Would appreciate assistance.  FYI, I am running Ubuntu 10.04 (Lucid Lynx).  I am reasonably computer savvy, with some programming experience, but am very new to Linux.  Also, I have the following USB-N13 drivers downloaded to my desktop:  

2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13

RT3070_LinuxSTA_V2.3.0.1_20100208

DPO_RT3070_LinuxSTA_V2.3.0.2_20100422

2010_0709_RT2870_Linux_STA_v2.4.0.1

Appreciate any help.

---

### Post by chili555 on 2011-10-12
Maybe there is an easier way. Please run:```
lsusb
```If your device ID is 0b05:1784 then we can shortcut the process. Remove the device and in a terminal, do:```

sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"
```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```

install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rt2870sta
```You should be all set. Post back if you need additional guidance.

---

### Post by ipolanikonane on 2011-10-13
Thanks...will give it a try.  One question, though.  Regarding the text/code you provide for inserting, should I assume to copy everything you provided exactly, including the quotation marks?  Just want to be sure before I proceed.  Thanks.

---

### Post by chili555 on 2011-10-13
> should I assume to copy everything you provided exactly, including the quotation marks?Yes, exactly. Be sure to scroll all the way over to the right to get all the text to the end. As always, proofread carefully before you save.

Post back if you have more questions.

---

### Post by ipolanikonane on 2011-10-13
Tried all you said.  USB receiver finally showed a green light.  Upper right hand of desktop shows radiating wireless icon, as well as the network name of my Windows 7 network.  Below the network name is the "disconnect" option.  However, a pop up black message indicates otherwise, stating no connection.  And, when I open up Firefox to browse, it shows offline status.  I tried restarting modem, router, and computer, in order, but no luck with getting it to work.  So, the good news is that the operating system is recognizing the ASUS USB-N13 receiver.  The bad news is that the indications are conflicting (i.e., shows connection, but really isn't).  FYI, I even double-checked to see if my network key/password was correct, and it was.  Quite stumped now.  Do you have any clue why this is happening?  Appreciate your help, again.

---

### Post by chili555 on 2011-10-13
Did you click on the network name and were you challenged for encryption details; WPA2 etc.? Ubuntu is not going to connect to any old possibly insecure network without direction from you. Please let us see:```
iwconfig
ifconfig wlan0
```

---

### Post by ipolanikonane on 2011-10-14
When I click on the network name, it appears a connection is either made or attempted, but I am not queried, as you asked.
 
OK, I entered the code and here are the results:
 
stan@Peter2-Linux-Ubuntu:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 RTxx70 Wireless ESSID:"" Nickname:"RT3070STA"
Mode:Auto Frequency=2.412 GHz Access Point: Not-Associated 
Bit Rate:1 Mb/s 
RTS thr:off Fragment thr:off
Link Quality=88/100 Signal level:-55 dBm Noise level:-87 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
stan@Peter2-Linux-Ubuntu:~$ ifconfig wlan0
wlan0 Link encap:Ethernet HWaddr 20:cf:30:a2:03:30 
inet6 addr: fe80::22cf:30ff:fea2:330/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1741 errors:0 dropped:0 overruns:0 frame:0
TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:492831 (492.8 KB) TX bytes:18968 (18.9 KB)
 
stan@Peter2-Linux-Ubuntu:~$ 
&#12288;
&#12288;

---

### Post by chili555 on 2011-10-14
Well, you are certainly not connected. Let's see:```
sudo iwlist wlan0 scan
dmesg | grep rt2
```Thanks.

---

### Post by ipolanikonane on 2011-10-14
OK, per the code, here is what I got:
 
stan@Peter2-Linux-Ubuntu:~$ sudo iwlist wlan0 scan
[sudo] password for stan: 
wlan0 Scan completed :
Cell 01 - Address: 00:23:69:65:2B:77
Protocol:802.11b/g/n
ESSID:"Peter Family"
Mode:Managed
Channel:1
Quality:89/100 Signal level:-55 dBm Noise level:-63 dBm
Encryption key:on
Bit Rates:54 Mb/s
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
 
stan@Peter2-Linux-Ubuntu:~$ dmesg | grep rt2
[ 11.684530] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 11.689091] usbcore: registered new interface driver rt2870
stan@Peter2-Linux-Ubuntu:~$

---

### Post by chili555 on 2011-10-14
You will probably have better luck without a space in the name of the router; I'd suggest PeterFamily. Moreover, many drivers have difficulty with mixed WPA and WPA2 mode. I suggest changing to WPA2 only.

Clearly, if you click on the name, before connection, you ought to be challenged for the key.

Your kernel messages look perfect; no problems there.

Please see examples attached.

---

### Post by ipolanikonane on 2011-10-15
I tried deleting the network name under "Wireless" tab in my "Network Connections" dialogue box, restarted, then tried again to reconnect.  This time I was queried/challenged for the key, which I entered.  However, the wireless icon will "radiate" for little bit, followed by another challenge for the key.  It repeats this loop, but never completely connects.  Again, I made absolutely certain my key password was correct..exact same one I'm using for my other computers on the network, which all connect fine.
 
Regarding "WPA" security, the Ubuntu version I am using only has options for "WPA & WPA2 Personal" and "WPA & WPA2 Enterprise" as options.  If I understand you correctly, ae you suggesting setting my router for plain "WPA" instead?  If I do, how safe is it? I thought I should be using the latest encryption to ensure the safety of my data?
 
So, if I change the network name to something without spaces, will this likely resolve this issue?

---

### Post by ipolanikonane on 2011-10-15
I finally got it to work!  I started with changing the network name to something without a space in it.  Then, I tried removing wireless security.  Initially, it didn't work, but a quick restart on my modem, followed by the router, then computer did the trick.  Voila, it worked.  I then tried secure with just WPA, and it worked (same restarting sequence of all hardware as before).  Finally, I tried stepping up to WPA2, but it would not work for this level of security.  
 
So, I have it working, but with only WPA security.  I suppose some security is better than none.  Do you know if there is a solution to get the WPA2 security to work?

---

### Post by ipolanikonane on 2011-10-15
Do you think the following code found at this link, post #47, will solve my issue with being able to step up a level and use WPA2, instead of WPA:
 
[http://ubuntuforums.org/showthread.php?t=607410&page=5](http://ubuntuforums.org/showthread.php?t=607410&page=5)
 
Would appreciate your guidance.

---

### Post by chili555 on 2011-10-16
I do not think so. That's for manual configuration, not Network Manager. I have never seen this behavior previously; that is, connection to WPA but not WPA2. I am Googling and suggest you do also.

---

### Post by ipolanikonane on 2011-10-16
Yes, I have been searching, but no luck so far.  Let me know if you find anything.
 
Do you think WPA is sufficient for a home network?
 
I've heard that WPA security can be "cracked" by someone with the right know how and resources.  Obviously, I'd prefer using the best security measure available, if possible.
 
Would appreciate your thoughts on this.
 
Thanks.

---

### Post by praseodym on 2011-10-16
Please show:

```
cat /etc/Wireless/RT2870STA/RT2870STA.dat
```

---

### Post by chili555 on 2011-10-16
Either WPA or WPA2 can be cracked, albeit with considerable effort and time. However, if your neighborhood is like mine, there are plenty of unencrypted and WEP networks available. As well, if a hacker is going to the time and effort to crack WPA, why not take the time to get something valuable like the bank!

You might consider compiling a better version from Ralink. I'm not sure the file you started with in post #1 is correct.

Let me know what you'd like to do.

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

---

### Post by chili555 on 2011-10-16
> **praseodym said:**
> Please show:

```
cat /etc/Wireless/RT2870STA/RT2870STA.dat
```Is this file installed for the in-tree module?

---

### Post by ipolanikonane on 2011-10-17
I absolutely agree with you.  Indeed, if someone is going to make the effort to hack into a system and has the ability, they would be better off trying to get to something truly valuable, like a large bank or similar institution.  Nevertheless, I'd still like to use the very best encryption, if possible.  Of course, why not.

As for compiling the correct driver, I thought the instructions I followed earlier bypassed any need for a driver.  I am not sure I ever installed a driver.  Forgive my ignorance if I'm not following you correctly.

Below is the output from the code you suggested using:

stan@Peter2-Linux-Ubuntu:~$ cat /etc/Wireless/RT2870STA/RT2870STA.dat
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
stan@Peter2-Linux-Ubuntu:~$

---

### Post by chili555 on 2011-10-20
> WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=You might change AuthMode to WPA2PSK; EncrypType to AES; and WPAPSK= to your key. Reboot and see if it makes any improvement.

---

### Post by ipolanikonane on 2011-10-21
Thanks...however, how do I access the code?  Forgive my ignorance, but I'm not familiar with Linux commands.  Appreciate your help.

---

### Post by praseodym on 2011-10-21
Open the file with

```
gksudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```

---

### Post by ipolanikonane on 2011-10-21
Tried it.  At first, it didn't work.  Then I changed my router setting from AES or TKIP to just AES, since that is what was set in the file I accessed.  It worked then.

Now I'm running WPA2 Personal with AES, which is better than just plain WPA.

What is the difference between TKIP and AES?  Is it best to use both, if possible?  What about my key now existing in the file I accessed...is it secure?

---

### Post by praseodym on 2011-10-21
Change the rights to 600 (read only for root):

```
sudo chmod 600 /etc/Wireless/RT2870STA/RT2870STA.dat
```

---

