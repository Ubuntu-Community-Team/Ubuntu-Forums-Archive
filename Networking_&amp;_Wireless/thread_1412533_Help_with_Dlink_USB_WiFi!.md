---
title: "Help with Dlink USB WiFi!"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Cessna 206 on 2010-02-21
I have been trying to get 9.10 to work with my D Link DWA 125 USB WiFi antenna for days now. I have searched these forums as well as other forums for answers. I have tried all of the suggestions I have come across, some simple, some complex. Nothing works. I have tried ndiswrapper, blacklisting drivers, re-installing, modifying the 2870sta.dat file......nothing works (or maybe I'm doing it wrong...I don't know).

I have a fresh install of 9.10 .Can someone please walk me through this and show me what I'm doing wrong?

---

### Post by chili555 on 2010-02-21
I'd love to help. First, let's make sure which device we have. Please plug in the device and post:```
lsusb
```Now, let's see what we have on the system:```
sudo updatedb
locate rt2870sta
lsmod | grep rt2
```updatedb will take a few moments; please be patient. Depending on what we see, we will have a better idea of how to proceed.

---

### Post by Cessna 206 on 2010-02-21
Thanks for the quick response.

	 	 	 	 	  


 david@david-desktop:~$ lsusb  
 Bus 002 Device 002: ID 0644:0200 TEAC Corp.  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 003: ID 13ba:0017 Unknown PS/2 Keyboard+Mouse Adapter  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 14cd:6600 Super Top USB 2.0 IDE DEVICE  
 Bus 001 Device 004: ID 07d1:3c0d D-Link System  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 



 david@david-desktop:~$ sudo updatedb  
 [sudo] password for david: 



 david@david-desktop:~$ locate 2870sta  
 /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt2870/rt2870sta.ko 



 david@david-desktop:~$ lsmod | grep rt2 
 rt2800usb              37372  0  
 rt2x00usb              11548  1 rt2800usb  
 rt2x00lib              29756  2 rt2800usb,rt2x00usb  
 led_class               4096  1 rt2x00lib  
 input_polldev           3716  1 rt2x00lib  
 mac80211              181236  2 rt2x00usb,rt2x00lib  
 cfg80211               93052  2 rt2x00lib,mac80211  
 crc_ccitt               1852  1 rt2800usb  
 david@david-desktop:~$

---

### Post by chili555 on 2010-02-21
These Ralinks are fun! I think I could get all the way to 5,000 posts strictly on Ralinks!

The module that's loaded, rt2800usb thinks it's an appropriate driver (and not rt2870sta):> $ modinfo rt2800usb | grep 07D1
--- snip ---
alias:          usb:v[COLOR="Blue"]07D1[/COLOR]p[COLOR="Blue"]3C0D[/COLOR]d*dc*dsc*dp*ic*isc*ip*> [COLOR="Blue"]07d1:3c0d[/COLOR] D-Link System I would love to see:```
iwconfig
dmesg | grep rt28
```Thanks.

---

### Post by 2hot6ft2 on 2010-02-21
> **chili555 said:**
> These Ralinks are fun! I think I could get all the way to 5,000 posts strictly on Ralinks!
That's a little twisted.:-k
And they are so abundant, just try and find a usb wifi adapter in the stores that doesn't have a pesky Ralink chip.

You go for it...:lol:

---

### Post by Cessna 206 on 2010-02-21
david@david-desktop:~$ iwconfig  
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
 

 david@david-desktop:~$ dmesg | grep rt28  
 [   19.311295] Registered led device: rt2800usb-phy0::radio  
 [   19.311312] Registered led device: rt2800usb-phy0::assoc  
 [   19.311330] Registered led device: rt2800usb-phy0::quality  
 [   19.311572] usbcore: registered new interface driver rt2800usb  
 [   19.413176] rt2800usb 1-6:1.0: firmware: requesting rt2870.bin  
 david@david-desktop:~$

---

### Post by chili555 on 2010-02-21
> wlan0 IEEE 802.11bgn ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=9 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 Looks like it's working correctly! When you click the Network Manager icon, do you see your network? Can you try to connect? What happens...or doesn't...when you try?

---

### Post by Cessna 206 on 2010-02-21
When I left click on the network icon it says "Wireless Networks - disconnected". Right click shows networking and wireless is enabled. The network icon shows no signal strength or activity. Firefox says "can't find server" when web address is typed in.

---

### Post by Cessna 206 on 2010-02-21
There is also no light blinking on the adapter to indicate that there is any communication going on.

---

### Post by chili555 on 2010-02-21
What does this tell us:```
sudo iwlist wlan0 scan
```I am surprised that you see no networks, most especially yours, in Network Manager.

---

### Post by Cessna 206 on 2010-02-21
I'm surprised too! It seems like it wants to work. That's why it's so frustrating!

  	 	 	 	 	 	  david@david-desktop:~$ sudo iwlist wlan0 scan  
 [sudo] password for david:  
 wlan0     No scan results  
 

 david@david-desktop:~$

---

### Post by chili555 on 2010-02-21
I notice this:> wlan0 IEEE 802.11bgn ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
[COLOR="Blue"]Tx-Power=9 dBm[/COLOR]You might try:```
sudo iwconfig wlan0 txpower [COLOR="Red"]10[/COLOR]
```Keep increasing the number until the terminal complains, usually that it's an invalid command. Then try again:```
sudo iwlist wlan0 scan
```

---

### Post by Cessna 206 on 2010-02-21
No luck

  	 	 	 	 	 	  david@david-desktop:~$ sudo iwconfig wlan0 txpower 10  
 [sudo] password for david:  
 Error for wireless request "Set Tx Power" (8B26) :  
     SET failed on device wlan0 ; Invalid argument.  
 david@david-desktop:~$

---

### Post by chili555 on 2010-02-21
I need to be away for a while, but this is where I suggest we look next. Don't be intimidated. Normal humans wote this and we can figure it out...easily, as a matter of fact.

[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=AYCBS8DDB4mXtgeBs8CcBw&sa=X&oi=translate&ct=result&resnum=4&ved=0CBYQ7gEwAw&prev=/search%3Fq%3D%252207d1:3c0d%2522%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26hs%3DMkw%26sa%3DG%26rls%3Dcom.ubuntu:en-US:official](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=AYCBS8DDB4mXtgeBs8CcBw&sa=X&oi=translate&ct=result&resnum=4&ved=0CBYQ7gEwAw&prev=/search%3Fq%3D%252207d1:3c0d%2522%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26hs%3DMkw%26sa%3DG%26rls%3Dcom.ubuntu:en-US:official)

---

### Post by Cessna 206 on 2010-02-21
Thanks. I appreciate the help. Will check back later.

---

### Post by chili555 on 2010-02-21
Before we go too crazy, I wonder if Network Manager is having any effect on the wireless. This is from [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themDo you have an ethernet wired connection going? If you detach the wire, do you then see wireless networks in Network Manager?

---

### Post by Cessna 206 on 2010-02-21
There is no wired internet connection available where my desktop is. All I have is wireless. I'd have to lug my desktop downstairs to have a wired connection (I will for testing purposes if needed).

Believe me, I wish I had a wired connection upstairs.

There is nothing plugged into the ethernet port either.

---

### Post by chili555 on 2010-02-21
Good. Grab your USB key and download this and transfer it to your desktop upstairs. While you do that, I will write some instructions.

RT3070USB (RT307x)

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Back in a few moments.

---

### Post by Cessna 206 on 2010-02-21
Ready. Copied package into Documents folder.

---

### Post by chili555 on 2010-02-21
Drag and drop the file to any convenient place, your Documents folder, for example. Right-click it and select 'Extract Here.' A folder will be created called 2009_1110_RT3070_Linux_STA_v2.1.2.0. 

Drop your Ubuntu install CD in the tray. Open a terminal and do:

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
cd Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0
gedit os/linux/config.mk 

```
Find the lines: HAS_WPA_SUPPLICANT=n and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

