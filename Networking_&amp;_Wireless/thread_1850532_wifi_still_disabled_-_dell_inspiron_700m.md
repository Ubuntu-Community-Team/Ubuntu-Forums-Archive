---
title: "wifi still disabled - dell inspiron 700m"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by By-Tor66 on 2011-09-26
I have a Dell Inspiron 700m running Joli.  I tried the following fix which turned my wifi light on, but still no connectivity.
 
lsmod | grep dell
sudo rmmod -f dell-laptop
sudo rfkill unblock all
 
I'm new to this, so any help is appreciated.

---

### Post by chili555 on 2011-09-26
Please let us see:```
lspci -nn | grep 0280
```Thanks.

---

### Post by By-Tor66 on 2011-09-26
> **chili555 said:**
> Please let us see:```
lspci -nn | grep 0280
```Thanks.
 
02:01.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by chili555 on 2011-09-26
Can you temporarily get a wired ethernet connection and do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After a reboot, you should see networks. If not, please post back.

---

### Post by By-Tor66 on 2011-09-26
> **chili555 said:**
> Can you temporarily get a wired ethernet connection and do:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```After a reboot, you should see networks. If not, please post back.
 
will try that when I get home, I can't connect wired here at work.  thanks!

---

### Post by By-Tor66 on 2011-09-26
> **By-Tor66 said:**
> will try that when I get home, I can't connect wired here at work.  thanks!

tried it and got the following:

:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer

also my wifi light is currently off

---

### Post by bkratz on 2011-09-27
> **By-Tor66 said:**
> tried it and got the following:

:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-installer

also my wifi light is currently off



Quoted from Dr. Chili

"Can you temporarily get a[COLOR=Red] wired ethernet[/COLOR] connection and do:"

Did you have a wired connection at the time?

---

### Post by wildmanne39 on 2011-09-27
Hi, I had the same problem with my 4306 recently it is a bug that would not allow me to install the firmware here is a way around it that is a fix thanks to chili555.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, disconnect your wired connection. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run these commands one at a time, now it should come on.
Thank you

---

### Post by By-Tor66 on 2011-09-27
> **bkratz said:**
> Quoted from Dr. Chili
 
"Can you temporarily get a[COLOR=red] wired ethernet[/COLOR] connection and do:"
 
Did you have a wired connection at the time?
 
Yes I was connected via wire.  I also found out that when I cold boot into Joli the wifi light does not come on.  I have to boot into windows 7 then restart into Joli for the wifi light to stay on, but I still can't connect wirelessly.

---

### Post by By-Tor66 on 2011-09-27
> **wildmanne39 said:**
> Hi, I had the same problem with my 4306 recently it is a bug that would not allow me to install the firmware here is a way around it that is a fix thanks to chili555.
 
Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, disconnect your wired connection. 
 
Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run these commands one at a time, now it should come on.
Thank you
 
Thanks, I will try that when I can get a wired connection.  I appreciate you guys helping me out with this.

---

### Post by wildmanne39 on 2011-09-27
Hi, your welcome! that is what we are here for.

---

### Post by By-Tor66 on 2011-09-27
> **wildmanne39 said:**
> Hi, I had the same problem with my 4306 recently it is a bug that would not allow me to install the firmware here is a way around it that is a fix thanks to chili555.
 
Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here, disconnect your wired connection. 
 
Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run these commands one at a time, now it should come on.
Thank you
 
Ok, managed to get it over via thumbdrive and extracted to desktop.  Ran commands but on
 
sudo rmmod -f ssb
 
I got "Error: Removing 'ssb': Resource temporarily unavailable".

---

### Post by wildmanne39 on 2011-09-27
Hi, just drag it to the desktop from the usb drive.
Thank you

---

### Post by bkratz on 2011-09-27
@wildmanne, do you think perhaps the OP is possibly using b44 for the ethernet since it is a Dell? Might account for the 
"I got "Error: Removing 'ssb': Resource temporarily unavailable"."

---

### Post by wildmanne39 on 2011-09-27
@bkratz, you maybe right, I did not see that it was edited after my last post.

@By-Tor66 Please post the results of:
```
lsmod
```
Thank you

---

### Post by By-Tor66 on 2011-09-28
> **wildmanne39 said:**
> @bkratz, you maybe right, I did not see that it was edited after my last post.
 
@By-Tor66 Please post the results of:
```
lsmod
```
Thank you
 
Module                  Size  Used by
joydev                  7469  0 
pcmcia                 45364  0 
snd_intel8x0           22816  2 
snd_ac97_codec         87399  1 snd_intel8x0
ac97_bus                 918  1 snd_ac97_codec
snd_pcm_oss            28725  0 
snd_mixer_oss          10783  1 snd_pcm_oss
b43                   143063  0 
tifm_7xx1               4448  0 
yenta_socket           20538  0 
pcmcia_rsrc             7635  1 yenta_socket
tifm_core               5269  1 tifm_7xx1
dell_laptop             5290  0 
pcmcia_core            16397  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_pcm                58904  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
dcdbas                  6593  1 dell_laptop
snd_timer              15323  1 snd_pcm
snd_page_alloc          6328  2 snd_intel8x0,snd_pcm
shpchp                 23902  0 
psmouse                52052  0 
ppdev                   6745  0 
lp                      6452  0 
parport_pc             22692  0 
parport                27135  3 ppdev,lp,parport_pc
fbcon                  29091  71 
tileblit                1687  1 fbcon
font                    7461  1 fbcon
bitblit                 3527  1 fbcon
softcursor              1001  1 bitblit
i915                  241970  3 
drm_kms_helper         24176  1 i915
drm                   146763  3 i915,drm_kms_helper
ide_cd_mod             14018  0 
ide_gd_mod             13369  2 
ata_piix               18770  0 
ide_pci_generic         2306  0 
i2c_algo_bit            4214  1 i915
ohci1394               22762  0 
b44                    20004  0 
ieee1394               68651  1 ohci1394
intel_agp              21761  2 i915
ssb                    36035  2 b43,b44
piix                    3936  1 
agpgart                27601  2 drm,intel_agp
video                  18579  1 i915
output                  1671  1 video

---

### Post by wildmanne39 on 2011-09-28
Hi, yes kbratz was correct the ssb is also used by your ethernet connection.

Did you unplug your wired connection before you ran the commands to install the firmware?

Please post the results of these commands:
```
dmesg | egrep 'b43|firm|wlan0'
```
```
lsmod | grep b43
```
```
sudo iwlist scan
```
Thank you

---

### Post by By-Tor66 on 2011-09-28
> **wildmanne39 said:**
> Hi, yes kbratz was correct the ssb is also used by your ethernet connection.
 
Did you unplug your wired connection before you ran the commands to install the firmware?
 
Please post the results of these commands:
```
dmesg | egrep 'b43|firm|wlan0'
```
```
lsmod | grep b43
```
```
sudo iwlist scan
```
Thank you
 
Yes I was disconnected.
 
I am currently not connected when I ran the above commands.
 
[EMAIL="s@jolicloud:~$"]@jolicloud:~$[/EMAIL] dmesg | egrep 'b43|firm|wlan0'
[    1.287208] b43-pci-bridge 0000:02:01.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[   10.840528] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.892389] PM: Adding info for No Bus:wlan0
[   10.893049] PM: Adding info for No Bus:b43-phy0::tx
[   10.893062] Registered led device: b43-phy0::tx
[   10.893080] PM: Adding info for No Bus:b43-phy0::rx
[   10.893092] Registered led device: b43-phy0::rx
[   10.893111] PM: Adding info for No Bus:b43-phy0::radio
[   10.893123] Registered led device: b43-phy0::radio
[   19.957405] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   19.957410] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   19.957414] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   20.047471] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   20.047476] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   20.047480] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[EMAIL="s@jolicloud:~$"]@jolicloud:~$[/EMAIL] lsmod | grep b43
b43                   143063  0 
ssb                    36035  2 b43,b44
[EMAIL="s@jolicloud:~$"]@jolicloud:~$[/EMAIL] sudo iwlist scan
[sudo] password for : 
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Interface doesn't support scanning : Network is down

---

### Post by wildmanne39 on 2011-09-28
Hi, did you get any other errors when you extracted the file and moved it to your desktop and ran the commands?

I recommend unplug your wired connection then restart your computer then try to install the firmware again with the file you download, you do have to extract it and move it to the desktop first, if that does not work post the results of this please:
```
sudo ls /lib/firmware/b43
```
Thank you

---

### Post by By-Tor66 on 2011-09-29
> **wildmanne39 said:**
> Hi, did you get any other errors when you extracted the file and moved it to your desktop and ran the commands?

I recommend unplug your wired connection then restart your computer then try to install the firmware again with the file you download, you do have to extract it and move it to the desktop first, if that does not work post the results of this please:
```
sudo ls /lib/firmware/b43
```
Thank you

I redid the download and extracted it then moved to my desktop then reran the commands with the wire removed.  I also tried with the wire connected, same results.  there are files in the lib/firmware/b43 folder, as follows.


@jolicloud:~$ sudo ls /lib/firmware/b43
a0g0bsinitvals5.fw   a0g1initvals5.fw	  lp0bsinitvals13.fw  n0initvals11.fw
a0g0bsinitvals9.fw   a0g1initvals9.fw	  lp0bsinitvals14.fw  pcm5.fw
a0g0initvals5.fw     b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode11.fw
a0g0initvals9.fw     b0g0bsinitvals5.fw   lp0initvals13.fw    ucode13.fw
a0g1bsinitvals13.fw  b0g0bsinitvals9.fw   lp0initvals14.fw    ucode14.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw	  lp0initvals15.fw    ucode15.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw	  n0absinitvals11.fw  ucode5.fw
a0g1initvals13.fw    b0g0initvals9.fw	  n0bsinitvals11.fw   ucode9.fw

---

### Post by By-Tor66 on 2011-09-29
came into work this morning and was surprised to see that the wireless was magically working.  Thank you all for your patience and help, I really appreciate it.

---

### Post by wildmanne39 on 2011-09-29
Hi, you welcome! I am glad to hear it is working, if it continues to work would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by By-Tor66 on 2011-09-30
> **wildmanne39 said:**
> Hi, you welcome! I am glad to hear it is working, if it continues to work would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

thanks, I will do that.  It is still working great!

---

