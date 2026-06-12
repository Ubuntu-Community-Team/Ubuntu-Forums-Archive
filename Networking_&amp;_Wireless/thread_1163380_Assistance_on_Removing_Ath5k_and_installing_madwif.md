---
title: "Assistance on Removing Ath5k and installing madwifi"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by easycheese on 2009-05-18
Does anyone know the best way to remove teh ath5k drivers and install the madwifi drivers?

---

### Post by t0mppa on 2009-05-18
Here we go:

[LIST=1]
[*]You'll need build-essential, make & friends for compiling the driver, so open up a terminal and run ```
sudo apt-get install build-essential
```
[*]Make sure you comment out (add a # in front) or delete the lines with ath_pci, ath_hal or wlan from the /etc/modprobe.d/blacklist*.conf files. Jaunty for instance creates a blacklist-ath_pci.conf file, where ath_pci is blacklisted.
[*]Unload the wireless with ```
sudo ifconfig wlan0 down
```
[*]Blacklist ath5k with ```
echo blacklist ath5k | sudo tee -a /etc/modprobe.d/blacklist.conf
```
[*]Grab the latest snapshot from [here]("http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz"), download it somewhere you can easily find it (need to compile it again every time you update kernel), ~/MadWifi/ for instance. Then unpack the archive.
[*]Navigate your terminal to the directory where the files were unpacked and ensure there are no conflicting modules present by running ```
sudo ./scripts/madwifi-unload
```
[*]Then compile the driver with ```
make clean
make
sudo make install
```
[*]Get the new driver up and running with ```
sudo depmod -ae
sudo modprobe -r ath5k
sudo modprobe ath_pci
```
[*]mkroetzsch (below) solved an issue with suspend (where you otherwise had to manually unload and reload the driver to get it working after resume) by editing the following line (the part on red is what you add there) in */etc/default/acpi-support*:```
MODULES="[COLOR="Red"]ath_pci[/COLOR]"
```
[/LIST]

If you run into some problems, post back on this thread and we can see about fixing them.

---

### Post by jelkimantis on 2009-10-30
Thank you very much! This was very helpful and mindless for me! :-)

---

### Post by jshayden on 2009-10-30
I think you meant:

```
echo blacklist ath5k | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Either way, ath5k is still being loaded in addition to ath_pci at boot.

Any idea what package it is in? I'll just uninstall it altogether.

Thanks,
Josh

---

### Post by t0mppa on 2009-10-31
> **jshayden said:**
> I think you meant:

