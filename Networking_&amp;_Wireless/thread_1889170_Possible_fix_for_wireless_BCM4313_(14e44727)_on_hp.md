---
title: "Possible fix for wireless: BCM4313 (14e4:4727) on hp dm1 laptop with Ubuntu 11.10"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by ts3 on 2011-11-30
[FONT="Arial"]Originally, I posted this on another thread (an Acer user with same chipset) but it turned out that poster's issue with the wireless was entirely different.  I know there is a mega-sticky about BCM43xxx drivers but there are so many pages with questions and answers about different Broadcom chipsets that I thought I'd bring this out as a separate thread.  One caveat: I am new to Linux (10 days on this laptop, another 2 weeks on an old dell laptop) so please take everything I write with a grain of salt.

My set-up: hp dm1 4010us with single-boot 11.10.  Wireless did not work after the install so tried the following:

1) Activated the Broadcom STA proprietary drivers through System Info -> Additional Drivers
2) Tried the firmware-b43-installer and bwcutter through the Ubuntu Software Centre
3) Tried the bcmwl-kernel-source through the software center

The result I ended with after trying the three methods above:

[FONT="Courier New"]Device: wlan0
Type: 802.11 WiFi
Driver: brcmsmac
State: disconnected
Default: no[/FONT]

configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes[/FONT]

Still no wireless, the little icon on the top panel would say "wireless disconnected" and would not show any wireless networks in the vicinity.

I read around a little bit and found a solution that worked for my set-up:

1) The b-43 installer does not support BCM4313 (4727)
2) The bcmwl-kernel-source driver (found in the Ubuntu Software
Center) supports it but first one needs to make sure that
   a) b43 and the option to activate the STA Broadcom drivers through System Settings -> Additional Drivers are uninstalled/disabled
   b)that those drivers (b43, bcma, brcsmac) are blacklisted and 
   c) that the wl driver that works is NOT blacklisted

This is the short answer :) The long answer, which is basically a copy/paste from my original post on another thread, with some edits, is below.

---

### Post by ts3 on 2011-11-30
[This is the long explanation which is written by a complete newbie and explains everything I did in as much detail as I could.  I reckon other new users might find it useful.  I had to work out how to do things from first principles so if more experienced users want to correct this / move the thread etc. please do so]

For Broadcom wireless one can 1) use the b43 driver or 2) use the Broadcom proprietary drivers. Option 1) does not support BCM4313 so that's out. Trying 2) by going through System Info &#8594; Additional Drivers and activating the default doesn't work. My guess is that trying that step installs the brcmsmac driver, which does not work and messes up the wireless; the Broadcom driver for 4313 4727(based on Broadcom's website) is called wl. 


Broadcom has a good readme.txt on its website with the linux STA drivers ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) that explains how to make the whole thing from scratch but I didn't feel quite up to this yet. The readme.txt also has a little subheading called Fresh Installation that explains how to remove conflicts with the b43 install and other artefacts that unfortunately do not work for BCM4313:

[FONT="Courier New"]Fresh installation: (from Broadcom's readme.txt) 
1: Remove any other drivers for the Broadcom wireless device. There are several other drivers (besides this one) that can drive Broadcom 802.11 chips such as b43, bcma and ssb. They will conflict with this driver and need to be uninstalled before this driver can be installed. Any previous revisions of the wl driver also need to be removed. 

Note: On some systems such as Ubuntu 9.10, the ssb module may load during boot even though it is blacklisted (see note under Common Issues on how to resolve this. Nevertheless, ssb still must be removed (by hand or script) before wl is loaded. 

The wl driver will not function properly if ssb the module is loaded. 

# lsmod | grep "b43\|ssb\|bcma\|wl" 

If any of these are installed, remove them: 
# rmmod b43 
# rmmod ssb 
# rmmod bcma 
# rmmod wl 

To blacklist these drivers and prevent them from loading in the future: 
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf 
# echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf 
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf[/FONT] 

I did the lsmod and the rmmod commands but didn't start blacklisting through the terminal right away. 

Instead I went to the /etc/modprobe.d/blacklist.conf file and looked around a bit, it's quite interesting. Plus it's a read-only so one can't mess up too much by just opening. It blacklists a BCM43xx b/c it has been replaced by b43 and ssb, something that's not true for people with BCM 4313. There is also a file called blacklist-local.conf which blacklists wl. I reckon that was created by attempts to install b43. 

I googled a bit more and found some helpful answers on the launchpad:

[https://answers.launchpad.net/ubuntu...uestion/174596](https://answers.launchpad.net/ubuntu...uestion/174596)

[https://answers.launchpad.net/ubuntu...uestion/178522](https://answers.launchpad.net/ubuntu...uestion/178522)

Both strings explain how to resolve conflicts between bcma or brcmsmac and wl drivers: by blacklisting the conflicting drivers so that wl can run. I figured I'd also have to un-blacklist the wl driver if I want it to work :)

I edited the files by opening them from the terminal (opening through the regular file manager does not work, the files are read-only for regular users so one needs sudo):

[FONT="Courier New"]gksudo gedit /etc/modprobe.d/blacklist.conf[/FONT]

which opens the text editor and added 

[FONT="Courier New"]blacklist bcma
blacklist brmcsmac[/FONT] 

Then:

[FONT="Courier New"]gksudo gedit /etc/modprobe.d/blacklist-local.conf[/FONT]

and added a # in front of blacklist wl so the line became

[FONT="Courier New"]# blacklist wl[/FONT]

which I gather makes it a mere comment :)

I also went to System Info &#8594; Additional Drivers and removed the Broadcom STA driver, then went to Ubuntu Software Centre and removed the bcmwl-kernel-source. Ultimately I wanted it to run but I thought I'd re-install after re-booting. 

Then rebooted and reinstalled bcmwl-kernel-source and then broadcom-sta-source and broadcom-sta-common for good measure. All those packages come up in the Ubuntu Software Centre if one types “bcm” in the search box. Then rebooted again & the neighbourhood wireless networks popped up like a charm. Next day I went to the university and connected without any problems (don't actually have wireless at home).

One last thing – trying to fiddle with the Bluetooth settings messes the newly-hatched wireless up (sigh). I'm keeping the Bluetooth off and will try to find a way to disable it permanently.

Sorry for the long post: I am fairly new to Linux and had to work things out from scratch. When someone writes “blacklist the driver” this is rather meaningless to me. So I wrote out the steps with explanations hoping that it might help other users with the same blasted driver.

Again, if more experienced users want to correct or add please do so.

One last thing: the wireless troubleshooting guide ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)) is really useful for trying out the commands related to hardware set-up.

---

### Post by papadopo on 2011-12-02
Hello everybody,

I have followed the instructions from broadcom (as presented by TS3) and the problems I had with BCM4313 are solved. In fact, I faced these problems after I downgrade from 11.10 to 10.10 due to several reasons. In 11.10 the wireless was not working OK, since at a distance less than 10cm from the router, the signal was around 60%. In 10.10 wireless was not working at all (i.e., no nets were detected). The solution was to download the driver from broadcom, make them and them insert it as a module to be used by the kernel. FYI: I tried every possible alternative posted in the forums, and this one was the one that solved the wireless problems.

My laptop: HP g6 pavilion, 4GB RAM, 600GB HD, ATI RADEON Graphics, BCM4313 wireless.

Good luck to all,

Apostolos

---

### Post by ts3 on 2011-12-04
> **papadopo said:**
> I have followed the instructions from broadcom (as presented by TS3) and the problems I had with BCM4313 are solved. 

Ah, the magic of readme.txt files.  Glad it worked for someone else :)

---

### Post by ts3 on 2011-12-27
UPDATE: Fix for BCM4313 (4727) when running Ubuntu 10.04 LTS on same hp dm1 laptop

OK, so I started fiddling with partitions on the laptop (which has a whole thread all to itself :) ) and ended up installing 10.04 on a small partition on the same laptop.   Wireless, of course, did not work again.  

