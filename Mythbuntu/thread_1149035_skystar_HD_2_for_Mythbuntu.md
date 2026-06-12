---
title: "skystar HD 2 for Mythbuntu"
date: 2009-05-04
forum: Mythbuntu
---

### Post by grifter13 on 2009-05-04
Hi Everyone,

Does anyone know how or able to point me to the right links to get SkyStar HD 2 working for Mythbuntu?  Thanks in advance.

Grif

---

### Post by tobiz on 2009-05-10
> **grifter13 said:**
> Hi Everyone,

Does anyone know how or able to point me to the right links to get SkyStar HD 2 working for Mythbuntu?  Thanks in advance.

Grif
Look at [http://www.munz.li/?p=47#comment-382]("http://www.munz.li/?p=47#comment-382")

I followed this an have this card working.

---

### Post by koe71 on 2009-06-16
> **tobiz said:**
> Look at [http://www.munz.li/?p=47#comment-382](http://www.munz.li/?p=47#comment-382)

I followed this an have this card working.


I installed Mythbuntu 9.04

updated it

sudo -s
apt-get install hg-buildpackage
cd /usr/local/src
hg clone [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin)
cd s2-liplianin
cd linux/include/linux
ln -s /usr/src/linux-headers-`uname -r`/include/linux/compiler.h ./
cd ../../../
make
make install
depmod -a
reboot  (might be an other way of restarting services butthis was fast enough.. :) )


worked for me... although without upgrading mythtv to 0.22 (beta) there won't be much HD as I understood.. still strugeling enough.. :) have tv on this installation so i am getting close.


ref:
[http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-multiproto-63073](http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-multiproto-63073)
[http://www.linuxtv.org/wiki/index.php/Azurewave_AD_SP400_CI_(VP-1041]("http://www.linuxtv.org/wiki/index.php/Azurewave_AD_SP400_CI_%28VP-1041"))

---

### Post by gocin on 2009-08-13
Hi, here's just another success - story :)

I tried the way koe71 wrote in this thread - and it works:)

My system is a Asus M4N78 Pro with an AMD 5050e, 4GB ram (3.2GB usable) and an Asus EN9400GT silent. 

I'm running Mythbuntu 9.04 with the latest updates and the NVidia driver 180.? installed.

SD channels are working in a good quality, signal strength is 0% s/n ratio is 2.2dB - so the signal strength is nonsense, with my cheap dvb-s card I had about 70% and s/n about 4dB. But that's no problem as long as it works.

Another thing I discovered is that CPU load increases up to about 70% on both cores if I try to watch a HD channel. But basicly it works - but only for a few seconds, then the screen freezes. 

Interesting for my opinion is that the decryption - which should be available  implemented in my Asus EN9400GT (VDPAU?) is not working, so the CPU has to do the job. Maybe the freezing results on my CPU, mybe I'd need a more powerful one? Against that thesis stands that the load is not 100%

If I can do sth (testing?) for bringing support for the SkyStar HD2 into the next MythBuntu version just contact me.

---

### Post by gocin on 2009-10-01
Yesterday I installed Mythbuntu 9.10 alpha 6 and also installed the liplianin-s2 driver. It installed without problems but it's not working.
Maybe due to the Kernel update to 2.6.31-9? Under 2.6.28-15 it worked as described before.

---

### Post by koe71 on 2009-11-19
now 9.10 is out the procedure changed a bit.... :)
Have fun.


sudo -s 
apt-get install libncurses5-dev hg-buildpackage
cd /usr/local/src 
hg clone [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin) 
cd s2-liplianin 
cd linux/include/linux 
ln -s /usr/src/linux-headers-`uname -r`/include/linux/compiler.h ./ 
cd ../../../
make menuconfig
     unselect the folowing module:
         multimedia support-> DVB/ATSC Adapter -> Firetv/Floppydtv 
make 
make install 
depmod -a 
 reboot  (might be an other way of restarting services but this was fast enough.. :smile: )
 

did not do it myself.. just a gatherer..... 

