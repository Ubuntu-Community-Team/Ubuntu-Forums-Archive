---
title: "Blacklist confused by additional video card"
date: 2010-11-01
forum: Multimedia Software
---

### Post by ronnielsen1 on 2010-11-01
I have a Dell 2400 that has an onboard Intel  Corporation 82845G/GL video card that I can't turn off in bios. I also  have a nVidia Corporation G98 [GeForce 8400 GS]  that I use which makes  me suffer from the following bug  

>                                                        **Blacklist confused by additional video card      **


[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234)

> djs@scilly:~$ lspci|egrep '(VGA|Display)'
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
01:05.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
 The Intel card is blacklisted in Intrepid-updates. However, I am  using the nVidia card, not the Intel card. The blacklist check in  /usr/bin/compiz just checks for the presence of a blacklisted card, not  whether that card is in use, so I see:
 Checking for Xgl: not present.
Blacklisted PCIID '8086:2562' found
aborting and using fallback: /usr/bin/metacity


That's not from me but it's real close. 

I've tried [this fix ]("http://art.ubuntuforums.org/showthread.php?t=1467202")and I couldn't find a string even close so it didn't work for me. 

> sudo apt-get install ghex
sudo ghex2 /usr/bin/compiz Now search for the ASCII string "8086:2562" (minus quotes, of course), and change it slightly - I changed the 2 to a 3.

I have the same graphics card (8086:2562) built into... something I  can't take out (don't quite remember what), but I also have a PCI NVIDIA  card that I actually use, so the fact that the Intel card keeps me from  using Compiz is quite annoying.


Will other non-debian distros suffer from this bug or can I install an earlier version of compiz? I have the nvidia driver installed beautiful but no compiz and I really would like to have it

[CENTER][SIZE=7]:( 
[/SIZE][/CENTER]

---

