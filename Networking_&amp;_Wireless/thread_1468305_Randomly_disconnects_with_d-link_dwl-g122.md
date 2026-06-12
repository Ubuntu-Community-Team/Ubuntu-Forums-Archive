---
title: "Randomly disconnects with d-link dwl-g122"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Warliy on 2010-05-01
Since the upgrade to Ubuntu 10.04 the wireless network became very unstable.
Every time I'm using the wireless network I get randomly disconnected. Just like that. It was the same on the beta & rc and its also so on Archlinux etc.

But everything works 100% fine with ubuntu 9.10 or lower and I've tried to use wicd but its superduperslow and I've tried some guides but I cant get it to work.
However I don't get disconnected if I don't do anything with network, like watching an movie or stuffs like that. 

I'm using D-link Dwl-g122 usb

---

### Post by Xmat on 2010-05-02
I've got the same problem in Ubuntu 10.04 LTS. Internet is very slow, and sometimes the wireless is disconnected randomly.

*Update: upgrading the linux kernel (by enabling the recommended updates in the repositories) solved the problem*

---

### Post by Warliy on 2010-05-02
> **Xmat said:**
> 
*Update: upgrading the linux kernel (by enabling the recommended updates in the repositories) solved the problem*

Unfortunately that did not work for me. Anyone knows what the problem is?

---

### Post by Xmat on 2010-05-02
> **Warliy said:**
> Unfortunately that did not work for me. Anyone knows what the problem is?

well... actually it didn't work for me either. After 10-15 minutes I've got a very slow connection again.

I suppose the problem is in the driver, because it used to work before the upgrade (with ubuntu 9.10)

---

### Post by Warliy on 2010-05-02
Anyone? Im going to downgrade to Ubuntu 9.10 soon cuz of this.

---

### Post by s_snop on 2010-05-05
I Just downgraded back to 9.10. I couldnt get the DWL-122g connect in 10.04. the dlink revision is A2.

---

### Post by Warliy on 2010-05-05
> **s_snop said:**
> I Just downgraded back to 9.10. I couldnt get the DWL-122g connect in 10.04. the dlink revision is A2.

Yeah, i did that too now and everything works fine. My revision is b1.

---

### Post by robvas on 2010-05-09
Just came to post that I am having the same problem. If I leave my computer for a little while and come back, it asks me for my WPA2 password. I re-enter it, but it won't re-connect.

I just pull the USB adapter out and plug it back in, then it connects fine. Going to try the kernel update and see what that does.

---

### Post by firefly2442 on 2010-05-12
I have the exact same problem.  Running a DWL-G122 rev. B1.  I have the latest kernel and have updated all packages.  Zero problems with the previous 9.10 release.  I also did an upgrade.  Using the network connection applet, it shows the driver being rt2500usb.  However, on the Ndiswrapper page, it [states]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Disable%20Free%20Drivers") that DWL-G122 is fully supported and should be using the rt73usb driver module.

I tried the following.  I went into /etc/modprobe.d/blacklist.conf and edited this file and blacklisted rt2500usb.  I then restarted the computer.  Then I added the driver module with:

> sudo modprobe rt73usb

I checked to make sure it's loaded:

> lsmod | grep rt73usb

rt73usb
rt2x00usb - rt73usb
rt2x00lib rt73usb,rt2x00usb


I unplugged the USB wireless device and plugged it back in, nothing happens.  No lights come on for the device.  I check to see what is in USB:

> lsusb

The D-Link device shows up correctly.


At this point, I'm pretty stumped.  I'm not sure if this is an upgrade bug or a kernel issue.  Does anyone else have this issue who hasn't upgraded?

---

### Post by ReggieBE on 2010-05-13
I also have rev B1 and it's not possible for me to connect with WPA2. I can however connect to unsecured access points.

Also tried blacklisting the rt2500usb driver, but the rt73usb isn't really working for me.

---

### Post by clemmy on 2010-05-13
same problem here with a Logilink usb wi-fi card, using **rt73usb** module..
the connection is unstable, and sometimes it disconnect. Watching a video in streaming is impossible

```
$ lsusb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```

