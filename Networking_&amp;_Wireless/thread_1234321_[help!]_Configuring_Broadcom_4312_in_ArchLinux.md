---
title: "[help!] Configuring Broadcom 4312 in ArchLinux"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by JIMIneitor on 2009-08-07
Hi there, i installed arch a few hours ago, and it all went fine.

Although i think, i missed some modules at boot. So they wont be loaded or something.

Im trying to add networking support.
I tried ethernet, and it didnt work, so i gave up and im currently trying to configure my wireless.

I followed the Arch Wiki, and it says that i need to add some modules in order to install the driver.

[http://wiki.archlinux.org/index.php/Broadcom_BCM4312](http://wiki.archlinux.org/index.php/Broadcom_BCM4312)

i did this ```
modprobe -a b43 (no output, so i think it worked)
modprobe lib80211_crypt_tkip  (returned an error, saying it couldnt find the module)


```then i added this modules to the boot-up list

MODULES=(lib80211_crypt_tkip, b43, ssb, wl)

and then blacklisted b43

am i missing something??:confused::confused::confused::confused:

---

### Post by JIMIneitor on 2009-08-08
anyone?

---

### Post by Ayuthia on 2009-08-08
You do not want to have b43 and ssb with the wl module so don't add b43 and ssb to the MODULES.

The other thing that you might need to do is add:
```
disablemodules=b43,ssb
```
to your kernel parameters.

---

### Post by snowpine on 2009-08-08
Impossible to help you without knowing which Broadcom 4312 you have. 

```
lspci | grep BCM43
```

For the 4312 on my Dell Mini 9, this worked: [http://aur.archlinux.org/packages.php?ID=19514](http://aur.archlinux.org/packages.php?ID=19514)

---

### Post by JIMIneitor on 2009-08-08
my card is this

> 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

and thanks for the advice about disabling those modules, i will make another attempt

Will lib80211_crypt_tkip be available after i install that?

---

### Post by snowpine on 2009-08-08
> 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 

I have the identical card. It is not supported by the b43 driver. You'll have to use the wl driver (developed by Broadcom themselves, so not strictly speaking "free software"). Easiest method is to install the driver from the AUR: [http://aur.archlinux.org/packages.php?ID=19514](http://aur.archlinux.org/packages.php?ID=19514) which installs the crypt_tkip thingy as well.

---

### Post by Ayuthia on 2009-08-08
> **JIMIneitor said:**
> my card is this



and thanks for the advice about disabling those modules, i will make another attempt

Will lib80211_crypt_tkip be available after i install that?

lib80211_crypt_tkip will be available after you install it.  It is a built-in kernel module and when wl is called (if you install it through the AUR repos) it should call lib80211_crypt_tkip automatically. 

The best way to do this is to install the wl module from AUR first (unless there is one through the Arch repos).  Once it is installed, you can try to load the modules:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
These commands will unload the possible wireless modules and then load the wl module.  It will then try to bring up the wireless module and then scan for sites.  If it works, then you know that the module is working.  From there you can work on configuring the items in your kernel parameters and /etc/rc.conf.

As for your card, the 4312 rev 01 card can have different chipsets so it could work with the b43 module if it does not have the 14e4:4315 chipset (you can verify with lspci -nn).  Most of the newer laptops have the 14e4:4315 chipsets though.

---

### Post by JIMIneitor on 2009-08-08
> **Ayuthia said:**
> lib80211_crypt_tkip will be available after you install it.  It is a built-in kernel module and when wl is called (if you install it through the AUR repos) it should call lib80211_crypt_tkip automatically. 

The best way to do this is to install the wl module from AUR first (unless there is one through the Arch repos).  Once it is installed, you can try to load the modules:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```These commands will unload the possible wireless modules and then load the wl module.  It will then try to bring up the wireless module and then scan for sites.  If it works, then you know that the module is working.  From there you can work on configuring the items in your kernel parameters and /etc/rc.conf.

As for your card, the 4312 rev 01 card can have different chipsets so it could work with the b43 module if it does not have the 14e4:4315 chipset (you can verify with lspci -nn).  Most of the newer laptops have the 14e4:4315 chipsets though.


thank you for your response

although, the broadcom-wl package in AUR, says it needs kernel > 2.6.30 as a dependency, and now i have 2.6.28 and .30, i just finished compiling .30, i modyfied GRUB and everything, but when it boots, i get a kernel panic because it cant find my root partition, then it starts looking for possible partitions, and then drops another error because it cant sync with i dont know that things.

After that, i think i will be able to figure out the wireless configuration  :KS:KS

EDIT: lspci -nn gave this

> 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g _**[14e4:4315**_] (rev 01)


---

### Post by Ayuthia on 2009-08-09
> **JIMIneitor said:**
> although, the broadcom-wl package in AUR, says it needs kernel > 2.6.30 as a dependency, and now i have 2.6.28 and .30, i just finished compiling .30, i modyfied GRUB and everything, but when it boots, i get a kernel panic because it cant find my root partition, then it starts looking for possible partitions, and then drops another error because it cant sync with i dont know that things.


Did you compile 2.6.30 or did you just update it from pacman?  I am pretty sure that Arch should be running on the 2.6.30 kernel now.  They usually keep up with the most recent stable version.

---

### Post by snowpine on 2009-08-09
It sounds like your system is desperately out of date (2.6.28 is quite old in the Arch world) and badly in need of a `pacman -Syu`.

---

### Post by snowpine on 2009-08-09
At the risk of stating the obvious, have you carefully followed the Arch Beginners Guide step-by-step and looked for answers on the Arch forum?

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
[http://bbs.archlinux.org/](http://bbs.archlinux.org/)

Have you tried Ubuntu, which has built-in support for the Broadcom cards?

---

### Post by JIMIneitor on 2009-08-09
I know my sistem was quite ouf date, and thAts because i decided to use the Core live cd, and i only had wireless internet available, and therefore i wasnt able to make almost anything from arch itself.

I USE ubuntu, if didnt, would i be registered on this site?

And i decided to give arch a try to learn a little bit more.

Now i managed to get ethernet internet, and right now im downloading all necessary packages, included the newest kernel, so i domt think ill run into more trouble.

Thanks to all of you!!

---

