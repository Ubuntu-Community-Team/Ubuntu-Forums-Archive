---
title: "ASUS Xonar DS + Ubuntu 9.10"
date: 2010-02-08
forum: Multimedia Software
---

### Post by Braveheart1980 on 2010-02-08
I just did a fresh install of Ubuntu 9.10 on my HTPC , but my sound card , [ASUS Xonar DS]("http://www.asus.com/product.aspx?P_ID=wcFuNdxM0I4Sf10X") didn't work.
I updated to the latest ALSA drivers , as described [here]("http://ubuntuforums.org/showthread.php?p=6589810") , and succesfully got the latest ALSA drivers :
```
george@HTPCUbuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  9 2010 for kernel 2.6.31-14-generic (SMP).

```

BUT my sound card isn't still detected!!

```
george@HTPCUbuntu:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

Then I saw [this]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus") on ALSA page and saw that Xonar DS is supported (in ALSA ver 1.0.23 !!! Typo? ), as described [here]("http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso")

So I :

```
 sudo  modprobe snd-virtuoso
sudo  modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss

```

but still 

```
george@HTPCUbuntu:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

Any ideas????

PS My lspci

```
george@HTPCUbuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
02:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
```

---

### Post by Braveheart1980 on 2010-04-21
I did solve the problem (looong ago) and the sound is awesome

I followed this [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

After downloading and extracting the above mentioned package you should do:
sudo ./AlsaUpgrade-1.0.22.1-2.sh -s
sudo ./AlsaUpgrade-1.0.22.1-2.sh -d
sudo ./AlsaUpgrade-1.0.22.1-2.sh -c
sudo ./AlsaUpgrade-1.0.22.1-2.sh -i

restart and you are ready to go!

---

### Post by terawave on 2010-04-21
I tried the original script  but it didn't work for me, I'm on ubuntu 9.10 64bit, I installed my xonar ds card after my initial installation of ubuntu. I altered the script according to the following thread and it worked!!! Yippeee!! 
[URL="http://ubuntuforums.org/showthread.php?t=1456739&highlight=xonar"]
http://ubuntuforums.org/showthread.php?t=1456739&highlight=xonar[/URL]

---

### Post by Abdul Haqq on 2010-04-24
I have just tried Ubuntu 9.10 from the live cd. All I did was set the output un the sound panel to digital. It ran perfectly.
I then Installed 9.10 and I can't even see it.
How can it work from the live cd but not when it is installed? Istill have to see what I can do. That script modification looks a bit complicated to me.:confused:

---

### Post by lidex on 2010-04-24
> **Abdul Haqq said:**
> I have just tried Ubuntu 9.10 from the live cd. All I did was set the output un the sound panel to digital. It ran perfectly.
I then Installed 9.10 and I can't even see it.
How can it work from the live cd but not when it is installed? I still have to see what I can do. That script modification looks a bit complicated to me.:confused:
What is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

Now run these:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Reboot!

---

