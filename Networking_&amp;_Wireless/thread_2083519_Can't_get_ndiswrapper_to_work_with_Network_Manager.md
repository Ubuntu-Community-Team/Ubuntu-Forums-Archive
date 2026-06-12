---
title: "Can't get ndiswrapper to work with Network Manager"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by Ralph L on 2012-11-12
I have a Compaq Presario 2100 on which I have installed several OS's.  A year of so ago I installed lucid, and got my wireless working using ndiswrapper, bcmwl5, and wicd.  However, this combination would work only on an unencrypted wireless network.  (As an aside I noticed that wpa_supplicant never ran as a process under wicd, and this may have had something to do with why I couldn't get WEP, or WPA2 running.)  The reason I used ndiswrapper and the bcmwl5 driver is that the standard linux b43legacy driver works only occasionally on my Broadcom 4306 Rev 2 chip.  After many tries, it may sync up, but it drops sync almost immediately and tries again.  I know my router works fine, because I can easily sync up to it with my other computer (unencrypted or encrypted), as well as with the Presario running ndiswrapper/bcmwl5 (unencrypted) as described above.  Moreover, Windows runs fine on the Presario 2100 (unencrypted or encrypted) using the bcmwl5 driver.  I know that the linux compatibility sites say that b43legacy supports the 4306 chip, but I think they are talking about 4306 Rev 3, not 4306 Rev 2, that I have.

But I don't like leaving my network unencrypted.  So I tried again to get encryption to work.

First, I installed a copy of 12.04.1, the latest version of Precise.  Just to make sure I did a standard install with b43legacy, and got the same results that I got a year ago with lucid.  The wireless may sync up, but it immediately drops out again.  So I proceeded to install ndiswrapper using the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) .  However, when I tried to use ndisgtk (the ndiswrapper gui) to install bcmwl5, it said it couldn't find ndiswrapper.  So I went to [http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found) and followed the directions for downloading ndiswrapper source and installing it.  This seemed to work as ndisgtk no longer complained that it couldn't find ndiswrapper.  I continued the installation according to the first web site above.  However, I noticed that as soon as I tried to do a configure with ndisgtk, the wireless network capability left the Network Manager icon pull down menu.  No longer was the checkbox for Wireless there, nor were any of the available wireless networks--my own or that of my neighbors.  It was if I had just disabled the wireless capability.

So my guess is that I somehow have a configuration parameter wrong and I shut off wireless, but I don't know where.  Any help would be appreciated.

---

### Post by Ralph L on 2012-11-15
COME ON PEOPLE!!!  How about a reply!!  Somebody must have installed ndiswrapper with Network Manager!!!  There is a Community Help Wiki site ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) ) with very detailed instructions for doing this installation, and it is very current having been updated for Precise (12.04) and even for 12.10 Quantal Quetza.  So somebody had to write it.  

My problem is that, when I follow the instructions, it still doesn't work as I stated in my first post above.  I can give a step by step description of what I have done if that would help anybody.  However, as far as I know I have done just what is specified in the web site.

HELP!!!

---

### Post by chili555 on 2012-11-17
I love a mystery.

I won't be surprised at all that older Broadcom devices may not do WPA and especially WPA2. There is a reason it's called 'legacy.' I will be *quite* surprised if bcmwlhigh5 is the correct inf for the device. I strongly suspect it's a hardware vs. driver problem and not an ndiswrapper vs. Network Manager problem. Please run and post:```
lspci -nn | grep 0280
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```There are many versions of bcmwhigh5.inf floating around. I even have a few myself. Where did you find yours?

---

### Post by flash63 on 2012-11-17
Hello,
i think this device works direct with b43/b43-legacy, but requires the right Firmware-file.

Same problem here: 
[http://ubuntuforums.org/showthread.php?p=12359653#post12359653](http://ubuntuforums.org/showthread.php?p=12359653#post12359653)

---

### Post by Ralph L on 2012-11-18
Flash63
Thank you very much for responding.

Edited in latter:  Flash63:  I am afraid I might have misled you.  What I have listed below is from my lucid system that uses bcmwl5, ndiswrapper, and wicd.  It run unencrypted wireless very well, but won't run encrypted.  I also have a Precise Pangolin system on which I have installed bcmwl5, ndiswrapper, but not wicd.  On that system I am trying to use Network Manager that came pre-installed.  I have messed up that system by trying many things, so I am going to do a fresh install and get you the results from a fresh system into which I have just installed ndiswrapper and bcmwl5.

I apparently have the ucode4.fw loaded.  See below:

ralph@presario-lucid:/lib/firmware/b43legacy$ ls -l
total 132
-rw-r--r-- 1 root root    18 2011-09-25 12:58 a0g0bsinitvals2.fw
-rw-r--r-- 1 root root   158 2011-09-25 12:58 a0g0bsinitvals5.fw
-rw-r--r-- 1 root root  2520 2011-09-25 12:58 a0g0initvals2.fw
-rw-r--r-- 1 root root  1818 2011-09-25 12:58 a0g0initvals5.fw
-rw-r--r-- 1 root root   158 2011-09-25 12:58 a0g1bsinitvals5.fw
-rw-r--r-- 1 root root  1818 2011-09-25 12:58 a0g1initvals5.fw
-rw-r--r-- 1 root root    18 2011-09-25 12:58 b0g0bsinitvals2.fw
-rw-r--r-- 1 root root   158 2011-09-25 12:58 b0g0bsinitvals5.fw
-rw-r--r-- 1 root root  2520 2011-09-25 12:58 b0g0initvals2.fw
-rw-r--r-- 1 root root  1818 2011-09-25 12:58 b0g0initvals5.fw
-rw-r--r-- 1 root root  1320 2011-09-25 12:58 pcm4.fw
-rw-r--r-- 1 root root  1320 2011-09-25 12:58 pcm5.fw
-rw-r--r-- 1 root root 21680 2011-09-25 12:58 ucode11.fw
-rw-r--r-- 1 root root 16360 2011-09-25 12:58 ucode2.fw
-rw-r--r-- 1 root root 20096 2011-09-25 12:58 ucode4.fw
-rw-r--r-- 1 root root 22280 2011-09-25 12:58 ucode5.fw
ralph@presario-lucid:/lib/firmware/b43legacy$ 


Maybe it is not in the correct folder;  I don't know.

Thanks again,
Ralph

---

### Post by Ralph L on 2012-11-18
Chili555

Thank you very much for responding.  Here is what you asked.  This system runs with no encryption using bcmwl5, ndiswrapper, and wicd.

```
ralph@presario-lucid:~$ lspci -nn | grep 0280
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
ralph@presario-lucid:~$ sudo modprobe ndiswrapper
[sudo] password for ralph: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
ralph@presario-lucid:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
ralph@presario-lucid:~$ dmesg | grep ndis
[   26.069664] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   27.246611] usbcore: registered new interface driver ndiswrapper
[   30.236000] usbcore: deregistering interface driver ndiswrapper
[   30.335117] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   30.414843] ndiswrapper: driver bcmwl5 (Linksys,02/12/2003, 3.10.39.7) loaded
[   30.415299] ndiswrapper 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[   30.537492] ndiswrapper: using IRQ 10
[   30.749203] ndiswrapper (set_ndis_auth_mode:619): setting auth mode to 3 failed (C0010015)
[   30.753273] usbcore: registered new interface driver ndiswrapper
ralph@presario-lucid:~$ 
```

Thanks again,
Ralph

---

### Post by chili555 on 2012-11-18
Let's see if your hardware does WPA:```
sudo iwlist wlan0 auth
```I'm pretty sure this is a valuable clue:> ndiswrapper (set_ndis_auth_mode:619): setting *auth mode* to 3 failed (C0010015)

---

### Post by Ralph L on 2012-11-18
Chili55

Here is the information you requested from my lucid system that uses ndiswrapper, bcmwl55, and wicd and runs well unencrypted but won't run encrypted.  One thing I noticed that may be relevant is that wpa supplicant did not show in the list of running processes.

```
ralph@presario-lucid:~$ sudo iwlist wlan0 auth
[sudo] password for ralph: 
wlan0     unknown authentication information.

```

Thanks for helping me.

---

### Post by Ralph L on 2012-11-18
Flash63

I installed, from the live cd, into a new disk partition 12.04.1,the latest version of Precise.  I then installed, using synaptic, the b43legacy driver. The network manager icon showed it connected to my wireless, but then dropped out.  It kept connecting and dropping out and I could not use it.  I have had this experience many times before.  b43legacy (nor b43) will work with this Broadcom 4306 rev2 chip.

So once again, using synaptic, I installed ndiswrapper from source, then ndisgtk, etc.  Then I used ndisgtk to install bcmwl5 and followed the installation procedure in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) .  I got no errors during the installation.  Note that the installation procedure emptied /lib/firmware/b43legacy of all its contents.  Then I rebooted and network manager icon no longer showed wireless networks.

So I followed your directions and performed
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```

This reinstalled the firmware into the /lib/firmware/b43legacy folder, and also installed the /lib/firmware/b43 folder with all its firmware.  I rebooted, but still no wireless networks showed up.  This is understandable, because I now had a mix of b43legacy and ndiswrapper.

So once again I proved that b43legacy and b43 won't work with a Broadcom 4306 REV 2 chip.  And I am back to the same problem that I can't get Precise with Network Manager to work with ndiswrapper.  As I said in my original post I do have (in another disk partition) Lucid Lynx running with ndiswrapper, bcmwl5, and wicd.  However, this only works with unencrypted wireless, which I don't like to use.  But with Precise and Network Manager, wireless is completely disabled.  And I don't know how to re-enable it.

Thank you for your help.  I appreciate it very much.  I look forward to any other ideas you might have on the subject.

---

### Post by Ralph L on 2012-11-18
Chili555

As I mentioned above I did a complete install from live cd into a new disk partition Precise Pangolin 12.04.1.  I then followed the instructions in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to do the ndiswrapper installation.  I had to install ndiswrapper itself from source, and I used ndisgtk to install bcmwl5.  After a restart wireless was completely shut off and I couldn't get it to re-enable.  Here is the output of the items you asked me to run again, but this time on Precise rather than Lucid with ndiswrapper working (but not with encryption).

```
ralph@ralph-Presario-2100-DM728A:/lib/firmware$ lspci -nn | grep 0280
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
ralph@ralph-Presario-2100-DM728A:/lib/firmware$ sudo modprobe ndiswrapper
ralph@ralph-Presario-2100-DM728A:/lib/firmware$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
ralph@ralph-Presario-2100-DM728A:/lib/firmware$ dmesg | grep ndi
[    2.529592] powernow: This is indicative of a broken BIOS.
[    3.284358] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[ 2461.517470] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 2461.564384] usbcore: registered new interface driver ndiswrapper
ralph@ralph-Presario-2100-DM728A:/lib/firmware$ sudo iwlist wlan0 auth
wlan0     no authentication information.

ralph@ralph-Presario-2100-DM728A:/lib/firmware$ 
```

You help is much appreciated.
Ralph

---

### Post by flash63 on 2012-11-19
> This reinstalled the firmware into the /lib/firmware/b43legacy folder, and also installed the /lib/firmware/b43 folder with all its firmware. I rebooted, but still no wireless networks showed up. This is understandable, because I now had a mix of b43legacy and ndiswrapper.
Unload Ndiswrapper and load b43/b43-legacy

```
sudo modprobe -rfv ndiswrapper
sudo modprobe ssb b43legacy
iwconfig
dmesg | egrep 'b43|Firm'
```

---

### Post by Ralph L on 2012-11-20
Flash63

Here is the output you requested.  Because I had made other mods to the system I installed yesterday, I installed still another OS into a new disk partition.  I will use this partition exclusively for changes you ask for. 
```

ralph@ralph-Presario-2100-DM728A:~$ sudo modprobe -rfv ndiswrapper
[sudo] password for ralph: 
FATAL: Module ndiswrapper not found.
ralph@ralph-Presario-2100-DM728A:~$ sudo modprobe ssb b43legacy
ralph@ralph-Presario-2100-DM728A:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

ralph@ralph-Presario-2100-DM728A:~$ dmesg | egrep 'b43|Firm'
[    3.311166] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    9.818425] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[    9.866158] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[    9.866181] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[    9.893261] b43legacy-phy0 debug: Radio initialized
[   17.278669] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   17.278681] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 7754.884125] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[ 7754.948657] b43legacy-phy0 debug: Chip initialized
[ 7754.949202] b43legacy-phy0 debug: 30-bit DMA initialized
[ 7754.951208] Registered led device: b43legacy-phy0::radio
[ 7754.951261] b43legacy-phy0 debug: Wireless interface started
[ 7754.964482] b43legacy-phy0 debug: Adding Interface type 2
ralph@ralph-Presario-2100-DM728A:~$ 
```

Just a note.  The wireless came up and ran fine as soon as I installed firmware-b43-installer.  However, it kept dropping out and resyncing so it was not useful.

Thanks for your help
Ralph

---

### Post by Bucky Ball on 2012-11-20
You actually need firmware-b43-installer and b43-fwcutter which has largely superseded ndiswrapper.

If that is going to work, you won't find out with ndiswrapper installed. Gets in the way. Chilli555 can probably add to this.

---

### Post by flash63 on 2012-11-20
The Firmware-File ucode4.fw is still missing:
```
[   17.278669] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
```

> The wireless came up and ran fine as soon as I installed firmware-b43-installer.
Check again:
```
dmesg | egrep 'b43|Firm'
```
If the same error occurs, install the older Firmware-Package as formerly described. ucode4.fw for this older device was not included into the official Firmware-Packages.

Now uninstall Ndiswrapper completely.

---

### Post by Ralph L on 2012-11-20
Flash63

