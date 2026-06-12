---
title: "Buffalo WLI-UC-GN USB adapter help needed"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by hungsolo on 2010-04-24
I just purchased Buffalo Nfiniti Wireless USB Adapter (WLI-UC-GN) but  have no idea how to get it to work in Ubuntu.  My previous adapter (a  D-Link) just had to be plugged in and it was ready to go.  The WLI-UC-GN  adapter lights up (stays solid though), but no wireless networks are  found.  I believe Ubuntu sees the adapter, it just isn't working with  Ubuntu.  

I have read a few other posts but them a little confusing.  If any one  could please help me and keep it simple (I'm fairly new to Ubuntu); I  would be grateful.

By the way, I just upgraded to Ubuntu 10.04 from 9.10 last night hoping  that might help.  I am also using WICD Network Manager because I heard  it's better than the native manager.  

Thanks.

---

### Post by chili555 on 2010-04-24
Please open a terminal and do:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by hungsolo on 2010-04-24
> **chili555 said:**
> Please open a terminal and do:```
lsmod | grep -e rt2 -e rt3
dmesg | grep -e rt2 -e rt3
```Thanks.

I entered the code above and got the following:

[I]~$ lsmod | grep -e rt2 -e rt3
rt2870sta                   461811    0 

~$ dmesg | grep -e rt2 -e rt3
[  155.629921] rt2870sta: module is from the staging directory, the  quality is unknown, you have been warned.
[  155.652176] usbcore: registered new interface driver rt2870

[/I]Not sure what to do now. I've read that the following may help:

```
blacklist rt2800usb
```
in /etc/modprobe.d/blacklist.conf 

but can't get it to work

---

### Post by chili555 on 2010-04-24
How about this?```
iwconfig
```Thanks.

---

### Post by hungsolo on 2010-04-24
> **chili555 said:**
> How about this?```
iwconfig
```Thanks.

Here are the results:
[I]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]

Not sure what that all means.

---

### Post by chili555 on 2010-04-25
It means you have a working wireless interface. Please do:```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 rate auto
sudo iwlist wlan0 scan
```Thanks.

---

### Post by hungsolo on 2010-04-25
> **chili555 said:**
> It means you have a working wireless interface. Please do:```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 rate auto
sudo iwlist wlan0 scan
```Thanks.
  Here are the results:[B]

:[/B][I]**~$ sudo iwconfig wlan0 mode managed**
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Network is down.
[B]
:~$ sudo iwconfig wlan0 rate auto[/B]
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Network is down.

**:~$ sudo iwlist wlan0 scan**
wlan0     Interface doesn't support scanning : Network is down
[/I]

---

