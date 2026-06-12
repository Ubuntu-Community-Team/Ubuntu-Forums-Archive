---
title: "Wireless won't work on my Lenovo s10 with UNR 9.10"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by ShinigamiKiba on 2010-03-29
Wired works fine, I installed the SATA wireless drives but UNR simply won't detect any wireless networks, my PS3, Wii, DS and PSP detect the wireless network perfectly fine.

I tried pressing the Wireless killswitch, restarting, still nothing, I did that a couple times to no avail.
Wired works perfectly fine, but the computer won't even bother looking for wireless networks for more than a second or two before stating it can't find any.

I read somewhere that if you disable wireless in the default windows xp installation using the hardware wireless switch there's no way to turn it on in Ubuntu later.
If this is true, would running a virtual machine with an installed XP help solve my problem? 


There seems to be no solution whatsoever for my problem at this point and I'm not computer savvy enough to understand why.

---

### Post by ShinigamiKiba on 2010-03-30
bump

---

### Post by ShinigamiKiba on 2010-03-30
sorry for bumping this guy
but I haven't been able to find a solution yet

---

### Post by ShinigamiKiba on 2010-03-31
.....bump

---

### Post by Naggobot on 2010-03-31
Now first I admit that I personally will not be able to help you but there are few things you can do to bump your thread and maybe get attention from someone who can. Normally first thing the more experienced users ask are

Open terminal
Applications -> Accessories > Terminal

Then type following commands one by one and post outputs to your thread

```
sudo lshw -C network
``````
lspci | grep Network
``````
ifconfig
```One of the items these commands returns is 

```
serial: 00:00:00:00:00:00
```or
```
HWaddr: 00:00:00:00:00:00
```with numbers instead of zeros. Change the numbers to zeros before posting so that you can keep your mac address private. I do not actually know if it matters, but there is no harm in not spreading the mac address. 

Outputs of the commands are pretty cryptic but from those outputs someone might be able to decipher what is wrong. 

Also please use hardwire to update your system since your problem may be solved just by updating. For example My Acer mini laptop with Linpus behaved as you describe before the first system update. 

Also could you verify if the driver you installed is really STA instead of SATA. Acronym SATA refers to serial ata and STA is wireless driver for some Broadcom chips. 

Also please describe how you installed the driver. 

Correct procedure in most cases is 
System -> Administration -> Hardware Drivers

---

### Post by gganjei on 2010-04-18
Hi! I just spent 3 hours on this, but I got it working :-) See, it works fine if you boot off of the USB flash drive and then enable the driver. The problem is when you first install Netbook Remix to your hard drive, THEN try to enable the wireless driver. Due to some silliness, the software is trying to pull the driver from a CD that does not exist.

Here is what I found to be VERY HELPFUL from a read-me file from the good folks at Broadcom:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.

In my case, I did not even have to launch the hardware driver tool after rebooting. I just had to use Synaptic to install bcmwl-kernel-source along with other files that it selected automatically. Then, after rebooting, I was no longer tethered to my Ethernet. 

Please note:
1. If Synaptic gives you some cryptic error about a locked file and not being able to access something, it is because the Hardware Driver tool had hung previously when you tried to enable the driver. You need to do a clean reboot and launch Synaptic without trying to use the Hardware Driver Tool.
2. If Synaptic asks you to insert a CD, you need to go into the options of Synaptic and uncheck the options that mention the CD. Basically all of your sources should start with http:// or maybe [ftp://.](ftp://.) (I think this is good by default, but I had turned on the "CD" while trying to get the Hardware Driver Tool to work earlier.)

I'm a bit new at this as I usually use Mepis Linux. But I love this Netbook Remix idea and decided to give Ubuntu a try. I'm a Windows IT guy by trade but I do enjoy playing with Linux on the side. I'd be glad to try to offer any assistance that I can here. I'm sure I'll be asking my share of questions too...

---