I did as you said on the clean install.  I still got the same error about about the firmware.  See below.

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```

```
ralph@ralph-Presario-2100-DM728A:~$ dmesg | egrep 'b4|Firm'
[    3.311166] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    9.818425] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[    9.866158] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[    9.866181] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[    9.893261] b43legacy-phy0 debug: Radio initialized
C
[ 7754.884125] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[ 7754.948657] b43legacy-phy0 debug: Chip initialized
[ 7754.949202] b43legacy-phy0 debug: 30-bit DMA initialized
[ 7754.951208] Registered led device: b43legacy-phy0::radio
[ 7754.951261] b43legacy-phy0 debug: Wireless interface started
[ 7754.964482] b43legacy-phy0 debug: Adding Interface type 2
[ 9113.427823] b43legacy-phy0 debug: Removing Interface type 2
[ 9113.432203] b43legacy-phy0 debug: Wireless interface stopped
[ 9113.440532] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 14/64
[ 9113.440651] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 7/64
[ 9113.440752] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[ 9113.448145] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[ 9113.456121] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[ 9113.464177] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[ 9113.472042] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 28/128
[ 9113.480041] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[ 9113.488045] b43legacy-phy0 debug: Radio initialized
[ 9113.488059] b43legacy-phy0 debug: Radio initialized
[50494.140100] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[50494.204623] b43legacy-phy0 debug: Chip initialized
[50494.205492] b43legacy-phy0 debug: 30-bit DMA initialized
[50494.211219] Registered led device: b43legacy-phy0::radio
[50494.211307] b43legacy-phy0 debug: Wireless interface started
[50494.217490] b43legacy-phy0 debug: Adding Interface type 2
ralph@ralph-Presario-2100-DM728A:~$ 
```

Thanks for taking so much time.

---

### Post by flash63 on 2012-11-20
Hello,
there occurs no more errors. Everything seems to be right now.

previous message was
```
[   17.278669] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
```

---

### Post by Ralph L on 2012-11-20
I'm not sure what you mean.  Doesn't the big ERROR message still mean that I have an error?

Anyway, it still doesn't work.  It just connects for a few seconds and then drops out. This is what it has been doing consistently, since I first tried to use b43legacy and b43.  Neither has been able to maintain a connection.  The system is unuseable.

Ralph

---

### Post by Bucky Ball on 2012-11-20
Are you 110% positive you have totally removed ndiswrapper?

---

### Post by varunendra on 2012-11-21
> **Ralph L said:**
> Anyway, it still doesn't work.  It just connects for a few seconds and then drops out. This is what it has been doing consistently, since I first tried to use b43legacy and b43.  Neither has been able to maintain a connection.  The system is unuseable.
I see that you are already being helped by the best people here, so just to help making the current picture a bit more clearer, please run and post the result of 'wireless_script' as suggested here : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

It should be able to give us all (or most) of the info we are interested in.

---

### Post by flash63 on 2012-11-21
Hello,
please use additionally the following Terminal-Commands for a better diagnosis after the connection was lost.

filter out your syslog and interface-settings:
```
egrep 'Net|b43|Firm|reason' /var/log/syslog
ifconfig
iwconfig
```

Basic Wireless Settings of your Wireless Router:
 * use only safe WPA2-AES Encryption, no mixed-Modes like WPA1/2 or WPA2-TKIP!
 * find a free radio-channel, don't use „Auto“ Konfiguration. For that, check other WLAN Access-Points in your neighbourhood:
```
sudo iwlist scan
```

---

### Post by Ralph L on 2012-11-22
Guys

Thank you very much for all your help.  However, I am traveling for about a week and won't have the malfunctioning computer with me.  I will be back home on Wed Nov 28, so I will be able to further work on my connection problem at that time.  I certainly hope you all will be able to continue helping me at that time.

Have a good Thanksgiving!!
Ralph

---

### Post by Ralph L on 2012-11-28
I am back.  I am pretty busy so I may not respond to everything quickly, but I would appreciate you people sticking with me to resolve this.

BuckyBall:
As to your question was all of ndiswrapper removed.  Answer:  I created a brand new clean install for these tests--a new disk partition.  I at no time installed ndiswrapper into this partition, so yes, I am sure ndiswrapper is not there.

varunendra: 
Here are the results of running "wireless script"


```
*************** info trace ****************



**** uname -a ****


Linux ralph-Presario-2100-DM728A 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Subsystem: Compaq Computer Corporation Device [0e11:00e7]
	Kernel driver in use: b43-pci-bridge
--
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
	Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network [103c:0024]
	Kernel driver in use: natsemi
	Kernel modules: natsemi


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**** lsmod ****


Module                  Size  Used by
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        106082  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ali5451,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
b43legacy             127187  0 
radeon                737891  2 
mac80211              436455  1 b43legacy
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39791  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                86486  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd                    62064  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali15x3            12878  0 
drm                   197599  4 radeon,ttm,drm_kms_helper
cfg80211              178679  2 b43legacy,mac80211
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
soundcore              14635  1 snd
i2c_ali1535            12777  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14108  1 snd_pcm
i2c_algo_bit           13199  1 radeon
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  1 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
video                  19068  0 
shpchp                 32325  0 
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
natsemi                36039  0 
pata_ali               13562  3 
crc_itu_t              12627  1 firewire_core
ssb                    50691  1 b43legacy
floppy                 60310  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            natsemi
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43legacy
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    taz:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA
    hpsetup:         Ad-Hoc, <MAC address removed>, Freq 2437 MHz, Rate 11 Mb/s, Strength 85
    Westminister Home Network: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Westminister Guest Network: Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 45 WPA2
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49
    westell2459:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"taz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00001a9593742149
                    Extra: Last beacon: 1048ms ago
                    IE: Unknown: 000374617A
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000100000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A0001101044000101103B000103104700102880288028801880A88000212970DD0F1021000C4C696E6B73797320496E632E1023001952616E6765506C757320576972656C65737320526F75746572102400065254323836301042000831323334353637381054000800060050F20400011011000E4C696E6B7379732057525431313010080002008A103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000084f0fcb7be2
                    Extra: Last beacon: 632ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020011000000
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"westell2459"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b69f10a8198
                    Extra: Last beacon: 776ms ago
                    IE: Unknown: 000B77657374656C6C32343539
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000037c94187
                    Extra: Last beacon: 716ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
          Cell 05 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Westminister Home Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000128e60d3d93f
                    Extra: Last beacon: 1124ms ago
                    IE: Unknown: 0019576573746D696E697374657220486F6D65204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1602001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106B8C75D09B47B
          Cell 06 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Westminister Guest Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000128e60d3e2bd
                    Extra: Last beacon: 1120ms ago
                    IE: Unknown: 001A576573746D696E6973746572204775657374204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1602001300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750208
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F20700010106B8C75D09B47B



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search westell.com


