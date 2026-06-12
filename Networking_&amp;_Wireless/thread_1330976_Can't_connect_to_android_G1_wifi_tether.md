---
title: "Can't connect to android G1 wifi tether"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by paulisdead on 2009-11-18
So I rooted my android G1 phone, and installed cyanogen and the wifi tether app.  My laptop, with network-manager, refuses to connect to it as an access point.  It doesn't give an error, just tries to connect for a minute or so, and fails.  I don't see any connection attempts on my phone.  Just for troubleshooting, I disabled encryption, and removed the password, and still can't get a connection.  I have tried manually configuring the connection as ad-hoc, and still get the same thing.  I'm not sure where network manager would store logs of any useful data.  The laptop's a dell latitude d430 with an intel mini-pcie wifi card.  I want to say it was 3945abg, if memory serves.  The laptop works fine on the access points at home and at work.  It's a clean, not even 2 week old install of Karmic.

I have not tried taking the interface out of network manager's control, and manually connecting.  I use a few other wifi access points, so I really don't want to do that.  I also haven't given wicd a shot for this yet.

As a side not, USB tethering works great.  I just plug the phone in with USB debugging turned on, on the phone, and Ubuntu starts using it without having to do a thing.  So that's a plus.  I'll probably use the USB Tethering more, since it saves on battery, but it would be nice to have wifi tethering, because more than one computer can use it.

---

### Post by paulisdead on 2009-11-19
gonna give this a bump.

---

### Post by dhaus111 on 2010-03-04
anybody ever find a solution to this? I'm having the same problem with the sprint hero...

---

### Post by pmknutsen on 2010-03-05
As you, I rooted my Android G1 and installed the android-wifi-tether app. The latter seems to run fine but I cant connect to it from my Dell Latitude E6400 running Ubuntu 9.10 Karmic Koala. In the FAQ for the android app it does mention something about Ubuntu not being good at connecting to adhoc networks. I'm unable to verify this and searches at google yielded nothing to help in this direction;

[http://code.google.com/p/android-wifi-tether/wiki/FAQ](http://code.google.com/p/android-wifi-tether/wiki/FAQ)

There are suggestions to work arounds in the FAQ above. Did you try any of those, and did it work?

For now, I have the same problem. In the network manager GUI I configured my android wireless as an adhoc network. The computer seems to see the phone, as it appears in the list of Available networks. I cannot, however, connect. It tries, then silently fails after about 30-60 sec. Will try more, but do post your solution if you find one.

---

### Post by paulisdead on 2010-03-05
I know I tried everything in the FAQ.  It hasn't been a huge concern for me, since USB tethering works, and is friendlier to my battery.  Cyanogen has a similar program to JF, and I've whitelisted the tethering app, so it's not that.

---

### Post by pmknutsen on 2010-03-05
Can you give a quick run-through how to set up Ubuntu <-> G1 tethering via USB?

---

### Post by paulisdead on 2010-03-05
I just installed the cyanogen modded firmware on my phone, enabled USB debugging in the settings of the phone, and tethering as well, and plug it into an ubuntu box.  It works great, and required no additional configuration under ubuntu 9.10 or 10.04.  No idea how to get it working with an unmodded firmware, though.  Installing cyanogen is a bit of a procedure and they've got a wiki on his site.

---

### Post by rhosea1 on 2011-06-19
Guess this answer is 4 years in the making. The problem I had with android tethering was the fact that the phone was in ad-hoc mode. I think Network Manager is not handling ad-hoc mode properly. I was able to connect to the phone with Win 7 without any additional config on the same laptop. Rebooting into Ubuntu with the same hardware gave me problems. So, I used 'iwconfig <adapter> mode ad-hoc' with NM wireless disabled. One wireless adapter's driver (Atheros) wouldn't let me set this mode, but my Cisco (linksys) had no problems. Then started NM back up. Logged in fine and runs good... Found the problem, but only a work around submitted.

---

### Post by petegw42 on 2011-12-01
I have a rooted LG Ally, running wifi tether 3.1-beta7.  I know, my phone sucks.  But if it had twice the processor speed I would love everything about it.

The Ally is not a supported device in wifi tether so I am using "generic" as my device profile and "auto" as my setup method.  128 bit WEP.  

I can connect an iPad and my laptop running Windows 7.  Cannot connect my laptop when running Ubuntu 11.10 (though it can see the network) - nor, for some reason, an HTC Sense running Android 2.3.  (Maybe Android's problem is related to Ubuntu's in that Android is Linux-based?)

Tried rhosea1's workaround but got "SET failed on device wlan0; Operation not supported."  (This was when running the command as sudo - first time it told me the operation was not "permitted.")  Any suggestions?

---

### Post by petegw42 on 2011-12-01
Oh - duh.  I think the laptop's wlan adapter is an Atheros.  So the original post answered my question (sort of).

---

### Post by paulisdead on 2011-12-01
Uhm wow, I can't believe this thread's still kicking around.  I've had time to get a g2x with cyanogenmod, and the wifi tethering has been working great under ubuntu.  It's been so long since I had the g1, but I think tethering under cyanogen eventually worked for me with later releases.

I'd see if cyanogen supports the Ally, or if somebody else has a custom version of android that includes tethering.  Stock firmware kind of sucks ;)

---

