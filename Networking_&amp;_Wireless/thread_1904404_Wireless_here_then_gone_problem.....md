---
title: "Wireless here then gone problem...."
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by voradeaur on 2012-01-04
My problem seems to be slightly different than that of everyone else I've seen.  I have an Acer Aspire 7741Z series laptop with the Atheros wireless card setup. I recently installed 11.10 with Windows 7 as the main OS (just to see if I could get Ubuntu to work properly this go around) and had wireless internet almost immediately. I figured everything was going well until I restarted from service packet updates... I could not get internet. After this situation if I reset the computer I have a 1 in 10 chance on startup that I have internet... The other 9/10 times It will attempt to connect to my router about 5-6 times before giving up... What could I do to get this issue resolved? I love the layout of Ubuntu and would like to continue using it.

PS... I have already checked to see if rfkill was blocking and it is not.

---

### Post by praseodym on 2012-01-04
Hi there.

Check with

```
lspci -nnk | grep -iA2 net
lsmod | grep ath
```
which driver is loaded ([COLOR="Red"]ath5k[/COLOR] or [COLOR="Lime"]ath9k[/COLOR]). Then deactivate the hardware encryption of the driver via:
```
echo "options [COLOR="Red"]ath5k[/COLOR] nohwcrypt=1" | sudo tee /etc/modprobe.d/[COLOR="Red"]ath5k[/COLOR].conf
sudo modprobe -rfv [COLOR="Red"]ath5k[/COLOR]
sudo modprobe -v [COLOR="Red"]ath5k[/COLOR]
```
Change [COLOR="Red"]ath5k[/COLOR] to [COLOR="Lime"]ath9k[/COLOR] if this is your driver.

---

### Post by voradeaur on 2012-01-05
So... I did what you told me and it reset the card... after it reset, I was unable until now to get internet back on the laptop lol. Is there any other ideas for this?

---

### Post by praseodym on 2012-01-05
Please show the outputs of the first 2 commands

---

### Post by jibawakee on 2012-01-05
I had this problem but try this in the terminal 

sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic

Helped after that reboot then you should be fine if you still have problems let me know

---

### Post by voradeaur on 2012-01-05
Ok I will go attempt it now. Thanks again, I will reissue the commands and post them up in just a few.  I just have to go back to Windows 7 in order to get back online... ugh I hate wireless issues. I can handle any other issue linux can throw at me cause I can just cope with it.. But wireless, that stings lol

---

### Post by voradeaur on 2012-01-05
michael@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Aspire 7740G [1025:033d]
	Kernel driver in use: tg3
--
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Quanta Microsystems, Inc Device [1a32:2309]
	Kernel driver in use: ath9k
michael@ubuntu:~$ 
michael@ubuntu:~$ lsmod | grep ath
ath9k                 127538  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
michael@ubuntu:~$ 
michael@ubuntu:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for michael: 
options ath9k nohwcrypt=1
michael@ubuntu:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/net/wireless/cfg80211.ko
michael@ubuntu:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.0.0-14-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
michael@ubuntu:~$ 



For Jibawakee...
michael@ubuntu:~$ sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-2.6.39-natty-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-2.6.39-natty-generic'

---

### Post by jibawakee on 2012-01-05
> **voradeaur said:**
> michael@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Aspire 7740G [1025:033d]
    Kernel driver in use: tg3
--
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Quanta Microsystems, Inc Device [1a32:2309]
    Kernel driver in use: ath9k
michael@ubuntu:~$ 
michael@ubuntu:~$ lsmod | grep ath
ath9k                 127538  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
michael@ubuntu:~$ 
michael@ubuntu:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for michael: 
options ath9k nohwcrypt=1
michael@ubuntu:~$ sudo modprobe -rfv ath9k
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.0.0-14-generic/kernel/net/wireless/cfg80211.ko
michael@ubuntu:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.0.0-14-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
michael@ubuntu:~$ 



For Jibawakee...
michael@ubuntu:~$ sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-2.6.39-natty-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-2.6.39-natty-generic'
You said you tried this copy exactly 
```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```

---

### Post by jibawakee on 2012-01-05
Try this [CODE]
sudo service gdm stop
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
sudo service gdm start

---

### Post by voradeaur on 2012-01-05
im a flat noob when it comes to linux... im seriously copying and pasting these codes unless i am required to alter them in any way.... copying this discussion board to a word docoument and opening it back up in ubuntu... lol

---

### Post by voradeaur on 2012-01-05
Ok... I have internet access this boot cycle... If there is anything you need directly from linux that doesnt require me to reset the wireless card.. speak now or for ever hold your peace... lol. Will your commands stop all transmission jiba?

---

### Post by jibawakee on 2012-01-05
You should be good from there

---

### Post by voradeaur on 2012-01-05
Negative... I will get internet like I stated in the first post 1 out of every 10 or so boots.... That was one of the fluke bootups that would allow me to get internet lol... I cannot connect again.

---

### Post by voradeaur on 2012-01-06
I know this may or may not matter.... But when I went into 2d mode to play around... I got internet connection again..... This could be completely irrelevant due to that only being mainly graphics oriented... but i have internet at the moment... lol

---

### Post by voradeaur on 2012-01-06
Ok New update.... If I do not turn off the computer... Internet does not go away. It is still connected just as it was last night when it did. What could cause it to just randomly decide to connect one boot, and not the next 10?

---

### Post by JavaQueen on 2012-01-21
I am having a similar problem. I've upgraded to 11.10 on my Aspire laptop and I also have the ath9k wireless driver. My Internet connection is really spotty. It's extremely slow and often just cuts out.

To be clear, I was previously running 10.10. The last few weeks, my wireless connection started to lag. Thinking now was a good time to upgrade and hoping that would fix the problem, I did a clean install of 11.10. Still problems with my wireless card. If you find a solution, please let me know.

Thanks!

---

### Post by praseodym on 2012-01-21
Hi JavaQueen,

deactivate the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Also try pure WPA2-AES encryption, if possible.

---

### Post by JavaQueen on 2012-01-21
Thank you so much! Everything seems to be working just fine now!

---

