---
title: "Madwifi installation for Atheros card in Karmic koala"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by drpjkurian on 2009-11-01
Hi guys in this thread you will the instructions to install [COLOR="Red"]**Madwifi**[/COLOR] drivers for [COLOR="Red"]**Atheros**[/COLOR] wireless cards. Please follow the instructions to the word.

Open the 'terminal' by navigating through Applications-->Accessories--> Terminal

Now type the following commands in terminal

1. ```
sudo nano /etc/apt/sources.list
```

From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER"

2. ```
sudo apt-get update && sudo apt-get upgrade
```

3. ```
sudo apt-get install build-essential libssl-dev
```

4. ```
sudo apt-get install linux-headers-`uname -r`
```

5. ```
sudo apt-get install subversion
```

6. ```
sudo -i
```

7. ```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```

8. ```
cd madwifi-ng
```

9. ```
echo "" >> /etc/modprobe.d/blacklist
```

10. ```
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
```

11. ```
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
```

12. ```
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```

13. ```
make && make install
```

14. ```
echo ath_pci >> /etc/modules
```

Restart your machine.
It should work

Well i use Wicd to connect to the wireless modem
To install Wicd type the following commands in terminal
```
sudo apt-get update
```

```
sudo apt-get install wicd
```


:KS Kernal updates of your system will kill your driver. Well no need to worry about that.Just recompile your driver.
For that you open a terminal and type the command```
sudo -i
``` and just repeat the steps from No 8. Your madwifi will cone back to life again.:popcorn:

Best of Luck
Dr Kurian

---

### Post by mahaganapati on 2009-11-01
Amazing. It just worked (not that I didn't expect it to, but I've learned not to have too high hopes for these things) - and you just saved me hours of frustration. Thank you very, very much.

---

### Post by jshayden on 2009-11-01
Previously, I hadn't tried to use the SVN snapshot; I was hopeful that this would fix my problem.  However, I get the same results: it continually asks for my password.  Every now and then, it actually connects, but it is HORRIBLY slow.  It never failed me in Jaunty (or before).

Any ideas?

Thanks,
Josh

---

### Post by jshayden on 2009-11-01
I decided to give wicd a try in hopes that it would solve my problem.  It seems to get past the WPA stuff just fine.  It just sits forever at "Obtaining IP Address..."

Josh

---

### Post by mahaganapati on 2009-11-02
Try going to "preferences" and change from "madwifi" to "wext" - that has worked for me previously.

---

### Post by Prosis on 2009-11-03
After doing this, I can't even turn my wireless card on...:(

---

### Post by drpjkurian on 2009-11-03
> **jshayden said:**
> I decided to give wicd a try in hopes that it would solve my problem.  It seems to get past the WPA stuff just fine.  It just sits forever at "Obtaining IP Address..."

Josh

Hi
I think yours is not a problem of a driver.How is it after Wicd?

With regards
Dr Kurian

---

### Post by kasparillo on 2009-11-05
Hi mates!

First of all, thanks for the info. I was trying to install dis madwifi driver by my own and was going nuts! It just worked perfectly!

The problem is that now i cant connect to any network and even the signal is much slower than before. 

My question: How can i go back to my old driver? I don't really know which one i was using, but i'm running Koala on a Macbook pro 1,1, wich has an Atheros 5424.

May somebody help me please? i know i know... why i'm touching what i don't understand? I'm a geek i can not do anything else!

---

### Post by hilltop_yodeler on 2009-11-06
Thank you drpjkurian!!!  I am able to now connect to wireless networks via command line.  Neither wicd or network-manager will recognize my AR5212 Atheros wireless card, but using the command line, I can access wireless by specifying the following (as root):

```
## scan for wireless networks
$ iwlist ath0 scanning
$ iwconfig ath0 essid routerName key yourWepKey
## if you can't connect to your router, try obtaining an IP via dhcp:
$ dhclient aht0
```

Thanks again!

---

### Post by Maxepr on 2009-11-08
drpjkurian, I've had the same problem as everyone else with 9.10. My wifi is rediculesly slow. 9.04 was excellent. I was just about to go back to 9.04 when I saw the link to this thread. This is the kind of C**P that makes me nervious but I had nothing to lose anyway so I tried it. My internet is noticably faster. I have not tried it away fron home yet but I see no reason that it would be different anywhere else. Thanks for the help. My wifi is near normal now. It still amazes me that 9.10 was released with such a blatent flaw! Internet is the root of using a computer! Whoever released 9.10 too early deserves a kick in the ***! Once again, Thanks.

---

### Post by drpjkurian on 2009-11-09
> **Maxepr said:**
> drpjkurian, I've had the same problem as everyone else with 9.10. My wifi is rediculesly slow. 9.04 was excellent. I was just about to go back to 9.04 when I saw the link to this thread. This is the kind of C**P that makes me nervious but I had nothing to lose anyway so I tried it. My internet is noticably faster. I have not tried it away fron home yet but I see no reason that it would be different anywhere else. Thanks for the help. My wifi is near normal now. It still amazes me that 9.10 was released with such a blatent flaw! Internet is the root of using a computer! Whoever released 9.10 too early deserves a kick in the ***! Once again, Thanks.

Hi
That was a fine post I ever had in my thread

---

### Post by bac522 on 2009-11-17
> **Maxepr said:**
> It still amazes me that 9.10 was released with such a blatent flaw! Internet is the root of using a computer! Whoever released 9.10 too early deserves a kick in the ***! Once again, Thanks.

Actually the problem has nothing to do with Ubuntu but the Linux kernel modules themselves, can't really blame the Ubuntu team on this. 

I tried download the very latest drivers from Linux Wireless site  [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball]("http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball"), compiled them and still had a problem with the ath9k module (although it did seem to be a little bit better then the one released with 9.10). 

Still, for now, I'm going to go back to Madwifi module. Hopefully Atheros will fix the ath9k code since they are the ones who initially released the code for the ath9k module.

---

### Post by Maxepr on 2009-11-18
I stand corrected. I am still hoping for a fix soon. I prefer 9.10 over 9.04. I think it has a couple of new features that are worth the upgrade. I will continue to use the madwifi drivers. They are not perfect but they are still pretty good. Since I don't use this particular computer for gaming, I don't mind.

---

### Post by bronxbomberz41 on 2009-11-18
> **Prosis said:**
> After doing this, I can't even turn my wireless card on...:(

Same thing here.  Dr Kurian please help!  I can't even turn my wifi on now.

---

### Post by bac522 on 2009-11-18
> **Maxepr said:**
> I stand corrected. I am still hoping for a fix soon. I prefer 9.10 over 9.04. I think it has a couple of new features that are worth the upgrade. I will continue to use the madwifi drivers. They are not perfect but they are still pretty good. Since I don't use this particular computer for gaming, I don't mind.


I know it is frustrating, but it's listed as a bug with the Linux Kernel Bug tracker. For those who are interested in seeing the problems you can look at [[URL="http://bugzilla.kernel.org/buglist.cgi?quicksearch=ath9k"]http://bugzilla.kernel.org/buglist.cgi?quicksearch=ath9k]("http://bugzilla.kernel.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=&content=ath9k")[/URL] 

