---
title: "GeForce 310M - Asus K52 - can't install drivers"
date: 2013-04-23
forum: Multimedia Software
---

### Post by dziadzia fritz on 2013-04-23
**Hello,**

i've found a lot about nVidia 310M drivers, but nothing help.

Can anyone give me some "how-to" which is really working?

My ubuntu version is 12.10.

Thanks, I love you all! <3

---

### Post by papibe on 2013-04-23
Hi dziadzia fritz.

Could you post the result of these 2 commands?
```
lsmod | grep -i nvidia

lspci -nnk | grep -iA3 vga
```
Regards.

---

### Post by dziadzia fritz on 2013-04-23
Your welcome.
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1432]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [GeForce 310M] [10de:0a70] (rev ff)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
```

---

### Post by papibe on 2013-04-23
Thanks.

It looks like you have [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html").

Start by taking a look at your BIOS so can disable it by selecting permanently your Nvidia card.

If you are able to do that, install this first:
```
sudo apt-get install linux-headers-generic
```
and then open 'Additional Drivers' and install the driver there.

If not, you may need to install first [Bumblebee]("https://wiki.ubuntu.com/Bumblebee").

Hope it helps. Let us know how it goes.
Regards,

---

### Post by dziadzia fritz on 2013-04-27
Hello,

i've tried to do it you recommended me.

I've update my Ubuntu to 13.04 and than i've installed nvidia-current and nvidia-settings and than rebooted PC.

Now I see only icons on desktop, but I can't see desktop bar etc.

What do?

---

### Post by papibe on 2013-04-27
Did you check your BIOS so you see if there's a way to disable Optimus and set just the Nvidia cards?
Were you able to make things work on 12.10?

Try this to get back your desktop. First you need to get a terminal
Method 1:
[LIST]
[*]Press Ctrl+Alt+t to lauch.
[/LIST]
Method 2:
[LIST]
[*]Press Ctrl+Alt+F1 to go to a text mode console.
[*]Login as you.
[*]
[/LIST]
Once you access to run commands,  uninstall the nvidia drivers and bumblebee:
```
sudo apt-get purge nvidia-*

sudo apt-get purge bumblebee

sudo rm /etc/X11/xorg.conf
```
Then reboot:
```
sudo reboot
```
Let us know how it goes.
Regards.

---

### Post by dziadzia fritz on 2013-04-28
I've checked my BIOS and there is no Optimus settings.

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge nvidia-*[/FONT][/COLOR]
sudo apt-get purge bumblebee
```

It didn't help, I still can't see desktop bar, I see only icons and wallpaper.

I have no xorg.conf file.

---

### Post by dziadzia fritz on 2013-04-30
I've had to reinstall my Ubuntu, that was the easiest way to fix this issue. ;(

---

