---
title: "Wireless hardware switch/hotkey fault"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by madrabbi on 2011-06-08
Hi everyone.

Have a problem with Ubuntu on my Dell Latitude D520. I'll be as detailed, but concise, as I can!

The machine previously ran XP and had no issues switching the wireless hardware on and off using the hotkey.
After installing Ubuntu on the machine (single boot, XP was removed) I used it for months wirelessly with no problems - no special measures needed to get wireless working, it worked 'straight out of the box' as it were.

Recently I connected the machine to my work's network via ethernet. At work the proxies are broken, so wireless only functions properly on work machines. However, the Dell's wireless "overrode" the ethernet and no matter what I tried, I couldn't get the wired connection to take the priority.  I needed to download something onto the machine urgently so I turned wireless hardware off using the hotkey - and I haven't been able to get it back on again since :(

I have gone into the BIOS setup and changed 2 settings: 1 to ensure the hotkey is set to switch the hardware on and 1 to set it to switch on the wireless hardware only (and not bluetooth simultaneously). Couldn't find anything else in BIOS that looked a likely candidate to help the situation, so I left it there.


After that failed to fix things, I decided to do a full and complete install of Kubuntu onto the machine (I was wanting to try KDE anyway) to see if it would pick up the correct settings as it had when I installed Ubuntu for the first time, but alas, no joy.

And so here I am, hoping somebody here can share a little knowledge and help get me back up and connected.

Thanks in advance!
:p

---

### Post by chili555 on 2011-06-08
Dell laptops use a module that is supposed to recognize key presses and translate them into messages the kernel recognizes, something like, "Turn on the wireless, please." Here is some data about the module, named cleverly enough, dell-laptop:> $ modinfo dell-laptop
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/platform/x86/dell-laptop.ko
alias:          dmi:*svnDellComputerCorporation.:*:ct8:*
alias:          dmi:*svnDellInc.:*:ct9:*
alias:          dmi:*svnDellInc.:*:ct8:*
license:        GPL
description:    [COLOR="Red"]Dell laptop driver[/COLOR]
author:         Matthew Garrett <mjg@redhat.com>
srcversion:     49CF0CA9A0E65F5B2F1DF06
depends:        dcdbas
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 The trouble is, it doesn't always work very well and you can often get the wireless working by removing (!) the module. Let's do some diagnostics. Open a terminal and do:```
lsmod | grep dell
rfkill list all
```Is the module loaded? Is your wireless blocked=yes? If so, please try:```
sudo rmmod -f dell-laptop
sudo rfkill unblock all
```Now does your wireless work? If so, we can blacklist dell-laptop and make 'unblock' run at boot and you should be all set.

If my assumptions are wrong, post back and we'll dig deeper.

---

### Post by madrabbi on 2011-06-08
chili555 - that has fixed it - thank you so much!

report 1 showed wireless had a software block but no hardware block, report 2 had it the other way around.
After running your commands I managed to navigate my way around the rest of the settings needed to get back online.

Your wisdom is great, oh mighty Oracle ;)

---

### Post by chili555 on 2011-06-08
Thanks for your kind comments. Would you care to amend a couple of files so this is effective on boot?```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
gedit /etc/rc.local
```Add one line above exit 0```
rfkill unblock all
```Proofread carefully, save and close gedit.```
exit
```Enjoy and post back if we can help you further.

---

### Post by madrabbi on 2011-06-14
Thanks for the further suggestions, Chili.
I'm sure they'll be useful for any other people looking for solutions to this problem on Ubuntu too.

I'm running Kubuntu and so don't have gedit. However, interestingly, the solution you first provided for the temporary fix turned out to work permanently in Kubuntu - no further changes were necessary and it still works after several restarts.

Extra Guru points for you, sir ;D [SIZE=1](and apologies for the delayed feedback)[/SIZE]

---

### Post by tienchii on 2012-01-02
Hey, sorry to revive this old thread, I wasn't sure where I can start.

I have a Dell Latitude D520 as well, and running Ubuntu 11.10. My wireless did not work initially, and after deactivating the STA wireless driver and installing the B43 firmware instead (as per solution I found in other parts of the forums), I see the "wireless is disabled by hardware switch" message in the network connections pop down.

Apparently some quick Googling led me to this thread, but I followed chili555's instructions and did not successfully get the wireless working. What are the next steps I should take?

---

### Post by chili555 on 2012-01-02
Please open a terminal and show us:```
rfkill list all
dmesg | grep b43
lspci -nn | grep 0280
```Thanks.

---

### Post by tienchii on 2012-01-04
```
rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dmesg | grep b43
[    1.201352] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.201368] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    7.687817] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    8.751408] Registered led device: b43-phy0::tx
[    8.751437] Registered led device: b43-phy0::rx
[    8.751465] Registered led device: b43-phy0::radio

lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

---

### Post by chili555 on 2012-01-04
Please try:```
sudo rmmod -f dell-laptop
```If your wireless springs to life, then let's blacklist it:```
sudo su
echo "blacklist dell-laptop" >> /etc/modprobe.d/blacklist.conf
exit
```If not, post:```
lsmod | grep dell
```Thanks.

---

### Post by tienchii on 2012-01-04
Removing the module didn't seem to work. (I even tried turning off my wired connection and unplugging my Ethernet to make sure.)

Here's my lsmod:

```
lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
wmi                    18744  1 dell_wmi
```Thanks.

---

### Post by chili555 on 2012-01-04
Ahh! It's dell-wmi and not dell-laptop. Hey, I took my best shot.> Please try:
```
sudo rmmod -f dell-[COLOR="Red"]wmi[/COLOR]
```

If your wireless springs to life, then let's blacklist it:

```
sudo su
echo "blacklist dell-[COLOR="Red"]wmi[/COLOR]" >> /etc/modprobe.d/blacklist.conf
exit

```


---

### Post by tienchii on 2012-01-04
Wow I feel like an idiot. All I had to do the whole time was to use the Dell shortcut for turning on/off the wireless (Fn+F2). For some reason I made the assumption that it wouldn't work (because I tried using it a number of times before, likely with a different wireless driver) and it didn't occur to me to try until now. I did not even have to remove any modules to make this work

Still, thanks a lot for your help! Hopefully my nearsightedness will allow others viewing this thread not to make the same mistake of neglecting the Fn+F2. :)

---

### Post by Zetman8383 on 2012-01-04
Hello
I'm having a similar problem with my HP

I can't enable the wireless switch again 

> rfkill list all
rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


lspci -nn | grep 0280
07:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)


What should I do?

---

### Post by chili555 on 2012-01-04
Please try:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
```Does it now work? If so, we can make it permanent.

---

### Post by Zetman8383 on 2012-01-05
Still nothing
 I forgot to say, I have a hp g60 running 10.10

---

### Post by chili555 on 2012-01-05
> **Zetman8383 said:**
> Still nothing
 I forgot to say, I have a hp g60 running 10.10Show us, please. Post the results of these commands:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Errors, warnings and specific output may be informative. Thanks.

---

