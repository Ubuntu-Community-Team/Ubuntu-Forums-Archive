---
title: "Problem with WIFI, Dell Latitude E5400"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by hato_CORP on 2010-03-19
Hi;

I have a problem with my WIFI card. Is anybody able to help? I have a Dell Latitude E5400 /Made in Ireland/. Week ago I switched to the newest Ubuntu /I am new user/. The System is great - everything is working perfect besides WIFI card.

System &#8594; Administration &#8594; Hardware Drivers /recognize TWO drivers/
* Broadcom B43 Wireless Driver /tested by Ubuntu Developers - Free/
* Broadcom STA Wireless Driver /tested by Ubuntu Developers – Proprietary/

First driver is not working.
I am not able to install the second one. There is some faulty information inside a log.
Would anybody help? Which driver will suit my WIFI card?

J.

---

### Post by bkratz on 2010-03-19
> **hato_CORP said:**
> Hi;

I have a problem with my WIFI card. Is anybody able to help? I have a Dell Latitude E5400 /Made in Ireland/. Week ago I switched to the newest Ubuntu /I am new user/. The System is great - everything is working perfect besides WIFI card.

System &#8594; Administration &#8594; Hardware Drivers /recognize TWO drivers/
* Broadcom B43 Wireless Driver /tested by Ubuntu Developers - Free/
* Broadcom STA Wireless Driver /tested by Ubuntu Developers – Proprietary/

First driver is not working.
I am not able to install the second one. There is some faulty information inside a log.
Would anybody help? Which driver will suit my WIFI card?

J.

The first thing needed is the version of the wifi card you have.
Please go to the terminal "Applications>>Accessories>>Terminal (in Ubuntu)" and enter

lspci | grep Wireless

(That is LSPCI in lowercase, W in uppercase)
if you get nothing returned just try

lspci -nn

and look through the long listing and find the network contoller and post the contents back here. It probably will say something "like  BCM43xx".

---

### Post by hato_CORP on 2010-03-19
Thx;

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by bkratz on 2010-03-19
> **hato_CORP said:**
> Thx;

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I know it says Dell mini, but these directions seem to be pretty straightforward and work for most people.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by hato_CORP on 2010-03-26
Hmm...

I followed the process.
STA driver installed, but WIFI still not working.

Also WIFI light indicator it is not on.

J.

---

### Post by chili555 on 2010-03-26
Please do:```
sudo rmmod -f dell-laptop
```Push the wireless switch and see if the light comes on. Any improvement?

If it works, we will have to tweak one file for it to be permanent.

---

### Post by bkratz on 2010-03-26
From your other thread on the same page the same advice!

[http://ubuntuforums.org/showpost.php?p=9031581&postcount=2](http://ubuntuforums.org/showpost.php?p=9031581&postcount=2)

---

### Post by hato_CORP on 2010-03-26
Still nothing.
The problem is that WIFI is still not recognized.

I installed aditional program like WIFI radar. WIFI nor recognized...

So i am still in the same point.

---

### Post by bkratz on 2010-03-26
> **hato_CORP said:**
> Still nothing.
The problem is that WIFI is still not recognized.

I installed aditional program like WIFI radar. WIFI nor recognized...

So i am still in the same point.




I think we now need to see 

```
lsmod
```


To see if both drivers are installed and are conflicting with each other.

---

### Post by Naggobot on 2010-03-26
My apologies for bumbing in with a disruptive post. I am hesitating with this since I really do not have any answers but I have a vague hope that this info might help you to find the problem ifinitesimally faster. 

I have Acer laptop with BCM4318 card and when the laptop comes out of hibernation  (not suspend) the wireless is disabled. 

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/538658](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/538658)
 
lshw -C networking returns
 *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0      


So far I have not found any way to enable the wireless from this state except rebooting. So if if you have related problem I am interested in the solution you find in this thread.


Good luck for you guys

---

### Post by hato_CORP on 2010-03-26
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59876  1 
snd_hda_intel          26920  4 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
pcmcia                 36808  0 
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wl                   1272936  0 
sdhci_pci               7100  0 
yenta_socket           24296  1 
sdhci                  17504  1 sdhci_pci
rsrc_nonstatic         11644  1 yenta_socket
led_class               4096  1 sdhci
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
lib80211                6432  1 wl
dell_wmi                2564  0 
psmouse                56500  0 
serio_raw               5280  0 
snd                    59204  20 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  7292  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
usbhid                 38208  0 
ohci1394               29900  0 
ssb                    35524  0 
ieee1394               86596  1 ohci1394
tg3                   109600  0 
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by bkratz on 2010-03-26
Well, you have the "wl" driver which is "STA" , and don't have b43 (  from the earlier posting ) so that seems ok.

