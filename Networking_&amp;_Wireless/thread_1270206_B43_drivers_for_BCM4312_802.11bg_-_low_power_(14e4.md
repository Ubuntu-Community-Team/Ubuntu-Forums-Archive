---
title: "B43 drivers for BCM4312 802.11b/g - low power (14e4:4315 )"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by maramot on 2009-09-19
**Machine brand and model:** Dell Inspiron 1520

**Wireless brand, model and wireless chipset:**
```
maramot@ubuntu:~$ lspci -nn | grep '14e4'
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
**0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)**
```

**iwconfig output:**
```

maramot@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:0D:51:9A   
          Bit Rate=5.5 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**Ubuntu version:**```

maramot@ubuntu:~$ lsb_release -d
Description:	Ubuntu 8.04.3 LTS
```

**Kernel architecture:**
```
maramot@ubuntu:~$ uname -mr
2.6.24-24-generic i686
```

Hi guys. I am using the unfortunate version of Broadcom 4312 wireless card (14e4:4315), that didn't support the B43 driver the last time I checked. It's been a lot of time and I'd like to post the question again, because I've been looking through google results and all the negative answers about B43 support are dated rather old, or at least I hope so :)

So if anyone is more updated than me, let me know if there is support for B43 on my card type yet. Also, if support exists in a newer ubuntu version, I'm prepared to update. I've kept the 8.04 so long because after I updated from 7.10 immediately after 8.04 went out, I found myself under an avalanche of bugs and hardware issues. :) I guess it's safe to update to 8.10 by now, for example ;P

Cheers!

---

### Post by Metaljaz on 2009-09-19
Update to 9.04. I have had no problems with my broadcom card using the below method. This method should still work with 8.04 and 8.10.

Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

---

### Post by Ayuthia on 2009-09-19
> **maramot said:**
> **Machine brand and model:** Dell Inspiron 1520

**Wireless brand, model and wireless chipset:**
```
maramot@ubuntu:~$ lspci -nn | grep '14e4'
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
**0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)**
```

**iwconfig output:**
```

maramot@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:0D:51:9A   
          Bit Rate=5.5 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**Ubuntu version:**```

maramot@ubuntu:~$ lsb_release -d
Description:	Ubuntu 8.04.3 LTS
```

**Kernel architecture:**
```
maramot@ubuntu:~$ uname -mr
2.6.24-24-generic i686
```

Hi guys. I am using the unfortunate version of Broadcom 4312 wireless card (14e4:4315), that didn't support the B43 driver the last time I checked. It's been a lot of time and I'd like to post the question again, because I've been looking through google results and all the negative answers about B43 support are dated rather old, or at least I hope so :)

So if anyone is more updated than me, let me know if there is support for B43 on my card type yet. Also, if support exists in a newer ubuntu version, I'm prepared to update. I've kept the 8.04 so long because after I updated from 7.10 immediately after 8.04 went out, I found myself under an avalanche of bugs and hardware issues. :) I guess it's safe to update to 8.10 by now, for example ;P

Cheers!

The b43 module has been updated in the 2.6.32 kernel so that it will support the 4315 card.  It does mean that even if you upgrade to Karmic, the b43 module will not be available for you without some manual intervention.

Larry Finger has apparently posted some information about it in the openSUSE forums about it and chenxiaolong has posted some instructions on how to install it here:
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

I do not have this card so I have not tested out the instructions.

---

### Post by maramot on 2009-09-19
@ Metaljaz:
Thanks for the fast reply. :) Should I uninstall ndiswrapper beforehand? I would feel safer with some instructions on how to keep an ndiswrapper ready for installation on my hdd, in case I uninstall it and then I mess something up. I'm at home and I don't have a wired connection. I'd hate to have to restart under windows and move to some wifi cafe. It's rainy today ;)

Also, I take it you are sure b43-fwcutter will work on my type of chipset?

---

### Post by maramot on 2009-09-19
@Ayuthia:
Which ubuntu version does this 2.6.32 kernel correspond to? I take it "Karmic" is the Ubuntu version after Jaunty? As I said, I haven't been around for a while :)

---

### Post by Metaljaz on 2009-09-19
I have been using the broadcom driver with no problems with my dell laptop. I do not use ndiswrapper and i would think that with both installed there could be some conflict problems, so if you diable ndiswrapper or uninstall it be sure you are near a wired connection to complete the install of the broadcom driver.

---

### Post by Ayuthia on 2009-09-19
> **maramot said:**
> @Ayuthia:
Which ubuntu version does this 2.6.32 kernel correspond to? I take it "Karmic" is the Ubuntu version after Jaunty? As I said, I haven't been around for a while :)

It doesn't correspond to any Ubuntu kernel yet.  Karmic is using 2.6.31.  It will be the version after Karmic that will most likely have it.  And yes, Karmic is the one after Jaunty.

As far as I know, the only way to get this right now is to either compile your own kernel or try the steps that I mentioned in my other post.  

The only automated options in Ubuntu for the 4315 card is the Broadcom STA and the NDISwrapper option.  The Broadcom STA option still seems to have problems with hidden ssid and WPA.

---