Using sudo lshw -C Network showed the network as UNCLAIMED which according to the 10.04 troubleshooting guide at [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html) indicates there was no driver associated.  The STA drivers did not turn up as an option to activate in the system preferences at all.  Rather than using wired to download the bcmwl-kernel-source I decided to follow this guide

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

namely the option STA - No Internet Access.  I followed the steps closely, with a few variations:

1) stick in the install USB and navigate to the packages listed below, then double-clicking to install:

../pool/main/p/patch  (the guide had this as second but patch was a dependency to dkms which would not install without patch being installed first)
../pool/main/d/dkms
../pool/main/f/fakeroot
../pool/restricted/b/bcmwl

2) restart (the second step in the guide, to navigate to system administration -> drivers -> STA drivers did not work, the STA driver still did not show; it appeared only after I connected to the internet and installed a bunch of updates)

3) Hit the hardware switch to make sure it is not blocking the connection

4) The next day the wireless network was showing as UNMANAGED and did not work again; I googled around (on a different device, obviously :) ) and came up with the following:

```
 gksudo gedit /var/lib/NetworkManager/NetworkManager.state 
```

and change NetworkingEnabled=false to NetworkingEnabled=true and also

```
 gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
```

and change managed=false to managed=true

I took this from post #4 in this thread [http://ubuntuforums.org/showthread.php?p=9402242](http://ubuntuforums.org/showthread.php?p=9402242)

Wireless on the 10.04 partition has been working since then but it is noticeably slower than the wireless on the 11.10 partition.  Oh, and it disappeared once by itself after suspend; the setting in one of the files listed in 4) above had reverted to false so had to change it back to true.

All in all having lots of fun with the wireless Broadcom driver and seriously thinking about buying a USB wireless card just in case the internet disappears completely at some point.  Using a wired connection or a mobile device to get to the internet to troubleshoot and search for answers may  not always be an option :) 

Still, troubleshooting the wireless connection has helped me learn a lot about the system, where things are and how to use the terminal to do useful stuff.  Very happy with Ubuntu and looking forward to 12.04 :)

---

### Post by ts3 on 2012-01-02
Another Update: building the Broadcom driver from scratch without wireless on 10.04 (and mint 12)

The STA driver on 10.04 (activation as described in the post above) turned out to be pretty useless (very weak wireless signal that kept disappearing completely) so I ended up going back to the broadcom drivers and installing without having internet access on the laptop (though I still needed another computer to download the driver).

Short answer 
1) Go to [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
2) Download the driver to USB
3) Build driver

Long answer