**** blacklist.conf ****


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


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard           Presario 2100 (DM728A)   /0024                     , BIOS KAM1.48   08/22/2003
[    1.736215] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    1.736282] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
[    1.736289] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    1.736295] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x01, vendor 0x4243)
[    1.736301] ssb: Core 3 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    1.736306] ssb: Core 4 found: PCI (cc 0x804, rev 0x07, vendor 0x4243)
[    1.736312] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    1.739707] ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
[   18.930004] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   18.953618] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   18.953648] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   18.976188] b43legacy-phy0 debug: Radio initialized
[   22.396079] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   22.460667] b43legacy-phy0 debug: Chip initialized
[   22.461180] b43legacy-phy0 debug: 30-bit DMA initialized
[   22.461678] Registered led device: b43legacy-phy0::radio
[   22.461721] b43legacy-phy0 debug: Wireless interface started
[   22.476580] b43legacy-phy0 debug: Adding Interface type 2
[   22.500576] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.505138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.572260] wlan0: authenticate with <MAC address removed> (try 1)
[   26.772108] wlan0: authenticate with <MAC address removed> (try 2)
[   26.972154] wlan0: authenticate with <MAC address removed> (try 3)
[   27.172119] wlan0: authentication with <MAC address removed> timed out
[   33.496130] wlan0: authenticate with <MAC address removed> (try 1)
[   33.696164] wlan0: authenticate with <MAC address removed> (try 2)
[   33.896160] wlan0: authenticate with <MAC address removed> (try 3)
[   34.096120] wlan0: authentication with <MAC address removed> timed out
[   40.416341] wlan0: authenticate with <MAC address removed> (try 1)
[   40.616068] wlan0: authenticate with <MAC address removed> (try 2)
[   40.816128] wlan0: authenticate with <MAC address removed> (try 3)
[   41.016054] wlan0: authentication with <MAC address removed> timed out
[   47.324138] wlan0: authenticate with <MAC address removed> (try 1)
[   47.524123] wlan0: authenticate with <MAC address removed> (try 2)
[   47.603773] type=1400 audit(1354147959.744:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1542 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   47.724137] wlan0: authenticate with <MAC address removed> (try 3)
[   47.924072] wlan0: authentication with <MAC address removed> timed out
[   54.236272] wlan0: authenticate with <MAC address removed> (try 1)
[   54.436100] wlan0: authenticate with <MAC address removed> (try 2)
[   54.636157] wlan0: authenticate with <MAC address removed> (try 3)
[   54.836116] wlan0: authentication with <MAC address removed> timed out
[   61.148133] wlan0: authenticate with <MAC address removed> (try 1)
[   61.348698] wlan0: authenticate with <MAC address removed> (try 2)
[   61.548221] wlan0: authenticate with <MAC address removed> (try 3)
[   61.748124] wlan0: authentication with <MAC address removed> timed out
[   68.072194] wlan0: authenticate with <MAC address removed> (try 1)
[   68.272111] wlan0: authenticate with <MAC address removed> (try 2)
[   68.472111] wlan0: authenticate with <MAC address removed> (try 3)
[   68.672112] wlan0: authentication with <MAC address removed> timed out
[   75.000171] wlan0: authenticate with <MAC address removed> (try 1)
[   75.200839] wlan0: authenticate with <MAC address removed> (try 2)
[   75.400070] wlan0: authenticate with <MAC address removed> (try 3)
[   75.600519] wlan0: authentication with <MAC address removed> timed out
[   81.944143] wlan0: authenticate with <MAC address removed> (try 1)
[   82.144149] wlan0: authenticate with <MAC address removed> (try 2)
[   82.344161] wlan0: authenticate with <MAC address removed> (try 3)
[   82.544159] wlan0: authentication with <MAC address removed> timed out
[  122.868111] wlan0: authenticate with <MAC address removed> (try 1)
[  123.068591] wlan0: authenticate with <MAC address removed> (try 2)
[  123.268125] wlan0: authenticate with <MAC address removed> (try 3)
[  123.468620] wlan0: authentication with <MAC address removed> timed out
[  129.800164] wlan0: direct probe to <MAC address removed> (try 1/3)
[  130.000089] wlan0: direct probe to <MAC address removed> (try 2/3)
[  130.200064] wlan0: direct probe to <MAC address removed> (try 3/3)
[  130.400097] wlan0: direct probe to <MAC address removed> timed out
[  136.712181] wlan0: authenticate with <MAC address removed> (try 1)
[  136.912129] wlan0: authenticate with <MAC address removed> (try 2)
[  137.112123] wlan0: authenticate with <MAC address removed> (try 3)
[  137.312140] wlan0: authentication with <MAC address removed> timed out
[  143.640220] wlan0: authenticate with <MAC address removed> (try 1)
[  143.840103] wlan0: authenticate with <MAC address removed> (try 2)
[  144.040098] wlan0: authenticate with <MAC address removed> (try 3)
[  144.240098] wlan0: authentication with <MAC address removed> timed out
[  150.584197] wlan0: direct probe to <MAC address removed> (try 1/3)
[  150.784145] wlan0: direct probe to <MAC address removed> (try 2/3)
[  150.984143] wlan0: direct probe to <MAC address removed> (try 3/3)
[  151.184096] wlan0: direct probe to <MAC address removed> timed out
[  157.504228] wlan0: authenticate with <MAC address removed> (try 1)
[  157.704143] wlan0: authenticate with <MAC address removed> (try 2)
[  157.904140] wlan0: authenticate with <MAC address removed> (try 3)
[  158.104128] wlan0: authentication with <MAC address removed> timed out
[  164.428253] wlan0: authenticate with <MAC address removed> (try 1)
[  164.628063] wlan0: authenticate with <MAC address removed> (try 2)
[  164.828345] wlan0: authenticate with <MAC address removed> (try 3)
[  165.028056] wlan0: authentication with <MAC address removed> timed out
[  171.352232] wlan0: authenticate with <MAC address removed> (try 1)
[  171.552138] wlan0: authenticate with <MAC address removed> (try 2)
[  171.752119] wlan0: authenticate with <MAC address removed> (try 3)
[  171.952138] wlan0: authentication with <MAC address removed> timed out
[  178.272293] wlan0: authenticate with <MAC address removed> (try 1)
[  178.472135] wlan0: authenticate with <MAC address removed> (try 2)
[  178.672120] wlan0: authenticate with <MAC address removed> (try 3)
[  178.872133] wlan0: authentication with <MAC address removed> timed out
[  186.416202] wlan0: authenticate with <MAC address removed> (try 1)
[  186.616116] wlan0: authenticate with <MAC address removed> (try 2)
[  186.816174] wlan0: authenticate with <MAC address removed> (try 3)
[  187.016123] wlan0: authentication with <MAC address removed> timed out
[  193.352241] wlan0: authenticate with <MAC address removed> (try 1)
[  193.552057] wlan0: authenticate with <MAC address removed> (try 2)
[  193.752304] wlan0: authenticate with <MAC address removed> (try 3)
[  193.952081] wlan0: authentication with <MAC address removed> timed out
[  200.284280] wlan0: direct probe to <MAC address removed> (try 1/3)
[  200.484103] wlan0: direct probe to <MAC address removed> (try 2/3)
[  200.684107] wlan0: direct probe to <MAC address removed> (try 3/3)
[  200.884088] wlan0: direct probe to <MAC address removed> timed out
[  207.208093] wlan0: authenticate with <MAC address removed> (try 1)
[  207.408153] wlan0: authenticate with <MAC address removed> (try 2)
[  207.608121] wlan0: authenticate with <MAC address removed> (try 3)
[  207.808164] wlan0: authentication with <MAC address removed> timed out
[  214.132192] wlan0: authenticate with <MAC address removed> (try 1)
[  214.332122] wlan0: authenticate with <MAC address removed> (try 2)
[  214.532145] wlan0: authenticate with <MAC address removed> (try 3)
[  214.732132] wlan0: authentication with <MAC address removed> timed out
[  221.064215] wlan0: authenticate with <MAC address removed> (try 1)
[  221.268098] wlan0: authenticate with <MAC address removed> (try 2)
[  221.468099] wlan0: authenticate with <MAC address removed> (try 3)
[  221.668161] wlan0: authentication with <MAC address removed> timed out
[  228.000239] wlan0: authenticate with <MAC address removed> (try 1)
[  228.200140] wlan0: authenticate with <MAC address removed> (try 2)
[  228.400115] wlan0: authenticate with <MAC address removed> (try 3)
[  228.600128] wlan0: authentication with <MAC address removed> timed out
[  234.908190] wlan0: authenticate with <MAC address removed> (try 1)
[  235.108166] wlan0: authenticate with <MAC address removed> (try 2)
[  235.308267] wlan0: authenticate with <MAC address removed> (try 3)
[  235.508130] wlan0: authentication with <MAC address removed> timed out
[  241.828216] wlan0: authenticate with <MAC address removed> (try 1)
[  242.028084] wlan0: authenticate with <MAC address removed> (try 2)
[  242.228088] wlan0: authenticate with <MAC address removed> (try 3)
[  242.428072] wlan0: authentication with <MAC address removed> timed out
[  249.380180] wlan0: direct probe to <MAC address removed> (try 1/3)
[  249.580074] wlan0: direct probe to <MAC address removed> (try 2/3)
[  249.781383] wlan0: direct probe to <MAC address removed> (try 3/3)
[  249.980064] wlan0: direct probe to <MAC address removed> timed out
[  256.296142] wlan0: authenticate with <MAC address removed> (try 1)
[  256.496122] wlan0: authenticate with <MAC address removed> (try 2)
[  256.696188] wlan0: authenticate with <MAC address removed> (try 3)
[  256.896119] wlan0: authentication with <MAC address removed> timed out
[  263.220177] wlan0: authenticate with <MAC address removed> (try 1)
[  263.420102] wlan0: authenticate with <MAC address removed> (try 2)
[  263.621419] wlan0: authenticate with <MAC address removed> (try 3)
[  263.820073] wlan0: authentication with <MAC address removed> timed out
[  270.144147] wlan0: direct probe to <MAC address removed> (try 1/3)
[  270.346809] wlan0: direct probe to <MAC address removed> (try 2/3)
[  270.544123] wlan0: direct probe to <MAC address removed> (try 3/3)
[  270.744080] wlan0: direct probe to <MAC address removed> timed out
[  277.068260] wlan0: authenticate with <MAC address removed> (try 1)
[  277.268059] wlan0: authenticate with <MAC address removed> (try 2)
[  277.468126] wlan0: authenticate with <MAC address removed> (try 3)
[  277.668530] wlan0: authentication with <MAC address removed> timed out
[  283.996134] wlan0: authenticate with <MAC address removed> (try 1)
[  284.196433] wlan0: authenticate with <MAC address removed> (try 2)
[  284.396125] wlan0: authenticate with <MAC address removed> (try 3)
[  284.596125] wlan0: authentication with <MAC address removed> timed out
[  290.924215] wlan0: authenticate with <MAC address removed> (try 1)
[  291.124073] wlan0: authenticate with <MAC address removed> (try 2)
[  291.324072] wlan0: authenticate with <MAC address removed> (try 3)
[  291.524142] wlan0: authentication with <MAC address removed> timed out
[  297.852231] wlan0: direct probe to <MAC address removed> (try 1/3)
[  298.052131] wlan0: direct probe to <MAC address removed> (try 2/3)
[  298.252114] wlan0: direct probe to <MAC address removed> (try 3/3)
[  298.452132] wlan0: direct probe to <MAC address removed> timed out
[  318.688139] wlan0: direct probe to <MAC address removed> (try 1/3)
[  318.888266] wlan0: direct probe to <MAC address removed> (try 2/3)
[  319.088132] wlan0: direct probe to <MAC address removed> (try 3/3)
[  319.288136] wlan0: direct probe to <MAC address removed> timed out
[  325.596217] wlan0: direct probe to <MAC address removed> (try 1/3)
[  325.796131] wlan0: direct probe to <MAC address removed> (try 2/3)
[  325.996139] wlan0: direct probe to <MAC address removed> (try 3/3)
[  326.196107] wlan0: direct probe to <MAC address removed> timed out
[  332.520223] wlan0: authenticate with <MAC address removed> (try 1)
[  332.720098] wlan0: authenticate with <MAC address removed> (try 2)
[  332.920090] wlan0: authenticate with <MAC address removed> (try 3)
[  333.120128] wlan0: authentication with <MAC address removed> timed out
[  339.436173] wlan0: authenticate with <MAC address removed> (try 1)
[  339.636116] wlan0: authenticate with <MAC address removed> (try 2)
[  339.836207] wlan0: authenticate with <MAC address removed> (try 3)
[  340.036368] wlan0: authentication with <MAC address removed> timed out
[  352.632206] wlan0: direct probe to <MAC address removed> (try 1/3)
[  352.832195] wlan0: direct probe to <MAC address removed> (try 2/3)
[  353.032135] wlan0: direct probe to <MAC address removed> (try 3/3)
[  353.232057] wlan0: direct probe to <MAC address removed> timed out
[  359.564249] wlan0: authenticate with <MAC address removed> (try 1)
[  359.764139] wlan0: authenticate with <MAC address removed> (try 2)
[  359.964157] wlan0: authenticate with <MAC address removed> (try 3)
[  360.164141] wlan0: authentication with <MAC address removed> timed out
[  366.492503] wlan0: authenticate with <MAC address removed> (try 1)
[  366.692058] wlan0: authenticate with <MAC address removed> (try 2)
[  366.892210] wlan0: authenticate with <MAC address removed> (try 3)
[  367.092076] wlan0: authentication with <MAC address removed> timed out
[  415.552360] wlan0: authenticate with <MAC address removed> (try 1)
[  415.752098] wlan0: authenticate with <MAC address removed> (try 2)
[  415.953248] wlan0: authenticate with <MAC address removed> (try 3)
[  416.152073] wlan0: authentication with <MAC address removed> timed out
[  422.468272] wlan0: authenticate with <MAC address removed> (try 1)
[  422.668043] wlan0: authenticate with <MAC address removed> (try 2)
[  422.868225] wlan0: authenticate with <MAC address removed> (try 3)
[  423.068110] wlan0: authentication with <MAC address removed> timed out
[  429.392226] wlan0: direct probe to <MAC address removed> (try 1/3)
[  429.592173] wlan0: direct probe to <MAC address removed> (try 2/3)
[  429.792113] wlan0: direct probe to <MAC address removed> (try 3/3)
[  429.992101] wlan0: direct probe to <MAC address removed> timed out
[  436.320232] wlan0: authenticate with <MAC address removed> (try 1)
[  436.520207] wlan0: authenticate with <MAC address removed> (try 2)
[  436.720136] wlan0: authenticate with <MAC address removed> (try 3)
[  436.920211] wlan0: authentication with <MAC address removed> timed out
[  443.248213] wlan0: authenticate with <MAC address removed> (try 1)
[  443.448165] wlan0: authenticate with <MAC address removed> (try 2)
[  443.648113] wlan0: authenticate with <MAC address removed> (try 3)
[  443.848111] wlan0: authentication with <MAC address removed> timed out
[  450.172117] wlan0: authenticate with <MAC address removed> (try 1)
[  450.372084] wlan0: authenticate with <MAC address removed> (try 2)
[  450.572065] wlan0: authenticate with <MAC address removed> (try 3)
[  450.772101] wlan0: authentication with <MAC address removed> timed out
[  457.092219] wlan0: authenticate with <MAC address removed> (try 1)
[  457.292099] wlan0: authenticate with <MAC address removed> (try 2)
[  457.492056] wlan0: authenticate with <MAC address removed> (try 3)
[  457.692084] wlan0: authentication with <MAC address removed> timed out
[  464.032199] wlan0: direct probe to <MAC address removed> (try 1/3)
[  464.232080] wlan0: direct probe to <MAC address removed> (try 2/3)
[  464.432217] wlan0: direct probe to <MAC address removed> (try 3/3)
[  464.632092] wlan0: direct probe to <MAC address removed> timed out
[  470.948305] wlan0: authenticate with <MAC address removed> (try 1)
[  471.148176] wlan0: authenticate with <MAC address removed> (try 2)
[  471.348140] wlan0: authenticate with <MAC address removed> (try 3)
[  471.548160] wlan0: authentication with <MAC address removed> timed out
[  672.396231] wlan0: authenticate with <MAC address removed> (try 1)
[  672.596117] wlan0: authenticate with <MAC address removed> (try 2)
[  672.796114] wlan0: authenticate with <MAC address removed> (try 3)
[  672.996258] wlan0: authentication with <MAC address removed> timed out
[  679.320162] wlan0: authenticate with <MAC address removed> (try 1)
[  679.520083] wlan0: authenticate with <MAC address removed> (try 2)
[  679.720063] wlan0: authenticate with <MAC address removed> (try 3)
[  679.920131] wlan0: authentication with <MAC address removed> timed out
[  698.788254] wlan0: direct probe to <MAC address removed> (try 1/3)
[  698.988125] wlan0: direct probe to <MAC address removed> (try 2/3)
[  699.188126] wlan0: direct probe to <MAC address removed> (try 3/3)
[  699.388146] wlan0: direct probe to <MAC address removed> timed out
[  705.716194] wlan0: authenticate with <MAC address removed> (try 1)
[  705.916100] wlan0: authenticate with <MAC address removed> (try 2)
[  706.116107] wlan0: authenticate with <MAC address removed> (try 3)
[  706.316157] wlan0: authentication with <MAC address removed> timed out
[  712.640197] wlan0: authenticate with <MAC address removed> (try 1)
[  712.840135] wlan0: authenticate with <MAC address removed> (try 2)
[  713.040150] wlan0: authenticate with <MAC address removed> (try 3)
[  713.135984] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  713.240121] wlan0: authentication with <MAC address removed> timed out
[  719.564132] wlan0: authenticate with <MAC address removed> (try 1)
[  719.764315] wlan0: authenticate with <MAC address removed> (try 2)
[  719.964110] wlan0: authenticate with <MAC address removed> (try 3)
[  720.164175] wlan0: authentication with <MAC address removed> timed out
[  726.496202] wlan0: authenticate with <MAC address removed> (try 1)
[  726.696205] wlan0: authenticate with <MAC address removed> (try 2)
[  726.896115] wlan0: authenticate with <MAC address removed> (try 3)
[  727.096172] wlan0: authentication with <MAC address removed> timed out
[  735.564304] wlan0: authenticate with <MAC address removed> (try 1)
[  735.764158] wlan0: authenticate with <MAC address removed> (try 2)
[  735.964116] wlan0: authenticate with <MAC address removed> (try 3)
[  736.164106] wlan0: authentication with <MAC address removed> timed out
[  742.500115] wlan0: authenticate with <MAC address removed> (try 1)
[  742.700193] wlan0: authenticate with <MAC address removed> (try 2)
[  742.900117] wlan0: authenticate with <MAC address removed> (try 3)
[  743.100122] wlan0: authentication with <MAC address removed> timed out
[  749.432222] wlan0: authenticate with <MAC address removed> (try 1)
[  749.632082] wlan0: authenticate with <MAC address removed> (try 2)
[  749.832196] wlan0: authenticate with <MAC address removed> (try 3)
[  750.032127] wlan0: authentication with <MAC address removed> timed out
[  756.368083] wlan0: authenticate with <MAC address removed> (try 1)
[  756.568094] wlan0: authenticate with <MAC address removed> (try 2)
[  756.768118] wlan0: authenticate with <MAC address removed> (try 3)
[  756.968088] wlan0: authentication with <MAC address removed> timed out
[  763.304128] wlan0: authenticate with <MAC address removed> (try 1)
[  763.504121] wlan0: authenticate with <MAC address removed> (try 2)
[  763.704129] wlan0: authenticate with <MAC address removed> (try 3)
[  763.904112] wlan0: authentication with <MAC address removed> timed out
[  770.224227] wlan0: authenticate with <MAC address removed> (try 1)
[  770.424079] wlan0: authenticate with <MAC address removed> (try 2)
[  770.624093] wlan0: authenticate with <MAC address removed> (try 3)
[  770.824060] wlan0: authentication with <MAC address removed> timed out
[  777.152207] wlan0: authenticate with <MAC address removed> (try 1)
[  777.352163] wlan0: authenticate with <MAC address removed> (try 2)
[  777.552113] wlan0: authenticate with <MAC address removed> (try 3)
[  777.752141] wlan0: authentication with <MAC address removed> timed out
[  784.080751] wlan0: authenticate with <MAC address removed> (try 1)
[  784.280094] wlan0: authenticate with <MAC address removed> (try 2)
[  784.480084] wlan0: authenticate with <MAC address removed> (try 3)
[  784.680060] wlan0: authentication with <MAC address removed> timed out
[  791.016126] wlan0: authenticate with <MAC address removed> (try 1)
[  791.216146] wlan0: authenticate with <MAC address removed> (try 2)
[  791.416140] wlan0: authenticate with <MAC address removed> (try 3)
[  791.616100] wlan0: authentication with <MAC address removed> timed out
[  798.344130] wlan0: direct probe to <MAC address removed> (try 1/3)
[  798.544115] wlan0: direct probe to <MAC address removed> (try 2/3)
[  798.744109] wlan0: direct probe to <MAC address removed> (try 3/3)
[  798.944185] wlan0: direct probe to <MAC address removed> timed out
[  805.276074] wlan0: authenticate with <MAC address removed> (try 1)
[  805.476068] wlan0: authenticate with <MAC address removed> (try 2)
[  805.676194] wlan0: authenticate with <MAC address removed> (try 3)
[  805.876069] wlan0: authentication with <MAC address removed> timed out
[  812.196261] wlan0: authenticate with <MAC address removed> (try 1)
[  812.396125] wlan0: authenticate with <MAC address removed> (try 2)
[  812.596118] wlan0: authenticate with <MAC address removed> (try 3)
[  812.796090] wlan0: authentication with <MAC address removed> timed out
[  819.112195] wlan0: authenticate with <MAC address removed> (try 1)
[  819.312133] wlan0: authenticate with <MAC address removed> (try 2)
[  819.512264] wlan0: authenticate with <MAC address removed> (try 3)
[  819.712096] wlan0: authentication with <MAC address removed> timed out
[  826.036185] wlan0: authenticate with <MAC address removed> (try 1)
[  826.236091] wlan0: authenticate with <MAC address removed> (try 2)
[  826.436134] wlan0: authenticate with <MAC address removed> (try 3)
[  826.636156] wlan0: authentication with <MAC address removed> timed out
[  832.968126] wlan0: authenticate with <MAC address removed> (try 1)
[  833.168096] wlan0: authenticate with <MAC address removed> (try 2)
[  833.186048] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  833.186263] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  833.368202] wlan0: authenticate with <MAC address removed> (try 3)
[  833.568170] wlan0: authentication with <MAC address removed> timed out
[  839.892212] wlan0: authenticate with <MAC address removed> (try 1)
[  840.092147] wlan0: authenticate with <MAC address removed> (try 2)
[  840.292150] wlan0: authenticate with <MAC address removed> (try 3)
[  840.492146] wlan0: authentication with <MAC address removed> timed out
[  846.832158] wlan0: authenticate with <MAC address removed> (try 1)
[  847.032099] wlan0: authenticate with <MAC address removed> (try 2)
[  847.232133] wlan0: authenticate with <MAC address removed> (try 3)
[  847.432134] wlan0: authentication with <MAC address removed> timed out
[  853.764238] wlan0: authenticate with <MAC address removed> (try 1)
[  853.964125] wlan0: authenticate with <MAC address removed> (try 2)
[  854.164424] wlan0: authenticate with <MAC address removed> (try 3)
[  854.364091] wlan0: authentication with <MAC address removed> timed out
[  861.368093] wlan0: authenticate with <MAC address removed> (try 1)
[  861.568119] wlan0: authenticate with <MAC address removed> (try 2)
[  861.768187] wlan0: authenticate with <MAC address removed> (try 3)
[  861.968129] wlan0: authentication with <MAC address removed> timed out
[  868.304266] wlan0: authenticate with <MAC address removed> (try 1)
[  868.504076] wlan0: authenticate with <MAC address removed> (try 2)
[  868.704099] wlan0: authenticate with <MAC address removed> (try 3)
[  868.904120] wlan0: authentication with <MAC address removed> timed out
[  875.232219] wlan0: authenticate with <MAC address removed> (try 1)
[  875.432354] wlan0: authenticate with <MAC address removed> (try 2)
[  875.632119] wlan0: authenticate with <MAC address removed> (try 3)
[  875.832120] wlan0: authentication with <MAC address removed> timed out
[  882.156801] wlan0: authenticate with <MAC address removed> (try 1)
[  882.356317] wlan0: authenticate with <MAC address removed> (try 2)
[  882.557827] wlan0: authenticate with <MAC address removed> (try 3)
[  882.756077] wlan0: authentication with <MAC address removed> timed out
[  889.080133] wlan0: authenticate with <MAC address removed> (try 1)
[  889.280155] wlan0: authenticate with <MAC address removed> (try 2)
[  889.480147] wlan0: authenticate with <MAC address removed> (try 3)
[  889.680117] wlan0: authentication with <MAC address removed> timed out
[  896.024215] wlan0: authenticate with <MAC address removed> (try 1)
[  896.224100] wlan0: authenticate with <MAC address removed> (try 2)
[  896.424160] wlan0: authenticate with <MAC address removed> (try 3)
[  896.624196] wlan0: authentication with <MAC address removed> timed out
[  902.960149] wlan0: authenticate with <MAC address removed> (try 1)
[  903.160171] wlan0: authenticate with <MAC address removed> (try 2)
[  903.360184] wlan0: authenticate with <MAC address removed> (try 3)
[  903.560129] wlan0: authentication with <MAC address removed> timed out
[  909.892202] wlan0: authenticate with <MAC address removed> (try 1)
[  910.092109] wlan0: authenticate with <MAC address removed> (try 2)
[  910.292131] wlan0: authenticate with <MAC address removed> (try 3)
[  910.492174] wlan0: authentication with <MAC address removed> timed out
[  916.836130] wlan0: authenticate with <MAC address removed> (try 1)
[  917.036132] wlan0: authenticate with <MAC address removed> (try 2)
[  917.236155] wlan0: authenticate with <MAC address removed> (try 3)
[  917.436140] wlan0: authentication with <MAC address removed> timed out
[  924.424212] wlan0: authenticate with <MAC address removed> (try 1)
[  924.624225] wlan0: authenticate with <MAC address removed> (try 2)
[  924.824143] wlan0: authenticate with <MAC address removed> (try 3)
[  925.024110] wlan0: authentication with <MAC address removed> timed out
[  931.344253] wlan0: authenticate with <MAC address removed> (try 1)
[  931.544118] wlan0: authenticate with <MAC address removed> (try 2)
[  931.744101] wlan0: authenticate with <MAC address removed> (try 3)
[  931.944106] wlan0: authentication with <MAC address removed> timed out
[  938.268190] wlan0: authenticate with <MAC address removed> (try 1)
[  938.468106] wlan0: authenticate with <MAC address removed> (try 2)
[  938.668081] wlan0: authenticate with <MAC address removed> (try 3)
[  938.868056] wlan0: authentication with <MAC address removed> timed out
[  945.188159] wlan0: authenticate with <MAC address removed> (try 1)
[  945.388151] wlan0: authenticate with <MAC address removed> (try 2)
[  945.590965] wlan0: authenticate with <MAC address removed> (try 3)
[  945.788154] wlan0: authentication with <MAC address removed> timed out
[  952.424193] b43legacy-phy0 ERROR: MAC suspend failed
[  952.436119] wlan0: authenticate with <MAC address removed> (try 1)
[  952.636555] wlan0: authenticate with <MAC address removed> (try 2)
[  952.836113] wlan0: authenticate with <MAC address removed> (try 3)
[  953.036095] wlan0: authentication with <MAC address removed> timed out
[  959.368123] wlan0: authenticate with <MAC address removed> (try 1)
[  959.568127] wlan0: authenticate with <MAC address removed> (try 2)
[  959.768124] wlan0: authenticate with <MAC address removed> (try 3)
[  959.968102] wlan0: authentication with <MAC address removed> timed out
[  966.296243] wlan0: authenticate with <MAC address removed> (try 1)
[  966.496128] wlan0: authenticate with <MAC address removed> (try 2)
[  966.696106] wlan0: authenticate with <MAC address removed> (try 3)
[  966.896110] wlan0: authentication with <MAC address removed> timed out
[  973.240138] wlan0: authenticate with <MAC address removed> (try 1)
[  973.440200] wlan0: authenticate with <MAC address removed> (try 2)
[  973.640097] wlan0: authenticate with <MAC address removed> (try 3)
[  973.840144] wlan0: authentication with <MAC address removed> timed out
[  980.156216] wlan0: authenticate with <MAC address removed> (try 1)
[  980.356108] wlan0: authenticate with <MAC address removed> (try 2)
[  980.556115] wlan0: authenticate with <MAC address removed> (try 3)
[  980.756136] wlan0: authentication with <MAC address removed> timed out
[ 1221.344185] wlan0: authenticate with <MAC address removed> (try 1)
[ 1221.544093] wlan0: authenticate with <MAC address removed> (try 2)
[ 1221.744098] wlan0: authenticate with <MAC address removed> (try 3)
[ 1221.944176] wlan0: authentication with <MAC address removed> timed out
[ 1228.252140] wlan0: authenticate with <MAC address removed> (try 1)
[ 1228.452120] wlan0: authenticate with <MAC address removed> (try 2)
[ 1228.652094] wlan0: authenticate with <MAC address removed> (try 3)
[ 1228.852116] wlan0: authentication with <MAC address removed> timed out
[ 1235.176106] wlan0: authenticate with <MAC address removed> (try 1)
[ 1235.376130] wlan0: authenticate with <MAC address removed> (try 2)
[ 1235.580190] wlan0: authenticate with <MAC address removed> (try 3)
[ 1235.780136] wlan0: authentication with <MAC address removed> timed out
[ 1242.108142] wlan0: authenticate with <MAC address removed> (try 1)
[ 1242.308139] wlan0: authenticate with <MAC address removed> (try 2)
[ 1242.508148] wlan0: authenticate with <MAC address removed> (try 3)
[ 1242.708125] wlan0: authentication with <MAC address removed> timed out
[ 1249.032246] wlan0: authenticate with <MAC address removed> (try 1)
[ 1249.232133] wlan0: authenticate with <MAC address removed> (try 2)
[ 1249.432124] wlan0: authenticate with <MAC address removed> (try 3)
[ 1249.632154] wlan0: authentication with <MAC address removed> timed out
[ 1255.964288] wlan0: authenticate with <MAC address removed> (try 1)
[ 1256.164088] wlan0: authenticate with <MAC address removed> (try 2)
[ 1256.364137] wlan0: authenticate with <MAC address removed> (try 3)
[ 1256.564132] wlan0: authentication with <MAC address removed> timed out
[ 1262.900184] wlan0: authenticate with <MAC address removed> (try 1)
[ 1263.100129] wlan0: authenticate with <MAC address removed> (try 2)
[ 1263.300117] wlan0: authenticate with <MAC address removed> (try 3)
[ 1263.500105] wlan0: authentication with <MAC address removed> timed out
[ 1269.824134] wlan0: authenticate with <MAC address removed> (try 1)
[ 1270.024116] wlan0: authenticate with <MAC address removed> (try 2)
[ 1270.224117] wlan0: authenticate with <MAC address removed> (try 3)
[ 1270.424146] wlan0: authentication with <MAC address removed> timed out
[ 1276.756204] wlan0: authenticate with <MAC address removed> (try 1)
[ 1276.956081] wlan0: authenticate with <MAC address removed> (try 2)
[ 1277.156117] wlan0: authenticate with <MAC address removed> (try 3)
[ 1277.356056] wlan0: authentication with <MAC address removed> timed out
[ 1284.388134] wlan0: authenticate with <MAC address removed> (try 1)
[ 1284.588070] wlan0: authenticate with <MAC address removed> (try 2)
[ 1284.788079] wlan0: authenticate with <MAC address removed> (try 3)
[ 1284.988657] wlan0: authentication with <MAC address removed> timed out
[ 1291.320200] wlan0: authenticate with <MAC address removed> (try 1)
[ 1291.520940] wlan0: authenticate with <MAC address removed> (try 2)
[ 1291.720087] wlan0: authenticate with <MAC address removed> (try 3)
[ 1291.920112] wlan0: authentication with <MAC address removed> timed out
[ 1298.260167] wlan0: authenticate with <MAC address removed> (try 1)
[ 1298.460135] wlan0: authenticate with <MAC address removed> (try 2)
[ 1298.660162] wlan0: authenticate with <MAC address removed> (try 3)
[ 1298.860117] wlan0: authentication with <MAC address removed> timed out
[ 1305.188090] wlan0: authenticate with <MAC address removed> (try 1)
[ 1305.388094] wlan0: authenticate with <MAC address removed> (try 2)
[ 1305.588110] wlan0: authenticate with <MAC address removed> (try 3)
[ 1305.788138] wlan0: authentication with <MAC address removed> timed out
[ 1312.108291] wlan0: authenticate with <MAC address removed> (try 1)
[ 1312.308063] wlan0: authenticate with <MAC address removed> (try 2)
[ 1312.508095] wlan0: authenticate with <MAC address removed> (try 3)
[ 1312.708054] wlan0: authentication with <MAC address removed> timed out
[ 1319.032191] wlan0: authenticate with <MAC address removed> (try 1)
[ 1319.232101] wlan0: authenticate with <MAC address removed> (try 2)
[ 1319.432088] wlan0: authenticate with <MAC address removed> (try 3)
[ 1319.632111] wlan0: authentication with <MAC address removed> timed out
[ 1325.980130] wlan0: authenticate with <MAC address removed> (try 1)
[ 1326.180130] wlan0: authenticate with <MAC address removed> (try 2)
[ 1326.380120] wlan0: authenticate with <MAC address removed> (try 3)
[ 1326.580199] wlan0: authentication with <MAC address removed> timed out
[ 1332.912127] wlan0: authenticate with <MAC address removed> (try 1)
[ 1333.112120] wlan0: authenticate with <MAC address removed> (try 2)
[ 1333.312254] wlan0: authenticate with <MAC address removed> (try 3)
[ 1333.512121] wlan0: authentication with <MAC address removed> timed out
[ 1339.832215] wlan0: authenticate with <MAC address removed> (try 1)
[ 1340.032138] wlan0: authenticate with <MAC address removed> (try 2)
[ 1340.232117] wlan0: authenticate with <MAC address removed> (try 3)
[ 1340.432075] wlan0: authentication with <MAC address removed> timed out
[ 1347.628264] wlan0: authenticate with <MAC address removed> (try 1)
[ 1347.828121] wlan0: authenticate with <MAC address removed> (try 2)
[ 1348.028116] wlan0: authenticate with <MAC address removed> (try 3)
[ 1348.228106] wlan0: authentication with <MAC address removed> timed out
[ 1354.568217] wlan0: authenticate with <MAC address removed> (try 1)
[ 1354.768273] wlan0: authenticate with <MAC address removed> (try 2)
[ 1354.968103] wlan0: authenticate with <MAC address removed> (try 3)
[ 1355.168197] wlan0: authentication with <MAC address removed> timed out
[ 1361.488127] wlan0: authenticate with <MAC address removed> (try 1)
[ 1361.688074] wlan0: authenticate with <MAC address removed> (try 2)
[ 1361.888374] wlan0: authenticate with <MAC address removed> (try 3)
[ 1362.088134] wlan0: authentication with <MAC address removed> timed out
[ 1368.416215] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1368.616103] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1368.816129] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1369.016115] wlan0: direct probe to <MAC address removed> timed out
[ 1375.360129] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1375.560083] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1375.760067] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1375.960121] wlan0: direct probe to <MAC address removed> timed out
[ 1382.304214] wlan0: authenticate with <MAC address removed> (try 1)
[ 1382.504111] wlan0: authenticate with <MAC address removed> (try 2)
[ 1382.704152] wlan0: authenticate with <MAC address removed> (try 3)
[ 1382.904101] wlan0: authentication with <MAC address removed> timed out
[ 1389.240258] wlan0: authenticate with <MAC address removed> (try 1)
[ 1389.440108] wlan0: authenticate with <MAC address removed> (try 2)
[ 1389.640102] wlan0: authenticate with <MAC address removed> (try 3)
[ 1389.840079] wlan0: authentication with <MAC address removed> timed out
[ 1396.176297] wlan0: authenticate with <MAC address removed> (try 1)
[ 1396.376722] wlan0: authenticate with <MAC address removed> (try 2)
[ 1396.576166] wlan0: authenticate with <MAC address removed> (try 3)
[ 1396.776153] wlan0: authentication with <MAC address removed> timed out
[ 1403.092253] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1403.292129] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1403.492182] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1403.692181] wlan0: direct probe to <MAC address removed> timed out
[ 1419.368129] wlan0: authenticate with <MAC address removed> (try 1)
[ 1419.568057] wlan0: authenticate with <MAC address removed> (try 2)
[ 1419.768516] wlan0: authenticate with <MAC address removed> (try 3)
[ 1419.971153] wlan0: authentication with <MAC address removed> timed out
[ 1426.312060] wlan0: authenticate with <MAC address removed> (try 1)
[ 1426.512110] wlan0: authenticate with <MAC address removed> (try 2)
[ 1426.712079] wlan0: authenticate with <MAC address removed> (try 3)
[ 1426.912411] wlan0: authentication with <MAC address removed> timed out
[ 1433.248259] wlan0: authenticate with <MAC address removed> (try 1)
[ 1433.448125] wlan0: authenticate with <MAC address removed> (try 2)
[ 1433.648142] wlan0: authenticate with <MAC address removed> (try 3)
[ 1433.848109] wlan0: authentication with <MAC address removed> timed out
[ 1440.168241] wlan0: authenticate with <MAC address removed> (try 1)
[ 1440.368121] wlan0: authenticate with <MAC address removed> (try 2)
[ 1440.568108] wlan0: authenticate with <MAC address removed> (try 3)
[ 1440.768097] wlan0: authentication with <MAC address removed> timed out
[ 1447.100193] wlan0: authenticate with <MAC address removed> (try 1)
[ 1447.300110] wlan0: authenticate with <MAC address removed> (try 2)
[ 1447.500099] wlan0: authenticate with <MAC address removed> (try 3)
[ 1447.700169] wlan0: authentication with <MAC address removed> timed out
[ 1454.024145] wlan0: authenticate with <MAC address removed> (try 1)
[ 1454.224113] wlan0: authenticate with <MAC address removed> (try 2)
[ 1454.424060] wlan0: authenticate with <MAC address removed> (try 3)
[ 1454.624125] wlan0: authentication with <MAC address removed> timed out
[ 1460.952217] wlan0: authenticate with <MAC address removed> (try 1)
[ 1461.152125] wlan0: authenticate with <MAC address removed> (try 2)
[ 1461.352146] wlan0: authenticate with <MAC address removed> (try 3)
[ 1461.552295] wlan0: authentication with <MAC address removed> timed out
[ 1467.876135] wlan0: authenticate with <MAC address removed> (try 1)
[ 1468.076099] wlan0: authenticate with <MAC address removed> (try 2)
[ 1468.276108] wlan0: authenticate with <MAC address removed> (try 3)
[ 1468.476385] wlan0: authentication with <MAC address removed> timed out
[ 1474.808288] wlan0: authenticate with <MAC address removed> (try 1)
[ 1475.008109] wlan0: authenticate with <MAC address removed> (try 2)
[ 1475.208145] wlan0: authenticate with <MAC address removed> (try 3)
[ 1475.408149] wlan0: authentication with <MAC address removed> timed out
[ 1482.376251] wlan0: authenticate with <MAC address removed> (try 1)
[ 1482.576124] wlan0: authenticate with <MAC address removed> (try 2)
[ 1482.776135] wlan0: authenticate with <MAC address removed> (try 3)
[ 1482.976098] wlan0: authentication with <MAC address removed> timed out
[ 1489.284213] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 1489.484347] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 1489.684176] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 1489.884123] wlan0: direct probe to <MAC address removed> timed out
[ 1496.212091] wlan0: authenticate with <MAC address removed> (try 1)
[ 1496.412081] wlan0: authenticate with <MAC address removed> (try 2)
[ 1496.612107] wlan0: authenticate with <MAC address removed> (try 3)
[ 1496.812084] wlan0: authentication with <MAC address removed> timed out
[ 1503.140177] wlan0: authenticate with <MAC address removed> (try 1)
[ 1503.340072] wlan0: authenticate with <MAC address removed> (try 2)
[ 1503.540120] wlan0: authenticate with <MAC address removed> (try 3)
[ 1503.740055] wlan0: authentication with <MAC address removed> timed out
[ 1510.068395] wlan0: authenticate with <MAC address removed> (try 1)
[ 1510.268190] wlan0: authenticate with <MAC address removed> (try 2)
[ 1510.468094] wlan0: authenticate with <MAC address removed> (try 3)
[ 1510.668123] wlan0: authentication with <MAC address removed> timed out
[ 1516.992262] wlan0: authenticate with <MAC address removed> (try 1)
[ 1517.192102] wlan0: authenticate with <MAC address removed> (try 2)
[ 1517.392141] wlan0: authenticate with <MAC address removed> (try 3)
[ 1517.592123] wlan0: authentication with <MAC address removed> timed out
[ 1523.932245] wlan0: authenticate with <MAC address removed> (try 1)
[ 1524.132124] wlan0: authenticate with <MAC address removed> (try 2)
[ 1524.332104] wlan0: authenticate with <MAC address removed> (try 3)
[ 1524.532167] wlan0: authentication with <MAC address removed> timed out
[ 1530.852229] wlan0: authenticate with <MAC address removed> (try 1)
[ 1531.052171] wlan0: authenticate with <MAC address removed> (try 2)
[ 1531.252074] wlan0: authenticate with <MAC address removed> (try 3)
[ 1531.452123] wlan0: authentication with <MAC address removed> timed out
[ 1537.772223] wlan0: authenticate with <MAC address removed> (try 1)
[ 1537.972123] wlan0: authenticate with <MAC address removed> (try 2)
[ 1538.172190] wlan0: authenticate with <MAC address removed> (try 3)
[ 1538.372175] wlan0: authentication with <MAC address removed> timed out


