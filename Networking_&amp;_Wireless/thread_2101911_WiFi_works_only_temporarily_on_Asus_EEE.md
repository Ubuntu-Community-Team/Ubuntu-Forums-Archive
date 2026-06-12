---
title: "WiFi works only temporarily on Asus EEE"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by BrandonSk on 2013-01-05
Dear all / Chili,

I went through the procedure as described in this thread:
[http://ubuntuforums.org/showthread.php?p=12440411](http://ubuntuforums.org/showthread.php?p=12440411)

As Chili suggested, I am starting a new thread so that may hopefully be useful for other people as well.

Here is of lspci -nn | grep 0280 :
```
lspci -nn | grep 0280
01:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
```Thanks for help.
Brandon.

---

### Post by Pjotr123 on 2013-01-05
Try disabling power management for your wireless card:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card)
(item 2.1, right column)

---

### Post by chili555 on 2013-01-05
> Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]I assume you are using the driver rt2800pci and haven't compiled or otherwise installed anything different; confirm:```
lsmod | grep rt2
```If so, please try:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If it helps, we can make it persistent.

---

### Post by coldraven on 2013-01-05
I'm running Xubuntu 12.10 on my eee pc 900 with no problems, the wifi seems to work perfectly.
I did update the BIOS which improved the battery life, the fan is running a lot less.
I posted how to here:
[http://ubuntuforums.org/showpost.php?p=12410115&postcount=8](http://ubuntuforums.org/showpost.php?p=12410115&postcount=8)

---

### Post by BrandonSk on 2013-01-05
@Chili
I am using the driver you suggested. In fact, as mentioned before, I have followed the previous guide, so I have downloaded the same stuff. The version of the driver is 2.4.0 I believe.

```
lsmod | grep rt2
rt2860sta             769209  0 
rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48875  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
eeprom_93cx6           12687  1 rt2800pci

```

sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
The above returns nothing.
Oh... I see, it first disconnected me and now has reconnected. I will unplug the cable and get back to you within few minutes. It does "go off" within 30 minutes.

@Coldraven
Thanks for the link. I will check that tutorial. If nothing else, battery life and fan sounds promising too.

@Pjotr123
Thank you for the suggestion. I think my powermanagement for wifi card is off. At least I remember seing it as output of one of the commands before (I mean the previous thread that I have followed).

Thanks again to all.
Cheers,
Brandon.

PS: Unplugging cable now. Fingers crossed.

---

### Post by BrandonSk on 2013-01-05
Well,

I am sorry to disappoint, but this time it worked only for a minute or so. When I removed and reinserted the module with those two commands above, it again started working but again only for a very short time.
On the third attempt it was not working immediately after the 2 commands were executed.
:(

B.

---

### Post by BrandonSk on 2013-01-06
So I did try the procedure from scratch.

This time not just copy/paste but also looking at the steps and thinking, what is the aim and thus adjusting few commands. Particularly I was messing with the step #6 - the "mv" and revised "cp" commands.
With the mv I have renamed the rt2860sta.ko into rt2860sta.ko.dist which resided in my .../net/wireless
Looking at the revised cp and my directory structure, I first created a directory called "rt2860" in my .../staging/ and then copied the rt2860sta.ko into that newly created directory.

The "..." is */lib/modules/3.2.0-35-generic/kernel/drivers/* and yes, the 3.2.0-35-generic is what *uname -r* returns.

Result: still the same situation - wifi not working, although connected.

For better orientation, I will now post output of several commands, maybe you can spot something.

```
dmesg | grep -e -ra0 -e rt2
[   20.714703] rt2800pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   20.714730] rt2800pci 0000:01:00.0: setting latency timer to 64
[   20.789605] Registered led device: rt2800pci-phy0::radio
[   20.789963] Registered led device: rt2800pci-phy0::assoc
[   20.790187] Registered led device: rt2800pci-phy0::quality

``````
lsmod | grep rt2
rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48875  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
eeprom_93cx6           12687  1 rt2800pci
``````
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MI6_guest"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:5D:4E:B4:05:C9   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

