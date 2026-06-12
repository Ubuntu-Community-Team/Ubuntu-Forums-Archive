---
title: "Ralink RT5370 error with Lubuntu 12.04 kernel 3.2.0-23-generic i686"
date: 2013-07-07
forum: Networking &amp; Wireless
---

### Post by gvajpai on 2013-07-07
I am encountering trouble using Ralink USB wifi Adapter RT5370 on my IBM Thinkpad X31.

Seems that the drivers are correctly installed, however the network seems to be blocked. On querying lshw -C network, the output shows network Disabled. Have checked for any hardware switch, however there is no change. 

Please see below output of various queries.

[B]lshw -C network

[/B] *-network:1 DISABLED
       description: Wireless interface
       physical id: 4
       logical name: ra0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


[B]lsusb:
[/B]
Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

[B]lsmod:

[/B]
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
option                 25580  1 
usb_wwan               19779  1 option
usbserial              37173  4 option,usb_wwan
hw_cdc_driver          37390  0 
thinkpad_acpi          73942  0 
snd_seq_midi           13132  0 
pcmcia                 39791  0 
radeon                729591  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65344  1 radeon
snd_intel8x0           33455  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rt5370sta             607878  0 
drm_kms_helper         45466  1 radeon
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
drm                   197692  4 radeon,ttm,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87140  0 
yenta_socket           27428  0 
snd_timer              28931  2 snd_seq,snd_pcm
serio_raw              13027  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62064  10 thinkpad_acpi,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_seq,snd_seq_device,snd_pcm,snd_timer
i2c_algo_bit           13199  1 radeon
nsc_ircc               23240  0 
soundcore              14635  1 snd
irda                  185517  1 nsc_ircc
nvram                  14029  1 thinkpad_acpi
shpchp                 32325  0 
video                  19068  0 
parport_pc             32114  1 
crc_ccitt              12595  1 irda
ppdev                  12849  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  1 
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
e100                   36289  0 
crc_itu_t              12627  1 firewire_core
floppy                 60310  0 

[B]ifconfig:

