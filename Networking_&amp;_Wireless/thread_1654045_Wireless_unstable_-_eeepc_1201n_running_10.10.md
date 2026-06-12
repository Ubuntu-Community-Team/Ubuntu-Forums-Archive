---
title: "Wireless unstable - eeepc 1201n running 10.10"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by IGITIHI on 2010-12-27
My netbook model is Asus eeepc 1201n and I'm running Ubuntu 10.10 but I had the same problem while running 10.04: wireless disconnects and reconnects every 30 minutes or so and, after this has happened for a few times, it doesn't reconnect and keeps asking for the password. Any ideas?

Thanks in advance for your help!

---

### Post by richaoj on 2011-01-22
experiencing same problem.  I even upgraded to the newest driver from realtek (see modinfo below).  I even experience crashes every once in a while after wireless acts goofy.

richaoj@richaoj-1201N:~$ modinfo r8192se_pci 
filename:       /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/r8192se_pci.ko
license:        GPL
version:        0019.1207.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     B35243106478C16B758F56E
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35.8 SMP mod_unload modversions 686 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

---

### Post by StevoSn on 2011-02-17
Well, I somehow have the same annoying problem! has anybody solved it?
cheers stevo

---

### Post by netuse on 2011-02-21
Same problem here. No solution yet. Seems like (unresolved) bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588822)

You can tell, that it affects you too.

---

### Post by StevoSn on 2011-02-21
hey again! sorry for being so imprecise before..

it seems like I have the same problem.. if the wireless connects without any problem it will get disconnected after a while and then the password is asked.. then sometimes it works if I just try to reconnect, but most often it will keep on asking me for the password and fails connecting to the network.

I am using ubuntu 10.04 with Kernel 2.6.32-28-generic-pae on a macbook (don't know which model..) anyway, the network controller is a "Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)"

Ah yeah, this happens to the most wireless networks that I am using.. If I use mac OS X - everything works fine..

please, anybody, tell me what information are also important for this.. how can I actually find out which module is used for the WiFi connection..?

Cheers!
Stevo

---

### Post by beta0x64 on 2011-03-13
hey guys, I'm a bit new here, but I'm not new to this problem.

basically, I believe that the problem is your wireless card drivers.

after running lspci, your card should appear as:

```

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

```and you can download the new drivers from realtek: [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true)

you should download RTL8191SE VA2, then run the following
```
./configure
make
sudo su
make install
```that should do it! reboot.

---

### Post by Shriner on 2011-03-13
> **beta0x64 said:**
> hey guys, I'm a bit new here, but I'm not new to this problem.

basically, I believe that the problem is your wireless card drivers.

after running lspci, your card should appear as:

```

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

```and you can download the new drivers from realtek: [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true)

you should download RTL8191SE VA2, then run the following
```
./configure
make
sudo su
make install
```that should do it! reboot.
This makes the assumption that a person is also using the Realtek wirless card. Since mine is a Linksys wusb54g v4 and has the most current drivers, this solution doesn't work for me.  But thanks, gave me an idea of something to check......

---

### Post by Shriner on 2011-03-13
Found another thread, that reports that if you are using a kernel before 2.6.34 this problem occurs. It is reported that manually updating your kernel to 2.6.34 will cure the drops with all wireless cards. I'm not willing to verify this at this time because my ISP has oversold their DSL capablities and my connection sucks at this time. I guess I'm fortunate that I have a WET-11 to use in the interim.

Instructions for manually updating your kernel can be found @
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("http://ubuntuforums.org/view-source:https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

You can determine your current kernel with uname -a

---

### Post by SeijiSensei on 2011-03-13
> **Shriner said:**
> This makes the assumption that a person is also using the Realtek wirless card. Since mine is a Linksys wusb54g v4 and has the most current drivers, this solution doesn't work for me.  But thanks, gave me an idea of something to check......

I have that Linksys device, and it was very unstable with the kernel in Lucid.  Eventually I upgraded to Maverick which improved the situation considerably.  That said, I find it necessary to pull the USB cable out of the adapter every 12-24 hours and force a reconnection. 

I'm using kernel 2.6.35-27-generic (amd64) on 10.10.  Kernels past 2.6.35-22 seemed to work for me.

My daughter's 1201n seemed to work fine out-of-the-box with Maverick as well.

---

### Post by Shriner on 2011-03-13
I may have found the culprit.....power saving enabled.

Check with "iwconfig"

If power saving is on, disable with "sudo iwconfig wlan0 power off"

(assuming that yours is wlan0)

---

### Post by Murrquan on 2011-03-15
I'm using a Compaq Presario CQ62-219WM and having the same problem. It's gotten worse since I updated to the Natty alpha.

I tried downloading and installing the drivers, but I got a "implicit declaration of function ‘init_MUTEX’" error, which some web searching suggests may be due to a kernel incompatibility. I'm using the latest, at any rate.

Going to try Shriner's "sudo iwconfig wlan0 power off" fix and see how that works. What are the ramifications of turning off power saving -- will I just wear down the battery faster with wi-fi turned on? And will I have to set this command to run every time my notebook starts up?

---