[http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-multiproto-63073](http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-multiproto-63073) 
[http://www.linuxtv.org/wiki/index.php/Azurewave_AD_SP400_CI_(VP-1041]("http://www.linuxtv.org/wiki/index.php/Azurewave_AD_SP400_CI_%28VP-1041")) 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://bugs.launchpad.net/ubuntu/+bug/440117](https://bugs.launchpad.net/ubuntu/+bug/440117)

---

### Post by SanderVdB on 2009-12-17
Hello,


I have followed the steps that koe71 described in his last reply but my systems stopped working after the reboot. The last thing I could see was that it was trying to load the LIRC module.

The software I have used is the last one from Mythbuntu, I have tried with the updates and without the updates. It is giving the same result.

Could someone help me to set up my skystar hd2 cart on a myth tv system.


Thank you in advance,

Kind regards,

Sander

---

### Post by mshannon on 2010-01-10
I'm also unable to get my Skystar HD2 recognised by Mythbuntu, I have tried the above and searched the web and find many users with the same problem.

I have been using Mythbuntu for many years with DVBT and DVBS cards, I have recently upgraded to a small factor &#8211; Mini ITX Asus AT3N7A-I, in the hope of putting this into a small low power case. I'm running it in a 400w A-Case with a 250g 2.5 drive. I wanted to get DVB S2 and hence the Skystar HD2 as this is one of the few (only?) low profile HDS2 cards available in the UK.

My card works fine in Vista on another PC, a DVBT card works fine in my current Mythbuntu set-up. I have also tried it on a full install of 9.04 and 8.10 but nothing in /dev, there is no dvb directory.

I'm reluctant to buy another DVBS2 card as the v4l wiki lists problems with all of them (if you open each cards wiki) and even more reluctant to go onto Vista/Win7 as I like Mythtv. 

Does anyone have a Skystar HD2 or any DVBS2 card working?

---

### Post by richard.e.morton on 2010-05-19
I did what Koe said and my system is now borked; boots, but after a few seconds is unresponsive. reports errors with dvb-usb event or something in recovery mode.

this is on ubuntu 9.10.

---

### Post by amacmil on 2010-06-09
Anyone managed to get this working yet?

---

### Post by alien878 on 2010-06-09
> **richard.e.morton said:**
> I did what Koe said and my system is now borked; boots, but after a few seconds is unresponsive. reports errors with dvb-usb event or something in recovery mode.

this is on ubuntu 9.10.Yup.  The latest kernel update in 9.10 borked my system when I re-added the mantis drivers (similar to what koe describes).  I had to go back to the older kernel.

To go back (there is probably a better way, but I couldn't find the menu.lst file):  Hard power off the computer during boot.  Reboot and it should show the grub2 menu.  Select the older kernel and it should boot.  apt-get install startupmanager,  then run it to permanently set the default kernel.

I had other problems with the mantis drivers in 10.04, so I can't upgrade to that.  I guess I'll just freeze my system until the mythbuntu gets a kernel that includes the mantis drivers (10.10?).

(I'm using a TerraTec Cinergy S2 PCI HD CI)

---

### Post by tester100 on 2010-12-11
Hi guys

Any luck with Mythbuntu 10.10 or 10.04 to work with SkystarHD ??

or which other DVBS2 PCI could work ok in those systems ?

---

### Post by alien878 on 2010-12-12
I can't speak for the skystar directly, but I managed to get the mantis drivers required for the skystar working on my TerraTec Cinergy S2 PCI HD CI in 10.10.

See [http://ubuntuforums.org/showthread.php?p=9981251#post9981251](http://ubuntuforums.org/showthread.php?p=9981251#post9981251)

NOTE NOTE NOTE:  I notice that there a new kernel has just been added to 10.10.  I have not yet tried it.  I can only say the original kernel delivered with 10.10 works with this driver.

---

### Post by tester100 on 2011-11-10
Hi guys

any updates on mythbuntu+mythTV with a decent enough support drivers for skystar hd2 ??

i have seen that the mythbuntu 11.10 version is out and also new version of mythtv

as anyone teste this with skystarhd2 pci card ??

by reading the support page from mythtv i have seen that the most well supported are the

WinTV-NOVA-HD-S2 (model 229)

for dvb-s and s2 streams for bot PAL and NTSC...

does anyonw confirm this, just before i go out like a lunatic and start buyin hardware that will not be compatible otherwords..

Also has anyone tested the HTPC cases with the iMon VDF and remote controls.. are they well supported for mythbuntu by now ?


any help is welcome guys on what sort of PCI dvbs and s2 compatible for mythtv and mythbuntu without crashes or permanent log errors.

thxs
tester100

---