1) On a computer with internet access (or on Ubuntu 11.10 with working wireless on same laptop) go to the broadcom website and download the correct (32-bit or 64-bit) version of the driver and the readme.txt
2) Save the driver (and the readme, or even better, print the readme) on a USB
3) Boot 10.04 (or Mint 12) and drag the driver on the desktop
4) Follow the instructions from the readme fairly closely with some modifications:
[LIST]
[*]mkdir hybrid_wl (makes the directory)
[*]cd hybrid_wl (changes to that directory)
[*]tar xzf /home/myusername/Desktop/hybrid-portsrc_x86_64-v5_100_82_112.tar.gz (make sure the name of the file is correct, it's changed since the readme was written and may change again)
[*]make
[*]follow instructions for fresh installations (see readme and earlier post above, make sure all unwanted broadcom drivers such as bcma and brcmsmac are blacklisted and that wl is NOT blacklisted)
[*]sudo modprobe lib80211 (or try the other one, ieee80211_crypt_tkip and see which works, you get a "module not found" message for the one that doesn't)
[*]sudo modprobe cfg80211 
[*]sudo insmod wl.ko (make sure you're still in hybrid_wl directory, if not type cd hybrid_wl, if there are errors check the readme for solutions) (at this point the wireless should be working, the next few steps are to load the driver at boot)
[*]uname -r (to get the kernel version, make a note of it, the one for Mint 12 was 3.0.0-12-generic)
[*]cp /boot/initrd.img-3.0.0-12-generic /home/username/Desktop (to back up the current boot ramfs onto the desktop, replace the kernel version with the results from previous command)
[*]sudo update-initramfs -u (generates new one)
[*]sudo reboot
[*]load the driver again (sudo modprobe lib80211, sudo modprobe cfg80211, cd hyrbrid_wl, sudo insmod wl.ko)
[*]sudo cp wl.ko /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless
[*]sudo depmod -a
[/LIST]

The last two commands make the driver load at boot time and worked both for 10.04 and Mint 12, the readme describes some steps for Fedora/Suse as well).  

A few things to keep in mind: 
[LIST]
[*]It's important to get the correct version of the kernel (I have different ones for 11.10, 10.04 and Mint 12) to use in some of the commands above
[*]When working with the wl.ko file it's important to be in the correct directory (cd hybrid_wl)
[*]I got a lot of errors from mistyping the file names and the kernel version (pay attention to dots, dashes and _)
[*]The "Permission denied" error is due to not using sudo when it's needed; it was a bit of a trial and error for me but it worked at the end
[/LIST]

The wireless with this driver on 10.04 is really strong, shows 4-5 bars where the STA driver showed one bar and kept dropping the connection.  Building a driver from scratch is a bit daunting but I managed, with some trial and error, and it worked in both 10.04 and Mint 12.  So I've decided to keep the driver on a USB and build every time I install something on this laptop and run into the same problem.

Cheers :)

---

### Post by 23senick on 2012-01-08
[FONT=Arial][SIZE=2]This fix worked for me - I had wireless but **very** weak (unusable) compared to windows. Brand new HP dm1 4020 dual boot.  

If you have this problem (no wifi or very weak signal) on a laptop equipped with Broadcom 4313 wireless, seems the place to start is checking which drivers Ubuntu is running for it - so go straight to terminal[/SIZE][/FONT] [FONT=Arial][SIZE=2](CTRL+ALT+T in Ubuntu) and type[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]lshw -C network[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial][SIZE=2]If the driver shown is something like &#8220;bcma&#8221; or &#8220;brmcsmac&#8221; Ubuntu isn't loading the right driver [/SIZE][/FONT][FONT=Arial][SIZE=2] (sort this out please!)[/SIZE][/FONT]

[FONT=Arial][SIZE=2]So what you need to do is blacklist the old drivers so Ubuntu does not load them when booting, as instructed by TS3 - I'll repeat so you don't need to find relevant section[/SIZE][/FONT] 

[FONT=Arial][SIZE=2]Firstly I disabled the proprietary driver (system/additional drivers).  Checked in Ubuntu Software Centre that all drivers were removed (type "bcm" in the search window and if any Broadcom drivers are shown as installed &#8211; uninstall them).  Then open terminal and type[/SIZE][/FONT]

[FONT=Arial][SIZE=2]gksudo gedit /etc/modprobe.d/blacklist.conf[/SIZE][/FONT][FONT=Arial][SIZE=2]

which opens the text editor for the blacklist file, and I added 

[/SIZE][/FONT][FONT=Arial][SIZE=2]# poor wireless [/SIZE][/FONT] 
[FONT=Arial][SIZE=2]blacklist bcma
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]# poor wireless 2[/SIZE][/FONT]
[FONT=Arial][SIZE=2]blacklist brmcsmac[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Then save the file.  Reboot, and then go into Ubuntu Software Centre again - search "bcm" and reinstall bcmwl-kernel-source and then broadcom-sta-source and broadcom-sta-common.[/SIZE][/FONT]

You may need to go into "System settings/additional drivers" and ensure the broadcom driver is enabled.

[FONT=Arial][SIZE=2]After this I rebooted and found wireless was at full strength[/SIZE][/FONT] :D

---

### Post by ts3 on 2012-01-08
> **23senick said:**
> After this I rebooted and found wireless was at full strength :D

I am so glad this works for other people with the same chipset as well :) Thanks for sharing and thanks for summarising my posts (I tend to get a bit long-winded but as a newbie I'd rather over-explain than under-explain).

Also thanks for pointing out that the specific chipset (BCM4313 (14e4:4727) is important: different drivers work for different chipsets and by trying out all at the beginning one can mess up the system.

Again, glad it worked.  Cheers :)

---

### Post by 23senick on 2012-01-10
I should thank you - I was actually starting to wonder if I would have to use windows on the new laptop. Yuk!

I still find the laptop sometimes takes time to access the router. Hangs for a while with repeated requests for password every couple of minutes.  When it does connect, all is well - but frustrating..  Seems to work if I disable wireless for a few minutes then re-enable.  Any ideas?

---

### Post by ts3 on 2012-01-10
> **23senick said:**
> Any ideas?
Sorry, no :(  Mine's been working without a hitch since I figured out how to install the driver.  Try starting a new thread, there are a lot of experienced Ubuntu users around who may be able to help :)

---

### Post by qwestt on 2012-01-11
> **23senick said:**
> [FONT=Arial][SIZE=2]This fix worked for me - I had wireless but **very** weak (unusable) compared to windows. Brand new HP dm1 4020 dual boot.  

If you have this problem (no wifi or very weak signal) on a laptop equipped with Broadcom 4313 wireless, seems the place to start is checking which drivers Ubuntu is running for it - so go straight to terminal[/SIZE][/FONT] [FONT=Arial][SIZE=2](CTRL+ALT+T in Ubuntu) and type[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]lshw -C network[/SIZE][/FONT][FONT=Arial][SIZE=2]

[/SIZE][/FONT][FONT=Arial][SIZE=2]If the driver shown is something like “bcma” or “brmcsmac” Ubuntu isn't loading the right driver [/SIZE][/FONT][FONT=Arial][SIZE=2] (sort this out please!)[/SIZE][/FONT]

[FONT=Arial][SIZE=2]So what you need to do is blacklist the old drivers so Ubuntu does not load them when booting, as instructed by TS3 - I'll repeat so you don't need to find relevant section[/SIZE][/FONT] 

[FONT=Arial][SIZE=2]Firstly I disabled the proprietary driver (system/additional drivers).  Checked in Ubuntu Software Centre that all drivers were removed (type "bcm" in the search window and if any Broadcom drivers are shown as installed – uninstall them).  Then open terminal and type[/SIZE][/FONT]

[FONT=Arial][SIZE=2]gksudo gedit /etc/modprobe.d/blacklist.conf[/SIZE][/FONT][FONT=Arial][SIZE=2]

which opens the text editor for the blacklist file, and I added 

[/SIZE][/FONT][FONT=Arial][SIZE=2]# poor wireless [/SIZE][/FONT] 
[FONT=Arial][SIZE=2]blacklist bcma
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]# poor wireless 2[/SIZE][/FONT]
[FONT=Arial][SIZE=2]blacklist brmcsmac[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Then save the file.  Reboot, and then go into Ubuntu Software Centre again - search "bcm" and reinstall bcmwl-kernel-source and then broadcom-sta-source and broadcom-sta-common.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]After this I rebooted and found wireless was at full strength[/SIZE][/FONT] :D:KS
:KS
[SIZE=2]**after reboot  need open " ADDITIONAL DRIVERS" and choose**" **Broadcom STA wireless driver " again!**
[B]after this my wi-fi modul is correct
Thank you very much [COLOR=Red]23 sennick[/COLOR]![/B] **You are super star!!**!:popcorn:[/SIZE]
[SIZE=2]**my system is ubuntu 11.10  (3.0.0.15-17).  my machine is  hp Pavilion dm 1 4000**[/SIZE]

---

### Post by ts3 on 2012-01-11
> **qwestt said:**
> after reboot  need open " ADDITIONAL DRIVERS" and choose "Broadcom STA wireless driver" again. after this my wi-fi modul is correct

I am glad your wireless works :) 

In my experience however, the STA driver from Additional drivers did not work with BCM4313 (14e4:4727).  Who knows, maybe the issue has been fixed by an Ubuntu update.

Out of curiosity, would you mind posting the result from

```
lspci -k
```

and then 

```
lspci -n | grep 14e4
```

These commands check the device ID of the Broadcom wireless card.  Thanks & again, congrats on getting the wireless working :)

---

### Post by 1slyfox on 2012-01-21
ts3,

