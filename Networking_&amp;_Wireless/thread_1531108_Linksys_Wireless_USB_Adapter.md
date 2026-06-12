---
title: "Linksys Wireless USB Adapter"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by c_raethke on 2010-07-14
Hi there.. I recently installed ubuntu on one of my computers to try it out, but this computer is in a place where I can't plug it directly into the router, so I plugged in my Linksys WUSB54GC ver. 3 adapter, but ubuntu won't recognize it. Here are the things I've tried:

1. Using ndiswrapper to install the drivers from the CD, and then ones I downloaded for the chipset

2. Adding 3 drivers I found to the blacklist file

I probably didn't do either one right, I have no experience with Linux at all, and was just going from tutorials I found on this website. I will also post some data I got from the console..

lsusb
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 002: ID 0461:4d42 Primax Electronics, Ltd 

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 004: ID 0930:6540 Toshiba Corp. TransMemory Flash Memory

Bus 001 Device 003: ID 1737:0077 Linksys 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Please help me get this working; I can't get the true ubuntu experience without internet xD Let me know if you need more information.

---

### Post by chili555 on 2010-07-14
This device is supposed to work with rt2870sta and is also claimed by rt2800usb. Let's start by seeing where we are now; that is, what has been done and what may need to be tweaked. Here are some commands to run in the terminal. With the results, we can figure out what to do or redo to get you running. Please post:```
lsmod | grep -e rt2 -e ndis
dmesg | grep -e rt2 -e ndis
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```In the blacklist files, I am interested in the last few lines that you added.

Thanks.

---

### Post by c_raethke on 2010-07-14
Alright, here are the results:

```
cody@ubuntu:~$ lsmod | grep -e rt2 -e ndis

rt2870sta             461811  1
 

cody@ubuntu:~$ dmesg | grep -e rt2 -e ndis

[   12.578977] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.

[   12.811235] usbcore: registered new interface driver rt2870

[   13.414107] Error: Driver 'rt2870' is already registered, aborting...

[   13.414164] usbcore: error -16 registering interface     driver rt2870


cody@ubuntu:~$ cat /etc/modprobe.d/blacklist

cat: /etc/modprobe.d/blacklist: No such file or directory


cody@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf

# This file lists those modules which we don't want to be loaded by

# alias expansion, usually so some other driver will be loaded for the

# device instead.


# evbug is a debug tool that should be loaded explicitly

blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse

blacklist usbkbd


# replaced by e100

blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces

blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much

# hardware on its own (Ubuntu bug #2011, #6810)

blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)

blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)

blacklist i2c_i801


# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.

blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)

blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)

blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes

# hangs at desktop session start (Ubuntu: #246969)

blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a

# nice pulseaudio bing (Ubuntu: #77010)

blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture

# from being initialised (Ubuntu: #297750). Blacklist so that the driver

# continues to build and is installable for the few cases where its

# really needed.

blacklist amd76x_edac


blacklist rt2x00usb

blacklist rt2x00lib

blacklist rt2800usb

```I had to post in Windows.. tried to get all the line breaks right, but might have missed some.

---

### Post by chili555 on 2010-07-14
It looks pretty good, actually. It appears that ndiswrapper is attempting and failing to load and the native driver, rt2870sta loads. Let's see if a wireless interface is created:```
iwconfig
sudo iwlist wlan0 scan
```We are making progress!

---

### Post by c_raethke on 2010-07-14
Ok, results:
```
cody@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"linksys"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:23:69:B7:EC:11   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=95/100  Signal level:-69 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cody@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:B7:EC:11
                    Protocol:802.11b/g
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:6
                    Quality:47/100  Signal level:-71 dBm  Noise level:-97 dBm
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


```

---

### Post by chili555 on 2010-07-14
It looks like you are connected! Can you open Firefox and surf the internet?

---

### Post by c_raethke on 2010-07-14
Nope.. I noticed that the results seemed to say I was connected, but I opened Firefox, and it was in work offline mode, so I turned that off, refreshed, and it said it couldn't connect.. I also tried about 5 other websites just to make sure, and checked like email and other programs, network.. nothing worked. Soo.. any ideas now? xD

---

### Post by chili555 on 2010-07-14
From the terminal:```
cat /etc/resolv.conf
ifconfig wlan0
ping -c3 74.125.65.99
```Thanks.

---

### Post by c_raethke on 2010-07-14
```
cody@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory
cody@ubuntu:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:23:69:6f:f4:1d  
          inet6 addr: fe80::223:69ff:fe6f:f41d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76818 (76.8 KB)  TX bytes:11960 (11.9 KB)

