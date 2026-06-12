---
title: "Netgear Wn111v2 adapter"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by mafustokes on 2009-03-21
Hello, after installling ubuntu I'm having problems getting my wireless usb adapter to work. I have an HP pavillion laptop, a netgear wnr2000 router and the aforementioned usb adapter(netgear wn111v2) - both the wireless n type. I already had them working in xp.
I have tried various solutions from threads on here and on the net - some which appear to have worked don't seem to work for me. Not sure if it's because my adapter is the v2 version - others seem to have the normal wn111. I have read the post regarding how to raise a ticket and this is the most info I can give at the minute. I'm pretty new to ubuntu and don't know what to do next.

---

### Post by mafustokes on 2009-03-21
Oh and I forgot to say - the problem is that ubuntu doesn't seem to recognise the device at all. I can connect to the router fine using a wired connection. I have tried a couple of suggestions but am unsure what to try next.

---

### Post by morloch on 2009-03-22
I have the same USB device and managed to get it working using the method detailed here:

[http://ubuntuforums.org/showthread.php?t=885520]("http://ubuntuforums.org/showthread.php?t=885520")

The drivers supplied by bean1975 worked a treat :)

---

### Post by mafustokes on 2009-03-22
Thanks for the reply. I will give it a go. Do you think I should uninstall the n-wrapper util and start again - I also tried a different driver - the one that comes on the xp install cd - should I remove that?
In the meantime I will have a look at the thread you linked and see how I get on. Thanks again.

---

### Post by cdproject on 2009-04-29
Thanks I also used the drivers supplied by bean1975 and connected a treat with my Netgear WN111v2 :):P

---

### Post by Habboblob on 2009-05-18
I've done everything and used the driver from Bean and everything is going well. But my 1 problem is, when I connect to my NetGear Wireless-N Router WNR2000 my Ubuntu, which is version 9.04, connects but stays on one of the green dots, and after five minutes ask for the wireless password. I have my wireless connection on auto and these password is 100% correct. I will upload a picture of it asking for Authentication in my next post as I am not at home.

---

### Post by john stiles on 2009-07-29
Probably to late now but I have a working WN111 v2 on Jaunty. Since this is my top Google I'll detail:

There is a native ar9170 linux driver ref:

[http://forum.ubuntuusers.de/topic/ne.../#post-1874262](http://forum.ubuntuusers.de/topic/ne.../#post-1874262) (German!)

In summary:

# remove ndiswrapper

sudo rm -r /etc/ndiswrapper/*
sudo modprobe -rf ndiswrapper

# download and install compat-wireless with driver/modules

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential
wget [http://elektronenblitz63.de/download..._230209.tar.gz](http://elektronenblitz63.de/download..._230209.tar.gz)
md5sum Compat-Wireless_ar9170_230209.tar.gz

tar xvf Compat-Wireless_ar9170_230209.tar.gz
cd compat-wireless-2009-02-22_AR9170_230209

make
sudo make uninstall
sudo make install

# move firmware/module to correct location

sudo cp ar9170-*.fw /lib/firmware

# Reboot. Jaunty automatically adds to network manager applet.

NB. I have backports installed as well but am unsure if this is necessary for the above.

Alternatively, go to the official Linux wireless page for the ar9170 module, and certainly good information:

[http://wireless.kernel.org/en/users/Drivers/ar9170](http://wireless.kernel.org/en/users/Drivers/ar9170)

I have not used this last method but it seems to involve installing git for the firmware/module and probably still needs compat-wireless.

---

### Post by BlackHecilopter on 2009-08-20
Hi guys, anyone know what driver versions you're running?  I've got the files for driver version 3.0.0.131 from Microsoft Support in a .RAR file.  There are a couple extra files provided in this .RAR file compared to the WNDA3100 file provided on one of the links above.  If anyone cares for them they're down below.  Just a couple side notes - I'm currently using driver version 3.0.0.141 provided from Netgear on my Windows computer and the driver upgrade seems to give a little boost in performance but maybe it's just me.  I've looked around but couldn't find one that wasn't just a plain old windows setup file, so I'm out of luck for now.  Any who, I am going to try the new files out as I'm switching over to Ubuntu on my laptop.   Ill let you guys know how they work.

---

### Post by decora on 2009-08-22
I wanted to say thank you to John Stiles and morloch and excogitation and flash63 and to elektronenblitz63 over on the german pages and many others. I was able to get a wn111v2 working on ubuntu 9.04 on a machine with no other internet access. I did not use ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=1150835](http://ubuntuforums.org/showthread.php?t=1150835)

[http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262](http://forum.ubuntuusers.de/topic/netgear-wlan-usb-stick-wn111v2-mit-atheros-ch/3/#post-1874262)

I am sorry that I don't have access to any ubuntu machines right now, or a wn111v2 so I cannot remember exactly what I did, nor test which parts are necessary and unnecessary. 

First i tried kernel 2.6.30 (from PPA) by itself. I used a working ubuntu internet machine to download .deb package files, transfer with a usb disk, and then used dpkg -i to install those .deb's. Upgrading to kernel 2.6.30 and installing firmware, by itself, didnt work. 

I also tried using linux-backport-modules by itself + firmware, but this didn't work either. (I got this package by using apt-get install --download, again transferring via usb disk and using dpkg -i)

Then I tried the special compat-wireless tarball from flash63. This didnt compile at first. I had transferred over some linux-header packages, though, for some reason I cant remember (was it a dependency of build-essential? or linux-backport-modules?). I dpkg -i on those linux-header .debs, and then special compat-wireless compiled. 

Then i followed the rest of the instructions listed by others already, and rebooted, and it worked fine.

I dont remember what version of the kernel I ended up with. It was not the 2.6.30. 

Thank you.

---

### Post by spamless on 2009-09-27
[COLOR=Blue]I'm leaving the below here as it was for 8 weeks, but meanwhile I am using Karmic Koala and have out-of-the-box support for the WN111v2.
[/COLOR]
> **BlackHecilopter said:**
> Hi guys, anyone know what driver versions you're running?  I've got the files for driver version 3.0.0.131 from Microsoft Support in a .RAR file.  There are a couple extra files provided in this .RAR file compared to the WNDA3100 file provided on one of the links above.  If anyone cares for them they're down below.  Just a couple side notes - I'm currently using driver version 3.0.0.141 provided from Netgear on my Windows computer and the driver upgrade seems to give a little boost in performance but maybe it's just me.  I've looked around but couldn't find one that wasn't just a plain old windows setup file, so I'm out of luck for now.  Any who, I am going to try the new files out as I'm switching over to Ubuntu on my laptop.   Ill let you guys know how they work.

Thanks, I grabbed that file, but what do I do with it? I can speak German, and I have been reading the German thread cited above, but so far I'm still stuck.  I have 9.04 running with AM2 64-bit architechture.  I also have a Windows 7 installation and use the latest Netgear driver there with no problem, as you say above you do as well.

When I get to the step "sudo make install" I get into an endless loop of this:
[INDENT] Running athenable ath5k...
  Disabling ath_pci ...mv: cannot stat `volatile/ath_pci.ko': No such file or directory
[ERROR]       Module is still being detected:
  volatile/ath_pci.ko
  Disabling ath_pci ...mv: cannot stat `volatile/ath_pci.ko': No such file or directory
  [ERROR]       Module is still being detected:
  volatile/ath_pci.ko
[/INDENT]The German thread has someone saying the same thing, and the original poster says thereafter it's not a problem, because the needed install was completed by then.  So I tried the next step -- "sudo cp ar9170-*.fw /lib/firmware" -- [COLOR=Sienna]but there is no such file.  Can anybody help?[COLOR=Black]

[I've edited this and colored the above because I now have things working.  If I knew how to use a strike-through font I would have done that.  The problem was that the two files to copy are in the parent dir above where we were running "make install".  Nobody bothered to mention that part.  And here I was using find and all sorts of things trying to locate those files in subdirs.]

Per t[/COLOR][/COLOR]he German pages referenced I added a line:[INDENT][FONT=Courier New][COLOR=Blue]echo 'options cfg80211 ieee80211_regdom="EU"' | sudo tee -a /etc/modprobe.d/cfg80211 [/COLOR][/FONT]
[/INDENT](all on one line), as I live in Germany.  Anyway, I rebooted and the stick works!

I still would like to know about the newer drivers the OP mentioned in the article I'm replying to.

---

### Post by rcastoro1 on 2009-11-26
Ubuntu 9.10 Supports the Wn111v2 netgear wireless adapter right out of the Box! Great! I was able to get a internet connection as soon as I installed Ubuntu Karmic Koala and plugged in the usb adapter. Happy Browsing!

---

### Post by spamless on 2009-11-26
> **rcastoro1 said:**
> Ubuntu 9.10 Supports the Wn111v2 netgear wireless adapter right out of the Box! Great! I was able to get a internet connection as soon as I installed Ubuntu Karmic Koala and plugged in the usb adapter. Happy Browsing!

Yup, I'm in Karmic too and found that out.  Thanks.  I had lots of trouble with Sun's VirtualBox in Karmic, though.  I have finally, after a week of trying all sorts of things, got that working right again.  Some people said to use the RT kernel, but that didn't solve it for me.  Today I ugraded my kernel to -15 and it seems better still, though that's subjective.

---

### Post by karlsoost on 2009-12-27
> **spamless said:**
> Yup, I'm in Karmic too and found that out.  Thanks.  I had lots of trouble with Sun's VirtualBox in Karmic, though.  I have finally, after a week of trying all sorts of things, got that working right again.  Some people said to use the RT kernel, but that didn't solve it for me.  Today I ugraded my kernel to -15 and it seems better still, though that's subjective.

Hi spamless,

did you manage to run this device in bridged mode in virtualbox as well?
This ability would be highest interesting for me.

Regards, KarlSoost

---

### Post by spamless on 2009-12-27
> **karlsoost said:**
> Hi spamless,

did you manage to run this device in bridged mode in virtualbox as well?
This ability would be highest interesting for me.

Regards, KarlSoost

Karl,

I believe I did, but at the moment my VB is disabled so I can't check for sure.  But everything that I tried with networking ultimately worked in the VB.

---