**************** done ********************
```

---

### Post by Ralph L on 2012-11-28
Please see the message after this one.

---

### Post by Ralph L on 2012-11-28
Flash63

Here is a later version of the previous message.  I think it has more of what you are looking for.  Note that the network I was trying to connect to, and the only unencrypted network, was "linksys".
```

ralph@ralph-Presario-2100-DM728A:~$ egrep 'Net|b43|Firm|reason' /var/log/syslog
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'linksys' invalid.
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:46:39 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 16:46:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:46:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:46:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:47:42 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long.
Nov 28 16:47:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 16:47:42 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 28 16:47:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:47:43 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> No agents were available for this request.
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (westell2459)
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'westell2459' invalid.
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:47:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:51:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 16:51:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 16:51:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:51:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associating -> completed
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'.
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 2471
Nov 28 16:52:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 28 16:52:30 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 16:52:30 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 192.168.1.100
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 192.168.1.1
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name 'westell.com'
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 16:52:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 16:52:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 16:52:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:52:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 28 16:52:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) successful, device activated.
Nov 28 16:52:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 28 16:52:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 28 16:52:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 16:52:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 16:52:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 28 16:53:13 ralph-Presario-2100-DM728A kernel: [ 2483.055143] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.073074] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.131992] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.145967] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.150482] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.154461] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.161758] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.165309] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:43 ralph-Presario-2100-DM728A kernel: [ 2513.892597] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:53:58 ralph-Presario-2100-DM728A wpa_supplicant[955]: CTRL-EVENT-DISCONNECTED bssid=00:18:f8:55:35:c5 reason=4
Nov 28 16:53:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 28 16:53:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:53:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:54:03 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): roamed from BSSID 00:18:F8:55:35:C5 (linksys) to (none) ((none))
Nov 28 16:54:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> (wlan0): link timed out.
Nov 28 16:54:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2471
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:54:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:55:13 ralph-Presario-2100-DM728A kernel: [ 2603.093378] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:55:13 ralph-Presario-2100-DM728A kernel: [ 2603.094371] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:55:13 ralph-Presario-2100-DM728A kernel: [ 2603.298164] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:55:13 ralph-Presario-2100-DM728A kernel: [ 2603.815716] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:55:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 16:55:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 16:55:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 16:55:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 16:55:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 16:55:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 16:55:14 ralph-Presario-2100-DM728A kernel: [ 2604.014980] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:55:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:55:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:55:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:55:14 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 16:55:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 16:55:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 16:55:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:55:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:55:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:55:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:55:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:55:43 ralph-Presario-2100-DM728A kernel: [ 2633.118100] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:55:43 ralph-Presario-2100-DM728A kernel: [ 2633.233608] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:55:43 ralph-Presario-2100-DM728A kernel: [ 2633.941103] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:56:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:56:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:56:17 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 16:56:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 16:56:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 16:56:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:56:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:56:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:56:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:56:43 ralph-Presario-2100-DM728A kernel: [ 2693.511219] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:56:43 ralph-Presario-2100-DM728A kernel: [ 2693.571068] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:56:43 ralph-Presario-2100-DM728A kernel: [ 2693.724307] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:56:43 ralph-Presario-2100-DM728A kernel: [ 2693.818927] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:57:13 ralph-Presario-2100-DM728A kernel: [ 2723.309843] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:57:14 ralph-Presario-2100-DM728A kernel: [ 2724.028884] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:57:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:57:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:57:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 16:57:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:57:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 16:57:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 16:57:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:57:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:57:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Nov 28 16:57:43 ralph-Presario-2100-DM728A kernel: [ 2753.232613] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:57:43 ralph-Presario-2100-DM728A kernel: [ 2753.431548] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:57:43 ralph-Presario-2100-DM728A kernel: [ 2753.940179] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:57:43 ralph-Presario-2100-DM728A kernel: [ 2754.007646] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'linksys' invalid.
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:58:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:58:23 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 16:58:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 16:58:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 16:58:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:58:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:58:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:58:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:58:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:58:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 16:58:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: group handshake -> completed
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'westell2459'.
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 2554
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 16:58:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 16:58:43 ralph-Presario-2100-DM728A wpa_supplicant[955]: CTRL-EVENT-DISCONNECTED bssid=0c:d5:02:85:85:40 reason=16
Nov 28 16:58:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 28 16:58:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:58:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:58:55 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 28 16:58:55 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 16:58:55 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 16:58:55 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 28 16:59:13 ralph-Presario-2100-DM728A kernel: [ 2843.526358] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> (wlan0): DHCPv4 request timed out.
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2554
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (westell2459)
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 16:59:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Nov 28 16:59:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 16:59:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 16:59:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:59:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 16:59:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 16:59:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 16:59:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 16:59:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 16:59:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:59:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 16:59:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:59:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:59:43 ralph-Presario-2100-DM728A kernel: [ 2873.426929] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:59:43 ralph-Presario-2100-DM728A kernel: [ 2873.427240] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:59:43 ralph-Presario-2100-DM728A kernel: [ 2873.644746] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 16:59:43 ralph-Presario-2100-DM728A kernel: [ 2873.995969] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associating -> associated
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: group handshake -> completed
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'westell2459'.
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 2564
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 17:00:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 10.0.0.7
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 10.0.0.1
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name 'westell.com'
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 17:00:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 17:00:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:00:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:00:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:00:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 28 17:00:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) successful, device activated.
Nov 28 17:00:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 28 17:00:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 28 17:00:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 17:00:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 17:00:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 28 17:00:43 ralph-Presario-2100-DM728A kernel: [ 2933.429599] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:01:43 ralph-Presario-2100-DM728A kernel: [ 2993.224790] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:05:18 ralph-Presario-2100-DM728A wpa_supplicant[955]: CTRL-EVENT-DISCONNECTED bssid=0c:d5:02:85:85:40 reason=4
Nov 28 17:05:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 28 17:05:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:05:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:05:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): roamed from BSSID 0C:D5:02:85:85:40 (westell2459) to (none) ((none))
Nov 28 17:05:33 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> (wlan0): link timed out.
Nov 28 17:05:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2564
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:05:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:05:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:06:13 ralph-Presario-2100-DM728A kernel: [ 3263.455958] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:06:34 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long.
Nov 28 17:06:34 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:06:34 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 28 17:06:35 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:06:35 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:06:43 ralph-Presario-2100-DM728A kernel: [ 3293.254015] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:06:43 ralph-Presario-2100-DM728A kernel: [ 3293.458899] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:06:43 ralph-Presario-2100-DM728A kernel: [ 3293.961855] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> No agents were available for this request.
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (westell2459)
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'westell2459' invalid.
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:06:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:06:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:06:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:06:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:06:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:06:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:06:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associating -> completed
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'.
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 2647
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 192.168.1.100
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 192.168.1.1
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name 'westell.com'
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 17:06:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 17:06:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:06:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:06:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:06:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 28 17:06:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) successful, device activated.
Nov 28 17:06:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 28 17:07:13 ralph-Presario-2100-DM728A kernel: [ 3323.501756] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:07:13 ralph-Presario-2100-DM728A kernel: [ 3323.681952] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:07:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 28 17:07:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 17:07:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 17:07:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 28 17:07:43 ralph-Presario-2100-DM728A kernel: [ 3353.238139] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:07:43 ralph-Presario-2100-DM728A kernel: [ 3353.478875] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:07:43 ralph-Presario-2100-DM728A kernel: [ 3353.786090] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:07:58 ralph-Presario-2100-DM728A wpa_supplicant[955]: CTRL-EVENT-DISCONNECTED bssid=00:18:f8:55:35:c5 reason=4
Nov 28 17:07:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 28 17:07:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:07:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:08:04 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): roamed from BSSID 00:18:F8:55:35:C5 (linksys) to (none) ((none))
Nov 28 17:08:13 ralph-Presario-2100-DM728A kernel: [ 3383.072375] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:08:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> (wlan0): link timed out.
Nov 28 17:08:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2647
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:08:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:08:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:09:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:09:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:09:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:09:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:09:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:09:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:09:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:09:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:09:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:09:14 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:09:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:09:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:09:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:09:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:09:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:09:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:09:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:09:43 ralph-Presario-2100-DM728A kernel: [ 3473.388128] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:09:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 17:09:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associating -> disconnected
Nov 28 17:09:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:09:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:10:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:10:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:10:17 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:10:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:10:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:10:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:10:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:10:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:10:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:10:43 ralph-Presario-2100-DM728A kernel: [ 3533.968405] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:11:13 ralph-Presario-2100-DM728A kernel: [ 3563.499307] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:11:13 ralph-Presario-2100-DM728A kernel: [ 3563.572843] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:11:13 ralph-Presario-2100-DM728A kernel: [ 3563.704117] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:11:19 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:11:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:11:19 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:11:19 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:11:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:11:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:11:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:11:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:11:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:11:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:11:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:11:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:11:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:11:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:11:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:11:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:11:43 ralph-Presario-2100-DM728A kernel: [ 3593.657427] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:11:43 ralph-Presario-2100-DM728A kernel: [ 3593.714358] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:12:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:12:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:12:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:12:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'linksys' invalid.
Nov 28 17:12:23 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:12:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:12:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:12:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:12:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:12:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:12:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 17:12:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 17:12:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:12:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:12:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:12:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:12:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: group handshake -> completed
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'westell2459'.
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 2724
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 17:12:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 10.0.0.7
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 10.0.0.1
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name 'westell.com'
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 17:12:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 17:12:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:12:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:12:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:12:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 28 17:12:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) successful, device activated.
Nov 28 17:12:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 28 17:13:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 28 17:13:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 17:13:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 17:13:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 28 17:14:43 ralph-Presario-2100-DM728A kernel: [ 3773.110994] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:14:43 ralph-Presario-2100-DM728A kernel: [ 3773.213349] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:14:43 ralph-Presario-2100-DM728A kernel: [ 3773.932393] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:14:43 ralph-Presario-2100-DM728A kernel: [ 3773.935669] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:14:43 ralph-Presario-2100-DM728A kernel: [ 3773.938957] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:14:58 ralph-Presario-2100-DM728A wpa_supplicant[955]: CTRL-EVENT-DISCONNECTED bssid=0c:d5:02:85:85:40 reason=4
Nov 28 17:14:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 28 17:14:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:15:00 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:15:04 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): roamed from BSSID 0C:D5:02:85:85:40 (westell2459) to (none) ((none))
Nov 28 17:15:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> (wlan0): link timed out.
Nov 28 17:15:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2724
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:15:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:15:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:16:14 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long.
Nov 28 17:16:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:16:14 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 28 17:16:15 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:16:15 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> No agents were available for this request.
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (westell2459)
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'westell2459' invalid.
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:16:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:16:43 ralph-Presario-2100-DM728A kernel: [ 3893.327471] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:17:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:17:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:17:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:17:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:17:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:17:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:17:43 ralph-Presario-2100-DM728A kernel: [ 3953.232495] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:17:43 ralph-Presario-2100-DM728A kernel: [ 3953.432989] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:17:43 ralph-Presario-2100-DM728A kernel: [ 3953.537599] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:17:43 ralph-Presario-2100-DM728A kernel: [ 3953.664944] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:18:13 ralph-Presario-2100-DM728A kernel: [ 3983.131410] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:18:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:18:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:18:23 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:18:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:18:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:18:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:18:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:18:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:18:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:18:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:18:43 ralph-Presario-2100-DM728A kernel: [ 4013.443581] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:18:43 ralph-Presario-2100-DM728A kernel: [ 4013.546282] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:18:43 ralph-Presario-2100-DM728A kernel: [ 4013.646432] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:18:43 ralph-Presario-2100-DM728A kernel: [ 4013.938623] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:18:43 ralph-Presario-2100-DM728A kernel: [ 4013.966217] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:19:13 ralph-Presario-2100-DM728A kernel: [ 4043.137270] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:19:13 ralph-Presario-2100-DM728A kernel: [ 4043.546375] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:19:13 ralph-Presario-2100-DM728A kernel: [ 4043.758805] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:19:13 ralph-Presario-2100-DM728A kernel: [ 4043.980042] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:19:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:19:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:19:26 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:19:28 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:19:28 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:19:28 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:19:28 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:19:29 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:19:30 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: associating -> completed
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'.
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 2817
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 192.168.1.100
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 192.168.1.1
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name 'westell.com'
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 17:19:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 17:19:52 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:19:52 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:19:52 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 28 17:19:52 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 28 17:19:52 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) successful, device activated.
Nov 28 17:19:52 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 28 17:20:10 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 28 17:20:10 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 28 17:20:10 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 28 17:20:10 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 28 17:21:13 ralph-Presario-2100-DM728A kernel: [ 4163.159303] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:22:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Nov 28 17:22:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Nov 28 17:22:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Nov 28 17:22:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1860
Nov 28 17:22:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:22:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:22:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'linksys' (wlan0) as default for IPv4 routing and DNS.
Nov 28 17:22:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'linksys' (wlan0) as default for IPv4 routing and DNS.
Nov 28 17:23:43 ralph-Presario-2100-DM728A kernel: [ 4313.173933] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:23:43 ralph-Presario-2100-DM728A kernel: [ 4313.276403] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:23:43 ralph-Presario-2100-DM728A kernel: [ 4313.378813] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:23:43 ralph-Presario-2100-DM728A kernel: [ 4313.894155] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:23:44 ralph-Presario-2100-DM728A kernel: [ 4314.096595] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:23:58 ralph-Presario-2100-DM728A wpa_supplicant[955]: CTRL-EVENT-DISCONNECTED bssid=00:18:f8:55:35:c5 reason=4
Nov 28 17:23:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 28 17:23:58 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:24:00 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:24:04 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): roamed from BSSID 00:18:F8:55:35:C5 (linksys) to (none) ((none))
Nov 28 17:24:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> (wlan0): link timed out.
Nov 28 17:24:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2817
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:24:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:24:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:24:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:24:43 ralph-Presario-2100-DM728A kernel: [ 4373.179808] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:24:43 ralph-Presario-2100-DM728A kernel: [ 4373.194318] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:13 ralph-Presario-2100-DM728A kernel: [ 4403.498750] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:13 ralph-Presario-2100-DM728A kernel: [ 4403.611075] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:13 ralph-Presario-2100-DM728A kernel: [ 4403.649570] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:13 ralph-Presario-2100-DM728A kernel: [ 4403.658019] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:13 ralph-Presario-2100-DM728A kernel: [ 4403.797216] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:13 ralph-Presario-2100-DM728A kernel: [ 4403.899608] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:14 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:25:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:25:14 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:25:14 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:25:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:25:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:25:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:25:15 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:25:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:25:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:25:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:25:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:25:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:25:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:25:43 ralph-Presario-2100-DM728A kernel: [ 4433.390525] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:43 ralph-Presario-2100-DM728A kernel: [ 4433.924619] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:43 ralph-Presario-2100-DM728A kernel: [ 4434.010494] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:25:44 ralph-Presario-2100-DM728A kernel: [ 4434.040936] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:26:13 ralph-Presario-2100-DM728A kernel: [ 4463.188691] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:26:13 ralph-Presario-2100-DM728A kernel: [ 4463.291041] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:26:17 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:26:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:26:17 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:26:17 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:26:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:26:17 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:26:18 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:26:18 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:26:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:26:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:26:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:26:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:26:22 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:27:13 ralph-Presario-2100-DM728A kernel: [ 4523.296961] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:27:13 ralph-Presario-2100-DM728A kernel: [ 4523.604468] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:27:13 ralph-Presario-2100-DM728A kernel: [ 4523.706528] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:27:14 ralph-Presario-2100-DM728A kernel: [ 4524.013654] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:27:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:27:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:27:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:27:20 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:27:20 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:27:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:27:21 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:27:21 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:27:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:27:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:27:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:27:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:27:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:27:25 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:27:43 ralph-Presario-2100-DM728A kernel: [ 4553.928123] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:27:44 ralph-Presario-2100-DM728A kernel: [ 4554.041387] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:28:23 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:28:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:28:23 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:28:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'linksys' invalid.
Nov 28 17:28:23 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:28:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:28:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:28:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:28:24 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:28:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 17:28:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 17:28:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:28:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:28:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:28:28 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:28:43 ralph-Presario-2100-DM728A kernel: [ 4613.612821] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:28:43 ralph-Presario-2100-DM728A kernel: [ 4613.817918] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:28:44 ralph-Presario-2100-DM728A kernel: [ 4614.031230] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:29:26 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long.
Nov 28 17:29:26 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:29:26 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 28 17:29:27 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:29:27 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:29:37 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> No agents were available for this request.
Nov 28 17:29:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 28 17:29:37 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (westell2459)
Nov 28 17:29:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'westell2459' invalid.
Nov 28 17:29:37 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:29:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:29:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:29:43 ralph-Presario-2100-DM728A kernel: [ 4673.107160] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:29:43 ralph-Presario-2100-DM728A kernel: [ 4673.515811] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:29:43 ralph-Presario-2100-DM728A kernel: [ 4673.732924] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:29:43 ralph-Presario-2100-DM728A kernel: [ 4673.916656] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:29:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:29:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:29:44 ralph-Presario-2100-DM728A kernel: [ 4674.029865] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:29:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:30:13 ralph-Presario-2100-DM728A kernel: [ 4703.314458] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:30:14 ralph-Presario-2100-DM728A kernel: [ 4704.031191] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:30:43 ralph-Presario-2100-DM728A kernel: [ 4733.317310] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:30:43 ralph-Presario-2100-DM728A kernel: [ 4733.419737] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:30:43 ralph-Presario-2100-DM728A kernel: [ 4733.522120] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:30:43 ralph-Presario-2100-DM728A kernel: [ 4733.910934] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:30:43 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:30:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:30:43 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:30:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'linksys' invalid.
Nov 28 17:30:43 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:30:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:30:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:30:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:30:44 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:30:44 ralph-Presario-2100-DM728A kernel: [ 4734.024001] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:31:43 ralph-Presario-2100-DM728A kernel: [ 4793.220765] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:32:13 ralph-Presario-2100-DM728A kernel: [ 4823.633358] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:33:13 ralph-Presario-2100-DM728A kernel: [ 4883.434437] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:34:13 ralph-Presario-2100-DM728A kernel: [ 4943.235519] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:34:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 17:34:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 17:34:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:34:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:34:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:34:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:34:43 ralph-Presario-2100-DM728A kernel: [ 4973.340747] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:34:43 ralph-Presario-2100-DM728A kernel: [ 4973.903274] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:34:44 ralph-Presario-2100-DM728A kernel: [ 4974.016645] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:35:37 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long.
Nov 28 17:35:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:35:37 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 28 17:35:37 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:35:38 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:35:43 ralph-Presario-2100-DM728A kernel: [ 5033.244184] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:35:43 ralph-Presario-2100-DM728A kernel: [ 5033.550896] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:35:43 ralph-Presario-2100-DM728A kernel: [ 5033.769114] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:35:43 ralph-Presario-2100-DM728A kernel: [ 5033.897534] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:35:43 ralph-Presario-2100-DM728A kernel: [ 5034.010938] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:35:44 ralph-Presario-2100-DM728A kernel: [ 5034.063420] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:35:50 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> No agents were available for this request.
Nov 28 17:35:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 28 17:35:50 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (westell2459)
Nov 28 17:35:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'westell2459' invalid.
Nov 28 17:35:50 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:35:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:35:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:35:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:35:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:35:53 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:35:54 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:35:55 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): disconnecting for new activation request.
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> disconnected (reason 'none') [50 30 0]
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:36:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:36:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:36:43 ralph-Presario-2100-DM728A kernel: [ 5093.045249] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:36:43 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:37:13 ralph-Presario-2100-DM728A kernel: [ 5123.253024] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:37:13 ralph-Presario-2100-DM728A kernel: [ 5123.559708] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:37:13 ralph-Presario-2100-DM728A kernel: [ 5123.776169] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:37:38 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:37:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:37:38 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:37:38 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:37:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:37:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:37:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:37:39 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:37:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:37:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:37:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:37:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:37:42 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:37:43 ralph-Presario-2100-DM728A kernel: [ 5153.767952] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:37:43 ralph-Presario-2100-DM728A kernel: [ 5153.994748] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:37:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:37:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:38:41 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:38:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:38:41 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:38:41 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:38:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:38:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:38:41 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:38:42 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:38:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:38:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:38:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:38:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:38:47 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:39:13 ralph-Presario-2100-DM728A kernel: [ 5243.164597] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:39:44 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:39:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:39:44 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:39:44 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:39:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:39:44 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:39:45 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:39:45 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:39:47 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'linksys'.
Nov 28 17:39:47 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'linksys'
Nov 28 17:39:47 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:39:47 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'linksys'
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:39:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:39:49 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 17:40:13 ralph-Presario-2100-DM728A kernel: [ 5303.168163] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:40:13 ralph-Presario-2100-DM728A kernel: [ 5303.372143] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:40:13 ralph-Presario-2100-DM728A kernel: [ 5303.577257] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:40:13 ralph-Presario-2100-DM728A kernel: [ 5303.790451] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:40:13 ralph-Presario-2100-DM728A kernel: [ 5303.884946] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 28 17:40:47 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 28 17:40:47 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 28 17:40:47 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 28 17:40:47 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Marking connection 'linksys' invalid.
Nov 28 17:40:47 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Activation (wlan0) failed.
Nov 28 17:40:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 28 17:40:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 28 17:40:48 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 28 17:40:48 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 28 17:40:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'westell2459'.
Nov 28 17:40:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) starting connection 'westell2459'
Nov 28 17:40:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 28 17:40:50 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): access point 'westell2459' has security, but secrets are required.
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0/wireless): connection 'westell2459' has security, and secrets exist.  No new secrets needed.
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'ssid' value 'westell2459'
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'scan_ssid' value '1'
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: added 'psk' value '<omitted>'
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Config: set interface ap_scan to 1
Nov 28 17:40:51 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 17:40:52 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
ralph@ralph-Presario-2100-DM728A:~$ 
ralph@ralph-Presario-2100-DM728A:~$ 
ralph@ralph-Presario-2100-DM728A:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:7a:61:53  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8155854 (8.1 MB)  TX bytes:844739 (844.7 KB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97353 (97.3 KB)  TX bytes:97353 (97.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:44:7f:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:192872 (192.8 KB)  TX bytes:63948 (63.9 KB)

ralph@ralph-Presario-2100-DM728A:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

ralph@ralph-Presario-2100-DM728A:~$ sudo iwlist scan
[sudo] password for ralph: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 2E:26:55:62:29:6B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000084fef22a1f9
                    Extra: Last beacon: 664ms ago
                    IE: Unknown: 000768707365747570
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 06020000
                    IE: Unknown: DD09001018020011000000
          Cell 02 - Address: 00:21:29:70:DD:0F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"taz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00001a9672cb2186
                    Extra: Last beacon: 1012ms ago
                    IE: Unknown: 000374617A
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706545720010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401000100000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A0001101044000101103B000103104700102880288028801880A88000212970DD0F1021000C4C696E6B73797320496E632E1023001952616E6765506C757320576972656C65737320526F75746572102400065254323836301042000831323334353637381054000800060050F20400011011000E4C696E6B7379732057525431313010080002008A103C000101
          Cell 03 - Address: 00:18:F8:55:35:C5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000011720418a
                    Extra: Last beacon: 740ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
          Cell 04 - Address: 0C:D5:02:85:85:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"westell2459"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b6ad0631183
                    Extra: Last beacon: 688ms ago
                    IE: Unknown: 000B77657374656C6C32343539
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

ralph@ralph-Presario-2100-DM728A:~$ 
```

---

### Post by varunendra on 2012-11-28
> **Ralph L said:**
> 
```

00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [**[COLOR="DarkRed"]14e4:4320[/COLOR]**] (**[COLOR="DarkRed"]rev 02[/COLOR]**)

Hi,
I'm a bit confused at your wireless connection status. But let's do a test and proceed accordingly. Please run-
[CODE]locate ucode4.fw ucode2.fw
```
It should return a couple of addresses, please post what it returns.

However, if it doesn't return anything, please run (while being connected to internet via cable) -
```
sudo modprobe -rfv b43legacy
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
modprobe -v b43legacy
```
Then retry to connect. Hope it's all you need.

.

---

### Post by Ralph L on 2012-11-29
varunendra
Here is the output from your latest instruction:

varunendra

```
ralph@ralph-Presario-2100-DM728A:~$ locate ucode4.fw ucode2.fw
/lib/firmware/b43legacy/ucode2.fw
/lib/firmware/b43legacy/ucode4.fw
ralph@ralph-Presario-2100-DM728A:~$ 
```

---

### Post by varunendra on 2012-11-29
> **Ralph L said:**
> ```
ralph@ralph-Presario-2100-DM728A:~$ locate ucode4.fw ucode2.fw
/lib/firmware/b43legacy/ucode2.fw
/lib/firmware/b43legacy/ucode4.fw
```
So you already have what I 'believe' is the correct driver for your chip and the required firmware files. Are you still unable to connect?

Mind you, you may need to disconnect the cable connection to connect wirelessly.

---

### Post by Ralph L on 2012-11-29
As I said in my first post, using b43-legacy, it connects and then drops out repeatedly.  It works fine (encrypted or unencrypted) using XP.  It also works fine (unencrypted only) from a lucid installation using ndiswrapper and bcmwl5.  However, I can't get ndiswrapper/bcmwl5 to work (encrypted or unencrypted) from Precise.  And now a year after I installed ndiwrapper in lucid, I can't remember how I did it.  Any suggestions on how to get it running?  Since I have another disk partition in which I have installed Precise with ndiswrapper/bcmwl5, I can run any commands that would help.

Ralph

---

### Post by chili555 on 2012-11-29
It seems that you *do* connect:> : Nov 28 16:52:30 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 192.168.1.100
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 192.168.1.1
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name '[COLOR="Red"]westell[/COLOR].com'
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 28 16:52:32 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 28 16:52:33 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...But then it roams to another SSID:> nager[722]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 28 16:53:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 28 16:54:03 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): [COLOR="Red"]roamed from BSSID 00:18:F8:55:35:C5 (linksys)[/COLOR] to (none) ((none))
Nov 28 16:54:13 ralph-Presario-2100-DM728A NetworkManager[722]: <warn> (wlan0): link timed out.
Nov 28 16:54:13 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2471
Nov 28 16:54:14 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...So who is your preferred network? I suggest you click the Network Manager icon and delete all the extras and while highlighting your prefeerd network, check off 'Connect Automatically.'

There may be some other issues, but let's see if we can connect to at least your preferred home network and stay there.

---

### Post by Ralph L on 2012-11-29
Chili555

I am am generally trying to connect to "linksys".  I set it up to not need encryption (no wep, wpa, wpa2).  I went to nm and deleted the items for the other networks, let it try to connect to linksys and then egreped the syslog.  As usual it didn't stay connected.  Here is what I got:


```
ralph@ralph-Presario-2100-DM728A:~$ egrep 'Net|b43|Firm|reason' /var/log/syslog
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): carrier now ON (device state 20)
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'Wired connection 1'.
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) starting connection 'Wired connection 1'
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 5255
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Beginning IP6 addrconf.
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov 29 10:51:36 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 10.0.0.9
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 10.0.0.1
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name 'westell.com'
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 29 10:51:38 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Nov 29 10:51:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 29 10:51:39 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov 29 10:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 29 10:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 29 10:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) successful, device activated.
Nov 29 10:51:40 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 29 10:51:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): IP6 addrconf timed out or failed.
Nov 29 10:51:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 29 10:51:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 29 10:51:57 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 29 10:56:19 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Nov 29 10:56:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Nov 29 10:56:23 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Nov 29 10:56:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): canceled DHCP transaction, DHCP client pid 5255
Nov 29 10:56:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 29 10:56:24 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): carrier now ON (device state 20)
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Auto-activating connection 'Wired connection 1'.
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) starting connection 'Wired connection 1'
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> dhclient started with pid 5413
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Beginning IP6 addrconf.
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov 29 11:00:56 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   address 10.0.0.9
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   prefix 24 (255.255.255.0)
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   gateway 10.0.0.1
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   nameserver '10.0.0.1'
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info>   domain name 'westell.com'
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 29 11:00:59 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Nov 29 11:01:00 ralph-Presario-2100-DM728A NetworkManager[722]: <info> DNS: starting dnsmasq...
Nov 29 11:01:00 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov 29 11:01:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 29 11:01:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov 29 11:01:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) successful, device activated.
Nov 29 11:01:01 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 29 11:01:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> (eth0): IP6 addrconf timed out or failed.
Nov 29 11:01:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 29 11:01:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 29 11:01:16 ralph-Presario-2100-DM728A NetworkManager[722]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 29 16:08:31 ralph-Presario-2100-DM728A kernel: [    0.111184] NetLabel: Initializing
Nov 29 16:08:31 ralph-Presario-2100-DM728A kernel: [    0.111187] NetLabel:  domain hash size = 128
Nov 29 16:08:31 ralph-Presario-2100-DM728A kernel: [    0.111189] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 29 16:08:31 ralph-Presario-2100-DM728A kernel: [    0.111215] NetLabel:  unlabeled traffic allowed by default
Nov 29 16:08:31 ralph-Presario-2100-DM728A kernel: [    1.764271] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
Nov 29 16:08:31 ralph-Presario-2100-DM728A avahi-daemon[515]: Network interface enumeration completed.
Nov 29 16:08:32 ralph-Presario-2100-DM728A kernel: [   14.996814] type=1400 audit(1354234112.140:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=588 comm="apparmor_parser"
Nov 29 16:08:32 ralph-Presario-2100-DM728A kernel: [   15.252741] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
Nov 29 16:08:32 ralph-Presario-2100-DM728A kernel: [   15.280553] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
Nov 29 16:08:32 ralph-Presario-2100-DM728A kernel: [   15.280579] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
Nov 29 16:08:32 ralph-Presario-2100-DM728A kernel: [   15.304447] b43legacy-phy0 debug: Radio initialized
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]: <info> NetworkManager (version 0.9.4.0) is starting...
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]: <info> DNS: loaded plugin dnsmasq
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: init!
Nov 29 16:08:33 ralph-Presario-2100-DM728A kernel: [   16.586873] type=1400 audit(1354234113.728:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=788 comm="apparmor_parser"
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: update_system_hostname
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPluginIfupdown: management mode: unmanaged
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:09.0/ssb0:0/net/wlan0, iface: wlan0)
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:09.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0)
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: end _init.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    Ifupdown: get unmanaged devices count: 0
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: (139071256) ... get_connections.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: (139071256) ... get_connections (managed=false): return empty list.
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    keyfile: parsing linksys ... 
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    keyfile:     read connection 'linksys'
Nov 29 16:08:33 ralph-Presario-2100-DM728A NetworkManager[742]:    keyfile: parsing westell2459 ... 
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]:    keyfile:     read connection 'westell2459'
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]:    Ifupdown: get unmanaged devices count: 0
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> modem-manager is now available
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:09.0/ssb0:0/ieee80211/phy0/rfkill0) (driver (unknown))
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> WiFi enabled by radio killswitch; disabled by state file
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Networking is enabled by state file
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): using nl80211 for WiFi device control
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> (wlan0): driver supports Access Point (AP) mode
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43legacy' ifindex: 3)
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): now managed
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): bringing up device.
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> failed to allocate link cache: (-10) Operation not supported
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): carrier is OFF
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): new Ethernet device (driver: 'natsemi' ifindex: 2)
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): now managed
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): bringing up device.
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): preparing device.
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (eth0): deactivating device (reason 'managed') [2]
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:12.0/net/eth0
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:09.0/ssb0:0/net/wlan0, iface: wlan0)
Nov 29 16:08:34 ralph-Presario-2100-DM728A NetworkManager[742]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:09.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 29 16:08:59 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): bringing up device.
Nov 29 16:08:59 ralph-Presario-2100-DM728A kernel: [   42.764092] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Nov 29 16:08:59 ralph-Presario-2100-DM728A kernel: [   42.828570] b43legacy-phy0 debug: Chip initialized
Nov 29 16:08:59 ralph-Presario-2100-DM728A kernel: [   42.829085] b43legacy-phy0 debug: 30-bit DMA initialized
Nov 29 16:08:59 ralph-Presario-2100-DM728A kernel: [   42.834471] Registered led device: b43legacy-phy0::radio
Nov 29 16:08:59 ralph-Presario-2100-DM728A kernel: [   42.834543] b43legacy-phy0 debug: Wireless interface started
Nov 29 16:08:59 ralph-Presario-2100-DM728A kernel: [   42.840311] b43legacy-phy0 debug: Adding Interface type 2
Nov 29 16:09:00 ralph-Presario-2100-DM728A NetworkManager[742]: <info> WiFi hardware radio set enabled
Nov 29 16:09:00 ralph-Presario-2100-DM728A NetworkManager[742]: <info> wpa_supplicant started
Nov 29 16:09:00 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: starting -> ready
Nov 29 16:09:00 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov 29 16:09:00 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: ready -> inactive
Nov 29 16:09:00 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Trying to remove a non-existant call id.
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Auto-activating connection 'linksys'.
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) starting connection 'linksys'
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): preparing device.
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'ssid' value 'linksys'
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'scan_ssid' value '1'
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: set interface ap_scan to 1
Nov 29 16:09:02 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: inactive -> scanning
Nov 29 16:09:03 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: associating -> completed
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'.
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> dhclient started with pid 1650
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 29 16:09:17 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info>   address 192.168.1.100
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info>   prefix 24 (255.255.255.0)
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info>   gateway 192.168.1.1
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info>   hostname 'ralph-Presario-2100-DM728A'
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info>   nameserver '10.0.0.1'
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info>   domain name 'westell.com'
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 29 16:09:18 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 29 16:09:19 ralph-Presario-2100-DM728A NetworkManager[742]: <info> DNS: starting dnsmasq...
Nov 29 16:09:19 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 29 16:09:19 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 29 16:09:19 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Policy set 'linksys' (wlan0) as default for IPv4 routing and DNS.
Nov 29 16:09:19 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) successful, device activated.
Nov 29 16:09:19 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 29 16:09:25 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): disconnecting for new activation request.
Nov 29 16:09:25 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: activated -> disconnected (reason 'none') [100 30 0]
Nov 29 16:09:25 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 29 16:09:25 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1650
Nov 29 16:09:25 ralph-Presario-2100-DM728A kernel: [   68.691891] wlan0: deauthenticating from 00:18:f8:55:35:c5 by local choice (reason=3)
Nov 29 16:09:25 ralph-Presario-2100-DM728A wpa_supplicant[1643]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Nov 29 16:09:25 ralph-Presario-2100-DM728A NetworkManager[742]: <info> DNS: starting dnsmasq...
Nov 29 16:09:25 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) starting connection 'linksys'
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'ssid' value 'linksys'
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'scan_ssid' value '1'
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: set interface ap_scan to 1
Nov 29 16:09:26 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 29 16:09:27 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 29 16:09:30 ralph-Presario-2100-DM728A kernel: [   73.185749] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:09:31 ralph-Presario-2100-DM728A kernel: [   73.902502] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): disconnecting for new activation request.
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: config -> disconnected (reason 'none') [50 30 0]
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) starting connection 'hpsetup'
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0/wireless): connection 'hpsetup' requires no security.  No secrets needed.
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'ssid' value 'hpsetup'
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'mode' value '1'
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'frequency' value '2437'
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 29 16:09:52 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: set interface ap_scan to 2
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.855921] b43legacy-phy0 debug: Removing Interface type 2
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.855973] b43legacy-phy0 debug: Wireless interface stopped
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.858622] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 13/64
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.858726] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 8/64
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.858824] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.864175] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.872123] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.880724] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.888150] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 128/128
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.896137] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.904125] b43legacy-phy0 debug: Radio initialized
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   95.904146] b43legacy-phy0 debug: Radio initialized
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   96.528140] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   96.592624] b43legacy-phy0 debug: Chip initialized
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   96.593149] b43legacy-phy0 debug: 30-bit DMA initialized
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   96.596450] Registered led device: b43legacy-phy0::radio
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   96.596506] b43legacy-phy0 debug: Wireless interface started
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   96.612390] b43legacy-phy0 debug: Adding Interface type 1
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: disconnected -> associating
Nov 29 16:09:53 ralph-Presario-2100-DM728A kernel: [   96.648213] b43legacy-phy0 debug: Set beacon interval to 10
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: associating -> completed
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'hpsetup'.
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> dhclient started with pid 1790
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Beginning IP6 addrconf.
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 29 16:09:53 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Nov 29 16:10:14 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 29 16:10:14 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 29 16:10:14 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 29 16:10:14 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 29 16:10:24 ralph-Presario-2100-DM728A kernel: [  127.457028] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> (wlan0): DHCPv4 request timed out.
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1790
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0) failed for access point (hpsetup)
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0) failed.
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 29 16:10:39 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: completed -> disconnected
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Auto-activating connection 'linksys'.
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) starting connection 'linksys'
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'ssid' value 'linksys'
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'scan_ssid' value '1'
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: set interface ap_scan to 1
Nov 29 16:10:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.364352] b43legacy-phy0 debug: Removing Interface type 1
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.372123] b43legacy-phy0 debug: Wireless interface stopped
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.374295] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 13/64
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.374398] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 2/64
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.374497] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.380137] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.388140] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.396207] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.404156] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 42/128
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.412115] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.420047] b43legacy-phy0 debug: Radio initialized
Nov 29 16:10:43 ralph-Presario-2100-DM728A kernel: [  146.420061] b43legacy-phy0 debug: Radio initialized
Nov 29 16:10:44 ralph-Presario-2100-DM728A kernel: [  146.860082] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
Nov 29 16:10:44 ralph-Presario-2100-DM728A kernel: [  146.924612] b43legacy-phy0 debug: Chip initialized
Nov 29 16:10:44 ralph-Presario-2100-DM728A kernel: [  146.925152] b43legacy-phy0 debug: 30-bit DMA initialized
Nov 29 16:10:44 ralph-Presario-2100-DM728A kernel: [  146.928489] Registered led device: b43legacy-phy0::radio
Nov 29 16:10:44 ralph-Presario-2100-DM728A kernel: [  146.928544] b43legacy-phy0 debug: Wireless interface started
Nov 29 16:10:44 ralph-Presario-2100-DM728A kernel: [  146.944429] b43legacy-phy0 debug: Adding Interface type 2
Nov 29 16:10:44 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 29 16:10:44 ralph-Presario-2100-DM728A kernel: [  147.015164] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:10:45 ralph-Presario-2100-DM728A NetworkManager[742]:    keyfile: removed /etc/NetworkManager/system-connections/westell2459.
Nov 29 16:10:52 ralph-Presario-2100-DM728A NetworkManager[742]:    keyfile: removed /etc/NetworkManager/system-connections/hpsetup.
Nov 29 16:11:14 ralph-Presario-2100-DM728A kernel: [  177.343500] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0) failed.
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 29 16:11:42 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 29 16:11:44 ralph-Presario-2100-DM728A kernel: [  206.918628] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:11:44 ralph-Presario-2100-DM728A kernel: [  207.021143] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:11:44 ralph-Presario-2100-DM728A kernel: [  207.737831] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:11:44 ralph-Presario-2100-DM728A kernel: [  207.840233] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Auto-activating connection 'linksys'.
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) starting connection 'linksys'
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'ssid' value 'linksys'
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'scan_ssid' value '1'
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'bssid' value '00:18:f8:55:35:c5'
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: added 'key_mgmt' value 'NONE'
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> Config: set interface ap_scan to 1
Nov 29 16:11:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 29 16:11:46 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 29 16:12:28 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 29 16:12:28 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: associating -> disconnected
Nov 29 16:12:33 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 29 16:12:35 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 29 16:12:44 ralph-Presario-2100-DM728A kernel: [  267.129297] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0) failed for access point (linksys)
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Activation (wlan0) failed.
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 29 16:12:45 ralph-Presario-2100-DM728A NetworkManager[742]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 29 16:13:14 ralph-Presario-2100-DM728A kernel: [  297.337113] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:13:14 ralph-Presario-2100-DM728A kernel: [  297.439467] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:13:14 ralph-Presario-2100-DM728A kernel: [  297.541861] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:13:44 ralph-Presario-2100-DM728A kernel: [  327.032842] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:13:45 ralph-Presario-2100-DM728A kernel: [  327.954369] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:14:14 ralph-Presario-2100-DM728A kernel: [  357.752556] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:14:44 ralph-Presario-2100-DM728A kernel: [  387.755460] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:14:44 ralph-Presario-2100-DM728A kernel: [  387.758060] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:15:15 ralph-Presario-2100-DM728A kernel: [  417.860844] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:15:15 ralph-Presario-2100-DM728A kernel: [  417.962363] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:16:14 ralph-Presario-2100-DM728A kernel: [  477.560270] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:16:44 ralph-Presario-2100-DM728A kernel: [  507.664857] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:17:14 ralph-Presario-2100-DM728A kernel: [  537.360548] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:17:44 ralph-Presario-2100-DM728A kernel: [  567.056311] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:17:44 ralph-Presario-2100-DM728A kernel: [  567.260993] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:17:44 ralph-Presario-2100-DM728A kernel: [  567.358602] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:18:14 ralph-Presario-2100-DM728A kernel: [  597.059179] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:18:15 ralph-Presario-2100-DM728A kernel: [  597.878357] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:18:44 ralph-Presario-2100-DM728A kernel: [  627.574136] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:19:14 ralph-Presario-2100-DM728A kernel: [  657.167464] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:19:15 ralph-Presario-2100-DM728A kernel: [  657.884241] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:19:44 ralph-Presario-2100-DM728A kernel: [  687.579946] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:19:44 ralph-Presario-2100-DM728A kernel: [  687.682416] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:19:44 ralph-Presario-2100-DM728A kernel: [  687.784718] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:21:14 ralph-Presario-2100-DM728A kernel: [  777.076778] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:21:14 ralph-Presario-2100-DM728A kernel: [  777.179135] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:21:14 ralph-Presario-2100-DM728A kernel: [  777.281519] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:21:44 ralph-Presario-2100-DM728A kernel: [  807.488472] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
Nov 29 16:21:44 ralph-Presario-2100-DM728A kernel: [  807.694131] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
ralph@ralph-Presario-2100-DM728A:~$ 
```

---

### Post by chili555 on 2012-11-29
> b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)I'm stuck here. I'm Googling and suggest you do the same. A few hours from now, Varun will be back and I suggest he do so, too. I haven't found a clue yet.

---

### Post by Ralph L on 2012-11-30
If we are stuck here, maybe you could help me a bit along the line of ndiswrapper.  As I said in my original post I had gotten the wireless to run under lucid using ndiswrapper (unencrypted).  I have another disk partition using Precise into which I have installed ndiswrapper and bcmwl5.  However, as soon as I restarted after installation of ndiswrapper, all traces of wireless went away.  Pulling down nm-applet showed no wireless networks, and even the "enable wireless networks" went away.  Moreover, all the results for the various network Terminal commands never heard of wlan0.

ralph@ralph-Presario-2100-DM728A:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ralph@ralph-Presario-2100-DM728A:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:7a:61:53  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:603488 (603.4 KB)  TX bytes:603488 (603.4 KB)

ralph@ralph-Presario-2100-DM728A:~$ ifconfig wlan0
wlan0: error fetching interface information: Device not found
ralph@ralph-Presario-2100-DM728A:~$ sudo dhclient wlan0
[sudo] password for ralph: 
Cannot find device "wlan0"
ralph@ralph-Presario-2100-DM728A:~$ 


Before I installed ndiswrapper wlan0 would show up in all these commands.  I followed the instructions in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to install ndiswrapper.

Any idea where any of these commands look for wlan0?  I must have wiped out something.  As I said I have ndiswrapper running under lucid, although I don't remember how I did it.

---

### Post by chili555 on 2012-11-30
Have you reinstalled ndiswrapper successfully? Please try:```
sudo modprobe -r b43legacy
sudo modprobe ndiswrapper
```Any errors or interesting messages?

---

### Post by Ralph L on 2012-11-30
Both commands completed normally with no messages.  After I ran them I did

```
ralph@ralph-Presario-2100-DM728A:~$ tail /var/log/syslog
Nov 30 07:46:28 ralph-Presario-2100-DM728A anacron[26703]: Job `cron.daily' terminated
Nov 30 07:46:28 ralph-Presario-2100-DM728A anacron[26703]: Normal exit (1 job run)
Nov 30 08:17:01 ralph-Presario-2100-DM728A CRON[27590]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 09:17:01 ralph-Presario-2100-DM728A CRON[28393]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 09:25:14 ralph-Presario-2100-DM728A kernel: [36442.179759] b43-pci-bridge 0000:00:09.0: PCI INT A disabled

```

