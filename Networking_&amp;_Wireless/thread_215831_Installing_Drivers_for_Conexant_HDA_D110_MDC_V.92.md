---
title: "Installing Drivers for Conexant HDA D110 MDC V.92"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by rayerta on 2006-07-14
Hello, I'm trying to get online using my modem - I know, it's archaic, but I'm living in Sudan. What can you expect?

Quick Facts:
PC - Dell Inspiron B130
Modem - Conexant HDA D110 MDC V.92
Version - Breezy Badger; 2.6.12-10-386

Here's the story. I don't think my computer even recognizes that I have a modem. I read somewhere that it might be integrated with my sound card. I would like to know how to detect my modem. This is the output I get from lspci

$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

I installed the XP driver from Conexant using ndiswrapper, but this is the output from ndiswrapper(the first driver/hardware listed is my successful installation of my wireless card)

$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
genhsf5 driver present

I was told by a linux friend that I have to use a ppp daemon to get on the net. I configured my connection with pppconfig (it couldn't detect a modem). I subsequently tried using pon to dial up and this was the output

$ pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

I've been studying this problem for a while now, but mostly I'm still at square one - how do I get my computer to recognize I have a modem? then, how do I install the appropriate driver? finally, how do I dial up? oops, one more - are there any other steps I have forgotten/not included?

Thank you tons.

---

### Post by blawson on 2006-10-23
I'm having the same problem. I've seen article after article about installing Ubuntu on Dell Notebooks, and all of them said that the Conexant modems have not been tested.

I think I finally found a driver for it!

Check out [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) .

I have not had a chance to try it yet, but if you get any results, let me know! :-D

---

### Post by Aleph42 on 2007-07-26
HI

Although I'm replying a year after the original post, know that this modem is not that archaic; I have the same in my Dell Ispiron 9400. Apparently connexant modems are very poorly supported (or you have to pay 20$ to linuxant). I'll tell if I find a good way to do this

---

### Post by siguretm on 2007-07-26
you should find the necessary package on dell site [here]("http://support.us.dell.com/support/downloads/download.aspx?c=us&cs=555&l=en&s=biz&releaseid=R155004&formatcnt=1&libid=0&fileid=206745").

From Dell USA > Support Home Page > Drivers & Downloads

Driver
Release Title:	Communications: Conexant D110,HDA,MDC,v.92,modem, Driver, Ubuntu Desktop Edition 7.04, English, Inspiron MM061, v.V7.60.00.06, A00
Release Date:	7/10/2007
Criticality:	Recommended
Description:	Linux driver for ubuntu OS x86 32bit V7.60.00.06 
File Name :	hsfmodem_7.60.00.06oem_i386.deb


it works fine for me and i'm using KPPP.

but it doesn't work if you just want to test it from live cd because you need to restart once you have installed it...

---

### Post by waynegr on 2007-08-01
Hello, hope no one minds me joining in--I've got this modem, and I'm trying out the driver in the post above right now--I'm doing a dual boot with windows right now.  We'll see if it works.  BTW, it says it's for Feisty, will it work with Edgy do you think?  I guess I'm about to find out...

Thanks, though for the link.

---

### Post by waynegr on 2007-08-02
Nope--didn't work.  I don't know what's wrong.  Perhaps edgy doesn't work with that driver or something.  I'd upgrade to feisty, but I kind of need an internet connection in my edgy to do that--and until I can get back to real internet (not dial-up) that's not possible... oh, well.  If you have any suggestions, post them.  Thanks!

---

