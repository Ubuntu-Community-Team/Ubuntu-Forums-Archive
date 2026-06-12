---
title: "need some help getting drivers for a ralink wireless card"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by iamrandy on 2013-03-31
i just got this ralink wireless card and when i download the drivers i get this[ATTACH=CONFIG]240787[/ATTACH]

---

### Post by chili555 on 2013-03-31
It would be very helpful to know the full name of the file. It appears to be RT2860 firmware which is already built in to Ubuntu.

---

### Post by iamrandy on 2013-03-31
oh sorry i have 12.04 and i also have a realtek 7811 usb hooked up as well i'm trying to get rid of the realtek adapter hopefully this helps somewhat thank you  i appreciate any help anyone can give me

---

### Post by iamrandy on 2013-03-31
yeah i tried the firmware thing and it is still consistently asking for the password to the router. the full file name is 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2

---

### Post by chili555 on 2013-03-31
>  i also have a realtek 7811 usb hooked up as well i'm trying to get rid of the realtek adapter hopefully this helps somewhat Well, it really doesn't. Do I surmise you have a built-in Realtek that you are trying to disable so you can use a USB device? Why? Is the built-in not working as expected? Shouldn't we trouble-shoot the daylights of it before we fire it?

Please open a terminal and run and post:```
lsusb
lspci -nn | grep 0280
```

---

### Post by iamrandy on 2013-03-31
the realtek adapter i have is in bad shape and it only wants to work part of the time i'm just trying to replace it with a a better working adapter

---

### Post by chili555 on 2013-03-31
> **iamrandy said:**
> the realtek adapter i have is in bad shape and it only wants to work part of the time i'm just trying to replace it with a a better working adapterIf we're going to figure all that out, we'll need the details I requested, please.

---

### Post by iamrandy on 2013-03-31
[ATTACH=CONFIG]240789[/ATTACH]here is the info you requested i hope

---

### Post by chili555 on 2013-03-31
> **iamrandy said:**
> here is the info you requested i hopeYes, indeed.

Your built-in is a Ralink and uses the driver rt2800pci. You can confirm it's loaded:```
lsmod | grep rt2
```Let's unload it and blacklist it so it's out of the way:```
sudo su
modprobe -r rt2800pci
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf

```Your USB uses the tricky module rtl8192cu about which there are no end of problems on this forum. Let's see if we can get it going:```
echo rtl8192cu >> /etc/modules
exit
```Now reboot and tell us if it's working:```
iwconfig
```> the full file name is 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2 This is an old, old driver that is appropriate about four years ago for your internal. Unless you are running Ubuntu 10.04, and you think the internal can work again, it's useless.

---

### Post by iamrandy on 2013-03-31
ok just so theres no confusion the ralink pci is the new wireless card and the realtek is the old one that doesn't work so well i know how to install the drivers for the realtek the ralink is the one that is giving me problems i hopw we're on the same page no or maybe i'm confused:(

---

### Post by chili555 on 2013-03-31
> the ralink pci is the new wireless card > the ralink is the one that is giving me problemsI guess I am confused. Are you? Please try that again.

According to the screenshot, you have a [COLOR="#FF0000"]Ralink[/COLOR] internal built-in wireless which I understand is giving you problems. You also have a [COLOR="#0000FF"]Realtek[/COLOR] USB device. Correct? The internal is troublesome and needs to be disabled, correct? If both of these statements are correct, then my last request stands.

---

### Post by iamrandy on 2013-03-31
i can't get the ralink to connect to the internet. sorry about that i can see how that last statement could have confused you. but yes the ralink is the new card and i cannot get it to connect.  it keeps asking for the router password

---

### Post by chili555 on 2013-03-31
> but yes the ralink is the new cardSo this PCI device is the *new one you want to get going*?> Ralink Corp. RT2790 Wireless 802.11n 1T/2R PCThen why do you have the USB at all? So you can connect and answer posts?

---

### Post by iamrandy on 2013-03-31
yeah i don't have an ethernet cable long enough to reach and the usb adapter works just not all the time. my dog got a hold of it when i first got it and chewed the part of the protects the antenna and also separated the antenna from the circuit board and i'm constantly having to reattach it along with the installing the software everytime the kernel updates i'm just finished with it

---

### Post by chili555 on 2013-03-31
I think...I hope I have it straight now. You should therefor disregard my suggestions in post #9. In order to get an updated driver, please do:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```After it finishes, detach the USB, reboot and let us hear your report.

---

### Post by iamrandy on 2013-03-31
that didn't work and now it won't even let me build the driver for the realtek

---

### Post by iamrandy on 2013-03-31
sorry i did work i just typed in the wrong password thank you very much chili. this is why i love ubuntu anything i don't understand you guys are always there willing to help and you've not failed me at all thank you again and ALL HAIL UBUNTU

---

### Post by iamrandy on 2013-03-31
you're going to think this is funny right as i was going to mark this as solved i lost connection and now it's back to the whole password thing. and i check and retyped the password several different times all to no avail

---

### Post by chili555 on 2013-03-31
> **iamrandy said:**
> you're going to think this is funny right as i was going to mark this as solved i lost connection and now it's back to the whole password thing. and i check and retyped the password several different times all to no availCan you confirm the USB is *not* inserted and also let me see:```
dmesg | grep -e rt2 -e wlan
```

---

### Post by iamrandy on 2013-03-31
i'm on my laptop and i can't connect to the internet on my pc i don't know if i can show you what i'm seeing but if you let me know what i'm looking for maybe i can give you the correct answers

---

### Post by iamrandy on 2013-03-31
from what i can see when i used that command it's showing a log of what the pci is doing and it is sending a signal to an ip but after 3 tries it times out

---

### Post by iamrandy on 2013-03-31
i don't know what's going on. i decided to go and play with the card itself and after detaching it and reattaching it it worked just fine. so, i'm going to mark this as solved and do some thinking about wireless access and thank you once again

---

### Post by iamrandy on 2013-03-31
i haven't been in here since the forum last updated i can't find where to mark as solved but i'm going to bed check this out tomorrow

---

