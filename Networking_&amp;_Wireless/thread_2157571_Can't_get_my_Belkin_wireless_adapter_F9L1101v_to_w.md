---
title: "Can't get my Belkin wireless adapter F9L1101v to work!"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by theRandy on 2013-06-25
Ok so ive gone through lots of tutorials on how to install the drivers using ndiswrapper with no luck.  I have the installation disk and have access to the:

netrtwlanu.cat
netrtwlanu.inf
rtwlanu.inf

When i type the lsusb command it recognizes the device is there:

```
root@bt:~# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 050d:110a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Im fairly sure i installed the driver correctly, WICD just shows "No wireless networks found"

---

### Post by theRandy on 2013-06-30
*bump*

---

### Post by KARNVORbeefRAGE on 2013-07-01
Unfortunately after a long search this is what I have come up with:
[https://bbs.archlinux.org/viewtopic.php?id=127710](https://bbs.archlinux.org/viewtopic.php?id=127710)  (more on ndiswrapper with same chipset)

I also found this and under "linux driver" it says unsupported...
[http://wikidevi.com/wiki/Belkin_F9L1101v1](http://wikidevi.com/wiki/Belkin_F9L1101v1)

If all else fails, this wifi adapter should work after a little modification.  
[http://www.belkin.com/us/F9L1103-Belkin/p/P-F9L1103](http://www.belkin.com/us/F9L1103-Belkin/p/P-F9L1103)
[http://wikidevi.com/wiki/Belkin_F9L1103](http://wikidevi.com/wiki/Belkin_F9L1103)

Unfortunately that means purchasing a more expensive adapter, but this is the model I use and the driver build was successful.  
[https://bbs.archlinux.org/viewtopic.php?id=149329](https://bbs.archlinux.org/viewtopic.php?id=149329)

Good luck and I hope you find a better answer than mine.

---

### Post by theRandy on 2013-07-01
Ahh ok i was hoping that it would be supported, should have checked before i bought it haha. Thanks for your response

---

### Post by m86 on 2013-07-01
Your USB ID doesn't match up with the v1. You have a v2 F9L1101, right?

The v2 uses RTL8192DU - if you can't get it working with ndiswrapper, you *may* be able to get it to work with [Realtek's vendor driver]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=53&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#3102").. or maybe with the source tree [here]("https://github.com/lwfinger/rtl8192du").

---

### Post by chili555 on 2013-07-01
> 050d:110a Belkin Components Your device works with the very new driver 8192du:```
$ modinfo 8192du.ko | grep 110A
alias:          usb:v[COLOR="#FF0000"]050D[/COLOR]p[COLOR="#FF0000"]110A[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```Here is the procedure to download and install it: [http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576](http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576)

Please post back if you get stuck or need additional assistance.

---

### Post by KARNVORbeefRAGE on 2013-07-01
[QUOTE=m86;12713782]Your USB ID doesn't match up with the v1. You have a v2 F9L1101, right?

I will should have paid attention to that, thanks and good eye.

---

### Post by theRandy on 2013-07-01
> **m86 said:**
> Your USB ID doesn't match up with the v1. You have a v2 F9L1101, right?

The v2 uses RTL8192DU - if you can't get it working with ndiswrapper, you *may* be able to get it to work with [Realtek's vendor driver]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=53&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#3102").. or maybe with the source tree [here]("https://github.com/lwfinger/rtl8192du").

Its the F9L1101v2, how can i delete the drivers i already installed to try do it from scratch?

---

### Post by theRandy on 2013-07-01
Ok so i downloaded the file from the Realtek site and unzipped it. Then i tried to install it using the install.sh script but i got the following error:

```
root@bt:~/Downloads/RTL8192DU_linux_v4.0.0_5260.20120921# sudo bash install.sh
: command not found 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
: command not found: 
: No such file or directoryiver
Decompress the driver source tar ball:
    
tar: \r\r: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
: command not found: 
android_reference_codes
android_reference_codes_ICS_nl80211
document
driver
hardware_wps_pbc
install.sh
readme.txt
ReleaseNotes.pdf
WiFi_Direct_User_Interface
wireless_tools
wpa_supplicant_hostapd
: command not found: 
install.sh: line 50: syntax error near unexpected token `else'
'nstall.sh: line 50: `else    

```

---

### Post by chili555 on 2013-07-01
That old antique isn't going to work. I suggest you remove ndiswrapper and use the procedure that is proven that I linked.

---

### Post by theRandy on 2013-07-01
> **chili555 said:**
> Your device works with the very new driver 8192du:```
$ modinfo 8192du.ko | grep 110A
alias:          usb:v[COLOR=#FF0000]050D[/COLOR]p[COLOR=#FF0000]110A[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
```Here is the procedure to download and install it: [http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576](http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576)

Please post back if you get stuck or need additional assistance.

I followed the instructions on this thread and tried doing:
```

sudo apt-get install build-essential linux-headers-generic git git clone https://github.com/lwfinger/rtl8192du.git cd rtl8192du make sudo make install sudo modprobe 8192du
```

when i try tun the  

sudo apt-get install build-essential linux-headers-generic git line i get the error message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-generic has no installation candidate


```

I skipped it and the rest of the instructions worked fine, I know have a wpa_gui application but when i run it it says could not get status from wpa_supplicant and i cannot scan for wireless networks. 
Also WICD still shows "No wireless networks found"

Running iwconfig in terminal shows:
```
wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

Which is good because before there was no wlan0, so its definitely a step in the right direction! Any idea why its still not functional though, is it because i skipped that first instruction?

---

### Post by chili555 on 2013-07-02
> is it because i skipped that first instruction? Nope. If you didn't have the appropriate headers installed, it would have not built the driver and ended in an error or three. Let's see if there are any clues in the message logs and elsewhere:```
dmesg | grep -e rtl -e 8192
rfkill list all
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```> I know have a wpa_gui applicationWhich? Do you means Wicd?

---

### Post by rgibbs on 2013-07-03
you rock... was just about to take the belkin back and try again... followed your cmd line recipes and got my wireless up and running... would not have happened without your easy to follow solutions... i love this community

---

### Post by theRandy on 2013-07-06
> **chili555 said:**
> Nope. If you didn't have the appropriate headers installed, it would have not built the driver and ended in an error or three. Let's see if there are any clues in the message logs and elsewhere:```
dmesg | grep -e rtl -e 8192
rfkill list all
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Which? Do you means Wicd?

Ok so when run the wlan0 scan it actually finds shows my wireless:
```
root@bt:~# sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 28:C6:8E:70:A7:13
                    ESSID:"lgdore_2GEXT"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010CE31E4FA3125860FA853ED269DF71CB81021000D4E4554474541522C20496E632E10230008574E32353030525010240008574E3235303052501042000230311054000800060050F204000110110008574E323530305250100800020084103C000103
                    Quality=0/100  Signal level=100/100  
          Cell 02 - Address: 2A:C6:8E:70:A7:13
                    ESSID:"lgdore_5GEXT"
                    Protocol:IEEE 802.11an
                    Mode:Master
                    Frequency:5.22 GHz (Channel 44)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD790050F204104A0001101044000102103B00010310470010CE31E4FA3125860FA853ED269DF71CB81021000D4E4554474541522C20496E632E10230008574E32353030525010240008574E3235303052501042000230311054000800060050F204000110110008574E323530305250100800020084103C000103
                    Quality=0/100  Signal level=100/100  


```

but wicd still shows no wireless detected. And the wpa_gui is a wpa_supplicant user interface, but nothing inside it works.

---

### Post by praseodym on 2013-07-06
Choose **wlan0** as interface name and **wext** as driver in Wicd. Networkmanager is deactivated?
```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

### Post by theRandy on 2013-07-06
> **praseodym said:**
> Choose **wlan0** as interface name and **wext** as driver in Wicd. Networkmanager is deactivated?
```

sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

Ahh your a genius, the wireless internet was set to eth0 for some reason. Working now, thanks for the help

---

