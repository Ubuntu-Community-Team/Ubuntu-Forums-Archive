---
title: "WPA - doesn't like the code :("
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by Angel44 on 2012-04-20
I decided to give ubuntu a try because I use my laptop mainly when I am traveling and it only has 1G RAM.  

I made a disk with ubuntu 11.10 and started up, a bit slow but I would imagine that is because it is running from CD.  

First thing I want to do is to go on the Internet, so I go to connect.  When I type in the password it tries to connect but doesn't. I also have the same problem on my Eee ASUS Netbook.
 
I have looked at some of the posts here and am not finding what I need.  I am not computer illiterate, I did work for the Evil empire for 7 years in Tech Support.  But have never really been a programmer (did some in University), so if someone could give me help in simple terms?
 
Appricate any help given! Gena

---

### Post by jerome1232 on 2012-04-20
Let's see what wireless chipset you are using.

open a terminal (ctrl+alt+t) and post the output of the below command. shift+ctrl+c to copy out of a terminal. When you post the output, goto advanced mode, highlight all of your output, and press the # symbol.

```
sudo lshw -C network
```

---

### Post by wildmanne39 on 2012-04-20
Hi, in my opinion it is not worth the trouble most of the time to install the wireless driver for your device while running from a cd, if it is not working when you boot the cd, because as soon as you reboot your computer you will lose the driver and need to install it again.
Thanks

---

### Post by jerome1232 on 2012-04-20
> **wildmanne39 said:**
> Hi, in my opinion it is not worth the trouble most of the time to install the wireless driver for your device while running from a cd, if it is not working when you boot the cd, because as soon as you reboot your computer you will lose the driver and need to install it again.
Thanks

It's even better to figure out if you wireless card flat out won't work or not before installing.

---

### Post by Angel44 on 2012-04-21
> **jerome1232 said:**
> It's even better to figure out if you wireless card flat out won't work or not before installing.

It works just fine under Windows Vista..... so that is not the problem.

---

### Post by Angel44 on 2012-04-21
> **jerome1232 said:**
> Let's see what wireless chipset you are using.

open a terminal (ctrl+alt+t) and post the output of the below command. shift+ctrl+c to copy out of a terminal. When you post the output, goto advanced mode, highlight all of your output, and press the # symbol.

```
sudo lshw -C network
```

*-network                
        description: Network controller  
        product: BCM4312 802.11b/g LP-PHY  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:10:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: driver=b43-pci-bridge latency=0  
        resources: irq:17 memory:e8000000-e8003fff  
   *-network  
        description: Ethernet interface  
        product: 88E8042 PCI-E Fast Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:30:00.0  
        logical name: eth0  
        version: 10  
        serial: 00:25:b3:5d:a3:04  
        capacity: 100Mbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:44 memory:e0000000-e0003fff ioport:2000(size=256)  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:25:56:9c:bc:87  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by Angel44 on 2012-04-21
> **wildmanne39 said:**
> Hi, in my opinion it is not worth the trouble most of the time to install the wireless driver for your device while running from a cd, if it is not working when you boot the cd, because as soon as you reboot your computer you will lose the driver and need to install it again.
Thanks

basically this is a 'one-time' thing, if it does what I want, then I will install it as dual-boot with Windows (but if I find I am not ever needing Windows will get rid of that too :)

---

### Post by jerome1232 on 2012-04-21
> **Angel44 said:**
> It works just fine under Windows Vista..... so that is not the problem.

You misunderstood, I wasn't referring to it being a hardware issue, I was referring to whether a good, working driver is available for Linux or not. Based on my very quick google search, the card ought to work after you install the appropriate driver.

After you install, hook up ethernet temporarily, and check under the gear icon in the top right, System Settings, Additional Drivers, it *should* list a driver for your wifi, after installing it and rebooting it *should* work.

Again this is just based on what I found with a quick google search, but I think your card will work fine.

This is where I got my information from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by praseodym on 2012-04-21
With Live-CD (and in the installed version) install the missing firmware (older version, works mostly better):
```

wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43 #unload the driver
sudo modprobe b43      #reload the driver
sudo service network-manager restart
```

---

### Post by Angel44 on 2012-04-21
> **jerome1232 said:**
> You misunderstood, I wasn't referring to it being a hardware issue, I was referring to whether a good, working driver is available for Linux or not. Based on my very quick google search, the card ought to work after you install the appropriate driver.

After you install, hook up ethernet temporarily, and check under the gear icon in the top right, System Settings, Additional Drivers, it *should* list a driver for your wifi, after installing it and rebooting it *should* work.

Again this is just based on what I found with a quick google search, but I think your card will work fine.

This is where I got my information from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I looked at things again after I read your message and I think the problem is that unless I install it, it won't see the drive.  I guess I hadn't been playing close enough attention (user error! :( ) when I activated the driver, and didn't notice it said it won't be available until I reboot and, of course, since I was running off CD, it lost the settings.  So now I am installing within Windows and we shall see what happens!   
 
I think the grey cells have gone stagnate and I need to use them more!

---

### Post by Angel44 on 2012-04-21
> **praseodym said:**
> With Live-CD (and in the installed version) install the missing firmware (older version, works mostly better):
```

wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43 #unload the driver
sudo modprobe b43      #reload the driver
sudo service network-manager restart
```

why is nothing easy?  Will try that if I need to (if I understand correctly, I should send these commands at the command prompt), but have decided it is best to install and just tried under Windows and got an error. so now have booted from the CD and installing. And hopefully all will go well..... (will create a new post if the install is a problem) :p

---

### Post by Angel44 on 2012-04-21
> **praseodym said:**
> With Live-CD (and in the installed version) install the missing firmware (older version, works mostly better):
```

wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43 #unload the driver
sudo modprobe b43      #reload the driver
sudo service network-manager restart
```

Not working :(  Have completely installed ubuntu and then activited the network driver but still didn't like the 'password'... so tried this but either grey cells are really lost or .....

---

### Post by praseodym on 2012-04-21
Your password? Or that of the wireless? How many characters does it have? At least 8 for WPA2!

---

### Post by Angel44 on 2012-04-21
> **praseodym said:**
> Your password? Or that of the wireless? How many characters does it have? At least 8 for WPA2!

I meant key, it is 16 characters using WPA - for the wireless.

---

### Post by wildmanne39 on 2012-04-21
Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

Your wireless will work with ubuntu so that is good news.
Thank you

---

### Post by Angel44 on 2012-04-21
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
michael_mic            12540  4 
arc4                   12473  2 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
hp_wmi                 13652  0 
rfcomm                 38408  0 
sparse_keymap          13658  1 hp_wmi
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
lib80211_crypt_tkip    17240  0 
uvcvideo               67271  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               85626  1 uvcvideo
wl                   2646601  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
serio_raw              12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
i915                  505108  3 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
binfmt_misc            17292  1 
drm                   192226  4 i915,drm_kms_helper
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
sky2                   49317  0 
```

am new at all of this, did I do that right? will go check the wifi after posting :)

---

### Post by Angel44 on 2012-04-21
thank you thank you thank you!!! it works!!! now I can go explore!!:biggrin:

---