---

### Post by Ralph L on 2012-12-01
I ran "wireless script" that came from varunendr on my ndiswrapper version of Precise.  Maybe it can give some hints as to why my wireless has completely disappeared.

Thanks
Ralph

```

*************** info trace ****************



**** uname -a ****


Linux ralph-Presario-2100-DM728A 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Subsystem: Compaq Computer Corporation Device [0e11:00e7]
	Kernel driver in use: b43-pci-bridge
--
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
	Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network [103c:0024]
	Kernel driver in use: natsemi
	Kernel modules: natsemi


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****




**** lsmod ****


Module                  Size  Used by
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        106082  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ali5451,snd_ac97_codec
radeon                737891  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39791  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd                    62064  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                86486  0 
drm                   197599  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
yenta_socket           27465  0 
i2c_ali15x3            12878  0 
soundcore              14635  1 snd
pcmcia_rsrc            18367  1 yenta_socket
i2c_ali1535            12777  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14108  1 snd_pcm
i2c_algo_bit           13199  1 radeon
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
video                  19068  0 
shpchp                 32325  0 
ati_agp                13242  1 
mac_hid                13077  0 
firewire_sbp2          18346  0 
ndiswrapper           192268  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  2 firewire_sbp2,firewire_ohci
natsemi                36039  0 
ssb                    50691  0 
floppy                 60310  0 
pata_ali               13562  3 
crc_itu_t              12627  1 firewire_core


**** nm-tool ****




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****




**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


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

#The following were added by ralph
blacklist b43
blacklist b43legacy
blacklist ssb


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard           Presario 2100 (DM728A)   /0024                     , BIOS KAM1.48   08/22/2003
[    3.377070] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    3.377132] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
[    3.377139] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    3.377144] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x01, vendor 0x4243)
[    3.377150] ssb: Core 3 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    3.377155] ssb: Core 4 found: PCI (cc 0x804, rev 0x07, vendor 0x4243)
[    3.377161] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    3.385765] ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
[   18.393292] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   18.519008] usbcore: registered new interface driver ndiswrapper
[   43.346583] type=1400 audit(1354410945.872:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1550 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************


```