Also more info can be found at Linux Wireless link [http://linuxwireless.org/en/users/Drivers/ath9k/bugs]("http://linuxwireless.org/en/users/Drivers/ath9k/bugs")

I'm actually finding the latest Compat-wireless drivers to work pretty good now, I seem to get almost 25 Mbps of throughput on my wireless G network and I don't seem to be dropping connection anymore!

---

### Post by bronxbomberz41 on 2009-11-18
I don't know what I did but this doesn't work.  I can't use the external button on my laptop to turn the wireless on.  Is there a way i can at least undo what I did before?

---

### Post by xtbt on 2009-11-19
> **bac522 said:**
> Actually the problem has nothing to do with Ubuntu but the Linux kernel modules themselves, can't really blame the Ubuntu team on this. 

I tried download the very latest drivers from Linux Wireless site  [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball), compiled them and still had a problem with the ath9k module (although it did seem to be a little bit better then the one released with 9.10). 

Still, for now, I'm going to go back to Madwifi module. Hopefully Atheros will fix the ath9k code since they are the ones who initially released the code for the ath9k module.

Did Madwifi actually work for you ? Post your results so people can find solutions to the same problem.

Thanks,
X-TBT a.k.a. The Mentor.

---

### Post by bac522 on 2009-11-20
> **bronxbomberz41 said:**
> I don't know what I did but this doesn't work.  I can't use the external button on my laptop to turn the wireless on.  Is there a way i can at least undo what I did before?

Well I'm not 100% sure about this, but I believe that following file /etc/modprobe.d/blacklist-ath_pci.conf might disable your madwifi driver. Make sure this that this file doesn't exist in your /etc/modprobe.d/blacklist-ath_pci.conf. If it does just do a > sudo mv /etc/modprobe.d/blacklist-ath_pci.conf /etc/modprobe.d/blacklist-ath_pci.conf.bak  and reboot. See if that fixes the problem.

---

### Post by bac522 on 2009-11-20
> **xtbt said:**
> Did Madwifi actually work for you ? Post your results so people can find solutions to the same problem.

Thanks,
X-TBT a.k.a. The Mentor.


I'm using the the latest version of compact-wireless from [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball]("http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball") that I compiled.

After further use, I've had mixed success. Sometime they work great, sometimes they drop connection.

---

### Post by bronxbomberz41 on 2009-11-20
> **bac522 said:**
> Well I'm not 100% sure about this, but I believe that following file /etc/modprobe.d/blacklist-ath_pci.conf might disable your madwifi driver. Make sure this that this file doesn't exist in your /etc/modprobe.d/blacklist-ath_pci.conf. If it does just do a  and reboot. See if that fixes the problem.

Um..I did this but nothing happened.  Did you mean "sudo rm" instead of "sudo mv?"

I was able to open the backup file you mentioned and it says something stopping Madwifi from automatically loading by default using something called Jockey.  I'm not sure what Jockey is.

---

### Post by bac522 on 2009-11-20
> **bronxbomberz41 said:**
> Um..I did this but nothing happened.  Did you mean "sudo rm" instead of "sudo mv?"


You can try "sudo rm" if that doesn't work I suggest reloading the compact-wireless drivers back on. Of course you'll need internet connectivity to get those drivers, then follow the following steps:

Open up a shell and create a working directory:
```
mkdir wireless
```
```
cd wireless
```

Next download (what I found to work) a version of the compact-wireless drivers
```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/10/compat-wireless-2009-10-15.tar.bz2
```

Uncompress and extract the files
```
bunzip2 ./compat-wireless-2009-10-15.tar.bz2
```
```

tar xvf ./compat-wireless-2009-10-15.tar
```
Change into the directory and build the drivers.
```
cd ./compat-wireless-2009-10-15/
```
```
./scripts/driver-select ath
```
```
make
```

Now install the drivers (don't worry about the initial warning message
```
make install
```

Now remove the blacklist entry that was created intially
```
sudo nano /etc/modprobe.d/blacklist
``` 

Thats it. Rather then doing a "make unload" I would suggest just rebooting. Barring everything worked okay your wireless should be working with the ath9k driver.

---

### Post by bronxbomberz41 on 2009-11-21
> Now remove the blacklist entry that was created intially
Code:

sudo nano /etc/modprobe.d/blacklist

Thats it. Rather then doing a "make unload" I would suggest just rebooting. Barring everything worked okay your wireless should be working with the ath9k driver.

When running this this is what i have.  

```
#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k

blacklist ath9k
blacklist ath5k

```

Should I delete those completely or is there something else I should do to remove those blacklists?  So far this worked pretty well actually and I'm optimistic that this will work.

---

### Post by bac522 on 2009-11-21
> **bronxbomberz41 said:**
> When running this this is what i have.  

```
#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k

blacklist ath9k
blacklist ath5k

```

Should I delete those completely or is there something else I should do to remove those blacklists?  So far this worked pretty well actually and I'm optimistic that this will work.

Yup...whack them or just delete the entire file. Bascially a blacklist tells Linux to not load those drivers even though it thinks it should.

One thing I notice is that the rev of the driver (oct-15) seems to work only at 802.11b speeds, but for now that's works for me. I suspect the developers working on the driver will resolve the issue in the next few weeks. You can pretty much follow these steps for other drivers from other dates...mileage will vary though.

For example, I found the drivers date Nov 19th didn't work at all.

---

### Post by bronxbomberz41 on 2009-11-21
mrh...It didn't work.  I'm not sure what to do.

---

### Post by bac522 on 2009-11-21
> **bronxbomberz41 said:**
> mrh...It didn't work.  I'm not sure what to do.


What does it show when you do a "lsmod"

Also show a print out of "lspci"

Try removing and reinstall the drivers:

```
modprobe -r ath9k
modprobe ath9k
```

And what does it show when you do a "iwconfig"

---

### Post by xtbt on 2009-11-21
bronxbomberz41:

   Did you already tried intstalling the linux-backports-modules-karmic from the repos? I fixed my ath9k issues with them.

Just go to synaptics and search for the package. Give it a try, you don't have nothing to loose.

Good luck,
X-TBT a.k.a. The Mentor.

---

### Post by bronxbomberz41 on 2009-11-21
lsmod output

```
^_^[brian@brian-laptop:~]$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26984  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_hwdep               7200  1 snd_hda_codec
snd_pcm                75488  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
ath5k                 122404  0 
mac80211              210504  1 ath5k
ath                     8444  1 ath5k
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              130536  3 ath5k,mac80211,ath
iptable_filter          3100  0 
uvcvideo               59112  0 
joydev                 10272  0 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               11228  0 
videodev               36736  1 uvcvideo
soundcore               7264  1 snd
ip_tables              11692  1 iptable_filter
sdhci_pci               7132  0 
psmouse                56180  0 
lis3lv02d               7452  1 hp_accel
jmb38x_ms               9696  0 
v4l1_compat            14496  2 uvcvideo,videodev
i2c_piix4              10124  0 
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
shpchp                 32336  0 
sdhci                  17632  1 sdhci_pci
lirc_ene0100            8192  0 
lp                      8964  0 
x_tables               16544  1 ip_tables
serio_raw               5280  0 
input_polldev           3716  1 lis3lv02d
lirc_dev               10804  1 lirc_ene0100
memstick               10104  1 jmb38x_ms
ndiswrapper           185564  0 
led_class               4096  3 ath5k,hp_accel,sdhci
parport                35340  2 ppdev,lp
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
video                  19380  0 
output                  2780  1 video
r8169                  32352  0 
mii                     5212  1 r8169

```

lspci output

```
O_O[brian@brian-laptop:~]$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

I tried installing those karmic backports and still no luck at first....but then I did iwconfig and saw that a wlan0 output was there...I had done this before and saw nothing for wlan0.  I was able to then turn on my wireless!  Thanks for all your help guys.

---

### Post by bac522 on 2009-11-21
> **bronxbomberz41 said:**
> 
I tried installing those karmic backports and still no luck at first....but then I did iwconfig and saw that a wlan0 output was there...I had done this before and saw nothing for wlan0.  I was able to then turn on my wireless!  Thanks for all your help guys.

So are you able to connected now? Man...don't know why your machine is being so temperamental.

---

### Post by xtbt on 2009-11-21
> **bronxbomberz41 said:**
> I tried installing those karmic backports and still no luck at first....but then I did iwconfig and saw that a wlan0 output was there...I had done this before and saw nothing for wlan0.  I was able to then turn on my wireless!  Thanks for all your help guys.

Nice to hear it my friend. It would be great if you can post the actions taken after installing the linux-backports-modules-karmic package. It could be helpful for other users as well.

Hopefully,
X-TBT a.k.a. The Mentor.

---

### Post by tjmcwiz on 2009-11-28
I tried the early recommendation with madwifi and wicd but the approach won't work for me. It now sees the network (couldn't before) but the approach is unsuccessful in obtaining an IP address. I will try the back porting approach and see if that works.... 

It will be interesting if they can fix the root problem of all this. It use to work underneath 9.04 but it's broken but good now underneath 9.10.....

Just an update --- I was able to get it working by compiling in madwifi. I needed to use the version that was listed at their web site based upon my kernel level

madwifi version: madwifi-0.9.4-r4100-20090929
linux version: 2.6.31-16-generic
wireless card: description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7f00000-f7f0ffff

---

### Post by gooberguy on 2009-11-29
followed these instructions in hopes of getting my very slow wifi quicker (atheros 5001) but to no luck. the top right does not even show the network notification, and my wifi is not present, only works wired now.

---

### Post by lbirunner on 2009-12-04
Your instructions were very good but I think my install (Ubuntu 9.10 Karmic) might be slightly different than yours. I'm seeing some issues with the contents of /etc/modprobe.d. See WARNING from 'modprobe' below.

**And the first line in /etc/apt/sources.list is:**
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
So I didn't uncomment that line. If I do, I get an error.

**Otherwise, I followed the instructions to the letter, but am not able to load the driver.**
- reboot didn't work
- "sudo modprobe ath_pci" gives:
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ath_pci not found.

**uname -r gives:**
2.6.31-15-generic-pae

**Contents of  /lib/modules/2.6.31-15-generic-pae:**
-rw-r--r-- 1 root 400321 2009-12-04 11:30 ath_hal.ko
-rw-r--r-- 1 root 266727 2009-12-04 11:30 ath_pci.ko
-rw-r--r-- 1 root  10288 2009-12-04 11:30 ath_rate_amrr.ko
-rw-r--r-- 1 root  20102 2009-12-04 11:30 ath_rate_minstrel.ko
-rw-r--r-- 1 root   9627 2009-12-04 11:30 ath_rate_onoe.ko
-rw-r--r-- 1 root  16929 2009-12-04 11:30 ath_rate_sample.ko
-rw-r--r-- 1 root   8153 2009-12-04 11:30 wlan_acl.ko
-rw-r--r-- 1 root  11037 2009-12-04 11:30 wlan_ccmp.ko
-rw-r--r-- 1 root 269962 2009-12-04 11:30 wlan.ko
-rw-r--r-- 1 root  14349 2009-12-04 11:30 wlan_scan_ap.ko
-rw-r--r-- 1 root  19108 2009-12-04 11:30 wlan_scan_sta.ko
-rw-r--r-- 1 root  15508 2009-12-04 11:30 wlan_tkip.ko
-rw-r--r-- 1 root   9442 2009-12-04 11:30 wlan_wep.ko
-rw-r--r-- 1 root   3065 2009-12-04 11:30 wlan_xauth.ko


**Here's the output from 'lspci'. You can see my Atheros AR5001X 3rd from the bottom (I use it for Wireshark captures, it's a AIR-CB21AG-A-K9 Aironet card):**
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
04:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

**If I use insmod on the 3 drivers: **
   insmod /lib/modules/2.6.31-15-generic-pae/net/ath_hal.ko
   insmod /lib/modules/2.6.31-15-generic-pae/net/wlan.ko
   insmod /lib/modules/2.6.31-15-generic-pae/net/ath_pci.ko
They appear to load ok but I'm missing something. I'm unable to get the interface (ath0) to show up.

Any help would be greatly appreciated. I have to leave for German Monday morning to troubleshoot some wireless issues with a customer and I would rather not revert back to 8.04.

Thanks,
Mike.

---

### Post by Lucretia9 on 2009-12-05
I upgraded and yet again, my wireless broke. every time I upgrade this happens, only this time, no madwifi. Why use a kernel with broken drivers and not give a madwifi deb as a backup?

Anyway, here's the relevant output from lspci -vvnn:

```

04:01.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
        Subsystem: Netgear Device [1385:5a00]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 96 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at ff9f0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath_pci
        Kernel modules: ath_pci, ath5k

```

The card is a Netgear WG311T.

Thanks for the fix.

Luke.

---

### Post by tulpie on 2009-12-06
I just have do the instruction of Post #1
And the network-manager had displayed about a wirless adapter.

> sudo modprobe ath_pci

and the new driver appear in network-manger with adaper.

> ifconfig 

display even wifi0

thanks (i don't know if ath_pci is the right driver, because after reboot i have compiled another madwifi, i think the free driver :D)

thanks (perhaps i shout write, that in mashine is AR5008X Chip)

---

### Post by n3had on 2009-12-06
i've followed the insturctions and after reboot still no icon in network manager 

```
Bus 001 Device 003: ID 2001:3a03 D-Link Corp. [hex] DWL-G132 (no firmware)

```

P.S. I haven't installed wicd

---

### Post by carsonrose on 2009-12-07
> **drpjkurian said:**
> Hi guys in this thread you will the instructions to install [COLOR=Red]**Madwifi**[/COLOR] drivers for [COLOR=Red]**Atheros**[/COLOR] wireless cards. Please follow the instructions to the word.

Open the 'terminal' by navigating through Applications-->Accessories--> Terminal

Now type the following commands in terminal

1. ```
sudo nano /etc/apt/sources.list
```From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER"

2. ```
sudo apt-get update && sudo apt-get upgrade
```3. ```
sudo apt-get install build-essential libssl-dev
```4. ```
sudo apt-get install linux-headers-`uname -r`
```5. ```
sudo apt-get install subversion
```6. ```
sudo -i
```7. ```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```8. ```
cd madwifi-ng
```9. ```
echo "" >> /etc/modprobe.d/blacklist
```10. ```
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
```11. ```
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
```12. ```
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```13. ```
make && make install
```14. ```
echo ath_pci >> /etc/modules
```Restart your machine.
It should work

Well i use Wicd to connect to the wireless modem
To install Wicd type the following commands in terminal
```
sudo apt-get update
``````
sudo apt-get install wicd
```
:KS Kernal updates of your system will kill your driver. Well no need to worry about that.Just recompile your driver.
For that you open a terminal and type the command```
sudo -i
``` and just repeat the steps from No 8. Your madwifi will cone back to life again.:popcorn:

Best of Luck
Dr Kurian

I am a total noob to Ubuntu..... My server runs CENTOS 5.3 with OSDial running w/Asterisk... I was thrown into the linux world, AGAINST MY WILL!! 

That being said, I decided if I was going to be stuck dealing with it, I might as well learn it, right? So I installed Ubuntu on one machine, Fedora on another, CentOS on one and openSUSE on yet another one....

Well, I have been pleasently surprised by Ubuntu. This was back in June of this year and I am now about ready to dump windows altogether!

The only issue I had was this wireless issue, which is now fixed thanks to this post!

Cheers!!

Doug Bradshaw
Carson Rose & Associates, Inc.
(214) 306-6528

---

### Post by drpjkurian on 2009-12-07
Hi Guys
Thank you very much for your compliments.

Dr Kurian
:p

---

### Post by tetebueno on 2009-12-12
I have an Acer 5570z with an Atheros AR5001 wireless card and latest Karmic and steps 1-14 of the 1st post worked great. I tried this after plenty of brainiacs suggested tons of other stuff. Thanks a lot.

---

### Post by drpjkurian on 2009-12-12
> **tetebueno said:**
> I have an Acer 5570z with an Atheros AR5001 wireless card and latest Karmic and steps 1-14 of the 1st post worked great. I tried this after plenty of brainiacs suggested tons of other stuff. Thanks a lot.

Hi

Thank you very much for your compliments

With regards
Dr Kurian

---

### Post by coxne on 2009-12-13
I followed the instructions as you posted, and it still doesn't work.  Wicd can't find any wireless networks.  I have an hp dv7-1135nr with atheros ar5001.  

Here are my lspci/ifconfig/iwconfig outputs.  Any help is appreciated.

cox@hplinux:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
cox@hplinux:~$ ifconfig
ath1      Link encap:Ethernet  HWaddr 00:23:4d:2c:c6:c0  
          inet6 addr: fe80::223:4dff:fe2c:c6c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:af:87:71  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:feaf:8771/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4100711 (4.1 MB)  TX bytes:508121 (508.1 KB)
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4D-2C-C6-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:180835 (180.8 KB)
          Interrupt:18 

cox@hplinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath1      IEEE 802.11g  ESSID:"DanielleIsAwesome"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by drpjkurian on 2009-12-13
> **coxne said:**
> I followed the instructions as you posted, and it still doesn't work.  Wicd can't find any wireless networks.  I have an hp dv7-1135nr with atheros ar5001.  

Here are my lspci/ifconfig/iwconfig outputs.  Any help is appreciated.

cox@hplinux:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
08:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
09:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
cox@hplinux:~$ ifconfig
ath1      Link encap:Ethernet  HWaddr 00:23:4d:2c:c6:c0  
          inet6 addr: fe80::223:4dff:fe2c:c6c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:af:87:71  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:feaf:8771/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2922 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4100711 (4.1 MB)  TX bytes:508121 (508.1 KB)
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4D-2C-C6-C0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:180835 (180.8 KB)
          Interrupt:18 

cox@hplinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath1      IEEE 802.11g  ESSID:"DanielleIsAwesome"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Hi Coxne

These instructions are meant for 32 bit chipsets, that means intel chipsets. I think it does not suite AMD Athlon.

---

### Post by coxne on 2009-12-13
Is there a way to mod these instructions to get it working?

---

### Post by drpjkurian on 2009-12-13
> **coxne said:**
> Is there a way to mod these instructions to get it working?
Hi Coxne
I did some meagre googling and found this. Let it be a beginning for you
[http://dir.filewatcher.com/d/Ubuntu/amd64/contrib/net.0.0.htm](http://dir.filewatcher.com/d/Ubuntu/amd64/contrib/net.0.0.htm)
[http://spacebison.com/files/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://spacebison.com/files/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)
Though it is an instruction of Hardy heron, You can give a try.
Best of luck

---

### Post by Halc10n_z3r0 on 2009-12-15
I am having a similar issue. After doing a full install of Karmic, once I do the system updates, it refuses to let me connect to my wifi. It just continuously asks for my wep key (and yes I am entering it correctly). However it will occasionally work if I restart my system, kill the network manager process, then do "Sudo nm-applet". But its a fat chance if it works, and when it does, my internet makes dial-up look like it's faster than lightning... I would like to just get my wifi to work again. I'm on a laptop so, sitting here in a corner huddled over this little ethernet cable isn't really a long-term option lol

---

### Post by tonycowan on 2009-12-16
Thank you Dr Kurian!
This worked for me.
I must say this has been the worst upgrade of Ubuntu that I've attempted. Too many things that worked in 9.04 broke.
I still don't have a good fix for my external monitor resolution issue. Currently I have to issue a command line xrandr command to adjust the resolution every time I reboot. I'll figure out how to put that in some rc script some day, but I must say this has been a frustrating release for me and I'm looking at other distro's as a result.

Thanks again for your help Dr Kurian.

---

### Post by drpjkurian on 2009-12-16
> **tonycowan said:**
> Thank you Dr Kurian!
This worked for me.
I must say this has been the worst upgrade of Ubuntu that I've attempted. Too many things that worked in 9.04 broke.
I still don't have a good fix for my external monitor resolution issue. Currently I have to issue a command line xrandr command to adjust the resolution every time I reboot. I'll figure out how to put that in some rc script some day, but I must say this has been a frustrating release for me and I'm looking at other distro's as a result.

Thanks again for your help Dr Kurian.
Dear Tonycovan
You are most welcome

with regards
Dr Kurian

---

### Post by swatsbiz on 2009-12-18
Followed these instructions and still no joy, very intermittent connection and slow if connected at all ... any help would be appreciated

David

---

### Post by drpjkurian on 2009-12-18
> **swatsbiz said:**
> Followed these instructions and still no joy, very intermittent connection and slow if connected at all ... any help would be appreciated

David

Hi
Please install the following packages by synaptic package manager
They are linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic.

This might help you. This solution was given by coffeecat

---

### Post by ripplecm on 2009-12-30
Hey just finished your steps and it WORKED!!! I am so happy.  I honestly don't know how much time I have spent trying to get my wireless driver to work.  The built in driver with ubuntu worked for me, but it was spotty and would go out and not come back.  Madwifi works like a dream.  Thank you so much for putting this thread up for everyone to use.  I had almost given up on ubuntu for good.
:guitar:

---

### Post by drpjkurian on 2009-12-30
> **ripplecm said:**
> Hey just finished your steps and it WORKED!!! I am so happy.  I honestly don't know how much time I have spent trying to get my wireless driver to work.  The built in driver with ubuntu worked for me, but it was spotty and would go out and not come back.  Madwifi works like a dream.  Thank you so much for putting this thread up for everyone to use.  I had almost given up on ubuntu for good.
:guitar:

Hi ripplecm
You are most welcome
Dr Kurian

---

### Post by JohnAdamTurnbull on 2010-01-01
drpjkurian, bac522 and others have been so patient and helpful I'm reluctant to ask for more help, but I am truly stuck.

I have a new 9.10 install on a Lenovo Thinkpad x60. I'm new to Ubuntu.

I have followed drpjkurian's instructions with only one anomaly: the 
sudo apt-get install linux-headers-`uname -r`

returned a packages not found error (I'm translating from french.)

Otherwise, I succeeded in making and installing. The result: no wirless can be found in Wicd. I re-did the whole sequence and I'm satisfied that everything (except the above anomaly) worked correctly.

Subsequently I also installed the backport modules.

Then I followed bac522's instructions -- no luck yet.

iwconfig returns

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

Still banging my head ...

Otherwise, I'm really impressed with Ubuntu and looking forward to a gradual migration of my Windows XP files.

Happy New Year!

-- jat

---

### Post by JohnAdamTurnbull on 2010-01-01
I also followed bac522's advice to remove and reinstall ath9k:


root@ubuntu:~# modprobe -r ath9k
root@ubuntu:~# modprobe ath9k
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-16-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.31-16-generic/updates/cw/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)


... Maybe this is a clue for someone more experienced than I am -- which must include almost everyone.

Thanks

-jat

---

### Post by bac522 on 2010-01-01
> **JohnAdamTurnbull said:**
> 

I have followed drpjkurian's instructions with only one anomaly: the 
sudo apt-get install linux-headers-`uname -r`

-- jat

Open a shell window and just type "uname -r". I run a later version of the kernal, so my shell shows "2.6.32"

Whatever prints out just tag that to the above command so it would look like something similar to the following:

```
sudo apt-get install linux-headers-2.6.32
```

Basically the header files are needed whenever you compile a program such as Madwifi.

---

### Post by JohnAdamTurnbull on 2010-01-01
My linux-headers name is 2.6.31-16-generic so that made a difference.

Yey! Now I get different results:

root@ubuntu:/# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Although modprobe -r ath9k and modprobe ath9k gives me the same error:

root@ubuntu:/# modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.bak2, it will be ignored in a future release.
WARNING: Error inserting mac80211 (/lib/modules/2.6.31-16-generic/updates/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.31-16-generic/updates/cw/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@ubuntu:/#

Am I closer? :confused:

---

### Post by bac522 on 2010-01-01
> **JohnAdamTurnbull said:**
> 

Although modprobe -r ath9k and modprobe ath9k gives me the same error:


Yeah, I believe you've got the madwifi driver installed and that is why you are seeing the ath0 wireless interface. Configure wicd to use that interface (ath0) and see if you can connect into your wireless network. Don't worry about the "Linux Wireless" drivers for now (that is the ath9k drivers).

---

### Post by JohnAdamTurnbull on 2010-01-02
I haven't mentioned yet that the wireless indicator light on my x60 does not go on in response to Wicd and cannot be turned on with Func+F5 -- the usual hardware switch.

Current state: after configuring Wicd for ath0 rather than eth0 to which it defaulted, I get no change in its behavior. When I tried to use an ad-hoc connection, the dialog just hung.

---

### Post by bac522 on 2010-01-02
> **JohnAdamTurnbull said:**
> I haven't mentioned yet that the wireless indicator light on my x60 does not go on in response to Wicd and cannot be turned on with Func+F5 -- the usual hardware switch.

Strange...what happens if you type "sudo ifconfig ath0 up"? Don't take the fact that you're wlan light on you computer is not working as being a problem. The madwifi drivers didn't always activate the light. 

Also, now that you have the linux headers installed you can run through the steps I listed for compiling the linux wireless drivers.

---

### Post by Throglogg on 2010-01-04
Hi there,   i just tried to get my wlan to work with the commands here.   I give you a few details...  1. I use linux since 5 days -> no backround  2. I use the netbook-remix  3. This is all i know about my network:  Atheros Communications Inv. Device 002c (rev01) Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev02)  4. After the installation of the MadWIFI drivers i still get:  iwconfig lo           no wireless extensions. eth0         no wireless extensions.   5. This is my netbook:  [http://www.alternate.de/html/solrSearch/toArticle.html?articleId=391811&query=alternate+mobile+mini&referer=topseller&link=solr%2Fsearch%2Fresult.productDetails](http://www.alternate.de/html/solrSearch/toArticle.html?articleId=391811&query=alternate+mobile+mini&referer=topseller&link=solr%2Fsearch%2Fresult.productDetails) (yes, i am from germany)  the netbook's got Wireless LAN IEEE 802.11 b/g  Maybe you can help me, getting my wLAN to work.   Thanks

---

### Post by JohnAdamTurnbull on 2010-01-05
bac522 -- sorry to go silent for a couple of days here, but things are working now.

I`m not confident that I can explain the path I took and the wrong turns, but in case it is useful for anyone else, here is the summary. On 9.10, installed via wabu on WinXP, I was unsucessful getting my Atheros 5212 wireless to work. I followed the tutorial at the top of this thread (relearning quite a bit about Linux along the way), but failed. On one of many reboots, I failed to connect to my wired network.

At that point, faced with communicating on WinXP and rebooting for each configuration change, I decided to uninstall ubuntu (from WinXP), create a disc and start again. On my first use of the live disc, the wireless connected. Bingo! So I`ve done a complete install and things are still working. Wish I could tell you why. I`m even getting a console light.

Thanks for everyone`s help. 

-- jat

---

### Post by trelxy68 on 2010-01-06
I did the madwifi and installed the wicd. did manage to scan wireless networks but when tried to connect, it will fail at trying to aquire ip address. any solutions?  using atheros ar5008x  ubuntu 9.10 kernel 2.6.31

---

### Post by drpjkurian on 2010-01-08
> **trelxy68 said:**
> I did the madwifi and installed the wicd. did manage to scan wireless networks but when tried to connect, it will fail at trying to aquire ip address. any solutions?  using atheros ar5008x  ubuntu 9.10 kernel 2.6.31

Hi Trelxy

Why cant you give a try to this thread [http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

Let me know the outcome

Dr Kurian

---

### Post by drpjkurian on 2010-01-08
> **trelxy68 said:**
> I did the madwifi and installed the wicd. did manage to scan wireless networks but when tried to connect, it will fail at trying to aquire ip address. any solutions?  using atheros ar5008x  ubuntu 9.10 kernel 2.6.31

Hi Trelxy

Please try the following instructions and let me know the outcome. These are to install the latest versions of Madwifi

Step 1 Download the driver which you can find at this [URL]("http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz") and extract it to the desktop either by ark or archive manager

Step 2```
sudo apt-get update && sudo apt-get upgrade
```

Step 3
```
sudo apt-get install linux-headers-`uname -r`
```

Step 4
```
cd Desktop
```

Step 5
```
cd madwifi-0.9.4-r4100-20091230
```

Step 6
```
make && make install
```

Step 7
```
sudo -i
```

Step 8
```
modprobe ath_pci
```

Reboot the machine

Dr Kurian

---

### Post by Throglogg on 2010-01-09
Hey Dr. Kurian, 

is it possible, that the URL isn't working? 

I can't download with my Windows Vista or with Ubuntu. 

Can you check this please?

Thank you!

---

### Post by drpjkurian on 2010-01-09
> **Throglogg said:**
> Hey Dr. Kurian, 

is it possible, that the URL isn't working? 

I can't download with my Windows Vista or with Ubuntu. 

Can you check this please?

Thank you!

Hi
Wait a minute

Dr Kurian

---

### Post by drpjkurian on 2010-01-09
Hi 
I have corrected it

Dr Kurian

---

### Post by Throglogg on 2010-01-09
Hey, 

the download worked fine now! Thanks for this!

But at your fifth step, comes an error-message... 

[HTML]root@lilRider:~# cd Desktop
-bash: cd: Desktop: No such file or directory[/HTML]

I tried it with my Downloads-Folder, but the result was the same. 

Can you tell me what's wrong?

(I'm sorry if this is a stupid question, but i really don't get it.)

Thanks for your help!

---

### Post by drpjkurian on 2010-01-09
> **Throglogg said:**
> Hey, 

the download worked fine now! Thanks for this!

But at your fifth step, comes an error-message... 

[HTML]root@lilRider:~# cd Desktop
-bash: cd: Desktop: No such file or directory[/HTML]

I tried it with my Downloads-Folder, but the result was the same. 

Can you tell me what's wrong?

(I'm sorry if this is a stupid question, but i really don't get it.)

Thanks for your help!

Hi Throglogg

I am very sorry throglogg for my inaccuracy. Thank you very much for pointing out the mistake. Well I have rewritten the steps now. Please do give a try.

Dr Kurian

---

### Post by Throglogg on 2010-01-10
Hey, 

i just tried to install once more. 

I copied the outcomming:

[HTML]
  	 	 	 	 	 	  throglogg@lilRider:~/Desktop$ cd madwifi-0.9.4-r4100-20091230
 

 throglogg@lilRider:~/Desktop/madwifi-0.9.4-r4100-20091230$ make && make install
 

 Checking requirements... ok.
 

 Checking kernel configuration... ok.
 

 make -C /lib/modules/2.6.31-16-generic/build SUBDIRS=/home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230 modules
 

 make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath/if_ath.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath/if_ath_pci.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath/ath_pci.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_hal/ah_os.o
 

   HOSTCC  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_hal/uudecode
 

   UUDECODE /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_hal/i386-elf.bin
 

   UNMANGLE /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_hal/i386-elf.hal.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_hal/ath_hal.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/amrr/amrr.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/amrr/ath_rate_amrr.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/minstrel/minstrel.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/minstrel/ath_rate_minstrel.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/onoe/onoe.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/onoe/ath_rate_onoe.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/sample/sample.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/sample/ath_rate_sample.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/if_media.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_beacon.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_crypto.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_crypto_none.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_input.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_node.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_output.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_power.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_proto.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_scan.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_wireless.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_linux.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_monitor.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_rate.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_acl.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_crypto_ccmp.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_scan_ap.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_scan_sta.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_crypto_tkip.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_crypto_wep.o
 

   CC [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/ieee80211_xauth.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_wep.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_tkip.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_ccmp.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_acl.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_xauth.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_scan_sta.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_scan_ap.o
 

   Building modules, stage 2.
 

   MODPOST 14 modules
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath/ath_pci.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath/ath_pci.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_hal/ath_hal.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_hal/ath_hal.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/amrr/ath_rate_amrr.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/amrr/ath_rate_amrr.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/minstrel/ath_rate_minstrel.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/minstrel/ath_rate_minstrel.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/onoe/ath_rate_onoe.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/onoe/ath_rate_onoe.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/sample/ath_rate_sample.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath_rate/sample/ath_rate_sample.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_acl.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_acl.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_ccmp.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_ccmp.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_scan_ap.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_scan_ap.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_scan_sta.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_scan_sta.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_tkip.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_tkip.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_wep.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_wep.ko
 

   CC      /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_xauth.mod.o
 

   LD [M]  /home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/net80211/wlan_xauth.ko
 

 make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
 

 make -C ./tools  all || exit 1
 

 make[1]: Entering directory `/home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/tools'
 

 gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath  athstats.c
 

 athstats.c: In function 'main':
 

 athstats.c:285: warning: format not a string literal and no format arguments
 

 athstats.c:287: warning: format not a string literal and no format arguments
 

 athstats.c:307: warning: format not a string literal and no format arguments
 

 athstats.c:309: warning: format not a string literal and no format arguments
 

 athstats.c:344: warning: format not a string literal and no format arguments
 

 gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I..  80211stats.c
 

 80211stats.c: In function 'main':
 

 80211stats.c:290: warning: format not a string literal and no format arguments
 

 gcc -o athkey -g -O2 -Wall -I. -I../hal -I..  athkey.c
 

 gcc -o athchans -g -O2 -Wall -I. -I../hal -I..  athchans.c
 

 gcc -o athctrl -g -O2 -Wall -I. -I../hal -I..  athctrl.c
 

 gcc -o athdebug -g -O2 -Wall -I. -I../hal -I..  athdebug.c
 

 gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I..  80211debug.c
 

 gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I..  wlanconfig.c
 

 wlanconfig.c: In function 'if_find_unit':
 

 wlanconfig.c:297: warning: ignoring return value of 'fgets', declared with attribute warn_unused_result
 

 wlanconfig.c: In function 'list_keys':
 

 wlanconfig.c:830: warning: ignoring return value of 'system', declared with attribute warn_unused_result
 

 wlanconfig.c: In function 'ieee80211_status':
 

 wlanconfig.c:946: warning: ignoring return value of 'system', declared with attribute warn_unused_result
 

 make[1]: Leaving directory `/home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/tools'
 

 sh scripts/find-madwifi-modules.sh -r 2.6.31-16-generic  
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/ath_hal.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan_ccmp.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan_wep.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan_tkip.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/ath_rate_minstrel.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan_xauth.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/ath_rate_amrr.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/ath_pci.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan_scan_ap.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan_acl.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/ath_rate_sample.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/ath_rate_onoe.ko': Permission denied
 

 rm: cannot remove `/lib/modules/2.6.31-16-generic/net/wlan_scan_sta.ko': Permission denied
 

 for i in ath/ ath_hal/ ath_rate/ net80211/; do \
 

 		make -C $i install || exit 1; \
 

 	done
 

 make[1]: Entering directory `/home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath'
 

 test -d //lib/modules/2.6.31-16-generic/net || mkdir -p //lib/modules/2.6.31-16-generic/net
 

 install -m 0644 ath_pci.ko //lib/modules/2.6.31-16-generic/net
 

 install: cannot remove `//lib/modules/2.6.31-16-generic/net/ath_pci.ko': Permission denied
 

 make[1]: *** [install] Error 1
 

 make[1]: Leaving directory `/home/throglogg/Desktop/madwifi-0.9.4-r4100-20091230/ath'
 

 make: *** [install-modules] Error 1
 

 throglogg@lilRider:~/Desktop/madwifi-0.9.4-r4100-20091230$ sudo -i
 

 [sudo] password for throglogg:  
 

 root@lilRider:~# modprobe ath_pci
 

 WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
 

 
[/HTML]

Hopefully you can analyse my problem with this better...

Thank you again!

---

### Post by drpjkurian on 2010-01-11
Hi Throglogg

I am sorry to say that this problem seems to be beyond my capacity to solve it. Please contact Pytheas my friend who is better than me in solving these issues.

---

### Post by Throglogg on 2010-01-12
Hey, 


thank you for your engagement! I'm very pleased about this. 

I just found the windows-driver for my wLan. But this won't help, will it?



Throglogg

---

### Post by drpjkurian on 2010-01-13
> **Throglogg said:**
> Hey, 


thank you for your engagement! I'm very pleased about this. 

I just found the windows-driver for my wLan. But this won't help, will it?



Throglogg

Hi Throglogg

This driver can be handy. You can use this windows driver in Ubuntu by using a programme known as Ndiswrapper.
Just google it. You will get a breakthrough.
Please visit this site for a beginning 
[http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/](http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/)

---

### Post by n125 on 2010-01-14
I've been having [wireless connectivity issues]("http://ubuntuforums.org/showthread.php?t=1376220"), so I've been trying various solutions that I came across on these forums.  I just tried installing the Madwifi drivers, but now wcid is not detecting *any* wireless networks. Is there a solution to pick up wireless networks so that I can at least try these drivers and see if they work well?  Thanks.

---

### Post by Ibidem on 2010-01-14
Have you rebooted yet?


You might try the following commands (in a terminal):
lsmod |grep ath
(lists all loaded drivers)
(should see ath_hal & ath_pci if madwifi drivers are loaded, ath5k or similar if default drivers are loaded)
ifconfig
(should see ath0, wifi0 with madwifi, wlan0 with ath5k)



Put the interfaces up if ath0, wifi0 aren't present & the drivers are loaded:
sudo ifconfig wifi0 up 
sudo ifconfig ath0 up
(ath0 is the one you configure; wifi0 must be present for some reason)

Then see how you're coming...
I've done the rest of the configuration in a terminal, also.
It's just ifconfig & iwconfig.

But really, I've been having great luck with kernels 2.6.31 & 2.6.32, using ath5k

Hope this helps,
Ibidem

---

### Post by n125 on 2010-01-14
> **Ibidem said:**
> Have you rebooted yet?


You might try the following commands (in a terminal):
lsmod |grep ath
(lists all loaded drivers)
(should see ath_hal & ath_pci if madwifi drivers are loaded, ath5k or similar if default drivers are loaded)
ifconfig
(should see ath0, wifi0 with madwifi, wlan0 with ath5k)



Put the interfaces up if ath0, wifi0 aren't present & the drivers are loaded:
sudo ifconfig wifi0 up 
sudo ifconfig ath0 up
(ath0 is the one you configure; wifi0 must be present for some reason)

Then see how you're coming...
I've done the rest of the configuration in a terminal, also.
It's just ifconfig & iwconfig.


Hi, thanks for replying. Rebooting was the first thing I did when I finished the Madwifi installation.

Let's see..

lsmod | grep ath returns ath_pci, wlan, and ath_hal. sudo ifconfig wifi0 up and sudo ifconfig ath0 up both return errors: ERROR while getting interface flags: No such device. I guess that's where the problem lies.

> But really, I've been having great luck with kernels 2.6.31 & 2.6.32, using ath5k

Hope this helps,
IbidemPrior to installing the Madwifi drivers, I was using the ath9k driver. I think that was the default. If I can't get the Madwifi drivers to work (or if they don't work well) would I be able to try the ath5k driver on a AR9285 chipset? Maybe that's more stable? Although I'm not sure how--I'm still very new to Linux.

---

### Post by tetebueno on 2010-01-16
For those who updated Karmic and screwed wifi, check this thread:

[http://ubuntuforums.org/showthread.php?t=1305812]("http://ubuntuforums.org/showthread.php?t=1305812")

Hope this helps.

Cheers.

---

### Post by Jason O on 2010-02-14
I tried this fix (and many others) and none of them worked.

However, after running this tutorials fix, I ran jockey-gtk and then the madwifi-alternate driver was available. I installed that driver and I have been cruising on WPA2 network with a stable connection.

I am using wicd as well. This is on a Toshiba Satellite M45-S165. That's true Celeron power! Sweet. Good luck.

---

### Post by drpjkurian on 2010-02-20
Thanks dude

---

### Post by sidkat2006 on 2010-02-26
hey ppl..i tried to mak my laptop as an access point or node but it shows me an error..can some1 help me out..I need it for my project urgently.

---

### Post by Fueled on 2010-03-13
Thanks a lot for this guide! It solved my wireless connection problem, which had worked before, and not anymore (probably a kernel update). Now I've bookmarked your post, so I will be able to solve it easily the next time the drivers are killed.

Thanks again!

---

### Post by drpjkurian on 2010-03-14
> **Fueled said:**
> Thanks a lot for this guide! It solved my wireless connection problem, which had worked before, and not anymore (probably a kernel update). Now I've bookmarked your post, so I will be able to solve it easily the next time the drivers are killed.

Thanks again!
Hi
You are most welcome

---

### Post by jhonnyboy on 2010-03-19
Just wanted to give my thanks to drpjkurian. This worked for me, I have been going thru hell to get my wifi working correctly. Thanks a million!!

---

### Post by drpjkurian on 2010-03-21
> **jhonnyboy said:**
> Just wanted to give my thanks to drpjkurian. This worked for me, I have been going thru hell to get my wifi working correctly. Thanks a million!!

Hi
you are most welcome

---

### Post by tzenda on 2010-04-16
hey guys i took the steps listed in the first post and then followed up through the rest of the post but i still cant get my wifi to work on my acer aspire 5570z. anyone else found other solutions?

---

### Post by drpjkurian on 2010-04-18
Hi tzenda
Please mentionn the make of your card
type ```
lshw
``` to know the wireless device

---

### Post by tzenda on 2010-04-22
tzenda-laptop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 993MiB
     *-cpu
          product: Genuine Intel(R) CPU           T2080  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.12
          serial: 0000-06EC-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor est tm2 xtpr pdcm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
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
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0300000-d037ffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:d0400000-d043ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0380000-d03fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d0440000-d0443fff
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:2000(size=4096) memory:44000000-440fffff
           *-network
                description: Ethernet interface
                product: 88E8038 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 14
                serial: 00:1b:24:61:83:49
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A ip=192.168.1.8 latency=0 multicast=yes
                resources: irq:27 memory:44000000-44003fff ioport:2000(size=256)
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 memory:44100000-441fffff
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wifi0
                version: 01
                serial: 00:19:7e:9b:23:27
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
                resources: irq:17 memory:44100000-4410ffff
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0644000-d06443ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:3000(size=4096) memory:d0200000-d02fffff memory:40000000-43ffffff(prefetchable)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:0a:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:20 memory:d0204000-d0204fff ioport:3000(size=256) ioport:3400(size=256) memory:40000000-43ffffff(prefetchable) memory:48000000-4bffffff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 9.2
                bus info: pci@0000:0a:09.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:20 memory:d0205000-d0205fff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)





i think its an atheros ar5001

---

### Post by drpjkurian on 2010-04-22
Hi
You are right it is AR 5001
well according to my knowledge this Madwifi should work, because in my macgine it is AR 5001. I am using Wicd to scan my network. Please try that..

---

### Post by tzenda on 2010-04-30
yea i use the wicd thingy. when i go to my drivers page it only shows the ath5k driver, says its the backup driver.  wasnt there supposed to be a ath9k or something driver?

---

### Post by ColmCille on 2010-05-01
My atheros wifi was running real slow and dropping the connection at random (every few minutes), requiring reboot to get going again.

After reading these threads, the very first thing I tried was installing the linux-backports-modules(-wireless)-karmic-generic packages, and it worked.   

I wonder if the reason it isn't working for some is that they tried other stuff first, which somehow prevented the modules from working properly. Maybe installing the modules should be the first thing folks try. Just a thought, not based on any expert knowledge. Also, I have the AR928X, so maybe it doesn't work the same with the 5000 series. 

Anyway, thanks to CoffeeCat for suggesting it (was that in a different thread?). It saved me the hassle of trying to install madwifi, finding a way that works with 64bit Athlon, etc. (though kudos to the Doc for posting the instructions for those who need it).

I was going to upgrade to Lucid, but I'm afraid (very, *very* afraid) of breaking my wifi again (the last Ubuntu version I used was Hardy, with an AR5001, and I went through bloody agony fixing that--in the end, with madwifi. I think I may have post traumatic stress disorder from it 8-[).

I really hope I can one day install Ubuntu and have wifi (and everything else) just, you know, *work*. Like they do with those other OSes. :P

---

### Post by drpjkurian on 2010-05-02
> **ColmCille said:**
> My atheros wifi was running real slow and dropping the connection at random (every few minutes), requiring reboot to get going again.

After reading these threads, the very first thing I tried was installing the linux-backports-modules(-wireless)-karmic-generic packages, and it worked.   

I wonder if the reason it isn't working for some is that they tried other stuff first, which somehow prevented the modules from working properly. Maybe installing the modules should be the first thing folks try. Just a thought, not based on any expert knowledge. Also, I have the AR928X, so maybe it doesn't work the same with the 5000 series. 

Anyway, thanks to CoffeeCat for suggesting it (was that in a different thread?). It saved me the hassle of trying to install madwifi, finding a way that works with 64bit Athlon, etc. (though kudos to the Doc for posting the instructions for those who need it).

I was going to upgrade to Lucid, but I'm afraid (very, *very* afraid) of breaking my wifi again (the last Ubuntu version I used was Hardy, with an AR5001, and I went through bloody agony fixing that--in the end, with madwifi. I think I may have post traumatic stress disorder from it 8-[).

I really hope I can one day install Ubuntu and have wifi (and everything else) just, you know, *work*. Like they do with those other OSes. :P

Hi
I upgraded to Lucid yesterday and did the steps mentioned in my first post. It works without any hassle. So I advice you to upgrade for it is a LTS version

---

### Post by pwabrahams on 2010-05-08
I've successfully used this procedure for several kernel upgrades.  But it hasn't worked for me for the upgrade from 2.6.32.21 to 2.6.32.22.  Any idea why?

Added info: from another thread, I learned that the problem seems to be related to **rfkill** and might be a kernel bug.  See [http://kubuntuforums.net/forums/index.php?topic=3111700.msg228832#msg228832]("http://kubuntuforums.net/forums/index.php?topic=3111700.msg228832#msg228832").

---

### Post by pwabrahams on 2010-05-08
Apparently the key thing is to set **rfkill=0**.  I found the following in an old post:>  Re: how to load ath_pci rfkill=0 on startup?
As usual, it's easier, just you have to know what to do.

I've removed linux-restricted-modules completly (i'll install ati from propietary driver) and just compile madwifi and installed.

Then at /etc/modules added ath_hal and ath_pci

after that, edited /etc/modprobe.d/options and added the line

options ath_pci rfkill=0

voila! working on startup.
The problem with applying this advice is that **/etc/modprobe.d/options ** no longer exists, so I don't know how to apply the option.

---

### Post by pedpie on 2010-05-10
This works awesome on an acer AO532h with AR928X wifi and 10.04 netbook edition. Thanks!!=D>

---

### Post by pwabrahams on 2010-05-11
> **pedpie said:**
> This works awesome on an acer AO532h with AR928X wifi and 10.04 netbook edition. Thanks!!=D>

Did you already have an **/etc/modprobe.d/options** file or did you create a new one?

---

### Post by dexaco on 2010-05-14
I just wanted to add my thanks for saving what's left of my hair! My wireless connection on my Toshiba Equium is now working as it should be. I had even considered going back to Windows on the Tosh, as I knew the wireless worked, but you've saved me. First time connection when I rebooted after following the instructions. Linux Mint 8, by the way.

Derick

---

### Post by pwabrahams on 2010-05-14
I haven't been able to get this procedure to work for myself (!!), but I'm glad (and encouraged) that it's worked for two other people at least.  For those whom it helped: did you already have an **/etc/modprobe.d/options** file, or did you have to create a new one?

I imagine there was some wisdom in changing the **rfkill** default setting in the kernel modules, but I'll be damned if I know what it is.

---

### Post by biloyp on 2010-05-14
> **bac522 said:**
> You can try "sudo rm" if that doesn't work I suggest reloading the compact-wireless drivers back on. Of course you'll need internet connectivity to get those drivers, then follow the following steps:

Open up a shell and create a working directory:
```
mkdir wireless
```
```
cd wireless
```

Next download (what I found to work) a version of the compact-wireless drivers
```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/10/compat-wireless-2009-10-15.tar.bz2
```

Uncompress and extract the files
```
bunzip2 ./compat-wireless-2009-10-15.tar.bz2
```
```

tar xvf ./compat-wireless-2009-10-15.tar
```
Change into the directory and build the drivers.
```
cd ./compat-wireless-2009-10-15/
```
```
./scripts/driver-select ath
```
```
make
```

Now install the drivers (don't worry about the initial warning message
```
make install
```

Now remove the blacklist entry that was created intially
```
sudo nano /etc/modprobe.d/blacklist
``` 

Thats it. Rather then doing a "make unload" I would suggest just rebooting. Barring everything worked okay your wireless should be working with the ath9k driver.

Yup, this did it for me!!! Thanks a bunch.

---

### Post by pwabrahams on 2010-05-14
I've got wireless on my Acer Aspire laptop working at last.  The last stumbling block was that in some previous attempt to solve the problem, I had commented out a couple of lines in the blacklist, so the **ath5k** module was still getting loaded and, apparently, overriding **ath_pci**.  So note that **/etc/modprobe.d/blacklist** should have the lines
```
blacklist ath5k
blacklist ath9k

```

---

### Post by pwabrahams on 2010-05-14
I've recorded the key methods from this thread in the Ubuntu wiki at [http://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("http://help.ubuntu.com/community/WifiDocs/Driver/Atheros"). It's listed as the "alternate method". If anyone following this thread discovers errors in that article, please correct them (or post the corrections here).

---

### Post by drpjkurian on 2010-05-15
> **pwabrahams said:**
> I've recorded the key methods from this thread in the Ubuntu wiki at [http://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("http://help.ubuntu.com/community/WifiDocs/Driver/Atheros"). It's listed as the "alternate method". If anyone following this thread discovers errors in that article, please correct them (or post the corrections here).

Hi
You have done a great job

---

### Post by RainKap on 2010-05-18
> **drpjkurian said:**
> Hi
I upgraded to Lucid yesterday and did the steps mentioned in my first post. It works without any hassle. So I advice you to upgrade for it is a LTS version

OK, I shall give this a try later this week - I upgraded to Lucid at the weekend, and had several sorts of grief trying to get WiFi working, so in the end I did a clean(ish) install of Karmic (retaining my /home partition), and had *even more* grief trying to get WiFi working again! In the end, I followed drpjkurian's recipe and was immensely relieved to get WiFi working again this afternoon, ready for me to take the laptop to a meeting. I have another meeting (for which I'm secretary) on Thursday evening, so Lucid will have to wait until after that...

Ian

---

### Post by pwabrahams on 2010-05-18
> **RainKap said:**
> OK, I shall give this a try later this week - I upgraded to Lucid at the weekend, and had several sorts of grief trying to get WiFi working, so in the end I did a clean(ish) install of Karmic (retaining my /home partition), and had *even more* grief trying to get WiFi working again! In the end, I followed drpjkurian's recipe and was immensely relieved to get WiFi working again this afternoon, ready for me to take the laptop to a meeting. I have another meeting (for which I'm secretary) on Thursday evening, so Lucid will have to wait until after that...

Ian

Be careful -- the Kurian recipe doesn't quite work after the latest kernel update to Lucid, even though it worked before that update.  For the correct recipe, see [http://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("http://help.ubuntu.com/community/WifiDocs/Driver/Atheros").  Dr. Kurian has looked at it and says it's OK (see his comment earlier in this thread).

I think it's far better to have this information in a Ubuntu (or Kubuntu) wiki, where it's easier to find than it is in a forum thread.

---

### Post by RainKap on 2010-05-27
Great stuff - I upgraded to Lucid recently on my netbook (Acer Aspire One) and my big laptop ("Custom PC" built to order), both of which use the Atheros 5001. Wireless worked at first on the Aspire One, but then got flakier and refused to work. On the "Custom PC" laptop wireless flatly refused to work at all. I followed drpjkurian's recipe on both machines, and we are now flying again :)

Thanks

Ian

---

### Post by RainKap on 2010-05-27
Oops, I typed a bit too soon :( The "Custom PC" laptop is fine, but when I started up the Aspire One again after submitting the previous post it hung, and eventually gave up. I tried the extra steps listed in the wiki (making sure that both ath_hal and ath_pci are included in /etc/modules, and creating /etc/modprobe.d/options with the line options ath_pci rfkill=0), but to no avail. I tried wicd (which, interestingly, now seems to ba able to co-exist with network manager), and *that* told me after trundling round trying to authenticate that the password was bad! After opening up the wireless access point (removing encryption), and repeating the access attempt using wicd, it failed because it couldn't get an IP address. Looks as though I need to do some more digging...

Ian

---

### Post by drpjkurian on 2010-05-30
> **RainKap said:**
> Oops, I typed a bit too soon :( The "Custom PC" laptop is fine, but when I started up the Aspire One again after submitting the previous post it hung, and eventually gave up. I tried the extra steps listed in the wiki (making sure that both ath_hal and ath_pci are included in /etc/modules, and creating /etc/modprobe.d/options with the line options ath_pci rfkill=0), but to no avail. I tried wicd (which, interestingly, now seems to ba able to co-exist with network manager), and *that* told me after trundling round trying to authenticate that the password was bad! After opening up the wireless access point (removing encryption), and repeating the access attempt using wicd, it failed because it couldn't get an IP address. Looks as though I need to do some more digging...

Ian

Hi Rainkap
Let me share you one of my experience after Lucid.

I was using Wicd from hardy heron to Karmic kaola. When I upgraded to Lucid, I got a weird message from Wicd stating that it is unable to get IP address. I switched over to Knetwork manager and it is robust connection again..
I think it is a bug in Wicd

Let me know yours... after trying network manager

---

### Post by swajime on 2010-07-11
> **pwabrahams said:**
> Be careful -- the Kurian recipe doesn't quite work after the latest kernel update to Lucid, even though it worked before that update.  For the correct recipe, see [http://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("http://help.ubuntu.com/community/WifiDocs/Driver/Atheros").  Dr. Kurian has looked at it and says it's OK (see his comment earlier in this thread).

I think it's far better to have this information in a Ubuntu (or Kubuntu) wiki, where it's easier to find than it is in a forum thread.

I followed the steps on that page exactly (AFAIK).  My wireless is still ridiculously slow. :(

```
2010/07/11 19:28:49 :: Connecting to wireless network hideout
2010/07/11 19:28:49 :: attempting to set hostname with dhclient
2010/07/11 19:28:49 :: using dhcpcd or another supported client may work better
2010/07/11 19:28:49 :: attempting to set hostname with dhclient
2010/07/11 19:28:49 :: using dhcpcd or another supported client may work better
2010/07/11 19:28:50 :: Putting interface down
Jul 11 19:28:50 system76-pc kernel: [  476.056629] r8169: eth0: link up
2010/07/11 19:28:50 :: Releasing DHCP leases...
2010/07/11 19:28:50 :: attempting to set hostname with dhclient
2010/07/11 19:28:50 :: using dhcpcd or another supported client may work better
2010/07/11 19:28:50 :: Setting false IP...
2010/07/11 19:28:50 :: Stopping wpa_supplicant
2010/07/11 19:28:50 :: Flushing the routing table...
2010/07/11 19:28:50 :: Putting interface up...
2010/07/11 19:28:52 :: Generating psk...
2010/07/11 19:28:52 :: Attempting to authenticate...
Jul 11 19:28:52 system76-pc kernel: [  478.707507] ath0: unknown SIOCSIWAUTH flag 12
2010/07/11 19:28:53 :: Setting static IP : 10.0.0.20
2010/07/11 19:28:53 :: Setting default gateway : 10.0.0.1
2010/07/11 19:28:53 :: not verifying
2010/07/11 19:28:53 :: Connecting thread exiting.
2010/07/11 19:28:53 :: Sending connection attempt result Success

```

iwconfig:
```
ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:1206  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm not sure why ifconfig now reports two wireless devices?
```
ath0      Link encap:Ethernet  HWaddr 00:24:01:12:ae:90  
          inet addr:10.0.0.20  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1ff:fe12:ae90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:125580 (125.5 KB)  TX bytes:15030 (15.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-24-01-12-AE-90-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3121 errors:0 dropped:0 overruns:0 frame:433
          TX packets:522 errors:45 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:369787 (369.7 KB)  TX bytes:38884 (38.8 KB)
          Interrupt:20 

```

I'll be happy to share whatever info can help resolve this...
```
# uname -a
Linux system76-pc 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
```
:popcorn:

---

### Post by pwabrahams on 2010-07-11
I'm only guessing, but it seems likely that the double path to the wireless device is responsible for the poor performance.  The Kurian recipe is intended to establish a connection but doesn't attempt to deal with the performance of that connection.

I don't know why you have a double path.  It's interesting that they both have the same HW address, but wifi0 has a bunch of extra zeros.

---

### Post by swajime on 2010-07-12
I'm at my wit's end with it.  Any suggestions for a non-Atheros replacement?

---

### Post by mgt_cole on 2010-07-13
> **drpjkurian said:**
> Hi guys in this thread you will the instructions to install [COLOR=red]**Madwifi**[/COLOR] drivers for [COLOR=red]**Atheros**[/COLOR] wireless cards. Please follow the instructions to the word.
 
Open the 'terminal' by navigating through Applications-->Accessories--> Terminal
 
Now type the following commands in terminal
 
1. ```
sudo nano /etc/apt/sources.list
```
 
From there make sure you uncomment anything that starts with "deb" in there. So changer it from "#deb" to "deb" Something along thoes lines. To exit and save hit "CTRL+X" the answer "YES" to do you want to save, then finally hit "ENTER"
 
2. ```
sudo apt-get update && sudo apt-get upgrade
```
 
3. ```
sudo apt-get install build-essential libssl-dev
```
 
4. ```
sudo apt-get install linux-headers-`uname -r`
```
 
5. ```
sudo apt-get install subversion
```
 
6. ```
sudo -i
```
 
7. ```
sudo svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
```
 
8. ```
cd madwifi-ng
```
 
9. ```
echo "" >> /etc/modprobe.d/blacklist
```
 
10. ```
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
```
 
11. ```
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
```
 
12. ```
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
```
 
13. ```
make && make install
```
 
14. ```
echo ath_pci >> /etc/modules
```
 
Restart your machine.
It should work
 
Well i use Wicd to connect to the wireless modem
To install Wicd type the following commands in terminal
```
sudo apt-get update
```
 
```
sudo apt-get install wicd
```
 
 
:KS Kernal updates of your system will kill your driver. Well no need to worry about that.Just recompile your driver.
For that you open a terminal and type the command```
sudo -i
``` and just repeat the steps from No 8. Your madwifi will cone back to life again.:popcorn:
 
Best of Luck
Dr Kurian
 
 
Dear Dr Kurian,
 
I have followed all your steps and I still couldn't bring up my wireless. I'm using an Acer 5820TG with Atheros AR8151. My installation is 10.04. The Ethernet portion works fine but I couldn't bring up the wireless.
 
I'm fairy new in Ubuntu...
 
Thank you!

---

### Post by simontaylor on 2010-07-16
Dear (K)Ubuteans,

it seems this is the thread that never says die.

I am trying to get 10.04 netbook remix working on an eee PC, 4G 701. I followed the instructions on the original post... 

> 01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Subsystem: Device 1a3b:1026
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: ath_pci
Kernel modules: ath_pci, ath5k

still no wireless. Any help you may offer would be greatly appreciated.

Thanks,

Simon Taylor

---

### Post by bigfootnmd on 2010-08-20
Double post.  See next entry

---

### Post by bigfootnmd on 2010-08-20
Greetings all,

I have an Acer Aspire one A0751 that has the Atheros 5001 (or so) network chip.  I followed drpjkurian's posted instructions to the letter.  I am using Ubuntu 10.04.  No kernel updates have occurred since I loaded the pci drivers two nights ago.  

I am using WPA encryption.  My Netbook wifi connects about 20% of the time when the netbook is in the same room as my router.  I have not yet tried the instructions in the posting 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
because I don't want to make things worse.  

Any help or suggestions will be appreciated.
Oh, and of course my compliments to Dr. Kurian for his well written instructions.

---

### Post by simontaylor on 2010-08-20
I went back to Jaunty Jackalope. No further problems. In fact, connectivity better for wireless than on my desktop running Lucid.

Best,
Simon

---

### Post by pwabrahams on 2010-08-20
> **bigfootnmd said:**
> 
I have an Acer Aspire one A0751 that has the Atheros 5001 (or so) network chip.  I followed drpjkurian's posted instructions to the letter.  I am using Ubuntu 10.04.  No kernel updates have occurred since I loaded the pci drivers two nights ago.  

I am using WPA encryption.  My Netbook wifi connects about 20% of the time when the netbook is in the same room as my router.

Something that happens 20% of the time suggests a signal strength or hardware problem.  If it's software, then I'd expect either 0% or 100%.

 >  I have not yet tried the instructions in the posting 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
because I don't want to make things worse. 

Those instructions are very unlikely to make things worse, even if they don't make things better.  Dr. Kurian himself looked at them and thought they were just fine.

---

### Post by bigfootnmd on 2010-08-21
> **bigfootnmd said:**
> Greetings all,

I have an Acer Aspire one A0751 that has the Atheros 5001 (or so) network chip.  I followed drpjkurian's posted instructions to the letter.  I am using Ubuntu 10.04.  No kernel updates have occurred since I loaded the pci drivers two nights ago.  

I am using WPA encryption.  My Netbook wifi connects about 20% of the time when the netbook is in the same room as my router.  I have not yet tried the instructions in the posting 
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
because I don't want to make things worse.  

Any help or suggestions will be appreciated.
Oh, and of course my compliments to Dr. Kurian for his well written instructions.

Minor update here.  Set my Verizon supplied Actiontec router to use channel 8.  So, far my netbook is connecting via wifi.

I will monitor events over the next few days before trying anything else.

---

### Post by bigfootnmd on 2010-08-22
This morning when I booted up my Netbook (with Lucid, and the madwifi drivers installed) my Netbook could not connect to my router.  My Netbook was no more than 18 inches from my router.  So, there could not have been an issue with signal strength.  I also verified that my WPA key was correct in my settings for my WIFI connection.  So, I did some more research and I found this community doc (which I believe has been mentioned several times in this thread.

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

This doc was last updated on May 15, 2010. It has Dr. Kurian's excellent instructions toward the bottom of the page. There is one additonal warning about kernels 2.6.32.22 and later that I have not seen (and maybe I missed it) in this thread.

"Additional step for kernel 2.6.32.22 and later

Kernel 2.6.32.22 changed the default for the rfkill parameter of ath_pci from 0 to 1, which had the effect of killing the methods described above. You'll need to make sure that it's set back to 0 on system startup. To do that, edit (or create) the file /etc/modprobe.d/options.conf to include the line

options ath_pci rfkill=0"

Since I added 'options ath_pci rkill=0' to my /etc/modprobe.d/options.conf file my netbook is connecting 100% of the time to my WIFI router.  

I have taken the last three steps from Dr. Kurian's method and placed them in a document on my Netbook desktop so that when I get kernel update in the future it will be easy to restore the madwifi drivers.
My thanks again to Dr. Kurian and to everyone who has shared their experiences with the Atheros drivers in this thread.
:popcorn:

---

### Post by SonnyKing on 2010-08-23
Still not working...
AR9287 + ubuntu 2.6.32-24-generic, (also,HP 6930P integrated an Intel 5300 card, and it works well with some other driver);

I have tried many methods, including above.
After building, lsmod | grep ath can return "ath_pci","ath_wlan",and "ath_hal", nevertheless, lshw -C network always returns "Unclaimed"...

I checked "Hard Drivers", and nothing except ATI graphic, even my intel card isn't in the list (but it works well)

Is there someone earnest to help me?
Thanks.

---

### Post by bigfootnmd on 2010-09-09
UPDATE:

Earlier this week I had a brain freeze and I could not remember the password to my Router. So, I reset the router to factory defaults.  Immediately my Acer Aspire one A0751h using the Madwifi drivers for the Atheros 5XXX card could not connect via WIFI.
I logged in to my router and checked the WIFI settings.  I had of course changed the SSID and WPA password to match what I had been using before (these were wiped when I reset the router).  The channel selection was set to automatic.  I changed this to channel 6 and immediately my Netbook was able to connect.  So,  If you have tried the MADWIFI drivers before and still have issues, change the WIFI channel on your router to 6 or 11.

---

### Post by drpjkurian on 2010-09-11
Thank you very much for your compliments

---

### Post by Zerberus on 2010-10-02
I have installed the latest version of maverick, I also used the latest update from

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

> options ath_pci rfkill=0
however my problem currently is as follows:

>   *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:a3:d3:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.69 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:44 ioport:3000(size=256) memory:31010000-31010fff memory:31000000-3100ffff memory:31020000-3103ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
   **    logical name: wifi0**
       version: 01
       serial: 00:22:69:11:c8:88
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:35200000-3520ffff

> **ath0 **     Link encap:Ethernet  HWaddr 00:22:69:11:c8:88  
          inet6 addr: fe80::222:69ff:fe11:c888/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:a3:d3:ae  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fea3:d3ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8088060 (8.0 MB)  TX bytes:1328787 (1.3 MB)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
[B]
wifi0  [/B]   Link encap:UNSPEC  HWaddr 00-22-69-11-C8-88-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:95770 (95.7 KB)
          Interrupt:18 

so i supposedly have two wifi networks one is wifi0 and one is ath0, the problem is atheros is not set as ath0 but as wifi0, so how can i circumvent the problem that it becomes ath0. Yes I did try to change the setting in wicd from ath0 to wifi0 as well I restarted it, I also pressed on the slider for the wifi (altho we all know the lights aren't working), so pretty much i tried everything, I even reinstalled maverick from scratch, as my operating system has a partition so no personal files get deleted!

so the problem is I still can not connect to anything without wired connection. And no wireless network shows up! The wireless was working perfectly in lucid, however you just want to know how the newest netbook edition is :P

---

### Post by chandru1 on 2010-12-25
oh after doing what kurian has said, i have not made my wireless active. What has happened is this.

Madwifi has installed and the iwconfig command shows this.


lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chandru@Chandru1:~$ 


Before installing madwifi i had tried these things which i posted on [http://askubuntu.com/questions/18723/atheros-wireless-not-working](http://askubuntu.com/questions/18723/atheros-wireless-not-working) 

Now if i want to remove madwifi driver how can i do it? I would be glad if anyone can make my wirless to work as i am in great need of it

---

### Post by lentilman on 2011-02-15
I'm using ubuntu 10.04 and ath5001. the wireless was showing networks but i couldn't connect, i thought this might be an issue with the driver so I followed drpjkurian's method. However, I'm now having the same problem as Chandru1. Please help.

---

### Post by lentilman on 2011-02-15
I tried to install wicd using the two commands but i get an error. 

Setting up wicd-daemon (1.7.0+ds1-2) ...
 * Starting Network connection manager wicd                            [fail] 

Could this be the problem?

---

### Post by suniljoseph on 2011-03-03
Thanks Dr. Kurian. It worked!!!
Would you be any chance the same Kurian from dzlabz & CET?
Thanks anyway

---

### Post by suniljoseph on 2011-03-03
I guess I spoke too soon.
After a while the wireless connection got disconnected and then it says it can't find a wireless network. But my phone is connected to the same wifi network.

---

### Post by amunibabu on 2011-06-26
Awesome... you rock..

Was just playing with 'fn' buttons and turned off wifi.
never knew that playing with extra buttons on laptop would give me this much trouble..

You saved my day..
Thankyou..

---

### Post by Subito Piano on 2011-12-07
Blessings, blessings, drpjkurian...

I encountered a MAD ORNERY Atheros AR2413 802.11bg card (5005) on an Acer 3680 running Mint 9 (i.e., Ubuntu 10.04 LTS). Yours was the last hope before installing a PCMCIA card.  

For anyone following this, it didn't work until I installed WICD.  

Merci!!  :D

---

### Post by Subito Piano on 2011-12-08
AAAAAAAAAAAAARRRGGGGGGGGGGHHHHHHH!!!!!!!!!!

Like suniljoseph, i spoke too soon.  Weird, yesterday i restarted several times and it worked fine but today -- no go.  The same thing happened with the original Ath5 driver.  I can't figure this out.   :confused:

---

### Post by Subito Piano on 2011-12-09
[SIZE=3][COLOR=Red]**SUCCESS!!!!!!!!!!!**[/COLOR][/SIZE]

SOMEwhere i saw this:  Go to Synaptic, search for "Atheros" and download everything you hadn't -- in my case, two packages: hostapd (which i think was the one i needed) and collectd-core.  I installed both, rebooted, and i got on that ornery network!!!!!!!!!!!!!!  I will try more neworks and report back ONLY if i DO have problems.  :D   :D  :D

---