I just wanted to say thanks.  I'm a linux noob, and after experiencing poor wireless, I started reading through thread after thread to find a fix.  Between trying the proprietary driver and the firmware-b43-installer I ended up with no working internet.  Following your step by step, I'm now getting a great connection.

It seems the blacklist entries caused most of the issues, and it begs the question... If a package is removed, shouldn't it remove any blacklist entries it made?

---

### Post by ts3 on 2012-01-23
> **1slyfox said:**
> ts3,

I just wanted to say thanks.  I'm a linux noob, and after experiencing poor wireless, I started reading through thread after thread to find a fix.  Between trying the proprietary driver and the firmware-b43-installer I ended up with no working internet.  Following your step by step, I'm now getting a great connection.

It seems the blacklist entries caused most of the issues, and it begs the question... If a package is removed, shouldn't it remove any blacklist entries it made?

You are entirely welcome :) Believe me when I started this thread I was in the same situation (new to Linux, messed up wireless from multiple driver installs etc.)  Glad the fix works for other people.

As to the blacklist entries I am thinking of filing a bug (if I can figure out how to do that and if it hasn't been filed yet).  

Cheers :)

---

### Post by TnTMike on 2012-02-24
Many thanks ts3, I was struggling but your fix is working a treat. My driver is listed as wl0 & like you, I do not have the STA driver enabled in system settings.

---

### Post by ts3 on 2012-02-24
> **TnTMike said:**
> Many thanks ts3, I was struggling but your fix is working a treat. My driver is listed as wl0 & like you, I do not have the STA driver enabled in system settings.

You are entirely welcome, I'm glad your wireless is up and running.  

As to the step-by-step fix I suspect it's a bit like using a hammer to kill an ant (a bug?).  If someone really knows what they're doing they can probably diagnose and solve the issue with a couple of elegant commands in the terminal.  Since I don't that much I ended up with a lot of blacklisting, rmmod-ing and rebooting but it seems to work so I'm happy.

Cheers :)

---

### Post by hansum_rahul on 2012-02-26
On my [COLOR="Red"]lenovo B570[/COLOR], the drivers from the the broadcom website could enable wifi and scan as well, but **could not be used in ad-hoc mode**. The same goes for the kernel modules, versions 5.100+ which is already in the ubuntu repository.

I needed the **bcmwl** source code in Ubuntu 10.04 LTS repository for bcmwl-kernel-source version 5.60.48.36_ubuntu5.

[http://packages.ubuntu.com/lucid/bcmwl-kernel-source]("http://packages.ubuntu.com/lucid/bcmwl-kernel-source")

This would install but the compilation fails.

So, after patching the source files (there are 4 patches) the driver compiles. After which blacklisting and installing the drivers worked like a charm!

---

### Post by angelsaint02 on 2012-02-28
I have a HP G7-1310us with this wireless adapter and I'm running 11.10. I am very new and could really use a step by step "how to" on what order exactly all this should be done in with the commands that I can basically copy and paste so I do not screw it up.  In the mean time I will be attempting to read through and figure this out. Thanks for the help.

---

### Post by ts3 on 2012-02-28
> **angelsaint02 said:**
> I have a HP G7-1310us with this wireless adapter and I'm running 11.10. I am very new and could really use a step by step "how to" on what order exactly all this should be done in with the commands that I can basically copy and paste so I do not screw it up.  In the mean time I will be attempting to read through and figure this out. Thanks for the help.

Hello, just saw your post here :)  I am going to crib shamelessly from wildmanne39 who seems to be one of the resident wireless gurus.  Here's a copy of wildmanne39's post from this thread [http://ubuntuforums.org/showthread.php?p=11720073#post11720073](http://ubuntuforums.org/showthread.php?p=11720073#post11720073) :

"Hi, please post the output of:
```

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets"

These commands gather some basic information about the wireless and seem to be a good starting point.  I am also hoping that wildmanne39 might step in at some point and lend a hand :)

---

### Post by sportsdude81 on 2012-03-02
TS3 your instructions worked great to fix the bad sta driver on my new HP folio.  Many Thanks

---

### Post by ts3 on 2012-03-02
> **sportsdude81 said:**
> TS3 your instructions worked great to fix the bad sta driver on my new HP folio.  Many Thanks

You're welcome, glad your wireless is up and running.  I wish the open source drivers worked for BCM4313 and I am sure that at some point they will :)

---

### Post by ts3 on 2012-03-09
UPDATE: Broadcom 4313 on 12.04 Precise Beta 1

I like thorough documentation and am not afraid to post to myself :) so here it goes:

Just installed 12.04 beta 1 on its own partition (bye-bye Mint) and had to tackle the wireless again but this time it was easier.  Perhaps the driver works better out of the box or perhaps I know a bit more about the blasted BCM4313 so didn't flail around too much.  Anyway, upon a clean install running 

```
lspci -k
```

gives 

```
kernel driver in use: brcmsmac
kernel modules: bcma, brcmsmac
```

The open-source brcmsmac, alas, still does not work with 4313.  I wish it did, I'd like nothing better than not having proprietary drivers on my hp laptop but I also do need the wireless :)

Anyway, going to Additional Drivers in System Info and activating the STA drivers adds the wl (WL)  driver to kernel modules.  To make it work immediately:

```
sudo rmmod bcma
sudo rmmod brcmsmac
sudo rmmod wl
```

to remove all drivers and avoid conflicts.  Then 

```
sudo modprobe wl
```

to load just the wl driver.  To make the changes permanent open the blacklist file in a text editor (in this case gedit) with root privileges by running 

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

and add the lines

```
blacklist bcma
blacklist brcmsmac
```

somewhere handy. Proofread, save and close.  Enjoy :)

I am still hoping that brcmsmac will start working at some point and intend to check again when I install 12.04 proper in April but until then wl will have to do.

---

### Post by irishetalon007 on 2012-03-11
Hello, and thank you! I now have full bars on my second floor when my router is 2 floors below!

My only problem is that even after getting it working and completing your instructions, I still have to do:
sudo modprobe lib80211
sudo modprobe cfg80211
sudo insmod wl.ko

after every restart. For some reason, which I can't figure out, the driver isn't loading after restart. any suggestions?

Thanks again!

---

### Post by ts3 on 2012-03-12
> **irishetalon007 said:**
> For some reason, which I can't figure out, the driver isn't loading after restart. any suggestions? Thanks again!

You're welcome, glad the wireless is working :)

As to loading at boot time, I've pasted below straight from the Broadcom readme.txt and have added my comments in square brackets and underlined:

"3: Setup to always load at boot time.

The procedure to make a module load at boot time varies from distro to distro.  Consult the docs for your specific distro to see how.  The following seems to work for my setup on Fedora and Ubuntu.  Check your docs to see the procedure for your distro.

Follow these steps to have the driver load as part of the boot process:

# load driver as described above _[My comment: these are the steps that you are doing up to insmod wl.ko]_
# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless _[My comment: need to add sudo at the beginning; check the kernel version by running uname -r in terminal and substitute above for `uname -r`; I think the way the command is written, with slanted quotes, probably pulls the kernel version automatically but I wasn't sure and didn't want to experiment so I just typed the kernel manually; also, you need to change directory to hybrid_wl and run the copy command from there; you're basically copying the wl.ko file to the /lib directory; you can use the file manager to go to /lib/modules/3.0.0-16/kernel/drivers/net/wireless and check that the file is there]_
# depmod -a _[My comment: again, add sudo here, this is for the module dependencies]_

# echo modeprobe wl >> /etc/rc.local  (Fedora/SUSE) _[My comment: I didn't do that, I don't remember why but I checked at the time and I don't think you need for Ubuntu]_ 

Ubuntu ships a version of wl.ko, so those need to be disabled.  On my system the were several versions, so I searched and renamed the .ko's like this:

# sh: for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done _[My comment: I did not run this either but I did search for other wl.ko files in /lib/ and didn't find any]_" End of quote from Broadcom readme.txt

Building the driver from scratch is probably the most difficult way to get a working wireless, I only did it once to make sure that I could build it if I had absolutely no access to wired internet.  

The easier way would be to remove and blacklist all conflicting drivers and then download the wl driver from Ubuntu Software Centre (search for "bcmwl" there and download all three) using wired internet.

P.S. I just looked through my printout of the readme file and my notes: it's probably a good idea to generate a new initramfs if you haven't done so (check the broadcom file on how to do that: back up the current one initrd.img, run update-initramfs -u to replace with new and then reboot)

P.P.S.  Please please double-check how your system is set-up before running any of those commands as I don't know nearly enough to give advice.  At the time before running any of those I'd browse to the relevant directory to make sure it existed before copying files there :)

---

### Post by irishetalon007 on 2012-03-12
thank you, sir, for the quick response!

I've looked over your post and the readme multiple times, and I've tried everything and can't get it to load on startup.

I guess I don't know enough about the kernel.

When I do lsmod after startup it doesn't list anything that I need loaded.

So after every startup, I have to do a "sudo modprobe wl" and then everything works, and in lsmod I see:


lib80211_crypt_tkip     8676  0 
wl                   2590926  0 
cfg80211              148725  1 wl
lib80211                6151  2 lib80211_crypt_tkip,wl

depmod -a should be loading these on startup, right? for some reason it isn't.

Any help is greatly appreciated!

UPDATE:::

I got it working by inserting the line "wl" into /etc/modules

I don't know why I had to do this, I'm confused how/why others were able to follow this guide and not have to edit /etc/modules. 
Can someone who got this working give a printout of their /etc/modules to see what's there?

---

### Post by ts3 on 2012-03-13
> **irishetalon007 said:**
> Can someone who got this working give a printout of their /etc/modules to see what's there?  

Sorry, took me a while to get to the actual laptop and look at the file you were asking about.  Here's my /etc/modules, it's the same in 11.10 and in 12.04 beta 1:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
```For what it's worth I haven't made any changes to the file.  LP seems to be for a parallel port printer that I have no use for so I am considering commenting it out; RTC seems to stand for Real Time Clock so I am definitely leaving that one in.

Ultimately, you have a working wireless so I wouldn't worry too much about having to add a module to load at boot.  Perhaps take a look at /etc/modprobe.d, particularly at the blacklist.conf but also at the other files to make sure wl is not blacklisted somewhere.

Cheers :)

