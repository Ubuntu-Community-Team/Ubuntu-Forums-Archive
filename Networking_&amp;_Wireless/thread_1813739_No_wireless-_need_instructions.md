---
title: "No wireless- need instructions"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by mr best buy on 2011-07-28
I have had several version of Ubuntu on this  Gateway laptop (old).  I have had netbook and now I think I have the latest...Natty(something)
I have no wireless.  I went to the Software center Installed Jockey-gtk, broadcom 802.11 linex sta wireless driver, installer package for firmware for bc3 driver  source for broadcom sta wireless driver and installer package for the Bc43.  

I go to additional drivers and it list nothing.  

Please give me a link or direct me some place with the details I need

---

### Post by mr best buy on 2011-07-28
Here is more information
john@john-3018GZ:~$ dmesg | grep firm
john@john-3018GZ:~$ sudo lshw -c network
[sudo] password for john: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:e0206000-e0207fff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
       resources: memory:e0208000-e0209fff
john@john-3018GZ:~$ 


when I run  
dmesg | grep firm 
I get a blank reply

---

### Post by mr best buy on 2011-07-28
I determined I have a broadcom 4306 card.  But I do not know what to do next. Please help

---

### Post by bkratz on 2011-07-28
Here is a pretty good explanation of what is needed.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)


Just noticed from your first post you have the STA driver installed and it looks like your wired connection has been affected, we may need to look at the blacklist file. Does you wired connection work???

---

### Post by mr best buy on 2011-07-29
john@john-3018GZ:~$ ~$ lspci -vvnn | grep 14e4
~$: command not found
john@john-3018GZ:~$ lspci -vvnn | grep 14e4
02:08.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
john@john-3018GZ:~$ 
This is my result.

---

### Post by mr best buy on 2011-07-29
Supported devices

Driver - Card/Model

STA - BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, **BCM43227, **BCM43228

b43 - BCM4306/3, BCM4311, BCM4312, BCM4318, BCM4320

b43legacy - BCM4301, BCM4306, BCM4306/2 

My model is here

---

