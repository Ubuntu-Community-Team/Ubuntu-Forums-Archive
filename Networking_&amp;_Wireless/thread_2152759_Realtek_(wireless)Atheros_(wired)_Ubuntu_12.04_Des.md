---
title: "Realtek (wireless)/Atheros (wired) Ubuntu 12.04 Desktop Toshiba Satellite S855D-S5148"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by agentofcode on 2013-06-08
I'm needing help to set up my wired/wireless networks on my Toshiba Satellite.
[I]
lspci -nn | grep -e 0200 -e 0280 Returns[/I]
> 
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)


Please guide me from here, Thanks!

---

### Post by chili555 on 2013-06-08
Let's take the easy one first. Does the module rtl8192ce exist in 12.04?```
modinfo rtl8192ce
```Is it already loaded?```
lsmod | grep rtl
```Do you need firmware?```
dmesg | grep rtl
```If you don't have rtl8192ce, then I'm going to recommend you install Ubuntu 13.04.

---

### Post by agentofcode on 2013-06-08
**modinfo rtl8192ce** Returns
> 
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     40628D8F1554C378D140D79
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)



**lsmod | grep rtl** Returns
> 
rtl8192ce              58779  0 
rtl8192c_common        49512  1 rtl8192ce
rtlwifi                76086  1 rtl8192ce
mac80211              555198  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              208382  2 rtlwifi,mac80211


**dmesg | grep rtl** Returns
> 
[   10.163519] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
[   10.163521] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[   10.322230] rtlwifi: Firmware rtlwifi/rtl8192cfwU_B.bin not available


---

### Post by varunendra on 2013-06-09
Please download the attached file > copy it to your Desktop.

Then Right-click > click "Extract Here" to extract the required firmware file.

Now open a terminal and enter the following command to copy it to correct location (you may just copy-paste it in terminal) -
```
sudo cp ~/Desktop/rtl8192cfwU_B.bin /lib/firmware/rtlwifi/
```

Then -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

If the wireless still remains inactive, post back the result of "dmesg | grep rtl" again.

If it makes it work, you can safely delete the downloaded and extracted files.


**PS:**
Greetings Dr.Chili ! :)

---

### Post by chili555 on 2013-06-09
Exactly! Also note the disclaimer:> This B_CUT device may not work with kernels 3.[COLOR="#FF0000"]6[/COLOR] and earlierYou are running:> 3.[COLOR="#FF0000"]5[/COLOR].0-23-genericYour wireless may work well or not at all. We'll see.

---

### Post by agentofcode on 2013-06-09
AWESOME!

I am posting this from the now working wireless connection on my laptop.

**Question:** I'm unable to connect to the router's 5ghz signal. I can only use the 2.4ghz signal. Is there an extra step I must take to make this happen?

---

### Post by chili555 on 2013-06-09
I'm not exactly sure what to do but let's look for clues:```
dmesg | grep -e rtl -e 80211 -e wlan
```@varunendra--

Are you ready to get his ethernet going? What do you think? linux-backports-modules??

---

### Post by varunendra on 2013-06-09
> **chili555 said:**
> @varunendra--

Are you ready to get his ethernet going? What do you think? linux-backports-modules??

Yeah that would have been the next step (coming from you I thought :)), or installing the 3.8 kernel from repositories ("linux-generic-lts-raring" package).

But now as you too know from his PM to us, he needs to get another issue solved first : [http://ubuntuforums.org/showthread.php?t=2152956](http://ubuntuforums.org/showthread.php?t=2152956) , (sigh..) thanks to the 'working wireless' :P

@ agentofcode,
Good luck with your freezing issue.
Keep the downloaded firmware handy in case you decide to do a fresh installation of 12.04.

---

### Post by agentofcode on 2013-06-11
I gave in and attempted v13.04. All WiFi and wired connections work now. Even the n (5.4ghz) works with no trouble. Thanks for your help!

---

### Post by zzadrian01 on 2013-07-06
Hi I have the same exact problem (except my computer is a sligthly differnet model:  S855D-SP5262Lm). 
I got the same responses from
**modinfo rtl8192ce**
**lsmod | grep rtl**
**dmesg | grep rtl**
 I followed the instructions in this post but i still cant use wired or wirless networks.
(Now after **modinfo rtl8192ce **i get the same response and after** lsmod | grep rtl**  and **dmesg | grep rtl** i get no response)

thak you
greetings

---

### Post by zzadrian01 on 2013-07-06
im not really good at this so maybe, is just an implicit step that i have still to do, to relauch the network  or something like that.
(i rebooted de computer, still not working)

---

### Post by varunendra on 2013-07-07
Welcome to the forums zzadrian01 ! :)

I'd suggest you post your own thread in [this]("http://ubuntuforums.org/forumdisplay.php?f=336") very same section, with the details of your problem and whatever you have tried so far.
Along with the details, please also post the result of "wireless_script" as requested in this post : [http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

Once you have started the thread and posted all that info there, give us a link to your thread.

Thanks !

---

### Post by chili555 on 2013-07-07
> **zzadrian01 said:**
> Hi I have the same exact problem (except my computer is a sligthly differnet model:  S855D-SP5262Lm). 
I got the same responses from
**modinfo rtl8192ce**
**lsmod | grep rtl**
**dmesg | grep rtl**
 I followed the instructions in this post but i still cant use wired or wirless networks.
(Now after **modinfo rtl8192ce **i get the same response and after** lsmod | grep rtl**  and **dmesg | grep rtl** i get no response)

thak you
greetingsI suggest you start your own new thread and include:```
lspci -nn | grep 0280
```Thanks.

---

### Post by praseodym on 2013-07-07
Check this one

[http://ubuntuforums.org/showthread.php?t=2157151&p=12719872#post12719872](http://ubuntuforums.org/showthread.php?t=2157151&p=12719872#post12719872)

Maybe you try kernel 3.9 as escribed there, too.

---

