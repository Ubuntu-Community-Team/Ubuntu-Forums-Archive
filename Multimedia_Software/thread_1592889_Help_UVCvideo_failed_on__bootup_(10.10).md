---
title: "Help? UVCvideo failed on  bootup (10.10)"
date: 2010-10-11
forum: Multimedia Software
---

### Post by iisdev on 2010-10-11
Hi,

I managed to work through most of the original issues on my own. I'm rewritten the post to make it easier for others with this notebook model to follow.

Environment:
Notebook: Sony Vaio SZ780
Ubuntu: 10.10 x86 fresh install on dedicated partition. Dual booting with Win 7.

Ubuntu installed fine. Checked for updates, installed them and rebooted. Was prompted for proprietary drivers (this model has a Nvidia 8400M GS in it). I selected the 'recommended' driver, installed and rebooted the computer.

After rebooting I received the following error messages:

```
[2.677402] UVCvideo: Failed to query(129) UVC probe control: -32 (exp .26)
[2.677499] UVCvideo: Failed to initialize the device (-5)
[3.635020] Sd 4:0:0:0 [sdb] Assuming drive cache write through

Ubuntu 10.10 <computer name> tty1
<computer name>login:
```

at this point if I do nothing about three minutes later this comes up:

```
[124.276042] tpm_tis 00:09: tpm_transmit: tpm_send: error 4294967234
```

and shortly after it continues to the login screen. I can login and everything appears ok with the exception of the graphics. 

I originally thought it was a problem with the Nvidia driver. It appears to have been several hardware related issues that appeared after the installation of the display driver.

After many hours here's what worked for me:

The UVCvideo error is related to ***Visual Communication Camera VGP-VCC7*** which is integrated into the bezel of the notebook.

Open up terminal and type:

```
$ sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial
$ hg clone http://bitbucket.org/ahixon/r5u87x/
$ cd r5u87x
$ make
$ sudo make install
$ sudo r5u87x-loader --reload
```

Upon rebooting the error messages have been reduced:

```

[3.635020] Sd 4:0:0:0 [sdb] Assuming drive cache write through

Ubuntu 10.10 <computer name> tty1
<computer name>login:
```

followed a couple of minutes later by

```
[124.276042] tpm_tis 00:09: tpm_transmit: tpm_send: error 4294967234
```

I believe the drive_cache is related to a multi-card reader in the express card slot of my notebook. The reader (Sony Model ***VGP-MCA20A***) came with my notebook and allows you to read Memory Stick Pro, xD, SD/SDHC, and MMC cards. When the multi-reader is plugged in (with media) the drive_cache errors appear. When the media is removed the error disappears. Not 100% sure if it's not the SD card; will re-visit this later.

The tpm errors are related to the ***Trusted Platform Module*** that apparently came with this model. I'm not really familiar with what exactly it does on this model but from what I read it sounds counter-intuitive to what Linux represents. Maybe that's why Ubuntu's making a fuss over it? **This is what causing the boot process to be interrupted**.

Initially I looked into the computer's bios to see if there were any TPM settings I could change. If there are they are not accessible from the built-in menu.

I typed this into the terminal to confirm that the module was in my notebook:

```
lsmod | grep tpm
```

The results were:

```
tpm_infineon            7937  0 
tpm_tis                 7562  0 
tpm                    13741  2 tpm_infineon,tpm_tis
tpm_bios                5310  1 tpm
```

One site (forgot which) recommended blacklisting these modules. I entered this into the terminal:

```
sudo gedit /etc/modprobe.d/blacklist
```

and added the following:

```
#trusted platform module
blacklist tpm
blacklist tpm_bios
blacklist tpm_infineon
blacklist tpm_tis
```

and saved. I then restarted and Ubuntu booted straight to the desktop. :)

At some point during troubleshooting I noticed that suspend wasn't working correctly either. I had tried this fix early on:

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

but it didn't work. After the TPM fix however suspend functions correctly. I'm not sure which of the two were responsible but both solutions involved blacklisting so maybe they were related in some way.

At this point the main issue (of the interupted boot process) was gone. The only other issue was related to the display performance.

The performance of the 8400M GS so far has been disappointing. It's an average chipset but I had assumed it would be capable of running Ubuntu without any issues. This particular model of the chipset has only 64MB of dedicated video RAM in it. It supplements this however with system memory and is typically displayed as having 256MB (or more under Windows) available to it. 

After installing the Nvidia drivers I was disappointed to see slow redraws (during fade effects), tearing (when moving windows), stuttering (when scrolling a webpage), etc.. 

One of the first things I tried was changing the PowerMizer settings to 'Prefer Maximum Performance' (System > Administration > NVIDIA X Server Settings > Powermizer (under GeForce 8400M GS). The equivalent setting under Windows forces the card to run with it's clock speeds at the highest values possible, hopefully eliminating any stuttering caused by ramp up times as it cycles through performance modes.

This didn't work quite the way I expected. My GPU temp and fan noise are indicative that it's still working under the Adaptive state even though 'Prefer Maximum Performance' is set under PowerMizer. According to the stats at the top of the window Adaptive Clocking is still enabled.

I tried several fixes. (type at the terminal)

```
sudo gedit /etc/X11/xorg.conf
```

Add the following line to the 'Device' section:

```
Option "RegistryDwords" "PowerMizerEnable=0×1; PerfLevelSrc=0×3322; PowerMizerDefaultAC=0×1"
```

Save and reboot afterwards.

This however didn't work for me. A while later I ended up somewhere on the Compiz forums. One of the posts suggested turning off all the effects.

I right-clicked on the desktop chose 'Change Desktop Background', then selected the 'Visual Effects' tab. By default Ubuntu had selected 'Normal'. When I switched it to 'None' all the problems disappeared. The GPU is still stuck in Adaptive mode (which I can tell by it's temperature and fan output) but all of the issues mentioned above have disappeared. The difference (to me, at least) is like night and day.

I'm still unsure about what the problem actually is here. Maybe it's a combination of these?

1. The default Compiz settings appear to be too much for this card to handle. (possible.. maybe)

2. I *should* be able to set the 8400M GS into High-performance/Prefer Maximum Performance mode. When I do however it reverts after reboot.

3. In Windows it was possible to completely disable PowerMizer. I haven't been able to do that yet under Ubuntu. (PowerMizer is pointless when under AC power)

4. Ubuntu may be incorrectly assessing the abilities of the 8400M GS.

5. The linux version of the Nvidia driver might be a contributing factor? With the same driver version under Windows I get excellent performance from this chipset.

6. (Not entirely critical but related to the Nvidia driver) The function keys which control screen brightness don't work. I couldn't get this working under Windows 7 either - I believe it's because of changes they made to the 2xx series.

If anyone has any suggestions for the multi-media card reader issue please let me know. 

Like-wise with the Compiz/Nvidia performance. If anyone specifically has the 8400M (or variant) and has Compiz running like butter please post your settings so that I can compare them to mine.

Lastly, if anyone has found a way to disable PowerMizer please post your solution.

Thanks!

---