```
echo blacklist ath5k | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Yes, that's right, good call there.

> **jshayden said:**
> Either way, ath5k is still being loaded in addition to ath_pci at boot.

Any idea what package it is in? I'll just uninstall it altogether.

Thanks,
Josh

That's odd, there shouldn't be any other module depending on it and thus loading it as a side product, so can't see why the simple blacklisting doesn't work.

Anyway all the wireless drivers come prebuilt with the kernel, so uninstalling it through conventional means might prove a little troublesome. What you can do though is look up the module file */lib/modules/<kernel_that_you_use>/kernel/drivers/net/wireless/ath5k/ath5k.ko* and rename it (to ath5k.ko.disabled for instance), that should make it unloadable and thus solve your problem.

---

### Post by jshayden on 2009-10-31
I eventually got the blacklist to work; I think I was writing to the wrong file somehow.

So, now ath_pci is loading and ath5k is not.

However, the wireless connection isn't working.  It asks for my WPA password over and over.  Every once in awhile it will connect, but it's very slow with horrible latency.

Not only did this work perfectly in Jaunty, but it was included in the repositories.  Any ideas?

Thanks,
Josh

---

### Post by t0mppa on 2009-10-31
Ok, that is a somewhat common problem in that it persists over different drivers and cards. I never was troubled by it myself, so can't really say one way or the other what's causing it (a lot of different solutions have been offered and without getting to test any of them, no way of knowing which are worth their while), but there's plenty of threads about it on the forums. Thus, I'm afraid I can't be of much help on solving said issue.

---

### Post by jshayden on 2009-10-31
Interesting.  What is odd, though, is that I have never had trouble with mine—since Gutsy.  I compiled the newest madwifi source.

Any idea why it is no longer in the repositories?

Any other ideas from anyone?

Thanks,
Josh

---

### Post by t0mppa on 2009-10-31
> **jshayden said:**
> Any idea why it is no longer in the repositories?

Because it was finally superseded by ath5k & ath9k as they use the newer wireless stack and don't feature binary-only, i.e., no source code is available, components, which are very troublesome to work with. You can read more about it from [here]("http://old.nabble.com/Karmic-linux-restricted-modules-(may-it-rest-in-peace)-td23388530.html"), if you're truly interested.

---

### Post by psycosmyth on 2009-11-04
giving this a bump.
I have had the same exact issue. I had no trouble in the alpha but the beta gave some speed issues. I now have a fresh 9.10 and it looses connection often. I'm going to play with some settings and see. Mandriva 2010 uses Madwifi still. WHY? :roll:

---

### Post by psycosmyth on 2009-11-04
Trying to figure why ath5k and wireless security are conflicting. No security=no problem.

---

### Post by mkroetzsch on 2009-11-17
I encountered two issues when following the above guide:

(1) The latest madwifi snapshot did not work for me: it compiled and installed properly, but trying to use it resulted in endless error/warning messages about unexpected default values in kernel.log (I am running Kubuntu Karmic). To fix the problem, I went to the madwifi website and downloaded the driver that they give there as the latest stable snapshot. This was version 0.9.4 and not the latest version "hal-0.10.5.6-r4100-20090929". This fixed the problem. (The rest of the above guide is still applicable.)

(2) The network fails after suspend (both to disk or to memory) if the driver is not unloaded and reloaded when suspending. This was not done automatically for me and I had to edit /etc/default/acpi-support by changing the line ```
MODULES=""
``` to ```
MODULES="ath_pci"
``` The WLAN now works directly after resuming.

Maybe it would be useful to include these hints into the otherwise very useful post of [t0mppa.]("http://art.ubuntuforums.org/member.php?u=787201")

---

### Post by t0mppa on 2009-11-17
About (1), 0.9.4 is really the newest release, the one I linked to only provides a later version of HAL, i.e., the closed source piece of code for this driver. The 10.5.6 HAL was the one that had support for AR5007, which is my card and thus I had to use it originally to get mine to work.

They stopped actively developing this driver about 1.5 years back, after Atheros released their source code fully and the work on ath5k and ath9k started. As you can see, the r4100 was released on September 29th, so it's not exactly brand new. It did compile back on Jaunty, but compiling it now does indeed bring up some warnings on my system as well.

I'm afraid I'm a bit out of the loop with this driver, since I haven't used it since Intrepid as ath5k has worked just fine for me on Jaunty & Karmic, thus the post is not getting updated unless someone posts here for newer information.

About (2), that'll be a welcome addition. Personally, I had so many other issues with suspend that I stopped using it as Ubuntu boots so quick that it's not a problem to simply turn it off when leaving the laptop for a longer time.

---

### Post by bronxbomberz41 on 2009-11-20
On the sudo make install command i'm getting an error that looks like this
```
WARNING: -e needs -E or -Fmake -C ./tools  install || exit 1
make[1]: Entering directory `/home/brian/MadWifi/madwifi-0.9.4-r4100-20090929/tools'
install -d /usr/local/bin
install: cannot create directory `/usr/local/bin': File exists
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/brian/MadWifi/madwifi-0.9.4-r4100-20090929/tools'

