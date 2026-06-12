---
title: "Trying to setup very simple home network and need help"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by Love2MeetU on 2009-12-04
I'm generally not ignorant about computers, but have never setup a network before.

OK, my situation is as follows. I have two PCs, both of which I want to be able to use internet, and link to each other other. We've bought Buffalo WLI-UC-G usb wireless and a WHR-AMG54 AirStation. We live in Japan, but my wife (who is Japanese) is not at all technically minded, so can't translate the GUI for the setup, although I've managed to work out some of it. The usb wireless doesn't appear to be functioning, or at least it's not detected. I tried wicd, and that didn't detect them either.

One PC is running on Ubuntu 9.10, the other is using Ubuntu 8.04 (still trying to get it up to 9.10, but kept getting problems).

I've tried lots of different things, been working on this for much of my free time for past 2 weeks, but just assume that I don't know a damn thing. I may have missed some important setting or detail. Is there any way to get these wireless devices to have English language on them? And most important, what can I do to get a network running?

---

### Post by em3raldxiii on 2009-12-04
Hmm, you might be stymied by the USB network device, since (from what I have read), USB wireless + Ubuntu = not very friendly yet.  It will probably depend on the chipset you have on that USB dongle of yours.  So, you might be able to do a command line command *lsusb* to tell you about your connected ethernet device.  Hopefully, it gives you the chipset information and/or other useful stuff.

I'm gonna google your product IDs and see if I can come up with something.

UPDATE:  This dongle uses the RaLink RT2870 chipset (according to another board).

Some good stuff is here:  [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

NOTE:  It looks like the driver for that device should be supported by the kernel, but I can't figure out whether that would include the USB device or not.

Now, if you type in *ifconfig* and you can see your wireless device in there, you might be a lot closer to it working.

---

### Post by Love2MeetU on 2009-12-05
OK, that was a fast reply, thank you very much.

Here's the result of *ifconfig*
> eth0      Link encap:Ethernet  HWaddr 00:15:f2:1c:f6:91  
          inet6 addr: fe80::215:f2ff:fe1c:f691/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:252015 (252.0 KB)  TX bytes:45115 (45.1 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:121.87.197.153  P-t-P:60.56.25.14  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:244618 (244.6 KB)  TX bytes:35109 (35.1 KB)



and for *lsusb*, there was this result
> Bus 001 Device 004: ID 04bb:0c71 I-O Data Device, Inc. 
Bus 001 Device 003: ID 0411:0137 MelCo., Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04fc:0005 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

No idea what most of that means. I'm still doing my own research.

---

### Post by em3raldxiii on 2009-12-05
So that looks to be the issue here; I don't see the device in your ifconfig, nor in your lsusb.  And unfortunately, I don't recognize the devices in your lsusb either - it could be one of Bus 001 Dev 004, or Dev 003, or Bus 002 Dev 002.  I am assuming you ran lsusb while the USB device was plugged in.  I also assume that when you plug in the USB dongle while Ubuntu is up and running, nothing happens?

I'll see what other info I can dig up.

---

### Post by em3raldxiii on 2009-12-05
I also found this page: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo)

Your chipset is at the  very bottom, and it's not looking promising.  At this point, I am thinking if you can afford the $50 (canadian) on a new card, you might consider going that route.  It would be a lot easier.  if you choose to do that, I highly recommend you contact the manufacturer (buffalo in this case I guess), and let them know why you cannot use their product.  Eventually we will get through to these manufacturers and they will start being Linux conscious.

On the other hand, if you are more inclined to keep hammering away at this device, we can probably find a way to make it work ... eventually.

---

### Post by Love2MeetU on 2009-12-06
> **em3raldxiii said:**
> So that looks to be the issue here; I don't see the device in your ifconfig, nor in your lsusb.  And unfortunately, I don't recognize the devices in your lsusb either - it could be one of Bus 001 Dev 004, or Dev 003, or Bus 002 Dev 002.  I am assuming you ran lsusb while the USB device was plugged in.  I also assume that when you plug in the USB dongle while Ubuntu is up and running, nothing happens?

I'll see what other info I can dig up.

Yes, nothing happens.

Just in case, I'm checking the USB plugs etc... Sometimes they get damaged with people putting things in and out all the time, and the PC is a 2-year-old 2nd-hand one.

---

### Post by Love2MeetU on 2009-12-06
> **em3raldxiii said:**
> I also found this page: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo)

