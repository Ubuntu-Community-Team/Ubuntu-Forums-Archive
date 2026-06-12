---
title: "Huawei e1750 on 9.10: it doesn't work anymore!"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by fantasmino on 2009-11-03
Hello,
as in the subject with the new release 9.10 the Internet usb key Huawei e1750 doesn't work any more. I spent many and many hours surfing the web trying to find a solution, trying to install many connection software, but nothing... The driver included in the key doesn't work any more, too. And Ubuntu doesn't recognise it in any way. 
The only solution for me was to downgrade Ubuntu to 9.04 again, reinstall the pen driver and get it work again. Very bad... :evil:
Someone founded the way to get it working in 9.10?
Thanks in advance.

Luca

---

### Post by jimmers on 2009-11-03
Hi Luca,
You don't say who supplied your dongle, but I had trouble with my Huawei K3565 from Vodafone, after upgrade it would'nt work.
Then I found this on the Betavine Website, and it works, I am connected by the K3565 as I write this,
try it if you like, you wont know otherwise. 

  	 	 	 	 	 	  VODAFONE MOBILE CONNECT INSTALLATION INSTRUCTIONS.  -------------------------------------------------   * You need a previously working internet connection (e.g: your ethernet one)  * Download from this page these two DEB packages:       - usb-modeswitch      - vodafone-mobile-connect  * Install them, e.g: in a terminal command line (substitute the version and architecture here for the ones you have downloaded)       sudo dpkg -i usb-modeswitch_0.9.4-1_i386.deb      sudo dpkg -i vodafone-mobile-connect_1.99.17-8_all.deb  * After this step, you will possibly have unresolved dependencies problems. To solve them execute:       sudo apt-get -f install    * If everything has gone fine you can plug in the modem, and execute the driver with:       vodafone-mobile-connect-card-driver-for-linux


Best of Luck Jimmers

---

### Post by pdc on 2009-11-03
this is a very good point jimmers;

as I understand it, the VMC software will allow a 3G modem to connect to any network; (ie doesn't have to be vodafone);

the VMC software is built with ozerocdoff; (rather than usbmodeswitch) to achieve the same thing of flipping a device from CD-Rom state to modem state

---

### Post by fantasmino on 2009-11-04
Hello and thanks for reply.
The provider of the dongle is 3.
I tried almost all possibilities founded on internet. But no results.:evil:
I had succes only on my eeepc with ubuntu remix, but the same machine with ubuntu desktop doesn't work. I think there is a problem with the kernel. 
Here all my tries:

updated kernel and headers to the latest release:
[http://people.canonical.com/~apw/lp451337-karmic/](http://people.canonical.com/~apw/lp451337-karmic/)

modified file following this bug:
[https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/424050](https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/424050)

installed the driver inside the dongle

installed VMC:
[https://forge.betavine.net/frs/?group_id=12&release_id=20](https://forge.betavine.net/frs/?group_id=12&release_id=20)

With all this, the ubuntu remix works fine with the e1750 and VMC. The other PC doesn't. Unfortunately the dongle isn't for the netbook!!](*,)

I have no more ideas, apart downgrade again to 9.04.
Very bad.

---

### Post by pdc on 2009-11-04
well if 9.04 works for you, that's all you need ?

---

### Post by fantasmino on 2009-11-05
> **pdc said:**
> well if 9.04 works for you, that's all you need ?

Yes, in fact I downgraded to 9.04, but I can downgrade to 8.10, 8.04 etc, or use windows or mac, this is not the point, I think.
If I upgrade to a new version, is not a good point for ubuntu that something so important, like the internet connection, doesn't work.

---

### Post by CbrPad on 2009-11-05
This is a well-known bug...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146?comments=all)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/449394](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/449394)

You might possibly be able to get it working by doing this...

sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001
sudo pppd ttyUSB0

Note that that usbserial vendor and product are for a Huawei E220 so your's could be different.  Try a lsusb or have a look at [https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

I've gone to Mandriva myself as it takes ages of plugging in and out the modem while rmmodding etc, just not worth the hassle, but your mileage may vary.  Best of luck !