### Post by chili555 on 2010-04-25
Let's have a look at:```
dmesg | grep wlan
dmesg | grep -i rt2
ls /etc/Wireless
```Thanks.

---

### Post by hungsolo on 2010-04-25
> **chili555 said:**
> Let's have a look at:```
dmesg | grep wlan
dmesg | grep -i rt2
ls /etc/Wireless
```Thanks.

This is what I get with those commands:
[I]**:~$ dmesg | grep wlan**
[  121.317568] rtusb_disconnect: unregister_netdev(), dev->name=wlan0!
[  200.496645] rtusb_disconnect: unregister_netdev(), dev->name=wlan0!
[ 5728.877228] rtusb_disconnect: unregister_netdev(), dev->name=wlan0!
[56100.990056] rtusb_disconnect: unregister_netdev(), dev->name=wlan0!
[56151.682280] rtusb_disconnect: unregister_netdev(), dev->name=wlan0!
[B]
:~$ dmesg | grep -i rt2[/B]
[   95.649527] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   95.671003] usbcore: registered new interface driver rt2870
[B]
:~$ ls /etc/Wireless[/B]
ls: cannot access /etc/Wireless: No such file or directory
[/I]
For the last command, I've seen other posts mention /etc/modprobe.d.  Now that I think about it, that may have been to blacklist certain drivers.  Also, I have a /etc/WICD folder. Not sure if that's needed, but since I use the WICD program for my network I thought I might mention it.  

By the way, thanks for the help.  I truly appreciate it.  I'd really hate to have to go back to Windows.

---

### Post by chili555 on 2010-04-25
> I've seen other posts mention /etc/modprobe.d. Now that I think about it, that may have been to blacklist certain drivers. Oh, my! What have you done? May I see:```
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```Also, do things change if we do:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Do you currently have an ethernet connection?

---

### Post by hungsolo on 2010-04-26
> **chili555 said:**
> Oh, my! What have you done? May I see:```
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```Also, do things change if we do:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Do you currently have an ethernet connection?

Latest results:
[I]
**~$ ls /etc/modprobe.d**
alsa-base.conf               blacklist-firewire.conf            blacklist-watchdog.conf
blacklist                          blacklist-framebuffer.conf     libpisock9.conf
blacklist-ath_pci.conf     blacklist-modem.conf           ndiswrapper
blacklist.conf                  blacklist-oss.conf
[B]
~$ cat /etc/modprobe.d/blacklist[/B]
blacklist rt2800usb
[B]
~$ cat /etc/modprobe.d/blacklist.conf[/B]
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
[B]
~$ sudo ifconfig wlan0 up[/B]
wlan0: ERROR while getting interface flags: No such device

**~$ sudo iwlist wlan0 scan**
wlan0     Interface doesn't support scanning.[/I] 

Is it better to just do a clean install?  Your response makes me think something is really messed up.  A clean install is not an ideal situation for me, but would rather do that then not have wireless. 

I can't really say I've done much tinkering in Ubuntu.  I think the biggest change I made was to start using WICD.  I did use System/Administration/Windows Wireless Drivers to install a driver for a different USB adapter.  I deleted it though (through the same program).  Those are the only things I can think of that might be part of the problem.  Oh and as I mentioned before, I blacklisted *rt2800usb*, but my problem was present even before I did that.

Thanks.

---

### Post by chili555 on 2010-04-26
It is evidently a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441990)

If you want to do a reinstall, I'd try the live CD for the latest daily build for Lucid. See post #11 in the bug report:> This bug was fixed in the package linux - 2.6.32-18.27[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

If the live Cd works, then I'd just install it.

By the way, your blacklist files don't look that bad. I notice you have a ndiswrapper file. Did you try and fail with ndiswrapper?

---

### Post by hungsolo on 2010-04-26
> **chili555 said:**
> It is evidently a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441990)

If you want to do a reinstall, I'd try the live CD for the latest daily build for Lucid. See post #11 in the bug report:[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

If the live Cd works, then I'd just install it.

By the way, your blacklist files don't look that bad. I notice you have a ndiswrapper file. Did you try and fail with ndiswrapper?

I do not remember blacklisting ndiswrapper.  When I installed WICD, I did not see it any more.  I'll try the live cd and see if that helps fix the problem.  By the way, I do have an ethernet connection; you asked previously and I forgot to tell you.

I'll keep you posted.

---

### Post by hungsolo on 2010-04-26
Just checked my Linux kernel version.  It's 2.6.32.21.22.  Per the bug  the fix was released in kernel 2.6.32-18.27.

Will still try the live CD, but think it may not work.

---

### Post by chili555 on 2010-04-26
The reason I asked about the ethernet connection is that I do not believe either Wicd or Network Manager will activate wireless if you have a wired ethernet connection. I suggest you disconnect the ethernet cable and try:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```

---