Could you now post

sudo lshw -C network
iwconfig

Hopefully we will see the driver associated with the interface.

---

### Post by hato_CORP on 2010-03-26
j-station@j-station-DELL:~$ sudo lshw -C network
[sudo] password for j-station: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:21:9b:dc:3e:2f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5756m-v3.11 ip=192.168.0.10 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68f0000-f68fffff
j-station@j-station-DELL:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

j-station@j-station-DELL:~$

---

### Post by bkratz on 2010-03-26
Sorry about taking so long, but could you do a 

sudo modprobe wl

report any errors

and then

sudo iwlist scan

if this doesn't help i will have to do a little googling.

---

### Post by hato_CORP on 2010-03-26
j-station@j-station-DELL:~$ sudo modprobe wl
[sudo] password for j-station: 
j-station@j-station-DELL:~$ report any errors
No command 'report' found, did you mean:
 Command 'sreport' from package 'slurm-llnl' (universe)
report: command not found
j-station@j-station-DELL:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

j-station@j-station-DELL:~$

---

### Post by hato_CORP on 2010-03-26
Thx Mate for helping me BtW...

J.

---

### Post by bkratz on 2010-03-26
I'm sorry that middle one wasn't really a command, I just wanted to see if you saw any error messages, sorry!


This seems pretty good

[http://ubuntuforums.org/showpost.php?p=8539988&postcount=7](http://ubuntuforums.org/showpost.php?p=8539988&postcount=7)

---

### Post by hato_CORP on 2010-03-27
j-station@j-station-DELL:~$ ls /etc/modprobe.d | grep blacklist
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-local.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf

I have a problem with renaming the file. The command is not working. Are you able to advice?

---

### Post by bkratz on 2010-03-27
> **hato_CORP said:**
> j-station@j-station-DELL:~$ ls /etc/modprobe.d | grep blacklist
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-local.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf

I have a problem with renaming the file. The command is not working. Are you able to advice?




Are you referring to this?  sudo mv thefile.conf newnameofthefile.conf.backup. If so, you do realize that "thefile" and "nameofthefile" is not what you type right? What command are you trying? Assuming that you are typing in the right command are you in the right directory?   cd /etc/modprobe.d

---

### Post by hato_CORP on 2010-03-29
Hi, sorry for not a direct response.
I tried to follow all the steps. I am attaching the history. Driver still not working...

j-station@j-station-DELL:~$ sudo apt-get remove b43-fwcutter bcmwl-kernel-source ndisgtk ndiswrapper linux-backports-modules-karmic
[sudo] password for j-station: 
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Pakiet b43-fwcutter nie jest zainstalowany, wi&#281;c nie zostanie usuni&#281;ty.
Pakiet ndisgtk nie jest zainstalowany, wi&#281;c nie zostanie usuni&#281;ty.
E: Nie uda&#322;o si&#281; odnale&#378;&#263; pakietu ndiswrapper
j-station@j-station-DELL:~$ ls /etc/modprobe.d | grep blacklist
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-local.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
j-station@j-station-DELL:~$ cd /etc/modprobe.d
j-station@j-station-DELL:/etc/modprobe.d$ ls /etc/modprobe.d | grep blacklist
blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-local.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
j-station@j-station-DELL:/etc/modprobe.d$ sudo mv *bcm43.conf *newbcmof43.conf.backup
j-station@j-station-DELL:/etc/modprobe.d$ sudo apt-get install bcmwl-kernel-source
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
bcmwl-kernel-source jest ju&#380; w najnowszej wersji.
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.
j-station@j-station-DELL:/etc/modprobe.d$ sudo cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
wl
j-station@j-station-DELL:/etc/modprobe.d$ ls /etc/modules
/etc/modules
j-station@j-station-DELL:/etc/modprobe.d$ cd /etc.modules
bash: cd: /etc.modules: No such file or directory
j-station@j-station-DELL:/etc/modprobe.d$ cd /etc/modules.d
bash: cd: /etc/modules.d: No such file or directory
j-station@j-station-DELL:/etc/modprobe.d$ echo "wl" | sudo tee -a /etc/modules
wl
j-station@j-station-DELL:/etc/modprobe.d$ sudo cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wj-station@j-station-DELL:/etc/modprobe.d$ l
wl
wl
j-station@j-station-DELL:/etc/modprobe.d$

---

### Post by bkratz on 2010-03-29
For some reason it still doesn't seem to associate the STA driver with the interface, here is a really good thread where Ayuthia ( probably the best with Broadcom devices ) solves approximately the same problem giving a lot of detail. 

[http://www.uluga.ubuntuforums.org/showthread.php?t=1308533](http://www.uluga.ubuntuforums.org/showthread.php?t=1308533)

Since you also have a Broadcom ethernet device, you probably can not remove ssb like is shown in post two and would have to modify it as follows:

(sudo modprobe -r b43  wl) to prevent loss of ethernet ( if accidentally done it could easily be added be in, so don't worry!)

I also would go back and remove the second wl shown in modprobe.d, I don't know if that makes any difference other than prettiness.

---

### Post by newthingstotry on 2010-03-29
I have had similar problems with Broadcom 4312 wireless, and installed the STA driver, blacklisted b43, b43legacy, ssb, ndiswrapper and so on. 
Forgive my approach, I am a completely newbie to Ubuntu and Linux. I eventually git it to work on a consistent basis, but after a few days my wireless vanished and no matter what I tried I could not get it to come backup. I did a fresh install and tried a lot of the methods described, including that of Ayuthia's great instructions, but somehow nothing seemed to work even though it worked in the last install.
I finally gave up that method and tried ndiswrapper.  You may also try it, it worked for me, not straightaway though. From my experience I found that the ssb module was always getting loaded even though I blacklisted it.
I had to write a small script, make it executable and add it to the system startup to prevent from wireless being disabled again and again. Finally I uninstalled network manager and installed wicd from synaptic.
Now it works flawlessly without any issues.
Here is what I did:

1) Installed ndiswrapper and the GUI utility, uninstalled the bcmwl-kernel-source and bcmwl-modaliases from synaptic.
2) Downloaded and extracted the XP driver for bcm4312. I have XP as dualboot so I used winrar to extract the file and placed it in a folder.
3) Used ndiswrapper to get to the.inf file, but that did not make wireless work. I ran lsmod and found that ssb was running at startup and as mentioned blacklisting it did no work, it always started at startup.
4) Wrote a small script with the following commands by doing   [FONT=&quot]sudo gedit /etc/init.d/ndiswrapper.sh[/FONT]

    modprobe -r ssb
    modprobe -r ndiswrapper
    modprobe ndiswrapper
   