eth0      no wireless extensions.
```
**What is this Invalid misc:10 ? **Does it lead to anything?

```
locate rt2860sta
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/rt2860sta.ko.dist
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/.rt2860sta.ko.cmd
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/.rt2860sta.mod.o.cmd
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/.rt2860sta.o.cmd
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.ko
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.mod.c
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.mod.o
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.o
/home/brano/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/.tmp_versions/rt2860sta.mod
/lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2860sta.ko
/lib/modules/3.2.0-35-generic/kernel/drivers/net/wireless/rt2860sta.ko.dist
/lib/modules/3.2.0-35-generic/kernel/drivers/staging/rt2860sta.ko.dist
/lib/modules/3.2.0-35-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
``````
modinfo rt2860sta
ERROR: modinfo: could not open /lib/modules/3.2.0-35-generic/kernel/drivers/net/wireless/rt2860sta.ko: No such file or directory
``````
modprobe rt2860sta
FATAL: Could not read '/lib/modules/3.2.0-35-generic/kernel/drivers/net/wireless/rt2860sta.ko': No such file or directory
```I understand the last 2 errors, as I have renamed the module to have ".dist" at the end.
What I do not understand is, how come the wifi gets connected, even when the module cannot be loaded?!

Well, any help is still greatly appreciated.

Cheers,
Brandon.

---

### Post by chili555 on 2013-01-06
If it's connected using rt2800pci, why, oh why did you go to the effort to compile the genetically inferior rt2860sta? I must be confused...

---

### Post by BrandonSk on 2013-01-06
> **chili555 said:**
> If it's connected using rt2800pci, why, oh why did you go to the effort to compile the genetically inferior rt2860sta? I must be confused...


Ooops. Most likely because I have very limited knowledge of linux and its drivers :(
The reason was that it suddenly stopped working out of nothing (it used work before but it must have been some update). So I started searching for solution.

Is there a simple way to get rid of all the drivers and let the system install whatever it prefers? If not, I am quite ready to do reinstall.

Thanks.B.

---

### Post by chili555 on 2013-01-06
> Is there a simple way to get rid of all the drivers and let the system install whatever it prefers?Sure.```
cd Desktop/RT2860folder  [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
sudo make uninstall
sudo modprobe -r rt2860sta

```Reboot and let us have your report. If there is anything not working, we'll address it, but older, inferior drivers won't help.

---

### Post by BrandonSk on 2013-01-06
Dear Cilli,

thanks for your help so far. Just before I hit submit reply, I thought we finally have some progress. But now I am editing the post, as unfortunately wifi stopped working again.
Here is what I have written before and I will add a small update at the end:

I did remove the rt2860sta module as you have suggested. I did couple of reboots and removed any reference to rt28060sta I could find (via locate).

WiFi still did not work, although connected.

So I went inside my router and disabled wifi security - voila, wifi has been running now for about 20 minutes.

Here's an output of iwconfig now (Invalid misc is now down to 3, whatever it is :) )
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MI6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: CC:5D:4E:B4:05:C8   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

eth0      no wireless extensions.
```

and here is output of sudo modinfo rt2800pci
```
filename:       /lib/modules/3.2.0-35-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B814F1B7538F8B99ECC7D4E
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.2.0-35-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```

I would like to use WPA2/AES. Before I do any changes, I will wait for any suggestions you may have.

After wifi stopped working:
While I was writing the post, I noticed that I have ping running in the terminal, constantly pinging the gateway. I stopped it to get output of the commands above. By the time I finished the post, the problem reappeared (retrying ping did not help, as I cannot ping gateway anymore).
Just for your info, on the same laptop I can boot also into Win XP. There, I have no problem with the wifi - this is just to rule out the hw or router problem.

Thanks again.
Cheers,
B.

---

### Post by chili555 on 2013-01-06
My suggestion is at post #3.

---

### Post by BrandonSk on 2013-01-06
> **chili555 said:**
> My suggestion is at post #3.

I tried that again but it did not help.
At that moment I thought that it just may be easier to save us some time trying to troubleshoot this, so I went ahead and made a fresh install of xubuntu (including formating the partition where system resides - so no upgrade or anything like that).

But to my great disappointment, that did not resolve the problem! So now I am pulling my hair out. I did try again the suggested two commands from post #3 - no change.

Well, I just may go and get a good sleep on this first, as it is close to 1:30 am here. If you come up with any idea of what I could try next, I will be grateful. Tomorrow I will post the output of the commands as I did before, so that you can see what has changed (if anything) after the clean set-up.

Thanks for the help so far.
Good night :)
B.

---

### Post by chili555 on 2013-01-06
Good evening. We'll attack it again after a nights rest.

---

### Post by BrandonSk on 2013-01-07
Hello,

show must go on and so does the puzzlement...
Believe it or not, I have been enjoying wifi connection now for about 3 hours without any problem. But I am at work now... when I tried back home in the morning, the wifi still would not communicate.

So next I checked the encryption settings we are running here at work. There is WPA2/WPA with TKIP. Back home I have pure WPA2 with AES. This could be an indication, but how come it did not work with wireless security set to none?!
Why also enabling the nohwcrypt for the module did not help? It must be some strange combination of this eee, my router, setup, and everything together.

