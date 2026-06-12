---
title: "Why do I have trouble connecting to wireless no matter what network manager I use?"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by iRiUX on 2010-03-24
Is it just me that can't seem to connect to any encrypted connection outside of their home?

Whether it be WPA1/2, WEP, whatever... it just doesn't connect. I've tried Knetwork manager, Gnome network manager, wicd, bah..... when will this **** be fixed?.....

---

### Post by Iowan on 2010-03-24
Last time I visited my relatives, my Jaunty laptop managed to connect to their encrypted network.

---

### Post by zepita on 2010-03-24
network-manager-applet from gnome works pretty well

---

### Post by Cabalbl4 on 2010-03-24
It seems that it may be a problem of keyring or non-manager related issue.
Using my laptop I can connect to any network, without problems.
Running ad-hoc WEP at home - also ok.

PS maybe Your autologin option messes up with keyrings? Is an option "available for all users" in network-manager checked? Try to uncheck it.

---

### Post by crlang13 on 2010-03-24
I have had no problems either.

I even got Ubuntu to connect to my Uni's wireless despite the fact that there were only instructions on how to do it through Windows (which is difficult enough) and the university warning that it doesn't support Linux.

I bring my computer everywhere for work and am always connecting to random encrypted networks with no problems.

You may be having a problem with the configuration of the encryption settings or, as others said, with the keyring.  What happens if you change the password of your default keyring to be blank (effectively disabling it and allowing all programs easy access to it)?

---

### Post by debianmike on 2010-03-24
I switched to WICD for some reason and just stuck with it...works just fine

---

### Post by chili555 on 2010-03-24
I have a computer that uses no manager; that is, manual configuration in /etc/network/interfaces and one that uses Wicd and one that uses Network Manager. All work well. My home network uses WPA2 but I have no problems connecting to any network at all, if I have the encryption key. That includes, remarkably, an 802.11a network.

I think some chipset manufacturers and driver developers do not always do the thorough job they should. I especially think WPA and ndiswrapper are extremely touchy, depending on the specific driver (XP, 2000 or whatever) that is wrapped.

---

### Post by iRiUX on 2010-03-25
Well at home I have WPA2 too, that has never been an issue. What has been an issue are the encrypted networks outside.

However, I have upgraded to Kubuntu 10.4 today, and I am hopeful. I don't know what its due to, however, In my house, the distance where i had 5% in 9.10, I now have 55%, and there where I had no connection at all in 9.10, I now have 44% in 10.4 :D

Tomorrow I will try it out on a encrypted network outside my house.

---

### Post by iRiUX on 2010-03-26
Okay, it still doesn't connect to the secure connections, so I'm connected to an unsecure one. However, the signal is so much stronger, its a great improvement. The signal strength is times 10 stronger where ever I go, sitting at the same spot I always sit. Maybe its because of updates in the new kernel, I have no idea, running kernel 32-17 right now.

Is there any site I can read on how to set up a connection without a network manager? I want to use that for the few connections I can't connect to.

---

### Post by c00lwaterz on 2010-03-26
i have problem with wireless using wpa-personal aes. I tried many tutorials and tips but no luck. i use toshiba m900 core 2 duo 2.2ghz with realtek PCIe and realtek wireless LAN

---

### Post by Cabalbl4 on 2010-03-26
WPA is a headache in ad-hoc mode. No luck either, only WEP for now. :sad:

---

### Post by iRiUX on 2010-03-26
> **c00lwaterz said:**
> i have problem with wireless using wpa-personal aes. I tried many tutorials and tips but no luck. i use toshiba m900 core 2 duo 2.2ghz with realtek PCIe and realtek wireless LAN

I have no problem connecting to WPA2-AES at my home, I just select it and it connects. Have you checked whether your modem/router is assigning your laptop an IP... (DHCP), sometimes that fails on my network (also on windows 7) and I manually type in an IP/etc under options.

---

### Post by iRiUX on 2010-03-27
After yesterday's update I can't connect to anything anymore. I couldn't even get into X for some reason... had to do some stuff to get in. But no network connection.

How do I check which networkmanager version I have? Is the one in Lucid, NM 0.8?

---

