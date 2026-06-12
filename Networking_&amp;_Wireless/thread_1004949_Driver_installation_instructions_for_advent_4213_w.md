---
title: "Driver installation instructions for advent 4213 wifi (Intrepid Ibex)"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by Rikki123s on 2008-12-07
_Here is a little guide to installing the wireless drivers for the Advent 4213 on Ubuntu Intrepid Ibex:_

The commands that were found were originally for the Advent 4211 (would have a reference page for you but I lost it, sorry), but with very few changes (just a few directory names) I had made these commands compatible with the Advent 4213. Both netbooks have the same wireless card (the realtek RTL8178SE) so it was only basic logic to get the drivers from the 4211 & have them work for the 4213.

This will only work for intrepid ibex.

Run these lines in terminal:

~$ sudo apt-get install build-essential linux-headers-`uname -r`
~$ wget [http://julienpecqueur.com/ftp/rtl8187se_linux_26.1023.0928.2008.tar.gz](http://julienpecqueur.com/ftp/rtl8187se_linux_26.1023.0928.2008.tar.gz)
~$ tar xvzf rtl8187se_linux_26.1023.0928.2008.tar.gz
~$ cd rtl8187se_linux_26.1023.0928.2008
~$ ./makedrv
~$ sudo ./wlan0up
~$ sudo cp -r ieee80211/*.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
~$ sudo cp -r ieee80211/*.ko /lib/modules/2.6.27-10-generic/kernel/drivers/net/wireless/
~$ sudo cp rtl8185/r8180.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/
~$ sudo cp rtl8185/r8180.ko /lib/modules/2.6.27-10-generic/kernel/drivers/net/wireless/
~$ sudo depmod -a
~$ sudo modprobe r8180

Restart Ubuntu. Your drivers will now work.

The changes that I made were the module directory names. If this is different for you also then you should change it from 2.6.27-7 & 2.6.27-10 to whatever it is in your module directory (/lib/modules/).

I haven't tested discovering networks yet, but this does work for named networks that you have already pre-configured into the operating system.

Hope this helps anyone who has been just as lost as me with this problem.

_Any problems, let me know._

---

### Post by Rikki123s on 2008-12-08
Just to confirm, discovery works. my roaming found all the networks that I found back when the netbook was on xp :)

---

### Post by subtleknife on 2008-12-29
Hi

Thanks for instructions - worked perfectly with
Advent 4211 - MSI BIOS (overclocked by 23%)
2.6.27-9-generic

Great little machine - Recommend the [MSI BIOS 1.09]("http://www.electricvagabond.com/2008/10/msi-wind-bios-109-update-overclock-and.html") if you don't have it.

---

### Post by apacheuk on 2009-01-26
Followed the above instructions and everything seems to work, however when ever I reboot I have to run the following command in the terminal to get the card to work

sudo ./wlan0up

have I missed something??

---

### Post by apacheuk on 2009-01-26
sorted, cheers

advent 4213 - 2.6.27.9-generic

---

### Post by complience on 2009-02-01
Had this working for a couple of days.

Then it stopped, think it might not like my new kernel
2.6.27-11-generic

anyone got it working on this one?

---

### Post by rfgizmo on 2009-02-13
I started this and got stuck on line 2 with the error that the url for the .tar.gz file was not found.

I'm running Ibis with 2.6.27-6 generic

Also can't get either vodafone's huawei k3565 or the built in hsdpa devices to work, but i guess i should post that elsewhere.

---

### Post by shayguitarra on 2009-03-06
I'm using 2.6.27-11-generic too, and I inserted it in all of the relevant lines. Everything seems to install fine, but when I reboot and run 'iwlist wlan0 scan' I just get 'no scan results'. I've tried setting up the networks manually but to be honest I'm not really sure what I'm doing, and it isn't working. So the discovery mode is pretty essential.

Is this just a problem with this kernel version?

I'm running on the advent 4211C.

Any suggestions appreciated.

---

