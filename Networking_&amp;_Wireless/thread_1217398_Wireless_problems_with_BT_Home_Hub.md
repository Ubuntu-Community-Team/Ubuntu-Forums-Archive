---
title: "Wireless problems with BT Home Hub"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by Stormrider83 on 2009-07-19
Hey,

I have searched for solutions to this problem with no sucess but I do apologuise if it has been asked elsewhere.

I have installed Xubuntu on a Acer TravelMate 2200. Everything worked fine apart from the wireless. I have installed Ndiswrapper and my network shows up in Network manager. I can connect to it if I turn WAP encryption off at the router however it wont connect with WAP encryped even if I type in the correct password. The router itself is a BT Home hub which I can connect to with my other pc both encrypted and not which is running Vista.

Any ideas? I am a complete Linux Newbie btw.

---

### Post by Stormrider83 on 2009-07-20
If there is any further information needed please let me know

---

### Post by glyndavies on 2009-07-24
I've got the same problem, and would be pleased if it can be resolved

---

### Post by superprash2003 on 2009-07-24
have you tried with a WEP key?

---

### Post by Cyked on 2009-07-24
Try WEP just to test as superprash2003 suggested.  I assume you mean WPA....  Make sure you are selecting the correct options when setting up wireless (PSK/AES, that you are selecting WPA or WPA 2, etc).  Maybe try a very short passphrase, like >= 6 characters for WPA.

---

### Post by glyndavies on 2009-07-25
I've been trying mainly with WEP as that's the default on the Home Hub, and it works happily with Vista, but I have also tried WPA. On WEP it knows the Home Hub is there, but just keeps asking for the key.

---

### Post by tipiglen on 2009-07-25
I have similar problems.  Working right now in office connected wirelessly in xubuntu, and can connect via long ethernet cable with my ubuntu (jaunty) laptop, but cannot get the same laptop (nor my son's Vista machine) to connect wirelessly, except directly near the hub.

I have put a WAP on the end of an ethernet cable plugged into the BTHub, and the signal is there, but the computers won't connect.  The Ubuntu one keeps asking for the key, and the Vista pile-of-crap says the connection is configured 'wrong'.

The old machine I'm on at the moment asks for the 'keyring' password, and accepts the admin password I set on the router.  I don't see any sign of my ubuntu laptop asking for the keyring password, but I've tried that as an alternative to the recurring requests...

---

### Post by Cyked on 2009-07-26
How long in the phrase you are using to generate the HEX key?  Try something <= 6 characters as a test.

---

### Post by glyndavies on 2009-07-26
I seem to have solved my difficulty.  As a beginner I was testing Ubuntu using a USB flash drive, but when I set up a full dual boot system the wireless connection set up without any problems!

---

### Post by ColdT on 2009-08-04
My problem is similar, ive got a wpc54g v5 wireless card running, correct drivers were installed using ndiswrapper, the homehub is visible in network connections but when i try to connect it keeps coming back asking for the correct password...the password is correct, is in wep but just will not connect!  Getting sick of tripping over my ethernet cable.Can anyone solve this annoying problem? Tune in next week to find out.

---

