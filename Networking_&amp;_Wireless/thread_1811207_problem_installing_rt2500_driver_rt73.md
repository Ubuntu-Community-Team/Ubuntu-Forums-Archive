---
title: "problem installing rt2500 driver rt73"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by NNNu on 2011-07-24
hi!
I am new to Linux and I have ubuntu 11.04 installed via wubi.
My wireless connection works but it is really really slow (slower than DSL 1000 but I have 6000) despite iwconfig saying Bitrate=11M.
so i downloaded the Enhanced Legacy Driver from [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)
To install the readme says i have to execute "make" in the Module directory. If i do say i get the following error:

```
xxx@ubuntu:~/Desktop/rt73-cvs-2009041204/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
rt73.ko failed to build!
make: *** [module] Error 1
```What do I need to do?
Thanks

btw I have a PCI Wireless card

---

### Post by chili555 on 2011-07-24
Maybe there's a better way. Please post:```
lsmod | grep rt2
lspci -nn | grep 0280
```Thanks.

---

### Post by NNNu on 2011-07-24
```
xxx@ubuntu:~$ lsmod | grep rt2
rt2x00usb              19693  1 rt73usb
rt2500pci              18668  0 
rt2x00pci              13986  1 rt2500pci
rt2x00lib              39075  4 rt73usb,rt2x00usb,rt2500pci,rt2x00pci
mac80211              257001  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2500pci

```


```
xxx@ubuntu:~$ lspci -nn | grep 0280
01:0a.0 Network controller [0280]: Ralink corp. RT2500 802.11g [1814:0201] (rev 01)

```

---

### Post by chili555 on 2011-07-24
Do you have a PCI *[SIZE="2"]and[/SIZE]* a USB card? Do you just love causing old Chili nightmares on a hot Sunday? What makes you think rt73 is correct for this device? It may be, I just don't understand.

---

### Post by NNNu on 2011-07-24
haha well I'm not sure about rt73 I just need a working rt2500 driver =)
I have only PCI, no USB!
And since the rt2x00 is used by default and its as slow as a snail I need different drivers.
The rt73 seems to be the official Ralink driver.

---

### Post by chili555 on 2011-07-24
Don't you think it's a bit dangerous to go download a file and compile it when you're not sure if it's right? How did these things get loaded?> $ lsmod | grep rt2
rt2x00[COLOR="Red"]usb[/COLOR]              19693  1 rt73[COLOR="Red"]usb[/COLOR]
rt2500pci              18668  0 
rt2x00pci              13986  1 rt2500pci
rt2x00lib              39075  4 rt73usb,rt2x00usb,rt2500pci,rt2x00pci
mac80211              257001  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2500pciAgain, do you also have a USB wireless card?

---

### Post by NNNu on 2011-07-24
no i have only PCI
Who knows why, but lsmod | grep rt2 gives the follow output now:
```
xxx@ubuntu:~$ lsmod | grep rt2
rt2500pci              18668  0 
rt2x00pci              13986  1 rt2500pci
rt2x00lib              39075  2 rt2500pci,rt2x00pci
mac80211              257001  2 rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2500pci

```

hm :confused:

---

### Post by chili555 on 2011-07-24
Hmm, indeed.

You might try compat wireless: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

Download it to your desktop, right-click to extract it and then in a terminal:```
cd Desktop/compat
```Press Tab to let the remainder of the file name fill in, press Enter.```
./scripts/driver-select rt2x00
make
sudo make install
```Reboot and tell us how it works.

---

### Post by NNNu on 2011-07-30
compat changed nothing, still slow internet =(

---

### Post by chili555 on 2011-07-30
May I please see:```
modinfo rt2500pci
```Thanks.

---

### Post by NNNu on 2011-07-30
```
xxx@ubuntu:~$ modinfo rt2500pci
filename:       /lib/modules/2.6.38-8-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     674352EBF9BCBCEF41DC358
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 

```

thanks chili for your help =)

---

### Post by chili555 on 2011-07-30
This is my least favorite kind of reply. When you have the latest driver correctly installed, there are very few options left. I am very low on useful ideas. Please let us see:```
iwconfig
```

---

### Post by NNNu on 2011-07-30
```
xxx@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:12:17:D4:7E:0B   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:80961   Missed beacon:0
```

---

### Post by SeijiSensei on 2011-07-30
I reverted back to 10.10 when I encountered problems with my rt2500-based USB adapter after an upgrade to 11.04.  Rock solid with 2.6.35-28 and, now, 2.6.35-30; unreliable performance with the 2.6.38 kernel in 11.04.

Support for the rt2500 chipset has been extremely variable across Ubuntu releases. I've had to pick and choose carefully to get the device working at full speed and maintain its connection over time.

---

### Post by chili555 on 2011-07-30
> wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:12:17:D4:7E:0B   
          [COLOR="Red"]Bit Rate=11 Mb/s[/COLOR]   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  Does it help to try to kick it up?```
sudo iwconfig wlan0 rate 54M
```It may not stick because of the link quality.> Support for the rt2500 chipset has been extremely variable across Ubuntu releases."Extremely variable" is a nice way to put it. Some might say poor.

---

### Post by keychange on 2011-08-04
> **SeijiSensei said:**
> Support for the rt2500 chipset has been extremely variable across Ubuntu releases. 

I have almost no connectivity and have lost days stuffing around on this - this is my first try on Ubuntu and the RT2500pci  works perfectly on Fedora and Win XP but hopeless here.  I was looking forward to playing with Studio but I guess not :(:guitar:

---

