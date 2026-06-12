---
title: "Sprint 3G/4G modem"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by wtrumbly on 2010-01-03
I need to find a driver for a Sprint 3G/4G modem. I am running 9.04.

Sprint lists this as a U300 but the actual part is a Franklin Wireless FW300DOWMX.

lsusb shows this as 
      ID 16d8:6002 CMOTECH Co., Ltd.
and
      ID 0409:005a NEC Corp. HighSpeed Hub

so my box can see the part.

If I can get just the 3G working that would help a lot. I would be happy to do beta, even alpha, testing.

Thank you - BillT

---

### Post by imcdona on 2010-01-06
I would like to use the device on my Ubuntu box as well. The only way I can use it currently is by connecting it to a CradlePoint PHS300 and then having Ubuntu connect to the PHS300 via WiFi.

---

### Post by Terc on 2010-01-11
Has anyone had any luck with this?  I'm assuming the device id is simply not added yet.  I'm actually working with the u301, but I assume they're similar.

I don't really want to waste my time on it, I'd rather stick with 3G only for the time being since 4G is barely available anywhere.  However, the purchasing department wants to buy the card with the bigger number (4G is more better than 3G, _obviously_) so, I'm being forced to take a look at one.

Anyone with some experience or suggestions, I'd love to hear your thoughts.

---

### Post by BARlotta on 2010-01-16
I've done a lot of searching and haven't found much on whether linux supports either of these modems yet (u300/u301).  My current sprint contract has wrapped up so I am looking to upgrade to the faster 4G/WiMax modems.

So add me to the camp of folks wondering if either of these modems will work with ubuntu/network manager.

---

### Post by alexfish on 2010-01-16
hi

also try to look up this device to no avail