---

### Post by andydaly on 2009-11-14
Now then, had the same problems (as mentioned its a known bug). However managed to sort it today using the following:

[http://sourceforge.net/projects/huaweie1750ubun/files/Huawei_E1750.sh/download](http://sourceforge.net/projects/huaweie1750ubun/files/Huawei_E1750.sh/download)

Basically some sound geezer has made a shell script running the various fixes and workarounds to enable this to work. I just ran it, rebooted and plugged it in. Working a treat now.

Hope it helps as much as it did for me.

I was the 2nd person to Download this from sourceforge so its very new.

Thanks,
Daly.

---

### Post by grahamdoel on 2010-02-21
Brilliant!  Thanks this solved my problem with this modem with no fuss.

---

### Post by st0nes on 2010-02-25
> **pdc said:**
> this is a very good point jimmers;

as I understand it, the VMC software will allow a 3G modem to connect to any network; (ie doesn't have to be vodafone);

the VMC software is built with ozerocdoff; (rather than usbmodeswitch) to achieve the same thing of flipping a device from CD-Rom state to modem state

I've tried to install this, but I get the following error:-

Error: Dependency is not satisfiable: oxerocdoff

I installed ozerocdoff, then tried to install vodafone-mobile-connect again with the same result.  How can I get this working?

---

### Post by Antonio Tavares on 2010-03-31
I've tryed a lot of "solutions" to this bug, and lost days trying to put this to work. My time is valuable, but I'm a stuborn guy. The solutions here that work (**usb-modeswitch**), don't work for long (maybe the updates are ruining the configuration?). It stops working misteriously and you're out of Internet again.

I came from Windows to Linux because it's quality is better, and it's open nature creates value for all humanity.

What I regret is that **Ubuntu is not developing any kind of quality solution for 3G fones**. Maybe they think the capacity of an operating system to connect to the Internet is not important?!!!

Supplyers like Huawey are also not doing enough to help their users. They are satisfied that it works on Windows and Mac OS. All the rest is meaningless to them.

I had a project to create a router using Linux to load balance Internet access between ADSL and 3G, but with no proper drivers it will have to wait...

---

### Post by itsols on 2010-09-06
The E1750 seems to be among the only few dongles in my local market and I need to get one urgently.

Does anyone have trouble working it with Lucid (10.4) ?

Any answer would be highly valued!

---

### Post by fantasmino on 2010-09-06
> **itsols said:**
> The E1750 seems to be among the only few dongles in my local market and I need to get one urgently.

Does anyone have trouble working it with Lucid (10.4) ?

Any answer would be highly valued!

It works fine, finally!:D
Install the package usb-modeswitch (I don't remember if you have to reboot after this), put in the E1750, left click on the network manager icon in the tray and choose the new mobile network!:popcorn:

---

### Post by itsols on 2010-09-07
That's GREAT news.
THANK YOU !!!

---

### Post by itsols on 2010-09-08
Observing the practice of many, I just installed usb-modeswitch even before I bought my dongle.

Then I plugged in my dongle - E1750.

It works like a breeze out of the box!

Just thought I'd share this. BTW, My OS is Lucid (10.4)

Cheers!

---

### Post by itsols on 2010-11-24
New problem!

The same E1750 does NOT work with Ubuntu 10.10

I've got the modeswitch installed

---

### Post by fantasmino on 2010-11-25
> **itsols said:**
> New problem!

The same E1750 does NOT work with Ubuntu 10.10

I've got the modeswitch installed

Very strange, I'm using 10.10 and it works fine just plug in it. I'm using it just now...
Doesn't the mobile broadband appear left clicking the wi-fi icon in the tray?
Really, I used 20 seconds to configure it.

---

### Post by itsols on 2010-11-25
Removed usb-modeswitch and reinstalled it.

Plugged in the modem.

reconfigured (only the) user name.

It works - Thanks for your feedback!

---

### Post by fantasmino on 2010-11-25
Great! :popcorn:

---

