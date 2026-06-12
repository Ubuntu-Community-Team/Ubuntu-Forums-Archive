---
title: "WPA/WPA2 Alfa AWUS036NH"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by TheEnigma on 2011-08-13
Hey guys, I have been having a horrible problem others seamed to have had a lot.
I cannot connect to my WPA/WPA2 connection but I can connect to unsecured networks with ease and no problems at all.
Whenever I try and connect to my BtHomeHub WPA/WPA2 Secured password with the right key it just gives me Bad Password, whenever I used the default wireless utility at the top right of the bar it just fails to get an IP.
I'm very very new to Linux as you can probably see.
I downloaded Wicd network manager etc but only get bad password.
The wireless works fine on windows to if that helps.
Wireless card = Alfa AWUS036NH
Any questions just let me know, thankyou. 
Ubuntu 11.04

---

### Post by TheEnigma on 2011-08-14
I have managed to find out I needed to change from WPA/WPA2 to just WPA2 but it hasn't helped at all.
I don't get bad password anymore it just simply wont obtain an IP address any help please?

---

### Post by realzippy on 2011-08-14
My 2c:
I never got stable wlan with Alfa AWUS036NH...also it is state of the art for penetration testing.

---

### Post by northd_tech on 2011-08-26
> **TheEnigma said:**
> 
I downloaded [COLOR=Black]Wicd[/COLOR] [COLOR=Red]**network manager **[/COLOR]etc but only get bad password.
The wireless works fine on windows to if that helps.
Wireless card = Alfa AWUS036NH
Any questions just let me know, thankyou. 
Ubuntu 11.04
If you are certain that your Alfa AWUS036NH is 'seeing' the Wireless Router(s) properly, then there is likely a conflict between **Wicd** and the[COLOR=Red]** [Gnome] Network Manager**[/COLOR].  Give post #5 on the following thread a try:

[http://ubuntuforums.org/showthread.php?t=1675398](http://ubuntuforums.org/showthread.php?t=1675398)

---

