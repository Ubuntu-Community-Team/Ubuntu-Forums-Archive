---
title: "laptop won't connect to internet"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by Cinnamonbun23 on 2012-10-30
My Toshiba Satellite C855-S5214 is dual booted with windows 7 and ubuntu 12.04. I can connect to internet either by wifi or wired in windows 7 but whenever i boot up ubuntu i can connect to internet for about 2 to 5 minutes before it disconnects and once it disconnects it never reconnects and just keeps asking me for my security key. I've tried to connect wired but it won't work that way either but I'm more concerned with the wifi connection right now. I did do some commands in the terminal such as sudo, lshw, lspci, lsusb, lsmod since somebody told me to do that but i have no idea what is means so I'll add the pictures just in case somebody can help me.

Thanks in advance

---

### Post by Cinnamonbun23 on 2012-10-30
here's some more of the terminal code results

---

### Post by Cinnamonbun23 on 2012-10-30
this is  the lsmod results

---

### Post by Cabalbl4 on 2012-10-30
I remember some issues with the wireless on my toshiba satellite A210P. They were resolved by installing new drivers for wireles. Try some compat-wireless backports from package manager or download tarball from here: [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) (be sure to get one with the same number as your kernel, as shown by ```
uname -a 
``` command.

---

### Post by Cinnamonbun23 on 2012-10-30
I got my kernel version which was 3.2.0-29-generic and i found my version in the website you provided but whenever i click my version it won't download for some reason.

---

### Post by Cabalbl4 on 2012-11-06
Try backports from package manager.

---

### Post by Cinnamonbun23 on 2012-11-07
I downloaded the compact wireless thing the website was just down. But I have no idea as to how I'm supposed to install it to ubuntu so if i could get some step by step instructions on how to install I would really appreciate it. Thanks

---

### Post by alkh3myst on 2012-11-08
Cinnamonbun23, get rid of that filthy tarball, and just install: "linux-backports-modules-cw-" from Synaptic. That package contains compat-wireless. Easy enough? Now, let me go get you some paint thinner to get that tarball off your hands.

:)

---

### Post by Cinnamonbun23 on 2012-12-06
I couldn't get the wireless working so i uninstalled ubuntu 12.04 and installed ubuntu 12.10 and I am writing you on ubuntu and not windows finally.

Thanks for all your help

---