```

I'm not sure what the "-e needs -E or -F" means.

---

### Post by t0mppa on 2009-11-21
That is rather odd indeed, since the *install -d <directory>* command in all its simplicity either creates the directory in question or if it already exists, does nothing. Checked the *Makefile* and it seems the only thing with an -e option is the *depmod -ae* command, which is also a very basic one and don't see why it'd fail.

Anyway, I was going to tell you about [drpjkurian's thread]("http://ubuntuforums.org/showthread.php?t=1309072"), as that one has people who're actually still using Madwifi, but it seems you already visited it. Did the version mentioned there compile properly?

---

### Post by bronxbomberz41 on 2009-11-21
Yes I've already been there.  Following his steps made my problem worse.  Initially I was just getting a lot of dropped connections, then after trying drpjkurian's solution i now can't even turn my wireless on.  at least before I could turn it on.

---

### Post by t0mppa on 2009-11-21
What I was getting at though, is that if when following his steps you managed to compile (make step) and install (sudo make install step) the driver properly, it'd make this a driver configuration issue, instead of a compiling issue. I can probably help you with the former, but I don't really have much experience with the latter. Plus, if the other branch of this same driver doesn't work properly, I'm not convinced this is all that much better.

---

### Post by zindy on 2009-12-01
Thank you, worked a treat!

Step 7, I did a sudo checkinstall instead of sudo make install. Involves a few more steps but it means changes can be reverted if anything goes wrong.

Regards,
Egor

---

### Post by pifactory on 2010-01-10
Hi

I have the same problem and this thread is proving useful... thanks.

However, I am stuck at step 7

make clean
make
sudo make install

My terminal responds:

make: *** No rule to make target `clean'.  Stop.
aiysha@aiysha-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.

Looking at the files in the madwifi directory I have files named Makefile and Makefile.inc

I've tried putting those file names instead, but I just get command not found.

Could you give little more detail/help here please.

Many thanks.

---

### Post by loosescrew on 2010-02-03
Guess, i'm a little slow. I got to step 6. How do i navigate the terminal to the file i just d/led ? So that i can compile the driver. Thanks joe

---

### Post by loosescrew on 2010-02-03
certainly,there is somebody out there that can help me with this. I about ready to toss this laptop out the window.

---

### Post by thafool on 2010-02-06
> **loosescrew said:**
> Guess, i'm a little slow. I got to step 6. How do i navigate the terminal to the file i just d/led ? So that i can compile the driver. Thanks joe

loose -- if you're using firefox it probably downloaded to the default Downloads folder under your username - just do a $ cd /home/*yourusername*/Downloads

If not, there are 2 easy things you can do to get it.

