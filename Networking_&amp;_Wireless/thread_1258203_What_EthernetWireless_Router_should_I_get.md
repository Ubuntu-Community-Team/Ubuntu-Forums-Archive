---
title: "What Ethernet/Wireless Router should I get?"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by coldReactive on 2009-09-04
I'm kind of liking Linksys, but how would I go about setting up the router using nothing but Ubuntu? Also, what router should I buy?

I'm looking for Wireless N (with an internal antenna) that's Backwards compatibile with b/g as well (so my PSP can hook up to it.)

It also has to be in-store, I can't get it on line.

---

### Post by bear24rw on 2009-09-04
Dont know any routers off hand but ubuntu has nothing to do with your router config or performance..

To edit config of your router go in firefox to 192.168.1.1

---

### Post by coldReactive on 2009-09-05
Got myself a WRT320N or whatever (Wireless-N Gigabit Router, with that silvery trim)

Works great, but I had to set it up in windows, otherwise Linux couldn't connect to the Internet. Glad I kept Windows on my netbook.

---

### Post by Cuba71 on 2009-09-05
I have a Linksys WRT150N, and I have no problem configuring it from Ubuntu 9.04 and Firefox. It works great for me and I can connect as far as 20' away, with 2 walls in between

---

### Post by coldReactive on 2009-09-05
> **Cuba71 said:**
> I have a Linksys WRT150N, and I have no problem configuring it from Ubuntu 9.04 and Firefox. It works great for me and I can connect as far as 20' away, with 2 walls in between

How did you configure it through the browser user interface?

---

### Post by Whiffle on 2009-09-05
WRT54G is always a safe bet, and widely available.  They're good out of the box, even better if you put dd-wrt or tomato on them.

I have a Buffalo Technology AirStation&#8482; G54 WHR-HP-G54, loaded with dd-wrt and it works great.


EDIT: Oh, you want N, not sure if they have any wrt54g's that do N yet.

---

### Post by coldReactive on 2009-09-05
> **Whiffle said:**
> EDIT: Oh, you want N, not sure if they have any wrt54g's that do N yet.

I already have a WRT54G that is the old style, it works well, but I wanted to upgrade. Now my ethernet goes faster and so does the time it takes to initiate a download speedtest.

---

### Post by Cuba71 on 2009-09-06
> **coldReactive said:**
> How did you configure it through the browser user interface?

Start your Firefox browser, in the URL address type: 192.168.1.1 and hit enter.  Then you'll see a screen to type your ID and Password, your manual will tell you what the defaults are, and later you can change them.'

After that you'll be presented with the Linksys configuration application.

These are the pics

---

### Post by coldReactive on 2009-09-06
> **Cuba71 said:**
> Start your Firefox browser, in the URL address type: 192.168.1.1 and hit enter.  Then you'll see a screen to type your ID and Password, your manual will tell you what the defaults are, and later you can change them.'

After that you'll be presented with the Linksys configuration application.

These are the pics

I know all that, but what do I configure. By default, my router couldn't allow my desktop or wireless to connect to the Internet.

---

### Post by theZoid on 2009-09-07
I have the Linksys Simultaneous Dual Band Router....very great indeed !!

---

### Post by Cuba71 on 2009-09-07
> **coldReactive said:**
> I know all that, but what do I configure. By default, my router couldn't allow my desktop or wireless to connect to the Internet.

This is how I have mine configured:

Setup > Basic > DHCP [Enabled]
Wireless > Basic > Network Mode [Mixed]; SSID [yourSSID]; Radio Band [Wide 40 MHz]; Wide Channel [3]; Standard Channel [1]; SSID Broadcast [Enabled]
Wireless > Security > Mode [WPA2 Personal]; Encryption [AES]; Passphrase [yourAccessPasword]; Key Renewal [3600 seconds]
Administration > Management > Router Password [yourSelectedPwd]; Web Utility [HTTP]; Web Utility via Wireless [Enabled]

Everything else is default.

Then you need to configuere your wireless connection to match this configuration.


I'm sure there's other ways to configure it, but this works for me.

---

### Post by coldReactive on 2009-09-07
Thanks I guess, I'll have to remember all that for next time. I can't use WPA2 yet, as I have a PSP.

---

### Post by jward3010 on 2009-09-07
> **Whiffle said:**
> I have a Buffalo Technology AirStation&#8482; G54 WHR-HP-G54, loaded with dd-wrt and it works great.

Ditto on the DD-WRT, firmware from heaven, and a brilliant router.

---

### Post by tjwilli on 2009-11-27
> **Cuba71 said:**
> I have a Linksys WRT150N, and I have no problem configuring it from Ubuntu 9.04 and Firefox. It works great for me and I can connect as far as 20' away, with 2 walls in between

I have a WRT150N too. It works fine, but the router's in the  basement and the signal is pretty weak upstairs. (I have a 3-level townhouse.) I'm thinking about upgrading to either a Linksys wrt320n or a Dlink DIR-825. Anyone have any experience with either?

---

