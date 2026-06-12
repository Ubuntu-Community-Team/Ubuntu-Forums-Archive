---
title: "Broadcom WiFi Driver not listed"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by Yamipirogoeth on 2011-07-27
This is the same Compaq Presario M2000 laptop I had an issue with before, unfortunately a HDD crash forced me to reinstall Ubuntu 10.10

When I first booted into Maverick after installing I could see the Broadcom wireless driver in the additional drivers section. However, once it finished doing its needed update and needed to reboot, I only see "Software modem" listed now.

I have gone in to Synaptic and installed the following Broadcom items:

```
bcmwl-kernel-source
broadcom-sta-common
broadcom-sta-source
b43-fwcutter
bcmwl-modaliases
firmware-b43-installer
```Running iwconfig produces the following results
```

lo        no wireless extensions.

eth0      no wireless extensions.
```Running ifconfig produces the following results
```

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ea:ea:4e  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feea:ea4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11623766 (11.6 MB)  TX bytes:512944 (512.9 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```And I believe my Broadcom is a 4318 (Rev 02), at least that's what I saw after running lspci

```
sudo lspci -n | grep 14e4
05:02.0 0280: 14e4:4318 (rev 02)
```At this point nothing seems to be working to get it working, any help I would be truly grateful of!!

---

### Post by mikewhatever on 2011-07-27
You've installed too many packages. Please run the following:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source bcmwl-modaliases
```

...remove leftovers:
```
sudo apt-get --purge autoremove
```

Reboot, and it should be working.

---

### Post by Yamipirogoeth on 2011-07-28
Unfortunately my wireless card still isn't showing up in the Additional Drivers after removing all those items.

This is what I still have installed for Broadcom, viewed in Synaptic:

```
firmware-b43-installer
b43-fwcutter
```

I have rebooted and made sure to purge everything, but I'm still not getting anything on my wireless.

---

### Post by garvinrick4 on 2011-07-28
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

---

### Post by bkratz on 2011-07-28
> **Yamipirogoeth said:**
> Unfortunately my wireless card still isn't showing up in the Additional Drivers after removing all those items.

This is what I still have installed for Broadcom, viewed in Synaptic:

```
firmware-b43-installer
b43-fwcutter
```

I have rebooted and made sure to purge everything, but I'm still not getting anything on my wireless.



Those are the correct drivers for your card. Perhaps it is "hard-blocked or soft blocked".  Post the output of 

rfkill list all

---

### Post by acc61287 on 2011-07-28
what version of ubuntu your using?

---

### Post by bkratz on 2011-07-28
Also, you may want to check your blacklist file--If you activate STA originally it sometimes add b43 and ssb to the backlist file.

cat /etc/modprobe.d/blacklist.conf

---

### Post by acc61287 on 2011-07-28
I have a problem on my Ubuntu 10.10 before,I'm using Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

Try this link [http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930) or Its better to upgrade your ubuntu to 11.04

I hope It could solve your problem.

---

### Post by Yamipirogoeth on 2011-07-28
bkratz, here is the output I got from the rfkill command

```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

And this is from the blacklist command

```
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
```

acc61287 I am using Maverick Meerkat, I would love to put Narwhal on this machine, but I know it wouldn't be able to support it, so I'll stick with Meerkat for now.

Also, as a note, I did go through Synaptic and marked for deletion all the Broadcom stuff (wl and b43), rebooted and then installed only the b43 items.

Unfortunately there still is no listing of the Broadcom driver

---

### Post by mikewhatever on 2011-07-28
Can you post the outputs of the following:

```
lsmod

dpkg -l | grep -e b43 -e bcm -e broadcom

ifconfig
```

---

### Post by Yamipirogoeth on 2011-07-28
Sure, here is the ouput of lsmod

