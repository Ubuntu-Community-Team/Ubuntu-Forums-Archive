---
title: "How do I go about installing the b43 drivers?"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by xxarthur33xx on 2011-06-11
Well first of all, I have tried EVERYTHING that I have read and cant get it to work. I had it perfect up until this morning, I was screwing around with stuff and managed to completely remove my wireless and nvidia drivers. atm I have ndiswrapper, but there is no monitor support so I would rather have b43 drivers. I've installed b43-fwcutter, and even did the offline install with the 2 files but it still doesn't show up in my additional drivers. Only my nvidia does, but that one still isn't like it was either.

Not too sure if these will help or not.
```
01:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

tldr; I deleted some stuff I shouldn't have and all my nvidia drivers and wireless drivers are jacked.

EDIT: I should also add that with ndiswrapper, I have no wifi reception at all. Everything is at 1 bar where they were around full bars last night/this morning.

---

### Post by superduperlinuxperson on 2011-06-12
congrats!!! your card is supported with b43xx
here is how i did it:
link: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access")
If you do not have any other means of Internet access on your computer, you will have to install b43-fwcutter and patch  packages from the install media. After that you will need to setup  firmware manually (without the firmware automatically downloading and  being set up). 
**Setp 1.** 
b43-fwcutter is located on the Ubuntu install media under **../pool/main/b/b43-fwcutter/** and patch is located under **../pool/main/p/patch/** **or** both in the official repositories online.  
Double click on the package to install **or** in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) navigate to the folder containing the package and issue the following command:  

:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter***Step 2.** 
On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
**Step 3.**  
Copy  the downloaded files to your home folder and execute the following  commands consecutively in a terminal to extract and install the  firmware: 

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
if you do have internet access, do this anyway, as it is the most robust way of doing it

---

