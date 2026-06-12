---
title: "Wireless-N (802.11n) Connection Help Please"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by pognogson on 2009-07-26
[LEFT][SIZE=3][FONT=Calibri]I am hoping someone can help me with this 802.11n connectivity issue. Have a Dell Mini-9 running Jaunty with Kernel 2.6.28-13 generic. I upgraded the network card to an intel PRO/Wireless 5300 AGN. This has worked fine since the upgrade and connections have been made and are solid. (The home connection is a Sonicwall TZ180 Wireless). [/FONT][/SIZE][/LEFT]

 

[LEFT][FONT=Calibri][SIZE=3]In an attempt to get greater speed and range I have purchased an updated Sonicwall device (TZ100 wireless) which also has 802.11n cabability. To this I have been unable to get a solid connection.[/SIZE][/FONT][/LEFT]

 
[FONT=Calibri][SIZE=3]As part of the trouble shooting, I have followed the suggestions at the following post:[/SIZE][/FONT]

[LEFT][COLOR=blue][FONT=Verdana][SIZE=3]How to get the Intel WiFi 5100 5300 Working in Ubuntu 9.04[/SIZE][/FONT][/COLOR]
[LEFT][FONT=Verdana][COLOR=black]by, HunterThomson - HowTo's that WORK ![/COLOR][/FONT][/LEFT]
[/LEFT]

 
[FONT=Calibri][SIZE=3]i.e. I installed the new kernel and the backport modules. Still this has not helped.[/SIZE][/FONT]
 

[LEFT][SIZE=3][FONT=Calibri]I have tried with no success the disabling suggestion at [/FONT][COLOR=black][FONT=Verdana][[COLOR=#444444]http://ubuntuforums.org/showpost.php...34&postcount=3[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7415234&postcount=3") [/FONT][/COLOR][/SIZE][/LEFT]

 

[LEFT][FONT=Calibri][SIZE=3]This involves updating the microcode (Done!), but I had problems with the ModProbe instruction (which issues a Warning that config files need .conf: …). (Anyway I don’t want to disable 802.11n, I want to make it work!)[/SIZE][/FONT][/LEFT]

 

[LEFT][FONT=Calibri][SIZE=3]I include output from dmesg below[/SIZE][/FONT][/LEFT]

 

[LEFT][FONT=Calibri][SIZE=3]Other steps I have taken:[/SIZE][/FONT]


[FONT=Calibri][SIZE=3]1. I have tried a USB DLink 11n USB card with similar results on the Ubuntu Netbook. Therefore I think it is not the card.[/SIZE][/FONT]


[FONT=Calibri][SIZE=3]2. I can make it connect to the ‘n’ capable AP if I restrict the AP to 802.11g only. Therefore it would appear to be something in the wireless’n’ instance.[/SIZE][/FONT]


[FONT=Calibri][SIZE=3]3. I have a different Vista PC connecting correctly to the 802.11n capable network at ‘g’ speeds. This proves the DHCP pass through for the server for IP4 settings[/SIZE][/FONT]


[FONT=Calibri][SIZE=3]4. Inspecting the Sonicwall Interface, I can see that both cards associate to the Access Point (AP) but then it times out and fails. This may have something to do with the IP settings.[/SIZE][/FONT]


[FONT=Calibri][SIZE=3]5. I have tried entering the IP4 networking details to see if it was a DHCP problem, but no joy. It perhaps indicates that it is trying to work at IP6 [/SIZE][/FONT]


[FONT=Calibri][SIZE=3]6. I ran the DLINK USB ‘n’ device on a Vista Machine and it successfully connected at ‘n’ including picking up the DHCP settings from the Server.[/SIZE][/FONT]


[FONT=Calibri][SIZE=3]7. I have tried using Open Network but have not had much joy here either.[/SIZE][/FONT][/LEFT]

 

[LEFT][FONT=Calibri][SIZE=3]Therefore I think that it might be something to do with the Ubuntu instance of the Wireless-N settings, either in the IP configuration or somewhere else. Can anyone else assist? (I am much of a newbie in Ubuntu)[/SIZE][/FONT][/LEFT]

 

[LEFT][FONT=Calibri][SIZE=3]The dmesg file attached is trying to connect to the Wireless-N device (set to ‘N’ only) following a reboot.[/SIZE][/FONT][/LEFT]

 

[LEFT][FONT=Calibri][SIZE=3]thanks[/SIZE][/FONT]


[FONT=Calibri][SIZE=3]David[/SIZE][/FONT][/LEFT]

---

