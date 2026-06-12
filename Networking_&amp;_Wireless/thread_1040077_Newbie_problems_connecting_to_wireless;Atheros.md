---
title: "Newbie problems connecting to wireless;Atheros"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by John Temple on 2009-01-15
Please help if you can.  I am brand new to Linux and Ubuntu - only installed Ubuntu 8.10 last night on my new (delivered 7 days ago) laptop - Samsung R510 using Core2duo T5750.  I have a dual boot system Vista (!!) and Ubuntu.  Can't link to my Netgear DG834GT ADSL wireless router from Ubuntu, although its working perfectly well from Vista. I filled in all the requested information in the Ubuntu network connection dialogue box - to no effect.  Vista (control panel, system) tells me I have an Atheros AR5007EG wireless adaptor.  Ubuntu says it is an AR242x wireless PCI express adaptor (I suspect this may be the chipset on the 5007) - states it is "UNCLAIMED". Atheros website is totally unhelpful as far as I have been able to find out.  [http://madwifi-project.org/ticket/1679](http://madwifi-project.org/ticket/1679) is obviously relevant and seems to imply there may be major problems trying to run Atheros under Ubuntu, but it's way beyond my comprehension; mention  of HAL and tar files loses me at once.  
    I have got Thunderbird and Firefox working (have used Firefox for years under windows).   At the moment I am connected by (a very short) cable to my router, which means I have to stand up - have been doing so for about 3 hours now.

   Please, can some kind person tell me in simple terms (comprehensible to a reasonably knowledgeable refugee from Windows!) what to do to get wirelessly connected.  Thanks in advance.

---

### Post by sp0nge on 2009-01-15
I just had to go through this myself. 

Please go to terminal and enter
```
lspci
```

Please post the results in your reply while I find the bits and pieces I used to accomplish this.

---

### Post by kevdog on 2009-01-15
Assuming you are using Intrepid:

sudo aptitude install linux-backports-modules-intrepid-generic

If Hardy:

sudo aptitude install linux-backports-modules-hardy-generic

Then 
System > Adminstration > Hardware drivers
You want to download the restricted drivers ath5k for your card.

It should then prompt you to download the ath5k driver.  This is the driver you need!

---

### Post by sp0nge on 2009-01-15
Use [this tutorial]("http://wireless.kernel.org/en/users/Download"). Be sure to only read the Download latest Linux wireless drivers section. There are several versions listed here that you don't need. The tutorial will walk you through getting the right thing later on. You really need to start paying attention at the Requirements section. 

This should help. Please post back if you run into trouble.

---

### Post by John Temple on 2009-01-15
> **sp0nge said:**
> I just had to go through this myself. 

Please go to terminal and enter
```
lspci
```

Please post the results in your reply while I find the bits and pieces I used to accomplish this.

Hi sp0nge
Thanks for your 2 replies.  
lspci give the following result:

jlt@JLT-HET-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
jlt@JLT-HET-laptop:~$ 

I am working through your second reply (for which many thanks) - but struggling a bit. 

I don't expect any illegitimi to carborundum me in Ubuntu; such goings on are the preserve of the "Redmond Hegemony" (aka Microsoft).
Best regards, and thanks
John Temple

---

### Post by John Temple on 2009-01-15
Hi sp0nge
This tutorial looks exactly right -thanks.  However you wouldn't believe how long it has taken me to find out the version number of my kernel and whether or not I have kernel headers.  Anyhow, "terminal" has been discovered and used for this and I have downloaded the required file "compat-wireless-2009-01-12.tar.bz2". I now have what looks like a box, with that exact label(carefully checked), sitting on my desktop.

The next bit of the tutorial tells me to:
" 
Extract the content of the package:

tar jxvf compat-wireless-$(date -I).tar.bz2
" 
so I open terminal, type in what is written and get errors.
Now I relace $(date -I) with 2009-01-12 -still error
then replace $(date -I) with $(2009-01-12 -I)

" 
jlt@JLT-HET-laptop:~$ tar jxvf compat-wireless-2009-01-12 -I.tar.bz2
tar: invalid option -- I
Try `tar --help' or `tar --usage' for more information.
jlt@JLT-HET-laptop:~$ 
"
then "
jlt@JLT-HET-laptop:~$ tar jxvf compat-wireless-2009-01-12.tar.bz2
tar: compat-wireless-2009-01-12.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jlt@JLT-HET-laptop:~$"

I am obviously doing something wrong - but I've no idea what.

I am going for a cup of coffee; I've been summoned by my "ever loving" and I've now been too long on my feet.  Will log in again in a few hours.
Best regards.
John Temple

---

### Post by theDaveTheRave on 2009-02-21
John

were you ever able to sort this, or did you resort to acquiring a longer network cable!?

It has now been over a month and no-one has replied.... deepest appologies on behalf of the community!

You are obviously about to compile from source, you only error has been the switches to unpack the tar file.

you entered
```

tar jxvf compat-wireless-2009-01-12.tar.bz2

```

needed to be
```

tar [COLOR="Red"]-[/COLOR]jxvf compat-wireless-2009-01-12.tar.bz2

```

I hope that helps.

I guess that afterwards you are going to have to < cd > into the directory that is created (probably someting like compat-wireless-2009-01-12) then you will do

```

make
sudo make install

```

You will be asked for your admin password as you will need to access the system files to install the module (hence the < sudo > on the second line.

I hope that that helps, or better still that I am far too late and you have allready solved your problem from another thread.

Welcome to the community.

David

---