So to sumarize:
My home wifi setup (WPA2+AES) + this Asus EEE (it's 1000H model) + WinXP = no problem
My home wifi setup (WPA2+AES) + this Asus EEE + Xubuntu 12.04 = not working
My home wifi setup (no security) + this Asus EEE + Xubuntu 12.04 = not working 
Work wifi setup (WPA/WPA2+TKIP) + this Asus EEE + Xubuntu 12.04 = no problem

Below is the output of selected commands (wifi is working at the moment, as I am connected to work wifi):
```
dmesg | grep -e ra0 -e rt2
[   13.683709] rt2800pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.683734] rt2800pci 0000:01:00.0: setting latency timer to 64
[   13.902727] Registered led device: rt2800pci-phy0::radio
[   13.905595] Registered led device: rt2800pci-phy0::assoc
[   13.905727] Registered led device: rt2800pci-phy0::quality
[  895.478218] rt2800pci 0000:01:00.0: PCI INT A disabled
[  896.377655] rt2800pci 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[  896.377687] rt2800pci 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbef0000)
[  896.377699] rt2800pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
[  896.377712] rt2800pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[  896.379348] rt2800pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  900.244870] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

```
lsmod | grep rt2
rt2800pci              18340  0 
rt2800lib              53264  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48805  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178679  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci
```

```
modinfo rt2800pci
filename:       /lib/modules/3.2.0-29-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     819E0C83946C477B1C23972
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.2.0-29-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```

```
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"zasadacka"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:3A:99:AB:9C:61   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:59   Missed beacon:0

eth0      no wireless extensions.
```

I will try later tonight to change settings at home to those here at work. Although I would not be entirely happy, it could solve the situation. But I am also up for the challenge for getting it to work no matter what the security set-up is.

Cheers,
B.

---

### Post by Pjotr123 on 2013-01-07
I see in the iwconfig output that power management is still on for wlan0. Have you tried whether disabling power management for your wireless chipset helps, like I suggested previously?

That particular tweak often solves problems like these, in my experience.

---

### Post by BrandonSk on 2013-01-07
> **Pjotr123 said:**
> I see in the iwconfig output that power management is still on for wlan0. Have you tried whether disabling power management for your wireless chipset helps, like I suggested previously?

That particular tweak often solves problems like these, in my experience.

True. Thanks. That is because I did a fresh install of the system. So before it was disabled and now I have not changed it yet. I will try your solution and post results later on (despite that the wifi works with Power management on at work).

Thanks again.
Cheers,
B.

---

### Post by chili555 on 2013-01-07
> [  900.244870] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardwareOld Chili doesn't like this one bit. I have no clue how to fix it and I've seen it for years. Arrggh!

There is an updated rt2800pci available.```
sudo apt-get install linux-backports-modules-cw-3.4-precise-generic
```Reboot and let us have your report.

Changing your home network to TKIP is certainly a valid experiment.

---

### Post by BrandonSk on 2013-01-07
> **chili555 said:**
> 
There is an updated rt2800pci available.```
sudo apt-get install linux-backports-modules-cw-3.4-precise-generic
```Reboot and let us have your report.


YOU ARE A KING!
 Well, first things first...

After I got home, I tried:
1) Disabling power management -> reboot -> no joy
2) Losen security on wifi to resemble the one at work -> no joy
3) Disable firewall (just in case) -> no joy

[B]4) Updated rt2800pci driver as in quote above -> joy joy joy

[/B]5) Returned to WPA2-PSK + AES setting on wifi -> joy continues

It's been running like this for past half hour, so still a bit of caution. But based on previous experience I am certain this is solved. You can even see much quicker responses of wifi connecting or pages being loaded. So there was definitely something wrong with old driver.

Chili, I know you've been told many times, but you are a true hero and expert. I was already feeling bad about wasting your time so much and wanted to give-in, but the enthusiasm and determination I could feel through the screen :) from you kept me going too!
But I also want to thank Pjotr123 and Coldraven for their suggestions, which hopefully will help some other people too.

I am marking this solved and hopefully will not need to return here (unless the 204 updates that are pending now will ruin something again ;) ).

Once again, thanks to all of you and +1 happy ubuntu user!
Great community.

Cheers,
Brandon.

PS: Where do I mark this solved? -> Got it.

---

### Post by chili555 on 2013-01-07
Awesome! Your experience will hep others that are troubled by rt2800pci. Thank you for your perseverance. I greatly enjoy what I do and I don't consider it a waste at all. Thanks for your kind comments.

---

