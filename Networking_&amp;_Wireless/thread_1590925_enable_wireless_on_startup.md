---
title: "enable wireless on startup"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by johnnytm on 2010-10-08
I have been having some problems with my wireless connection. I am having to start my computer 2 times in order for my wireless connection to work. The first time I start up, even after I enable wireless it wont connect. If I reboot immediately and enable wireless it will then connect. I would like to be able to fix this problem since it has become really annoying to me to have to boot my computer 2 times every time I turn it on. BTW Network manager shows auto-connect, however it also shows i month ago as to the last time the connections were used.

---

### Post by opasnost on 2011-02-05
> try placing;
nmcli nm wifi on
in /etc/rc.local using;
sudo nano /etc/rc.local
-make sure to add the line before exit 0 in the file.
-this will instruct network manager to enable wifi on every login
-solved issue on Acer Aspire One 721, Ubuntu 10.10 x64

(looks like ([http://ubuntuforums.org/showthread.php?t=1563463](http://ubuntuforums.org/showthread.php?t=1563463)) nmcli is  only available in 10.10, I'd imagine you could accomplish the same thing  using dbus-send in other versions)

I am also using an Aspire one and it worked for me

got this from [http://ubuntuforums.org/archive/index.php/t-1471456.html](http://ubuntuforums.org/archive/index.php/t-1471456.html)

---

### Post by loskiorama on 2011-05-26
Worked for me! on a hp pavillion with a wireless usb adapter

thanks a lot!!
greetings from uruguay

---