---

### Post by irishetalon007 on 2012-03-14
Thanks for all your help!!!:guitar:

---

### Post by pmheideman on 2012-04-21
I just upgraded to 12.04 beta 2, and my BCM4313 has, once more, crapped out.  I tried the solution above, but when I tried to enable the STA driver in Additional Drivers, I got an error.  In /var/logs/jockey.log, it gives me:



[PHP]2012-04-21 16:58:42,474 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-21 16:58:43,597 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-21 16:58:48,256 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-21 16:58:48,258 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-04-21 16:58:48,360 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
[/PHP]lspci -k yields

[PHP]
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 1795
    Kernel modules: bcma, brcmsmac
[/PHP]

---

### Post by wildmanne39 on 2012-04-21
Hi pmheideman, please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot
Thanks

---

### Post by ts3 on 2012-04-21
> **pmheideman said:**
> I just upgraded to 12.04 beta 2, and my BCM4313 has, once more, crapped out.  I tried the solution above, but when I tried to enable the STA driver in Additional Drivers, I got an error.  In /var/logs/jockey.log, it gives me:



[PHP]2012-04-21 16:58:42,474 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-21 16:58:43,597 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-21 16:58:48,256 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-21 16:58:48,258 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-04-21 16:58:48,360 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
[/PHP]lspci -k yields

[PHP]
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Hewlett-Packard Company Device 1795
    Kernel modules: bcma, brcmsmac
[/PHP] 

I googled the /var/log error and found a couple of posts that might help:

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979) where the poster in post #9 had to install linux-headers for the new kernel after an upgrade (it seems the problem affected people who had built the wl driver manually).

I was going to suggest on general principles first to install all updates (obviously you need wired internet for this), then to take a look at /etc/modprobe.d/blacklist.conf to make sure wl is not blacklisted there and also to check the other blacklist files in that directory (I remember finding wl blacklisted in a file called blacklist-local.conf).  

You can try to install the driver through the software centre, type wl in the search field and install bcmwl-source and the two sta something or other packages that come up, or through the command line with apt-get install.

If you have wired internet and can try any of those suggestion then great.  If worse comes to worse you may need to build the driver from the broadcom website but you'll need linux-headers and other tools for that as well.  It's not fun but it's doable.

Also, check this thread, in particular post #44 and post #84, great info and some suggestions on how to troubleshoot BCM4313 using the scorched earth approach (once the wireless gets messed up uninstall and re-install everything and reboot a few times for good measure; this is what worked for me the first time around too).  Also, people who have the acer-wmi module need to blacklist that apparently.

If anyone has other suggestions or experience please jump in :)  Reckon there'll be a lot of broadcom posts with the 12.04 upgrade getting closer and closer.

EDITED TO ADD: Please ignore the above and listen to wildemanne39, he knows what he's doing when it comes to troubleshooting wireless :)

---

### Post by pmheideman on 2012-04-22
Thanks for the quick replies folks!  So I tried what wildmanne39 suggested, but no dice.  bcma and brcmsmac are both in blacklist.conf, but lspci -k still lists them as the drivers.  I also went through all my blacklist files, and I couldn't find WL in any of them, though in broadcom-sta-common.conf there's a line that reads
```
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
```

According to software center, wl is already installed.  Also, I'm still getting the same error message when I try to install STA from additional drivers.

