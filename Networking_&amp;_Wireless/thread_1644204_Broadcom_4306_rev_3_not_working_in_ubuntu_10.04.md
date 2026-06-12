---
title: "Broadcom 4306 rev 3 not working in ubuntu 10.04"
date: 2010-12-12
forum: Networking &amp; Wireless
---

### Post by peperomia on 2010-12-12
I'm having a bit of trouble getting the wireless to work on a Dell Inspiron 9200. Following the instructions [here]("http://ubuntuforums.org/showthread.php?t=1490717") didn't help, though I didn't get any errors along the way. Scanning for networks produced 'No scan results,' though.  I'm using Ubuntu 10.04.1.

**lscpi  | grep 'Broadcom\ Corporation'**
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)[B]

iwconfig wlan0
[/B]wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off[B]

lsmod | grep 'b43'
[/B]b43                   163524  0 
mac80211              205402  1 b43
cfg80211              126528  2 b43,mac80211
led_class               2864  2 b43,sdhci
ssb                    38902  2 b43,b44[B]

 dmesg | grep 'b43'
[/B][    1.249401] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[  225.980415] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[  226.172959] Registered led device: b43-phy0::tx
[  226.173684] Registered led device: b43-phy0::rx
[  226.174350] Registered led device: b43-phy0::radio
[  226.433141] b43-phy1: Broadcom 4306 WLAN found (core revision 5)
[  226.496771] Registered led device: b43-phy1::tx
[  226.497012] Registered led device: b43-phy1::rx
[  226.497489] Registered led device: b43-phy1::radio
[  226.548098] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  226.664005] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  226.678441] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  226.687350] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[  226.830726] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2185.012259] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 3021.556075] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)[B]

 sudo lshw -C network
 [/B] *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:0f:ed:0e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Since there's no driver info here under configuration, I'm guessing it's a driver issue, but I don't know how to fix it. System -> Administration -> Hardware Drivers says the Broadcom B43 wireless driver is activated and currently in use.

**iwlist wlan0 scan**
wlan0     No scan results

[B]sudo /etc/init.d/networking restart
[/B] * Reconfiguring network interfaces...                                       [ OK ]

---

### Post by bkratz on 2010-12-13
Really everything looks pretty normal ( I admit I didn't look too closely after finding this)

iwconfig wlan0
wlan0 IEEE 802.11bg ESSIDff/any 
[COLOR="Red"]Mode:Ad-Hoc[/COLOR] Frequency:2.412 GHz Cell: Not-Associated 
Tx-Power=20 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

Ad hoc is between computers, not to an A/P.

You might want to try



sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up


Which hopefully will make your connection work.  This is in the terminal and the sudo will require your password, which will not be echoed (not even stars) just press enter when done.

---

### Post by chemdtn687 on 2010-12-13
bkratz is correct... somehow you got your wlan in ad-hoc mode.

---

### Post by peperomia on 2010-12-14
I'm not sure how the mode got changed to Ad-Hoc, but changing it back to managed does not fix the problem.

---

### Post by bkratz on 2010-12-14
How about trying  

sudo modprobe b43
sudo iwlist scan

and 
sudo lshw -C network

again, and copy/paste

also
rfkill list

This one may or may not have an output, if not
then 

sudo apt-get install rfkill

again try again

---

### Post by peperomia on 2010-12-14
I didn't get any errors or warnings from modprobe.  The rest of what you've asked for is below. There are no changes in lshw output from the initial post and rfkill reports no blocks.
[B]
sudo iwlist scan[/B]
wlan0     No scan results

**sudo lshw -C network**
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:0f:ed:0e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

**rfkill list**
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by peperomia on 2010-12-21
I wasn't able to get my wireless working with the Linux driver.  However, I was able to get my wireless working using another approach.  I grabbed the windows driver from [sidulus.textdrive.com]("http://sidulus.textdrive.com/bcmwl5sys.zip") and followed [this guide]("http://ubuntuforums.org/showthread.php?t=201902") for using Ndiswrapper with a Broadcom 4306.  Hope this helps someone else!

---

