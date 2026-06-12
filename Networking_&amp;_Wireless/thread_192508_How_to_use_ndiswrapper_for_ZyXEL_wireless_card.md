---
title: "How to use ndiswrapper for ZyXEL wireless card"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by endokrin on 2006-06-08
I can't get the driver installed!

This is for 64 bit.

Here is what I have and what I've done..
ZyXEL G-302 (Texas Instruments ACX 111 chip) wireless PCI card

Went [here](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper) and followed instructions and went here [sourceforge ndiswrapper list](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#Y)

Downloaded the .zip file for the Zyxel G-162 card which has the TI ACX 111 just as my G-302.

Extract the driver files into  ~/drivers

It has: FwRad16.bin, FwRad17.bin, tnet1130.sys, tnet1130x.sys and TNET1130.inf

then:
```

sudo ndiswrapper -i ~/drivers/tnet1130.inf
Installing tnet1130.inf
couldn't copy ~/drivers/tnet1130.inf at /usr/sbin/ndiswrapper line 135.

```
Ok, guess it didn't work.

```

sudo ndiswrapper -l
Installed ndis drivers:
tnet1130   invalid driver!

```

I'd like some help installing the driver for my wireless card using ndiswrapper.

Thanks!!!!

Found this on the ndiswrapper list site, can someone explain??:

Other: Ubuntu 6.06, kernel 2.6.15-23-386, ndiswrapper 1.8. **Make sure you remove acx Kernel module as this conflicts and does not work.** Next Ubuntu release with latest acx Kernel module will probably work

---

### Post by endokrin on 2006-06-09
bump... anyone?..please?

---

### Post by endokrin on 2006-06-12
Anyone got any ideas?

---

### Post by endokrin on 2006-06-12
I deleted the acx driver which I found was included with the distro but is not the correct driver.
Even after deleting the acx driver, I get the same error message:

```

sudo ndiswrapper -i ~/drivers/tnet1130.inf
Installing tnet1130.inf
couldn't copy ~/drivers/tnet1130.inf at /usr/sbin/ndiswrapper line 135.

```

Help.

---

### Post by noname101 on 2006-06-12
try 
```
sudo ndiswrapper -i ~/drivers/TNET1130.inf
```
Linux is case sensitive.

---

### Post by endokrin on 2006-06-12
shutup!

Stop making me look like an idiot... wait, that's just me ;) 

Ok, I did this and it installed the driver, driver & hardware present

I also did the modprobe and ndiswrapper -m thing.
```

sudo ndiswrapper -m
modprobe config already contains alias directive

```

Now, when I go to System->Administration->Networking, the wireless card (wlan0) doesn't show up.  Before installing the driver, wlan0 was visible.

I tried lspci and it shows up.

---

### Post by noname101 on 2006-06-13
Now do the following:
```
sudo modprobe ndiswrapper
```
Now edit /etc/modules and put ndiswrapper at the bottom. So that when you reboot it'll load the module.
```
sudo gedit /etc/modules
```

---

### Post by tzcomwiz on 2006-06-13
If wlan0 was visible before you isntalled ndiswrapper, then that means there's another wireless driver already present (but may not work properly). You must first remove that driver and maybe a few more things. So you'll probably have to do some research and find out what the Linux drivers for your card are. I had to execute:
> rmmod islsm && rmmod ieee80211_crypt
Also all the dependencies. Mine was a Prism Intersil card.

Then modprobe ndiswrapper and everything should work fine.

---

### Post by endokrin on 2006-06-13
Hi,

Well I think I made some headway, but the thing still won't work.
I found that the driver included with the card's CD and the driver available for download on the manufacturer's website is not compatible with 64 bit.

I went to this website: [http://acx100.sourceforge.net](http://acx100.sourceforge.net)
They specialize in fixing ACX 100 and ACX 111 drivers.  I have seen some posts that say their driver is compatible with 64 bit, so I gave it a try.  I went to their [wiki](http://acx100.sourceforge.net/wiki/ACX) and followed the directions.

I did the following per the wiki:
```

cd /usr/src
mkdir acx-20060512

```

```

cd acx-20060215
wget http://acx100.erley.org/acx-20060512.tar.bz2
tar xjvf acx-20060512.tar.bz2

```

Now here's where I run into a problem:

```
user@user-desktop:/usr/src/acx-20060512$ sudo make -C /lib/modules/`uname -r`/build M=`pwd` 
make: Entering directory `/lib/modules/2.6.15-23-amd64-generic/build' 
**make: *** No targets specified and no makefile found. Stop. **
make: Leaving directory `/lib/modules/2.6.15-23-amd64-generic/build' 

```

I thought maybe there is a space between **modules/** and **`uname**
```
user@user-desktop:/usr/src/acx-20060512$ sudo make -C /lib/**modules/ `uname** -r`/build M=`pwd` 
make: Entering directory `/lib/modules/2.6.15-23-amd64-generic/build' 
**make: Nothing to be done for '2.6.15-23-amd64-generic/build'.** 
make: Leaving directory `/lib/modules/2.6.15-23-amd64-generic/build' 

```


I installed build-essential in order to us make..
but I get that no target/no makefile found error...

Any suggestions or am I so completely lost I should just blow up the computer now and be done with it?!?!

---

### Post by noname101 on 2006-06-13
The make -C command should look like the following:
> sudo make -C /lib/modules/2.6.15-23-amd64-generic/build M=/path/to/acx
If that doesn't work try [this]("http://vanvalkinburgh.org/howtos.php?itemid=25866&catid=8") how to. Though using that driver may brake your card. So I would find a 64 bit version of a Texas Instruments ACX 111 windows driver.

---

### Post by endokrin on 2006-06-13
the make command I used was mentioned in the wiki.. it said it was the equivalent of the make command you mentioned.

I tried the command the way you mentioned it and
```

make: *** No targets specified and no makefile found. Stop. 

```


I'll look at the page you mentioned..

The quest goes on!

---

### Post by endokrin on 2006-06-14
I found [this](http://www.planetamd64.com/lofiversion/index.php/t12798.html) discussion which mentioned [64 bit Atheros drivers on the gigabyte website](http://america.giga-byte.com/Communication/FileList/Driver/64bit_wlan42052bin.zip)
I downloaded, unzipped, and installed using ndiswrapper, did a modprobe, and added ndiswrapper to /etc/modules, rebooted and no luck.

My wlan0 still won't show up.

lsmod | grep ndiswrapper shows two entries:
ndiswrapper & usbcore


lspci lists the card
lspci -n lists it
lspci -v lists it and shows it is assigned an IRQ

---

### Post by noname101 on 2006-06-14
Did you do this:
Replace the kernel version with the version your using.
```

apt-get install linux-source-2.6.12 
cd /usr/src
sudo tar xvjf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
sudo ln -s /usr/src/linux /lib/modules/2.6.12-10-k7/build
cd linux
sudo make oldconfig
sudo make include/linux/version.h
sudo make modules
cd ../
```

---

### Post by jyap on 2006-09-16
> **endokrin said:**
> I can't get the driver installed!

This is for 64 bit.

Here is what I have and what I've done..
ZyXEL G-302 (Texas Instruments ACX 111 chip) wireless PCI card

<SNIP>

Found this on the ndiswrapper list site, can someone explain??:

Other: Ubuntu 6.06, kernel 2.6.15-23-386, ndiswrapper 1.8. **Make sure you remove acx Kernel module as this conflicts and does not work.** Next Ubuntu release with latest acx Kernel module will probably work

Endokrin,

I have the site which has that post.

The full instructions I have are here:
[Getting the Zyxel ZyAir G-302v2 802.11bg wireless card to work on Ubuntu 6.06]("http://www.julianyap.com/wiki/Getting_the_Zyxel_ZyAir_G-302v2_802.11bg_wireless_card_to_work_on_Ubuntu_6.06")

I wasn't able to get the card to work with any other kernel other than the standard 386 kernel.  I have a P4 chip for this particular computer so no 686 kernel for me :P.

Try using the stock 386 kernel.  Also use the drivers on the supplied CDs.  I don't think I found the drivers on the web anywhere.

~ Julian

---

