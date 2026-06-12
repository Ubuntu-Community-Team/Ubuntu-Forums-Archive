---
title: "Wireless hookup takes forever"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by luiznetto on 2011-11-30
I use Ubuntu 8.04 on my Acer Aspire 5315 laptop. I cannot upgrade my system, because my hardware won't accept any Ubuntu newer than this one.

The wireless card is Atheros, and my driver is ndiswrapper. I believe there is another driver for this wireless card, I believe it's called Ath9 or something, but I don't know if I can install it on my system.

But the problem is: I recently moved, and in my old house I shared a wireless internet connection with some other people (the owner gave me the password). It worked fine for more than 2 years. In this new house, though, I had to purchase and install my own internet connection; it's Comcast, and the wireless router is Netgear. I made the following setup:

Wireless Network

Name (SSID):  myownname
Channel:      Auto
Mode:         Up to 65 Mbps b/g/n mixed mode (neighbor friendly)

Security Options

WPA-PSK [TKIP] + WPA2-PSK [AES]
Password: myownpassword

The problem is, when I boot, the wireless hookup takes forever (with Gnome Network Manager (nm applet 0.6.6)). After several failed attempts, it finally hooks up, and I can use it all day without any problems.

My friend here by my side uses Linux Mint Helena on his laptop, and he can hook up without any problems at all.

When I put Security Options: None, I don't have the same problem. The hookup is fast. But then I have an open network that anybody can join without a password. Since I don't know those people that are using my network, and I don't know what they are doing, that gives me the creeps, even though I was almost convinced by this guy

[http://www.schneier.com/blog/archives/2008/01/my_open_wireles.html](http://www.schneier.com/blog/archives/2008/01/my_open_wireles.html)

to just use an open network; after all, if Starbucks and the Public Library do it, why can't I? But when I see somebody else is using my network, and I don't know what they are doing, I do get nervous.

Anyway, does anyone have an idea? Why isn't my automatic hookup after boot working as expected? Why does it take so long, and fail many times before it succeeds? Is my system having trouble with the WPA encryption? Any help will be deeply appreciated.

Luiz

---

### Post by luiznetto on 2011-11-30
After a lot of tweaking, I am convinced this is an encryption problem. It works fine with an unencrypted network, but when I try either WPA or WEP, it has trouble connecting. But the problem is, I did share an encrypted network in the other house with a hexadecimal key, and never had any problem. What's going on?

---

### Post by luiznetto on 2011-12-01
I changed from WPA to WEP and now it works. Definitely, Ubuntu 8.04 has trouble with WPA. Yea, now I remember, in the old house, the wireless network was WEP encrypted.

---

### Post by praseodym on 2011-12-01
Hi,

the windows driver used by ndiswrapper makes the problems, or the firmware of it. For Hardy you can use an older file of "linux-wireless-old" to compile ath9k:

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/12/compat-wireless-old-2008-12-31.tar.bz2
tar jxvf compat-wireless-old-2008-12-31.tar.bz2
cd compat-*
make
sudo make install
```
Ndiswrapper needs to be uninstalled for that:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```
Reboot and check:
```
iwconfig
dmesg | grep ath
lsmod
sudo iwlist scan
lspci -nn
```

---

### Post by gordintoronto on 2011-12-01
Have you considered trying the current Xubuntu or Lubuntu? If you don't have a problem with memory, is it the video adapter? An unsupported version of any OS is just asking for trouble.

WEP is better than no security at all, but not by much. You could also tell your router not to broadcast its SSID, and set up filtering by MAC address, but all those things are less secure than you would imagine.

---

### Post by luiznetto on 2011-12-02
Thanks to **praseodym**: your recipe worked beautifully. I just tested it, and all is working flawlessly: WEP, WPA and WPA2.

As to **gordintoronto**: Thanks but no thanks. I never really understood why a new version has to be launched every 6 months. My Hardy Heron is wonderful and does everything I want it to do. It is a lot of hard work to install a new system. It's not just the installation itself, but there is a lot of tweaking and configuring that has to be done. There is also a lot of software that I use and is not installed by default and has to be installed, and sometimes I don't even know if there is a new version of that particular package that will work with the new OS. Much software that is installed by default that I don't use needs to be uninstalled, so as not to occupy idle space on my disk. All of this is time-consuming and often frustrating. And every new installation comes with new bugs - things that used to work fine suddenly break. And, to top it all off, every time I try to upgrade my system, the installation stalls midway due to hardware incompatibilities.

So I guess I will be using Ubuntu 8.04 as long as my hardware lasts.

But thanks anyway.

Luiz

---