### Post by hungsolo on 2010-04-26
> **chili555 said:**
> The reason I asked about the ethernet connection is that I do not believe either Wicd or Network Manager will activate wireless if you have a wired ethernet connection. I suggest you disconnect the ethernet cable and try:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```

This is what I got after unplugging the ethernet:
[B]
*~$ sudo ifconfig wlan0 up*[/B][I]
SIOCSIFFLAGS: Operation not permitted

**:~$ sudo iwlist wlan0 scan**
wlan0     Interface doesn't support scanning : Network is down

[/I]

---

### Post by hungsolo on 2010-04-28
Performed a clean install of 10.04 RC and this helped quite a bit.  However, it is not without issues.  I can now see my wireless connection but I just can't connect to it.  I've entered my password correctly and ensured the MAC ID# is in the router's MAC filter, but it just won't connect.  Should I blacklist the rt2800usb again as mentioned in another thread?  If this doesn't work, how do I un-blacklist that item?

---

### Post by chili555 on 2010-04-28
If you can see your network and it attempts to connect, I'd try removing MAC filtering for a few moments to see if things improve.

Let's see what modules are loaded:```
lsmod | grep rt2
```

---

### Post by hungsolo on 2010-04-28
> **chili555 said:**
> If you can see your network and it attempts to connect, I'd try removing MAC filtering for a few moments to see if things improve.

Let's see what modules are loaded:```
lsmod | grep rt2
```


Turning off the MAC filtering didn't help.  I got the following from the bcommand you provided:

*rt2870sta                 461811  1*

---

### Post by hungsolo on 2010-04-28
After some research, it appears that I may need to recompile the driver to use WAP.  Before I do, does this sound correct in my situation?

---

### Post by chili555 on 2010-04-29
> **hungsolo said:**
> After some research, it appears that I may need to recompile the driver to use WAP.  Before I do, does this sound correct in my situation?No.

What does this tell us?```
sudo iwlist wlan0 auth
```If it says, for example:> Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMPThen you have WPA capability.

If you do:```
sudo tail -n50 /var/log/syslog
```Can you see the place where the authentication process fails? Please post the relevant lines (probably not all 50).

---

### Post by hungsolo on 2010-04-29
Here's what I get:

```
sudo iwlist wlan0 auth
```[I]wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
        Current Drop unencrypted : no
        Current Authentication algorithm : open[/I]

Not sure if the last two lines make a difference.

```
sudo tail -n50 /var/log/syslog
```[I]Apr 29 09:00:20 ubuntu NetworkManager: <info>  (wlan0): preparing device.
Apr 29 09:00:20 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Apr 29 09:00:21 ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Apr 29 09:00:21 ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Apr 29 09:00:22 ubuntu avahi-daemon[669]: Registering new address record for fe80::224:a5ff:fe76:6248 on wlan0.*.
Apr 29 09:00:26 ubuntu kernel: [59908.948128] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 481
Apr 29 09:00:26 ubuntu wpa_supplicant[909]: No network configuration found for the current AP
Apr 29 09:00:26 ubuntu kernel: [59909.517334] DRS: unkown mode,default use 11N 1S AP 
Apr 29 09:00:26 ubuntu kernel: [59909.517348] DRS: unkown mode (SupRateLen=0, ExtRateLen=0, MCSSet[0]=0x0, MCSSet[1]=0x0)
Apr 29 09:00:26 ubuntu wpa_supplicant[909]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 29 09:00:31 ubuntu wpa_supplicant[909]: last message repeated 2 times
Apr 29 09:00:31 ubuntu kernel: [59913.992063] wlan0: no IPv6 routers present
Apr 29 09:00:32 ubuntu anacron[2429]: Anacron 2.3 started on 2010-04-29
Apr 29 09:00:32 ubuntu anacron[2429]: Normal exit (0 jobs run)[/I]


I hope these are the relevant events.

If it matters, I also get the following message (a little earlier than the ones above):

*Apr 29 09:00:20 ubuntu kernel: [59903.767799] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.dat*

---

### Post by chili555 on 2010-04-29
> If it matters, I also get the following message (a little earlier than the ones above):

Apr 29 09:00:20 ubuntu kernel: [59903.767799] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.datIt certainly matters. Let's try to fix it. Please do:```
ls /etc/Wireless
```Do you have a directory called RT3070STA? If not, let's create one:```
sudo mkdir /etc/Wireless/RT3070STA
```If you do have such a directory, just proceed to the next step.

When you did the *ls* step, did you have a directory called RT2870STA? Please do:```
cd /etc/Wireless/RT2870STA && ls
```Do you have a file called RT2870STA.dat? Let's copy it over to RT3070STA.```
sudo cp /etc/Wireless/RT2870STA/RT2870STA.dat /etc/Wireless/RT3070STA
```And let's rename it:```
sudo mv /etc/Wireless/RT3070STA/2870STA.dat /etc/Wireless/RT3070STA/RT3070STA.dat
```Then reboot and see if you can connect. If not, let's tweak a bit more.

---

### Post by hungsolo on 2010-04-29
Unfortunately, it failed.  I re-ran the following code and received:

```
sudo tail -n50 /var/log/syslog
```
[I]Apr 29 14:04:05 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'The Dominion'
Apr 29 14:04:05 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr 29 14:04:05 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Apr 29 14:04:05 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Apr 29 14:04:05 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 29 14:04:05 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 29 14:04:05 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 29 14:04:05 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Apr 29 14:04:05 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Apr 29 14:04:06 ubuntu kernel: [ 1111.582149] end_request: I/O error, dev fd0, sector 0
Apr 29 14:04:06 ubuntu kernel: [ 1111.582174] Buffer I/O error on device fd0, logical block 0
Apr 29 14:04:10 ubuntu wpa_supplicant[708]: Trying to associate with 00:1e:e5:b9:b9:2b (SSID='The Dominion' freq=2462 MHz)
Apr 29 14:04:10 ubuntu wpa_supplicant[708]: Association request to the driver failed
Apr 29 14:04:10 ubuntu kernel: [ 1114.792483] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 281
Apr 29 14:04:10 ubuntu kernel: [ 1114.795543] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
Apr 29 14:04:10 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 29 14:04:15 ubuntu wpa_supplicant[708]: Authentication with 00:1e:e5:b9:b9:2b timed out.
Apr 29 14:04:15 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Apr 29 14:04:15 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Apr 29 14:04:20 ubuntu kernel: [ 1124.645789] end_request: I/O error, dev fd0, sector 0
Apr 29 14:04:20 ubuntu kernel: [ 1124.645812] Buffer I/O error on device fd0, logical block 0
Apr 29 14:04:20 ubuntu kernel: [ 1124.812030] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 385
Apr 29 14:04:20 ubuntu wpa_supplicant[708]: Trying to associate with 00:1e:e5:b9:b9:2b (SSID='The Dominion' freq=2462 MHz)
Apr 29 14:04:20 ubuntu wpa_supplicant[708]: Association request to the driver failed
Apr 29 14:04:20 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Apr 29 14:04:20 ubuntu kernel: [ 1124.812533] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)[/I]

---

### Post by chili555 on 2010-04-29
It looks a lot closer. When you do:```
sudo gedit /etc/Wireless/RT3070STA/RT3070STA.dat
```Do these settings look correct?> CountryRegion=5
CountryRegionABand=7
CountryCode=[COLOR="Red"]??[/COLOR]
ChannelGeography=1
SSID=[COLOR="Red"]11n-AP[/COLOR]  <== "The Dominion" ??
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=[COLOR="Red"]OPEN[/COLOR]
EncrypType=[COLOR="Red"]NONE[/COLOR]
WPAPSK=[COLOR="Red"]??[/COLOR]
--- snip ---You might edit them and see if it helps us connect.

---

### Post by hungsolo on 2010-04-29
> **chili555 said:**
> It looks a lot closer. When you do:```
sudo gedit /etc/Wireless/RT3070STA/RT3070STA.dat
```Do these settings look correct?You might edit them and see if it helps us connect.

Still not working.  Here are my results:
> #The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=US
ChannelGeography=1
SSID=11n-AP
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=Not sure what is needed for WPAPSK=.  Also, my Wireless Mode = 9 (you showed 5).  My country code I added and my SSID=[COLOR=Red]11n-AP[/COLOR](same as you had); should this be changed to The Dominion?

---

### Post by chili555 on 2010-04-29
> SSID=11n-AP(same as you had); should this be changed to The Dominion?Yes, I tried to indicate that in my post above. Since the name of your network contains a space, be sure to enclose it in quotes.```
SSID="The Dominion"
```> Not sure what is needed for WPAPSK=Are you using WPA-PSK or WPA2-PSK? If so, this needs to be your actual key. Do not post it here; obscure it for the snoopy hackers:```
WPAPSK=mysecretkey
```From the README:> # 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

---

### Post by hungsolo on 2010-04-30
Changed my settings to this, but still no go:

[I]SSID="The Dominion"
NetworkType=Infra
WirelessMode=5
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
PktAggregate=0
WmmCapable=1
AckPolicy=0;0;0;0
AuthMode=WPA2PSK
EncrypType=AES
WPAPSK=***********[/I]

---

### Post by hungsolo on 2010-05-01
If it helps:

```
sudo tail -n50 /var/log/syslog
```

provides the following:
[I]
May  1 09:22:34 ubuntu NetworkManager: <info>  Config: added 'ssid' value 'The Dominion'
May  1 09:22:34 ubuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
May  1 09:22:34 ubuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
May  1 09:22:34 ubuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
May  1 09:22:34 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  1 09:22:34 ubuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
May  1 09:22:34 ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  1 09:22:34 ubuntu NetworkManager: <info>  Config: set interface ap_scan to 1
May  1 09:22:34 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May  1 09:22:37 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  1 09:22:37 ubuntu kernel: [  835.272055] wlan0: no IPv6 routers present
May  1 09:22:41 ubuntu kernel: [  839.166136] end_request: I/O error, dev fd0, sector 0
May  1 09:22:41 ubuntu kernel: [  839.166155] Buffer I/O error on device fd0, logical block 0
May  1 09:22:42 ubuntu wpa_supplicant[935]: Trying to associate with 00:1e:e5:b9:b9:2b (SSID='The Dominion' freq=2462 MHz)
May  1 09:22:42 ubuntu kernel: [  839.753876] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 592
May  1 09:22:42 ubuntu wpa_supplicant[935]: Association request to the driver failed
May  1 09:22:42 ubuntu kernel: [  839.755913] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
May  1 09:22:42 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating[/I]


As you can see, lines 5 and 6 fail as does line 16.

---

### Post by hungsolo on 2010-05-03
> **chili555 said:**
> Are you using WPA-PSK or WPA2-PSK? If so, this needs to be your actual key. Do not post it here; obscure it for the snoopy hackers:```
WPAPSK=mysecretkey
```

Does this need to be in hex?  I thought I read that somewhere, or I was just daydreaming.

---

### Post by chili555 on 2010-05-03
> **hungsolo said:**
> Does this need to be in hex?  I thought I read that somewhere, or I was just daydreaming.It needs to be whatever your actual key is. In the router, if you set the WPA-PSK password as, for example, *ilovecoldbeer*, then that's exactly what needs to be in the .dat file.

---

### Post by hungsolo on 2010-05-03
> **chili555 said:**
> It needs to be whatever your actual key is. In the router, if you set the WPA-PSK password as, for example, *ilovecoldbeer*, then that's exactly what needs to be in the .dat file.

That's what I have, so that's not the issue.  Here's several failures that I noticed the other day after looking at the log.

* ubuntu NetworkManager:  nm_setting_802_1x_get_pkcs11_engine_path: assertion  `NM_IS_SETTING_802_1X (setting)' failed*[I]

ubuntu kernel: [  839.166155] Buffer I/O error on device  fd0, logical block 0[/I]

A more complete listing is on page 3 of this thread near the bottom of the page.

---

### Post by chili555 on 2010-05-03
> Buffer I/O error on device [COLOR="Blue"]fd0[/COLOR], logical block 0This is a floppy disk error and has nothing at all to do with your wireless. Incidentally, I got floppy errors on my laptop which had no floppy at all! I amended */etc/fstab* and they stopped.> NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failedI am Googling and I suggest you do so as well.

---

### Post by hungsolo on 2010-05-24
chili555,

I tried looking up the fail message, but haven't found anything of use.  Any other options?

---

### Post by mrgoodfox on 2011-10-29
Sorry for bringing an old topic up but was this ever fixed? I have the same wireless adapter and have been struggling with ndiswrapper and other methods (unsuccessfully of course)

---

