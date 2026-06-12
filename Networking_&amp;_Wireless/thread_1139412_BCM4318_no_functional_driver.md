---
title: "BCM4318 no functional driver"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by mjitkop on 2009-04-27
Hi all,

I've been trying since I did a fresh install of Jaunty on Thursday to get my wireless internet to work.

I have a dual boot with XP so if I need to download something, I can do it on my XP account.

I have tried a few things to no avail so far. The first thing I tried was to use **ndisgtk** as explained on [https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html) but when I selected the INF file of my Windows driver, it showed that the driver was incorrect. :confused:

Then I found instructions to use b43-fwcutter and followed instructions but still nothing. I noticed that I now have a directory in /lib/firmware called b43 that was not readable unless you tried as root. I managed to do a chmod to allow the directory to be read but that didn't make a difference after I restarted the computer.

After doing this, I added "blacklist bcm43xx" at the end of /etc/modprobe.d/blacklist.conf but still nothing. I have removed this line now.

I would be very grateful if somebody could take some of their time to help me get this working. This is a tough one and I feel that I have spent enough time to try to fix this problem on my own.

Here is technical information about my wireless card:

```
:~$ sudo lshw -C network

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: <hidden on purpose>
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

``````
:~$ iwconfig

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```My ESSID is not "linksys". I use WEP encryption.

Thank you in advance for your help.

---

### Post by jondecker76 on 2009-04-28
I am also having problems with a bcm4318 wireless chipset in Jaunty. In fact, lsmod shows no such driver loaded. Furthermore, running modprobe bcm43xx gives and error:
FATAL: Module bcm43xx not found.

Anybody have any suggestions?

---

### Post by jondecker76 on 2009-04-28
a little more research..
It seems that the old bcm43xx module has been replaced with the b43 module. This module IS loaded. However, clinking on the network icon on the taskbar shows no wireless networks, despite having several in my home.

---

### Post by jondecker76 on 2009-04-28
Ok, I finally got mine working.

I went to System->Administration->Hardware Drivers and was surprised to see a B43 driver listed. After enabling it and rebooting, my wireless is now working.

This would have been much smoother if Ubuntu would have alerted me that there were new restricted drivers available like it normally does.

---

### Post by mjitkop on 2009-04-29
You're lucky, jondecker76. After reading your message, I booted to Ubuntu again and checked  System->Administration->Hardware Drivers and I do have a b43 driver listed too. Not only is it listed but it is already enabled! However I still don't have an internet connection!

It's strange because the very first thing I did after installing Jaunty was to check the drivers and b43 was not listed at that time! 
I did a lot of things to try to get it working and I am wondering if there conflicts now between ndiswrapper and b43-fwcutter.

Do you remember what you did before you checked the drivers? Did you install ndiswrapper? Did you use b43-fwcutter?

Thank you in advance for your help if you have time. 

Enjoy Jaunty! :)

---

### Post by Ayuthia on 2009-04-29
> **mjitkop said:**
> You're lucky, jondecker76. After reading your message, I booted to Ubuntu again and checked  System->Administration->Hardware Drivers and I do have a b43 driver listed too. Not only is it listed but it is already enabled! However I still don't have an internet connection!

It's strange because the very first thing I did after installing Jaunty was to check the drivers and b43 was not listed at that time! 
I did a lot of things to try to get it working and I am wondering if there conflicts now between ndiswrapper and b43-fwcutter.

Do you remember what you did before you checked the drivers? Did you install ndiswrapper? Did you use b43-fwcutter?

Thank you in advance for your help if you have time. 

Enjoy Jaunty! :)

You don't need ndiswrapper if you are going to use the b43 module.  Can you provide the information for the following (from the Terminal):
```
ndiswrapper -l
ls /lib/firmware/b43
```
The first command is going to check and see if ndiswrapper is using a Windows driver (we will need to back it out if one exists) and the second one is to check and see if the needed firmware is installed or not.

---

### Post by mjitkop on 2009-04-29
Hello, Ayuthia.

Here is what you requested:

```
:~$ ndiswrapper -l
netg54s : invalid driver!
```