---

### Post by chili555 on 2012-12-01
> #The following were added by ralph
blacklist b43
blacklist b43legacy
blacklist ssbHmmm, they are still loading according to lsmod. Studying..

---

### Post by varunendra on 2012-12-02
> **Ralph L said:**
> 
```
**[COLOR="Red"][    3.377070][/COLOR]** b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
**[COLOR="Red"][    3.377132][/COLOR]** ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
<snip>
**[COLOR="Navy"][   18.393292][/COLOR]** ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
**[COLOR="Navy"][   18.519008][/COLOR]** usbcore: registered new interface driver ndiswrapper

```
I still don't understand all of those messages properly, but quite obviously the b43legacy and ssb are loading much earlier than ndiswrapper. May be a stupid guess, assuming Ralph has reported everything he has tried so far, yet just to make sure, I'd like to see -
```
cat /etc/modules
cat /etc/rc.local
```


**PS:**
> **Ralph L said:**
> I ran "wireless script" that came from varunendr..Ahem.. you mean "the link that came from..", because I've done nothing in that script except writing that post on how to use it.
:P

---

### Post by Ralph L on 2012-12-02
Here is the result of what you requested.  Note that I have added items to /etc/rc.local, since I modified that in accordance with [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) on post #1, and by [http://forums.linuxmint.com/viewtopic.php?f=194&t=89323](http://forums.linuxmint.com/viewtopic.php?f=194&t=89323). Note that I also added ndiswrapper to /etc/modules.  Also, the web sites above had "modprobe -r ssb" and "modprobe -r b44" in them, before reinstalling them.  But ssb and b44 were not loaded, and this caused errors in the ndiswrapper install so I deleted them.  At any rate with all the trial and error I did, I could not get niswrapper to find any wireless sites, nor even be aware of wlan0.  Note also that I have uninstalled NetworkManager and installed wicd.  This is because I have lucid working that way and I thought I would give it a try.  I can change back, since it doesn't seem to help.

