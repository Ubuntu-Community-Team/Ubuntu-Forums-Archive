---
title: "Wifi disconnects after 10 mins and wont connect back"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by big10 on 2011-12-19
Hello Guys,
I have been using Ubuntu for last 7 years and never had any  problems. For last 2 years I am using an acer AspireOne netbook on dual boot with Ubuntu and WinXp without any problem, but for last 2 months my wireless has gone mad.
It wont stay connected for more than 10-15 minutes and automatically gets disconnected and then keep on attempting to connect back to wifi. if i disable wifi and then enable it, I wont even see the wifi networks to connect back.
I initially thought this is a hardware issue but then on WinXp it worked fine and on my another Dell laptop the wifi is perfectly stable so no issues with wifi router as well.

Once disconnected i have to let my netbook shutdown for atleast an hours and restart to get the wifi work again - just to get disconnected in 10 minutes.

Yesterday I upgraded to 11.10 from 11.04 (which was also upgraded from 10.10) but the problem persists.

My wifi driver details are as following:

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

I have tried to see if there is any patterns in internet connectivity and following observations were made:

1) I am facing similar issue with bluetooth internet connectivity using my Android Phone - i.e. it wont connect back after 10 minutes.

2)  my ethernet and usb tethering via android phone is perfectly stable - in fact I upgraded to 11.10 using android tethering using the wifi connectivity to Android phone.

Please advice, this is my first post in as many years and its always been a plug and play experience for me on Ubuntu and all my files and work is on Ubuntu file system now and kind of stuck.

Many Thanks.

---

### Post by praseodym on 2011-12-19
Hi,

there is a bug in 11.10 with the Atheros drivers ath5k and ath9k, respectively, concerning the hardware encryption. You can turn it off via:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by big10 on 2011-12-19
Thanks praseodym, I ran the above code - though the problem persisted. i have tried using WEP and WPA both.

---

### Post by praseodym on 2011-12-19
You can try Wicd instead of the NetworkManager:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver. It works much better with WEP/WPA.

Or you first try using WPA2-AES if possible with the networkmanager

---

### Post by big10 on 2011-12-21
thanks for your help and patience. I tried wicd it did not got installed by above command somehow - then i installed it from software center and tried as suggested by you. unfortunatly it wont even detect any wireless network. I understand I need to customise it before it can be made to work but still all other connections like android tethering stopped working as well. So i reverted back to NetworkManager.
 
Is it possible that heating of netbook may stop wireless networks to stop working, This is because even my bluetooth stops working after 10-12 minutes from starting the laptop, while there is no problem with wired networks.
 
Please advice if i need to pull out some details helpful for you.
 
Many Thanks

---

### Post by praseodym on 2011-12-21
Please show
```
iwconfig
sudo iwlist scan
```

---

### Post by big10 on 2011-12-21
iwconfig details
lo        no wireless extensions.

eth0      no wireless extensions.
Thanks, Please find the details as requested. masked mac address.

wlan0     IEEE 802.11bgn  ESSID:"MyCon"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1E:40:83:D2:B6   
          Bit Rate=36 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:26   Missed beacon:0

########################################################################
iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:40:XX:XX:XX
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c760a187
                    Extra: Last beacon: 440ms ago
                    IE: Unknown: 00050000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
          Cell 02 - Address: 00:1E:40:XX:XX:XX
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"SSIDXXXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b99beca4
                    Extra: Last beacon: 231432ms ago
                    IE: Unknown: 00054D79436F6E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014

---

### Post by big10 on 2011-12-21
Also facing same issue with mobile broadband as mentioned by two users on this thread - [http://ubuntuforums.org/showthread.php?t=1794356](http://ubuntuforums.org/showthread.php?t=1794356)

Not sure if there is any correlation

Thanks

---

### Post by praseodym on 2011-12-21
Try to not hide the network, this is no security advantage. Also try to set the encryption mode from WEP to WPA2-AES if possible.

---

### Post by sailor2001 on 2011-12-24
go to: system preferences/wallpaper and untick the 2 screensaver options

---

