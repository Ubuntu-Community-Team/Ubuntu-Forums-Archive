---
title: "Connecting Android 1.6 to Ubuntu 10.10 via Bluetooth"
date: 2010-09-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by AndyP79 on 2010-09-17
Hi Ya'll,
 Okay, so, this weeks problem. Got me a Bluetooth adapter for my laptop. At the moment, I am running a mostly stock Ubuntu 10.10 and have a MyTouch 3G with Android 1.6
I would like to connect via Bluetooth. I know that I can just plug it in with the USB cable, but, I wnat to do it with Bluetooth. I am not even worried so much about the internet at the moment, as I am trying to transfer music via Banshee, which sees it just fine with USB cable. So far, using the stock Ubuntu application for Bluetooth, I managed to make the laptop and phone pair, but they don't seem to want to connect? I have Googled this, and I can't seem to find one that is either relevant or upto date or the information is not the same. Everything seems to be everyone trying to do Internet, which I am more concerned about my music at the moment. Anyone got any ideas? 
Thanks
AndyP79

---

### Post by uRock on 2010-09-17
Moved to MM testing & discussion.

---

### Post by AndyP79 on 2010-09-19
Bump

---

### Post by autocrosser on 2010-09-19
Not sure about Android, but my Win 6.1 phone wants to be on the "controlling" end of the pair--I can send from the phone to my computer, but it "seems" to be a one-way street---I can't browse the phone from Ubuntu---weird, but it works......

---

### Post by ricsi-pontaz on 2010-09-20
You should try Bluetooth File Transfer application. ([http://www.androlib.com/android.application.it-medieval-blueftp-qAFE.aspx](http://www.androlib.com/android.application.it-medieval-blueftp-qAFE.aspx)).

---

### Post by AndyP79 on 2010-09-20
Okay, so far none of the posts have actually helped or were useful in the first place. In order to transfer files, first I need to get the phone to connect. Second, it is ANDROID, not freakin windows, seriously, did that comment do me any good? It's two different OS for crying out loud!!If you don't have something relevent to say, please don't post and waste space, instead of just wanting to see your words in print. 
 The devices see each other. But do not connect. Anyone with a MyTouch tried to connect to Lucid even? Surely someone has got their Android phone to connect to Ubuntu?

---

### Post by cariboo on 2010-09-20
Remember we are all volunteers here.

We need to do some diagnostic, before any thing else. Is your bluetooth device detected and the proper drivers loaded?

Type:

```
dmesg | tail -n10
```

and post the output in your next post.

---

### Post by jfernyhough on 2010-09-20
> **AndyP79 said:**
> If you don't have something relevent to say, please don't post and waste space, instead of just wanting to see your words in print. Well done. You've just alienated all those who might want to try and help. I was just about to turn on Bluetooth on my Hero running Froyo (that's 2.2 if you didn't know), then I thought, "No, that's not the same version of Android. Although the principle will be the same he'll likely just run his mouth off and call me stupid for trying to help."

---

### Post by AndyP79 on 2010-09-20
> **cariboo907 said:**
> Remember we are all volunteers here.

We need to do some diagnostic, before any thing else. Is your bluetooth device detected and the proper drivers loaded?

Type:

```
dmesg | tail -n10
```

and post the output in your next post.

Allright, here is what I got;

dmesg | tail -n10
[15153.374311]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15153.374317]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15153.374322]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15153.374328]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15153.374333]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15154.210842] wlan0: authenticate with 00:1d:e6:26:dd:c0 (try 1)
[15154.212206] wlan0: authenticated
[15154.212255] wlan0: associate with 00:1d:e6:26:dd:c0 (try 1)
[15154.217784] wlan0: RX AssocResp from 00:1d:e6:26:dd:c0 (capab=0x431 status=0 aid=1)
[15154.217788] wlan0: associated

So, does it tell us anything?

---

### Post by plun on 2010-09-20
FYI
[http://code.google.com/p/android/issues/detail?id=1725](http://code.google.com/p/android/issues/detail?id=1725)

---

### Post by AndyP79 on 2010-09-20
> **AndyP79 said:**
> Allright, here is what I got;

dmesg | tail -n10
[15153.374311]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15153.374317]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15153.374322]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15153.374328]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15153.374333]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15154.210842] wlan0: authenticate with 00:1d:e6:26:dd:c0 (try 1)
[15154.212206] wlan0: authenticated
[15154.212255] wlan0: associate with 00:1d:e6:26:dd:c0 (try 1)
[15154.217784] wlan0: RX AssocResp from 00:1d:e6:26:dd:c0 (capab=0x431 status=0 aid=1)
[15154.217788] wlan0: associated

So, does it tell us anything?


