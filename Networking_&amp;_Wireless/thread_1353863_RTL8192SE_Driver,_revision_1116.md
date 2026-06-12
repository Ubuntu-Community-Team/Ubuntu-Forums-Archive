---
title: "RTL8192SE Driver, revision 1116"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by LinuxFanBoi on 2009-12-13
Finlay found a place to host this, as it exceeds the forum's allowable attachment size.  Anyway, I hope this is of use

Download the driver:
[http://download39.mediafire.com/wxmcelayvx2g/1lwltyz4viy/rtl8192se_linux_2.6.0010.1116.2009.tar.gz]("http://download39.mediafire.com/wxmcelayvx2g/1lwltyz4viy/rtl8192se_linux_2.6.0010.1116.2009.tar.gz")

create a folder named ~/Realtek and unpack the driver there.

Open a terminal
```
cd ~/Realtek/rtl8192se_linux_2.6.0010.1116.2009
sudo su
make
make install

```

Reboot, enjoy.

---

### Post by chili555 on 2009-12-13
Please don't forget, you searchers, that when you get an updated kernel, or linux-image as we call it here, you will need to build the driver module against the newer kernel:```
cd ~/Realtek
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
```Your hint to do so will be that, when you boot into the new kernel, your wireless suddenly doesn't work!

---

### Post by LinuxFanBoi on 2009-12-13
Chili555,

Thank you for that addition,  could you please post the apt command to install build essentials and kernel sources as well?

---

### Post by chili555 on 2009-12-13
> **LinuxFanBoi said:**
> Chili555,

Thank you for that addition,  could you please post the apt command to install build essentials and kernel sources as well?Sure!```
sudo apt-get install build-essential linux-headers-generic
```These two are required in order to compile these things. Installation of *linux-headers-generic* will make sure that as you get a new kernel, the matching headers are also downloaded and installed.

---

### Post by LinuxFanBoi on 2009-12-13
> **chili555 said:**
> Sure!```
sudo apt-get install build-essential linux-headers-generic
```These two are required in order to compile these things. Installation of *linux-headers-generic* will make sure that as you get a new kernel, the matching headers are also downloaded and installed.

One last trick I will ask of you chili,;)

How can we get this driver included in the kernel so people don't have to go searching through hell or high watter for the driver that should 'just work?'

I've already asked Realtek to post the driver on their web site, which they informed me that they would not do, neglecting to state a reason why.

Also,  This driver seems to force the wireless adapter to use the lowest Tx/Rx power settings and there is no way to change that to my knowledge, without editing the source code, which I'm not proficient enough to do.  How can we fix this?

---

### Post by chili555 on 2009-12-13
> How can we get this driver included in the kernel Please check here: [http://www.ubuntu.com/community/ReportProblem](http://www.ubuntu.com/community/ReportProblem)> This driver seems to force the wireless adapter to use the lowest Tx/Rx power settings and there is no way to change Have you tried:```
sudo iwconfig wlan0 txpower 15
```...or whatever power your card supports? This is from man iwconfig:> [B]txpower
[/B]
              For cards supporting multiple transmit powers, sets the transmit power in dBm. If W is the power in Watt, the power in dBm is P = 30  +  10.log(W).   If  the value is postfixed by mW, it will be    automatically converted to dBm. In addition, on and off enable and disable the radio,  and  auto and  fixed  enable  and disable power control (if those features  are available).
              Examples :
                   iwconfig eth0 txpower 15
                   iwconfig eth0 txpower 30mW
                   iwconfig eth0 txpower auto
                   iwconfig eth0 txpower off

---

### Post by R3P71L3 on 2011-05-25
Running the Make command takes forever and freezes my computer. Do I have to update the kernel completely before I can run Make and Make Install without a problem, like running the apt-get  install build-essential linux-headers-generic? I'm currently running Ubuntu Lucid inside Linux 2.6.38. I've been fighting with this driver and wireless for two weeks and haven't been able to reach a resolution. Any and all help would be appreciated.

---

### Post by chili555 on 2011-05-25
> like running the apt-get install build-essential linux-headers-generic?Yes, absolutely.

---

### Post by R3P71L3 on 2011-05-26
Excellent, as soon as I get to a wired connection (Sunday night at midnight, yay for travel!) I'm going to give that a try.  Thank you!

---

