---
title: "Ralink rt5390 driver causing kernel panic."
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by dotpc on 2013-01-27
When running Ubuntu 12.10 (or any os with a kernel 3.5 or greater, this problem also happens in Fedora) I encounter a kernel panic after compiling and installing the latest Ralink driver for the rt5390.

My laptop is an hp dv6.6135dx.

Here's what I do:

(this works perfectly in 12.04)

Download Ralink's latest driver and rename it.

```
tar xjvf rt.bz2.bz2
```

Edit /os/linux/config.mk to make sure these two below values are accurate.
```

HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```Then the compiling (after installing build-essential and linux-headers-generic of course).

```
cd rt5390
sudo su
make clean
make
make install
modprobe rt5390sta
exit
```I get some warnings but no errors. I then edit:

```
/etc/modprobe.d/blacklist.conf
```and add:

```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Then I get a kernel panic on reboot, I've taken a picture since I can't take a screen-shot. :(

Please help, I really would like to use 12.10 so I could have access to the latest AMD drivers.

---

### Post by chili555 on 2013-01-30
Are you able to boot at all, even in recovery mode? If so, uninstall rt5390sta:```
cd rt5390
sudo su
make uninstall
modprobe -r rt5390sta
exit
```Then reboot and remove the rt2800pci blacklist and tell us what works or not. I believe in 12.10 and forward that rt2800pci covers your device.

---

### Post by dotpc on 2013-01-31
Unfortunately I can't even log in to the recovery console (ctrl+alt+f1, is that what you even call it?) before the kernel panic occurs. The rt2800pci driver is compatible but drops the wireless connection every 5 minutes.

---

### Post by chiec on 2013-01-31
Exactly the same over here. I can boot, but it gaves me a kernel panic in 5 minutes or so before it happens. At least the wifi works perfectly before it.

Thank you very much chili555, you're the master of this! ):P

---

### Post by chili555 on 2013-01-31
> **dotpc said:**
> Unfortunately I can't even log in to the recovery console (ctrl+alt+f1, is that what you even call it?) before the kernel panic occurs. The rt2800pci driver is compatible but drops the wireless connection every 5 minutes.I meant when the GRUB menu comes up or you bring it up with the shift key: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by chiec on 2013-01-31
I can even log in, and use the wifi, but the kernel panic happens in 5 minutes or so.
Uninstalling the rt5390sta module is not an option for me because im a little far from the router and the connection drops a lot with the other module, if I can't fix this I should buy a usb key...

---

### Post by dotpc on 2013-01-31
Alas, I've also tried this but it doesn't really matter since the rt2800pci driver works so poorly. :-(

---

### Post by dotpc on 2013-01-31
Chili,
Do you know of any steps to improve rt2800pci's resiliency?

---

### Post by chiec on 2013-01-31
Seeing this make me realize I'm not the only one with this issue so I'm going to report the bug in LinuxMint Launchpad (it's the distribution I use) although it should be the same for Ubuntu since Mint is Ubuntu + some packages.

I'm gonna post the link here when I finish.

Cya!

---

### Post by chili555 on 2013-01-31
> **dotpc said:**
> Chili,
Do you know of any steps to improve rt2800pci's resiliency?Certainly. You might try the Ubuntu version of compat-wireless. With a wired ethernet connection temporarily, do:> sudo apt-get install linux-backports-modules-cw-3.6-quantal-genericReboot and tell us if it's working better.

You might also try a driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If this helps, we'll write a quick file to make it persistent.

You might also set the router to WPA2 only, not WPA/WPA2 mixed mode. If it's available, try shutting off N speeds in the router.

---

### Post by dotpc on 2013-01-31
I only did the first step so far:

> **chili555 said:**
> ```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```

I've been using it for a few hours now with NO disconnect. Very impressive.

Is there any kind of similar package for Fedora?

If it is still working tomorrow, I'm marking this as solved.

---

### Post by chiec on 2013-01-31
WOW! Me neither! No kernel panics nor connection dropouts!

Thank you very much! It really helped me!:D:D:D

Edit: Is I realize now, it works better now, but worse than the driver from ralink, the connection reach is the same as before and if I'm far from the router it goes slower than the rt5390pci, but without dropouts or kernel panics, so I'm sticking with this. As I said, thank you very much!

---

### Post by chili555 on 2013-01-31
> Very impressive.It's what we strive for.> Is there any kind of similar package for Fedora?I don't know; I suggest you ask at fedoraforum.org. The package is based on compat-wireless which, I assume, could be compiled for any Linux distribution. The backports package is just a little easier and neatly wrapped in an Ubuntu-ized .deb.

Feel free to massage that Solved button at the top at any time.

---

### Post by chili555 on 2013-01-31
> **chiec said:**
> WOW! Me neither! No kernel panics nor connection dropouts!

Thank you very much! It really helped me!:D:D:D

Edit: Is I realize now, it works better now, but worse than the driver from ralink, the connection reach is the same as before and if I'm far from the router it goes slower than the rt5390pci, but without dropouts or kernel panics, so I'm sticking with this. As I said, thank you very much!Working beats kernel panics every time!! Glad it's fixed.

---

### Post by dotpc on 2013-02-01
I left the laptop on overnight and have yet to be disconnected. Slainte!

I really cannot thank you enough Chili, you have helped me fulfil my new year's resolution of not using windows on any of my computers. Thanks again.

Go Linux!

---

### Post by chili555 on 2013-02-01
I am very happy to have helped. Go Linux, indeed.

---

### Post by chiec on 2013-02-02
It's weird and I don't know why. I had to reinstall Mint and then I installed the backport cw package, but this time didn't work...

Any idea?

---

### Post by chili555 on 2013-02-02
I don't know much about Mint. What does this tell us?```
nm-tool
rfkill list all
dmesg | grep rt2
```

---

### Post by chiec on 2013-02-02
Mint is just Ubuntu with some added packages and without Unity, so is the same.

I'm having connection problems even with a signal strength of 49 :(

[http://dpaste.com/905803/](http://dpaste.com/905803/)

---

### Post by chili555 on 2013-02-02
> *ONO7C30:        Infra, BC:14:01:38:7C:38, Freq 2432 MHz, Rate 54 Mb/s, Strength 49 [COLOR="Red"]WPA WPA2[/COLOR]What are your results if you set the router to WPA2 only and not mixed mode WPA and WPA2? Are you some distance from the router? Have you tried other channels? I get the best result on channel 11.

---

### Post by chiec on 2013-02-02
Yes, I'm at some distance, but here, windows reach without problems and linux dont :(
I set the router to WPA2 only and changed it to channel 11 and I don't know if it's the WPA2 only, or the channel, but it's even worse now xD. Before, I had connection dropouts, but now it's almost impossible to connect in my bedroom.

---

### Post by chili555 on 2013-02-03
> **chiec said:**
> Yes, I'm at some distance, but here, windows reach without problems and linux dont :(
I set the router to WPA2 only and changed it to channel 11 and I don't know if it's the WPA2 only, or the channel, but it's even worse now xD. Before, I had connection dropouts, but now it's almost impossible to connect in my bedroom.I suggest you change back to the original channel (6 maybe?) and try it. You might also try a temporary driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If it helps, we'll write one small file to make it persistent.

---

### Post by chiec on 2013-02-03
> **chili555 said:**
> I suggest you change back to the original channel (6 maybe?) and try it. You might also try a temporary driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If it helps, we'll write one small file to make it persistent.


It helped a little, less dropouts, but there are still. I'm going to install the module that gave me kernel panics and then reinstall the cw-backports again. If that helped me before, maybe it still can xD

Thanks :)

---

### Post by chiec on 2013-02-03
Didn't worked u.u. Still very very slow compared with rt5390sta

---

### Post by dotpc on 2013-02-03
I'd like to weigh back in, this problem seems to be Gnome-related. May I suggest trying KDE, I've had no dropouts on Kubuntu and I did not even install the cw backports package.

---

### Post by dotpc on 2013-02-04
I've filed the bug with Gnome.

It would be great if this got fixed upstream!

[https://bugzilla.gnome.org/show_bug.cgi?id=693122]("https://bugzilla.gnome.org/show_bug.cgi?id=693122")

---

### Post by chiec on 2013-02-14
I just installed the 32-bits ubuntu and the driver from ralink works perfectly!  

If the drivers are free, why isn't this one by default (at least on 32bits distributions)?

PD: I'm using gnome remix edition, so isn't gnome's fault.

---

### Post by dotpc on 2013-02-19
How might I make this persistent, Chili?

Code:
                     ```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```

---

### Post by chili555 on 2013-02-19
Write a new file:```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```Add a single line:```
options rt2800pci nohwcrypt=Y
```Proofread carefully, save and close gedit.

---

### Post by dotpc on 2013-03-09
Weighing back in! I started having disconnect issues on KDE, which led me to try many other avenues ... eventually leading to Arch Linux and using netcfg.

Performance is amazing, and I've had ZERO disconnects over many days. This problem seems to be part of network manager after all. Chiec, if you are brave you should try Arch and netcfg (or maybe wicd in Ubuntu).

---

### Post by Marzian on 2013-05-12
Hello,
This command doesn't work anymore in Ubuntu 13.04:

sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic

Is there any alternative?

(My problem is described here: [http://ubuntuforums.org/showthread.php?t=2137576&page=2](http://ubuntuforums.org/showthread.php?t=2137576&page=2))

---

### Post by chili555 on 2013-05-12
> **Marzian said:**
> Hello,
This command doesn't work anymore in Ubuntu 13.04:

sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic

Is there any alternative?

(My problem is described here: [http://ubuntuforums.org/showthread.php?t=2137576&page=2](http://ubuntuforums.org/showthread.php?t=2137576&page=2))Do you have a xxxx:5390 device? If not, please start a new thread and give us your details:```
lspci -nn | grep 0280
```Leave the link here and I'll be happy to help.

---

### Post by Marzian on 2013-05-12
Thanks for the offer of help!

All the information is here: [http://ubuntuforums.org/showthread.php?t=2137576](http://ubuntuforums.org/showthread.php?t=2137576)

To sum it up:

- I have a Ralink RT3290 PCI, but the Ubuntu driver is working awfully (very poor signal, and always disconnecting), even after disabling power managment and hardware encryption.

- I tried to compile the official driver, but kept getting errors that I was able to solve only with a patch for the RT5390 driver. The connection looked wonderful, but then I got a kernel panic and had to blacklist this driver and get back to 2800pci, so I'm looking for a solution to improve the 2800pci or avoid the kernel panic.

- Spent money on a USB adaptor working even worse than the PCI card.

---

### Post by chili555 on 2013-05-12
> **Marzian said:**
> Thanks for the offer of help!

All the information is here: [http://ubuntuforums.org/showthread.php?t=2137576](http://ubuntuforums.org/showthread.php?t=2137576)

Replied.

---

### Post by dotpc on 2013-05-30
What helped me the most (after everything) was disabling 'N' speeds on my router. Thanks Chili.

---