Here's everything from jockey.log for the latest error:
```

2012-04-22 12:01:08,759 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c>
2012-04-22 12:01:12,331 DEBUG: reading modalias file /lib/modules/3.2.0-23-generic-pae/modules.alias
2012-04-22 12:01:12,681 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-04-22 12:01:12,710 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-04-22 12:01:12,837 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2012-04-22 12:01:12,884 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2012-04-22 12:01:12,885 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2012-04-22 12:01:12,939 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2012-04-22 12:01:12,940 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-04-22 12:01:13,050 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-04-22 12:01:13,051 DEBUG: Firmware for DVB cards not available
2012-04-22 12:01:13,051 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2012-04-22 12:01:13,067 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2012-04-22 12:01:13,077 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2012-04-22 12:01:13,341 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2012-04-22 12:01:13,342 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-04-22 12:01:13,412 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-04-22 12:01:13,423 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-04-22 12:01:13,426 DEBUG: nvidia.available: falling back to default
2012-04-22 12:01:13,471 DEBUG: XorgDriverHandler(nvidia_96, nvidia-96, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-22 12:01:13,471 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-22 12:01:13,480 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-04-22 12:01:13,490 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-04-22 12:01:13,492 DEBUG: nvidia.available: falling back to default
2012-04-22 12:01:13,577 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-04-22 12:01:13,583 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2012-04-22 12:01:13,591 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2012-04-22 12:01:13,593 DEBUG: nvidia.available: falling back to default
2012-04-22 12:01:13,678 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-22 12:01:13,687 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2012-04-22 12:01:13,698 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2012-04-22 12:01:13,700 DEBUG: nvidia.available: falling back to default
2012-04-22 12:01:13,741 DEBUG: XorgDriverHandler(nvidia_173_updates, nvidia-173-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-22 12:01:13,742 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-22 12:01:13,751 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-04-22 12:01:13,761 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-04-22 12:01:13,763 DEBUG: nvidia.available: falling back to default
2012-04-22 12:01:13,813 DEBUG: XorgDriverHandler(nvidia_173, nvidia-173, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-22 12:01:13,814 DEBUG: NVIDIA accelerated graphics driver not available
2012-04-22 12:01:13,822 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2012-04-22 12:01:13,833 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2012-04-22 12:01:13,835 DEBUG: nvidia.available: falling back to default
2012-04-22 12:01:13,879 DEBUG: XorgDriverHandler(nvidia_96_updates, nvidia-96-updates, None): Disabling as package video ABI xorg-video-abi-10 does not match X.org video ABI xorg-video-abi-11
2012-04-22 12:01:13,879 DEBUG: NVIDIA accelerated graphics driver (post-release updates) not available
2012-04-22 12:01:13,879 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-04-22 12:01:13,891 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-04-22 12:01:13,893 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-04-22 12:01:13,893 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-04-22 12:01:13,893 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-04-22 12:01:13,905 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-22 12:01:13,950 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-04-22 12:01:13,950 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-04-22 12:01:13,951 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-04-22 12:01:14,000 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-04-22 12:01:14,047 DEBUG: Software modem not available
2012-04-22 12:01:14,047 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-04-22 12:01:14,062 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-22 12:01:14,072 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-04-22 12:01:14,073 DEBUG: fglrx.available: falling back to default
2012-04-22 12:01:14,162 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2012-04-22 12:01:14,175 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-22 12:01:14,186 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-04-22 12:01:14,186 DEBUG: fglrx.available: falling back to default
2012-04-22 12:01:14,270 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-04-22 12:01:14,270 DEBUG: all custom handlers loaded
2012-04-22 12:01:14,271 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d00001314sv0000103Csd00003387bc04sc03i00')
2012-04-22 12:01:14,851 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-22 12:01:15,053 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,054 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-22 12:01:15,063 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,063 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,063 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,088 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2012-04-22 12:01:15,089 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-22 12:01:15,089 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-22 12:01:15,090 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d00004394sv0000103Csd00003387bc01sc06i01')
2012-04-22 12:01:15,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'platform:pcspkr')
2012-04-22 12:01:15,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2012-04-22 12:01:15,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2012-04-22 12:01:15,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-22 12:01:15,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,100 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,100 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-22 12:01:15,101 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-22 12:01:15,126 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,127 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-22 12:01:15,127 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,127 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,128 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-22 12:01:15,128 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-22 12:01:15,128 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,129 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-22 12:01:15,130 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-04-22 12:01:15,136 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-22 12:01:15,137 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-22 12:01:15,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2012-04-22 12:01:15,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-22 12:01:15,138 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v0BDAp0138d3882dc00dsc00dp00ic08isc06ip50')
2012-04-22 12:01:15,164 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek'}
2012-04-22 12:01:15,164 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ums_realtek', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,164 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2012-04-22 12:01:15,165 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:SYN1E50:PNP0F13:')
2012-04-22 12:01:15,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-22 12:01:15,165 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d00009806sv0000103Csd00003387bc03sc00i00')
2012-04-22 12:01:15,172 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2012-04-22 12:01:15,238 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:15,239 DEBUG: fglrx_updates is not the alternative in use
2012-04-22 12:01:15,172 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-22 12:01:15,248 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-04-22 12:01:15,258 DEBUG: fglrx.available: falling back to default
2012-04-22 12:01:15,335 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:15,336 DEBUG: fglrx_updates is not the alternative in use
2012-04-22 12:01:15,305 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2012-04-22 12:01:15,336 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2012-04-22 12:01:15,367 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:15,367 DEBUG: fglrx is not the alternative in use
2012-04-22 12:01:15,337 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-22 12:01:15,376 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-04-22 12:01:15,387 DEBUG: fglrx.available: falling back to default
2012-04-22 12:01:15,456 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:15,457 DEBUG: fglrx is not the alternative in use
2012-04-22 12:01:15,427 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2012-04-22 12:01:15,458 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2012-04-22 12:01:15,458 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,458 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-22 12:01:15,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-22 12:01:15,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-22 12:01:15,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-22 12:01:15,459 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v0A5Cp21E3d0112dcFFdsc01dp01icFFisc01ip01')
2012-04-22 12:01:15,469 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-22 12:01:15,470 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,470 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,472 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00003387bc0Csc05i00')
2012-04-22 12:01:15,481 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2012-04-22 12:01:15,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,482 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2012-04-22 12:01:15,482 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,482 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-22 12:01:15,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,483 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,483 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-22 12:01:15,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,484 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0003v064EpD217e0292-e0,1,kD4,ramlsfw')
2012-04-22 12:01:15,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,484 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,484 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-22 12:01:15,485 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,485 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v0A5Cp21E3d0112dcFFdsc01dp01icFEisc01ip01')
2012-04-22 12:01:15,485 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-22 12:01:15,486 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,486 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-22 12:01:15,486 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,486 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,486 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-22 12:01:15,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,487 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-22 12:01:15,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,487 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-22 12:01:15,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,487 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-22 12:01:15,487 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,488 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00003387bc0Csc03i20')
2012-04-22 12:01:15,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.13:bd12/13/2011:svnHewlett-Packard:pnHPPaviliondm1NotebookPC:pvr0696110000204600000320100:rvnHewlett-Packard:rn3387:rvr36.15:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-22 12:01:15,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-22 12:01:15,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-22 12:01:15,523 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,524 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,524 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2012-04-22 12:01:15,524 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,524 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-22 12:01:15,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v064EpD217d0292dcEFdsc02dp01ic0Eisc01ip00')
2012-04-22 12:01:15,525 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo'}
2012-04-22 12:01:15,526 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-22 12:01:15,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-22 12:01:15,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v0A5Cp21E3d0112dcFFdsc01dp01icFFiscFFipFF')
2012-04-22 12:01:15,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'btusb'}
2012-04-22 12:01:15,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'btusb', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-22 12:01:15,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi'}
2012-04-22 12:01:15,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hp_wmi', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00003387bc02sc00i00')
2012-04-22 12:01:15,544 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2012-04-22 12:01:15,544 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,544 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00003387bc04sc03i00')
2012-04-22 12:01:15,551 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-22 12:01:15,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2012-04-22 12:01:15,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'platform:eisa')
2012-04-22 12:01:15,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-22 12:01:15,554 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,554 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-22 12:01:15,554 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,554 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-22 12:01:15,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'usb:v064EpD217d0292dcEFdsc02dp01ic0Eisc02ip00')
2012-04-22 12:01:15,555 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00003387bc06sc01i00')
2012-04-22 12:01:15,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-22 12:01:15,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,564 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-22 12:01:15,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2012-04-22 12:01:15,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,579 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2012-04-22 12:01:15,579 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,579 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-22 12:01:15,580 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,580 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,580 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000103Csd00001795bc02sc80i00')
2012-04-22 12:01:15,658 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2012-04-22 12:01:15,659 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:15,659 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-04-22 12:01:15,665 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-22 12:01:15,667 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:15,666 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2012-04-22 12:01:15,667 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac'}
2012-04-22 12:01:15,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'brcmsmac', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,668 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'bcma'}
2012-04-22 12:01:15,668 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'bcma', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-22 12:01:15,669 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,670 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,670 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2012-04-22 12:01:15,670 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,670 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-22 12:01:15,671 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2012-04-22 12:01:15,671 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-04-22 12:01:15,672 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb724fd0c> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-22 12:01:15,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d00001314sv0000103Csd00003387bc04sc03i00')
2012-04-22 12:01:15,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2012-04-22 12:01:15,672 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001703sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001702sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-04-22 12:01:15,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-04-22 12:01:15,673 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d00004394sv0000103Csd00003387bc01sc06i01')
2012-04-22 12:01:15,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'platform:pcspkr')
2012-04-22 12:01:15,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2012-04-22 12:01:15,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-04-22 12:01:15,674 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v1D6Bp0001d0302dc09dsc00dp00ic09isc00ip00')
2012-04-22 12:01:15,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001704sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,')
2012-04-22 12:01:15,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0103:')
2012-04-22 12:01:15,675 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001718sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'platform:hp-wmi')
2012-04-22 12:01:15,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2012-04-22 12:01:15,676 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2012-04-22 12:01:15,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2012-04-22 12:01:15,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001510sv00001022sd00001510bc06sc00i00')
2012-04-22 12:01:15,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4')
2012-04-22 12:01:15,677 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v0BDAp0138d3882dc00dsc00dp00ic08isc06ip50')
2012-04-22 12:01:15,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:SYN1E50:PNP0F13:')
2012-04-22 12:01:15,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-04-22 12:01:15,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d00009806sv0000103Csd00003387bc03sc00i00')
2012-04-22 12:01:15,678 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0200:')
2012-04-22 12:01:15,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-04-22 12:01:15,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0000:')
2012-04-22 12:01:15,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0100:')
2012-04-22 12:01:15,679 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v0A5Cp21E3d0112dcFFdsc01dp01icFFisc01ip01')
2012-04-22 12:01:15,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001719sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d00004385sv0000103Csd00003387bc0Csc05i00')
2012-04-22 12:01:15,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001701sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,680 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw')
2012-04-22 12:01:15,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0003v064EpD217e0292-e0,1,kD4,ramlsfw')
2012-04-22 12:01:15,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v0A5Cp21E3d0112dcFFdsc01dp01icFEisc01ip01')
2012-04-22 12:01:15,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,14D,14E,ra0,1,18,1C,2F,35,36,39,mlsfw')
2012-04-22 12:01:15,681 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d00004396sv0000103Csd00003387bc0Csc03i20')
2012-04-22 12:01:15,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.13:bd12/13/2011:svnHewlett-Packard:pnHPPaviliondm1NotebookPC:pvr0696110000204600000320100:rvnHewlett-Packard:rn3387:rvr36.15:cvnHewlett-Packard:ct10:cvrChassisVersion:')
2012-04-22 12:01:15,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-04-22 12:01:15,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2012-04-22 12:01:15,682 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00')
2012-04-22 12:01:15,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v064EpD217d0292dcEFdsc02dp01ic0Eisc01ip00')
2012-04-22 12:01:15,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0303:')
2012-04-22 12:01:15,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:PNP0800:')
2012-04-22 12:01:15,683 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001700sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v0A5Cp21E3d0112dcFFdsc01dp01icFFiscFFipFF')
2012-04-22 12:01:15,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C')
2012-04-22 12:01:15,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v000010ECd00008168sv0000103Csd00003387bc02sc00i00')
2012-04-22 12:01:15,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d00004383sv0000103Csd00003387bc04sc03i00')
2012-04-22 12:01:15,684 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'platform:eisa')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0011v0001p0001eAB83-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'usb:v064EpD217d0292dcEFdsc02dp01ic0Eisc02ip00')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001002d0000439Dsv0000103Csd00003387bc06sc01i00')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'platform:lis3lv02d')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v00001022d00001716sv00000000sd00000000bc06sc00i00')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-04-22 12:01:15,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2012-04-22 12:01:15,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'pci:v000014E4d00004727sv0000103Csd00001795bc02sc80i00')
2012-04-22 12:01:15,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-04-22 12:01:15,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2012-04-22 12:01:15,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb694e8ec> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2012-04-22 12:01:15,804 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:15,805 DEBUG: fglrx_updates is not the alternative in use
2012-04-22 12:01:15,908 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:15,956 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:15,957 DEBUG: fglrx is not the alternative in use
2012-04-22 12:01:16,020 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:16,021 DEBUG: fglrx_updates is not the alternative in use
2012-04-22 12:01:16,139 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:16,140 DEBUG: fglrx_updates is not the alternative in use
2012-04-22 12:01:16,181 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:16,245 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:16,246 DEBUG: fglrx is not the alternative in use
2012-04-22 12:01:19,289 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:19,430 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:23,788 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:28,499 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-04-22 12:01:28,501 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-04-22 12:01:28,629 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:30,534 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:30,535 DEBUG: fglrx_updates is not the alternative in use
2012-04-22 12:01:30,583 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:30,662 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:30,663 DEBUG: fglrx is not the alternative in use
2012-04-22 12:01:30,720 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:30,847 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:30,847 DEBUG: fglrx_updates is not the alternative in use
2012-04-22 12:01:30,888 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-04-22 12:01:30,958 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-04-22 12:01:30,959 DEBUG: fglrx is not the alternative in use
2012-04-22 12:03:20,303 DEBUG: Shutting down
```

