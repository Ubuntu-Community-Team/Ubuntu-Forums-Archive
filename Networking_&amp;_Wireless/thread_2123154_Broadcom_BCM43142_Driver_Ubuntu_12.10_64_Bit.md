---
title: "Broadcom BCM43142 Driver Ubuntu 12.10 64 Bit"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by kanishkdudeja on 2013-03-07
I got to know that broadcom doesnt provide linux drivers for my wireless card.

I searched various ubuntu forums and everybody gave me one single solution to get the drivers working for ubuntu 12.10 64 Bit.

The setps are:

download this file: [http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb](http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)

sudo apt-get install linux-headers-generic build-essential dkms

navigate to the folder you have saved the downloaded file and run this command.

sudo dpkg -i wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb

sudo modprobe wl

Now when i do all these steps on a live cd run, without actually installing ubuntu, they seem to work. my wireless connection gets detected.

But on a normal install, i am greeted the following error when i run this command "sudo dpkg -i wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb"

Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

And then when i run the command, sudo modprobe wl:

It says : FATAL: Module wl not found.

How can i make it run?

---

### Post by kc1di on 2013-03-07
go to the terminal and install the kernel source like this
```
 sudo apt-get update
 sudp apt-get install linux-source
```

---

### Post by chili555 on 2013-03-07
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.This is result when you forgot to do:```
sudo apt-get install [COLOR="#FF0000"]linux-headers-generic[/COLOR] build-essential dkms
```...or if the headers didn't get installed correctly. I'd try:```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Then try again:```
sudo dpkg -i wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb
```If there is another error, which i doubt, post it and we'll fix it.

---

### Post by kanishkdudeja on 2013-03-07
It worked. Thank you so much :)

---

### Post by chili555 on 2013-03-07
> **kanishkdudeja said:**
> It worked. Thank you so much :)Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by kanishkdudeja on 2013-03-07
Yes i tried that. It doesnt show that option. Under the option 'Thread Tools' it only shows three options 'show printable version', 'email this thread' and 'subscribe to this thread'

---

### Post by chili555 on 2013-03-07
> **kanishkdudeja said:**
> Yes i tried that. It doesnt show that option. Under the option 'Thread Tools' it only shows three options 'show printable version', 'email this thread' and 'subscribe to this thread'I'll ask a moderator. Thanks.

---

### Post by coffeecat on 2013-03-07
How to mark as solved:

[http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730)

---

### Post by chili555 on 2013-03-07
> **coffeecat said:**
> How to mark as solved:

[http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730)Thank you, Mr. Cat!

---

### Post by kanishkdudeja on 2013-03-07
marked as solved. :)

---

### Post by Sashank on 2013-04-09
hey!

thanks a lot. i had the exact same problem with my new DEll bostro 2520 laptop. 

the wireless drivers work perfectly with windows 8 but on ubuntu 12.10 they didnt even show up. 

i tried the above  mentioned and it worked! 

thanks a lot.

cheers!

---