```
ralph@ralph-Presario-2100-DM728A:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
#added manually by ralph
ndiswrapper

ralph@ralph-Presario-2100-DM728A:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Added by ralph
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44

#End of added by ralph

exit 0
ralph@ralph-Presario-2100-DM728A:~$ cd /media/PresData
ralph@ralph-Presario-2100-DM728A:/media/PresData$ ./wireless_script
[sudo] password for ralph: 

*************** info trace ****************



**** uname -a ****


Linux ralph-Presario-2100-DM728A 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Subsystem: Compaq Computer Corporation Device [0e11:00e7]
	Kernel driver in use: b43-pci-bridge
--
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
	Subsystem: Hewlett-Packard Company Pavilion ze4400 builtin Network [103c:0024]
	Kernel driver in use: natsemi
	Kernel modules: natsemi


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****




**** lsmod ****


Module                  Size  Used by
b44                    31364  0 
ndiswrapper           192268  0 
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        106082  1 snd_ali5451
radeon                737891  2 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
i2c_ali15x3            12878  0 
pcmcia                 39791  0 
ttm                    65344  1 radeon
psmouse                86486  0 
drm_kms_helper         45466  1 radeon
drm                   197599  4 radeon,ttm,drm_kms_helper
snd_rawmidi            25424  1 snd_seq_midi
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
i2c_ali1535            12777  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 radeon
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
video                  19068  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  1 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
snd                    62064  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
shpchp                 32325  0 
mac_hid                13077  0 
snd_page_alloc         14108  1 snd_pcm
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
floppy                 60310  0 
natsemi                36039  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_ali               13562  3 
ssb                    50691  1 b44


**** nm-tool ****




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****




**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


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

#The following were added by ralph
blacklist b43
blacklist b43legacy
blacklist ssb


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard           Presario 2100 (DM728A)   /0024                     , BIOS KAM1.48   08/22/2003
[    1.699937] b43-pci-bridge 0000:00:09.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[    1.699997] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
[    1.700087] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    1.700094] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x01, vendor 0x4243)
[    1.700099] ssb: Core 3 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[    1.700104] ssb: Core 4 found: PCI (cc 0x804, rev 0x07, vendor 0x4243)
[    1.700111] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[    1.765102] ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
[   13.972457] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   14.129984] usbcore: registered new interface driver ndiswrapper
[   20.174543] usbcore: deregistering interface driver ndiswrapper
[   20.192640] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   20.204299] usbcore: registered new interface driver ndiswrapper
[   40.743902] type=1400 audit(1354498133.896:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1640 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


**************** done ********************



```

