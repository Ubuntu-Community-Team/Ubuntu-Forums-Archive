---
title: "neither my wireless or ethernet devices work"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by berner5 on 2012-09-10
Hello, I recently got a new laptop and as the title says, neither my wireless nor my ethernet devices work.  So, when I boot to ubuntu, I am unable to connect to the internet, and I have to use windows for internet.  I am ubuntu verion 12.04.  My lsusb out put is:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 064e:d283 Suyin Corp. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0930:021d Toshiba Corp. 


Hope someone can help, thanks.

---

### Post by chili555 on 2012-09-10
We see no wired or wireless device in your *lsusb*. Please post:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by berner5 on 2012-09-10
ok, will do after dinner

---

### Post by berner5 on 2012-09-10
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

---

### Post by chili555 on 2012-09-10
> Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090]Let's start here. Once you get it going, the wireless will be a lot easier. Unfortunately, it will not be easy with no internet at all. Here is a link showing the process. As you can see, it worked and we're all still friends!

[http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx](http://ubuntuforums.org/showthread.php?t=2050126&highlight=alx)

Post back if you get stuck.

---

### Post by berner5 on 2012-09-10
Thank you, on it.

---

### Post by berner5 on 2012-09-10
ok, when installing the .debs the out put was


berner@berner-Satellite-S855D:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for berner: 
(Reading database ... 139901 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using build-essential_11.5ubuntu2_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace linux-headers-generic 3.2.0.29.31 (using linux-headers-generic_3.2.0.29.31_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not installed.
 build-essential depends on dpkg-dev (>= 1.13.5); however:
  Package dpkg-dev is not installed.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-29-generic; however:
  Package linux-headers-3.2.0-29-generic is not installed.
dpkg: error processing linux-headers-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential
 linux-headers-generic

---

### Post by berner5 on 2012-09-10
oh, actually, hold on a minute, the ethernet cable I was using just wasn't giving a signal

---

### Post by chili555 on 2012-09-10
> dpkg: dependency problems prevent configuration of build-essential:
build-essential depends on g++ (>= 4:4.4.3); however:
Package [COLOR="Red"]g++[/COLOR] is not installed.
build-essential depends on dpkg-dev (>= 1.13.5); however:
Package [COLOR="Red"]dpkg-dev[/COLOR] is not installed.> linux-headers-generic depends on linux-headers-3.2.0-29-generic; however:
Package [COLOR="Red"]linux-headers-3.2.0-29-generic[/COLOR] is not installed.You need to download and install those packages, too. I hope that was clear in the link I gave you.

---

### Post by berner5 on 2012-09-10
yeah, I got that, I just had forgotten to, at least now sired IS working, I just can't install anything else because of those which I will get to right now

---

### Post by berner5 on 2012-09-10
alright, wired working, no errors, but, when I updated, I had to reinstall the older version of build essential and linux headers, then applied compat wireless again.

---

### Post by chili555 on 2012-09-11
Yes, indeed. When you compile a driver from source code, you compile it against your running kernel only. When Update Manager installs a later kernel, also known as linux-image, you need to compile the driver for the newer kernel after you reboot to the later version:```
cd Desktop/compat-wireless-3.5.1-1-snpc
make clean
make
sudo make install
sudo modprobe alx
```Some day, the driver will be included in the kernel and you'll be surprised to reboot with a working ethernet! Fingers crossed.

Now that you have ethernet, build-essential and linux-headers, let's get the wireless working:> Realtek Semiconductor Co., Ltd. Device [10ec:8723] Here is a pretty good guide: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

I suggest you amend the build process slightly:> Change to the extracted driver's directory, build and install the driver:

cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
[COLOR="Red"]sudo su[/COLOR]
make
make install

Test the driver by loading it (this is a one-time step; after you reboot once, the driver should automatically load on every boot):

modprobe rtl8723e
[COLOR="Red"]exit[/COLOR]
I just ran 'make' against my 3.2.0-30 kernel and it makes without any errors or warnings. Woo hoo!

I don't have the device, so I can't test further.

As before, post back if you get stuck or encounter an error.

---

### Post by berner5 on 2012-09-11
Alright, I'll do it this afternoon after school.

---

### Post by berner5 on 2012-09-11
Thank you, it worked, only problem I encountered was a space before .2012, but I checked back to the ask ubuntu and figured that out.

---

### Post by berner5 on 2012-09-11
Also, the thought just occured to me, when I upgrade to quantal quetzal, what parts will have to be redone?

---

### Post by chili555 on 2012-09-11
> **berner5 said:**
> Also, the thought just occured to me, when I upgrade to quantal quetzal, what parts will have to be redone?I don't know if *alx* is included in the Quantal kernel or not. If your ethernet doesn't work, then I'd check for *alx*:```
modinfo alx
```If it isn't found, then redo everything. You might save yourself some difficulty by saving the tar.bz2 on a USB key or CD so at least you don't have to download it again.

---

### Post by berner5 on 2012-10-18
alright, so I upgraded to 12.10, installed the quetzal variants of the ethernet packages, then find that the dropbox link is no longer active, so, I am unable to connect to wifi. where should I go to look for this then?

---

### Post by chili555 on 2012-10-18
>  the dropbox link is no longer activeDo you mean the Network Manager icon? Please tell me more.

May I see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by berner5 on 2012-10-18
berner5@berner5-Satellite-S855D:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

and by that I mean when I clicked on the dropbox link from here [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized) there was a list of files to download, now it is shown as down(maybe I am just be trying it at a bad time)

---

### Post by berner5 on 2012-10-18
yup, my fault, it was just temporarily down doh! ](*,)

---

### Post by berner5 on 2012-10-18
actually, it may have been the accidental space in your copy that was throwing it off when I copied commands, so, in all reality, false alarm

---

### Post by chili555 on 2012-10-18
> **berner5 said:**
> berner5@berner5-Satellite-S855D:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

and by that I mean when I clicked on the dropbox link from here [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized) there was a list of files to download, now it is shown as down(maybe I am just be trying it at a bad time)It downloads for me.

---

