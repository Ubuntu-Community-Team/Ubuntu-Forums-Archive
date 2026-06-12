---
title: "No Ethernet 10.04 - Atheros"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by glethro on 2012-06-05
I have no ethernet connection on ubuntu 10.04. 

The NIC is built into the motherboard which is a Gigabyte GA-Z77-D3H

The card shows up in windows 7 as an atheros 8151 card. I searched around and found this thread: [http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231) but that did not seem to work.

uname -r
```
2.6.32-40-generic
```
sudo lshw -C network
```
 *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f6200000-f623ffff ioport:d000(size=128)
```
lspci -nn | grep 0200
```
05:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
```

---

### Post by glethro on 2012-06-06
bump

---

### Post by glethro on 2012-06-14
Well its been over a week now and its still not working....

---

### Post by wildmanne39 on 2012-06-14
Hi, the driver is not included in 10.04 for that device, I recommend you install 12.04.
Thanks

---

### Post by glethro on 2012-06-14
I can't do that till I've got internet on that one. Is there a way to get the driver working with 10.04?

---

### Post by wildmanne39 on 2012-06-15
Hi, do you have wireless working in 10.04?

You could use someone else's computer to download ubuntu and create a livecd or liveusb.
Thanks

---

### Post by glethro on 2012-06-16
Its a desktop with no wireless card

Instead on my Windows partition I've made a 12.04 live USB. This does have an internet connection. Do you know what I need to add to 10.04 to get the same functionality?

---

### Post by wildmanne39 on 2012-06-16
Hi, a couple of months ago I tried to help someone that did not have internet to setup this same card, I spent hours getting the directions with google and it still failed, the only thing that I can recommend is use a cell phone to get a tethered connection or borrow a usb adaptor or install 12.04 as I recommended in the beginning which is still the best choice.
Thanks

---

### Post by t0llphree on 2012-06-16
Aloha,  Hang in there!  I am running into this same issue with my laptop.  Already found a fix for my wireless card now I just have to figure out the Ethernet NIC.  Please post any information if you happen to find a fix.  I will do the same.

---

### Post by t0llphree on 2012-06-16
Aloha glethro,
We're in LUCK!  Well at least I am in luck.  This is where I went:
([http://askubuntu.com/questions/127151/ethernet-conection-not-working-atheros-ar8152-os-12-04](http://askubuntu.com/questions/127151/ethernet-conection-not-working-atheros-ar8152-os-12-04))

Look at darin's response.

    Go to linuxwireless.org/download/compat-wireless-2.6/
    Download the most recent ( mine was "compat-wireless-3.5-rc2-2-n" at the time of download)

Then do:

sudo apt-get update
sudo apt-get install build-essential
cd ~/Downloads # [or wherever you download it to]
sudo su
tar-xjvf compat-wireless-3.5-rc2-2-n [or whatever version you downloaded]
cd compat-wireless-3.5-rc2-2-n [or whatever your untarred folder is named(type "ls" if you are unsure - the folder name should be in blue)]
scripts/driver-select atl1c
make
make install

Then just reboot.



Good Luck!!!  Hope you didn't give up and just upgrade...it defeats the purpose of learning!  Have fun and a great day!  Please post questions!

---

### Post by wildmanne39 on 2012-06-16
Hi t0llphree, the problem is that the poster does not have any internet access, can you tell him how to make it all work without internet at all?

It is very hard because of the dependences that need to be install to compile the driver.

Thanks!!! you have done a great job, and I did know how he could get the driver just not without internet.

---

### Post by t0llphree on 2012-06-16
Aloha Wild,
My apologies and thanks.  I simply saw this in glethro's post:

"*-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications"

I was having the exact same issue. The fix I came across was a big help.  Thought I'd share it. 

glethro, if the case is no internet access - I'm sorry...can't help you there buddy.  =)

Have a great day everyone!!!

---

### Post by glethro on 2012-06-16
> **t0llphree said:**
> sudo apt-get update
sudo apt-get install build-essential
cd ~/Downloads # [or wherever you download it to]
sudo su
tar-xjvf compat-wireless-3.5-rc2-2-n [or whatever version you downloaded]
cd compat-wireless-3.5-rc2-2-n [or whatever your untarred folder is named(type "ls" if you are unsure - the folder name should be in blue)]
scripts/driver-select atl1c
make
make install

Then just reboot.


Excellent. I should have build essentials already installed.. if not I can get it on there. Thanks. I'll update on progress.

> **wildmanne39 said:**
> Install 12.04 as I recommended in the beginning which is still the best choice.
Thanks
I really can't stand 12.04. I do appreciate what Canonical is attempting to do but it has made ubuntu into something that is no longer appealing to me. The driving reason behind this need for internet access is so that I can sort out some files, wipe the harddrive and then setup Arch. Thank you for the suggestions though.. If this doesn't work I can probably do the update over a bluetooth adapter....

---

