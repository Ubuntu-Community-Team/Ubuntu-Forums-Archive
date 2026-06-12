---
title: "Ralink RT2860 using ndiswrapper"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by revengeofthecow on 2009-03-03
Hello all,

I'm trying to get my wireless card to work in Ubuntu using ndiswrapper. It's an Encore ENLWI-N with the Ralink RT2860 chipset. They do provide drivers on their website (without the need for ndiswrapper), and I have successfully installed them before, but a) it's annoying and b) when I updated the kernel the wireless card stopped functioning. I have gotten the card to work before using ndiswrapper with the drivers listed on the ndiswrapper list, but the site's been dead since, I think, October of last year and I didn't save the files.

Is there another place I could download files that will work with this chipset in ndiswrapper? Would files for other chipsets work with my card? What do you suggest?

---

### Post by Crafty Kisses on 2009-03-03
Hey there! Let's try to get you that driver. I found a RT2860 driver, here is the [link.]("http://www.ralinktech.com.tw/data/drivers/IS_AP_STA_RT2870_D-1.0.3.0_VA-1.0.4.0_RU-2.0.2.0_VA-1.0.12.0_AU_1.1.9.0_060107_0.1.0.22.exe") It's a .exe though. It's not a problem all you have to do is right click on the .exe and select "Extract Here" then there should be a bunch of files, then find the .inf file. Then from there you can install the ndiswrapper. If you need help setting up the ndiswrapper let me know.

---

### Post by revengeofthecow on 2009-03-03
Got it! Thanks for your help. I actually did some googling and found a guy who was able to get HIS chipset working using some drivers from Gigabyte (Gigabyte product, same chipset). It's [here]("http://america.giga-byte.com/FileList/Driver/comm_driver_gigabyte_mimobility_v.1.3.1.0.15.zip"). It's just a .zip file, thankfully, so no need to extract stupid .exe files! I clicked through and found the files, including the .inf file, for the R2860 chipset (the R2870 was there also, but those do not work), pointed ndisgtk to it, and wireless immediately started working. Rock on.

---

### Post by NoobBiscUiT on 2009-03-28
I was able to get my Gigabyte gn-ws30n-rh working in ubuntu 8.1 by following the procedures here:[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/62622]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/62622")

It uses the same RaLink RT2860 driver.

---

### Post by acreda on 2009-03-29
just to let you know that you can get this working nativley with DKMS and the RT2860 package provided by this developer:-

[https://launchpad.net/~stgraber/+archive/ppa](https://launchpad.net/~stgraber/+archive/ppa)

For me, Ndiswrapper is always a last resort..........

---

### Post by NoobBiscUiT on 2009-03-30
I agree, 

although or some reason i can't connect to any networks at all, i can only see them?..

i followed the procedure in the link i provided in my previous post:....

[quote="mark"]

 Mark Rijckenberg said on 2009-03-01:

Hi,

Please try this installation procedure:

[https://bugs.launchpad.net/linux/+bug/210725/comments/152](https://bugs.launchpad.net/linux/+bug/210725/comments/152)

- Download rt2860-source_1.8.0.0-3_all.deb from [http://packages.debian.org/sid/all/rt2860-source/download](http://packages.debian.org/sid/all/rt2860-source/download)

wget [http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb](http://http.us.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb)

- install source .deb:

sudo dpkg -i rt2860-source_1.8.0.0-3_all.deb

- compile
sudo aptitude install debhelper module-assistant
sudo module-assistant auto-install rt2860

- install the module
sudo modprobe rt2860sta
this should activate the new wireless interface without reboot

- to load the module automatically on each reboot, add rt2860sta to /etc/modules

sudo gedit /etc/modules

- add the following line to the end of the /etc/modules file:
rt2860sta

- reboot and retest wireless

- if that does not work, you should consider upgrading to Jaunty (Ubuntu 9.04 alpha) Alpha 5, which should support your RT2860 wireless card out of the box.

Download location here:

[http://cdimage.ubuntu.com/releases/jaunty/alpha-5/jaunty-desktop-i386.iso](http://cdimage.ubuntu.com/releases/jaunty/alpha-5/jaunty-desktop-i386.iso)

Regards,

Mark
[/quote]

Can't connect to wireless networks..?

any ideas?

thanks

---

### Post by NoobBiscUiT on 2009-03-30
Also, sorry for hijacking this thread.
More info:

I have a wireless device in ifconfig, i am using Wicd for my network manager rather than gnome network manager. 

i can scan, set it to monitor mode (I think) and see other networks, but... it just hangs when i try to connect.

I was previously using a bcm4312, do i need to disable the driver for it or something?

thanks again,

---

