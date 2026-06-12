---
title: "Broadcom wireless problem with 9.10"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by dbreeder on 2010-05-08
Hello,

I'm a newbie to linux and just started using Ubuntu. I can't get the wireless working at all on 9.10. I am using a HP Pavillion dv6000. Also, I'm using a LiveKey USB and haven't installed ubuntu to hard drive if it matters.

I've searched A LOT of the threads on this matter and nothing seems to work. I've done the following:

Tried installing the hardware drivers --> I get an error that says "Driver is activated but not currently in use"; requires me to activate/deactivate every time I reboot.

Tried using ndiswrapper for a bit, the GUI kept saying "Network net configureable"

The closest I got was using this guide:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

trying to manually install the linux driver and remove the existing ones. It would appear that my problem comes from my computer continually using 'ssb' no matter what I do.

```
lsmod | grep "b43\|ssb\|wl"
```yields ssb 35300 every time I reboot the computer, and then I need to remove it manually before I can get wireless to go. I've added it to blacklist with the following:

```
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
```and also tried:

```
cd /lib/modules/`uname -r`/kernel/drivers/net/wireless/b43/
sudo mv b43.ko b43.ko.backup
cd /lib/modules/`uname -r`/kernel/drivers/ssb
sudo mv ssb.ko ssb.ko.backup
```I checked the directory and the name was actually changed. However, when 
I restart I STILL get the ssb 35300 when searching for it and the 
wireless won't work...

Can anyone help me out? I'm losing my wits over this...

---

### Post by dbreeder on 2010-05-08
So I sort of fixed the problem... I found somewhere that ssb is always loaded even if it is blacklisted... so I used the commands in the linux driver guide to set up a script in /etc/rc.local.

```
sudo rmmod ssb
sudo modprobe lib80211
sudo modprobe ieee80211_crypt_tkip
cd hybrid_wl
sudo insmod wl.ko
```

Unfortunately, it still won't run after a reboot. If I go into terminal and run the last two lines, the wireless activates. Anyone know why it won't activate automatically?

Thanks in advance.

---