---

### Post by Ralph L on 2012-12-02
Ignore this post.

---

### Post by Ralph L on 2012-12-14
Hey guys and gals!!!  I'm celebrating!!!  After spending an inordinate amount of time trying to get my Compaq Presario 2100 with Broadcom 4306 REV 2 wireless working, I have SUCCEEDED!!!  And it runs FAST!!!

I followed a combination of the instructions from this web site ([http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) Post #1) and this web site ([http://ubuntuforums.org/showthread.php?t=25683&page=59](http://ubuntuforums.org/showthread.php?t=25683&page=59) Post 583). If anybody else is trying to get a Broadcom 4306 REV 2 (rev 2 is different) my advice is forget b43 and b43legacy.  As far as I can tell they just don't work on the rev 2.  Use ndiswrapper following the instructions on the sites above.  The first site will get you running unencrypted (lucid or precise) (its instructions for running encrypted are wrong for the rev 2).  The second site will get you running encrypted.  You need more and different firmware for encrypted than unencrypted.  The Dell firmware download, listed on the second site, worked on my Presario.  And you have to use bcmwl5a.inf (not bcmwl5.inf) in your ndiswrapper commands.  This brings in a number of additional firmware files for running encrypted.  Oh, and ndiswrapper works fine with network-manager and its panel applet.

I will write up a better post, when I get a chance.  I still have one rough edge.  Whenever I do a system update (Update Manager), it wipes out ndiswrapper and I have to reinstall it (sudo make install).  The wipeout is misleading, because only ndiswrapper (and not ndiswrapper-utils) gets wipe out.  All the ndiswrapper commands seem to use the utils so they still work, and lsmod still shows ndiswrapper installed, but it really isn't.  If anybody knows how to prevent ndiswrapper from being wiped out on update, I would appreciate the help.

Ralph

I did a more complete write-up on this at [http://ubuntuforums.org/showthread.php?t=2095736](http://ubuntuforums.org/showthread.php?t=2095736)

---

### Post by Bucky Ball on 2012-12-14
Please mark thread as solved to help others and create a new thread with any further issues. This will increase your chances of getting help rather than posting a new problem buried forty posts deep and with an unrelated thread title. ;)

---

### Post by Ralph L on 2012-12-18
I got everything working and I did a more complete write-up on this at [http://ubuntuforums.org/showthread.php?t=2095736](http://ubuntuforums.org/showthread.php?t=2095736)

---