Your chipset is at the  very bottom, and it's not looking promising.  At this point, I am thinking if you can afford the $50 (canadian) on a new card, you might consider going that route.  It would be a lot easier.  if you choose to do that, I highly recommend you contact the manufacturer (buffalo in this case I guess), and let them know why you cannot use their product.  Eventually we will get through to these manufacturers and they will start being Linux conscious.

On the other hand, if you are more inclined to keep hammering away at this device, we can probably find a way to make it work ... eventually.

That appears rather worrying..........

Still, if the problem can be solved, it would help others in the same boat. I'll try to contact the manufacturer as well; Ubuntu (and Linux in general) have a very strong following in Japan these days.

---

### Post by Love2MeetU on 2009-12-06
After a bit of testing with trial & error, I've discovered that the USB dongle is this one;

Bus 001 Device 003: ID 0411:0137 MelCo., Inc.

---

### Post by Love2MeetU on 2009-12-14
After trying to fix the problems with the driver for the USB dongle for the past couple of weeks, finally getting somewhere following the tutorial but I'm still stumbling in the dark.

The driver appears now to be installed.

I get this result with iwconfig;
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ppp0      no wireless extensions.

ra0       Ralink STA  

So, next what do I do?

I've never set up a network before, and the wireless side appears complicated.

---

### Post by em3raldxiii on 2009-12-14
Well, that's definitely promising.  First, with the usb id giving us that much, we have one more path.  On the other hand, the Ralink STA thing might be a dead end (I could be dead wrong).  Worth pursuing for sure tho.

Just so you know, many devices like the ones I currently have in my system are automagically installed and configured.  Networking is therefore absolutely simple.  The good news is that once you get your driver & device configured, the rest will be a walk in the park.

I'll try to help where I can.  If I get a chance tomorrow I will do some more scouring of the net for more things to try.  And yes, if we can get this bad boy working it will definitely be a plus for the community.

... I just had a thought,  have you looked into ndiswrapper to make use of the Windows driver?

---

### Post by em3raldxiii on 2009-12-14
Well, that's definitely promising.  First, with the usb id giving us that much, we have one more path.  On the other hand, the Ralink STA thing might be a dead end (I could be dead wrong).  Worth pursuing for sure tho.

Just so you know, many devices like the ones I currently have in my system are automagically installed and configured.  Networking is therefore absolutely simple.  The good news is that once you get your driver & device configured, the rest will be a walk in the park.

I'll try to help where I can.  If I get a chance tomorrow I will do some more scouring of the net for more things to try.  And yes, if we can get this bad boy working it will definitely be a plus for the community.

... I just had a thought,  have you looked into ndiswrapper to make use of the Windows driver?

---

### Post by Love2MeetU on 2010-01-05
After a lot of fiddling around, I finally got the USB wifi dongles working with ndiswrapper. Although the Linux STA2870 driver got them started, later they kept switching off. Using ndiswrapper with a copy of the proprietary driver disc that I'd burned from the main Buffalo site ended up working better.

Unfortunately, although now both PCs have working wifi and can contact the router, the router is not doing it's job otherwise. It won't link the PCs, they can't see each other, and it can't seem to get internet access. I'm unable to work out yet how to change the settings properly as the setup provided is entirely in Japanese, and is so complex & technical it confuses the hell out of my wife and I. Not at all "user-friendly"

I've tried to find an English version, but can't so far

---

