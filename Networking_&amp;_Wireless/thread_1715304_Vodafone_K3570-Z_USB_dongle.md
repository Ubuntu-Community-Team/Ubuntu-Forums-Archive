---
title: "Vodafone K3570-Z USB dongle"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by malel on 2011-03-26
I am in a real spot here now. I have just installed Ubuntu 10.10 on my machine dual booting with Windows XP . My problem is that Ubuntu will recognise my internet provider but will not action the Vodafone USB mobile stick that I have to use . Consequently any internet work I have to do is via Windows. All the instructions that I have read about this seems to have an download component in it but I am unable to download as I cannot use the Vodafone stick in Ubuntu. Of course it operates okay in Windows. I have visited the Betavine website but it seems that they have not been able to overcome this problem . Is there some one out there that can help me so that I can revert to using my favourite OS (Ubuntu).




My system:
Pentium 4
80 Gb HDD
1 GB RAM
Nvidia graphics card

---

### Post by malel on 2011-03-30
I have been trying to have my Vodafone USB dongle recognised by the various distributions and this is what has happened to me.
I tried Ubuntu 8.10, 9.10 and 10.04 to no avail. Also tried Fedora 11 still no recognition. However tried Fedora 14 Live and hey presto it works. The only thing is that I have to fiddle with it a few times before it actually starts up but hey it is working. 
I tried Betavine but even though I signed up and was told that they were forwarding  me a password via email I have not heard a thing from them . That was three days ago. Usually a reply comes back right away.
One thing I found very frustrating with the other distro's was that all the info I was reading was telling me to download this that and the other thing but as I was not able to connect to the internet it was impossible for me to download anything. I wonder if anyone else had the same sort of happening as myself.

---

### Post by patryk77 on 2011-03-31
Hey!

You can download the Ubuntu .deb packages [online](http://packages.ubuntu.com/maverick/).

This allows you to download them on another computer (or in Windows) and then transferring them over.

What fixed my woes was USB mode-switch
[http://packages.ubuntu.com/maverick/usb-modeswitch](http://packages.ubuntu.com/maverick/usb-modeswitch)
[http://packages.ubuntu.com/maverick/usb-modeswitch-data](http://packages.ubuntu.com/maverick/usb-modeswitch-data)
(remember the dependencies as well)

Once you download the packages, you can install them with:
sudo dpkg -i *

You may also have to [disable automount/autorun](http://glog.procrasstination.com/index.php?/archives/18-HowTo-Prevent-Ubuntu-from-mounting-3G-modem-as-CD-ROM.html); at least I did.

Also, I noticed with my 3G modem, it worked as long as I booted the laptop with the modem plugged in, so you can give that a try and maybe you can install it using apt-get.

---

### Post by dineshs on 2011-03-31
Did you try [ this]("http://ubuntuforums.org/showthread.php?t=1600325") (sakis3G)?

---