```
:~$ ls /lib/firmware/b43
a0g0bsinitvals4.fw   a0g1bsinitvals5.fw   b0g0bsinitvals5.fw  lp0bsinitvals14.fw  n0initvals11.fw  ucode4.fw
a0g0bsinitvals5.fw   a0g1bsinitvals9.fw   b0g0bsinitvals9.fw  lp0bsinitvals15.fw  pcm4.fw          ucode5.fw
a0g0bsinitvals9.fw   a0g1initvals13.fw    b0g0initvals13.fw   lp0initvals13.fw    pcm5.fw          ucode9.fw
a0g0initvals4.fw     a0g1initvals5.fw     b0g0initvals4.fw    lp0initvals14.fw    ucode11.fw
a0g0initvals5.fw     a0g1initvals9.fw     b0g0initvals5.fw    lp0initvals15.fw    ucode13.fw
a0g0initvals9.fw     b0g0bsinitvals13.fw  b0g0initvals9.fw    n0absinitvals11.fw  ucode14.fw
a0g1bsinitvals13.fw  b0g0bsinitvals4.fw   lp0bsinitvals13.fw  n0bsinitvals11.fw   ucode15.fw
```

Thanks for your help!

---

### Post by mjitkop on 2009-04-30
Are you there, Ayuthia? :biggrin:

---

### Post by Ayuthia on 2009-04-30
> **mjitkop said:**
> Hello, Ayuthia.

Here is what you requested:

```
:~$ ndiswrapper -l
netg54s : invalid driver!
```

```
:~$ ls /lib/firmware/b43
a0g0bsinitvals4.fw   a0g1bsinitvals5.fw   b0g0bsinitvals5.fw  lp0bsinitvals14.fw  n0initvals11.fw  ucode4.fw
a0g0bsinitvals5.fw   a0g1bsinitvals9.fw   b0g0bsinitvals9.fw  lp0bsinitvals15.fw  pcm4.fw          ucode5.fw
a0g0bsinitvals9.fw   a0g1initvals13.fw    b0g0initvals13.fw   lp0initvals13.fw    pcm5.fw          ucode9.fw
a0g0initvals4.fw     a0g1initvals5.fw     b0g0initvals4.fw    lp0initvals14.fw    ucode11.fw
a0g0initvals5.fw     a0g1initvals9.fw     b0g0initvals5.fw    lp0initvals15.fw    ucode13.fw
a0g0initvals9.fw     b0g0bsinitvals13.fw  b0g0initvals9.fw    n0absinitvals11.fw  ucode14.fw
a0g1bsinitvals13.fw  b0g0bsinitvals4.fw   lp0bsinitvals13.fw  n0bsinitvals11.fw   ucode15.fw
```

Thanks for your help!

You can try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
If it does not produce any wireless sites, please post the results of:
```
dmesg|grep b43
```

---

### Post by mjitkop on 2009-04-30
Thank you. I will try tonight when I get home. :)

---

### Post by gary987 on 2009-04-30
> **Ayuthia said:**
> You can try the following:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```If it does not produce any wireless sites, please post the results of:
```
dmesg|grep b43
```


I had the same issue trying the live CD.

It seems that the b43 driver is autoloaded on boot, even though it has not been requested.

When you go and 'install' the b43 driver, it downloads the firmware, then trys to load the module.

All I did to get it to work was after 'installing'  (downloading the firmware) was

```
sudo rmmod b43
sudo modprobe b43

```Cheers,

Gary

---

### Post by mjitkop on 2009-04-30
Wow, do I feel stupid! I am now posting this message from Ubuntu!

All this time when I looked at the icon by the clock that indicates if you are connected, there was a red cross on it to let me know I was not connected. When I placed the mouse on the icon, it did not show me any networks around so I thought the driver didn't work (I think in Windows it shows you the wireless connections if you just place the mouse on the icon without clicking on it). Less than 5 minutes ago I "accidentally" did a left click on the icon and I saw all the wireless connections available in my neighborhood! :redface: :lolflag:
So I don't know exactly at what moment the b43 driver appeared in the Hardware Drivers but it has been several days, I think.

I guess I can change the status of this thread to [SOLVED] even though I really don't know if I did anything to fix the problem. It seems to just work. :lolflag:

Thank you all for spending the time to reply and try to help me.

Happy Ubuntu to all! :guitar:

---

### Post by rodrigr2006 on 2009-09-19
i've had the same problems, i have been working on my problem for about 3 weeks now and im to my wits end.  i have tried what is on this thread and tried others. i have tired with b43, without b43 (ndskg) and nothing works.  im using the same card bcm4318 in an old hp omnibook xe3 runing the new ubuntu 9
 
any sugestions?

---

### Post by Herukam on 2009-10-22
> **rodrigr2006 said:**
> i've had the same problems, i have been working on my problem for about 3 weeks now and im to my wits end.  i have tried what is on this thread and tried others. i have tired with b43, without b43 (ndskg) and nothing works.  im using the same card bcm4318 in an old hp omnibook xe3 runing the new ubuntu 9
 
any sugestions?

This worked for me [http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm4318)

---

### Post by kevdog on 2009-10-22
If this thread isnt an example of thread necromancy -- I don't know what is?

---