5) Saved the file. Made it executable with this :   sudo chmod +x /etc/init.d/ndiswrapper
6) To make the script run at startup : sudo update-rc.d ndiswrapper defaults 80

[FONT=Verdana]You have been following the STA driver instructions, hope it works. If not you can give 
this a try. There are much more detailed instrcutions for ndiswrapper in the forum by 
experts, who can help better. Best of luck.
[/FONT]

---

### Post by bkratz on 2010-03-29
> **newthingstotry said:**
> I have had similar problems with Broadcom 4312 wireless, and installed the STA driver, blacklisted b43, b43legacy, ssb, ndiswrapper and so on. 

    modprobe -r ssb
    modprobe -r ndiswrapper
    modprobe ndiswrapper


Please keep in mind that you have a Broadcom Ethernet controller 

product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
vendor: Broadcom Corporation

Which probably-perhaps not necessarily--requires the ssb module so if you remove it you may have to put it back in.

---

### Post by hato_CORP on 2010-04-03
Thank You very much.
Problem solved /Ayuthia solution/.

One more time BIG THANK YOU!

J.

---

### Post by bkratz on 2010-04-03
> **hato_CORP said:**
> Thank You very much.
Problem solved /Ayuthia solution/.

One more time BIG THANK YOU!

J.

Glad it helped!

---

### Post by Fatima Mohey on 2011-05-19
> **bkratz said:**
> For some reason it still doesn't seem to associate the STA driver with the interface, here is a really good thread where Ayuthia ( probably the best with Broadcom devices ) solves approximately the same problem giving a lot of detail. 

[http://www.uluga.ubuntuforums.org/showthread.php?t=1308533](http://www.uluga.ubuntuforums.org/showthread.php?t=1308533)

Since you also have a Broadcom ethernet device, you probably can not remove ssb like is shown in post two and would have to modify it as follows:

(sudo modprobe -r b43  wl) to prevent loss of ethernet ( if accidentally done it could easily be added be in, so don't worry!)

I also would go back and remove the second wl shown in modprobe.d, I don't know if that makes any difference other than prettiness.


i accidently did that, would you please tell me how to restore it... and am also still having the wireless not working problem.

Any advice?

---

