---
title: "TV Tuner card"
date: 2015-01-07
forum: Mythbuntu
---

### Post by zkab on 2015-01-07
Hi,

I am new to this forum and Mythbuntu.
My intention is to run Mythbuntu as a back end server.
Before I open my wallet and buy an expensive TV Tuner card I wounder if someone can tell me if this card works 'TBS6985 DVB-S2 Quad Tuner PCIe Card' ([http://www.tbsdtv.com/products/tbs6985-dvb-s2-quad-tuner-pcie-card.html](http://www.tbsdtv.com/products/tbs6985-dvb-s2-quad-tuner-pcie-card.html))
According to the description it should work but that is the sellers information ...

If not - can someone - recommend another dual or quad PCIe DVB-S2 that works.
Thanks

---

### Post by wyliecoyoteuk on 2015-01-07
It should work, but you will have to compile the drivers. visit  [http://www.tbsdtv.com/download/](http://www.tbsdtv.com/download/) for more info.

I use a 6280 DVBTV-2 card, works well, but I needed to compile the drivers.

I am not aware of any HDTV satellite cards that have native drivers. there is a USB one that apparently works out of the box - PCTV nanostick, but not sure if tha satellite version is supported

---

### Post by bullwinkle2 on 2015-01-08
> **zkab said:**
> Before I open my wallet and buy an expensive TV Tuner card I wounder if someone can tell me if this card works 'TBS6985 DVB-S2 Quad Tuner PCIe Card' ([http://www.tbsdtv.com/products/tbs6985-dvb-s2-quad-tuner-pcie-card.html](http://www.tbsdtv.com/products/tbs6985-dvb-s2-quad-tuner-pcie-card.html))
According to the description it should work but that is the sellers information ...

Here are a couple of articles from a free-to-air satellite site that may prove helpful to you:

[What is the best backend software to use for a Free-To-Air satellite TV system?]("http://freetoairamerica.wordpress.com/2014/10/08/what-is-the-best-backend-software-to-use-for-a-free-to-air-satellite-tv-system/")

[URL="http://freetoairamerica.wordpress.com/2014/11/08/do-you-run-one-or-more-tbs-pcie-cards-under-linux-check-your-irqs/"]Do you run one or more TBS PCIe cards under Linux? Check your IRQs…

[/URL]The impression I get from various things that I have read is that it is a minor miracle to get a satellite tuner card to work with Mythbuntu.  Mythbuntu works great with devices like HDHomeRuns, but with satellite tuner cards, I think that in the long run you'd have much greater success using TVHeadEnd, UNLESS you are very skilled in Linux and can accept that it's not going to be an easy install and go.  If you need help, one place you can go is [this forum]("http://rickcaylor.websitetoolbox.com/?forum=106995"), but be aware that the guys there seem to be operating at a pretty high level and seem incapable of explaining things in such a way that new Linux users can understand.

Not that TVHeadEnd is a piece of cake - it's a little bit non-intuitive when you first start out, especially until you realize that certain necessary options don't even appear until you have selected other options that require them and save those selections, but it seems to be much more compatible with satellite tuner cards of the type you have.

As for the sellers description, if even one person can get the card to work then technically they aren't lying, and my take is that there were some early versions of Mythbuntu that had better support for satellite cards that is broken in more recent versions.  See [this post]("http://rickcaylor.websitetoolbox.com/post/show_single_post?pid=1283067895&postcount=54") - the card was different but still it appears there is a real problem with MythTV using these satellite tuner cards.  I would say read the whole thread to get the context, but your eyes will likely glaze over and if you are like me you won't understand a great deal of what they are talking about.

Unless someone else posts here specifically saying that they could get these cards to work with Mythbuntu, I would say the answer to your question is most likely "no".  The TBS6985 is a fine card, and should work well with any software that can actually utilize DVB-S2 tuner cards, but the big question is whether the latest versions of MythTV can.  As wyliecoyoteuk said, you will need to compile the drivers.  Before you do, you may need to install some packages (you only need to do this once and you may already have some or all of these):

sudo apt-get update
sudo apt-get install linux-headers-`uname -r`  **<— Note those are backticks, NOT single quotes!**
sudo apt-get install make gcc

Then I have followed [these instructions]("http://linux.mjnet.eu/post/401/tbs-driver-install-ubuntu-11-10-tbs6921/") when installing TBS drivers, except of course you will want the current version of the drivers for your card, so adjust the URL's and paths accordingly.  Also the dmesg test shown at the bottom of that page may not show the TBS6985, instead use either or both of

dmesg | grep -i dvb
ls -l /dev/dvb

The first line in particular should show output similar to this (but with the actual MAC address of your card) if the drivers are installed correctly:

[   10.326628] DVB: registering new adapter (SAA716x dvb adapter)
[   10.916765] TurboSight TBS6985 DVB-S2 card port0 MAC=00:00:00:00:00:00
[   10.916774] DVB: registering adapter 0 frontend 0 (TurboSight TBS 6985 DVBS/S2 frontend)...
[   10.916987] DVB: registering new adapter (SAA716x dvb adapter)
[   11.466620] TurboSight TBS6985 DVB-S2 card port1 MAC=00:00:00:00:00:00
[   11.466629] DVB: registering adapter 1 frontend 0 (TurboSight TBS 6985 DVBS/S2 frontend)...
[   11.466855] DVB: registering new adapter (SAA716x dvb adapter)
[   12.018292] TurboSight TBS6985 DVB-S2 card port2 MAC=00:00:00:00:00:00
[   12.018298] DVB: registering adapter 2 frontend 0 (TurboSight TBS 6985 DVBS/S2 frontend)...
[   12.018493] DVB: registering new adapter (SAA716x dvb adapter)
[   12.569971] TurboSight TBS6985 DVB-S2 card port3 MAC=00:00:00:00:00:00
[   12.569980] DVB: registering adapter 3 frontend 0 (TurboSight TBS 6985 DVBS/S2 frontend)...
[   12.589835] DVB: registering new adapter (SAA716x dvb adapter)

Also note that the tuners may be numbered in the reverse order from what you expect, in other words adapter 3 may actually be tuner "A" and adapter 0 may be tuner "D".  So if the card doesn't seem to work on your initial tests, that could be the problem.

---

### Post by wyliecoyoteuk on 2015-01-09
I did:

sudo apt-get update
sudo apt-get install linux-headers-`uname -r`
sudo apt-get build-essential 

 you will also need 

sudo apt-get pk7zip-full
or 
sudo apt-get unzip

to unzip the archive

Sorry I can't comment on Satellite cards, not having one, but most DVB-T cards work with no trouble, I have used several different ones in the past. 
DVB-T2 cards are a different matter, but the TBS6280 works perfectly once the drivers are in place.
Annoying to have to recompile whenever the kernel is updated, but not a deal breaker for me.
I tend to delete the /lib/modules/<kernel number>/kernel/drivers/media folder when recompiling, as it sometimes doesn't overwrite cleanly.

As for the problems with different back and frontend versions on Mythtv, I use Kodi (used to be XBMC) as a frontend for MythTV with no issues, it even has an Android client.
Myth also supports multiple channels per tuner (must be same multiplex).

I have used MythTV for years without any major issues. I looked at TVheadend a while back, and scheduling was poorer, especially duplicate detection.

---

### Post by bullwinkle2 on 2015-01-09
> **wyliecoyoteuk said:**
> As for the problems with different back and frontend versions on Mythtv, I use Kodi (used to be XBMC) as a frontend for MythTV with no issues, it even has an Android client.
Myth also supports multiple channels per tuner (must be same multiplex).

I have used MythTV for years without any major issues. I looked at TVheadend a while back, and scheduling was poorer, especially duplicate detection.

I've used MythTV (actually Mythbuntu on the backend side) and will readily agree that it is in some ways superior to TVHeadEnd, when it will work with your tuners.  I would have preferred to use Mythbuntu with my satellite tuner but everything I read said that it was nearly impossible to get MythTV to work with satellite tuners, unless you are a certified Linux geek.  And the Kodi PVR addon for MythTV does seem to work with a range of backend versions, unlike Myth's official frontend.

If you have used MythTV for years with DVB-T cards, that does not surprise me.  I've used MythTV with HDHomeRun devices, and it was the same, the MythTV backend found and used them with no real problems.  It's only when you get into satellite tuners that MythTV falls over flat, if everything I have read is to be believed.

That said, I would not discourage you from trying it.  Maybe the cards, drivers, or MythTV itself have improved, and what was a problem a year ago no longer is.  I just wanted you to be aware that people have tried and failed, and found that the same devices that MythTV wouldn't touch are sometimes readily found and used by TVHeadEnd.  So if you do try and you can't make it work, don't automatically assume that you did something wrong. I wish you success, it would be nice to see someone get this card working with MythTV.

---

### Post by wyliecoyoteuk on 2015-01-10
I usually test with VLC first, if that won'r see the tuner, you are on a hiding to nothing really, as V4L (Video4Linux) drivers are produced by the same group.

Most of the problems I have had with compiled drivers were down to lack of understanding of the process when I first tried it.
There are some quite confusing and over-complex posts out there.

That is why I usually clean out and delete the old v4l drivers before compiling.

It might be a good idea to look at the TBS forums.
[http://www.tbsdtv.com/forum/](http://www.tbsdtv.com/forum/)

---

### Post by zkab on 2015-01-14
Thanks for all valuable input - I read them very carefully.

I will take the challenge and try to get satellite card to work.
I made a change  ... I ordered TBS6908 ([http://www.buydvb.net/tbs6908-professional-dvbs2-quad-tuner-pcie-card-p-118.html](http://www.buydvb.net/tbs6908-professional-dvbs2-quad-tuner-pcie-card-p-118.html))  instead of TBS6985.
TBS6908 is newer and I thought it will work better.
My setup will be MythTV as backend and Kodi as frontend.
Haven't got my card yet and I guess I have a lot of reasons to return to this forum when it arrives.

One thing I don't understand is why MythTV haven't made it easier to get satellite cards to work - they are used in Europe a lot.

---

### Post by wyliecoyoteuk on 2015-01-14
It isn't MythTV, or even Linux. It is the manufacturer's choice not to make open-source drivers.
There are ongoing efforts to reverse engineer the TBS HD drivers, but they are still in the early stages. 
If they come to fruition, then the cards will work "out of the box", in the same way most SDTV cards do.
Good luck, and don't hesitate to ask if you need help.

---

### Post by zkab on 2015-01-14
Ok

---

### Post by zkab on 2015-02-02
I followed exactly instructions for README_TBS6980 (same as [http://linux.mjnet.eu/post/401/tbs-driver-install-ubuntu-11-10-tbs6921/](http://linux.mjnet.eu/post/401/tbs-driver-install-ubuntu-11-10-tbs6921/)) but apparently something went wrong:

I.1 extract linux-tbs-drivers.tar.bz2 archive:
*** In my case 'linux-tbs-drivers_150130.tar.bz2'
I.2 go to driver package directory:
I.3 depending on your kernel version and if the kernel is x86 or 
x86_64 (check output of 'uname -a') do:
*** In my case - for any x86_64 kernel (x86 64 bit installations of Linux):
# ./v4l/tbs-x86_64.sh
I.4 build and install the driver:
# make && make install
I.5 reboot in order to load the newly installed driver:
# shutdown -r now
I.6 after reboot check that the newly installed driver is loaded correctly:
# dmesg | grep cx gave me errors:

dmesg | grep -i dvb
[    7.247918] tbs_pcie_dvb: disagrees about version of symbol dvb_dmxdev_init
[    7.247920] tbs_pcie_dvb: Unknown symbol dvb_dmxdev_init (err -22)
[    7.247937] tbs_pcie_dvb: disagrees about version of symbol dvb_register_adapter
[    7.247938] tbs_pcie_dvb: Unknown symbol dvb_register_adapter (err -22)
[    7.247943] tbs_pcie_dvb: disagrees about version of symbol dvb_dmx_swfilter_packets
[    7.247944] tbs_pcie_dvb: Unknown symbol dvb_dmx_swfilter_packets (err -22)
[    7.247950] tbs_pcie_dvb: disagrees about version of symbol dvb_dmx_release
[    7.247950] tbs_pcie_dvb: Unknown symbol dvb_dmx_release (err -22)
[    7.247955] tbs_pcie_dvb: disagrees about version of symbol dvb_net_init
[    7.247956] tbs_pcie_dvb: Unknown symbol dvb_net_init (err -22)
[    7.247959] tbs_pcie_dvb: disagrees about version of symbol dvb_dmxdev_release
[    7.247960] tbs_pcie_dvb: Unknown symbol dvb_dmxdev_release (err -22)
[    7.247964] tbs_pcie_dvb: disagrees about version of symbol dvb_frontend_detach
[    7.247965] tbs_pcie_dvb: Unknown symbol dvb_frontend_detach (err -22)
[    7.247968] tbs_pcie_dvb: disagrees about version of symbol dvb_net_release
[    7.247969] tbs_pcie_dvb: Unknown symbol dvb_net_release (err -22)
[    7.247972] tbs_pcie_dvb: disagrees about version of symbol dvb_unregister_frontend
[    7.247973] tbs_pcie_dvb: Unknown symbol dvb_unregister_frontend (err -22)
[    7.247976] tbs_pcie_dvb: disagrees about version of symbol dvb_register_frontend
[    7.247977] tbs_pcie_dvb: Unknown symbol dvb_register_frontend (err -22)
[    7.247981] tbs_pcie_dvb: disagrees about version of symbol dvb_unregister_adapter
[    7.247981] tbs_pcie_dvb: Unknown symbol dvb_unregister_adapter (err -22)
[    7.247984] tbs_pcie_dvb: disagrees about version of symbol dvb_dmx_init
[    7.247985] tbs_pcie_dvb: Unknown symbol dvb_dmx_init (err -22)

---

### Post by wyliecoyoteuk on 2015-02-02
I had a similar issue.
It is a conflict between driver versions.
If you repeat the compiling, but first delete the existing v4l drivers, it should work. Here is what I did:
[https://wyliecoyoteuk.wordpress.com](https://wyliecoyoteuk.wordpress.com)

---

### Post by wyliecoyoteuk on 2015-02-02
The driver package is the same for all the tbs cards.
It recompiles all of the v4l Drivers.
150130 is the very latest, out 3 days ago, and the only one to support your card.

---

### Post by zkab on 2015-02-02
> **wyliecoyoteuk said:**
> If you repeat the compiling, but first delete the existing v4l drivers, it should work.
Where are the v41l drivers located ?
According to the wordpress-link v4l files are stored at:
'/lib/modules/kernel/(your kernel version)/drivers/media' but I don't have that location.
I have following:
ls -l /lib/modules/3.13.0-45-generic/kernel/drivers/media/v4l2-core/
total 592
-rw-r--r-- 1 root root  38148 Jan 13 21:13 tuner.ko
-rw-r--r-- 1 root root  17196 Jan 13 21:13 v4l2-common.ko
-rw-r--r-- 1 root root  25556 Jan 13 21:13 v4l2-dv-timings.ko
-rw-r--r-- 1 root root   8900 Jan 13 21:13 v4l2-int-device.ko
-rw-r--r-- 1 root root  24636 Jan 13 21:13 v4l2-mem2mem.ko
-rw-r--r-- 1 root root  58148 Jan 13 21:13 videobuf2-core.ko
-rw-r--r-- 1 root root  25012 Jan 13 21:13 videobuf2-dma-contig.ko
-rw-r--r-- 1 root root  12340 Jan 13 21:13 videobuf2-dma-sg.ko
-rw-r--r-- 1 root root   9524 Jan 13 21:13 videobuf2-memops.ko
-rw-r--r-- 1 root root  12612 Jan 13 21:13 videobuf2-vmalloc.ko
-rw-r--r-- 1 root root  37900 Jan 13 21:13 videobuf-core.ko
-rw-r--r-- 1 root root  17388 Jan 13 21:13 videobuf-dma-contig.ko
-rw-r--r-- 1 root root  23260 Jan 13 21:13 videobuf-dma-sg.ko
-rw-r--r-- 1 root root  17396 Jan 13 21:13 videobuf-dvb.ko
-rw-r--r-- 1 root root  14116 Jan 13 21:13 videobuf-vmalloc.ko
-rw-r--r-- 1 root root 216988 Jan 13 21:13 videodev.ko

---

### Post by wyliecoyoteuk on 2015-02-03
Sorry, typo.
Should be 
/lib/modules/(kernel version)/kernel/drivers/media
Delete the contents of that folder.

In your case 
/lib/modules/3.13.0-45-generic/kernel/drivers/media

---

### Post by zkab on 2015-02-03
OK - I cleared the directory, recompiled and rebooted.
As I understand there are some issues left - 'make' generates a warning and 'dmesg' complains about the card - please check below.
And I don't get any video signal to my Kodi frontend.

Excerpt from sudo make:

  LD [M]  /home/rajan/TBS6908_driver/linux-tbs-drivers/v4l/snd-bt87x.o
  Building modules, stage 2.
  MODPOST 527 modules
WARNING: could not find /home/rajan/TBS6908_driver/linux-tbs-drivers/v4l/.tbs8921ctrl.o.cmd for /home/rajan/TBS6908_driver/linux-tbs-drivers/v4l/tbs8921ctrl.o
WARNING: could not find /home/rajan/TBS6908_driver/linux-tbs-drivers/v4l/.tbs5220ctrl.o.cmd for /home/rajan/TBS6908_driver/linux-tbs-drivers/v4l/tbs5220ctrl.o
WARNING: could not find /home/rajan/TBS6908_driver/linux-tbs-drivers/v4l/.tbs5680ctrl.o.cmd for /home/rajan/TBS6908_driver/linux-tbs-drivers/v4l/tbs5680ctrl.o

dmesg gave this:

 8.123072] cx23885 driver version 0.0.3 loaded
[    8.123136] cx23885[0]: Your board isn't known (yet) to the driver.
[    8.123136] cx23885[0]: Try to pick one of the existing card configs via
[    8.123136] cx23885[0]: card=<n> insmod option.  Updating to the latest
[    8.123136] cx23885[0]: version might help as well.
[    8.123137] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[    8.123138] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[    8.123138] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[    8.123139] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[    8.123139] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[    8.123140] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[    8.123140] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[    8.123141] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[    8.123142] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[    8.123142] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[    8.123143] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[    8.123143] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[    8.123144] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[    8.123144] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[    8.123145] cx23885[0]:    card=13 -> Compro VideoMate E650F
[    8.123146] cx23885[0]:    card=14 -> TurboSight TBS 6920
[    8.123146] cx23885[0]:    card=15 -> TeVii S470
[    8.123147] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[    8.123147] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[    8.123148] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[    8.123148] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[    8.123149] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[    8.123149] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[    8.123150] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[    8.123150] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[    8.123151] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[    8.123151] cx23885[0]:    card=25 -> Compro VideoMate E800
[    8.123152] cx23885[0]:    card=26 -> Hauppauge WinTV-HVR1290
[    8.123152] cx23885[0]:    card=27 -> Mygica X8558 PRO DMB-TH
[    8.123153] cx23885[0]:    card=28 -> LEADTEK WinFast PxTV1200
[    8.123153] cx23885[0]:    card=29 -> GoTView X5 3D Hybrid
[    8.123154] cx23885[0]:    card=30 -> NetUP Dual DVB-T/C-CI RF
[    8.123154] cx23885[0]:    card=31 -> Leadtek Winfast PxDVR3200 H XC4000
[    8.123155] cx23885[0]:    card=32 -> TurboSight TBS 6980
[    8.123155] cx23885[0]:    card=33 -> TurboSight TBS 6981
[    8.123156] cx23885[0]:    card=34 -> TurboSight TBS 6921
[    8.123156] cx23885[0]:    card=35 -> TurboSight TBS 6925C
[    8.123298] CORE cx23885[0]: subsystem: 0070:c138, board: UNKNOWN/GENERIC [card=0,autodetected]
[    8.204748] tbs6908fe: module license 'TurboSight Proprietary: [www.tbsdtv.com](www.tbsdtv.com)' taints kernel.
[    8.204749] Disabling lock debugging due to kernel taint
[    8.204907] TurboSight TBS 6908 Frontend Attaching...
[    8.206016] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    8.249694] cx23885_dev_checkrevision() Hardware revision = 0xd0
[    8.249697] cx23885[0]/0: found at 0000:05:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xf7c00000
[    8.310039] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    8.310114] IPv6: ADDRCONF(NETDEV_UP): em1: link is not ready
[    9.115268] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.232067] TurboSight TBS6908 DVB-S2 card adapter0 MAC=00:22:ab:69:08:01
[    9.232070] DVB: registering adapter 0 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...
[    9.232117] DVB: registering new adapter (TBS PCIE DVB Adapter)
[    9.232260] TurboSight TBS 6908 Frontend Attaching...
[    9.234926] TurboSight TBS6908 DVB-S2 card adapter1 MAC=00:22:ab:69:08:02
[    9.234928] DVB: registering adapter 1 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...
[    9.234962] DVB: registering new adapter (TBS PCIE DVB Adapter)
[    9.393364] TurboSight TBS 6908 Frontend Attaching...
[    9.797254] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   10.415118] TurboSight TBS6908 DVB-S2 card adapter2 MAC=00:22:ab:69:08:03
[   10.415120] DVB: registering adapter 2 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...
[   10.415231] DVB: registering new adapter (TBS PCIE DVB Adapter)
[   10.415456] TurboSight TBS 6908 Frontend Attaching...
[   10.418214] TurboSight TBS6908 DVB-S2 card adapter3 MAC=00:22:ab:69:08:04
[   10.418216] DVB: registering adapter 3 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...
[   11.977452] e1000e: em1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   11.977479] IPv6: ADDRCONF(NETDEV_CHANGE): em1: link becomes ready
[   16.133411] init: failsafe main process (643) killed by TERM signal
[   16.168639] audit_printk_skb: 12 callbacks suppressed

---

### Post by wyliecoyoteuk on 2015-02-03
Sorry, but that is as far as I can go, not having access to the card.
I have similar errors for make.
The notes for that version of the driver say "initial support for 6908"
Not sure whether that means it will work or not. it seems to be the same chipset as the 6983.
It does look like the driver is installed, have you run the mythbackend setup to see if the card is recognised?

---

### Post by zkab on 2015-02-03
My fault ...
I left my testing tuner card Hauppauge WinTV HVR-5500 HD (works OK) in the computer together with TBS6908 and it seemed that it created some conflict.
But when I removed Hauppauge then it looked better after the recompile & reboot.

dmesg | grep -i TBS
[    8.432304] TBS PCIE Detected TBS6908 Board Rev 3
[    8.433476] DVB: registering new adapter (TBS PCIE DVB Adapter)
[    8.595044] tbs6908fe: module license 'TurboSight Proprietary: [www.tbsdtv.com](www.tbsdtv.com)' taints kernel.
[    8.595178] TurboSight TBS 6908 Frontend Attaching...
[    9.595734] TurboSight TBS6908 DVB-S2 card adapter0 MAC=00:22:ab:69:08:01
[    9.595736] DVB: registering adapter 0 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...
[    9.595773] DVB: registering new adapter (TBS PCIE DVB Adapter)
[    9.595908] TurboSight TBS 6908 Frontend Attaching...
[    9.598504] TurboSight TBS6908 DVB-S2 card adapter1 MAC=00:22:ab:69:08:02
[    9.598505] DVB: registering adapter 1 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...
[    9.598526] DVB: registering new adapter (TBS PCIE DVB Adapter)
[    9.757506] TurboSight TBS 6908 Frontend Attaching...
[   10.768223] TurboSight TBS6908 DVB-S2 card adapter2 MAC=00:22:ab:69:08:03
[   10.768226] DVB: registering adapter 2 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...
[   10.768331] DVB: registering new adapter (TBS PCIE DVB Adapter)
[   10.768484] TurboSight TBS 6908 Frontend Attaching...
[   10.771173] TurboSight TBS6908 DVB-S2 card adapter3 MAC=00:22:ab:69:08:04
[   10.771175] DVB: registering adapter 3 frontend 0 (TurboSight TBS 6908 DVBS/S2 frontend)...

But still I can't scan ... which I did without problems with my testing tuner card Hauppauge before ... hmmm

sudo w_scan -fs -c SE -s s0w8 -C UTF-8 -O 0 -R 0
...
trying 'S2 f = 10747 kHz H SR = 25000  3/4 0,35  8PSK'
(time: 00:11) 
trying 'S2 f = 10747 kHz V SR = 25000  3/4 0,35  8PSK
...
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

---

### Post by wyliecoyoteuk on 2015-02-04
I have just compiled and installed that driver, I get no errors at all, and everything works with my TBS 6820
However, I don't have a Satellite card to test with, sorry.

---

### Post by zkab on 2015-02-05
I started from scratch ...

1. Made a new installation of Ubuntu server.
2. Removed files /lib/modules/3.13.0-45-generic/kernel/drivers/media/*
3. Compiled tbs drivers
4. Rebooted

and voilà ... no errors.
It seemed that some old left-overs before disturbed the building of tbs drivers.

Now I am going to test my back&frontend to see the quality if the signal ...

Thanks for your help

---

