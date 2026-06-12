---
title: "Wireless manager disappeared, can't connect"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by veryannoyed on 2009-11-08
I don't understand what happened. I had a wireless manager thingy on the top panel next to the clock that would show which wireless networks I could connect to and show how many bars I had. I hadn't used my Mini for a little while and now I noticed that the wireless thingy is gone. 

When I try to add an icon to my panel, the wireless thingy doesn't seem to be an option. There is something called "network monitor," which I added, but it doesn't do anything. When I clicked on it, it just says "Name: lo" and "Status: Idle." If I change it from "lo" and then click on it, I get "Please contact your system administrator to resolved the following problem, SIOCGIFFLAGS error: No such device."

When I go into Network Settings under administration, it says automatic is enabled for wireless and wired, but everything is blank. I'm really confused. It's like it just stopped working on its own. I can plug in my ethernet directly and get online, but I can't find any wireless signals anymore.

(FYI I have the Ubuntu Dell remix, but I use the classic Ubuntu mode, 8.04. My computer is the Dell Mini 9.)

---

### Post by veryannoyed on 2009-11-08
Bump. Please! Even if I could restore default settings, maybe it would work again. Hellllpppppp!!!

---

### Post by psyboy55 on 2009-11-08
The same thing happened to me! help please! It happened after i updated to ubuntu 8.10.

---

### Post by psyboy55 on 2009-11-08
I found a quick fix! run nm-applet in terminal. can u help me find  a permanent fix?

---

### Post by veryannoyed on 2009-11-08
Running nm-applet does work, but as soon as I close the terminal, I can't get online again. This is ridiculous. Will someone please help us?!

---

### Post by jkorten on 2009-11-09
> **veryannoyed said:**
> Bump. Please! Even if I could restore default settings, maybe it would work again. Hellllpppppp!!!

I am having the same issues with my wife's T60p Thinkpad. Her wireless sometimes boots up connected to itself (a wireless service with our name on it and an icon indicating a computer to computer link [no other computer on] - when a wireless encrypted service listed with our name on it also exists).

Some times the computer will just NOT connect. If I boot in Windows - it always connects. So this is not a hardware issue. (Intel Pro/Wireless 3845ABG).

Something has definitely changed with the wireless HAL in my opinion.

---

