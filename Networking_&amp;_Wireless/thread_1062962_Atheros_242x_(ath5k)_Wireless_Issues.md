---
title: "Atheros 242x (ath5k) Wireless Issues"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by iangoeth on 2009-02-07
**Detailed bellow is how, after extensive trials with different wireless packages, I got my Atheros 5007 (AR242x chip) working.**

I own a refurbished HP G60-125NR. I have xubuntu 8.10 32-bit installed on it in a dual-boot fashion with Vista Home Premium 32-bit.

I started off by trying [this tutorial](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/). The interface started appearing in iwconfig as ath0, but no networks showed up with iwlist ath0 scanning, so I decided to try something else.

I proceeded with [this tutorial](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/). Upon installing compat-wireless, the prior madwifi drivers / modules were uninstalled. I rebooted and checked /var/log/messages, and the ath5k driver was automagically loaded. Upon inspection of iwconfig, the interface was now listed as wlan0. Still, though, when utilizing iwlist wlan0 scanning, no networks seem to show up. Although, if I click on the ubuntu wireless assistant icon, the networks show up. Unfortunately, when I attempt to connect to a network, the connection times out.

Still finding fruitless results, I removed compat-wireless and decided to try compiling madwifi from an svn source. Before doing this, I double checked the exact version of my Atheros card by booting into Windows and looking at the device manager. This revealed that my laptop had an integrated Atheros AR5007 (242x chip). I searched through the madwifi website, and was assured that the 5007 would be supported in the latest svn release of their package. I followed [this HowTo from the wiki](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowto), and everything compiled correctly. Upon adding the modules to /etc/modules and rebooting, the interface did not appear in ifconfig.

Searching around some forums some more, I came across [this tutorial](http://oesediez.blogspot.com/2008/11/intrepid-atheros-wifi-card-on-compaq.html) and decided to try it. I removed all traces of madwifi (including the modules in /etc/modules) and installed the linux-backports package it mentioned. This yielded similar results to what the compat-wireless install did. I could see networks through the network manager, but not with iwlist wlan0 scanning. I still cannot connect to any networks.

I stumbled upon a Windows XP Atheros 5211 driver, which I was told also supported the 5007, so I decided to try that with ndiswrapper. Loading it went smoothly, so I added ndiswrapper to /etc/modules and rebooted. Upon checking dmesg | grep ndiswrapper, I see:```
[   17.156640] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   17.207410] usbcore: registered new interface driver ndiswrapper
```and ndiswrapper -l yields:```
net5211 : driver installed
         device (168C:001C) present (alternate driver: ath5k)
```So, I then attempted to blacklist that driver in /etc/modprobe.d/blacklist, along with ath9k just in case. Upon rebooting, I check iwlist wlan0 scan and to my surprise, networks actually show up! Not getting my hopes up too much, I reconfigure my router for a WEP 128-bit Open System passphrase and attempt to connect to it through the Network Manager. After a few seconds, it works!

Attached is the driver that I got everything to work with. Hope this helps some folks who have been battling with their Atheros AR242x chip-based Wireless device.

---

### Post by iangoeth on 2009-02-11
Bump for others to see. :)

---

### Post by FishRCynic on 2009-02-11
does seem to a horde of them

---

### Post by mfox on 2009-02-11
I also have the Atheros 242x chipset in my Gigabyte GN-WI01GT mini PCI express card that I installed in my MSI Wind.  In my case, it works in Ubuntu 8.10 without having to install anything else, and until the latest kernel upgrade, it also works with Ubuntu 8.04.  The latest kernel upgrade in 8.04 (2.6.24.23) broke that and I'm a bit mystified as to why. iangoeth, is your driver machine-specific, or might it work on my netbook with the "wayward" 2.6.24.23 kernel?

---

### Post by iangoeth on 2009-02-12
The file attached is the Atheros 5211 Windows XP driver. It should support all cards that utilize the AR242x chip, but don't quote me on that. Can't hurt to give it a shot, right?

---

### Post by soad6 on 2009-02-13
hey thanks for the information. My friend is new to linux however i am not, but the problem was his wifi card. I tried everything I could think of and had no luck Im about to try your suggestion with the Ndiswrapper and the XP driver files... wish me luck because if this doesnt work then I am afraid to
say he'll have to still use "Windows" and we all know how that is! slow and painful! also just a little word of advice you may want to make a reference for noobs to use because they may not understand ndiswrapper, I know it should be common sense to the most of us but for them it may not be and they may not know where to find it. LOL

---

### Post by soad6 on 2009-02-13
SIMPLE guide for newbs...new people or windows users// lol
... first put in live cd of linux go to synaptic download ndiswrapper all
second go to terminal " type sudo ndisgtk" 
third go to folder net5211 and find the .inf file use that for the driver!
this will fix any problem with any wifi card is 242X!
hope this helps because i just did it perfectly with an aspire 5520 and no problems!! woot-woot...thanx again the drivers are in the post above! =D>=D>=D>

---

### Post by beetlejuice_masterson on 2009-04-13
Hi -
I'm running a Toshiba Tecra M1.  I needed a slightly different driver (atheros 5001X i believe) but I was able to get my wireless up & running thanks to this post (you guys rock).  I've done some ndiswrapper hacking in the past with a bcm4306 "nightmare" card and vaguely remember having to "make it permanent".

Currently when I boot Ubuntu loads up ath_hal, ath_pci, and ath_rate_sample (or something like that).  I want it to use the ndiswrapper always and never use the ath_ ones.  Any ideas?  Thanks!

---

### Post by t0mppa on 2009-04-13
beetlejuice_masterson: Get a MadWifi driver package (you can download one from [here]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz"), if you have none on your HDD), extract the scripts directory from it, go there and run ```
sudo ./madwifi-unload
sudo ./find-madwifi-modules.sh 
``` That should clean up any MadWifi drivers associated with the kernel.

---

### Post by damgar on 2009-09-17
THANK YOU! I have beat my head against the wall for 3 days trying to get my atheros 242x to work.  My problem was quite different in that I was able to connect, but i could never get transmission speeds over 1.5M/s which made even looking for the answer painful.  Awesome post and thanks for the driver as well, took 3 minutes with the right driver.

:guitar:

---

