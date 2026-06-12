---
title: "RTL8187 wireless driver"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by nash black on 2010-05-07
Hi

I've been having problems with my USB wireless card (no cable hookup on my side of the duplex :icon_frown: )

Its a Rosewill RNX-G1 IEEE 802.11b/g wireless USB adapter

The windows driver included is for an RTL8187. I've seen some new drivers around for similar models, but not this one. It seems like they all need some work to perform properly in ubuntu.

The connection works a bit better since my upgrade to ubu 10.04, but it is still quite unrelaiable compared to its performace in XP with the windows driver.

And ideas about how to find a better driver or improve performance?

---

### Post by cariboo on 2010-05-08
A bump for the move.

---

### Post by nash black on 2010-05-09
After doing some more research, this seems to be a relatively common problem. People with older versions of Ubuntu seem to have identified this as a connection strength issue and had some luck installing wireless backport packages, but the lucid package (below) didn't do anything for me.

sudo apt-get update && sudo apt-get install linux-backports-modules-wireless-lucid-generic

The connection works sometimes, but 75% of the time it will only be able to load anything from the web for the first few seconds after connecting. After this, it says that it is connected but does not seem to be receiving data. It works in the XP partition perfectly, so this is a driver issue as far as I can tell.

My laptop, which also runs lucid connects with no issues and good strength in the same room (frequently at the same time that the desktop w/ the USB wireless cannot... like now...) So the issue is definitely not just the signal.

This has been particularly frustrating because I have been trying to fix it for a month now and it is really the only thing that is still preventing me from using lucid as my primary OS. If someone could explain what might be going on or offer a possible solution, that would be HUGE.

Thanks
Nash

---

### Post by Crio on 2010-05-10
See if it helps [http://ubuntuforums.org/showthread.php?p=9272125#post9272125](http://ubuntuforums.org/showthread.php?p=9272125#post9272125)
There are different modifications of rtl8187 - b, l, se. Use lsusb to find out which you have.

---

### Post by nash black on 2010-05-10
---
*******@Computus:~$  lsusb|grep -i realtek
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
---

There is no letter after the 8187 for mine. There is no such driver on realtek's site, but I do have the windows 8187 driver installation disk. Do you think this would work?

---

### Post by chili555 on 2010-05-10
> **nash black said:**
> ---
*******@Computus:~$  lsusb|grep -i realtek
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
---

There is no letter after the 8187 for mine. There is no such driver on realtek's site, but I do have the windows 8187 driver installation disk. Do you think this would work?What does this tell us?```
sudo modprobe rtl8187
sudo iwconfig wlan0 txpower 20
sudo iwlist wlan0 scan
```Thanks.

---

### Post by nash black on 2010-05-10
Here are the results. I should note that the connection is currently working... 



*******@Computus:~$ sudo modprobe rtl8187
[sudo] password for *******: 
*******@Computus:~$ sudo iwconfig wlan0 txpower 20
*******@Computus:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:26:51:32
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Palace"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000245589c183
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 000650616C616365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


Also, I found the driver files on the installation CD if Ndiswrapper becomes necessary...

---

### Post by chili555 on 2010-05-10
Looks like it's working well! Can you click the Network Manager icon and see your network and connect?

---

### Post by nash black on 2010-05-10
Yeah, the network shows up and everything. It is actually working perfectly right now.

This is the funny thing though... it works perfectly sometimes and other times I can see the connection and it says that it is connected, but does not load web pages or updates. I'll run those commands next time its acting funny... It usually doesn't work well for more than a day.

---

### Post by nash black on 2010-05-16
Alright, it was on a roll for a while there, but its been acting up again for the last two days... One bar, but no apparent data transfer after the first few seconds. Again, it works fine in windows and on my laptop. Now when I run those three commands in terminal it returns the following message:

wlan0     Interface doesn't support scanning: Device or resource busy

I think that I'm going to try Ndiswrapper with the driver files from the windows installation disk. The USB drive isn't listed as having worked with Ndiswrapper, but its worth a shot for reliable internet

---

### Post by nash black on 2010-05-16
Ahh no luck

I installed ndiswrapper, as instructed in the Ubuntu manual and used it to install  the .inf file from the driver CD (risky I know, but I'M DESPERATE)

After installing the .inf file, the connection reset, but behaved just as it has before. Because of this, I did not continue to follow the instructions and just removed the driver and uninstalled ndiswrapper.

I am open to reinstalling it if anyone thinks that they could get it to work with some fiddling, but for now I'm back to square one.

Just an observation: The driver seems to misbehave at low signal strength. When I have a strong signal I have no issues, but when the signal gets a bit low, this driver seems to fail while the Ubuntu driver on my other computer is fine, as is the windows driver in the windows partition of my desktop(the computer with the misbehaving Linux driver). The misbehaving driver seems to be underreporting signal strength and failing to work in the absence of a very strong signal...If someone knows why this might be the case, it could be the key to figuring this thing out...

---

### Post by Callius on 2010-05-26
I'm having this exact same issue.

It seems that the RTL8187 linux driver doesn't play nicely.

---

### Post by madbyte on 2010-06-26
Same issue here the web navigation is ok only if the signal is strong. If not the connection is intermitent and some times is impossible to load a page. The driver doesn't work like it does on XP or Seven. Its very annoying and frustrating.

---

### Post by xMatterx on 2010-07-10
yes, I wish this bug would be fixed soon ):

---

### Post by 3rdalbum on 2010-07-10
My rtl8187 works fine, but you should try turning down the speed of the link. I am not on my computer, but I think it's:

sudo iwconfig wlan0 rate 5.5M

See 'man iwconfig' for more details.

---

