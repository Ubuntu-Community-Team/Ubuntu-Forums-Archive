---
title: "Securing a wireless network"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by khaar_nabash on 2011-09-22
Hello everyone! This is my first post on ubuntuforums and I am sorry if I posted this in the wrong section or did anything wrong. 

Anyways here's my problem:

I have a dlink WBR-1310 router, with 4 computers (2 desktop 2 laptop) and an Ipod Touch connecting to it wirelessly. I have enabled the hidden SSID option and have set a WPA-2 21 character password. So a couple of days ago my connection was a bit slow, so I went to the dlink settings and noticed a blackberry who was leeching on my wireless. I did everything to get him off my wireless with no success: MAC filtering, resetting, changing password, etc...
So running out of ideas, I decided to post my problem on yahoo answers, but i didn't get any useful answers. Knowing that you guys are very good with those kind of things, i hoped that someone on this forum could help me kick that hacker out of my wireless connection. Thanks to everyone who took their time to help me.

---

### Post by Dangertux on 2011-09-22
Ok first things first, change your WPA2 passphrase, at 21 characters I find it unlikely that a WPA2 key was cracked (unless it's been the same for a VERY long time)

Just change the WPA2 key and reset the access point, also may wish to change any login credentials (admin password) associated with the access point.

Also of interest

-- Hiding your SSID  (essid) doesn't really do anything, if they are actually cracking your WPA2 Key (I doubt it) they can see you anyway.

-- Mac filtering is good but focus on your encryption, that is your REAL security.

-- Did you give the pass phrase to anyone? Is it your name or any personal information about you? (meaning could someone guess it)

---

### Post by khaar_nabash on 2011-09-23
Well I did everything you just said,  changed the network name, changed the passwor, changed the admin/user name and password (the one that we use to connect to the router settings) MAC filtering (allowing only computers that I know, or denying access to the blackberry), reset the AP,  the guy is still connecting to the network as soon as I enable wireless. Could it be a glitch or something? because I honestly don't know how he's managing to hack back in my wireless network in less than 30 sec after basically changing everything on it (passwords, names etc..).

---

### Post by Dangertux on 2011-09-23
> **khaar_nabash said:**
> Well I did everything you just said,  changed the network name, changed the passwor, changed the admin/user name and password (the one that we use to connect to the router settings) MAC filtering (allowing only computers that I know, or denying access to the blackberry), reset the AP,  the guy is still connecting to the network as soon as I enable wireless. Could it be a glitch or something? because I honestly don't know how he's managing to hack back in my wireless network in less than 30 sec after basically changing everything on it (passwords, names etc..).

Are you sure someone in your house doesn't have a blackberry you don't know about?

The reality is quite simple, with current technology with a STRONG WPA2 key there is no way that they could be breaking into the network that quickly. So I think it's either a glitch or someone knows the key and is messing with you. I would ask your family, roommates, or whatever lives with you if they have a blackberry.

---

### Post by khaar_nabash on 2011-09-23
> **Dangertux said:**
> Are you sure someone in your house doesn't have a blackberry you don't know about?

The reality is quite simple, with current technology with a STRONG WPA2 key there is no way that they could be breaking into the network that quickly. So I think it's either a glitch or someone knows the key and is messing with you. I would ask your family, roommates, or whatever lives with you if they have a blackberry.


Thanks for the help, I've asked my family and apparently my brother's friend forgot his blackberry in our house and my brother was using the wireless network on that blackberry to get on the Internet. Thanks again for your help and I'm sorry, I should have asked everyone if there was a blackberry before posting here

---

### Post by Dangertux on 2011-09-23
> **khaar_nabash said:**
> Thanks for the help, I've asked my family and apparently my brother's friend forgot his blackberry in our house and my brother was using the wireless network on that blackberry to get on the Internet. Thanks again for your help and I'm sorry, I should have asked everyone if there was a blackberry before posting here

Nothing to be sorry about :-)

I'm rather glad to hear that I didn't miss some ground breaking technology that can crack WPA in 30 seconds :-)

Glad it all worked out.

---