Change both lines to =y

Proofread, save and close gedit.

```
sudo su
make
```

You may get a few warnings, but no errors. If you get errors, stop and post them here.

```
make install
gedit /etc/modprobe.d/blacklist.conf
```

Add two lines:

```
blacklist rt2800usb
blacklist rt2x00usb

```
Proofread, save and close gedit.

Reboot.
```
lsmod | grep rt3

```
Did rt3070sta get loaded automagically?

```
iwconfig
```

Do you see a wireless interface, ra0 perhaps? Can you connect in Network Manager?

---

### Post by Victormd on 2010-02-21
I'm having a very similar problem but my USB dongle is different and just wanted to check before following the same steps. Here are the results for some of the commands suggested before (this is on *_mythbuntu_*):
**lsusb**
> Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00f9 Microsoft Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 07d1:3c10 D-Link System 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 2304:0225 Pinnacle Systems, Inc. [hex] 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**iwconfig**
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=26 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I've set: **sudo iwconfig wlan0 txpower 26** to the max before getting an error and this is the result from **sudo iwlist wlan0 scan**
> wlan0     No scan results

sorry, forgot to post this:
**dmesg|grep ar91**
> [    8.231284] usb 2-6: firmware: requesting ar9170.fw
[    9.184136] Registered led device: ar9170-phy0::tx
[    9.184148] Registered led device: ar9170-phy0::assoc
[    9.184167] usbcore: registered new interface driver ar9170usb