Any other quick fix suggestions, or is it on to scorched earth?

---

### Post by pmheideman on 2012-04-22
Just to double-check, actually the driver that software center says I have is broadcom-sta-source.  I can't seem to find bcmwl-source, and apt-get install says unable to locate package bcmwl-source.

---

### Post by pmheideman on 2012-04-22
Fixed it!  Reinstalled bcmwl-source-kernel-source in synaptic, restarted, and wifi started working great.  wahoo!

---

### Post by wildmanne39 on 2012-04-22
Hi, that is great sorry I did not get here sooner to help.

---

### Post by peppezic on 2012-07-27
Hi guys 
I made a fresh installation of ubuntu 12.04 64bit from CD (so it's not an upgrade), updated all the packages and now I'm running 3.2.0 kernel on my DV-7099 hp laptop. 
As you can understand the wifi card is a BCM4313 (14e4:4727).
I tried many of the solutions described on this (and other) thread but none of them really seems to work!

Here is the scenario:
After blacklisting the proper modules I can see and scan all the wireless networks surrounding me both with **wl** (bcmwl-kernel-source) or **bcrmsmac** drivers but I can't connect to none of them. I can see and associate with those access points but I don't obtain an IP address...
So the network manager tries many times until it fails...

Any help would be appreciated.
G.

---

### Post by iSWORD on 2012-09-22
Hmmmm... BUMP! I just bought a new HP laptop (HP Pavilion g6-1310), it has a BCM4313 adapter, and I'm **unable to boot** neither **Ubuntu 12.04** 64bit nor **Fedora 17** 64bit (well, I actually got F17 to work under basic graphics mode, but I couldn't use my WiFi adapter, plus it performs shittily in basic graphics mode)