```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_atiixp_modem        9147  0 
snd_atiixp             12426  2 
joydev                  8767  0 
snd_ac97_codec         99227  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
radeon                830107  3 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 35973  0 
ttm                    56633  1 radeon
drm_kms_helper         30136  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  5223  0 
video                  18712  0 
drm                   168092  5 radeon,ttm,drm_kms_helper
output                  1883  1 video
yenta_socket           21518  0 
psmouse                59033  0 
snd                    49102  12 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 radeon
pcmcia_rsrc            10566  1 yenta_socket
serio_raw               4022  0 
ati_agp                 5202  0 
shpchp                 29886  0 
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_atiixp_modem,snd_atiixp,snd_pcm
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                  3228  0 
i2c_piix4               8635  0 
agpgart                32011  3 ttm,drm,ati_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
pata_atiixp             3288  2 
mii                     4425  2 8139too,8139cp
```The output of dpkg -l | grep -e b43 -e bcm -e broadcom

```
ii  b43-fwcutter                         1:013-2                                           Utility for extracting Broadcom 43xx firmware
rc  bcmwl-kernel-source                  5.60.48.36+bdcom-0ubuntu5                         Broadcom 802.11 Linux STA wireless driver source
rc  broadcom-sta-common                  5.60.48.36-2                                      Common files for the Broadcom STA Wireless driver
rc  firmware-b43-installer               4.150.10.5-4                                      Installer package for firmware for the b43 driver
```and the output of ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ea:ea:4e  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feea:ea4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7634896 (7.6 MB)  TX bytes:918679 (918.6 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

---

### Post by Yamipirogoeth on 2011-08-03
Is it possible to reinstall the needed drivers off the Ubuntu install disc?

If so, where would you go after booting into the disc?

---

### Post by josephmills on 2011-08-03
Hi there remove everything like mike told you too earlier then 

 
download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)