### Post by mr best buy on 2011-07-29
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/14.6 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Selecting previously deselected package b43-fwcutter.
(Reading database ... 137423 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...

---

### Post by mr best buy on 2011-07-29
next:
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,632 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package firmware-b43-installer.
(Reading database ... 137430 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Deleting old extracted firmware...
Setting up firmware-b43-installer (4.150.10.5-5) ...
--2011-07-29 16:17:46--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Resolving mirror2.openwrt.org... 46.4.11.11
Connecting to mirror2.openwrt.org|46.4.11.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-bzip2]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2'

100%[======================================>] 3,888,794   16.5K/s   in 1m 41s  

2011-07-29 16:19:30 (37.5 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
john@john-3018GZ:~$ sudo rmmod bc44

---

### Post by wildmanne39 on 2011-07-29
Hi,let us know if that worked for you if not post the results of
```
lsmod | grep b43
```
```
sudo iwlist scan
```
```
rfkill list all
```
Thank you

---

### Post by mr best buy on 2011-07-29
still no wireless

---

### Post by mr best buy on 2011-07-29
As requested:
john@john-3018GZ:~$ lsmod | grep b43
john@john-3018GZ:~$ sudo iwlist scan
[sudo] password for john: 
lo        Interface doesn't support scanning.

wlan1     Interface doesn't support scanning : Device or resource busy

john@john-3018GZ:~$ 
john@john-3018GZ:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

john@john-3018GZ:~$ rfkill list all
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
john@john-3018GZ:~$

---

### Post by chili555 on 2011-07-29
Wild Man--

Please see PM.

---

### Post by mr best buy on 2011-07-29
I am very sorry:
What is PM?
Thanks
The reply asked me to see pm.  I do not know what this means

---

### Post by chili555 on 2011-07-29
It asked the guy helping you, wildmanne39 to check *his* private messages. We are consulting as we sometimes do because two heads are better than one, especially if one is mine.

---

### Post by wildmanne39 on 2011-07-29
Hi, sorry I did not see your last post I was in the process of posting to this thread so I messed it.

Thank you Chili555.

Ok you need to remove bcmwl-kernel-source by using synaptic. 

Paste this into the terminal
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
then remove blacklist from b43 and ssb then save and close. 

Make sure you unplug your wired connection.

Then do this command
```
sudo modprobe b43
```
Now your wireless should be working.

---

### Post by bkratz on 2011-07-29
@Mr Best Buy

just got in and see you are in good hands--glad to see the blacklist info I mentioned earlier is being taken care of. Good luck!

---

### Post by mr best buy on 2011-07-29
john@john-3018GZ:~$ lsmod | grep b43
john@john-3018GZ:~$ dmesg | grep b43
john@john-3018GZ:~$ sudo cp -r ~/wireless/* /lib/firmware/
[sudo] password for john: 
john@john-3018GZ:~$ sudo cp -r ~/wireless/* /lib/firmware/
john@john-3018GZ:~$ ls /lib/firmware
2.6.38-10-generic         hp                       rt2561s.bin
2.6.38-8-generic          i2400m-fw-usb-1.4.sbcf   rt2661.bin
3com                      i2400m-fw-usb-1.5.sbcf   rt2860.bin
acenic                    i6050-fw-usb-1.5.sbcf    rt2870.bin
adaptec                   intelliport2.bin         rt3070.bin
advansys                  ipw2100-1.3.fw           rt3071.bin
agere_ap_fw.bin           ipw2100-1.3-i.fw         rt3090.bin
agere_sta_fw.bin          ipw2100-1.3-p.fw         rt73.bin
aic94xx-seq.fw            ipw2200-bss.fw           RTL8192E
ar3k                      ipw2200-ibss.fw          RTL8192SE
ar7010_1_1.fw             ipw2200-sniffer.fw       rtl_nic
ar7010.fw                 iwlwifi-1000-3.ucode     rtlwifi
ar9170-1.fw               iwlwifi-1000-5.ucode     s2250.fw
ar9170-2.fw               iwlwifi-100-5.ucode      s2250_loader.fw
ar9170.fw                 iwlwifi-3945-2.ucode     sb16
ar9271.fw                 iwlwifi-4965-2.ucode     scripts
asihpi                    iwlwifi-5000-1.ucode     slicoss
ath3k-1.fw                iwlwifi-5000-2.ucode     sun
atmel_at76c502_3com.bin   iwlwifi-5000-5.ucode     sxg
atmel_at76c502.bin        iwlwifi-5150-2.ucode     tehuti
atmel_at76c502d.bin       iwlwifi-6000-4.ucode     ti_3410.fw
atmel_at76c502e.bin       iwlwifi-6000g2a-5.ucode  ti_5052.fw
atmel_at76c504_2958.bin   iwlwifi-6000g2b-5.ucode  ti-connectivity
atmel_at76c504a_2958.bin  iwlwifi-6050-4.ucode     tigon
atmel_at76c504.bin        iwlwifi-6050-5.ucode     tlg2300_firmware.bin
atmel_at76c506.bin        kaweth                   tr_smctr.bin
atmsar11.fw               keyspan                  ttusb-budget
av7110                    keyspan_pda              ueagle-atm
b43                       korg                     usbdux
b43-all-fw.tar_.gz        lgs8g75.fw               usbduxfast_firmware.bin
b43legacy                 libertas                 usbdux_firmware.bin
bnx2                      matrox                   v4l-cx231xx-avcore-01.fw
bnx2x-e1-4.8.53.0.fw      mrvl                     v4l-cx23418-apu.fw
bnx2x-e1-5.2.13.0.fw      mts_cdma.fw              v4l-cx23418-cpu.fw
bnx2x-e1-5.2.7.0.fw       mts_edge.fw              v4l-cx23418-dig.fw
bnx2x-e1h-4.8.53.0.fw     mts_gsm.fw               v4l-cx2341x-dec.fw
bnx2x-e1h-5.2.13.0.fw     mts_mt9234mu.fw          v4l-cx2341x-enc.fw
bnx2x-e1h-5.2.7.0.fw      mts_mt9234zba.fw         v4l-cx2341x-init.mpg
brcm                      mwl8335_duplex.fw        v4l-cx23885-avcore-01.fw
carl9170-1.fw             mwl8k                    v4l-cx23885-enc.fw
cis                       myricom                  v4l-cx25840.fw
cpia2                     NPE-B                    v4l-pvrusb2-24xxx-01.fw
cxgb3                     NPE-C                    v4l-pvrusb2-29xxx-01.fw
dabusb                    ositech                  vicam
dsp56k                    phanfw.bin               vntwusb.fw
dvb-fe-xc5000-1.6.114.fw  ql2100_fw.bin            vxge
dvb-usb-dib0700-1.20.fw   ql2200_fw.bin            WHENCE.ubuntu
e100                      ql2300_fw.bin            whiteheat.fw
ea                        ql2322_fw.bin            whiteheat_loader.fw
edgeport                  ql2400_fw.bin            yam
emi26                     ql2500_fw.bin            yamaha
emi62                     qlogic                   zd1201-ap.fw
ess                       r128                     zd1201.fw
f2255usb.bin              radeon                   zd1211
GPL-3                     rt2561.bin
john@john-3018GZ:~$ cd /lib/firmware
john@john-3018GZ:/lib/firmware$ pwd
/lib/firmware
john@john-3018GZ:/lib/firmware$ sudo -s
root@john-3018GZ:/lib/firmware# sudo -s
root@john-3018GZ:/lib/firmware# tar -xzf b43-all-fw.tar_.gz
root@john-3018GZ:/lib/firmware#

---

### Post by mr best buy on 2011-07-29
I did this but do not know what it means.

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

---

### Post by nm_geo on 2011-07-29
try this one just copy and paste..

```
cat /etc/modprobe.d/* | egrep 'b43|bcm|ssb|wl'
```We are just looking to see why b43 is not taking off.. the command above searches all files in the blacklist area.
If we spot a problem we will help you fix it.  Please add 

```
lsmod
```

paste result of both in thread..

---

### Post by wildmanne39 on 2011-07-29
Hi, are you now trying to install a ralink wireless device?

---

### Post by chili555 on 2011-07-29
> **mr best buy said:**
> john@john-3018GZ:~$ lsmod | grep b43
john@john-3018GZ:~$ dmesg | grep b43
john@john-3018GZ:~$ sudo cp -r ~/wireless/* /lib/firmware/
[sudo] password for john: 
john@john-3018GZ:~$ sudo cp -r ~/wireless/* /lib/firmware/
john@john-3018GZ:~$ ls /lib/firmware
2.6.38-10-generic         hp                       rt2561s.bin
2.6.38-8-generic          i2400m-fw-usb-1.4.sbcf   rt2661.bin
3com                      i2400m-fw-usb-1.5.sbcf   rt2860.bin
acenic                    i6050-fw-usb-1.5.sbcf    rt2870.bin
adaptec                   intelliport2.bin         rt3070.bin
advansys                  ipw2100-1.3.fw           rt3071.bin
agere_ap_fw.bin           ipw2100-1.3-i.fw         rt3090.bin
agere_sta_fw.bin          ipw2100-1.3-p.fw         rt73.bin
aic94xx-seq.fw            ipw2200-bss.fw           RTL8192E
ar3k                      ipw2200-ibss.fw          RTL8192SE
ar7010_1_1.fw             ipw2200-sniffer.fw       rtl_nic
ar7010.fw                 iwlwifi-1000-3.ucode     rtlwifi
ar9170-1.fw               iwlwifi-1000-5.ucode     s2250.fw
ar9170-2.fw               iwlwifi-100-5.ucode      s2250_loader.fw
ar9170.fw                 iwlwifi-3945-2.ucode     sb16
ar9271.fw                 iwlwifi-4965-2.ucode     scripts
asihpi                    iwlwifi-5000-1.ucode     slicoss
ath3k-1.fw                iwlwifi-5000-2.ucode     sun
atmel_at76c502_3com.bin   iwlwifi-5000-5.ucode     sxg
atmel_at76c502.bin        iwlwifi-5150-2.ucode     tehuti
atmel_at76c502d.bin       iwlwifi-6000-4.ucode     ti_3410.fw
atmel_at76c502e.bin       iwlwifi-6000g2a-5.ucode  ti_5052.fw
atmel_at76c504_2958.bin   iwlwifi-6000g2b-5.ucode  ti-connectivity
atmel_at76c504a_2958.bin  iwlwifi-6050-4.ucode     tigon
atmel_at76c504.bin        iwlwifi-6050-5.ucode     tlg2300_firmware.bin
atmel_at76c506.bin        kaweth                   tr_smctr.bin
atmsar11.fw               keyspan                  ttusb-budget
av7110                    keyspan_pda              ueagle-atm
b43                       korg                     usbdux
b43-all-fw.tar_.gz        lgs8g75.fw               usbduxfast_firmware.bin
b43legacy                 libertas                 usbdux_firmware.bin
bnx2                      matrox                   v4l-cx231xx-avcore-01.fw
bnx2x-e1-4.8.53.0.fw      mrvl                     v4l-cx23418-apu.fw
bnx2x-e1-5.2.13.0.fw      mts_cdma.fw              v4l-cx23418-cpu.fw
bnx2x-e1-5.2.7.0.fw       mts_edge.fw              v4l-cx23418-dig.fw
bnx2x-e1h-4.8.53.0.fw     mts_gsm.fw               v4l-cx2341x-dec.fw
bnx2x-e1h-5.2.13.0.fw     mts_mt9234mu.fw          v4l-cx2341x-enc.fw
bnx2x-e1h-5.2.7.0.fw      mts_mt9234zba.fw         v4l-cx2341x-init.mpg
brcm                      mwl8335_duplex.fw        v4l-cx23885-avcore-01.fw
carl9170-1.fw             mwl8k                    v4l-cx23885-enc.fw
cis                       myricom                  v4l-cx25840.fw
cpia2                     NPE-B                    v4l-pvrusb2-24xxx-01.fw
cxgb3                     NPE-C                    v4l-pvrusb2-29xxx-01.fw
dabusb                    ositech                  vicam
dsp56k                    phanfw.bin               vntwusb.fw
dvb-fe-xc5000-1.6.114.fw  ql2100_fw.bin            vxge
dvb-usb-dib0700-1.20.fw   ql2200_fw.bin            WHENCE.ubuntu
e100                      ql2300_fw.bin            whiteheat.fw
ea                        ql2322_fw.bin            whiteheat_loader.fw
edgeport                  ql2400_fw.bin            yam
emi26                     ql2500_fw.bin            yamaha
emi62                     qlogic                   zd1201-ap.fw
ess                       r128                     zd1201.fw
f2255usb.bin              radeon                   zd1211
GPL-3                     rt2561.bin
john@john-3018GZ:~$ cd /lib/firmware
john@john-3018GZ:/lib/firmware$ pwd
/lib/firmware
john@john-3018GZ:/lib/firmware$ sudo -s
root@john-3018GZ:/lib/firmware# sudo -s
root@john-3018GZ:/lib/firmware# tar -xzf b43-all-fw.tar_.gz
root@john-3018GZ:/lib/firmware#We have no idea what you are trying to do here. Are you reading some other tutorial? Are you quite sure it applies to your circumstances? If you just blindly throw everything you read anywhere at the problem, you are very likely to cause more problems than you solve.

---

### Post by mr best buy on 2011-07-29
As Requested.  The wireless has worked fine until I loaded the netbook in and then I reinstalled 11.04, from usb device


john@john-3018GZ:~$ cat /etc/modprobe.d/* | egrep 'b43|bcm|ssb|wl'
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
john@john-3018GZ:~$

---

### Post by nm_geo on 2011-07-29
> **mr best buy said:**
> As Requested.  The wireless has worked fine until I loaded the netbook in and then I reinstalled 11.04, from usb device


john@john-3018GZ:~$ cat /etc/modprobe.d/* | egrep 'b43|bcm|ssb|wl'
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
[COLOR=Red]blacklist b43
blacklist ssb[/COLOR]
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
john@john-3018GZ:~$


Those are a problem... You need to find that file and remove it .. It was created by the STA driver almost/install...

you could 

```
cd /etc/modprobe.d/
ls
```Then I bet we can find that sucker.. You never answered bkratz about having ethernet lan connection but it looks like you have it at times CORRECT?

---

### Post by bkratz on 2011-07-29
@Dr Chili
Isn't this where it is blacklisted?

/etc/modprobe.d/broadcom-wl-blacklist.conf 

???

---

### Post by nm_geo on 2011-07-29
> **bkratz said:**
> @Dr Chili
Isn't this where it is blacklisted?

/etc/modprobe.d/broadcom-wl-blacklist.conf 

???

I have seen other names too.

here is one  broadcom-sta-common.conf

---

### Post by mr best buy on 2011-07-29
Is this what you wanted?

john@john-3018GZ:~$ cd /etc/modprobe.d/
john@john-3018GZ:/etc/modprobe.d$ ls
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         broadcom-sta-common.conf
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-rare-network.conf
john@john-3018GZ:/etc/modprobe.d$ 
john@john-3018GZ:/etc/modprobe.d$ ^C
john@john-3018GZ:/etc/modprobe.d$

---

### Post by nm_geo on 2011-07-29
> **mr best buy said:**
> Is this what you wanted?

john@john-3018GZ:~$ cd /etc/modprobe.d/
john@john-3018GZ:/etc/modprobe.d$ ls
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf **[COLOR=Red]        broadcom-sta-common.conf[/COLOR]**
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-rare-network.conf
john@john-3018GZ:/etc/modprobe.d$ 
john@john-3018GZ:/etc/modprobe.d$ ^C
john@john-3018GZ:/etc/modprobe.d$

Yes we need to remove that file..

be sure you are in that directory again

```
cd /etc/modprobe.d
ls
``````
sudo rm broadcom-sta-common.conf
```then maybe 

```
modprobe b43
```

---

### Post by chili555 on 2011-07-29
Guys, I think it will help if we take a look before we proceed. mr best buy, please run and post:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/broadcom-sta-common.conf
```Thanks.

---

### Post by mr best buy on 2011-07-29
john@john-3018GZ:~$ cd /etc/modprobe.d
john@john-3018GZ:/etc/modprobe.d$ ls
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         broadcom-sta-common.conf
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-rare-network.conf
john@john-3018GZ:/etc/modprobe.d$ sudo rm         broadcom-sta-common.conf
[sudo] password for john: 
john@john-3018GZ:/etc/modprobe.d$ sudo rm         broadcom-sta-common.conf
rm: cannot remove `broadcom-sta-common.conf': No such file or directory
john@john-3018GZ:/etc/modprobe.d$ modprobe b43
FATAL: Error inserting b43 (/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted
john@john-3018GZ:/etc/modprobe.d$

---

### Post by mr best buy on 2011-07-29
Ya fixed it.

Good job and thank you

---

### Post by bkratz on 2011-07-29
> **mr best buy said:**
> Ya fixed it.

Good job and thank you



Does your wired connection work now?

---

### Post by jtarin on 2011-07-29
[Here]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/") is a similar but alternate method which calls for removing SAT drivers rather than just a blacklist.

---

### Post by mr best buy on 2011-07-29
i HAVE NEVER USED A WIRED CONNECTION ON THIS COMPUTER.  WHEN THE WIRELESS WAS NOT WORKING I WAS USING A LINKSYS USB I HAVE SEVERAL LAPTOPS AND NEVER USE THE WIRED.  IF YOU WANT ME TO, I WILL CONNECT IT UP TO TOMORROW AND LET YOU KNOW.  TELL ME IF YOU WANST THE INFO

---

### Post by bkratz on 2011-07-29
> **mr best buy said:**
> i HAVE NEVER USED A WIRED CONNECTION ON THIS COMPUTER.  WHEN THE WIRELESS WAS NOT WORKING I WAS USING A LINKSYS USB I HAVE SEVERAL LAPTOPS AND NEVER USE THE WIRED.  IF YOU WANT ME TO, I WILL CONNECT IT UP TO TOMORROW AND LET YOU KNOW.  TELL ME IF YOU WANST THE INFO



No, if you are happy we are all happy, still just referring to your first post. It should work now. Congratulations on getting the wireless working! Enjoy.

Actually it was the second one where both said "unclaimed"

---

### Post by bkratz on 2011-07-29
> **jtarin said:**
> [Here]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/") is a similar but alternate method which calls for removing SAT drivers rather than just a blacklist.



Just removing the STA driver may not be enough. Once installed it usually adds blacklists for b43 and ssb somewhere. If the user has a broadcom wired device blacklisting of ssb will probably make it not work too.

---

### Post by nm_geo on 2011-07-30
> **mr best buy said:**
> i HAVE NEVER USED A WIRED CONNECTION ON THIS COMPUTER.  WHEN THE WIRELESS WAS NOT WORKING I WAS USING A LINKSYS USB I HAVE SEVERAL LAPTOPS AND NEVER USE THE WIRED.  IF YOU WANT ME TO, I WILL CONNECT IT UP TO TOMORROW AND LET YOU KNOW.  TELL ME IF YOU WANST THE INFO

 very good I see you went ahead and removed the sta blacklist file.. The  modprobe was probably not even needed reading the result.  That b43 was waiting in the gate .. Please marked Solved if you will.

---

### Post by nm_geo on 2011-07-30
> **bkratz said:**
> Just removing the STA driver may not be enough. Once installed it usually adds blacklists for b43 and ssb somewhere. If the user has a broadcom wired device blacklisting of ssb will probably make it not work too.


That the one I call the "perfect storm".. b44 for wired.. b43 for wireless and most people try that recommended STA (wl) driver and get blacklists on ssb and b43.. Makes getting connected a little more difficult..

---

### Post by nm_geo on 2011-07-30
mr best guy..

 modinfo b44
filename:       /lib/modules/2.6.32-32-generic/kernel/drivers/net/b44.ko
version:        2.0
license:        GPL
description:    Broadcom 44xx/47xx 10/100 PCI ethernet driver
author:         Felix Fietkau, Florian Schirmer, Pekka Pietikainen, David S. Miller
srcversion:     2D2A163E2FF45B9D37D09F6
alias:          pci:v000014E4d0000170Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00004402sv*sd*bc*sc*i*
[COLOR=Red]alias:          pci:v000014E4d00004401sv*sd*bc*sc*i*[/COLOR]


Hook a cable to your computer tomorrow it may make you happy..
Without doing much work at all..

---

### Post by mr best buy on 2011-07-31
New Lap the same problem
Acer Extensa 4620-4605
Installed Ubunutu 11.04.  
No wireless.
When to additional driver and it wanted me  to activate sta driver it found,   I did and it was no help.  Then I went to the next step and jnstalled a bWcutter (?) from the package manager.

Ido not know what to do next.  Could some one please walk me through the process again????

---

### Post by jtarin on 2011-07-31
> **mr best buy said:**
> New Lap the same problem
Acer Extensa 4620-4605
Installed Ubunutu 11.04.  
No wireless.
When to additional driver and it wanted me  to activate sta driver it found,   I did and it was no help.  Then I went to the next step and jnstalled a bWcutter (?) from the package manager.

Ido not know what to do next.  Could some one please walk me through the process again????
Why don't you go back through the thread step-by step and if doesn't work for you try starting another thread specifying your equipment and Ubuntu version.

---

### Post by wildmanne39 on 2011-08-01
Hi, we need to start with 
```
sudo lshw
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all

```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
binfmt_misc            13213  1 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
joydev                 17322  0 
arc4                   12473  4 
i915                  450944  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rt73usb                26854  0 
b43                   296610  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rt2x00usb              19693  1 rt73usb
acer_wmi               23123  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt2x00lib              39075  2 rt73usb,rt2x00usb
sparse_keymap          13666  1 acer_wmi
pcmcia                 39671  0 
mac80211              257001  3 rt2x00usb,rt2x00lib,b43
snd_timer              28659  2 snd_pcm,snd_seq
uvcvideo               66851  0 
cfg80211              156212  3 rt2x00lib,b43,mac80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
tifm_7xx1              12898  0 
videodev               75143  1 uvcvideo
drm_kms_helper         40745  1 i915
yenta_socket           27230  0 
serio_raw              12990  0 
drm                   180037  4 i915,drm_kms_helper
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core              15040  1 tifm_7xx1
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
ahci                   21591  2 
crc_itu_t              12627  2 rt73usb,firewire_core
sdhci                  22720  1 sdhci_pci
tg3                   131476  0 
libahci                25548  1 ahci
ssb                    45942  1 b43
john@john-Extensa-4620:~$

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-threeg: Wireless WAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
john@john-Extensa-4620:~$

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"Motorola"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:73:F7:6B:11   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24   Missed beacon:0

john@john-Extensa-4620:~$

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
john@john-Extensa-4620:~$

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ sudo lshw
[sudo] password for john: 
john-extensa-4620         
    description: Notebook
    version: 0100
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=463C1140-915D-11DC-8929-EAF1C2F22A5A
  *-core
       description: Motherboard
       product: Biwa
       vendor: Acer
       physical id: 0
       version: Rev
       serial: LXEA00X001745132FB2000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.20
          date: 09/26/2007
          size: 105KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 4MiB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:fc000000-fc0fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fc100000-fc1fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fc504800-fc504bff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:fc300000-fc303fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f6000000-f7ffffff ioport:f0000000(size=33554432)
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1d:72:0a:5f:ab
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5787m-v3.23 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:44 memory:f6000000-f600ffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f8000000-f9ffffff ioport:f2000000(size=33554432)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:f8000000-f8003fff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:fa000000-fbffffff ioport:f4000000(size=33554432)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fc504c00-fc504fff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:fc200000-fc2fffff ioport:80000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:0f:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:22 memory:fc204000-fc204fff ioport:5000(size=256) ioport:5400(size=256) memory:80000000-83ffffff memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:0f:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:22 memory:fc206000-fc2067ff memory:fc200000-fc203fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:0f:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:22 memory:fc205000-fc205fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:0f:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=57 maxlatency=4 mingnt=7
                resources: irq:22 memory:fc206800-fc2068ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AC01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:1c00(size=8) ioport:18d4(size=4) ioport:18d8(size=8) ioport:18d0(size=4) ioport:18e0(size=32) memory:fc504000-fc5047ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEKT-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXM309VE1687
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00017b3b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 2e7071b0-6651-4c76-ab07-f6a63d74a6e3
                   size: 296GiB
                   capacity: 296GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-31 21:38:29 filesystem=ext4 lastmountpoint=/ modified=2011-07-31 21:38:40 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-08-01 08:06:01 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2038MiB
                   capacity: 2038MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2038MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:84000000-840000ff ioport:1c20(size=32)
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:4c:25:6c:e7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@2:4
       logical name: wlan1
       serial: 00:14:bf:7f:6c:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-8-generic firmware=1.7 ip=192.168.0.6 link=yes multicast=yes wireless=IEEE 802.11bg
john@john-Extensa-4620:~$

---

### Post by wildmanne39 on 2011-08-01
Hi, I see a couple of issues.

1. You can only have one wireless adapter being used at a time. Which one do you want to use? the broadcom should work fine and be easy to setup.

2. Your wireless card is soft blocked.
Run this command to fix the soft block it is only good until you restart your system so if it works we will need to write a little config script.
Install the driver and firmware the the broadcom card, I see the driver but it is missing the firmware.
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
Unplug your usb adapter and restart your system then run this command.
```
sudo rmmod -f acer-wmi
```
if you do not have wireless working then run these commands please
```
lsmod | grep b43
```
```
dmesg | grep b43
```
Also I left out part of the command in the first command I gave you I am sorry about that, it is ok I do not think we need it right now.
Thank you

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:1693
14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-Extensa-4620:~$ 


Iam not sure that this is good or not

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ sudo rmmod -f acer-wmi
[sudo] password for john: 
john@john-Extensa-4620:~$ sudo rmmod -f acer-wmi
ERROR: Removing 'acer_wmi': No such file or directory
john@john-Extensa-4620:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:1693
14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-Extensa-4620:~$

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ sudo rmmod -f acer-wmi
[sudo] password for john: 
john@john-Extensa-4620:~$ sudo rmmod -f acer-wmi
ERROR: Removing 'acer_wmi': No such file or directory
john@john-Extensa-4620:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:1693
14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-Extensa-4620:~$ dmesg | grep b43
[    1.475159] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.475175] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[   11.559152] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   11.688365] Registered led device: b43-phy0::tx
[   11.688481] Registered led device: b43-phy0::rx
[   11.688594] Registered led device: b43-phy0::radio
[   11.795368] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.795374] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.795378] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
john@john-Extensa-4620:~$

---

### Post by wildmanne39 on 2011-08-01
Hi, lets try it this way open synaptic type bcm into the search window of synaptic you will see only broadcom related packages uninstall all broadcom packages then restart your computer.
Then run 
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```
and it should install fine, then restart your computer.
Thank you

---

### Post by mr best buy on 2011-08-01
john@john-Extensa-4620:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:1693
14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
john@john-Extensa-4620:~$

---

### Post by mr best buy on 2011-08-01
I make a suggest:  Is there another Ubunutu I can install?  I had an older version of unubutu on this before i put on 11.04?
I will do anything you say to do

---

### Post by chili555 on 2011-08-01
Wild Man, please see PM.

mr best buy-- wildmanne39 has a suggestion soon.

---

### Post by wildmanne39 on 2011-08-01
Hi, did you open synaptic and remove everything that was installed for the broadcom wireless card before you tried the commands I gave you to install your driver and firmware? 

It looks like it is not installing the correct firmware because you still have firmware-b43-lpphy-installer installed.

---

### Post by chili555 on 2011-08-01
Can you use this, Wild Man?

---

### Post by wildmanne39 on 2011-08-01
Hi, here are the instructions for installing chili555's script.

Down load the file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mv b43 /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Now is your wireless working?
Thank you

---

### Post by mr best buy on 2011-08-01
I installed 1010.  I was using a wireless usb adapter and during the install  I saw the system switch over to the laptop system.  it is working fine now.  Thanks for your help

---

### Post by wildmanne39 on 2011-08-01
Hi, your welcome glad you got it working.

---

### Post by mr best buy on 2011-08-01
This stuff is good but it is not absolutely perfect

---

### Post by wildmanne39 on 2011-08-01
Hi, what stuff are you talking about?

---

### Post by nm_geo on 2011-08-01
> **mr best buy said:**
> This stuff is good but it is not absolutely perfect

You are correct but IT IS FREE ...

Please run 
```

sudo lshw -C network
```

I am curious..Thanks

---

### Post by mr best buy on 2011-08-01
I am a retired computer science teacher.  In my lifetime there have been huge changes in  Operating system.  I call Operating systems, "stuff"
I like  Ubunutu over all the rest including microsoft and apple.  
I will never ever buy another HP product.  they have no reliable customer service.

---

### Post by wildmanne39 on 2011-08-01
Hi, I just finished working with another person that had the exact error message as you and chili555's script did fix it.

I am glad you like ubuntu, it is my favorite out of all the operating systems I have used.

I never boot into windows it has been about 9 months, it just upsets me every time I do.

---

### Post by mr best buy on 2011-08-03
I have this problem.  When I sign out of firefox, everything on the desk top dissappears.  I have to hit sprint screen or press power button.  Then things reappear.  What is wrong?

---

### Post by wildmanne39 on 2011-08-03
Hi, you will get more help on this topic if you start a new thread in general or absolute beginners section, with a title describing your problem,would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