I could run Ubuntu 10.04.4 32bit, but the drivers that Ubuntu automatically installed for my WiFi adapter were not enough (very weak signal + slow and "confused" connection).. I know there's a fix for 10.04 in this thread, but **I need to run either Fedora 17 or Ubuntu 12.04**, because Ubuntu 10.04 is quite not my type. (actually it'd be better if you give me a fix for F17, I'm a Fedora fan)..

Thanks in advance.

---

### Post by bellansy on 2012-10-11
Hi guys

I just bought a new computer, having a 4313 wifi module, and was nervous about doing all this steps. 
I use ubuntu 12.10 and I just had to install packet bcmwl-kernel-source and everything works !!

Hope it's a new packet from ubuntu team and that it will work for you also !

Bye

---

### Post by bellansy on 2013-03-03
Hi, for information, sorry for the previous message, I thought it works, but it did work only when "power wire" was plugged. When i unplugged it wifi was so slow that unusable.
When i noticed that, i searched on topic that did the link between wifi and power and found this topic to disable power management on wifi.
I can finnally use my laptop :)

[http://ubuntuforums.org/showthread.php?t=1615318&page=2&p=10193828#post10193828](http://ubuntuforums.org/showthread.php?t=1615318&page=2&p=10193828#post10193828)

---

### Post by 0n1m3 on 2013-03-04
First of all thanks you [**[COLOR=#000000]ts3[/COLOR]**]("http://ubuntuforums.org/member.php?u=1500872")  for this thread it became solution for my Broadcom 4313 wireless on  Lenovo B580, but for me there was few problems with comptilation  regarded to new kernel.

I use 3.5.0-17-generic.

The  problem is that compilation of bcmwl-kernel-source will fail because it  cannot find header file "asm/system.h", because compilation fails you  will not get wl.ko file in kernel modules directory and because of this  at time when you run ```
# modprobe wl
``` you will get message like  this ```
FATAL: Module wl not found.
```

to fix this you need to manually compile source bcmwl-kernel-source:

1) Open terminal become a superuser and go in directory which was created when you where trying to install bcmwl-kernel-source.

```
$ sudo su
# cd /usr/src/bcmwl-5.100.82.112+bdcom
```

note that you may have different version for sources so change name accordingly.

2) Open the file that fails to compile

```
# gedit  src/wl/sys/wl_linux.c
```

find the line with string "#include <asm/system.h>", it is located on ~43 line, remove this line.

then search for the string ```
.ndo_set_multicast_list
``` and replace it with ```
.ndo_set_rx_mode
```

save the file.

3) Now compile. Run make. This part is very easy for your fingers :P , but also very important.

```
# make
```

Now you should not get error message like: ....wl/sys/wl_linux.c:43:24: fatal error: asm/system.h: No such file or directory

4)  If everything where ok you should have wl.ko file in current directory  (/usr/src/bcmwl-5.100.82.112+bdcom) if so, run these commands.

```
# mkdir -p /lib/modules/$(uname -r)/extra/wl
# cp wl.ko /lib/modules/$(uname -r)/extra/wl
# depmod -a
# modprobe wl
```

5) after this check if all conflicting modules are blacklisted, (see original post).

6) Reboot, now you should have working WiFi :)


NOTE:  On first page of this thread you will find instructions on how to build  broadcom driver from scratch maybe you decide to follow it. It should  work same way.

Good luck.

---

### Post by andrespara on 2013-12-12
> **23senick said:**
> 

[FONT=Arial][SIZE=2]Then save the file.  Reboot, and then go into Ubuntu Software Centre again - search "bcm" and reinstall bcmwl-kernel-source and then broadcom-sta-source and broadcom-sta-common.[/SIZE][/FONT]

You may need to go into "System settings/additional drivers" and ensure the broadcom driver is enabled.

[FONT=Arial][SIZE=2]After this I rebooted and found wireless was at full strength[/SIZE][/FONT] :D


Hi I am a newbie here with the same problem when I tried to follow these instructions and went to additional drivers and enable the driver the screen turned all black with some text that stated "unable to write bytes" I had to turn it off and when I start again the driver was enabled but there's no connection. Thanks in advance for your help

---