1. Change the firefox download folder to somewhere you know how to navigate to (just don't put it on the desktop - gets messy) and download the package again.

2. or do a locate of the package name:
$ sudo updatedb (may take a few mins)
$ locate *insertfilenamehere*

that will show you where everything with that filename is on your system - then just cd to it like above

Good luck with the rest - I'm still battling my wireless too!

---

### Post by eGaTS on 2010-03-07
I saw this hinted at earlier in the thread, but if it was resolved, I am not seeing it.

```
$ sudo depmod -ae
WARNING: -e needs -E or -F
```I also saw similar messages during the make.  The man page for depmod tells me I need a core map file for my kernel.  Do I have that?  Is it even necessary? "depmod -a" executes fine.


Edit: Everything seems to be working fine, despite the warnings.  Switched it over to Wicd and connected to my WPA2 without any trouble.  I do have a slightly off topic question though... Wicd's Advanced Settings tab shows the WPA Supplicant is set to "wext" (and works fine with this setting).  The note below it says I should "almost always" use wext, but I noticed that madwifi is also listed as an option there.  Should I be using the madwifi supplicant with my setup?  Pros? Cons?

---

### Post by karthick ayyapillai on 2010-03-07
> **psycosmyth said:**
> giving this a bump.
I have had the same exact issue. I had no trouble in the alpha but the beta gave some speed issues. I now have a fresh 9.10 and it looses connection often. I'm going to play with some settings and see. Mandriva 2010 uses Madwifi still. WHY? :roll:

hi
I have 9.10 fresh install and wify not working i tried all the solutions mentioned in forum and no hope. my chipset uses ath5k driver which is a old one so i installed mad wifi latest version and made the system to use ath_PCI drivers still no hope if you find any way to check the mad wifi working properly please can you post the procedure, thanks in advance.

---

### Post by karthick ayyapillai on 2010-03-07
> **mkroetzsch said:**
> I encountered two issues when following the above guide:

(1) The latest madwifi snapshot did not work for me: it compiled and installed properly, but trying to use it resulted in endless error/warning messages about unexpected default values in kernel.log (I am running Kubuntu Karmic). To fix the problem, I went to the madwifi website and downloaded the driver that they give there as the latest stable snapshot. This was version 0.9.4 and not the latest version "hal-0.10.5.6-r4100-20090929". This fixed the problem. (The rest of the above guide is still applicable.)

(2) The network fails after suspend (both to disk or to memory) if the driver is not unloaded and reloaded when suspending. This was not done automatically for me and I had to edit /etc/default/acpi-support by changing the line ```
MODULES=""
``` to ```
MODULES="ath_pci"
``` The WLAN now works directly after resuming.

Maybe it would be useful to include these hints into the otherwise very useful post of [t0mppa.]("http://art.ubuntuforums.org/member.php?u=787201")

As you have mentioned i have also tried madwifi for my ath5 driver and got it installed when i tried to edit the file in /etc/default.acpi-support it says file not found error
using ubuntu 9.10 karmic kola and atheros 5001 chipset for wireless. ath5 drivers

---

### Post by Gatita on 2010-04-08
I hope that you have found the information you were looking for by now, but just in case...

[QUOTE="karthick ayyapillai"]when i tried to edit the file in /etc/default.acpi-support it says file  not found error[/QUOTE]

I don't know if that was a typo, but you should be editing the  /etc/default/acpi-support file. You can also use the "locate" command to find all files containing the word "acpi".

---

### Post by cj-tess on 2010-04-25
Hi there

I just wanted to say that I have been experiencing a sloopy connection on Lucid RC. I have an Atheros wireless card.

09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

I have tried everything: people blaming the DHCP, NSS, etc. Was none. -indeed, I have two laptops on Lucid, and the other (with intel chipset) worked fine-

After installing madwifi, looks like it solved completely the issue. Thanks for the post. I will report the bug now.


Best

---

### Post by aapo4 on 2010-05-02
My WLAN worked very badly on Lucid.
```
Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
```

It is using ath5-module. It was slow and disconnected often.

I followed instructions from here: 
[http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

And I got newer driver installed and it works great!

---

### Post by Tamalin on 2010-05-02
Thank You!  It worked perfectly.  I can't thank you enough.

---

### Post by Tamhvm on 2010-05-13
Hello everyone!

I've recently installed Kubuntu 10.04 [Lucid Lynx]... It's really great overall, but I'm having a bit of a trouble with the wireless adapter in my laptop.
Sometimes it acts really slow (3 Kbps). Sometimes it doesn't connects to the router (if doesn't matters if the laptop is one or 10 feet away from the router). Sometimes it shows it's connected but it doesn't works.

According to lspci it's
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```
I tried the steps that user *t0mppa* wrote about a year ago (changing ath5k with madwifi), compiled perfectly, but it didn't work (madwifi didn't seem to recognize (or initialize) the wireless adapter, so I couldn't set anything).
I also tried what user *aapo4* suggested a week ago (using compat-wireless). It also compiled perfectly, but it didn't solve my problem (like if I hadn't done anything).

I'll test the first solution again tomorrow.

Anyway, any insights on this problem?
Thanks!

---

### Post by forgewire on 2010-09-25
Thanks a lot. It seems a new Mint and Ubuntu adopted ath5k driver for Atheros chipsets wich sucks completely with aircrack and other tools. And it supposed to be a newer driver than madwifi. Damn it.
Madwifi forewer!

---