Now in  your [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it Wireless**
[IMG]http://img862.imageshack.us/img862/8053/screenshotba.png[/IMG]





Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 
[IMG]http://img850.imageshack.us/img850/4563/screenshot1kl.png[/IMG]






Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/Wireless/* /lib/firmware/
``` 
[IMG]http://img101.imageshack.us/img101/5329/screenshot5ei.png[/IMG]






Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step
[IMG]http://img151.imageshack.us/img151/5092/screenshot3ln.png[/IMG]





Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 
[IMG]http://img143.imageshack.us/img143/3945/screenshot4zv.png[/IMG]





Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ?

---

### Post by Yamipirogoeth on 2011-08-03
Unfortunately no wireless still.

One question though, was I supposed to get some sort of output when I put the following in?

```

tar -xzf b43-all-fw.tar_.gz
```

---

### Post by josephmills on 2011-08-03
> **Yamipirogoeth said:**
> Unfortunately no wireless still.

One question though, was I supposed to get some sort of output when I put the following in?

```

tar -xzf b43-all-fw.tar_.gz
```

no as long as you did it right do a ls in your firmware dir did it turn from red to green ? is not you did it wrong

---

### Post by Yamipirogoeth on 2011-08-04
I have run that command multiple times now and b43-all-fw.tar_.gz still shows up red each time I run

```
tar -xzf b43-all-fw.tar_.gz
```

---

### Post by josephmills on 2011-08-04
are you sure that you did the ```
sudo -s
``` before trying to untar ?

---

### Post by Yamipirogoeth on 2011-08-05
Yes, here is everything I've typed into terminal

```
piro@Marenslaptop:~$ ls /lib/firmware
2.6.35-22-generic         GPL-3                    rt2561.bin
2.6.35-30-generic         i2400m-fw-usb-1.4.sbcf   rt2561s.bin
3com                      i2400m-fw-usb-1.5.sbcf   rt2661.bin
acenic                    i6050-fw-usb-1.5.sbcf    rt2860.bin
adaptec                   intelliport2.bin         rt2870.bin
advansys                  ipw2100-1.3.fw           rt3070.bin
agere_ap_fw.bin           ipw2100-1.3-i.fw         rt3071.bin
agere_sta_fw.bin          ipw2100-1.3-p.fw         rt3090.bin
aic94xx-seq.fw            ipw2200-bss.fw           rt73.bin
ar7010_1_1.fw             ipw2200-ibss.fw          RTL8192E
ar9170-1.fw               ipw2200-sniffer.fw       RTL8192SE
ar9170-2.fw               iwlwifi-1000-3.ucode     RTL8192SU
ar9170.fw                 iwlwifi-3945-2.ucode     s2250.fw
ar9271.fw                 iwlwifi-4965-2.ucode     s2250_loader.fw
asihpi                    iwlwifi-5000-1.ucode     sb16
ath3k-1.fw                iwlwifi-5000-2.ucode     scripts
ath3k-2.fw                iwlwifi-5000-5.ucode     slicoss
atmel_at76c502_3com.bin   iwlwifi-5150-2.ucode     sun
atmel_at76c502.bin        iwlwifi-6000-4.ucode     sxg
atmel_at76c502d.bin       iwlwifi-6000g2a-5.ucode  tehuti
atmel_at76c502e.bin       iwlwifi-6000g2b-5.ucode  ti_3410.fw
atmel_at76c504_2958.bin   iwlwifi-6050-4.ucode     ti_5052.fw
atmel_at76c504a_2958.bin  iwlwifi-6050-5.ucode     tigon
atmel_at76c504.bin        kaweth                   tr_smctr.bin
atmel_at76c506.bin        keyspan                  ttusb-budget
atmsar11.fw               keyspan_pda              ueagle-atm
av7110                    korg                     usbdux
b43                       lgs8g75.fw               usbduxfast_firmware.bin
b43-all-fw.tar_.gz        libertas                 usbdux_firmware.bin
b43legacy                 matrox                   v4l-cx231xx-avcore-01.fw
bnx2                      mts_cdma.fw              v4l-cx23418-apu.fw
bnx2x-e1-4.8.53.0.fw      mts_edge.fw              v4l-cx23418-cpu.fw
bnx2x-e1-5.2.7.0.fw       mts_gsm.fw               v4l-cx23418-dig.fw
bnx2x-e1h-4.8.53.0.fw     mts_mt9234mu.fw          v4l-cx2341x-dec.fw
bnx2x-e1h-5.2.7.0.fw      mts_mt9234zba.fw         v4l-cx2341x-enc.fw
cis                       mwl8k                    v4l-cx2341x-init.mpg
cpia2                     myricom                  v4l-cx23885-avcore-01.fw
cxgb3                     NPE-B                    v4l-cx23885-enc.fw
dabusb                    NPE-C                    v4l-cx25840.fw
dsp56k                    ositech                  v4l-pvrusb2-24xxx-01.fw
dvb-fe-xc5000-1.6.114.fw  ql2100_fw.bin            v4l-pvrusb2-29xxx-01.fw
dvb-usb-dib0700-1.20.fw   ql2200_fw.bin            vicam
e100                      ql2300_fw.bin            whiteheat.fw
ea                        ql2322_fw.bin            whiteheat_loader.fw
edgeport                  ql2400_fw.bin            yam
emi26                     ql2500_fw.bin            yamaha
emi62                     qlogic                   zd1201-ap.fw
ess                       r128                     zd1201.fw
f2255usb.bin              radeon                   zd1211
piro@Marenslaptop:~$ cd /lib/firmware
piro@Marenslaptop:/lib/firmware$ pwd
/lib/firmware
piro@Marenslaptop:/lib/firmware$ sudo -s
[sudo] password for piro: 
root@Marenslaptop:/lib/firmware# tar -xzf b43-all-fw.tar_.gz
root@Marenslaptop:/lib/firmware#
```

And that's where it sits, and the file still shows in red no matter how many times I've run tar

---

### Post by josephmills on 2011-08-06
hi again could we see a ```
lsmod
``` and a ```
rfkill list all 
``` and a ```
lspci -nn | grep 14e4
``` thanks

---

### Post by Yamipirogoeth on 2011-08-07
Sure, here is lsmod:

```
Module                  Size  Used by
snd_seq_dummy           1350  0 
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_atiixp             12426  2 
snd_atiixp_modem        9147  0 
snd_ac97_codec         99227  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1014  1 snd_ac97_codec
radeon                830107  3 
snd_pcm                71475  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia                 35973  0 
snd_seq                47174  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30136  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
hp_wmi                  5223  0 
video                  18712  0 
psmouse                59033  0 
yenta_socket           21518  0 
i2c_algo_bit            5168  1 radeon
output                  1883  1 video
snd                    49102  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
soundcore                880  1 snd
ati_agp                 5202  0 
agpgart                32011  3 ttm,drm,ati_agp
shpchp                 29886  0 
k8temp                  3228  0 
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  3
```and from rfkill

```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```and lspci

```
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

---

### Post by pdc on 2011-08-07
incidentally:

I note 

> hp-wifi: Wireless LAN
    Soft blocked: no
    **Hard blocked: yes**

that usually means a toogle switch (for) wifi is set to OFF

is worth checking

---

### Post by Yamipirogoeth on 2011-08-07
Yeah, there's a button just above the keyboard for the wifi, I didn't realize it was hard blocking the wireless card as it doesn't light up, however, I have corrected that so that rfkill now shows that its neither soft or hard blocked.

---

### Post by Yamipirogoeth on 2011-08-16
Would it work if I untarred that file in my home directory and then moved it to where the currently tarred file is?

---

### Post by Yamipirogoeth on 2011-09-03
So I went ahead and unpacked it (seeing that I hadn't gotten a reply in 2 weeks) in the Home folder and then copied it over to /lib/firmware again and this is what I'm getting when I do "ls /lib/firmware"

```
piro@Marenslaptop:~$ ls /lib/firmware
2.6.35-22-generic         GPL-3                    rt2561.bin
2.6.35-30-generic         i2400m-fw-usb-1.4.sbcf   rt2561s.bin
3com                      i2400m-fw-usb-1.5.sbcf   rt2661.bin
acenic                    i6050-fw-usb-1.5.sbcf    rt2860.bin
adaptec                   intelliport2.bin         rt2870.bin
advansys                  ipw2100-1.3.fw           rt3070.bin
agere_ap_fw.bin           ipw2100-1.3-i.fw         rt3071.bin
agere_sta_fw.bin          ipw2100-1.3-p.fw         rt3090.bin
aic94xx-seq.fw            ipw2200-bss.fw           rt73.bin
ar7010_1_1.fw             ipw2200-ibss.fw          RTL8192E
ar9170-1.fw               ipw2200-sniffer.fw       RTL8192SE
ar9170-2.fw               iwlwifi-1000-3.ucode     RTL8192SU
ar9170.fw                 iwlwifi-3945-2.ucode     s2250.fw
ar9271.fw                 iwlwifi-4965-2.ucode     s2250_loader.fw
asihpi                    iwlwifi-5000-1.ucode     sb16
ath3k-1.fw                iwlwifi-5000-2.ucode     scripts
ath3k-2.fw                iwlwifi-5000-5.ucode     slicoss
atmel_at76c502_3com.bin   iwlwifi-5150-2.ucode     sun
atmel_at76c502.bin        iwlwifi-6000-4.ucode     sxg
atmel_at76c502d.bin       iwlwifi-6000g2a-5.ucode  tehuti
atmel_at76c502e.bin       iwlwifi-6000g2b-5.ucode  ti_3410.fw
atmel_at76c504_2958.bin   iwlwifi-6050-4.ucode     ti_5052.fw
atmel_at76c504a_2958.bin  iwlwifi-6050-5.ucode     tigon
atmel_at76c504.bin        kaweth                   tr_smctr.bin
atmel_at76c506.bin        keyspan                  ttusb-budget
atmsar11.fw               keyspan_pda              ueagle-atm
av7110                    korg                     usbdux
b43                       lgs8g75.fw               usbduxfast_firmware.bin
b43-all-fw.tar_.gz        libertas                 usbdux_firmware.bin
b43legacy                 matrox                   v4l-cx231xx-avcore-01.fw
bnx2                      mts_cdma.fw              v4l-cx23418-apu.fw
bnx2x-e1-4.8.53.0.fw      mts_edge.fw              v4l-cx23418-cpu.fw
bnx2x-e1-5.2.7.0.fw       mts_gsm.fw               v4l-cx23418-dig.fw
bnx2x-e1h-4.8.53.0.fw     mts_mt9234mu.fw          v4l-cx2341x-dec.fw
bnx2x-e1h-5.2.7.0.fw      mts_mt9234zba.fw         v4l-cx2341x-enc.fw
cis                       mwl8k                    v4l-cx2341x-init.mpg
cpia2                     myricom                  v4l-cx23885-avcore-01.fw
cxgb3                     NPE-B                    v4l-cx23885-enc.fw
dabusb                    NPE-C                    v4l-cx25840.fw
dsp56k                    ositech                  v4l-pvrusb2-24xxx-01.fw
dvb-fe-xc5000-1.6.114.fw  ql2100_fw.bin            v4l-pvrusb2-29xxx-01.fw
dvb-usb-dib0700-1.20.fw   ql2200_fw.bin            vicam
e100                      ql2300_fw.bin            whiteheat.fw
ea                        ql2322_fw.bin            whiteheat_loader.fw
edgeport                  ql2400_fw.bin            yam
emi26                     ql2500_fw.bin            yamaha
emi62                     qlogic                   zd1201-ap.fw
ess                       r128                     zd1201.fw
f2255usb.bin              radeon                   zd1211
```

So it seems that didn't do any sort of change in allowing me to get the wireless working. I did do "rfkill list" and there is no soft/hard blocks on the wireless at all.

So...I'm still at a loss for getting this laptop connected...I'm almost tempted to reinstall Ubuntu and see if that will work -_-

---

### Post by northd_tech on 2011-09-03
> **Yamipirogoeth said:**
> S **lsmod:**

```
Module                  Size  Used by
[COLOR=Magenta][...]
hp_wmi                  5223  0 [/COLOR]
video                  18712  0 
psmouse                59033  0 
yenta_socket           21518  0 
i2c_algo_bit            5168  1 radeon
output                  1883  1 video
snd                    49102  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
soundcore                880  1 snd
ati_agp                 5202  0 
agpgart                32011  3 ttm,drm,ati_agp
shpchp                 29886  0 
k8temp                  3228  0 
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  3
```and from rfkill

```
0: hp-wifi: Wireless LAN
    Soft blocked: no
  [COLOR=Red]**  Hard blocked: yes**[/COLOR]
```** lspci**
```
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:**4318**] (rev 02)
```

Aside from that "Hard blocked: yes" that someone else alredy pointed out above, I'm not seeing **any** "b43" modules in that** lsmod** output above- could you run that command again and post the results here?

I suspect you might still have a blacklist on your "b43" modules carrying over from an "old" Broadcom setup under an earlier Ubuntu version.

Can you post the results of these terminal commands [again?] when you get a chance?

```
sudo lshw -C network
lsmod
ifconfig
iwconfig
sudo iwscan list
ndiswrapper -l
nm-tool
ping -c5 www.google.com 
lsusb

```I'm hoping this long-winded terminal command will find a blacklist problem in your wireless setup:

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|rt8|ssb|witch|wl'
```

---

### Post by Yamipirogoeth on 2011-09-05
lsmod

```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_atiixp             12426  2 
snd_atiixp_modem        9147  0 
radeon                830107  3 
snd_ac97_codec         99227  2 snd_atiixp,snd_atiixp_modem
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia                 35973  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ttm                    56633  1 radeon
hp_wmi                  5223  0 
snd_timer              19067  2 snd_pcm,snd_seq
drm_kms_helper         30136  1 radeon
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
yenta_socket           21518  0 
video                  18712  0 
pcmcia_rsrc            10566  1 yenta_socket
ati_agp                 5202  0 
output                  1883  1 video
psmouse                59033  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
i2c_algo_bit            5168  1 radeon
snd                    49102  12 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 29886  0 
i2c_piix4               8635  0 
k8temp                  3228  0 
agpgart                32011  3 ttm,drm,ati_agp
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2 
```

sudo lshw -C network

```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ea:ea:4e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.10 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:c0204000-c0205fff
```ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:ea:ea:4e  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:feea:ea4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:556174 (556.1 KB)  TX bytes:94512 (94.5 KB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.
```sudo iwscan list

```
sudo: iwscan: command not found
```ndiswrapper -l

```
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

```Also, I tried running sudo apt-get to install this and it kept telling me invalid operation

nm -tool

```
nm: 'a.out': No such file
```ping -c5 [www.google.com]("http://www.google.com")

```
PING www.l.google.com (74.125.224.148) 56(84) bytes of data.
64 bytes from 74.125.224.148: icmp_req=1 ttl=56 time=40.7 ms
64 bytes from 74.125.224.148: icmp_req=2 ttl=56 time=40.6 ms
64 bytes from 74.125.224.148: icmp_req=3 ttl=56 time=52.6 ms
64 bytes from 74.125.224.148: icmp_req=4 ttl=56 time=57.2 ms
64 bytes from 74.125.224.148: icmp_req=5 ttl=56 time=153 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 20399ms
rtt min/avg/max/mdev = 40.657/68.881/153.099/42.613 ms

```lsusb

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|rt8|ssb|witch|wl'

```
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
options iwlagn 11n_disable=1
```

---

### Post by fdrake on 2011-09-05
ops it looks like was blacklisted all this time:

```

less /etc/modprobe.d/blacklist.conf | sed s/"blacklist b43"/"#blacklist b43" | tee > log
cat >> log
"blacklist wl" <enter>
<ctrl+d>
sudo mv log /etc/modprobe.d/blacklist.conf

```

---

### Post by Yamipirogoeth on 2011-09-05
When I get through the "tree > log" part I get the following output

```
sed: -e expression #1, char 30: unterminated `s' command

```

---

### Post by fdrake on 2011-09-05
my bad
```

less /etc/modprobe.d/blacklist.conf | sed s/"blacklist b43"/"#blacklist b43"[COLOR="Red"]**/**[/COLOR] | tee > log
cat >> log
"blacklist wl" <enter>
<ctrl+d>
sudo mv log /etc/modprobe.d/blacklist.conf
```

---

### Post by Yamipirogoeth on 2011-09-05
Its cool, and I put in all that code...was I supposed to get some sort of output from all that?

Of course, terminal closed when I hit ctrl+D

---

### Post by fdrake on 2011-09-05
> **Yamipirogoeth said:**
> Its cool, and I put in all that code...was I supposed to get some sort of output from all that?

Of course, terminal closed when I hit ctrl+D

no you are suposed to activated b43 driver for your card.
try to reboot ,post the results of "lsmod" if the wifi does not work .

---

### Post by Yamipirogoeth on 2011-09-05
After a reboot, I'm still not seeing anything for the broadcom wireless

Here is the lsmod output

```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_atiixp             12426  2 
radeon                830107  3 
snd_atiixp_modem        9147  0 
snd_ac97_codec         99227  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1014  1 snd_ac97_codec
joydev                  8767  0 
snd_pcm                71475  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30136  1 radeon
pcmcia                 35973  0 
hp_wmi                  5223  0 
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18712  0 
yenta_socket           21518  0 
ati_agp                 5202  0 
i2c_algo_bit            5168  1 radeon
output                  1883  1 video
psmouse                59033  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    49102  12 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
k8temp                  3228  0 
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_atiixp_modem,snd_atiixp,snd_pcm
agpgart                32011  3 ttm,drm,ati_agp
shpchp                 29886  0 
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2 
```

---

### Post by fdrake on 2011-09-06
> 
Of course, terminal closed when I hit ctrl+D
 . . . . . . . . . . . . . 

After a reboot, I'm still not seeing anything for the broadcom wireless


you probably pressed "ctrl + D" twice (1st to exit from cat, 2nd to exit from terminal). repeat again my commands and make sure you press "ctrl + D" once only. try untill you see "b43" showing up in the lsmod command. unce you see it shows up reboot to test your wifi.

---

### Post by Yamipirogoeth on 2011-09-06
I realized why it was closing, I was typing Cat >> Log too soon but I realized what I was doing there.

Now, I've typed all this in at least 7 times and still no b43 driver activated...should I just keep typing and doing those commands until it is?

Also, here's my current output of lsmod now that I've done this multiple times

```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_atiixp             12426  2 
snd_atiixp_modem        9147  0 
snd_ac97_codec         99227  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1014  1 snd_ac97_codec
radeon                830107  3 
snd_pcm                71475  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  0 
snd_seq_midi_event      6047  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30136  1 radeon
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
hp_wmi                  5223  0 
yenta_socket           21518  0 
video                  18712  0 
pcmcia_rsrc            10566  1 yenta_socket
snd                    49102  12 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
psmouse                59033  0 
ati_agp                 5202  0 
soundcore                880  1 snd
i2c_algo_bit            5168  1 radeon
serio_raw               4022  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
k8temp                  3228  0 
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,ati_agp
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2 
```

---

### Post by pdc on 2011-09-06
You do not have the b43 module installed;

you need to install the b43 module;

how do you install the b43 module?

if you read here

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and scroll down to the section that says

> Installing b43 drivers

it seems to say (as you have Maverick)

> sudo apt-get install b43-fwcutter

.........one can only suggest you do the above; *I can't find any record in this thread that you have ever done this*;**correct me if I am wrong**;

so you need to plug your system into the internet with an ethernet cable;

(as I understand you are trying to get your wireless working);

if you type

> lsmod

**AFTER** you have done the above, we would all hope fervently that you can see a b43 module

why don't you subscribe to this thread; then you get told by email when there is a reply

---

### Post by Yamipirogoeth on 2011-09-06
I've actually tried installing that a few times, and just for the sake of continuity I went ahead and tried again and terminal showed that everything was completely installed, and this is the lsmod output

```
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
snd_atiixp             12426  2 
snd_atiixp_modem        9147  0 
snd_ac97_codec         99227  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1014  1 snd_ac97_codec
radeon                830107  3 
snd_pcm                71475  3 snd_atiixp_modem,snd_atiixp,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia                 35973  0 
drm_kms_helper         30136  1 radeon
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  5223  0 
video                  18712  0 
drm                   168092  5 radeon,ttm,drm_kms_helper
yenta_socket           21518  0 
output                  1883  1 video
ati_agp                 5202  0 
pcmcia_rsrc            10566  1 yenta_socket
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    49102  12 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
serio_raw               4022  0 
k8temp                  3228  0 
i2c_algo_bit            5168  1 radeon
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
i2c_piix4               8635  0 
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,ati_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
pata_atiixp             3288  2 
mii                     4425  2 8139too,8139cp
```

---

### Post by wildmanne39 on 2011-09-06
Hi, try this please:
```
sudo rmmod -f hp-wmi
```
make sure you disconnect any other internet connections you have.
Thank you

---

### Post by nm_geo on 2011-09-06
The blacklisted b43 and ssb are not in the blacklist.conf file.. It is in another one.. can't recall the name this ought to give it.  
 
```
 
grep b43 /etc/modprobe.d/*

```

---

### Post by Yamipirogoeth on 2011-09-06
@wildmanne39 - what was that supposed to do? I ran that line after I unplugged the ethernet but still saw no change.

@nm_geo - Here is the output of that code

```
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-local.conf:blacklist b43
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43legacy
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43
```

---

### Post by wildmanne39 on 2011-09-06
Hi, it is suppose to unblock your wireless card hopefully.
Thank you

---

### Post by nm_geo on 2011-09-06
> **Yamipirogoeth said:**
> @wildmanne39 - what was that supposed to do? I ran that line after I unplugged the ethernet but still saw no change.

@nm_geo - Here is the output of that code

```
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist-local.conf:blacklist b43
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43legacy
/etc/modprobe.d/broadcom-sta-common.conf:blacklist b43
```

It appears you have two blacklist b43 problems.
We can fix those..

```
gksudo gedit /etc/modprobe.d/blacklist-local.conf
```Put a # in front of blacklist b43 and ssb if you see it

save and exit



Then lets just remove the broadcom-sta-common.conf

Gets us in the correct directory
```
cd /etc/modprobe.d
```List files in directory
```
ls
```Removes the offending file
```
sudo rm broadcom-sta-common.conf
```

Oh yeah reboot and hopefully enjoy...If not we can fix it.

---

### Post by Yamipirogoeth on 2011-09-07
@nm_geo - That worked!!! Thank you soooooo much!!!

Also, thank you to everyone who has helped me try to get this issue fixed...it's been a HUGE pain in the butt (as was the owner of the machine, lol)

---

### Post by wildmanne39 on 2011-09-07
Hi, I am very glad you got it working, enjoy.

---

