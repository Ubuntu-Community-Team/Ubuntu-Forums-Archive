---
title: "almost got my d-link to work"
date: 2006-01-01
forum: Networking &amp; Wireless
---

### Post by grman3 on 2006-01-01
ok so i tried to get my d-link dwl-g122 usb card to work a long time ago got fedup with it and sad to sa it went back to windows. for sum unknown reason i cant get my laptop to play video with windows. i'm now with kubuntu and almost go the card to work with ndiswrapper. i can get all the way to load the module into the running kernel then i get.

"fatal: error inserting ndiswrapper (/lib/modules/2.6.19-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): operation not permitted"

i'm still very new to this so any help will be apreshiated 

i'm using ndiswrapper1.1 the one that came with kubunut

~jonathan

---

### Post by Jeff12088 on 2006-01-01
What command did you type?

In the wiki ([https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards))
basic information is provided for that model. ;)

---

### Post by grman3 on 2006-01-01
i used this link to get it set up ([https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto))  i did not do the first step of compiling from the source because i installed the one that came with kubuntu. the command i used was "modprobe ndiswrapper" then i get the error. 

thanks
~jonathan

---

### Post by EEPS on 2006-01-01
did you forget to sudo that? You need to be root to load kernel modules.

---

### Post by grman3 on 2006-01-01
i did do sudo. i also did "ndiswrapper -l" to see if the drivers were loaded and it said they were invalade but i think that is due to the error im getting  with he modules.

~jonathan

---

### Post by grman3 on 2006-01-02
any one know what im doing wrong

~jonathan

---

### Post by Lambert on 2006-01-02
Going off memory, I remember seeing quite a few posts about this device and problems.

I can't speak for ndiswrapper but what I would suggest is trying the native linux driver to see if you can get it working.

Here is a link to a how to. Make sure you remove the the driver from ndiswrapper before this and ndiswrapper doesn't load

sudo ndiswrapper -e __________ 
(removes driver)
sudo modprobe -r ndiswrapper
(unloads ndiswrapper as a module)

[http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)

---

### Post by grman3 on 2006-01-03
I gave ndiswrapper one more try. this time i installed 1.7. when i go to load the drivers i typ " ndiswrapper -i -/home/jon/prisma02.inf " it starts to load them then i get" installing prisma02 could not copy -hime/jon/prisma02.inf at /usr/sbin/ndiswrapper line 131" 

If any one knows how to fix that i think that might sove my problem.

~jonathan

---

### Post by grman3 on 2006-01-06
any one have any ideas on this.

~jonathan

---