[/B]eth0      Link encap:Ethernet  HWaddr 00:0d:60:80:d5:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr 00:1e:10:1f:00:01  
          inet addr:10.76.75.107  Bcast:10.76.75.111  Mask:255.255.255.248
          inet6 addr: fe80::21e:10ff:fe1f:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88392573 (88.3 MB)  TX bytes:11321076 (11.3 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:476201 (476.2 KB)  TX bytes:476201 (476.2 KB)

[B]iwconfig:

[/B]lo        no wireless extensions.


eth1      no wireless extensions.


ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


irda0     no wireless extensions.


eth0      no wireless extensions.

[B]iwlist scan:

[/B]ra0       Interface doesn't support scanning.

---

### Post by wildmanne39 on 2013-07-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by gvajpai on 2013-07-08
Dear Wild Man,

Thanks. Please see attached the file.

---

### Post by wildmanne39 on 2013-07-08
Please give me a link to where you got the wireless driver and the directions used for installing it.
Thanks

---

### Post by gvajpai on 2013-07-08
Dear Wild Man, please see link to the file

[http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5016](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5016)

After downloading and extracting, I did the usual process of 'make' and 'make install'.

---

### Post by wildmanne39 on 2013-07-08
Before you compiled the driver did you do what is in post 4 of this link?
[http://ubuntuforums.org/showthread.php?t=1800178&highlight=rt5370sta](http://ubuntuforums.org/showthread.php?t=1800178&highlight=rt5370sta)
if not uninstall the driver and make the changes then recompile the driver.
Thanks

---

### Post by gvajpai on 2013-07-08
Hey Wild Man, I recompiled the driver and installed again. I am able to connect to the wireless networks now, however the browser does not download or upload any data and it is perpetually running without any error.

I am once again running the wireless script and posting the output. Please send your comment.

Thanks once again.

---

### Post by wildmanne39 on 2013-07-08
Please go into your router and change the encryption to wpa2 AES not mixed mode if you have that option because it works best with ubuntu.
In network manager change the wireless security setting to wpa/wpa2. 

Also try channel 1 or 11.
Reboot
Thanks

---

### Post by wildmanne39 on 2013-07-08
I forgot to add this in my last post please change your wireless settings to match the screenshots.
Thanks

---

### Post by gvajpai on 2013-07-09
Dear Wild Man, I don't understand how to change router setting. I am using a public wifi with WEP encryption and key assigned to me. I tried to change settings as mentioned above, however it still remains the same. Please also elaborate channel 1 and 11 (sorry I dont know about any of it)

---

### Post by wildmanne39 on 2013-07-09
If it is a public wifi then you can not change the settings in the router.

You can still change the settings in the screenshots.

Please post the output of:
```
modinfo rt5370sta
```
Thanks

---

### Post by gvajpai on 2013-07-10
Please see output of modinfo rt5370sta

```
filename:       /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/rt5370sta.koversion:        2.5.0.1
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     9705101B3B731BF1E4DF833
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)



```

---

### Post by wildmanne39 on 2013-07-10
Hi, you have a couple of error messages, let's try to work through them.
Please post the output of:
```
 modinfo rt5370sta | grep version
```
Thanks

---

### Post by gvajpai on 2013-07-10
Please see output of : modinfo rt5370sta | grep version

```

version:        2.5.0.1srcversion:     9705101B3B731BF1E4DF833
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686
```

---

### Post by wildmanne39 on 2013-07-11
Okay the version of driver you have is older then the one I downloaded from the same site, I suggest you remove that driver and then change the config.mk file using the directions from the link I gave you earlier, then compile this one.
[ATTACH]244596[/ATTACH]
Just incase you do not know how to uninstall the old driver this is how.
```
cd path to where the driver is installed
make clean
sudo make uninstall

```
Then install the new driver, you will have to unzip it twice or at least I did, I believe because it is in the bz2 format.
Thanks

---

### Post by gvajpai on 2013-07-19
Dear Wild Man, sorry for late reply. however I am unable to find the location of driver. Can you tell me any alternate method.

Thanks Man

---

### Post by wildmanne39 on 2013-07-19
In my last post just above the code there is numbers and letters in red click on it that is the driver.
Thanks

---

### Post by gvajpai on 2013-07-20
Dear Wild Man, I have hard luck here. After re installing the driver as above, the wifi still stays the same. I am able to see wifi networks however it does not connect.
Apologies for troubling too much

---

### Post by wildmanne39 on 2013-07-20
Please show:
```
 modinfo rt5370sta | grep version
```
we are checking to see if the new driver you installed is the one that is loaded.

Also please delete the netinfo.txt from your home folder and run the script again and post the file here.
Thanks

---

### Post by praseodym on 2013-07-20
Hi,

afaik this driver doesnt work anymore with kernel 3.2 and 3.5. Add the device ID to the rt2800usb via:
```

echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "[COLOR="#FF0000"]148f 5370[/COLOR]" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -rfv rt2800usb
sudo modprobe -v rt2800usb 
```
Check your respective device IDs (in red) via
```

lsusb
```
rt5370sta need to be uninstalled as Wildman showed above

---

### Post by gvajpai on 2013-07-20
Hi, Please see output of modinfo rt5370sta | grep version
```

version:        2.5.0.3srcversion:     B5F68EDB8F10C7E19E04080
vermagic:       3.2.0-23-generic SMP mod_unload modversions 686
```

---

### Post by gvajpai on 2013-07-20
Please see attached output of wireless script

---

### Post by wildmanne39 on 2013-07-20
You have two drivers loaded, please do:
```
sudo modprobe -r rt2800usb
sudo modprobe -r rt5370sta
sudo modprobe rt5370sta
```
Thanks

---

### Post by gopi_nath_vajpai on 2013-09-20
Hey this wifi device is working now. Thank you for all the support :D

---