$ lsmod | grep rt
rt73usb                24256  0 
crc_itu_t               1715  1 rt73usb
rt2500usb              19643  0 
rt2x00usb              11260  2 rt73usb,rt2500usb
rt2x00lib              32133  3 rt73usb,rt2500usb,rt2x00usb
led_class               3732  1 rt2x00lib
mac80211              238128  2 rt2x00usb,rt2x00lib
cfg80211              148386  2 rt2x00lib,mac80211
parport                37160  2 ppdev,lp
```

---

### Post by firefly2442 on 2010-05-13
It's interesting to note in the "lsmod" that rt2x00usb is listed.  I did some simple searching and it looks like this is a generic module for interacting with USB devices.  Perhaps this also needs to be blacklisted?  Maybe someone who hasn't upgraded and has a working rt73usb driver module can post their "lsmod" so we can see what has been loaded.

---

### Post by clemmy on 2010-05-13
I've found something here [https://bugzilla.kernel.org/show_bug.cgi?id=13362](https://bugzilla.kernel.org/show_bug.cgi?id=13362)

I've just gave a quick look to that page, it seems interesting. Turning off the power management solved the problem for someone, but did not solved for others
```
sudo iwconfig wlan0 power off
```

Some one with a different driver from the same family (rtxxxx) also had some improvements after manually setting the tx-rate
```
sudo iwconfig wlan0 rate 54M fixed
```

I found also a old post on this forum where someone got a more stable connection setting the tx-rate to 11M ([http://ubuntuforums.org/showthread.php?p=7605785](http://ubuntuforums.org/showthread.php?p=7605785))


I'm  trying out in this moment the options tx-rate->11M and power-management->off...will post if it solve or not

---

### Post by hypernihl on 2010-05-13
Since upgrading from 9.10 to 10.04 I have this problem on my netbook (wifi) and my desktop (wired).

---

### Post by clemmy on 2010-05-13
after a quick test the problem seems almost gone with the two options
```
sudo iwconfig wlan0 power off
sudo iwconfig wlan0 rate 11M fixed
```
better testing tomorrow

now it should be interesting to find a easy way to automatically set those options. In the thread I've linked in my previous post there is a nice howto, but it doesn't work with Network Manager, WICD is required. I'd like to keep with Network Manager.

---

### Post by clemmy on 2010-05-15
In my laptop the problem is solved the the two options I've posted in my previous reply.

I've also found a way to set that options automatically, it's very easy :)
It uses NetworManagerDispatcher ([http://linux.die.net/man/1/networkmanagerdispatcher](http://linux.die.net/man/1/networkmanagerdispatcher))

[LIST=1]
[*]create and edit the file 99wifi-fix.sh in the NetworkManagerDispatcher dir: ```
$ sudo gedit /etc/NetworkManager/dispatcher.d/99wifi-fix.sh
```

[*]copy and paste the following code into that file **(replace wlan0 with the name of your interface.. if unsure check with iwconfig)**
```
#!/bin/bash

if [ $1 == "wlan0" ] && [ $2 == "up" ]; then
    iwconfig wlan0 power off
    iwconfig wlan0 rate 11M fixed
fi
```
[*]make the file 99wifi-fix.sh executable ```
sudo chmod +x /etc/NetworkManager/dispatcher.d/99wifi-fix.sh
```
[*]**done!**
[/LIST]

to check if it works..

[LIST=1]
[*]disconnect from the network
[*]connect again
[*]check the settings of your wireless card
```
$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"xxxxxxxxxxxxxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          **Bit Rate=11 Mb/s**   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:off**
          Link Quality=24/70  Signal level=-86 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
[/LIST]
:guitar:

---

### Post by mudie on 2010-05-24
Its not fixed for me!!!

I can make it work when I put those lines into the Terminal and reconnect but if a plug out the dwl-g122 when I plug in again I have to re-enter those lines it another time. And when I start the computer also... 

Ive done the shell script but nothing...

Thanks!!!

---

### Post by clemmy on 2010-05-30
oh, I forgot one more point in my small "howto"!!!! :oops:

The script should be made executable in order to work!
```
sudo chmod +x /etc/NetworkManager/dispatcher.d/99wifi-fix.sh
```

I will now update the howto in the previous post for the sake of completeness.

---

### Post by cincinnatus13 on 2010-06-04
Clemmy, thank you so much. I've been trying to figure out this wireless issue for a while on both of my Tosh Satellites. The power management turn off along with wicd helped me it seems.
I guess I'll post back if I have any problems. But for at least 10 mins. now I have had no disconnects and the speed is as good as can be.
Thanks again.

---

### Post by firefly2442 on 2010-06-09
Thanks for posting regarding this issue.  I've tried the script as you described and it seems to be working.  Hopefully, this bug can be fixed as it worked perfectly fine in previous kernel versions.

---

### Post by Warliy on 2010-06-09
It seams like it's working without the script now with the new kernel for me.

---

### Post by dineshbabumm on 2010-06-09
Thank you very much clemmy for the solution. I have the same unstable wifi issue. I will check if this works. I have another problem with my wifi getting connected to network but not fetching any data (ethernet works fine though).

---

### Post by mudie on 2010-06-12
Continue having problems... 

To fix it i modified the scripts and put a link on Desktop, every time I turn on the computer i click on the script... :D

---

