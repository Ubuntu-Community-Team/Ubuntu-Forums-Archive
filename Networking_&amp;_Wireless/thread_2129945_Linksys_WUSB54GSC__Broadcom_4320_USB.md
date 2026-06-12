---
title: "Linksys WUSB54GSC / Broadcom 4320 USB"
date: 2013-03-27
forum: Networking &amp; Wireless
---

### Post by dude1 on 2013-03-27
Edited

---

### Post by chili555 on 2013-03-27
Ndiswrapper is seldom the correct solution, especially for a Broadcom. My conviction is increased when you say it works perfectly in the netbook. Let's do some diagnostics. Please insert the device, open a terminal and run and post:```
lsusb
```

---

### Post by dude1 on 2013-03-27
Edited

---

### Post by chili555 on 2013-03-28
Your device uses the rare and elusive module *rndis_wlan.* There are a few driver parameters available. Let's try the most likely sounding one:```
sudo modprobe -r rndis_wlan
sudo modprobe rndis_wlan roamdelta=2
```This reduces the tendency for the device to try to roam to another network, at which point it disconnects,looks around, decides home was best and asks for the password *AGAIN!* Sound familiar?

If it helps, we can write one file to make it persistent.

There are a couple of other things we can try. May I safely assume this a stay-at-home computer that you simply want to stick on your home router? We can probably tell Network Manager who we want to default to.

---

### Post by dude1 on 2013-03-28
Edited

---

### Post by chili555 on 2013-03-28
Let's try a different approach. Please run:```
iwconfig
```When you know the MAC address of the router, I suggest you tell Network Manager to connect *ONLY* to it by specifying it in BSSID here. Please see attached. Hopefully, then the device will lock to your router.

---

### Post by dude1 on 2013-03-28
Edited

---

### Post by chili555 on 2013-03-28
How is your network configured?```
nm-tool
```

---

### Post by dude1 on 2013-03-28
edited

---

### Post by chili555 on 2013-03-28
> ATT7341: Infra, 20:4E:7F:627D, Freq 2412 MHz, Rate 54 Mb/s, [COLOR="#FF0000"]Strength 42[/COLOR] WPA2 This may be a big part of the problem. Is there any transmit strength setting in the router? Please see attached. Also, we might try another driver parameter:```
sudo modprobe -r rndis_wlan
sudo modprobe rndis_wlan roamtrigger=-80
```

---

### Post by dude1 on 2013-03-28
Edited

---

### Post by PARO on 2013-03-28
I had a similar card Linksys WUSB54G and in the past I know I had to use ndiswrapper to get it working.  Squeeze & Lucid both worked with it out of the box though, but at some point Lucid stopped working with it for me, and I've been using Debian exclusively on that computer ever since.  I've tried a few other distros on there and the connection varies quite a bit.  Some will disconnect and keep asking for a password, others (ubuntu for me) will get a steady 428 bytes per second reported.  Anyway, are the versions of Ubuntu the same on your netbook and desktop?

---

### Post by dude1 on 2013-03-29
Edited

---

### Post by chili555 on 2013-03-29
> **dude1 said:**
> I didn'y specifically compare both versions. I think for Netbooks its slightly different than a Desktop but I really don't know more than that. The netbook is updated so I think they should be more or less the same. I just figured it would be something minor to tweek, but not the case! ARRG! My Netbook does have ndiswrapper kernel, I did see that the other day. I tried it on this one but didn't do anything. I wonder if the built in network on the motherboard is taking some kind of prioity on resorces over the USB wireless?To utilize ndiswrapper, you need the ndiswrapper packages *AND* the .inf and .sys files from Windows XP appropriate to your architecture; either 32- or 64-bit. 

Signal strength of 50 is better than 42. 

Let's compare the desktop and the netbook. What do each say about:```
arch
uname -r
nm-tool
```Thanks.

---

### Post by dude1 on 2013-03-29
Edited

---

### Post by chili555 on 2013-03-29
I prefer that you observe the Code of Conduct. Please edit your post so you don't get an infraction.

---

### Post by PARO on 2013-03-29
I'm not sure if it's any different today, but it took a bit of commands to set up ndiswrapper for the card, and like chili said, you need the windows driver files (you can grab them off the installer cd).  I followed a really good howto in the past for this, but searching couldn't find it, but there are many other guides out there if you wanted to try your luck. I wasn't clear from reading your posts if you thought ndiswrapper would auto-configure the card and connect, or if you had already tried setting something like this up.

---

### Post by dude1 on 2013-03-29
Edited

---

### Post by PARO on 2013-03-29
Hm.. the password that it's asking for is definitely the Wireless Key right, and not the password to the keyring used to encrypt your wifi info?  Sometimes you need to initially input that password to gain access I believe...  but it should be OK, since you were connecting and getting signal strength reported.. hm..

---

### Post by dude1 on 2013-03-29
Yes its asking for the Key, like its trying to connect but doesn't and keeps asking. Maybe its a security thing where there's some kind of missing protocol / handshake. I keep searching around lots of posts almost no "I fixed it" posts.

---

### Post by dude1 on 2013-03-29
Maybe this is an authentication problem??? so I looked in my sys.log and seen this. Not sure exactly what its telling me...

Mar 29 10:54:57 dad-MS-7252 kernel: [  575.169083] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 29 10:54:57 dad-MS-7252 kernel: [  575.169088] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Mar 29 10:54:57 dad-MS-7252 kernel: [  575.169093] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 29 10:54:57 dad-MS-7252 kernel: [  575.169097] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Mar 29 10:54:58 dad-MS-7252 NetworkManager[989]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar 29 10:55:04 dad-MS-7252 wpa_supplicant[1030]: wlan0: Trying to associate with 20:4e:7f:62:d7:dd (SSID='ATT7341' freq=2412 MHz)
Mar 29 10:55:04 dad-MS-7252 NetworkManager[989]: <info> (wlan0): supplicant interface state: scanning -> associating
Mar 29 10:55:05 dad-MS-7252 kernel: [  582.988887] rndis_wlan 1-3:1.0: wlan0: media connect
Mar 29 10:55:05 dad-MS-7252 wpa_supplicant[1030]: wlan0: Associated with 20:4e:7f:62:d7:dd
Mar 29 10:55:05 dad-MS-7252 NetworkManager[989]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Mar 29 10:55:06 dad-MS-7252 NetworkManager[989]: <warn> Activation (wlan0/wireless): association took too long.
Mar 29 10:55:06 dad-MS-7252 NetworkManager[989]: <info> (wlan0): device state change: config -> failed (reason 'no-secrets') [50 120 7]
Mar 29 10:55:06 dad-MS-7252 NetworkManager[989]: <info> Marking connection 'ATT7341 ' invalid.
Mar 29 10:55:06 dad-MS-7252 NetworkManager[989]: <warn> Activation (wlan0) failed for connection 'ATT7341 '
Mar 29 10:55:06 dad-MS-7252 NetworkManager[989]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [12

There is more.. like it runs through a bunch of frequencies trying to find a channel to connect but never does.

I installed wicd to try it out. It hangs up at "validating Authentication" then finally gives up.

---

### Post by dude1 on 2013-04-01
Looks like everyone gave up.
 I'm guessing this must be some sort bug or maybe the new releases dropped support for wifi on desktop. 
I was fooling around with removing some of my network apps and removed all of them. So I ended up re-installing. I figured maybe this might fix the problem. But actually made it worse. The broadcom is not recognized any more by the NM.
It does seen my new Netgear N150 but it is stuck doing the same fail authenticating.
Anyone have any ideas?

---