There is a site here worth looking at it also has a forum

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Link to [ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")
[URL="http://www.draisberghof.de/usb_modeswitch/bb/"]
[/URL]

---

### Post by Lakota on 2010-01-27
Hi folks.  I'm new to all this and was looking around to see if anyone had trouble with Sprint/Sierra wireless satellite modems.  I did call Sprint and was told that all Sprint modems are compatible with Linux, but does not have an installer like it does for Windows.  It has to be done manually.  
 
I was instructed by a Tech at Sprint to go to the website at:
 
sprint.com/downloads
 
Click Mobile Broadband Devices,
Click the picture of your device,
Download the document to a file.
 
The document will give you explicit instructions as to the set up.

---

### Post by BARlotta on 2010-01-28
> **Lakota said:**
> Hi folks.  I'm new to all this and was looking around to see if anyone had trouble with Sprint/Sierra wireless satellite modems.  I did call Sprint and was told that all Sprint modems are compatible with Linux, but does not have an installer like it does for Windows.  It has to be done manually.  
 
I was instructed by a Tech at Sprint to go to the website at:
 
sprint.com/downloads
 
Click Mobile Broadband Devices,
Click the picture of your device,
Download the document to a file.
 
The document will give you explicit instructions as to the set up.

As far as I can tell those directions are for non-wimax modems.  I did something similar for my u727 in previous versions of Ubuntu but the last few releases are able to detect the u727 out of the box.  I am mostly wondering if the u300/u301 also work out of the box or not.

Download links for the u301 do not have a linux reference:
[http://www.nextel.com/en/software_downloads/mobile_broadband/sprint_u301.shtml]("http://www.nextel.com/en/software_downloads/mobile_broadband/sprint_u301.shtml")

Neither does the u300:
[http://www.nextel.com/en/software_downloads/mobile_broadband/sprint_u300.shtml]("http://www.nextel.com/en/software_downloads/mobile_broadband/sprint_u300.shtml")

---

### Post by rabbit20 on 2010-03-10
I just got the sprint u300 modem also and i am running ubuntu 9.10...does not register it being there...i am still a noob with ubuntu, i know enough to get myself in trouble but it appears the card is still not supported.

---

### Post by BARlotta on 2010-03-10
> **rabbit20 said:**
> I just got the sprint u300 modem also and i am running ubuntu 9.10...does not register it being there...i am still a noob with ubuntu, i know enough to get myself in trouble but it appears the card is still not supported.

Is the device not showing up at all?  What happens when you run the following commands:
```
lsusb
```
```
lspci
```
```
dmsg
```

Sometimes with my u727 I need to restart hal for it to get picked up properly.  Have you tried running:
```
sudo restart hal
```
after plugging in the device?

---

### Post by rabbit20 on 2010-03-14
got it working...:p Followed the instructions from this site to the letter 
[http://jebus.nu/tech-corner/sprint-u300](http://jebus.nu/tech-corner/sprint-u300)  and its up and running now

---

### Post by BARlotta on 2010-03-14
Awesome news.  I'm going to have to run out and get one of these now!

---

### Post by Rexor on 2010-03-25
> **rabbit20 said:**
> got it working...:p Followed the instructions from this site to the letter 
[http://jebus.nu/tech-corner/sprint-u300](http://jebus.nu/tech-corner/sprint-u300)  and its up and running now

I followed those direction substituting my U301, no go. I made sure to change the vendor ID to reflect the U301 as well, kinda stumped now.

---

### Post by BARlotta on 2010-03-25
> **Rexor said:**
> I followed those direction substituting my U301, no go. I made sure to change the vendor ID to reflect the U301 as well, kinda stumped now.

I was able to get the u301 I purchased yesterday working following those instructions.  It seemed slightly "flaky" in that it worked 8 out of 10 times.  I had more luck not having the modem plugged in while the computer started up.

My /etc/udev/rules.d/50-u301modem.rules looks like this
```

ACTION!="add", GOTO="3G_End"

SUBSYSTEMS=="usb", ATTRS{idProduct}=="6008", ATTRS{idVendor}=="16d8", RUN+="/sbin/modprobe usbserial vendor=0x16d8 product=0x6008"

LABEL="3G_End"


```

---

### Post by Torxbit on 2010-03-25
The modem comes with a y USB cable that needs to be plugged in.  The card will work if you plug it in but as soon as you attempt to use the device it can die.  I can get it to work fine as a 3G device.  Has anyone gotten the 4G modem to work?

---

### Post by BARlotta on 2010-03-25
> **Torxbit said:**
> The modem comes with a y USB cable that needs to be plugged in.  The card will work if you plug it in but as soon as you attempt to use the device it can die.
I haven't used the supplied cable, just plugged it directly in.

> **Torxbit said:**
> I can get it to work fine as a 3G device.  Has anyone gotten the 4G modem to work?
I only have a green light (3G) not blue light (4G) so not sure if I can test this (in the DC metro area, so I should get 4G here soon - will try with a OS X when I get the chance)

---

### Post by pcfixitguy on 2010-04-30
I got my Sprint U300 working in Ubuntu 10.04 using the instructions listed on that website too.  However, I live in a 4G area (Atlanta), but I only get a green LED (3G) on the modem.  If I use the U300 in Windows with the SprintView software, I can connect to the 4G network.  Does anyone know how to switch the U300 to 4G mode in Ubuntu?

Thanks

---

### Post by BARlotta on 2010-05-01
> **pcfixitguy said:**
> I got my Sprint U300 working in Ubuntu 10.04 using the instructions listed on that website too.  However, I live in a 4G area (Atlanta), but I only get a green LED (3G) on the modem.  If I use the U300 in Windows with the SprintView software, I can connect to the 4G network.  Does anyone know how to switch the U300 to 4G mode in Ubuntu?


From everything I've been reading it looks like WiMax/4G is not supported by NetworkManager yet.

[a launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/509843")

[Potential Solution]("http://ubuntuforums.org/showthread.php?p=8677756"), haven't tried it though...

---

### Post by tech721 on 2010-05-01
> **BARlotta said:**
> From everything I've been reading it looks like WiMax/4G is not supported by NetworkManager yet.

[a launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/509843")

[Potential Solution]("http://ubuntuforums.org/showthread.php?p=8677756"), haven't tried it though...

cants get it to work any luck anyone?

---

### Post by beerhat on 2010-05-04
> **rabbit20 said:**
> got it working...:p Followed the instructions from this site to the letter 
[http://jebus.nu/tech-corner/sprint-u300](http://jebus.nu/tech-corner/sprint-u300)  and its up and running now

I did this too on my 9.10 (64 bit) box.  After a reboot, my u301 works/connects fine but only stays connected for exactly one minute. Then the device basically disappears.  

Very  peculiar, and such a pain. 

Dan
:confused:

---

### Post by labanjohnson on 2010-05-04
I've got the 3G portion working but really want to know what 4G is like!

What's it gonna take? I'm in Houston on Sprint.

---

### Post by p110011 on 2010-05-05
I have a Clear 4g USB card and the chip is made by Beceem. Word from Clear reps. is there are drivers on the way. There are mobile routers that you can plug your Sprint cards into and use wifi. I'm using a Cradlepoint PHS300cw. If you get an un-branded (non Clear or Sprint) PHS300, make sure it has Ver. 2 hardware, for the 4g.

---

### Post by Deval on 2010-05-05
I'm totally new to Linux, so please forgive my newbie questions, but here is my situation.

I have a friend who has a Dell mini Inspiron 910, running Ubuntu 8.04 (I believe).

I'm trying to configure the u301 for her, and I'm stuck, and need some assistance. Here is what I did:

Source Site: [http://jebus.nu/tech-corner/sprint-u300](http://jebus.nu/tech-corner/sprint-u300)

I opened a terminal window, and typed in
```
lsusb
```
which outputted
```

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 020: ID 16d8:6008
Bus 004 Device 018: ID 1a40:0101
Bus 005 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0c45:63e5 Microdia
```

Based on what I read in this post:

> 
I was able to get the u301 I purchased yesterday working following those instructions. It seemed slightly "flaky" in that it worked 8 out of 10 times. I had more luck not having the modem plugged in while the computer started up.

My /etc/udev/rules.d/50-u301modem.rules looks like this
```


ACTION!="add", GOTO="3G_End"

SUBSYSTEMS=="usb", ATTRS{idProduct}=="6008", ATTRS{idVendor}=="16d8", RUN+="/sbin/modprobe usbserial vendor=0x16d8 product=0x6008"

LABEL="3G_End"

```


I figure this line is the u301.

```
Bus 005 Device 020: ID 16d8:6008
```

So, I entered this in the terminal window:
```
sudo modprobe usbserial vendor=0x16d8 product=0x6008
```

Now, I'm stuck...not sure what to do next. I hate to sound like a total rookie, but I am when it comes to Linux, been a Windows user my entire life. 

Thank you in advance for any assistance you may be able to provide!

---

### Post by alexfish on 2010-05-06
Hi 

I am assuming the above details are correct::

                                    Open /etc/modules by

Code:

 gksudo gedit /etc/modules

 and add the string


usbserial vendor=0x16d8 product=0x6008

---

### Post by Deval on 2010-05-06
> **alexfish said:**
> Hi 

I am assuming the above details are correct::

                                    Open /etc/modules by

Code:

 gksudo gedit /etc/modules

 and add the string


usbserial vendor=0x16d8 product=0x6008

when I typed in the ```
gksudo gedit /etc/modules
```, I'm prompted for the admin password, which I enter, but nothing else happens after that, I'm left with the terminal window.

I'm beginning to thing the system is maybe locked down by Dell?

---

### Post by pdc on 2010-05-07
alex has helped you with commands that should automate the system; each time it restarts;

perhaps helpful to see if it worked on the first occasion ......... ???

when you do

> sudo modprobe usbserial vendor=0x16d8 product=0x6008

that should; according to this 

[http://jebus.nu/tech-corner/sprint-u300](http://jebus.nu/tech-corner/sprint-u300)

make the device ready to work as a modem;

one way to test that is to type 

> dmesg | grep tty

and if you get ttyUSB0 (or ttyACM0) you should be good to configure ..

..... do you know how to configure .. ???

it is described here

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

half-way down page ............ create a mobile broadband connection ..

---

### Post by Thomas Garman on 2010-05-29
I am running Ubuntu 10.04 and I used the instructions here:

[http://community.sprint.com/baw/message/162432](http://community.sprint.com/baw/message/162432)

This has allowed me to get a broadband connection with my U300 but it seems that it is only a 3G connection (because the indicator light is green).  Has anyone gotten a 4G connection?

Also, it seems slower than if I run it in Vista with the proprietary software that Sprint requires.

---

### Post by kuazar on 2010-06-18
Hello. My cousin has an Aspire One netbook that I installed Karmic on for him. He just got the Franklin u301. I don't have it with me as he is using the u301 now, thanks to some of the posts here. I got to the point where after a minute or so it drops the connection. After having the netbook for three days, and my cousin coming by to see my progress every day, I am convinced that the connection being dropped has to do with Network Manager and Modem Manager. I went to this site [http://www.gnulinux.in/article/ubuntu-910-reliance-netconnect-broadband-modem-huawei-ec1260-networkmanager-works-out-box](http://www.gnulinux.in/article/ubuntu-910-reliance-netconnect-broadband-modem-huawei-ec1260-networkmanager-works-out-box) for a patched Modem Manager and followed the instructions and rebooted. The connection came up at boot but after about 5 mins, dropped again. I then went into /etc/NetworkManager/...(again, I don't have the netbook with me, but the file is in one of the folders) where the "sprint" file is located, and following the wvdial instructions in the Sprint_Mobile pdf entered the baud for 460800 and flow for crtscts. I then rebooted without the u301 connected. Plugged it back in once Ubuntu was back up, and had a steady connection without being dropped for hours. However, if I reboot with the u301 still connected Network Manager will drop it in a few seconds. If I reboot without it connected and then connect the device, it will not drop it, leading to me to believe further that it has something to do with Network Manager and Modem Manager. I don't know if the problem is specific to this device or Broadband devices in general. I also noticed that the conection is slower and download rates jump back and forth from bytes to kb, the highest being in the 40's. My cousin thanks you all as do I. Hope this helps someone...
Peace.):P

---

### Post by kuazar on 2010-06-19
After thought...on reboot I was getting an error about not being able to load cdrom0 when the device was connected, lsusb showed "cmotech", but also "terminus". Thinking that this is the flash portion of the u301. 
Maybe this:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)
or this:
[http://sourceforge.net/projects/cmotech-tools/](http://sourceforge.net/projects/cmotech-tools/)
might help get the device to be seen on reboot?:confused:

---

### Post by chr0n0 on 2010-08-06
> **rabbit20 said:**
> got it working...:p Followed the instructions from this site to the letter 
[http://jebus.nu/tech-corner/sprint-u300](http://jebus.nu/tech-corner/sprint-u300)  and its up and running now

Thank you sooo much for posting this!

Praise jebus!

---

### Post by chr0n0 on 2010-08-12
Any update about getting 4G working? :-)

---

### Post by newadvice on 2010-11-27
*bump

There has got to be a way to put the U301 in 4G mode.

Still researching...

---

### Post by iisaphd on 2010-12-20
This thread seems to have a solution: [http://ubuntuforums.org/showthread.php?t=1383251](http://ubuntuforums.org/showthread.php?t=1383251)

---

### Post by majordilemma on 2012-01-29
i've successfully gotten the 3G to work, but after many hours trying to get 4G running i am left pretty much where I started.  The only thread that I've found about Linux and wimax actualy running was in reference to an Intel model.  It would seem that a future version of NetworkManager might suport it, but a of right now i cannot find anyone who has it the u30x cards working under Linux.What a drag!

---

### Post by majordilemma on 2012-01-29
I found a very promising page on this.

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=591&sid=b96f0174ab2cd7eddb10fd87c2c4be47](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=591&sid=b96f0174ab2cd7eddb10fd87c2c4be47)

The key was to look up the issue by the hex ID found in 'lsusb'

Bus 001 Device 005: ID 16d8:6008 CMOTECH Co., Ltd.

a google search for '16d8:6008 wimax linux' turned it up.

It appears that you need to use AT commands through minicom to switch to 4G.  Unfortunately I can't try it out right now, but i will be attempting very soon.  I have several hours into this, so I'm pretty determined to get it done.

---

### Post by alexfish on 2012-01-31
Hi  majordilemma
for interest . the device mentioned

the link for this driver appears to be

[http://cgit.haiku-os.org/haiku/commit/?id=5ec0ede](http://cgit.haiku-os.org/haiku/commit/?id=5ec0ede)

regards

alexfish

---

