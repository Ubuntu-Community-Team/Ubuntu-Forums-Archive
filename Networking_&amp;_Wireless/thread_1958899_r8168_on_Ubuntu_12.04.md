---
title: "r8168 on Ubuntu 12.04"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by matera.ttp on 2012-04-15
The old switchmod does not work in 12.04.

Here is updated version: [https://gist.github.com/2390823](https://gist.github.com/2390823)

Or just tar on my dropbox: [http://dl.dropbox.com/u/1901109/r8168_switchmod12.04.tar.gz](http://dl.dropbox.com/u/1901109/r8168_switchmod12.04.tar.gz) including drivers r8168-8.028 that works fine for me.

Steps:
1. Download [http://dl.dropbox.com/u/1901109/r8168_switchmod12.04.tar.gz](http://dl.dropbox.com/u/1901109/r8168_switchmod12.04.tar.gz)
2. tar -xzf r8168_switchmod12.04.tar.gz
3. cd r8168_switchmod12.04
4. sudo ./switchmods12.04

List of available drivers: [http://code.google.com/p/r8168/downloads/list](http://code.google.com/p/r8168/downloads/list)

---

### Post by underkz on 2012-04-30
nice one ! A big thank's to you for this amazing script.

I would like to add that the driver, even if it's the incorrect one by default (r8169 instead of r8168 ), is functioning better than when I was on 11.10 (I'm not loosing the connection randomly with this one)

I'm wondering if its the case for others people?

Edit: After using the script with r8168-8.029, all is working great :)

---

### Post by Daniel15 on 2012-05-05
Thanks for this, seems to work perfectly :)

---

### Post by praseodym on 2012-05-05
Hi,

you can also install this driver via dkms:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/44/18/3005217-r8168-dkms-8.029.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.029.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.029.00
sudo dkms build -m r8168-dkms -v 8.029.00
sudo dkms install -m r8168-dkms -v 8.029.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168 
```
From here:
[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

You should install the metapackage **linux-headers-generic** or **linux-headers-generic-pae** (or whatever kernel-architecture is in use) for that. Otherwise the driver r8169 occurs again with the new kernel image.

---

### Post by markseddon on 2012-06-10
Excellent!

Much appreciated, it's always a hassle to upgrade and have no internet connection.

Thanks once again.

Mark.

---

### Post by praseodym on 2012-06-10
New driver version 31 available. I updated the link

---

### Post by Yudley on 2012-08-20
If you wanna go the dkms route (setup once ... automatically installed on every kernel upgrade) with the latest release (8.032.00 as of right now) follow the dkms steps (subsection with the title "Update &#8211; 2/22/2011"):

[http://djlab.com/2010/10/fixing-rtl8111-8168b-driver-debian-ubuntu/](http://djlab.com/2010/10/fixing-rtl8111-8168b-driver-debian-ubuntu/)

but with two changes in dkms.conf:

1 - change the r8168 version strings (to your r8168 version)

2 - change third line from:

```
MAKE[0]="make"
```

to

```
MAKE[0]="'make'"
```

I had to go thru quite a bit of trouble without this 2nd change cz dkms build would keep failing with the error message "No rule to make target `clean'" whatever ...

I have done this procedure myself but haven't tested it yet (need to wait for next kernel upgrade)

---

### Post by andres jurado on 2013-01-30
thank you sooooo much for your script it worked wonders after 6 hours trying to get decent internet on my brand new PC.

---

### Post by paperring on 2013-02-09
I installed this driver with dkms,how can I uninstall this driver safely?

---

### Post by praseodym on 2013-02-10
```
sudo modprobe -rfv r8168
sudo dkms remove -m r8168-dkms -v 8.035.00 --all 
sudo depmod -a
sudo update-initramfs -u
```
will uninstall it. Adjust the version number.

---

### Post by paperring on 2013-02-10
This step:
```
sudo dkms remove -m r8168-dkms -v 8.035.00 --all 
```
is giving
```
Error! There are no instances of module: r8168-dkms 
8.035.00 located in the DKMS tree.
```
error, so what should I do?

Thats okay, I change the version to correct one and it works, thanks for help...

---

### Post by chrisbeeley on 2013-05-26
Dude, you rock! A billion thank yous, so much frustration removed from my evening.

If I ever learn to do anything useful, you can ask me to help you with it any time.

---

