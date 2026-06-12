---
title: "Strange problem"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by Lekitanin on 2009-10-19
[FONT=Comic Sans MS][SIZE=3]Greetings to all,[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]I installed Ubuntu 9.04 on an old Dell laptop (Pentium II, 850 MHz, 512 MB RAM) as the only OS. I have Linksys network adapter card with appropriate driver installed by someone who knows more about computers then me.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]Installation of OS went without any problems from ISO CD I created myself.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]My problem is inability to connect to the wireless network at my home.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]If I am in a location with wireless network then connection is easy and reliable. When I am back at home, network card recognizes my network (as well as three others from my neighbors I guess but with much weaker signal then mine) and connects me automatically to the Internet. I can stay on for a long time and connection is fast and good - no problem.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]But if I power down computer and after while I try to get to the Internet again then nothing happens. Blue thing, sperm like, is circling two dots for a while and the message appears: “Network Disconnected” and “You are off line”.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]I right click on the four little bars on the top, click on Edit, Wireless; enter SSID, password, close. Left click on the bars, click on the radio button next to my network name, blue thing is circling two dots for a while and again the same message appears: “Network Disconnected and “Your are off line”.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]I can repeat the same procedure over and over and over with the same results. I noticed however that password I entered before somehow changes “by itself” to a really long string of letters and number. I delete it, enter my own password and it happens again and again.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]My router is a new one, also by Linksys and another computer I have, desktop PC running Windows XP, SP 2 connects to the network every time without glitch.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]Any idea or advice will be greatly appreciated,[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]Tad[/SIZE][/FONT]

---

### Post by soni1770 on 2009-10-19
yo, ubuntu and wireless doesn't allways go smooth, here's how i fixed mine, maybe you can make it work to

there seems to be some problem for ubuntu to decide what form of security the network has
 
i entered the wireless key several times changing the security each time
so wep 40/128-bit key

wep 128-bit passphrase

leap

etc,etc

then when i got it working, mine was wep 40/128-bit key i wrote down the new password it give me, a really long string of numbers, since then i have used this as the key for example when i re-enstaled ubuntu after messing up the resolution. lazy i know, but better than aimless.

good luck,


oh, and if all that fails....
you could go nuclear and re install ubuntu to get it connected again then write down the really long stream of letters/numbers and see what security is in use
make sure you have backup of all data you want to keep, prob some easier way, maybe someone else will know?

---

