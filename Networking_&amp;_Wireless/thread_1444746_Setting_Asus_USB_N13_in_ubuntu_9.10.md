---
title: "Setting Asus USB N13 in ubuntu 9.10"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by 828688 Ben on 2010-04-01
Hi everyone,
I am not only VERY new to Ubuntu, but i am new to linux as well, so any answers to my question need to be as simple as possible, so i can understand it. Anyways, i need help setting up an Asus USB N-13 wireless adapter (when i plug it NOTHING happens (the light on the device doesn't even blink)). I was trying to use this [(click me)]("http://ubuntuforums.org/showthread.php?t=1419504&highlight=usb-n13"), but i got confused mid way through. Any help would be great.
P.S. I have Ubuntu 10.04 LTS

Thanks in advanced,
Ben

---

### Post by chili555 on 2010-04-01
Please open Applications > Accessories > Terminal and post:```
lsusb
```Thanks.

---

### Post by 828688 Ben on 2010-04-01
benjamin@Ben-laptop:~$ lsusb
Bus 001 Device 012: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
benjamin@Ben-laptop:~$

---

### Post by chili555 on 2010-04-01
> I am not only VERY new to Ubuntu, but i am new to linux as well, so any answers to my question need to be as simple as possible, so i can understand it.Here we go! Remove the device from the USB slot. Open a terminal and do these commands; it is perfectly alright to copy and paste and proofread carefully. Spacing, case and spelling must be exact!```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```The text editor gedit will pop open as a new file. Type in one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
```Proofread carefully, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Type in one long line:```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread carefully, save and close gedit. Detach the ethernet cable. Insert the USB device. Click the Network Manager icon and connect.


My thanks to poohstickz.

---

### Post by 828688 Ben on 2010-04-01
Unfortunately, it did not work. 
Here are some things that might help you, help me:

when i used windows xp, the usb wireless adapter would flash (it has a  green light on it) when i plugged it in and when i used it, i have not  seen it flash once now that have ubuntu (even after i tried your  instructions).

after i unplugged my ethernet cable, the icon on the top of my screen  that represents my internet connection show the wireless bars with an  exclamation beside it.

initially, when i was setting up this device, when i was using windows  xp, i used the cd that it came with to install the drivers. after  installing the drivers from the cd, the usb device worked perfectly.  however, when i updated the drivers to the most recent version (this is  when i was using windows xp), the device failed to work, similarly to  now (windows did not recognize that any device was plugged in and the  green light did not flash). Maybe the newer drivers don't work? 

I have also attached the linux drivers (these are drivers made for linux  (they came from the included cd that i got with my wireless usb  adapter)). Inside the zip file there is also (confusing and advanced)  instructions on how to install these drivers in linux.

I hope this helps,
Ben

---

### Post by chili555 on 2010-04-02
I am very familiar with the Realtek-provided one size fits all Suse-Debian-Gentoo-whatever drivers. They work well less often than our built-ins.

I am sorry that you did not tell me that you already tried and failed with ndiswrapper. Of course, we will need to undo, even temporarily, that installation.

Please insert the device and do:```
sudo rmmod -f ndiswrapper
sudo modprobe rt3070sta
```Now click the Network Manager icon ("the icon on the top of my screen that represents my internet connection") and see if you see networks. Can you connect?

If it works, we will erase your faulty ndiswrapper installation.

---

### Post by 828688 Ben on 2010-04-02
It didn't work.

here's what happened---

benjamin@Ben-laptop:~$ sudo rmmod -f ndiswrapper
benjamin@Ben-laptop:~$ sudo modprobe rt3070sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta
benjamin@Ben-laptop:~$ 

Sorry about not telling you about ndiswrapper, I completely forgot. 
Do you think that i should completely reinstall ubuntu 10.04  LTS on my computer and try this all again?

Thanks Again,
Ben

---

### Post by chili555 on 2010-04-02
> Do you think that i should completely reinstall ubuntu 10.04 LTS on my computer and try this all again?That's your choice. If you don't have much on it, it might be easier and faster than repairing what you now have. Please let me know what you decide.

---

### Post by 828688 Ben on 2010-04-02
Due to the fact that i just installed Ubuntu on my computer, i have decided to reinstall ubuntu 10.04 LTS on my system.  I will retry your suggestions at the begining of this thread when the installation is complete.

P.S. don't worry this time i will not install ndiswrapper on my system

Thanks, 
Ben

---

### Post by chili555 on 2010-04-02
Ben-

We will be waiting! I look forward to your report of your success.

---

### Post by 828688 Ben on 2010-04-02
Okay, I reinstalled ubuntu, I Updated ubuntu, i did not install ndiswrapper and i tried your suggested terminal commands that involved me using gedit (that is where i stopped) and, unfortunately, similarly to before, nothing happened. What should i try next?

Thanks,
Ben

---

### Post by chili555 on 2010-04-02
Did you reboot?

---

### Post by 828688 Ben on 2010-04-02
Just tried rebooting and nothing happened. Is there some kind of terminal command that I can do that will help troubleshoot this problem?

---

### Post by chili555 on 2010-04-02
Sure. Let's try:```
sudo modprobe rt3070sta
iwconfig
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by 828688 Ben on 2010-04-02
Heres what I got--

ben@Ben-Laptop:~$ sudo modprobe rt3070sta
[sudo] password for ben: 
FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta
ben@Ben-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ben@Ben-Laptop:~$ lsmod | grep -e rt2 -e rt3
ben@Ben-Laptop:~$ dmesg | grep -e rt2 -e rt3
ben@Ben-Laptop:~$ 


Thanks,
Ben

---

### Post by chili555 on 2010-04-02
I must apologize; I thought rt3070sta would be a part of Lucid. I am running a machine with it on it now, but I am unable to find it in any repositories or backports. We will have to build it.

I tried the file you attached and it errors out, even with a patch.

I have attached the file that works for me. Download it to Downloads, where downloads go by default. Next, do:```
cd Downloads
tar -xvzf 2009
```Press the Tab key, the remainder will fill in for you.```
cd 2009 
```Tab.```
sudo su
make
make install
modprobe rt3070sta
exit
```Any errors? Now, please reboot with the device inserted and the ethernet cable removed and tell me if you have wireless and can connect.

---

### Post by 828688 Ben on 2010-04-02
Okay, I think i am doing something wrong, here's what i'm doing-
1st- i click the link to download the file
2nd- a smaller window in firefox pops up
3rd- i can either 
                            Open with (Archive Manager (default))
                 OR
                            Save File
4th- i choose Save file and click OK
5th- the file then downloads to my Downloads folder (the _exact_ name of this downloaded file is ---2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2)
6th- (i did not not extracted the file) i then open up terminal heres what it says---

ben@Ben-Laptop:~$ cd Downloads
ben@Ben-Laptop:~/Downloads$ tar -xvzf 2009
tar: 2009: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
ben@Ben-Laptop:~/Downloads$ 

What did i do wrong? am i missing a step? Do i have to rename the downloaded file?

P.S.--- here is the location of the downloaded file--- /home/ben/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2   *keep in mind i am new to linux and ubuntu, so i am probably missing a step.

Thanks For The Help,
Ben

---

### Post by chili555 on 2010-04-02
> 
Code:

cd Downloads
tar -xvzf 2009

[COLOR="Red"]Press the Tab key, the remainder will fill in for you[/COLOR].Please try again. I am right here for you, man!

---

### Post by 828688 Ben on 2010-04-02
I did this another way before you were able to respond, sorry. 

here's how i did it-
1st-- I extracted the download myself 
2nd-- I renamed the extracted folder "2009"
3rd-- i then did "cd Downloads" in terminal
4th-- then "cd 2009"
I then did everything else as directed, seemingly successfuly.
I then restarted, removed the Ethernet cord, plugged and the USB drive.  still, nothing.

Here are the new results of the troubleshooting terminal commands you  suggested earlier---


ben@Ben-Laptop:~$ sudo modprobe rt3070sta
ben@Ben-Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ben@Ben-Laptop:~$ lsmod | grep -e rt2 -e rt3
rt3070sta             510191  0 
ben@Ben-Laptop:~$ dmesg | grep -e rt2 -e rt3
[   23.793863] usbcore: registered new interface driver rt2870
ben@Ben-Laptop:~$ 


What do i do next to get this wireless usb adapter working?

Once Again, Thanks,
Ben

---

### Post by chili555 on 2010-04-02
> ra0 RT2870 Wireless ESSID:""
Mode:Auto Frequency=2.412 GHz
Link Quality=10/100 Signal level:0 dBm Noise level:-143 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0I think it is working! Please try to click the Network Manager icon and see if you see networks. If not, please do:```
sudo ifconfig ra0 up
sudo iwconfig ra0 mode managed
sudo iwlist ra0 scan
```Have you rebooted? Would you please? Thanks.

---

### Post by 828688 Ben on 2010-04-02
I feel so close!
I rebooted the system with the ethernet cord unplugged and the usb wireless adapter plugged in. I then checked the network manager and nothing. I then tried your terminal commands and here is what I got---

ben@Ben-Laptop:~$ sudo ifconfig ra0 up
[sudo] password for ben: 
SIOCSIFFLAGS: Operation not permitted
ben@Ben-Laptop:~$ sudo iwconfig ra0 mode managed
ben@Ben-Laptop:~$ sudo iwlist ra0 scan
ra0       No scan results

ben@Ben-Laptop:~$ 


What is "SIOCSIFFLAGS: Operation not permitted" and how do I turn ra0 on? Is this why its all not working? What should I do next?

Thanks,
Ben

---

### Post by chili555 on 2010-04-02
Something wacky is going on. Let's take a look at:```
dmesg | grep -i rt2
dmesg | grep -i rt3
```Thanks.

---

### Post by 828688 Ben on 2010-04-02
Heres what i get---

ben@Ben-Laptop:~$ dmesg | grep -i rt2
[   24.924889] usbcore: registered new interface driver rt2870
[  160.180862] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  160.180868] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  160.199004] !!! rt28xx Initialized fail !!!
[  349.076290] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  349.076296] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  349.104404] !!! rt28xx Initialized fail !!!
ben@Ben-Laptop:~$ dmesg | grep -i rt3
ben@Ben-Laptop:~$

Thanks,
Ben

---

### Post by chili555 on 2010-04-02
> Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!Ah, ha! Without doing a lot of long-distance diagnosis, let's try to fix it, no matter what the issue is.```
sudo mkdir /etc/Wireless/RT2870STA
```If it says the directory already exists, that's fine.```
sudo cp ~/Downloads/2009/RT2870STA.dat /etc/Wireless/RT2870STA/
sudo chmod 755 /etc/Wireless/RT2870STA/*
```Now remove the device, wait a few moments for the stars to align and reinsert it. Any improvement?

---

### Post by 828688 Ben on 2010-04-02
YESSSSSSSSSSSS!!!
ALMOST THERE!!
I did --
sudo mkdir /etc/Wireless/RT2870STA
sudo cp ~/Downloads/2009/RT2870STA.dat /etc/Wireless/RT2870STA/
sudo chmod 755 /etc/Wireless/RT2870STA/*

Then I did-- "sudo ifconfig ra0 up" and the green light starts flashing (for the first time since i was using windows xp)!!
This is what i did next---

ben@Ben-Laptop:~$ sudo iwconfig ra0 mode managed
ben@Ben-Laptop:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:14:d1:C9:26:9C
                    Protocol:802.11b/g/n
                    ESSID:"P.F.C."
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-29 dBm  Noise level:-95 dBm
                    Encryption key: on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:B2:39:C3:6A
                    Protocol:802.11b/g
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Channel:3
                    Quality:0/100  Signal level:-95 dBm  Noise level:-95 dBm
                    Encryption key: on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

ben@Ben-Laptop:~$ 

The network P.F.C is mine!!!
my next question is, how do i connect to it? 
P.S.- the network manager still doesn't recognize the device, so how do i fix that OR how can i set up a connection while using terminal. 

P.S. (again)-- my security mode for my network is WPA2-PSK and my WPA Cipher is AES

THANKS YOU SO MUCH,
Ben

---

### Post by chili555 on 2010-04-02
We are going to restart Network Manager.```
sudo /etc/init.d/NetworkManager restart
```I have seen systems where it is named network-manager (no caps, but with a hyphen) so be prepared to try that. Now does NM see your network and connect?

---

### Post by 828688 Ben on 2010-04-02
Here's what i got--
ben@Ben-Laptop:~$ sudo /etc/init.d/NetworkManager restart
[sudo] password for ben: 
sudo: /etc/init.d/NetworkManager: command not found
ben@Ben-Laptop:~$  sudo /etc/init.d/network-manager restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart network-manager
network-manager start/running, process 1862
ben@Ben-Laptop:~$ 

From what i can see (I may be wrong), this command did not restart network manager.
If i'm wrong and network manager did restart, It still does not detect my connection.

P.S.--I am not sure if network manager is installed on my computer. What i thought was network manager has a windows titled "Network Connections". If they are the same thing, then forget i said anything, but if they are not, where is the network manager program located, and if i don't have it how can i download it?

P.S. (Again)-- not sure why the smiley faces are there.

Thanks,
Ben

---

### Post by chili555 on 2010-04-02
Please reboot. We may have to try Wicd.

---

### Post by 828688 Ben on 2010-04-02
Okay, I have rebooted my computer. I am ready to use Wicd.

P.S.-- just so you know (not sure if this is important), i must use the terminal command "sudo ifconfig ra0 up" every time i reboot in order for the usb wireless adapter to turn on.

Thanks,
Ben

---

### Post by chili555 on 2010-04-02
Please do:```
sudo apt-get remove --purge network-manager*
```Then go to System > Administration > Software Sources and enable, if not already done, the Universe repository. Then do:```
sudo apt-get update
sudo apt-get install wicd
```You should then see the application in Applications > Internet > Wicd. Under Preferences, add your wireless interface, ra0. Click OK and then Refresh. Do you see your network and can you connect?

---

### Post by 828688 Ben on 2010-04-02
It's Sooooo close!
Okay, i did everything you said and Wicd is up and running. However when i try to connect to my wireless network it says "bad password", but i am 100% sure that i am inputing the correct password. I even changed (under the properties button in the Wicd window) the WPA 1/2 from passphrase to preshared key, which according to my trendnet router wireless security settings, is what i am should be using. 

What am i doing wrong? do you have any suggestions?

P.S.-- I was able to connect to this router under windows xp using this very same computer and usb wireless adapter (i wanted you know that this router i functioning correctly.)

**Quick thought- in Wpa settings for my router, i have a setting called "key renewal interval" (it is set as "3600" seconds), if i lower or raise this will my bad password error be fixed.

Thanks for your help,
Ben

---

### Post by chili555 on 2010-04-02
Your scan looks exactly like mine: WPA2-PSK. I drop the password in as per attached and it rushes to connection! Is that where you are inputting yours?> if i lower or raise this will my bad password error be fixed.
I don't know, I've never seen this.

---

### Post by 828688 Ben on 2010-04-02
Do you have any suggestions as to how i can fix my problem (previously stated)?

Thanks,
Ben

---

### Post by 828688 Ben on 2010-04-02
I think i might of found a solution!
How would i downgrade my current version of wicd to version 1.6.1?
can you explain (in simple steps) the terminal commands that i would need to do to downgrade the current version of my wicd program to version 1.6.1.

Thanks,
Ben

---

### Post by 828688 Ben on 2010-04-03
Okay, Here's what I'm gonna do:

I am doing a clean install of ubuntu 9.10. I am doing this becouse my ubuntu 10.04 has been very buggy, and many of my applications are quitting and crashing randomly.

After that i will go through all the previously listed steps, as before.

If Wicd does not work for me still, i will try a program called Wifi Radar (i did try Wifi Radar in ubuntu 10.04, but like many of my other applications, it crashes).
 
I will then post my results, and let you know how it all tuned out.

P.S.-- Hopefully my next post will be sent through WIFI!

Thanks For All The Great Help,
Ben

---

### Post by chili555 on 2010-04-03
So, what do you have installed now? Network Manager, Wicd or what?

In my experience, both Wicd and Network manager connect easily, if the details are correct. When I converted to WPA2 from WEP, both connected quickly.

---

### Post by chili555 on 2010-04-03
May we see:```
sudo cat /etc/Wireless/RT2870STA/RT2870STA.dat
```Thanks.

---

### Post by 828688 Ben on 2010-04-03
Here's what i got:

ben@Bens-Laptop:~$ sudo cat /etc/Wireless/RT2870STA/RT2870STA.dat
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
ChannelGeography=1
SSID=11n-AP
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
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_BADecline=0
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
FtSupport=1
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=ben@Bens-Laptop:~$

Thanks,
Ben

---

### Post by chili555 on 2010-04-03
Please remove the device and do:```
sudo rmmod -f rt3070sta
sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```Make the changes I have highlighted in red:```
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=[COLOR="Red"]US[/COLOR]
ChannelGeography=1
SSID=[COLOR="Red"]P.F.C.[/COLOR]
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
AuthMode=[COLOR="Red"]WPA2PSK[/COLOR]
EncrypType=[COLOR="Red"]AES[/COLOR]
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
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_BADecline=0
HT_AutoBA=1
HT_BADecline=0
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
FtSupport=1
Wapiifname=ra0
WapiPsk=
WapiPskType=
WapiUserCertPath=
WapiAsCertPath=
```Now, re-insert the device and see if Wicd is more cooperative.

---

### Post by 828688 Ben on 2010-04-03
Almost there.....
Here's what Happens when i connect to Wicd:

I FINALLY (and for the first time) get past:
"Validating Authentcaiton"    AND
"P.F.C. validating authentication" 

Then I see this:
"P.F.C. obtaining IP address" AND
"obtaining IP address"
    Those two dialogues appear back and forth a couple times, then, A small window pops up saying: "Connection Failed: Unable to Get IP Address"

What Should I do?

Thanks,
Ben

---

### Post by chili555 on 2010-04-03
Take a look at:```
sudo tail -n25 /var/log/syslog
```See if you can see why it fails and post any details for our examination.

You might also try inputting your password here:> ---snip---
mmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=[COLOR="Red"]yourkeyhere[/COLOR]
DefaultKeyID=1
Key1Type=0
---snip---
Re-insert the device and see what if anything improves. I would have thought Wicd would do that for us.

---

### Post by 828688 Ben on 2010-04-03
[SIZE=6]Success!![/SIZE]

Finally, I am able to connect to my router!

I do have question. When i connect to my router wirelessly, i seem to be getting my Internet in short bursts. For example, when i went to speedtest.net (to test my connection speed), it stopped the test download half way, pause for a little bit, and then continued. It is doing that on all websites i visit. Is there a setting or terminal command i can change/do to fix this?

P.S.-- when i was using this computer, wireless usb adapter, and router under windows xp, i did not have this problem. (i say this so you know its not my router and Internet that's causing the problem.)

Thanks For All The Help, And Successfully Getting Me Connected To My Router Wirelessly,
Ben

---

### Post by chili555 on 2010-04-03
Thank you for your kind comments. I wonder if it helps to disable IPv6 in Firefox:

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by 828688 Ben on 2010-04-04
Okay, Wicd is just not working the way it should.

Can you please show me how to connect to my router, through _Terminal Commands_.
I would really like to try to connect this way.

Thanks,
Ben

---

### Post by chili555 on 2010-04-04
I have never tried with terminal commands and WPA. I rather suspect that, after you remove Wicd altogether, you can, since you have all the details hard-coded into RT2870STA.dat, that you might be able to do, simply:```
sudo dhclient wlan0
```I suggest you try this and check the syslog, as above, to see why it didn't connect, if it didn't.

I have set up */etc/network/interfaces* like this:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid mylilrouter
wpa-psk ineedacoldbeer

#auto eth0
iface eth0 inet dhcpObviously, substitute your details here. As well, all you haX4rz, you can be assured these are not my actual details.

My network connects on boot and stays connected, with no Wicd or Network Manager.> it stopped the test download half way, pause for a little bit, and then continued. It is doing that on all websites i visit.You might see if it more stable at lower speeds:```
sudo iwconfig ra0 rate 54M
```Try even lower speeds as well. I don't know if you have a N speed router, but N is a bit spotty in Linux drivers these days. It will improve.

---

### Post by 828688 Ben on 2010-04-04
As you know, I'm pretty new to Ubuntu, and Linux in general.

You said:

I have set up */etc/network/interfaces* like this:     Quote:
                                                 auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid mylilrouter
wpa-psk ineedacoldbeer

#auto eth0
iface eth0 inet dhcp                      


Can you give me an example of what mine should look like if:
My wireless interface is:  ra0
My wpa-ssid is:  P.F.C.
My wpa-psk is : 12345678 (I made the password up)

ALSO: this file is marked as "read only", how do i edit it?


Again, Thanks For The Help,
Ben

---

### Post by chili555 on 2010-04-04
```
sudo gedit /etc/network/interfaces
```Edit the file that comes up in the text editor gedit to read as follows:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
wpa-ssid P.F.C.
wpa-psk 12345678

#auto eth0
iface eth0 inet dhcp


```Proofread carefully, save and close gedit. Reboot and see if your wireless is connected:```
ping -c3 www.google.com
```If you get ping returns, you are all set.

---

### Post by 828688 Ben on 2010-04-04
Before i try to troubleshoot the problem that i have now, i have one quick question:

What usb wireless adapter is not only good, but it supports ubuntu right out the box and works without any problems(or as close to that as possible). If there is more than one, can you list them in order of Best To Worst.

Thanks Again,
Ben

---

### Post by chili555 on 2010-04-04
I suggest you check here as well as search this forum.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by 828688 Ben on 2010-04-04
[SIZE=6]IT WORKS, With NO problems, and NO disconnecting!

Thank You _Chilli555_, YOU ROCK!!! ,
[SIZE=5]Ben[/SIZE]

[/SIZE]

---

### Post by chili555 on 2010-04-04
Your post above makes it all worthwhile. Thanks, Ben, for you very kind comments.

---

### Post by jacklinux on 2010-06-24
Your fix worked perfectly, i tried many methods from installing different versions of ubuntu to reinstalling no end of drivers. 
Thankyou VERY much.

---

### Post by roydrager on 2010-07-17
Just an update to the much appreciated solution from Chili555.  I  managed to get his solution working in 10.04 lucid lynx 32 bit with the  latest usb-n13 driver from the Asus site, version 2.3.0.2 dated April 22  2010 (zip file attached to this post, and here is also the Asus  official link):

[http://support.asus.com/download/download.aspx?modelname=USB-N13&SLanguage=en-us](http://support.asus.com/download/download.aspx?modelname=USB-N13&SLanguage=en-us)

(Of course Chili555's solution also works with the driver he attached in  post #17 of the main thread:

[http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2](http://ubuntuforums.org/showthread.php?t=1419504&highlight=USB-N13&page=2)

)

The steps I followed were:

tar -xvzf DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz
cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
sudo make 
make install

At this point, there was an error "error 1" with the new driver's  makefile where it's looking for the file  /DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat .  However the  actual file is named RT2870STA.dat .  Here is the terminal output of the  error:

```
make -C  /home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux -f  Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory  `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp  /home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat  /etc/Wireless/RT3070STA/.
**cp: cannot stat  `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT3070STA.dat':  No such file or directory**
make[1]: *** [install] Error 1
make[1]: Leaving directory  `/home/d/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
make: *** [install] Error 2
```The solution is to edit the  os/linux/Makefile.6 file:

sudo gedit os/linux/Makefile.6

There is a line near the top:

```
DAT_FILE_NAME = RT$(CHIPSET)STA.dat
```Change this line to:

```
DAT_FILE_NAME = RT2870STA.dat
```Save, exit, then: 

sudo make install

The makefile should install without errors now.  Then create the two  files in /etc/modprobe.d/ and /etc/udev/rules.d/ exactly as Chili555  wrote them:

[http://ubuntuforums.org/showpost.php?p=9395844&postcount=2](http://ubuntuforums.org/showpost.php?p=9395844&postcount=2)

Then physically insert the usb-n13 device in the usb port.  At this  point ubuntu recognized the hardware, I didn't need to restart.  This  new driver seems to give me better speed than the older version.

---

### Post by blackhawkover on 2010-07-26
to roydragger:

I appreciate that someone else is working on this adapter at the same time as me. 

I attempted your fix in 10.04, and on the sudo make command, got this:


```
make -C tools
make[1]: Entering directory `/home/thinkpad/build/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/thinkpad/build/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
make: *** [build_tools] Error 2
```



What does this mean?

---

### Post by blackhawkover on 2010-07-27
> **blackhawkover said:**
> to roydragger:

I appreciate that someone else is working on this adapter at the same time as me. 

I attempted your fix in 10.04, and on the sudo make command, got this:


```
make -C tools
make[1]: Entering directory `/home/thinkpad/build/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/thinkpad/build/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
make: *** [build_tools] Error 2
```



What does this mean?


It seems wierd to reply to your own post, but I found out it was because I didn't have the gcc installed, as I am running Netbook Edition which doesn't have gcc installed, therefore, could not compile anything. Hope this helps anyone else involved in this trek getting the Asus usb n13 to work.

---

### Post by Swan48 on 2010-07-30
Will these instructions work in 8.04 LTS? I started to follow roydrager's instructions but when it talked about editing the  os/linux/Makefile.6 file, I couldn't even find that directory.

Here's my background about how I've come to this point. When WinXP went down on my old Toshiba A15-157, I first tried putting Ubuntu 10.04 on it but it wouldn't boot up properly. So I put 8.04 on it because I already had the disk. When I tried to use the internal wireless, I can see the wireless networks but it wouldn't support WPA, only WEP. I followed instructions from another thread to try to update the firmware. But it still wouldn't offer WPA when I selected roaming.  If I selected manual configuration, WPA was offered but I still couldn't connect to the network. This seemed to be the end of that attempt, so I decided to try a new USB adapter. Like 828688 Ben, I'm not familiar with the internal workings of Linux & when I plug in the USB N13 I get nothing.

---

### Post by Swan48 on 2010-07-30
Forget the part about not finding the os/linux directory. I found it and made the changes from above but got the following message:
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta
root@sas-laptop:/home/sas/Desktop/RT3070_V2.3.0.2# exit
exit
sas@sas-laptop:~/Desktop/RT3070_V2.3.0.2$ dir
chips		  LICENSE\ ralink-firmware.txt	RT2870STACard.dat	  tools
common		  Makefile			RT2870STA.dat
include		  os				sta
iwpriv_usage.txt  README_STA_usb		sta_ate_iwpriv_usage.txt
sas@sas-laptop:~/Desktop/RT3070_V2.3.0.2$ sudo make install
[sudo] password for sas: 
make -C /home/sas/Desktop/RT3070_V2.3.0.2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/sas/Desktop/RT3070_V2.3.0.2/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/sas/Desktop/RT3070_V2.3.0.2/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.24-28-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.24-28-generic/kernel/drivers/net/wireless/
install: **cannot stat `rt3070sta.ko': No such file or directory**
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/sas/Desktop/RT3070_V2.3.0.2/os/linux'
make: *** [install] Error 2
sas@sas-laptop:~/Desktop/RT3070_V2.3.0.2$

---

### Post by roydrager on 2010-07-31
Swan48 sorry I didn't get those particular errors so I don't exactly have an answer for you.  From the top of your console output:

```

sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta

```

It seems that your first command, sudo make, failed, which probably caused the later errors of not finding rt3070.ko


The things different I noticed about our setups are: 

distro: 8.04 vs. 10.04
kernel: 2.6.24-28 vs. 2.6.32-21

directory:  it appears you made your own directory named Desktop/RT3070_V2.3.0.2/.  I just used the default directory that the DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz file creates when you untar it, Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/.  Perhaps the makefile looks specifically for this directory?

---

### Post by Swan48 on 2010-08-02
I just got my N13 to work.:D In fact, I'm using it now. I ended up installing 9.10 & that solved a lot of problems I was having. After updating 9.10, I followed the instructions Chilli gave Ben & hoped for similar results. So to answer my own question, to solve this problem if you're using 8.04, I suggest you update your system to at least 9.10 & follow the above instructions.

Thanks everyone.

---

### Post by 828688 Ben on 2010-08-02
I'm glad to see that this thread has helped everyone as much as it has helped me.

--
Ben

---

### Post by Kainage on 2010-09-03
For anyone with a setup similar to mine (Ubuntu 10.04, fresh install) these are the exact steps I followed to get mine up and running. Works great now with no problems. All of these steps were compiled from this thread, and perhaps some insight from a few others.

```
sudo su
```Create the file '/etc/udev/rules.d/network_drivers.rules' with this code all on one line with matching case and everything

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
```Create the file '/etc/modprobe.d/network_drivers.conf' with this code all on one line with matching case and everything

```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Download newest drivers from ralinktech.com (DPO_RT3070_LinuxSTA_V2.3.0.4_20100604) and extract them.
Go into the new folder and 
```
make
```Edit the following file
```
gedit os/linux/Makefile.6
```Rename the line that says
```
DAT_FILE_NAME = RT$(CHIPSET)STA.dat
```to
```
DAT_FILE_NAME = RT2870STA.dat
```Then in the same directory you ran 'make' in

```
make install
```Then finish up with 

```
mkdir /etc/Wireless/RT2870STA
cp ~folder_where_you_ran_make_install~/RT2870STA.dat /etc/Wireless/RT2870STA/
chmod 755 /etc/Wireless/RT2870STA/*
```finally restart your networking service

```
/etc/init.d/networking restart
```Should be up and running. Thanks to everyone in this thread and these forums!

---

### Post by iClouseau88 on 2010-09-03
> **Kainage said:**
> For anyone with a setup similar to mine (Ubuntu 10.04, fresh install) these are the exact steps I followed to get mine up and running. Works great now with no problems. All of these steps were compiled from this thread, and perhaps some insight from a few others.

```
sudo su
```Create the file '/etc/udev/rules.d/network_drivers.rules' with this code all on one line with matching case and everything

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
```Create the file '/etc/modprobe.d/network_drivers.conf' with this code all on one line with matching case and everything

```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Download newest drivers from ralinktech.com (DPO_RT3070_LinuxSTA_V2.3.0.4_20100604) and extract them.
Go into the new folder and 
```
make
```Edit the following file
```
gedit os/linux/Makefile.6
```Rename the line that says
```
DAT_FILE_NAME = RT$(CHIPSET)STA.dat
```to
```
DAT_FILE_NAME = RT2870STA.dat
```Then in the same directory you ran 'make' in

```
make install
```Then finish up with 

```
mkdir /etc/Wireless/RT2870STA
cp ~folder_where_you_ran_make_install~/RT2870STA.dat /etc/Wireless/RT2870STA/
chmod 755 /etc/Wireless/RT2870STA/*
```finally restart your networking service

```
/etc/init.d/networking restart
```Should be up and running. Thanks to everyone in this thread and these forums!
Hi,

> Create the file '/etc/udev/rules.d/network_drivers.rules' with this code all on one line with matching case and everything

Code:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"

Create the file '/etc/modprobe.d/network_drivers.conf' with this code all on one line with matching case and everything

Code:

install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id


How do you create a file?  Which command to use in the terminal?

Thanks!

---

### Post by Kainage on 2010-09-03
> **iClouseau88 said:**
> Hi,


How do you create a file?  Which command to use in the terminal?

Thanks!

```
gedit /etc/udev/rules.d/network_drivers.rules
``````

gedit /etc/modprobe.d/network_drivers.conf
```

---

### Post by bkwraith on 2010-09-05
Worked Flawlessly!  My HTPC and I thank you!

---

### Post by dc2045 on 2010-10-04
I have been trying the solutions outlined in this thread and others, but cannot seem to make the most simple steps work. I get an error every time I try the make command. I already have the build-essential package installed, as well as the gcc compiler. I just bought this adapter because I thought it would be compatible with Linux. Im really stuck here guys, any help would be appreciated.
```

robert@robert-desktop:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ make
make -C tools
make[1]: Entering directory `/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools/bin2h
cp -f os/linux/Makefile.6 /home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
robert@robert-desktop:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ sudo make
[sudo] password for robert: 
make -C tools
make[1]: Entering directory `/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools/bin2h
cp -f os/linux/Makefile.6 /home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1510: error: ‘struct net_device’ has no member named ‘open’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1511: error: ‘struct net_device’ has no member named ‘stop’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1512: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1513: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1519: error: ‘struct net_device’ has no member named ‘get_stats’
/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.c:1553: error: ‘struct net_device’ has no member named ‘validate_addr’
make[2]: *** [/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/robert/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
```

---

### Post by j_mill on 2010-10-06
> **Kainage said:**
> For anyone with a setup similar to mine (Ubuntu 10.04, fresh install) these are the exact steps I followed to get mine up and running. Works great now with no problems. All of these steps were compiled from this thread, and perhaps some insight from a few others....

Kainage, this worked perfectly for me and I am a total Ubuntu/Linux newbie. Thanks for posting it!

Now ... this Asus USB N13 is advertised as able to act as a wireless router ... does anyone know how to activate that function?

---

### Post by WarmonkeyUK on 2010-10-15
I get the same problem as dc2045. On Maverick, the solution no longer works, as you are unable to successfully make from source.

---

### Post by zyriik on 2010-11-30
> **chili555 said:**
> I think it is working! Please try to click the Network Manager icon and see if you see networks. If not, please do:```
sudo ifconfig ra0 up
sudo iwconfig ra0 mode managed
sudo iwlist ra0 scan
```Have you rebooted? Would you please? Thanks.
 
Hello, I was actually digging through all of these posts and now Im actually running into a problem with getting this wireless card running myself. I am running a little netbook that already has a built in wireless card however I am trying to use  the same network adapter as yourself for other purposes. Everything up until this point I have done and gotten at least some sign that its going through ok, however when I issue "ifconfig ra0 up" I get an error saying there is no such device. Can anyone give me a hand here?

---

### Post by leppel on 2011-01-12
> **chili555 said:**
> Here we go! Remove the device from the USB slot. Open a terminal and do these commands; it is perfectly alright to copy and paste and proofread carefully. Spacing, case and spelling must be exact!```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```The text editor gedit will pop open as a new file. Type in one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
```Proofread carefully, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Type in one long line:```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread carefully, save and close gedit. Detach the ethernet cable. Insert the USB device. Click the Network Manager icon and connect.


My thanks to poohstickz.


hi. Sorry to barge in on a response. But, I actually got mine to work here! my only problem is that i recently updated my system with the updater, and when my system restarted, the usb adapter is no longer working in the system. I have tried to re-run the commands given above, where the first time it was successful, and now i cant get it to work. what should i do? should there be an entry in /etc/init.d to make the driver start with the system? PLEASE HELP!!!

---

### Post by chili555 on 2011-01-12
> **leppel said:**
> hi. Sorry to barge in on a response. But, I actually got mine to work here! my only problem is that i recently updated my system with the updater, and when my system restarted, the usb adapter is no longer working in the system. I have tried to re-run the commands given above, where the first time it was successful, and now i cant get it to work. what should i do? should there be an entry in /etc/init.d to make the driver start with the system? PLEASE HELP!!!rt3070sta is now merged with rt2870sta. Amend the files you mentioned to change every reference to rt3070sta to rt2870sta. Reboot.

---

### Post by Cauda_Draconis on 2011-01-20
I'm having problems with the same card in Ubuntu 10.10. I tried following the instructions in [Kainage's post #61]("http://ubuntuforums.org/showpost.php?p=9801809&postcount=61"), but make failed:
```
vicky@Aphrodite:~/2009_1110_RT3070_Linux_STA_v2.1.2.0$ sudo make
make -C tools
make[1]: Entering directory `/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:219: warning: cast to pointer from integer of different size
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:306: warning: cast to pointer from integer of different size
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:324: warning: cast to pointer from integer of different size
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:341: warning: cast to pointer from integer of different size
/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.c:357: warning: cast to pointer from integer of different size
make[2]: *** [/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/vicky/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
```
I don't know what those error messages mean. Any ideas?

---

### Post by chili555 on 2011-01-20
> cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’Edit include/os/linux_rt.h to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. DO NOT replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.

Now do:```
sudo su
make clean
make 
make install
exit
```Post back with any errors. Warnings are probably OK.

---

### Post by bugianen on 2011-02-26
Hi,
following your instructions i succesffully installed drivers for my USB DWL-G122 Ver E1 wifi dongle.

I used a predefined script dwlg122e1.sh with changes you suggested in order to build correctly.

Now with iwconfig i can see "ra0" wireless interface.
My expectation was to find out a "wlan0"...is "ra0" correct?

My system is a backtrac 4 R2 on VMWare.

Regards.

---

### Post by chili555 on 2011-02-26
> is "ra0" correct?On the compiled version from the manufacturer, ra0 is correct. Enjoy!

---

### Post by Subharo on 2011-05-18
I'm using Ubuntu 11.04 Natty.  I have an Asus USB-N13.   The minimal "fix" is to merely blacklist rt2800usb in  /etc/modprobe.d/blacklist.conf and reboot.    Thanks, chili555!   :smile:

---

### Post by blackhawkover on 2011-06-19
The **blacklist rt2800usb** (from above post) was quick and painless solution for me after trying everything else.

I love this community. Thanks guys for helping us all struggle together for better computing. 
Thanks.

---

### Post by addux on 2011-08-27
A little late in the game, I just bought this product and using Ubuntu 10.10 it worked out of the Box. Linux is getting better by the day.


[117171.502392] usbcore: registered new interface driver rt2870
[117172.135071]  [<ffffffff814013b6>] usb_alloc_coherent+0x26/0x30
[117172.876582]  [<ffffffff814013b6>] usb_alloc_coherent+0x26/0x30
:):):)

---

### Post by therealtatata on 2011-11-25
> **Kainage said:**
> For anyone with a setup similar to mine (Ubuntu 10.04, fresh install) these are the exact steps I followed to get mine up and running. Works great now with no problems. All of these steps were compiled from this thread, and perhaps some insight from a few others.

```
sudo su
```Create the file '/etc/udev/rules.d/network_drivers.rules' with this code all on one line with matching case and everything

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"
```Create the file '/etc/modprobe.d/network_drivers.conf' with this code all on one line with matching case and everything

```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```Download newest drivers from ralinktech.com (DPO_RT3070_LinuxSTA_V2.3.0.4_20100604) and extract them.
Go into the new folder and 
```
make
```Edit the following file
```
gedit os/linux/Makefile.6
```Rename the line that says
```
DAT_FILE_NAME = RT$(CHIPSET)STA.dat
```to
```
DAT_FILE_NAME = RT2870STA.dat
```Then in the same directory you ran 'make' in

```
make install
```Then finish up with 

```
mkdir /etc/Wireless/RT2870STA
cp ~folder_where_you_ran_make_install~/RT2870STA.dat /etc/Wireless/RT2870STA/
chmod 755 /etc/Wireless/RT2870STA/*
```finally restart your networking service

```
/etc/init.d/networking restart
```Should be up and running. Thanks to everyone in this thread and these forums!

When I cd into the directory and 
```
make
```
I get this:
```

root@bt:~/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1# make
make -C tools
make[1]: Entering directory `/root/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/root/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /root/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.38/build SUBDIRS=/root/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.38/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.38/build'
make: *** [LINUX] Error 2

```

I'm using Ubuntu 10.04, Backtrack 5 to be precise. Total Linux newbie. Hope you guys can help...

---

