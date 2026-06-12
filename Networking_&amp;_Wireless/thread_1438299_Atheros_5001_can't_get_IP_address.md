---
title: "Atheros 5001 can't get IP address"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by C2W? on 2010-03-24
**Greetings ... **

Started out with a Toshiba Satellite L305 given to my daughter as "dead". Dead turned out to mean that the Vista operating system had hosed itself and the previous owner wasn't gonna go buy a set of BillyGates discs.  Nor was I...

Always wanted to try Linux so I did some homework and decided on Ubuntu.  Downloaded, Burned a CD and did a a fresh 9.10 install.  **WOW, how EZ was that.**  

System fired right up and most everything worked from the git-go.  The exceptions being the webcam and the LightScribe system and the WiFi.  The first two only because I haven't taken the time to research them and wanted to get the WiFi up and running.

Aterhos didn't work from the git go but an accessory USB 2.0 wireless device I had laying around worked as soon as I plugged it in.  **Yesssssssss WiFi 1st Try.**

The, like a dummy I noticed the tiny slider switch for the WiFi on the front of the system (it was off and yep, I'm the dummy) so I turned it on.  All it would do would be continue to ask for my WPA key over and over and over again.  Eventually my external unit wouldn't connect. Like the Atheros, it kept asking for my password "forever" without connecting. 

Plugged in cable from our D-Link router and jumped on google looking for a quick fix to my stupidity or newbyness.  

More than a bit hesitant to open a terminal and start *"doing stuff*" but I did anyway ...

And in the process I *(somehow)* hosed my hardwire connection. ** Arrrrrggggggghhhhh.**

Don't ask me what I did as I wasn't smart enough to chronicle my stupidity.

OK, after another fresh install I dumped the network manager and tried Wicd.  Hardwire works fine and it finds my wireless network but can't get an IP address. 

Now all I get is a **connection failed: unable to get IP address message.**

**Any ideas???**

---

### Post by chili555 on 2010-03-25
In Wicd > Preferences > Advanced settings, is the WPA supplicant driver set to wext? If you try other drivers, notably madwifi, is the behavior improved? If it is now madwifi, try wext.

---

### Post by C2W? on 2010-03-25
**Thanks for the reply chili555 ...  **I checked and the WPA supplicant driver is set to wext.  Doesn't seem to make any difference which supplicant driver is used.  **Still "no joy".**

---