I was able to connect at one point but then lost the connection and haven't been able to get a list of networks since... Suggestions??

---

### Post by chili555 on 2010-02-21
> Suggestions??Yes. Please start a new thread so we don't get confused as to who is who. I'll do my best to help.

---

### Post by Cessna 206 on 2010-02-21
Everything went well until reboot. It seems the wlan is not showing up at all now. Here's the results of the last two commands:


  	 	 	 	 	 	  david@david-desktop:~$ lsmod | grep rt3 
 david@david-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 david@david-desktop:~$

---

### Post by Victormd on 2010-02-21
Here's the thread... any help would be greatly appreciated.
[http://ubuntuforums.org/showthread.php?p=8861963#post8861963](http://ubuntuforums.org/showthread.php?p=8861963#post8861963)

Thanks!!!

---

### Post by chili555 on 2010-02-21
> **Cessna 206 said:**
> Everything went well until reboot. It seems the wlan is not showing up at all now. Here's the results of the last two commands:


  	 	 	 	 	 	  david@david-desktop:~$ lsmod | grep rt3 
 david@david-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 david@david-desktop:~$Let's try to load it explicitly:```
sudo modprobe rt3070sta
iwconfig
```Any improvement?

---

### Post by Cessna 206 on 2010-02-21
No good

  	 	 	 	 	 	  david@david-desktop:~$ sudo modprobe rt3070sta  
 [sudo] password for david:  
 david@david-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 david@david-desktop:~$

---

### Post by Cessna 206 on 2010-02-21
lsmod | grep rt3 is now showing rt3070sta     503348  0

---

### Post by chili555 on 2010-02-21
Please let us see:```
dmesg | grep rt3
dmesg | grep rt2
```Thanks.

---

### Post by Cessna 206 on 2010-02-21
david@david-desktop:~$ dmesg | grep rt3 
 [ 1580.903517] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.  
 david@david-desktop:~$ dmesg | grep rt2 
 [ 1580.907334] usbcore: registered new interface driver rt2870  
 [ 6596.703134] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [ 6596.706852] Error: Driver 'rt2870' is already registered, aborting...  
 [ 6596.706856] usbcore: error -17 registering interface 	driver rt2870  
 david@david-desktop:~$

---

### Post by chili555 on 2010-02-21
Please do:```
lsmod | grep rt2
```If you see an rt2870 in there (which I don't understand in the least), please do:```
sudo rmmod -f rt2870whatever_u_found
sudo modprobe rt3070sta
iwconfig
```If *lsmod* looks at all suspicious, please post it.

---

### Post by Cessna 206 on 2010-02-21
Looks empty

                                 david@david-desktop:~$ lsmod | grep rt2 
 david@david-desktop:~$
  	 	 	 	 	 	  david@david-desktop:~$ sudo modprobe rt3070sta  
 [sudo] password for david:  
 david@david-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 david@david-desktop:~$

---

### Post by chili555 on 2010-02-21
Did you previosly try ndiswrapper?? Please let us see:```
lsmod | grep ndis
```

---

### Post by Cessna 206 on 2010-02-21
I did, but it didn't work. Remember, I'm on a fresh (re)install here.

lsmod | grep ndis shows nothing

---

### Post by Cessna 206 on 2010-02-21
Judging by the incredible amount of WiFi related complaints, I'm guessing WiFi is not a strong selling point for Ubuntu.

It's funny. I ran 7.10 on a Gateway laptop. It worked great, WiFi included. No need for any messing around.

Now I'm on day 3 (or is it 4) of trying to get 9.10 to work. Other than becoming familiar with the console and the blacklist.conf file I haven't accomplished anything.

It's like one step forward and 5 steps backwards.

---

### Post by chili555 on 2010-02-21
Please do:```
sudo cp /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat
sudo gedit /etc/modules
```Add a new line:```
rt3070sta
```Proofread, save and close gedit.```
sudo rmmod -f rt3070sta
sudo modprobe rt3070sta
sudo ifconfig ra0 up
iwconfig
```Any improvement? If not, please reboot and then do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```In your reply, please attach the dmesg.zip file for my surgical evaluation.

---

### Post by Cessna 206 on 2010-02-21
david@david-desktop:~$ sudo cp /etc/Wireless/RT3070STA/RT2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat  
 [sudo] password for david:  
 david@david-desktop:~$ sudo gedit /etc/modules  
 david@david-desktop:~$ sudo rmmod -f rt3070sta  
 david@david-desktop:~$ sudo modprobe rt3070sta  
 david@david-desktop:~$ sudo ifconfig ra0 up  
 ra0: ERROR while getting interface flags: No such device  
 david@david-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 david@david-desktop:~$

---

### Post by chili555 on 2010-02-21
> I'm guessing WiFi is not a strong selling point for Ubuntu.It's a challenge because the Ralinks, Realteks and Broadcoms of the world live and die making the latest, greatest go-fast chipsets and then fail to provide working Linux drivers.

If you went to the pawn shop and bought some crusty old 802.11b PCMCIA card that only does WEP, it would work out of the box.

People naturally go buy a new wireless device, not realizing that Linux drivers are either non-existent or in early beta. Printers are more or less the same.

I am fairly confident we'll get it.

---

### Post by chili555 on 2010-02-21
While I study dmesg, please run:```
modinfo rt3070sta
```We need to know the location and we hope it's /lib/modules/2.6.31-19-generic/kernel/drivers/net/wireless/rt3070sta.ko, and not from staging. If it is from staging, do:```
sudo updatedb
locate rt3070sta.ko
```Thanks.

---

### Post by Cessna 206 on 2010-02-21
I know it's not Ubuntus fault. I wish more of the hardware companies would develop drivers for open source OS.

---

### Post by Cessna 206 on 2010-02-21
It looks like it was in staging

  	 	 	 	 	 	  david@david-desktop:~$ modinfo rt3070sta  
 filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko 
 version:        2.0.1.0  
 license:        GPL  
 description:    RT2870 Wireless Lan Linux Driver  
 author:         Paul Lin <paul_lin@ralinktech.com>  
 srcversion:     D4B10F9A8294B392DA64AEE 
 alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*  
 alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*  
 depends:         
 staging:        Y  
 vermagic:       2.6.31-14-generic SMP mod_unload modversions 586  
 parm:           mac:rt28xx: wireless mac addr (charp)  
 david@david-desktop:~$ sudo updatedb  
 [sudo] password for david:  
 david@david-desktop:~$ locate rt3070sta 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/.rt3070sta.ko.cmd 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/.rt3070sta.mod.o.cmd 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/.rt3070sta.o.cmd 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/rt3070sta.ko 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/rt3070sta.mod.c 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/rt3070sta.mod.o 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/rt3070sta.o 
 /home/david/Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/.tmp_versions/rt3070sta.mod 
 /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rt3070sta.ko 
 /lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko 
 david@david-desktop
 


I really appreciate your help.

---

### Post by chili555 on 2010-02-21
You have a staging and a net. We built 'net' from the tarball, but the computer is using staging. Here is why it matters. Your device is:> Bus 001 Device 004: ID [COLOR="Blue"]07d1:3c0d[/COLOR] D-Link System Modinfo for staging looks like this:> $ modinfo /lib/modules/2.6.31-19-generic/kernel/drivers/staging/rt3070/rt3070sta.ko | grep 07D1
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*No sign of product 3C0D.

Net looks like this:> $ modinfo /lib/modules/2.6.31-19-generic/kernel/drivers/net/wireless/rt3070sta.ko | grep 07D1
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:[COLOR="Blue"]v07D1p3C0D[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*So, let's get staging out of the way and see if net loads and creates an interface:```
sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/rt3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/rt3070sta.ko.old
sudo rmmod -f rt3070sta
sudo modprobe rt3070sta
iwconfig
```Those are tickmarks, on my US keyboard with ~.

Now is there an interface, ra0, perhaps.

After 40 posts, I break out the meds.

---

### Post by chili555 on 2010-02-21
Gotta run. I'll check in tomorrow morning.

---

### Post by Cessna 206 on 2010-02-21
Good night. Thanks for the help. Hopefully this won't take too much longer.

  	 	 	 	 	 	  david@david-desktop:~$ sudo mv /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/rt3070sta.ko /lib/modules/`uname -r`/kernel/drivers/staging/rt3070/rt3070sta.ko.old  
 [sudo] password for david:  
 david@david-desktop:~$ sudo rmmod -f rt3070sta  
 david@david-desktop:~$ sudo modprobe rt3070sta  
 FATAL: Could not open '/lib/modules/2.6.31-14-generic/kernel/drivers/staging/rt3070/rt3070sta.ko': No such file or directory  
 david@david-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 david@david-desktop:~$

---

### Post by chili555 on 2010-02-22
Let's try another way and work out how to make it work automagically after we work out how to get it to simply work!!

Please do:```
cd Documents/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux
sudo insmod rt3070sta
iwconfig
```Any new developments?

---

### Post by mark bower on 2010-02-23
You can save a heap of frustration by getting the Belkin F5D7050 USB wireless adapter.  It works out of the box with native (built into Ubuntu) drivers.  I can practically guarantee it working for you.  It was recommended in two posts so I switched to it and junked my Netgear version.  I have used it with Ubu 8.10, 9.04 and 9.10, three different computers and as many motherboards, with absolutely no problems.  So I keep posting this information.

I purchased the F5D7050 because my PCI wireless adapters will not work without ndiswrapper(and as mentioned the Netgear did not work).  I only returned to using the wrapper so I could use my PCI adapters with high gain antennas.  Going thru 3 thick plaster walls at my residence to reach the router, the F5D7050 works just fine with a signal strength of about 30/100.  However, with the PCI cards and antennas I get about 50/100.   

This is in no way to diminish the efforts of Chili555 - he helped me with ndiswrapper.  Its just if you want an easy install and your time is valuable, spring for the $30 or so for the F5D7050.

mark

---

### Post by Cessna 206 on 2010-02-24
Sorry, I've been busy with work.

Chili, I appreciate the help, but I have decided to just buy another adapter.

Thanks for the tip Mark, I will definitely look into that!

---

