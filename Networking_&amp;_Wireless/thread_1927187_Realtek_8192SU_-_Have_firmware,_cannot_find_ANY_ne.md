---
title: "Realtek 8192SU - Have firmware, cannot find ANY networks"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by Dao333 on 2012-02-17
Hi All,

I've had a trawl through the forums and Google and I can see a lot of people have had some luck getting this particular network card working but none of the solutions have worked for me.

I'm using Ubuntu 10.10 and the network card is just a bog standard realtek 8192S usb card. I could buy another one but refuse to on principle ;)

I can find the device using lsusb, have installed the firmware, checked it's in the correct directory, tried ndiswrapper, nothing's worked at all.

It's had no trouble recognising the device, I just can't get it to find any networks at all.

I'm currently using my Galaxy Ace as a tethered modem to try and look up solutions, which seems to use AutoEth0 (I do disconnect this when I try to use the wireless card).

I'm newish to Linux so not fluent in terminal commands so might need some hand-holding on the right commands ;)

Will be happy to post any logs/messages needed. The only ones I can think that might be useful at this stage is dmesg | grep 819:

root@Firefly:~/Desktop# dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
[   21.081955] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   21.081991] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   21.082720] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192su'
[   21.083183] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192su; check system log for messages from 'loadndisdriver'

OR:

root@Firefly:~/Desktop# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 002: ID 04e8:689e Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Firefly:~/Desktop# 

Anything that will stop me tearing my hair out any longer would be appreciated!!!

Ta muchly folks.

---

### Post by praseodym on 2012-02-17
Try this driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_dkms.tar.gz
sudo tar xvf rtl8712u-2.6.6.0.2_dkms.tar.gz -C /usr/src
sudo dkms add -m rtl8712u -v 2.6.6.0.2
sudo dkms build -m rtl8712u -v 2.6.6.0.2
sudo dkms install -m rtl8712u -v 2.6.6.0.2 
echo "blacklist r8192s_usb" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Uninstall Ndiswrapper via:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
and reboot. Copy/paste these commands.

---

### Post by Dao333 on 2012-02-18
[FONT="Century Gothic"][/FONT]

Thanks very much for the quick reply!
Gave that a quick blast but it didn't work :(

root@Firefly:~# wget [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_dkms.tar.gz)
--2012-02-18 13:04:34--  [http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8712u-2.6.6.0.2_dkms.tar.gz)
Resolving media.cdn.ubuntu-de.org... 213.95.41.13
Connecting to media.cdn.ubuntu-de.org|213.95.41.13|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-02-18 13:04:37 ERROR 404: Not Found.

So trying to be clever (you'll see what I meant about not quite understanding how commands work exactly, I'm working on that though!), I found the driver, downloaded it and tried to continue on with your advice:

root@Firefly:~/Downloads# tar xvf rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz -C /usr/src

