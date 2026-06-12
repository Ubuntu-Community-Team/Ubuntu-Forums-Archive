---
title: "Help with Hauppauge WinTV Nova-T stick Model 1185 ID 2040:7070"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by dan888 on 2008-04-12
Good Morning,

I've just got a new PC and hope to build a MythTV system. I had the thing 20 mins and blew away MS Vista that came with it. (cant test the card in Vista, doh!)

Now running Ubuntu Hardy Herron with all latest updates;

user01@server04:~$ uname -a
Linux server04 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

I've searched t'interweb untill the early hours and can't find much that helps me.

My DVB card is one of these;
[http://www.currys.co.uk/martprd/store/cur_page.jsp?BV_SessionID=@@@@1475698269.1207998052@@@@&BV_EngineID=ccdhadedklmmdhkcflgceggdhhmdgmi.0&page=Product&fm=null&sm=null&tm=null&sku=226218&category_oid=-33188](http://www.currys.co.uk/martprd/store/cur_page.jsp?BV_SessionID=@@@@1475698269.1207998052@@@@&BV_EngineID=ccdhadedklmmdhkcflgceggdhhmdgmi.0&page=Product&fm=null&sm=null&tm=null&sku=226218&category_oid=-33188)

Now looking around at various posts I see some confusion around Hauppauge models so;
Mine is;
**hauppauge wintv nova t stick**
model info from the box
**model 1185 G (sl-1185-v2.0-uk)**

It is not the older usb or usb2 (larger device) not this;
[http://www.hauppauge.co.uk/pages/products/data_usb2stick.html](http://www.hauppauge.co.uk/pages/products/data_usb2stick.html)

My problem is that I dont think it is recognised, have I got a weird one or a very new model?

when i plug it into a usb 2 slot lsusb shows;
Bus 007 Device 006: ID 2040:7070 Hauppauge

dmesg shows;
[30868.981659] usb 7-3: new high speed USB device using ehci_hcd and address 6
[30869.114499] usb 7-3: configuration #1 chosen from 1 choice

thats about as far as I get! and I'm loathed to install Windoze to test the stick!!!

I have tried various firmware in both these locations;
/lib/firmware/
/lib/firmware/2.6.24-16-generic

firmware was;
dvb-usb-dib0700-01.10.fw
dvb-usb-dib0700-03-pre1.fw
dvb-usb-dib0700-01.fw

lsusb shows;
Bus 007 Device 006: ID 2040:7070 Hauppauge 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2040 Hauppauge
  idProduct          0x7070 
  bcdDevice            1.00
  iManufacturer           1 Hauppauge
  iProduct                2 Nova-T Stick
  iSerial                 3 4030988909
  bNumConfigurations      1

I found one post that says this; but its a bit beyond me, and I cant find those dir or files anywhere;

[http://www.linuxtv.org/pipermail/linux-dvb/2007-December/022177.html](http://www.linuxtv.org/pipermail/linux-dvb/2007-December/022177.html)

Could someone help or point me in the right direction.

Thanks;

---

### Post by Tom Mann on 2008-04-21
Hi there,

I had the very same problem a few weeks back, and have the same TV Stick model as you. :)

I don't know how experienced with Linux you are, but this shouldn't be too difficult.

1. Click on Applications, Utilities then Terminal.
2. In the terminal type 'cd /tmp' (without the quotes)
3. Type the following into a command line and hit enter (or copy and paste the box below), you will be required to enter your password.
```
sudo apt-get install me-tv build-essential mercurial linux-headers-$(uname -r); hg clone http://linuxtv.org/hg/v4l-dvb
```
4. Type 'cd v4l-dvb'
5. Type 'make' (this will generate the driver)
6. Type 'sudo make install'
7. Type 'sudo make unload' (this will prepare the system for the TV card)
8. If it's plugged in, unplug the TV stick and plug it back in.
9. Start up me-tv from Applications/Sound & Video menu.
10. Enjoy your DVB! (and replace that terrible little aerial you get with it too!)

This is a breakdown of the guide found here, all thanks go to the guys that made this easy :)
[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

Tom

---

### Post by chandolin on 2008-05-22
Hi, thank you SO much for your how-to!!

Just a question: I have a nova t stick usb 2 7070, and it's now "successfully initialized and connected", but do I need to add a firmware somewhere?

Thanks

---

### Post by Tom Mann on 2008-06-04
Hi Chandolin - Ubuntu for me automatically uploaded the firmware for my stick when I did the above.
What I did fail to do was install me-tv in my howto - in a terminal do this:

sudo apt-get install me-tv

and you should be able to see me-tv in your applications > sound & video menu.

---

### Post by Riverside on 2008-06-22
> **chandolin said:**
> Hi, thank you SO much for your how-to!!

Just a question: I have a nova t stick usb 2 7070, and it's now "successfully initialized and connected", but do I need to add a firmware somewhere?

ThanksSame issue for me, and rather disappointingly the only download site which I have been able to find is unavailable at present:

[http://ubuntuforums.org/showthread.php?p=5240591#post5240591](http://ubuntuforums.org/showthread.php?p=5240591#post5240591)

---

### Post by Riverside on 2008-06-22
> **Tom Mann said:**
> Hi Chandolin - Ubuntu for me automatically uploaded the firmware for my stick when I did the above.
What I did fail to do was install me-tv in my howto - in a terminal do this:

sudo apt-get install me-tv

and you should be able to see me-tv in your applications > sound & video menu.You're using Hardy I believe?  It appears that the required 
firmware file dvb-usb-dib0700-1.10.fw is now included in linux-restricted-modules packages for Hardy:

[https://bugs.launchpad.net/mythbuntu/+bug/179626/comments/4](https://bugs.launchpad.net/mythbuntu/+bug/179626/comments/4)

However, the firmware file does not appear to be included in linux-restricted-modules packages for Gutsy and previous versions.

Me-TV also appears to be packaged by Ubuntu maintainers for Hardy only, and not previous versions.

---

### Post by Riverside on 2008-06-22
Which has given me an idea.  All I need to do is find and download the linux-restricted-modules-2.6.22-15-generic .deb package for Hardy, use dpkg to extract the dvb-usb-dib0700-1.10.fw file from it, then install it on my (Gutsy) machine.

Except that I have spent the last hour trying to find the actual download location for .deb files on the Ubuntu update servers, with no success!

---

### Post by Riverside on 2008-06-22
> **Riverside said:**
> Which has given me an idea.  All I need to do is find and download the linux-restricted-modules-2.6.22-15-generic .deb package for Hardy, use dpkg to extract the dvb-usb-dib0700-1.10.fw file from it, then install it on my (Gutsy) machine.I meant the linux-restricted-modules-2.6.24-19-generic .deb package for Hardy of course.

A download location that works is:

[http://gb.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-19-386_2.6.24.13-19.42_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-2.6.24-19-386_2.6.24.13-19.42_i386.deb)

I downloaded the .deb and extracted file:

./lib/firmware/2.6.24-19-386/dvb-usb-dib0700-1.10.fw

From the .deb file package, and copied it as root to the correct location on my Gutsy system:

```
sudo cp dvb-usb-dib0700-1.10.fw /lib/firmware/2.6.22-15-generic/.
```

Rebooted, and everything worked.

I next installed Kaffeine and libxine1-ffmpeg and am now watching Freeview TV here in the UK.

---

