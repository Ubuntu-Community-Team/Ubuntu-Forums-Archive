---
title: "Killed my network manager after deleting login.keyring"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by Dorrax on 2010-04-20
I couldn't get wireless to work when it needed WPA2 encryption. I found some suggestions that I delete the login.keyring file, I did that. It didn't fix the network manager. It just made it not work at all. Even with wired connections it just sits there with the thing spinning around and never lets me actually get on the internet, saying it's waiting for an address or something. I tried to purge network manager, maybe reinstall it, but then it occured to me I can't use apt if I can't get online.... 


Also, I'm using linux mint 8, which isn't ubuntu, but is pretty close, if that matters.

NOTE: I am not above brute force methods using command line and scripting if that is what it takes. On a previous installation of ubuntu 8.04, it stopped mounting USB drives and SD cards, so I mounted them manually. Also had to use python to write volume control scripts for OSS because it stopped reading the volume buttons on my laptop. If you know a way to use command line to get online, I would be willing to try.

---

### Post by pastalavista on 2010-04-20
Have you tried changing your router to use WEP encryption? If that doesn't work, post the output of these terminal commands...```
ifconfig

iwconfig
```also, did you restore the keyring file?

---

### Post by pastalavista on 2010-04-20
One more trick... open Synaptic settings/repositories and put your Mint CD in the drive and check 'Use CD as repository' or something like that, to reinstall the Network Manager.

---

### Post by Dorrax on 2010-04-20
It's for my university's wireless network. Their IT webpage specifically states that linux is not supported, and if it weren't for the math department being nicer about it, I wouldn't have any clue to get on at all.

---