cody@ubuntu:~$ ping -c3 74.125.65.99
connect: Network is unreachable
cody@ubuntu:~$ 
```I should also probably mention this: when I tried to install the drivers I downloaded with ndiswrapper, I had to edit some files that came with the driver, including one where I entered my SSID, passkey, and some encryption information for my network.. 

Also, when I start up the computer, it asks me for the password for the network, and then about every 30 seconds after until I hit cancel. I'm not sure if it can "see" the network or not, but could it be a problem with the encryption info I gave it? I wasn't sure about one of the things, so I just put the same one as the tutorial had.

---

### Post by baguahsing on 2010-07-14
In firefox, options - advanced -  network, are you set up properly?

---

### Post by c_raethke on 2010-07-14
I didn't change anything.. what would "properly" be?

---

### Post by chili555 on 2010-07-14
> could it be a problem with the encryption info I gave it? I wasn't sure about one of the things, so I just put the same one as the tutorial had. The encryption should be the exact same as listed in your router. It look like your router is set up for the messy mixed WPA and WPA2 mode. Ubuntu will connect most efficiently with one or the other, not mixed.> Scan completed :
          Cell 01 - Address: 00:23:69:B7:EC:11
                    Protocol:802.11b/g
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:6
                    Quality:47/100  Signal level:-71 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    [COLOR="Red"]IE: WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    [COLOR="Red"]IE: IEEE 802.11i/WPA**2** Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKI suggest you log on to the setup pages of the router and change to WPA2 only. Also, take note of the password and then reboot Ubuntu and input the exact correct password.

I'll bet you connect.

---

### Post by c_raethke on 2010-07-14
My router is set up for WPA2 Personal.. there isn't an option for mixed on the router. But, in ubuntu, when I tried to connect to a "hidden network" (the network didn't show up on its own, is it supposed to?) I had to tell it I needed a password, and one of the options was "WPA/WPA2 Personal". The other one was "WPA Enterprise" or something like that. I put in the correct SSID and password, I rechecked it multiple times. 

The reason I was wondering about the encryption, is there was another option in the file that I edited.. I'm not even sure if that driver is being used, or if those files are used, or where it is now, since I didn't really understand most of the tutorial. 
These were the instructions:
> gedit RT2870STA.dat


and insert your SSID, Channel, AUTHMODE, EncrypType and WPAPSK


save and close


For info : 
- I only entered my SSID; selected WPA2PSK for 4.) ;TKIP for 5.) and left the rest alone


- 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infra (ie infrastructure)

- 2.) set Channel to "0" for auto-select on Infra mode

- 3.) set SSID for connecting to your Accss-point 

- 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"

- 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

I put WPA2PSK for the AuthMode, and TKIP as the EncrypType, as the person who wrote it did.. I'm not sure if I should have put a different EncrypType, or changed any of the many other options in the file.

By the way, thanks for all your help, and the fast replies.. :)

---

### Post by chili555 on 2010-07-14
This is the driver being used. It is unclear if the native driver uses the .dat file. Did you also enter the password?> WPAPSK=yourpasswordAll your other entries look fine.

I regret the quick replies must await a night of sleep. I will check in tomorrow.

---

### Post by c_raethke on 2010-07-14
I am pretty sure I put the password in, but I don't remember the WPAPSK variable.. I'll check and let you know tomorrow (I need sleep also).

EDIT: Yep, I had the password in there. Just so you have a better idea of what it looks like right now:
When I logon the computer, it tries to automatically connect to the network, because I gave it the name and password in the NetworkManager thing. It appears to be "available", and even looks like it has 4/5 bars of signal. But, it just sits there spinning for about 30 seconds, then shows "disconnected from network" and shows the ! mark in the notification icon. So it seems like it's able to use the USB device, and find the network (or maybe it's just pretending to be able to, I'm not sure), but is unable to connect. Would it be a good idea to just reinstall ubuntu, and start from scratch? It might be easier to get past something I did wrong that I shouldn't have done that way.

EDIT2: YES, I changed the security on my router from WPA2 to None (I don't need security, I'm the only one within a half mile radius of my router anyways) and it was able to find and connect to my network on the first try. Thank you so much for all your help and dedication. 
Proudly posted from ubuntu using my wireless adapter :D

---

### Post by rmamrick on 2010-07-29
I am also having trouble with the Linksys AE1000 network adapter card.  I have followed your thread trying to learn.  For my system, the answers to your questions are listed below.  Can you please help.  I have tried multiple thread solutions without success.  Thank you in advance.

  	 	 	 	 	 	  rick@rick-desktop:~$ lsmod | grep -e rt2 - ndis 
 (standard input):rt2870sta             461971  0  
 grep: ndis: No such file or directory 
 

 

 rick@rick-desktop:~$ dmesg | grep -e rt2 -e ndis 
 [   14.419527] ndiswrapper version 1.55 loaded (smp=yes, preempt=no) 
 [   14.422340] usbcore: registered new interface driver ndiswrapper 
 [   15.210133] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned. 
 [   15.223610] usbcore: registered new interface driver rt2870 
 [   15.280251] Error: Driver 'rt2870' is already registered, aborting... 
 [   15.280288] usbcore: error -16 registering interface 	driver rt2870 
 

 

 rick@rick-desktop:~$ cat /etc/modprobe.d/blacklist 
 blacklist bcm43xx 
 blacklist b43 
 blacklist b43legacy 
 blacklist ssb 
 blacklist bcm43xx 
 blacklist b43 
 blacklist b43legacy 
 blacklist ssb 
 blacklist bcm43xx 
 blacklist b43 
 blacklist b43legacy 
 blacklist ssb 
 

 

 rick@rick-desktop:~$ cat /etc/modprobe.d/blacklist.conf 
 # This file lists those modules which we don't want to be loaded by 
 # alias expansion, usually so some other driver will be loaded for the 
 # device instead. 
  
 # evbug is a debug tool that should be loaded explicitly 
 blacklist evbug 
  
 # these drivers are very simple, the HID drivers are usually preferred 
 blacklist usbmouse 
 blacklist usbkbd 
  
 # replaced by e100 
 blacklist eepro100 
  
 # replaced by tulip 
 blacklist de4x5 
  
 # causes no end of confusion by creating unexpected network interfaces 
 blacklist eth1394 
  
 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much 
 # hardware on its own (Ubuntu bug #2011, #6810) 
 blacklist snd_intel8x0m 
  
 # Conflicts with dvb driver (which is better for handling this device) 
 blacklist snd_aw2 
  
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306) 
 blacklist i2c_i801 
  
 # replaced by p54pci 
 blacklist prism54 
  
 # replaced by b43 and ssb. 
 blacklist bcm43xx 
  
 # most apps now use garmin usb driver directly (Ubuntu: #114565) 
 blacklist garmin_gps 
  
 # replaced by asus-laptop (Ubuntu: #184721) 
 blacklist asus_acpi 
  
 # low-quality, just noise when being used for sound playback, causes 
 # hangs at desktop session start (Ubuntu: #246969) 
 blacklist snd_pcsp 
  
 # ugly and loud noise, getting on everyone's nerves; this should be done by a 
 # nice pulseaudio bing (Ubuntu: #77010) 
 blacklist pcspkr 
  
 # EDAC driver for amd76x clashes with the agp driver preventing the aperture 
 # from being initialised (Ubuntu: #297750). Blacklist so that the driver 
 # continues to build and is installable for the few cases where its 
 # really needed. 
 blacklist amd76x_edac 
 blacklist bcm43xx.conf 
 blacklist b43.conf 
 blacklist b43legacy.conf 
 blacklist ssb.conf 
 blacklist bcm43xx.conf 
 blacklist b43.conf 
 blacklist b43legacy.conf 
 blacklist ssb.conf 
 

 

 rick@rick-desktop:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 rick@rick-desktop:~$ sudo iwlist wlan0 scan 
 [sudo] password for rick:  
 wlan0     Interface doesn't support scanning. 
 

 

 rick@rick-desktop:~$ cat /etc/resolv.conf 
 # Generated by NetworkManager 
 nameserver 24.178.162.3 
 nameserver 97.81.22.195 
 nameserver 24.217.0.5 
 

 

 rick@rick-desktop:~$ ifconfig wlan0 
 wlan0: error fetching interface information: Device not found 
 

 

 rick@rick-desktop:~$ ping -c3 74.125.65.99 
 connect: Network is unreachable

---