(Massive lines of code relating to extraction, I'm guessing! Let me know if needed)

root@Firefly:~/Downloads# dkms add -m rtl8712u -v 2.6.6.0.2

Error! Could not find module source directory.
Directory: /usr/src/rtl8712u-2.6.6.0.2 does not exist.

(When that didn't work, I tried specifying the directory as it was named in /usr/src/)

root@Firefly:~/Downloads# dkms add -m rtl8712u -v 2.6.0006.20100511

Error! Could not find module source directory.
Directory: /usr/src/rtl8712u-2.6.0006.20100511 does not exist.

root@Firefly:~/Downloads# dkms add -m rtl8712u -v 2.6.6.0.2

(then I renamed the directory to see if that worked! Nope!)

Error! Could not find module source directory.
Directory: /usr/src/rtl8712u-2.6.6.0.2 does not exist.
root@Firefly:~/Downloads# cd root
bash: cd: root: No such file or directory

If you know of another place I could use wget to get the driver and carry on from there, that might do the trick :)

I did also try:

root@Firefly:~# wget [https://launchpad.net/~lexical/+archive/hwe-wireless/+files/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz](https://launchpad.net/~lexical/+archive/hwe-wireless/+files/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz)
--2012-02-18 13:14:37--  [https://launchpad.net/~lexical/+archive/hwe-wireless/+files/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz](https://launchpad.net/~lexical/+archive/hwe-wireless/+files/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz)
Resolving launchpad.net... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://launchpadlibrarian.net/52359824/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz](https://launchpadlibrarian.net/52359824/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz) [following]
--2012-02-18 13:14:44--  [https://launchpadlibrarian.net/52359824/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz](https://launchpadlibrarian.net/52359824/rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz)
Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 420370 (411K) [application/gzipped-tar]
Saving to: `rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz'

100%[=============================================================================================>] 420,370      997B/s   in 5m 32s  

2012-02-18 13:20:24 (1.24 KB/s) - `rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz' saved [420370/420370]

root@Firefly:~# tar xvf rtl8712u-dkms_2.6.0006.20100511ubuntu1.tar.gz -C /usr/src

(More extraction gibberish)

root@Firefly:~# sudo dkms add -m rtl8712u -v 2.6.0006.20100511ubuntu1

Error! Could not find module source directory.
Directory: /usr/src/rtl8712u-2.6.0006.20100511ubuntu1 does not exist.

---

### Post by praseodym on 2012-02-18
Did you install the kernel-headers, build-essential, and dkms? Do you have any connection and/or the installation CD left?

---

### Post by Dao333 on 2012-02-18
> **praseodym said:**
> Try this driver:

[CODE]sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms


Are you talking about this part? I did that and it went fine, no problems at all. I just can't get the file from http://media.cdn etc...

---

### Post by praseodym on 2012-02-18
Sorry, the links changed due to a portal update. Try this one:

[http://media.cdn.ubuntu-de.org/forum/attachments/33/30/2844083-rtl8192cu-3.1.2590_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/33/30/2844083-rtl8192cu-3.1.2590_dkms.tar.gz)

---

### Post by Dao333 on 2012-02-18
Thanks for the update :)

It's this part that's causing me problems:

matt@Firefly:~$ sudo dkms add -m rtl8712u -v 2.6.6.0.2

Error! Could not find module source directory.
Directory: /usr/src/rtl8712u-2.6.6.0.2 does not exist.

I've tried things like changing the -v 2.6.6.0.2 etc and I think that's what's confusing me, I'm not sure what to change out of that line of command :/

---

### Post by praseodym on 2012-02-18
Sorry wrong link. Remove this directory and use this one:

```
wget [http://media.cdn.ubuntu-de.org/forum/attachments/35/41/2844083-rtl8712u-2.6.6.0.2_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/35/41/2844083-rtl8712u-2.6.6.0.2_dkms.tar.gz)
sudo tar xvf 2844083-rtl8712u-2.6.6.0.2_dkms.tar.gz -C /usr/src
```

---

### Post by kurt18947 on 2012-02-18
This won't help directly but here's something to consider.  Support for 10.10 expires in April 2012, about 2 months.  11.04 and later should support rtl-8192SU 'out of the box'.  If you're intimidated by Unity, don't be.  Unity is not mandatory.  Gnome shell in 12.04 seems to be working pretty well,  Xubuntu or Xfce desktop, Lubuntu,  LXDE, Mint.  There are options that don't involve Unity.

---

### Post by Dao333 on 2012-02-20
Thanks Kurt. I'm umming and ahhing about it as I tried it and wasn't too keen. I'm happy with 10.10 as it stands for the moment.

praseodym, thanks for all your help so far.

I encountered a major problem though, once I rebooted after getting the driver and installing everything, it gave me a weird error on booting:

(Screen changes quickly so only caught part of it):

Cannot make it's own calls, it is not a modem.

Then a series of errors that look like this:

[   22.67579 [<fffffffad7>] start_secondary+0x100/0x102

I can see around 2 dozen of these on my screen and then it just hangs on the boot indefinitely. 

I reinstalled, tried reinstalling the driver and it seemed to work. Rebooted, same problem again. 

I've tried to repair the install using my 10.10 install disc but can't seem to get the option to repair install. I could re-install again (doesn't take *too* long) but would rather just repair it and fix the driver. 

Any ideas anyone =(

---

### Post by kurt18947 on 2012-02-20
Here is a fix that worked for me in 10.04 & 10.10.  Note the error messages in dmesg.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Having tried other solutions, I'm not sure if this would work for you.  I always used it on a fresh install.

---

### Post by praseodym on 2012-02-20
Uninstall the dkms driver via:

```
sudo dkms remove -m rtl8712u -v 2.6.6.0.2 --all
sudo depmod -a
sudo update-initramfs -u
```
Install the firmware version 1.60:
```

wget [http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb)
sudo dpkg -i linux-*.deb
```
and reboot.

---

### Post by Dao333 on 2012-02-22
Thank you both guys :) Had to reinstall but it kept most of my settings etc. The driver kicked in once I reinstalled! :D 
Shame it was a bit fiddly but at least this is here for future reference for others and myself.

What's Unity Kurt, and why are people against it? I just wasn't keen on the interface etc. Just generally prefer U10.10 overall, works nicely, does what I need for my web design :)

---

### Post by kurt18947 on 2012-02-22
> **Dao333 said:**
> 
**What's Unity Kurt, and why are people against it?** I just wasn't keen on the interface etc. Just generally prefer U10.10 overall, works nicely, does what I need for my web design :)

Oh Boy :D.  According to some of the threads here, Unity is the end of the world as we know it.  Actually, it's a huge change in the user interface from Gnome2 used up until 11.04.  It was also pretty unfinished when it debuted as one of the choices in 11.04 but the traditional gnome 2 was still available as an alternative in 11.04 .  11.10 was Unity only as installed, there are other add-ons available in the repositories.  Unity has gotten better in 12.04,  I and others prefer gnome-shell,  others prefer Xubuntu or Xfce4 desktop on Ubuntu, others Lubuntu.   There are at 2 alternative desktops  in Linux Mint -- mate & cinnamon -- that seek to keep the 'traditional'  feel of Gnome2 but run on Gnome 3.  There are numerous choices in addition to Unity.  I think a lot of the 'hate' was the way it was introduced with little warning or tutorials.  Plus using it is a LOT different.

---

