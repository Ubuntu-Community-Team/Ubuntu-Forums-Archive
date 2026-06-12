---
title: "No wireless after unity upgrade"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by Uberloser on 2011-04-30
Good morning all,
After upgrading from 10.10 I now have no wireless activity. Everything was great with 10.10 by the way. I have a dell inspiron 1520 with a Dell wireless 1390 card and broadcom 440x integrated controller.
I have seen other threads that are to complicated for me to follow, I would just love for my wireless to work and can follow basic instructions if anyone can help.

I just spent the last 6 days in Florida on business while the tornadoes ravaged my homeland in Alabama :) and turned alot of people on to Ubuntu. Everyone that walked past my laptop wanted to play with it and asked what it was. 

Grateful for any assistance.

---

### Post by dcosiem on 2011-04-30
Somebody help this fella out! I am also having issues with the wireless connection with the [SIZE=3][COLOR=Magenta]Broadcom 440x 10/100 Integrated Controller or [/COLOR][/SIZE][SIZE=3][COLOR=Magenta]Dell Wireless 1390 WLAN MiniCard[/COLOR] [SIZE=1]on a Dell Inspiron 1720, Intel duo core 2.4 processor with 2gb or ram[/SIZE]. [SIZE=1]After reformatting several times to try out Ubuntu 11.04 and Kubuntu 11.04, neither of these operation system's wireless Internet service is working. I have been using to standard cable ethernet cable to connect to the internet, but I would like to be untied again. Thank you! 

Kubuntu is so cool! The new unity format is too mainstream consumer-ish. THank you again! 

:D 
[/SIZE] [/SIZE]

---

### Post by Uberloser on 2011-04-30
Hey dude, this worked.

"I had the same problems... this is what I did:
- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot"

---

### Post by dcosiem on 2011-05-02
Dear Uberloser, 

You ain't an uberloser! Thank you for sharing! Have an awesome life! Even works on Kubuntu! 

> **Uberloser said:**
> Hey dude, this worked.

"I had the same problems... this is what I did:
- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot"

---

### Post by green_earth on 2011-05-02
dcosiem & Uberloser:

Help me understand the process (mostly non-technical Ubuntu/Kubuntu user here). Since installing 11.04, I have exactly ZERO drivers available in the additional drivers. On the last two Ubuntu version, that is how I got my wireless to work. What is the "STA driver" you refer to? And, dcosiem, what is the Kubuntu variant of synaptic? I just installed Kubuntu for the first time since I'm not a fan of Unity. Any help is appreciated...

---

