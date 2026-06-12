---
title: "RTL-8185 linux driver ./makedrv err &amp; ndiswrapper not working"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by scurry7 on 2008-12-18
Hello all I have tried 2 methods to get my wireless working
**1st : download the linux driver**
(1) download driver: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)
	wget [ftp://152.104.238.19/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz](ftp://152.104.238.19/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz)
(2) unzip the tarball
	tar -zxvf rtl8185_linux_26\[1\].1027.0823.2007.tar.gz
(3) compile the drivers
	apt-get install build-essential
	cd rtl8185_linux_26.1027.0823.2007/
	cat readme
```

< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

        (1)Build up the driver from the source code
                ./makedrv

        (2)Load the driver module to kernel and start up nic
                ./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
                ./wlan0rmv
                ./wlan0down
                ./wlan0up
            should be OK.
           )
        (3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.

```

...so i...
./makedrv
...everything seems to go okay until the end is says...
```

make[2]: *** [/root/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/root/rtl8185_linux_26.1027.0823.2007/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```
...and ./wlan0up does not work...


**2nd attempt (ndiswrapper)**
i follow this how to: [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)
apt-get install ndiswrapper-common ndiswrapper-utils-1.9
depmod -a
modprobe ndiswrapper
echo 'ndiswrapper' | tee -a /etc/modules
ndiswrapper -m 
echo 'blacklist rtl8180' | tee -a /etc/modprobe.d/blacklist

download xp driver: [http://www.wireless-driver.com/download/realtek/Realtek-RTL8185L-Wireless-LAN-Mini-PCI-Driver.htm](http://www.wireless-driver.com/download/realtek/Realtek-RTL8185L-Wireless-LAN-Mini-PCI-Driver.htm)

(i tried both .inf files in these packages)
wget [http://aliendl.alienware.com/Mobile/m9700/m9700_WIFI_RTL8185_ABG_MINIPCI__5.1060.0413.zip](http://aliendl.alienware.com/Mobile/m9700/m9700_WIFI_RTL8185_ABG_MINIPCI__5.1060.0413.zip)
or
wget [ftp://210.51.181.211/cn/wlan/rtlwlan-8185(1094).zip](ftp://210.51.181.211/cn/wlan/rtlwlan-8185(1094).zip)


unzip rtlwlan-8185(1094).zip
cd WINXP
ndiswrapper -i net8185.inf 
 ndiswrapper -l
```

net8185 : driver installed
	device (10EC:8185) present (alternate driver: rtl8180)

```
nano /etc/network/interfaces
i add:
```

auto wlan0
iface wlan0 inet dhcp 

```
then reboot
...after reboot i try to iwconfig but no wireless extensions
...and ifconfig only shows my lo and eth0

help!

---

### Post by scurry7 on 2008-12-19
okay so I tried ndiswrapper with the 64 bit driver version and it seemed to work.  I now have a wlan0 and all that stuff, but it freezes all the time.

If i start the computer with the wireless enabled (from bios) it hands when it is loading the wireless driver.  

So what can I do? anything?
buy a new card...

can you purchase new internal wireless controllers (its a internal pci for laptops... minipci?)

---

### Post by khowe on 2008-12-31
[http://rtl-wifi.sourceforge.net/wiki/Main_Page]("http://rtl-wifi.sourceforge.net/wiki/Main_Page")

I think this is the latest code for rtl818x

I just ordered some pci cards, hope they work.

---

### Post by transform100 on 2009-01-05
I was able to get the RTL8185 working with these drivers under ndiswrapper make sure to install ndiswrapper through Ubuntu's package manager or apt-get then install them under System > Administration > Windows Wireless Drivers. For some reason I was unable to get these drivers to work on anything other then Ubuntu I have tried Fedora, Opensuse and many others. Drivers: [http://www.filedropper.com/wifidrivers-mx3231tar](http://www.filedropper.com/wifidrivers-mx3231tar)

---