On a quick note, this was done with bluetooth not visible( I am guessing that means not on?) and then when I made it visible, this is the output that I got;
dmesg | tail -n10
[15153.374311]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15153.374317]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15153.374322]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[15153.374328]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15153.374333]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[15154.210842] wlan0: authenticate with 00:1d:e6:26:dd:c0 (try 1)
[15154.212206] wlan0: authenticated
[15154.212255] wlan0: associate with 00:1d:e6:26:dd:c0 (try 1)
[15154.217784] wlan0: RX AssocResp from 00:1d:e6:26:dd:c0 (capab=0x431 status=0 aid=1)
[15154.217788] wlan0: associated
andy@andy-laptop:~$ [15153.374311]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
bash: syntax error near unexpected token `2402000'
andy@andy-laptop:~$ [15153.374317]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
bash: syntax error near unexpected token `2457000'
andy@andy-laptop:~$ [15153.374322]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
bash: syntax error near unexpected token `2474000'
andy@andy-laptop:~$ [15153.374328]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
bash: syntax error near unexpected token `5170000'
andy@andy-laptop:~$ [15153.374333]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
bash: syntax error near unexpected token `5735000'
andy@andy-laptop:~$ [15154.210842] wlan0: authenticate with 00:1d:e6:26:dd:c0 (try 1)
bash: syntax error near unexpected token `('
andy@andy-laptop:~$ [15154.212206] wlan0: authenticated
[15154.212206]: command not found
andy@andy-laptop:~$ [15154.212255] wlan0: associate with 00:1d:e6:26:dd:c0 (try 1)
bash: syntax error near unexpected token `('
andy@andy-laptop:~$ [15154.217784] wlan0: RX AssocResp from 00:1d:e6:26:dd:c0 (capab=0x431 status=0 aid=1)
bash: syntax error near unexpected token `('
andy@andy-laptop:~$ [15154.217788] wlan0: associated
[15154.217788]: command not found


THis looks like a bit more information hopefully

---

### Post by AndyP79 on 2010-09-20
> **plun said:**
> FYI
[http://code.google.com/p/android/issues/detail?id=1725](http://code.google.com/p/android/issues/detail?id=1725)

This definitley hit what I was trying to do. While I am actually trying to just get the initial connection, the end result is having want to do file transfers, but..... Dang, I scanned through most of those posts, and it seems like it has been going on for most the year, and still no real response from Google. 
Amazing that we can make our phone hook up to the internet, yet transfering a simple file is still difficult.

---

### Post by cariboo on 2010-09-20
Is your bluetooth devie seen as wlan0?

This is what I get when I plug in my usb bluetooth device:

```
[24554.198815] Bluetooth: HCI device and connection manager initialized
[24554.198819] Bluetooth: HCI socket layer initialized
[24554.202581] Bluetooth: Generic Bluetooth USB driver ver 0.6
[24554.202790] usbcore: registered new interface driver btusb
[24554.341128] Bluetooth: L2CAP ver 2.14
[24554.341132] Bluetooth: L2CAP socket layer initialized
[24554.388070] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[24554.388074] Bluetooth: BNEP filters: protocol multicast
[24554.405037] Bluetooth: SCO (Voice Link) ver 0.6
[24554.405040] Bluetooth: SCO socket layer initialized
[24554.667799] Bluetooth: RFCOMM TTY layer initialized
[24554.667806] Bluetooth: RFCOMM socket layer initialized
[24554.667808] Bluetooth: RFCOMM ver 1.11
```

---

### Post by cariboo on 2010-09-20
Just to add a little more info I can connect to the internet through my phone, once bluetooth is setup and the phone and computer are paired, the dmesg output should look like this:

```
usb 2-2: new full speed USB device using uhci_hcd and address 5
[ 3714.321160] PPP BSD Compression module registered
[ 3714.356568] PPP Deflate Compression module registered
cariboo@redstone:~$ ping www.google.com
PING www.l.google.com (74.125.53.147) 56(84) bytes of data.
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=1 ttl=53 time=101 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=2 ttl=53 time=123 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=3 ttl=53 time=43.3 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=4 ttl=53 time=66.2 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=5 ttl=53 time=87.9 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=6 ttl=53 time=109 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=7 ttl=53 time=131 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=8 ttl=53 time=51.3 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=9 ttl=53 time=81.2 ms
64 bytes from pw-in-f147.1e100.net (74.125.53.147): icmp_req=10 ttl=53 time=95.8 ms
```

---

### Post by AndyP79 on 2010-09-20
Okay, so I am going out on a limb here, and guessing that my little USB Bluetooth dongle that I bought at Wal-mart is not working? I have saved the package and reciept, so it might be getting returned. What brand Bluetooth dongle do you have? Any suggestions on brands to stay away from?

---

### Post by cariboo on 2010-09-20
I've got an MSI Btoe, I've had it for years, I used to use it with a Nokia cell phone, but that died several years ago, this is the first time I've used it with my Samsung Instinct.

---

### Post by AndyP79 on 2010-09-21
> **cariboo907 said:**
> I've got an MSI Btoe, I've had it for years, I used to use it with a Nokia cell phone, but that died several years ago, this is the first time I've used it with my Samsung Instinct.

Huh? I guess that my little bluetooth dongle must be defective. I am going to get another one this weekend and see if it works better or different and try again...... 
Thanks for the time, I will post on here after the next round.
Cheers

---

